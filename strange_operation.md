

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
