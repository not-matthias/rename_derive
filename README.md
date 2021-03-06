# rename-rs

[![crates.io](https://img.shields.io/crates/v/rename.svg)](https://crates.io/crates/rename)
[![docs.rs](https://docs.rs/rename/badge.svg)](https://docs.rs/rename)
![Lines of Code](https://tokei.rs/b1/github/not-matthias/rename-rs)

Easy modification of structure names.

## Example

```rust
#[rename(prepend = "One", name = "Two", append = "Three")]
struct Placeholder {
    pub one: u64,
    pub two: u64,
    pub three: u64
}
```
The name of the struct is now `OneTwoThree`. 

# Why?

When working with [declarative macros](https://doc.rust-lang.org/book/ch19-06-macros.html#declarative-macros-with-macro_rules-for-general-metaprogramming) you can't create new [idents](https://doc.rust-lang.org/reference/identifiers.html). You could also remove this problem by using a [proc-macro](https://doc.rust-lang.org/reference/procedural-macros.html), but this would increase the complexity. However, there's the macro [concat_idents](https://doc.rust-lang.org/std/macro.concat_idents.html) which allows you to, as you can probably guess, concat identifiers. The big problem with this macro is, that it's not yet stable and doesn't allow the creation of new identifiers. Thus I decided to create my own little helper crate that solves this problem. 

The implementation for the aforementioned problem can be found [here](./examples/macro.rs).
