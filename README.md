# airu

静的型付けスクリプト言語

##  基本構文

- 行末のセミコロンは不要
- C言語に似た構文をベースとするが、独自の拡張あり

##  変数宣言

```
var x = 5       // ミュータブル変数
let y = "Hello" // イミュータブル変数
```

## 関数定義

```
fn add(a: int, b: int) -> int {
    a + b
}
```

## 制御構造

条件文

```
x > y -> {
    print("x is greater")
} -> {
    print("x is not greater")
}
```

ループ

```
0..5 -> |i| {
    print(i)
}

{x > 0} -> {
    print(x)
    x = x - 1
}
```

##  エラー処理

```
fn divide(x: int, y: int) -> Result<int, string> {
    y == 0 -> Err("Division by zero")
    -> Ok(x / y)
}

match result {
    Ok(value) -> print("Result: {}", value)
    Err(msg) -> print("Error: {}", msg)
}
```


## クラスとオブジェクト指向

```
class Animal {
    var name: string

    fn init(name: string) {
        self.name = name
    }

    fn speak() -> string {
        "..."
    }
}

class Dog : Animal {
    fn speak() -> string {
        "Woof!"
    }
}
```

## トレイト (Mix-in)

```
trait Swimmable {
    fn swim() {
        print("{} is swimming", self.name)
    }
}

class Duck : Animal + Swimmable {
    // ...
}
```

## モジュールシステム

```
// math.ar
pub fn square(x: int) -> int {
    x * x
}

// main.ar
import math

fn main() {
    print(math.square(5))
}
```

## パイプライン演算子

```
[1, 2, 3, 4, 5]
    |> map(square)
    |> filter(|x| x > 10)
    |> sum
    |> print
```


## ジェネリクス

```
fn print_twice<T>(value: T) {
    print(value)
    print(value)
}

class Box<T> {
    var value: T

    fn get() -> T {
        self.value
    }
}

trait Comparable<T> {
    fn compare_to(other: T) -> int
}
```

## 型推論

明示的な型注釈は必須ではありませんが、複雑な場合は推奨

## その他

- 多重継承は禁止されていますが、複数のトレイトを実装可能です
- 静的型付け言語ですが、型推論により多くの場合で明示的な型注釈は不要です。
- スクリプト言語（インタープリタ型）として設計されていますが、将来的にはJITコンパイラの導入も検討可能です