# 泛型
一种多态
```
fn add<T>(a:T, b:T) -> T {
    a + b
}

fn main() {
    println!("add i8: {}", add(2i8, 3i8));
    println!("add i32: {}", add(20, 30));
    println!("add f64: {}", add(1.23, 1.23));
}
```

## 泛型详解
先决条件：使用前先声明 `fn largest<T>(list: &[T]) -> T`

T 的操作：
- 可比较修饰 `T: std::cmp::PartialOrd`
- 可相加修饰 `T: std::ops::Add<Output = T>`

## 枚举类型
```
enum Option<T> {
    Some<T>,
    None,
}

enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

## 方法使用泛型
```
struct Point<T, U> {
    x: T,
    y: U,
}

impl<T, U> Point<T, U> {
    fn mixup<V, W>(self, other: Point<V, W>) -> Point<T, W> {
        Point {
            self.x,
            other.y,
        }
    }
}

fn main() {
    let p1 = Point {x : 5, y : 10.5};
    let p2 = Point {x : "Hello", y : 'c'};
    let p3 = p1.mixup(p2);

    println!("p3.x is {}, p3.y is {}", p3.x, p3.y);
}
```
### 泛型：具体的泛型实现方法
```
impl Point<f32> {
    fn distance_from_origin(&self) {
        (self.x.pow(2) + self.y.pow(2)).sqrt()
    }
}
```

### const 泛型
解决变长数组的问题，不用以不变引用的形式调用

#### 不变引用的调用形式
```
fn display_array<T: std::fmt::Debug>(arr: &[T]) {
    println!("{:?}", arr);
}

fn main() {
    let arr: [i32; 3] = [1, 2, 3];
    display_array(&arr);

    let arr: [i32; 2] = [1, 2];
    display_array(&arr);
}
```

#### const 泛型的形式
语法：`const N: usize`
```
fn display_array<T: std::fmt::Debug, const N: usize>(arr: [T; N]) {
    println!("{:?}", arr);
}

fn main() {
    let arr: [i32; 3] = [1, 2, 3];
    display_array(arr);

    let arr: [i32; 2] = [1, 2];
    display_array(arr);
}
```

### const 泛型表达式
nightly版本，测试中


## 性能分析
rust 编译时将泛型代码进行单态化(monomorphization)处理，相当于代码自动扩充（C++内敛，但更强大）
