# 特征
特征：定义了一组可以被共享的行为，只要实现了特征，就能使用这组行为

## 定义特征
```
pub trait Summary {
    fn summarize(&self) -> String;
}
```

### 孤儿规则 特征定义以及实现的位置
孤儿规则：保证其他人的代码不会破坏原有的代码。

### 使用特征作为函数参数
```
pub fn notify(item: &impl Summary) {
    println!("Breaking news! {}", item.summarize());
}
```

### 特征约束 trait bound
```
pub fn notify<T: Summary>(item: &T) {
    println!("Breaking news! {}", item.summarize());
}
```

