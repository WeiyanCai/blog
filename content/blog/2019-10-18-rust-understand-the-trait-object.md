---
title: 'Rust: Understand the Trait Object'
date: 2019-10-18T02:13:46.737Z
image: /images/screenshot-from-2019-10-17-21-10-48.png
draft: true
---
Trait Object 内部表示可作如下理解：
```rust 
pub struct TraitObject {
	pub data: *mut (),
	pub vtable: *mut (),
}
```

- `dyn Trait` 是 DST 类型，即 unsized 的类型。
- `&dyn Trait` 是胖指针类型，是 sized，大小为两个普通指针的大小之和。
- `*const dyn Trait` 和 `&dyn Trait` 是一样的，都是胖指针，不过前者没有 borrow checker。
- `*const &dyn Trait` 表示指向胖指针的指针（即指向上面表示的结构的指针）。

下面是关于
![Example code for trait object](https://cwy.im/images/screenshot-from-2019-10-17-21-10-48.png)
