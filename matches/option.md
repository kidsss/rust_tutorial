# Option枚举类型
Option枚举类型，被设计的目标为：解决Rust中变量是否有值的问题
定义格式：一个变量要么为None，要么为 Some(T)
```
Enum Option<T> {
    Some(T),
    None,
}
// Some, None, Option支持直接调用，无需 Option::Some, Option::None的形式
```

与 match 结合，实现值解构
```
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        None => None,
        Some(i) => Some(i + 1),
    }
}
```
