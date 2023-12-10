

### 数组枚举
```
let v = vec![1, 2, 3];

for (index, value) in v.iter().enumerate() {
    println!("index {} value {}", index, value);
}
```

### 动态数组取值(模拟栈)
```
let mut stack = Vec::new();

stack.push(1);
stack.push(2);
stack.push(3);

while let Some(top) = stack.pop() {
    println!("{}", top);
}
```

### @绑定
@运算符：为一个字段绑定另一个变量
```
// case 1
enum Message {
    Hello { id: i32 },
}

let msg = Message::Hello { id: 5 };

match msg {
    Message::Hello { id: id_assigned @ 3..=7 } => {
        println!("Found and id {} in range [3..7]", id_assigned)
    },
    Message::Hello { id: 10..=12 } => {
        println!("Found an id")
    },
    Message::Hello { id } => {
        println!("Found some other id {}", id)
    },
}
```

```
// case 2
#[derive(Debug)]
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    // 绑定新变量 p，同时对 Point 进行解构
    let p @ Point {x: px, y: py} = Point {x: 10, y: 32};
    println!("x: {}, y: {}", px, py);
    println!("{:?}", p);

    let point = Point {x: 10, y: 5};
    if let p @ Point {x:10, y} = point {
        println!("x is 10 and y is {} in {:?}", y, p);
    } else {
        println!("x was not 10 :( ");
    }
}
```
