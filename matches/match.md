
# 模式匹配的函数：
- match
- if let

## match 基本用法
### match 匹配的通用形式，返回值
```
match target {
    pattern 1 => exp 1,
    pattern 2 => {
        statement1;
        statement1;
        statement1
    },
    _ => exp 3,
}
// _ 可以用 一个变量名替代
```

### 支持自动提取状态中的值
```
#[derive(Debug)]
enum UsState {
    Alabama, Alaska,
    // --snip--
}

enum Coin {
    Penny, Nickel, Dime,
    Quarter(UsState), // 25美分硬币
}

fn value_in_cents(coins: Coin) -> u8 {
    match coins {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("State quanter from {:?}!", state);
            25
        },
    }
}
```

### matches! ：bool判断
枚举值互相比较时使用，
warning: 无法直接将 变量 与 一个枚举成员进行直接比较；
比较方法：`matches!(x, MyEnum::Foo)`

## if let 匹配
仅需要识别一种模式，其他模式无操作；以下两种方式等价
```
let v = Some(3u8);

// match 的形式
match v {
    Some(3) => println("three"),
    _ => (), // 什么也不做，返回 ()
}

if let Some(3) = v {
    println("three");
}

```
