# 方法 Method

### 关联函数
关联函数：定义在impl之中，但没有self的函数；常用于提供结构体的构造器方法
调用样例： String::from

### 方法的定义形式
```
struct Circle {
    x: f64,
    y: f64,
    radius: f64,
}

impl Circle {
    // Circle结构体的方法实现
    // 关联函数，提供实例初始化，参数不是self，非struct的方法
    fn new(x: f64, y: f64, radius: f64) -> Circle {
        Circle {
            x: x,
            y: y,
            radius: radius,
        }
    }

    // Circle的方法，&self表示借用当前的结构体
    fn area(&self) -> f64 {
        std::f64::consts::PI * (self.radius * self.radius)
    }
}
```

### 关键定义 self, &self, &mut self
- self 表示 Rectangle 的所有权转移到该方法中，这种形式用的较少
- &self 表示该方法对 Rectangle 的不可变借用
- &mut self 表示可变借用

使用方法代替函数有以下好处：
- 不用在函数签名中重复书写 self 对应的类型
- 代码的组织性和内聚性更强，对于代码维护和阅读来说，好处巨大


