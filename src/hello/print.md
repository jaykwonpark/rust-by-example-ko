# 형식을 지정하는 출력

출력은 [`std::fmt`][fmt] 에 정의된 몇개의 [`macro`][macros] 로 처리합니다.

* `format!`: 형식 지정된 문자열을 [`String`][string] 에 출력합니다.
* `print!`: `format!` 과 동일하지만, 문자열을 콘솔 (io::stdout) 에 출력합니다.
* `println!`: `print!` 과 동일하지만, 개행 문자를 덧 붙여줍니다.
* `eprint!`: `format!` 과 동일하지만, 문자열을 표준 오류 스트림 (io::stderr) 에 출력합니다.
* `eprintln!`: `eprint!`과 동일하지만, 개행 문자를 덧 붙여줍니다.

이들은 모두 동일한 방식으로 문자열을 분석합니다. 그리고, 러스트는 컴파일 시점에
형식지정이 올바른지 여부를 검사합니다.


```rust,editable,ignore,mdbook-runnable
fn main() {
    // 일반적으로, `{}`는 자료형(type)에 관계없이 주어진 인지로 대치됩니다.
    // 이때, 인자들은 문자열로 변환됩니다.
    println!("{} 번째 날", 31);

    // 자료형 표시(suffix)가 없으므로 31은 i32 형이 됩니다. 31 의 자료형을 바꾸려면
    // 자료형 표시(suffix)를 해주면 됩니다. 31i64 라고 하면 i64 형이 됩니다.

    // 중괄호를 이용해서 다양한 방법으로 형식을 지정할 수 있습니다.
    // 인자의 위치를 이용할 수도 있습니다.
    println!("{0}, this is {1}. {1}, this is {0}", "Alice", "Bob");

    // 이름을 줄 수도 있습니다.
    println!("{subject} {verb} {object}",
             object="the lazy dog",
             subject="the quick brown fox",
             verb="jumps over");

    // `:` 의 뒤에 특별한 형식을 지정할 수도 있습니다.
    println!("{} of {:b} people know binary, the other half doesn't", 1, 2);

    // You can right-align text with a specified width. This will output
    // "     1". 5 white spaces and a "1".
    println!("{number:>width$}", number=1, width=6);

    // You can pad numbers with extra zeroes. This will output "000001".
    println!("{number:>0width$}", number=1, width=6);

    // Rust even checks to make sure the correct number of arguments are
    // used.
    println!("My name is {0}, {1} {0}", "Bond");
    // FIXME ^ Add the missing argument: "James"

    // Create a structure named `Structure` which contains an `i32`.
    #[allow(dead_code)]
    struct Structure(i32);

    // However, custom types such as this structure require more complicated
    // handling. This will not work.
    println!("This struct `{}` won't print...", Structure(3));
    // FIXME ^ Comment out this line.
}
```

[`std::fmt`][fmt] contains many [`traits`][traits] which govern the display
of text. The base form of two important ones are listed below:

* `fmt::Debug`: Uses the `{:?}` marker. Format text for debugging purposes.
* `fmt::Display`: Uses the `{}` marker. Format text in a more elegant, user
friendly fashion.

Here, we used `fmt::Display` because the std library provides implementations
for these types. To print text for custom types, more steps are required.

Implementing the `fmt::Display` trait automatically implements the
[`ToString`] trait which allows us to [convert] the type to [`String`][string].

### Activities

 * Fix the two issues in the above code (see FIXME) so that it runs without
   error.
 * Add a `println!` macro that prints: `Pi is roughly 3.142` by controlling
   the number of decimal places shown. For the purposes of this exercise,
   use `let pi = 3.141592` as an estimate for pi. (Hint: you may need to
   check the [`std::fmt`][fmt] documentation for setting the number of
   decimals to display)

### 참고:

[`std::fmt`][fmt], [`macros`][macros], [`struct`][structs], [`traits`][traits]

[fmt]: https://doc.rust-lang.org/std/fmt/
[macros]: ../macros.md
[string]: ../std/str.md
[structs]: ../custom_types/structs.md
[traits]: https://doc.rust-lang.org/std/fmt/#formatting-traits
[`ToString`]: https://doc.rust-lang.org/std/string/trait.ToString.html
[convert]: ../conversion/string.md
