# 코멘트

모든 프로그램에는 코멘트가 필요합니다. 러스트는 여러가지 코멘트 형식을 
지원합니다.

* *일반 코멘트* 에는 컴파일러가 관여하지 않습니다.:
   * `// 한 줄 코멘트는 해당 줄의 끝까지 무시됩니다.`
   * `/* 블럭 코멘트는 종료 표시가 나올 때까지 무시됩니다. */`
* *Doc 코멘트는* [라이브러리 문서][docs] 생성에 사용됩니다.:
   * `/// 코멘트 다음에 오는 것의 문서를 생성합니다.`
   * `//! 코멘트를 감싸는 것의 문서를 생성합니다.`

```rust,editable
fn main() {
    // 이것이 한 줄 코멘트입니다.
    // 맨 앞에 슬래시 두개를 넣으면 됩니다.
    // 컴파일러는 코멘트 안에 있는 것은 아무것도 읽지 않습니다.

    // println!("Hello, world!");

    // 실행해보세요. 뭐가 보이나요? 윗줄에서 슬래시 두개를 지우고 다시 실행해보면요?

    /* 
     * 이건 블럭 코멘트입니다. 일반적으로는 한줄 코멘트를 많이 사용합니다. 하지만
     * 임시로 코드를 막을 때에는 블럭 코멘트가 아주 편리합니다.
     * /* 블럭 코멘트는 /* 중첩 */ 될 수 있습니다. */
     * 이 main 함수 안의 모든 것을 코멘트로 감싸는 것도 몇번의 타이핑이면 충분합니다.
     * /*/*/* 직접 해보세요! */*/*/
     */

    /*
    주의: 위의 블럭 코멘트 앞쪽에 `*` 컬럼은 보기 좋으라고 넣은 것입니다. 
    블럭 코멘트앞에 '*' 를 넣어야만 하는 것은 아닙니다.
    */

    // 표현식을 다룰 때는 블럭 코멘트가 한줄 코멘트보다 편리합니다.
    // 다음에서 코멘트를 삭제하고 결과가 어떻게 바뀌는지 확인해보세요.
    let x = 5 + /* 90 + */ 5;
    println!("`x` 는 10 인가 아니면 100 인가? x 는 {} 이다.", x);
}

```

### 참고:

[라이브러리 문서][docs]

[docs]: ../meta/doc.md
