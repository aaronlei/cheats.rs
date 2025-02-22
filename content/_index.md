+++
weight = 1
sort_by = "weight"
template = "index.html"
insert_anchor_links = "right"
+++

<img id="logo" class="hide_on_small" src="logo.png" alt="煮熟的大闸蟹~"></img>
<pagetitle>Rust 语言备忘清单</pagetitle>
<subtitle><span id="subtitle" onclick="advance_subtitle()">{{ date() }}</span></subtitle>


<blockquote class="legend">

<symbol-legend class="short">

文中提到的书籍:
《Rust 程序设计语言》{{ book(page="") }} (中文),
《通过例子学 Rust》{{ ex(page="") }} (中文),
《标准库文档》{{ std(page="std") }},
《Rust 秘典》{{ nom(page="") }} (中文),
《Rust 参考手册》{{ ref(page="") }} (中文).

</symbol-legend>

<symbol-legend class="long">

<twocolumn>
<column>

**可点击凡例** <br>
<br> <legend-symbol> {{ book(page="") }} </legend-symbol>《Rust 程序设计语言》
<br> <legend-symbol> {{ ex(page="") }} </legend-symbol>《通过例子学 Rust》
<br> <legend-symbol> {{ std(page="std") }} </legend-symbol>《标准库文档》
<br> <legend-symbol> {{ nom(page="") }} </legend-symbol>《Rust 秘典》(死灵书)
<br> <legend-symbol> {{ ref(page="") }} </legend-symbol>《Rust 参考手册》
<br> <legend-symbol> {{ rfc(page="") }} </legend-symbol>官方 **RFC** 文档
<br> <legend-symbol> {{ link(url="https://nootn.com/rust-language-cheat-sheet/") }} </legend-symbol>**外部链接**
<br> <legend-symbol> {{ above(target="#") }} </legend-symbol>参见**上文**
<br> <legend-symbol> {{ below(target="#") }} </legend-symbol>参见**下文**

</column>
<column>

**其他凡例** <br>
<br> <legend-symbol> {{ deprecated() }}   </legend-symbol>基本**已废弃**
<br> <legend-symbol> {{ edition(ed="'18") }} </legend-symbol>有**最低版本**要求. 
<br> <legend-symbol> {{ experimental() }} </legend-symbol>要求**Rust nightly** (或不完整). 
<br> <legend-symbol> {{ bad() }}   </legend-symbol>故意的**错误示例**或**缺陷代码**. 
<br> <legend-symbol> {{ esoteric() }}   </legend-symbol>略显**深奥**, 很少使用的高级我. 
<br> <legend-symbol> {{ hot() }}   </legend-symbol>**常用特性**
<br> <legend-symbol> {{ todo() }} </legend-symbol>**缺少链接**或说明
<br> <legend-symbol> {{ opinionated() }} </legend-symbol>**作者见解**

</column>
</twocolumn>
</symbol-legend>

<div style="text-align: right; height: 1px;">
    <span class="expander" style="font-size: 10px; position: relative; top: -20px;">
        <a href="javascript:toggle_legend();">➕</a>
    </span>
</div>

</blockquote>


<noprint>
<page-controls>
    <!-- <a id="" href="" style="float: left; margin-left:5px;">X-Ray Mode 👓</a> -->
    <a id="toggle_ligatures" href="javascript:toggle_ligatures()">字体连字 (<code>..=, =></code>)</a>
    <a id="expand_everything" class="hide_on_small" href="javascript:toggle_expand_all()">展开所有内容？</a>
    <a href="javascript:toggle_night_mode()">夜间模式 &#x1f4a1;</a>
</page-controls>
</noprint>

<noprint>
<toc><column>

**语言结构**
* [数据结构](#data-structures)
* [引用 & 指针](#references-pointers)
* [函数 & 行为](#functions-behavior)
* [控制流程](#control-flow)
* [代码组织](#organizing-code)
* [类型别名和转换](#type-aliases-and-casts)
* [宏 & 属性](#macros-attributes)
* [模式匹配](#pattern-matching)
* [泛型和约束](#generics-constraints)
* [高阶项目](#higher-ranked-items)
* [字符串和字符](#strings-chars)
* [文档](#documentation)
* [其他](#miscellaneous)

**增强设施**
* [抽象层](#the-abstract-machine)
* [语法糖](#language-sugar)
* [内存和生命周期](#memory-lifetimes)


**数据布局**
* [基本类型](#basic-types)
* [自定义类型](#custom-types)
* [引用 & 指针](#references-pointers-ui)
* [闭包](#closures-data)
* [标准库类型](#standard-library-types)

**附录**
* [外链 & 服务](#links-services)
* [打印 & PDF](#printing-pdf)

</column>

<column>

**标准库**
* [基本准则](#one-liners)
* [线程安全](#thread-safety)
* [迭代器](#iterators)
* [数字转换](#number-conversions)
* [字符串转换](#string-conversions)
* [字符串输出](#string-output)


**工具**
* [项目结构](#project-anatomy)
* [Cargo](#cargo)
* [交叉编译](#cross-compilation)
* [工具指令](#tooling-directives)


**与类型打交道**
* [类型, Trait, 泛型](#types-traits-generics)
* [类型乐园](#type-zoo)
* [类型转换](#type-conversions)


**编码指南**
* [Rust 惯用法](#idiomatic-rust)
* [Async-Await 101](#async-await-101)
* [API 中的闭包](#closures-in-apis)
* [Unsafe, Unsound, Undefined](#unsafe-unsound-undefined)
* [API 稳定性](#api-stability)


</column>
</toc>
</noprint>

</noprint>

## 你好, Rust!

如果你是 Rust 新手, 或者你想试点什么, 可以在下面尝试运行一下: 

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-1" name="tab-hello" checked/>
<label for="tab-hello-1"><b>Hello World</b></label>
<panel><div>
<div id="hellostatic">

```rust
fn main() {
    println!("Hello, world!");
}
```


</div>
<div id="helloplay"></div>
<div id="helloinfo">服务由 <a href="https://play.rust-lang.org/" target="_blank" rel="noopener">play.rust-lang.org <sup>🔗</sup></a> 提供</div>
<div id="helloctrl"><a href="javascript:show_playground(true);">▶️ 编辑 & 运行</a></div>
</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-3" name="tab-hello">
<label for="tab-hello-3"><b>优势</b></label>
<panel><div>

**Rust 擅长此事**

- 编译后的代码拥有与 C/C++ [几乎同样的性能](https://benchmarksgame-team.pages.debian.net/benchmarksgame/box-plot-summary-charts.html) , 在[内存和能效](https://dl.acm.org/doi/10.1145/3136014.3136031)方面甚至更强.
- 可以避免 C/C++ 存在 [70% 的安全问题](https://www.chromium.org/Home/chromium-security/memory-safety)和绝大多数内存问题.
- 强类型系统可防止[数据竞争](https://doc.rust-lang.org/nomicon/races.html), 带来[「无畏并发」](https://blog.rust-lang.org/2015/04/10/Fearless-Concurrency.html) (以及更多).
- 与 C 无缝衔接, [支持数十个平台](https://doc.rust-lang.org/rustc/platform-support.html) (基于 LLVM).
- 连续 6 年[「最喜爱的语言」](https://insights.stackoverflow.com/survey/2021#technology-most-loved-dreaded-and-wanted).
- 现代工具链: `cargo` (构建工作 _正好能用_), `clippy` (450+ 代码质量 lints), `rustup` (易用的工具链管理)).

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-4" name="tab-hello">
<label for="tab-hello-4"><b>劣势</b></label>
<panel><div>

**你可能会遇到的问题**

- 学习曲线陡峭<sup>1</sup>. 其他场合下的“最佳实践”往往会被编译器教训一通(特别是内存方面).
- 缺少某些领域的 Rust-native 库, 目标平台(尤其是嵌入式)以及 IDE 功能.<sup>1</sup>
- 比起其他语言中“类似的”代码编译时间更长.<sup>1</sup>
- 没有正式语言规范, 影响在某些领域(如航空, 医疗等)的合法使用.
- 内部使用了 `unsafe` 的第三方库有可能会破坏安全性保证.

<sup>1</sup> 参见该 [Rust 调查结果](https://blog.rust-lang.org/2020/04/17/Rust-survey-2019.html#why-not-use-rust).
</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-5" name="tab-hello">
<label for="tab-hello-5"><b>安装</b></label>
<panel><div>

**下载**
- 从 [**rustup.rs**](https://rustup.rs/) 获取安装程序 (推荐用于任何平台) 


**IDE 编辑器**
- [IntelliJ](https://www.jetbrains.com/idea/)  (免费) 或者带有 [**IntelliJ Rust**](https://intellij-rust.github.io/) 功能的 [CLion](https://www.jetbrains.com/clion/)  (收费). 
- 安装了 [**rust-analyzer**](https://rust-analyzer.github.io/) 插件的 [Visual Studio Code](https://code.visualstudio.com/). 


</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-6" name="tab-hello">
<label for="tab-hello-6"><b>开始于此</b></label>
<panel><div>

<!-- Note - Please ONLY submit PRs linking to high-quality, "permanent" sites
            dedicated to learning Rust that work in a browser, are moderately
            condensed, and have a public Git repo and issue tracker.
            Also, this section should be very short <=3 entries, so it should only list
            "the best of their kind".
             -->

**模块化初学者资源**
- [《Rust 语言之旅》(中文)](https://tourofrust.com/TOC_zh-cn.html) - 一边讲解, 一边实时编码.
- [Rust in Easy English](https://dhghomon.github.io/easy_rust/Chapter_3.html) - 用若干个例子和简单的英语解释了 60 多个概念. 可以用来练习英语.

另可参考常用文档. {{ book(page="") }} {{ ex(page="") }} {{ std(page="std") }}


> **作者按** {{ opinionated() }} &mdash; 如果你从来没用过 Rust 最好还是先看看上面的教程, 本文后续章节对相关概念仅作简要说明, 不会深入讲解. 

</div></panel></tab>

</tabs>
</noprint>


### 数据结构 {#data-structures}

数据类型和内存位置由关键字定义. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `struct S {}` | 定义包含命名字段的**结构体**{{ book(page="ch05-00-structs.html") }} {{ ex(page="custom_types/structs.html") }} {{ std(page="std/keyword.struct.html") }} {{ ref(page="expressions/struct-expr.html") }}.  |
| {{ tab() }} `struct S { x: T }` | 定义包含 `T` 类型命名字段 `x` 的结构体.  |
| {{ tab() }} `struct S` &#8203;`(T);` | 定义 `T` 类型数字字段 `.0` 的“元组”结构体.  |
| {{ tab() }} `struct S;` | 定义一个**零大小**{{ nom(page="exotic-sizes.html#zero-sized-types-zsts")}}的单元结构体. 已优化不占用任何空间.  |
| `enum E {}` | 定义**枚举**{{ book(page="ch06-01-defining-an-enum.html") }} {{ ex(page="custom_types/enum.html#enums") }} {{ ref(page="items/enumerations.html") }},  参见[数字数据类型](https://en.wikipedia.org/wiki/Algebraic_data_type)和[标签联合](https://en.wikipedia.org/wiki/Tagged_union).  |
| {{ tab() }}  `enum E { A, B`&#8203;`(), C {} }` | 定义变体枚举; 可以是单元- `A`, 元组 `B` &#8203;`()` 或者结构体风格的 `C{}`.  |
| {{ tab() }}  `enum E { A = 1 }` | 如果所有变体都是单元值, 则允许判别式值, 例如用于 FFI.  |
| `union U {}` | 不安全的 C 风格**联合体**{{ ref(page="items/unions.html") }}, 用于兼容 FFI.  {{ esoteric() }} |
| `static X: T = T();`  | 具有 `'static` 生命周期的**全局变量** {{ book(page="ch19-01-unsafe-rust.html#accessing-or-modifying-a-mutable-static-variable") }} {{ ex(page="custom_types/constants.html#constants") }} {{ ref(page="items/static-items.html#static-items") }}, 内存位置独立.  |
| `const X: T = T();`  | 定义**常量**{{ book(page="ch03-01-variables-and-mutability.html#differences-between-variables-and-constants") }} {{ ex(page="custom_types/constants.html") }} {{ ref(page="items/constant-items.html") }}, 使用时会临时复制一份.  |
| `let x: T;`  | 在栈{{ note( note="1") }}上分配 `T` 大小的字节并命名为 `x`.  一旦分配不可修改.  |
| `let mut x: T;`  | 类似于 `let`, 但具有**可变性**{{ book(page="ch03-01-variables-and-mutability.html") }} {{ ex(page="variable_bindings/mut.html") }}, 允许修改和可变借用{{ note( note="2") }}.  |
| {{ tab() }} `x = y;` | 将 `y` 移动到 `x`, 如果 `T` 不能 **`Copy`**{{ std(page="std/marker/trait.Copy.html") }}, `y` 将不再可用, 否则会复制一份 `y`.  |

</fixed-2-column>

<footnotes>

<sup>1</sup> **域变量** {{ book(page="ch03-01-variables-and-mutability.html") }} {{ ex(page="variable_bindings.html") }} {{ ref(page="variables.html") }}是生存在栈上的同步代码. 在`async{}`中, 这些变量将成为异步状态机的一部分, 最终可能是驻留在堆上. <br>
<sup>2</sup> 注意术语_可变_和_不可变_并不准确. 不可变绑定或共享引用可能仍然包含 Cell {{ std(page="std/cell/index.html") }}, 从而提供_内部可变性_. 

</footnotes>


{{ tablesep() }}

下面列出了如何构建和访问数据结构; 以及一些_神奇的_类型. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `S { x: y }` | 构建 `struct S {}` 或者 `use` 的 `enum E::S {}` 字段 `x` 设置为 `y`.  |
| `S { x }` | 同上, 但字段 `x` 会被设置为局部变量 `x`.  |
| `S { ..s }` | 用 `s` 填充剩余字段, 常配合 [Default](https://doc.rust-lang.org/std/default/trait.Default.html) 一起使用.  |
| `S { 0: x }` | 类似下面的 `S` &#8203;`(x)`, 但是用结构体语法设置字段 `.0`.  |
| `S`&#8203; `(x)` | 创建 `struct S` &#8203;`(T)` 或者 `use` 的 `enum E::S`&#8203; `()` 其中字段 `.0` 设置为 `x`.  |
| `S` | 表示 `struct S;` 或以 `S` 为值创建 `use` 来的 `enum E::S`.  |
| `E::C { x: y }` | 构建枚举变体 `C`.  上面的其他方法依然有效.  |
| `()` | 空元组, 既是字面量也是类型, 又称**单元**. {{ std(page="std/primitive.unit.html") }} |
| `(x)` | 括号表达式.  |
| `(x,)` | 单元素**元组**表达式. {{ ex(page="primitives/tuples.html") }} {{ std(page="std/primitive.tuple.html") }} {{ ref(page="expressions/tuple-expr.html") }} |
| `(S,)` | 单元素元组类型.  |
| `[S]` | 未指明长度的数组类型, 如**切片**. {{ ex(page="primitives/array.html") }} {{ std(page="std/primitive.slice.html") }} {{ ref(page="types.html#array-and-slice-types") }} 不能生存在栈上. {{ note( note="*") }} |
| `[S; n]` | 元素类型为 `S`, 定长为 `n` 的**数组类型** {{ ex(page="primitives/array.html") }}  {{ std(page="std/primitive.array.html") }}.  |
| `[x; n]` | 由 `n` 个 `x` 的副本构建的数组实例. {{ ref(page="expressions/array-expr.html") }} |
| `[x, y]` | 由给定元素 `x` 和 `y`构成的数据实例.  |
| `x[0]` | 索引, 下标为 `usize` 类型. 可重载 [**Index**](https://doc.rust-lang.org/std/ops/trait.Index.html) 和 [**IndexMut**](https://doc.rust-lang.org/std/ops/trait.IndexMut.html).  |
| {{ tab() }} `x[..]` | 范围索引, 这里是_全部范围_, 又见下 `x[a..b]`, `x[a..=b]`, ...  |
| `a..b` | **左闭右开区间** {{ std(page="std/ops/struct.Range.html") }} {{ ref(page="expressions/range-expr.html") }}, 如 `1..3` 表示 `1, 2`.   |
| `..b` | 无起点到**右开区间** {{ std(page="std/ops/struct.RangeTo.html") }}.  |
| `a..=b` | **全闭合区间**, {{ std(page="std/ops/struct.RangeInclusive.html") }} `1..=3` 表示 `1, 2, 3`.  |
| `..=b` | 无起点到**右闭合区间** {{ std(page="std/ops/struct.RangeFrom.html") }}.  |
| `..` | **全包含区间**{{ std(page="std/ops/struct.RangeFull.html") }}, 常表示_整个组合_.  |
| `s.x` | 命名 **字段访问**{{ ref(page="expressions/field-expr.html") }}, 如果 `x` 不是类型 `S` 的一部分的话则会尝试 [Deref](https://doc.rust-lang.org/std/ops/trait.Deref.html).  |
| `s.0` | 数字字段访问, 用于元组类型 `S` &#8203;`(T)`.  |

</fixed-2-column>

<footnotes>

<sup>*</sup> 目前, 可以参考{{ rfc( page ="1909-unsized-rvalues.html") }}中的[已知问题](https://github.com/rust-lang/rust/issues/48055). 

</footnotes>


### 引用 & 指针 {#references-pointers}

为非所有者内存赋予访问权限. 另请参见 [泛型 & 约束](#generics-constraints). 


<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `&S` | 共享 **引用** {{ book(page="ch04-02-references-and-borrowing.html") }} {{ std(page="std/primitive.reference.html") }} {{ nom(page="references.html")}} {{ ref(page="types.html#pointer-types")}} (用于存储_任意_`&s`). |
| {{ tab() }} `&[S]` | 特殊的切片引用, 包含地址和长度 (`address`, `length`). |
| {{ tab() }} `&str` | 特殊的字符串引用, 包含地址和长度 (`address`, `length`). |
| {{ tab() }} `&mut S` | 允许修改的独占引用 (参见 `&mut [S]`, `&mut dyn S`, &hellip;). |
| {{ tab() }} `&dyn T` | 特殊的 **trait 对象** {{ book(page="ch17-02-trait-objects.html#using-trait-objects-that-allow-for-values-of-different-types") }} 引用, 包含地址和虚表 (`address`, `vtable`). |
| `&s` | 共享**借用** {{ book(page="ch04-02-references-and-borrowing.html") }} {{ ex(page="scope/borrow.html") }} {{ std(page="std/borrow/trait.Borrow.html") }} (_该_ `s` 的地址, 长度, 虚表等, 如 `0x1234`). |
| {{ tab() }} `&mut s` | 具有**可变性**的独占借用. {{ ex(page="scope/borrow/mut.html") }} |
| `*const S` | 不可变的**裸指针类型** {{ book(page="ch19-01-unsafe-rust.html#dereferencing-a-raw-pointer") }} {{ std(page="std/primitive.pointer.html") }} {{ ref(page="types.html#raw-pointers-const-and-mut") }}, 内存不安全 |
| {{ tab() }} `*mut S` | 可变的裸指针类型, 内存不安全. |
| {{ tab() }} `&raw const s` | 不通过引用创建裸指针, 见 `ptr:addr_of!()` {{ std(page="std/ptr/macro.addr_of.html") }} {{ experimental() }} {{ esoteric() }}  |
| {{ tab() }} `&raw mut s` | 同上, 但可变. {{ experimental() }} 裸指针可用于未对齐的包装字段. {{ esoteric() }} |
| `ref s` | **引用绑定**, {{ ex(page="scope/borrow/ref.html") }} 创建绑定的引用类型. {{ deprecated() }}|
| {{ tab() }} `let ref r = s;` | 等价于 `let r = &s`. |
| {{ tab() }} `let S { ref mut x } = s;` | 可变引用绑定 (`let x = &mut s.x`), 解构{{ below( target = "#pattern-matching") }}的简写. |
| `*r` | **解引用** {{ book(page="ch15-02-deref.html") }} {{ std(page="std/ops/trait.Deref.html") }} {{ nom(page="vec-deref.html") }} 引用 `r` 以访问指针指向的内容. |
| {{ tab() }} `*r = s;` | 如果 `r` 是一个可变引用, 则将 `s` 移动或复制到目标内存.  |
| {{ tab() }} `s = *r;` | 如果 `r` 可 `Copy`, 则将 `r` 引用的内容复制到 `s`.  |
| {{ tab() }} `s = *my_box;` | `Box` 有一个特例{{ link(url="https://www.reddit.com/r/rust/comments/b4so6i/what_is_exactly/ej8xwg8") }}, 即便它不可 `Copy`, 也仍会从 Box 里面移动出来. |
| `'a`  | **生命周期参数**, {{ book(page="ch10-00-generics.html") }} {{ ex(page="scope/lifetime.html")}} {{ nom(page="lifetimes.html") }} {{ ref(page="items/generics.html#type-and-lifetime-parameters")}}, 为静态分析声明一块代码的持续时间. |
| {{ tab() }}  `&'a S`  | 仅支持生存时间不短于 `'a` 的地址 `s` . |
| {{ tab() }}  `&'a mut S`  | 同上, 但允许改变地址指向的内容. |
| {{ tab() }}  `struct S<'a> {}`  | 表明 `S` 包含一个生命周期为 `'a` 的地址.由 `S` 的创建者决定 `'a`. |
| {{ tab() }} `trait T<'a> {}` | 表明一个实现了 `impl T for S` 的 `S` 可能会包含地址. |
| {{ tab() }}  `fn f<'a>(t: &'a T)`  | 同上, 用于函数.调用者决定 `'a`. |
| `'static`  | 特殊的生命周期, 生存在程序的整个执行过程中.  |

</fixed-2-column>




###  函数 & 行为 {#functions-behavior}

定义代码单元及其抽象. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `trait T {}`  | 定义 **trait** {{ book(page="ch10-02-traits.html") }} {{ ex(page="trait.html") }} {{ ref(page="items/traits.html") }}, 它是一系列可被实现的通用行为. |
| `trait T : R {}` | `T` 是**父 trait** {{ ref(page="items/traits.html#supertraits") }} `R` 的子 trait.任何要 `impl T` 的 `S` 都必须先 `impl R`. |
| `impl S {}`  | 类型 `S` 的函数**实现** {{ ref(page="items/implementations.html") }}, 如方法. |
| `impl T for S {}`  | 为类型 `S` 实现 trait `T`. |
| `impl !T for S {}` | 禁用自动推导的 **auto trait**. {{ nom(page="send-and-sync.html") }} {{ ref(page="special-types-and-traits.html#auto-traits") }} {{ experimental() }} {{ esoteric() }} |
| `fn f() {}`  | 定义一个**函数**{{ book(page="ch03-03-how-functions-work.html") }}  {{ ex(page="fn.html") }} {{ ref(page="items/functions.html") }}, 或在 `impl` 里关联一个函数. |
| {{ tab() }} `fn f() -> S {}`  | 同上, 但会返回一个 `S` 类型的值. |
| {{ tab() }} `fn f(&self) {}`  | 定义一个方法.{{ book(page="ch05-03-method-syntax.html") }}  {{ ex(page="fn/methods.html") }}例如, 在 `impl S {}` 中. |
| `const fn f() {}`  | 编译期常量函数 `fn`.如 `const X: u32 = f(Y)`. {{ edition(ed="'18") }}|
| `async fn f() {}`  | **异步** {{ ref(page="items/functions.html#async-functions") }} {{ edition(ed="'18") }} 函数转写{{ below(target="#async-await-101") }}. 令 `f` 返回一个 `impl` **`Future`**. {{ std(page="std/future/trait.Future.html") }} |
| {{ tab() }} `async fn f() -> S {}`  | 同上, 但令 `f` 返回 `impl Future<Output=S>`. |
| {{ tab() }} `async { x }`  | 用在函数内部, 使 `{ x }` 变得 `impl Future<Output=X>`. |
| `fn() -> S`  | **函数指针**{{ book(page="ch19-05-advanced-functions-and-closures.html#function-pointers") }} {{ std(page="std/primitive.fn.html") }} {{ ref(page="types.html#function-pointer-types") }}, 内存存放的可调用地址. |
| `Fn() -> S`  | **可调用 Trait**{{ book(page="ch19-05-advanced-functions-and-closures.html#returning-closures") }} {{ std(page="std/ops/trait.Fn.html") }}(又见 `FnMut` 和 `FnOnce`), 可由闭包或函数等实现. |
| <code>&vert;&vert; {} </code> | **闭包** {{ book(page="ch13-01-closures.html") }} {{ ex(page="fn/closures.html") }} {{ ref(page="expressions/closure-expr.html")}} , 将会借用它所有的**捕获**.{{ below(target="#closures-data") }} {{ ref(page="types/closure.html#capture-modes") }}  (如局部变量). |
| {{ tab() }} <code>&vert;x&vert; {}</code> | 有传入参数 `x` 的闭包. |
| {{ tab() }} <code>&vert;x&vert; x + x</code> | 没有块表达式的闭包, 仅可由单个表达式组成. |
| {{ tab() }} <code>move &vert;x&vert; x + y </code> | 闭包, 将会获取它所有捕获的所有权. |
| {{ tab() }} <code> return &vert;&vert; true </code> | 闭包, 看起来像是逻辑或, 但这里表示返回一个闭包. |
| `unsafe` | **不安全代码**.{{ below(target="#unsafe-unsound-undefined") }} {{ book(page="ch19-01-unsafe-rust.html#unsafe-superpowers") }} {{ ex(page="unsafe.html#unsafe-operations") }} {{ nom(page="meet-safe-and-unsafe.html") }} {{ ref(page="unsafe-blocks.html#unsafe-blocks") }} . 如果你喜欢在周五晚上调试段错误的话~ |
| {{ tab() }} `unsafe fn f() {}` | 意味着“调用会导致 UB{{ below(target="#unsafe-unsound-undefined") }}, **必须检查**依赖.” |
| {{ tab() }} `unsafe trait T {}` | 意味着“不完善的 `impl T` 会导致 UB, **必需检查实现**.”  |
| {{ tab() }} `unsafe { f(); }` | 向编译器保证“**我已检查过**依赖, 请相信我.”  |
| {{ tab() }} `unsafe impl T for S {}` | 保证“`S` 的行为确实符合 `T`”, 在 `S` 上使用 `T` 是安全的.  |

</fixed-2-column>


### 控制流程 {#control-flow}

在函数中控制执行. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `while x {}`  | **循环**{{ ref(page="expressions/loop-expr.html#predicate-loops") }}, 当表达式 `x` 为真时运行. |
| `loop {}`  | **无限循环**{{ ref(page="expressions/loop-expr.html#infinite-loops") }}直到 `break`. 可以用 `break x` 来 yield 一个值出来. |
| `for x in iter {}` | 在**迭代器**上循环的语法糖.{{ book(page="ch13-02-iterators.html") }} {{ std(page="std/iter/index.html") }} {{ ref(page="expressions/loop-expr.html#iterator-loops") }} |
| `if x {} else {}`  | **条件分支** {{ ref(page="expressions/if-expr.html") }}. 如果表达式为真则...否则... |
| `'label: loop {}` | **循环标签** {{ ex(page="flow_control/loop/nested.html") }} {{ ref(page="expressions/loop-expr.html#loop-labels")}}, 用于嵌套循环的流程控制. |
| `break`  | **Break 表达式** {{ ref(page="expressions/loop-expr.html#break-expressions") }}, 用于退出循环. |
| {{ tab() }} `break x`  | 同上, 但将 `x` 作为循环表达式的值(仅在 `loop` 中有效). |
| {{ tab() }} `break 'label`  | 不单单退出的是当前循环, 而是最近一个标记有 `'label` 的循环. |
| {{ tab() }} `break 'label x`  |  同上, 但返回 `x` 作为闭包循环 `'label` 的值. |
| `continue `  | **Continue 表达式** {{ ref(page="expressions/loop-expr.html#continue-expressions") }}, 用于继续该循环的下一次迭代. |
| `continue 'label`  | 同上, 但继续的是最近标记有 `'label` 的循环迭代. |
| `x?` | 如果 `x` 是 [Err](https://doc.rust-lang.org/std/result/enum.Result.html#variant.Err) 或 [None](https://doc.rust-lang.org/std/option/enum.Option.html#variant.None), **返回并向上传播**.{{ book(page="ch09-02-recoverable-errors-with-result.html#propagating-errors") }} {{ ex(page="error/result/enter_question_mark.html") }} {{ std(page="std/result/index.html#the-question-mark-operator-") }} {{ ref(page="expressions/operator-expr.html#the-question-mark-operator")}} |
| `x.await` | 仅在 `async` 中可用. yield 当前控制流直到 **`Future`** {{ std(page="std/future/trait.Future.html") }} 或流 `x` 已就绪. {{ ref(page="expressions/await-expr.html#await-expressions") }} {{ edition(ed="'18") }} |
| `return x`  | 从函数中提前返回.然而以表达式结束的方式更惯用. |
| `f()` | 调用 `f`(如函数, 闭包, 函数指针或 `Fn` 等). |
| `x.f()` | 调用成员函数(方法), 要求 `f` 以 `self`, `&self` 等作为第一个参数. |
| {{ tab() }} `X::f(x)` | 同 `x.f()`.除非 `impl Copy for X {}`, 否则 `f` 仅可调用一次. |
| {{ tab() }} `X::f(&x)` | 同 `x.f()`. |
| {{ tab() }} `X::f(&mut x)` | 同 `x.f()`. |
| {{ tab() }} `S::f(&x)` | 同 `x.f()`, 仅当 `X` 实现了对 `S` 的 [Deref](https://doc.rust-lang.org/std/ops/trait.Deref.html).这里 `x.f()` 会去找 `S` 的方法. |
| {{ tab() }} `T::f(&x)` | 同 `x.f()`, 仅当 `X impl T`. 这里 `x.f()` 会去找作用域内 `T` 的方法. |
| `X::f()` | 调用关联函数, 比如 `X::new()`. |
| {{ tab() }} `<X as T>::f()` | 调用为 `X` 实现了的 trait 方法 `T::f(). |

</fixed-2-column>



### 代码组织 {#organizing-code}

将项目分割成更小的单元并最大限度地减少依赖关系. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `mod m {}`  | 定义**模块**{{ book(page="ch07-02-defining-modules-to-control-scope-and-privacy.html") }} {{ ex(page="mod.html#modules") }} {{ ref(page="items/modules.html#modules") }}, 其中的定义在 `{}` 内. {{ below(target="#project-anatomy") }} |
| `mod m;`  | 定义模块, 其中的定义在 `m.rs` 或 `m/mod.rs`. {{ below(target="#project-anatomy") }}|
| `a::b` | 命名空间**路径**{{ ex(page="mod/use.html") }} {{ ref(page="paths.html")}}, 表示 `a`(`mod` 或 `enum` 等) 里面的元素 `b`. |
| {{ tab() }} `::b` | 相对于当前 crate 根下搜索 `b` .{{ deprecated() }} |
| {{ tab() }} `crate::b` | 相对于当前 crate 根下搜索 `b`.{{ edition(ed="'18") }} |
| {{ tab() }} `self::b`  | 相对于当前模块下搜索 `b`. |
| {{ tab() }} `super::b`  | 相对于父级模块下搜索 `b`. |
| `use a::b;`  | **Use** {{ ex(page="mod/use.html#the-use-declaration") }} {{ ref(page="items/use-declarations.html") }} 声明, 将 `b` 直接引入到当前作用域, 以后就不需要再加 `a` 前缀了. |
| `use a::{b, c};` | 同上, 但同时将 `b` 和 `c` 都引入. |
| `use a::b as x;`  | 将 `b` 引入作用域但命名为 `x`. 比如 `use std::error::Error as E`. |
| `use a::b as _;`  | 将 `b` 匿名的引入作用域, 用于含有冲突名称的 trait. |
| `use a::*;`  | 将 `a` 里面的所有元素都引入作用域.仅推荐在 `a` 为 **prelude** 的情况下使用.{{ link(url="https://stackoverflow.com/questions/36384840/what-is-the-prelude" ) }} |
| `pub use a::b;`  | 将 `a::b` 引入作用域, 并再次从当前位置导出. |
| `pub T`  | 控制 `T` 的**可见性** {{ book(page="ch07-02-defining-modules-to-control-scope-and-privacy.html") }}.「如果父级路径公开, 我也公开」. |
| {{ tab() }} `pub(crate) T` | 可见性仅<sup>1</sup>在当前 crate 内. |
| {{ tab() }} `pub(super) T`  | 可见性仅<sup>1</sup>在父级以下.  |
| {{ tab() }} `pub(self) T`  | 可见性仅<sup>1</sup>在当前模块内.  |
| {{ tab() }} `pub(in a::b) T`  | 可见性仅<sup>1</sup>在 `a::b` 内. |
| `extern crate a;` | 声明依赖一个外部 **crate** {{ book(page="ch02-00-guessing-game-tutorial.html#using-a-crate-to-get-more-functionality") }} {{ ex(page="crates/link.html#extern-crate") }} {{ ref(page="items/extern-crates.html#extern-crate-declarations") }} {{ deprecated() }}. 换用 `use a::b` {{ edition(ed="'18") }}.  |
| `extern "C" {}`  | _声明_ **FFI** 的外部依赖和 ABI(如 `"C"`){{ book(page="ch19-01-unsafe-rust.html#using-extern-functions-to-call-external-code") }} {{ ex(page="std_misc/ffi.html#foreign-function-interface") }} {{ nom(page="ffi.html#calling-foreign-functions") }} {{ ref(page="items/external-blocks.html#external-blocks") }}.  |
| `extern "C" fn f() {}`  | _定义_ FFI 导出成 ABI(如 `"C"`)的函数.  |

</fixed-2-column>

<footnotes>

<sup>1</sup> 子模块中的总是可以访问所有项目, 与其是否是 `pub` 无关. 

</footnotes>


### 类型别名和转换 {#type-aliases-and-casts}

类型名称的简写, 以及转为其他类型的方法. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `type T = S;`  | 创建**类型别名**{{ book(page="ch19-04-advanced-types.html#creating-type-synonyms-with-type-aliases") }} {{ ref(page="items/type-aliases.html?highlight=alias#type-aliases") }}. 这里表示 `S` 的另一个名字. |
| `Self`  | **当前实现类型**{{ ref(page="types.html#self-types") }} 的别名. 如 `fn new() -> Self`. |
| `self`  | `fn f(self) {}` 的方法主体. 同 `fn f(self: Self) {}`. |
|  {{ tab() }}  `&self`  | 同上, 但将借用指向自己的引用. 同 `f(self: &Self)`. |
|  {{ tab() }}  `&mut self`  | 同上, 但是可变借用. 同 `f(self: &mut Self)`. |
|  {{ tab() }}  `self: Box<Self>`  | [任意自型](https://github.com/withoutboats/rfcs/blob/arbitray-receivers/text/0000-century-of-the-self-type.md), 为智能指针增加方法 (`my_box.f_of_self()`). |
| `S as T`  | **消歧义**{{ book(page="ch19-03-advanced-traits.html#fully-qualified-syntax-for-disambiguation-calling-methods-with-the-same-name") }} {{ ref(page="expressions/call-expr.html#disambiguating-function-calls") }}, 将类型 `S` 作为 trait `T` 看待. 比如 `<X as T>::f()`. |
| `S as R`  | 在 `use` 里, 将 `S` 导入为 `R`.如 `use a::b as x`. |
| `x as u32`  | 裸**转换**{{ ex(page="types/cast.html#casting") }} {{ ref(page="expressions/operator-expr.html#type-cast-expressions") }}, 会发生截断和一些比特上的意外.<sup>1</sup> {{ nom(page="casts.html") }} |

</fixed-2-column>

<footnotes>

<sup>1</sup> 关于在类型之间转换的所有方法, 请参见下面的[类型转换](#type-conversions). 

</footnotes>



### 宏 & 属性 {#macros-attributes}

实际编译前的代码预展开. 

<fixed-2-column>

| 示例 |  说明 |
|---------|---------|
| `m!()` |  **宏** {{book(page="ch19-06-macros.html")}} {{std(page="std/index.html#macros")}} {{ref(page="macros.html")}} 咒语, 也作 `m!{}`, `m![]` (取决于宏本身)  |
| `#[attr]`  | 外部**属性**{{ex(page="attribute.html")}} {{ref(page="attributes.html")}}, 注解接下来的内容.  |
| `#![attr]` | 内部属性, 注解_上部_, 周边的内容.  |

</fixed-2-column>

{{ tablesep() }}

<fixed-2-column class="color-header special_example">

| 宏内写法 |  说明 |
|---------|---------|
| `$x:ty`  | 宏捕获 (此处表示捕获一个类型), 详见**工具链命令**{{ below(target="#tooling-directives") }}. |
| `$x` |  宏替换, 如使用上面的 `$x:ty` 捕获. |
| `$(x),*` | 宏重复“零次或若干次”. |
| {{ tab() }} `$(x),?` | 宏重复“零次或一次”. |
| {{ tab() }} `$(x),+` | 宏重复“一次或若干次”. |
| {{ tab() }} `$(x)<<+` | 分隔符可以不是逗号“`,`”. 比如这里用 `<<` 作为分割符. |


</fixed-2-column>



### 模式匹配 {#pattern-matching}

函数参数, `match` 或 `let` 表达式中的构造. 


<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `match m {}` | **模式匹配**{{ book(page="ch06-02-match.html") }} {{ ex(page="flow_control/match.html") }} {{ ref(page="expressions/match-expr.html") }}, 下面跟匹配分支. 参见下表. |
| `let S(x) = get();`  | 显然, `let` 也和下表的模式匹配类似. |
|  {{ tab() }} `let S { x } = s;` | 仅将 `x` 绑定到值 `s.x`. |
|  {{ tab() }} `let (_, b, _) = abc;` | 仅将 `b` 绑定到值 `abc.1`. |
|  {{ tab() }} `let (a, ..) = abc;` | 也可以将「剩余的」都忽略掉. |
|  {{ tab() }} `let (.., a, b) = (1, 2);` | 忽略前面「剩余的」, 这里 `a` 是 `1`, `b` 是 `2`. |
|  {{ tab() }} `let s @ S { x } = get();`  | 将 `s` 绑定到 `S` 并将 `x` 绑定到 `s.x`, **模式绑定**, {{ book(page="ch18-03-pattern-syntax.html#-bindings") }} {{ ex(page="flow_control/match/binding.html#binding") }} {{ ref(page="patterns.html#identifier-patterns") }} 见下 {{ esoteric() }} |
|  {{ tab() }} `let w @ t @ f = get();`  | 存储 3 份 `get()` 结果的拷贝分别到 `w`, `t`, `f`. {{ esoteric() }} |
|  {{ tab() }} `let Some(x) = get();` | **不可用**{{ bad() }}, 因为模式可能会**不匹配**{{ ref(page="expressions/if-expr.html#if-let-expressions") }}. 换用 `if let`. |
| `if let Some(x) = get() {}`  | 如果模式匹配则执行该分支(如某个 `enum` 变体). 语法糖<sup>*</sup>.  |
| `while let Some(x) = get() {}`  | 等效; 这里继续调用 `get()`, 只要可以分配模式就运行 `{}`.  |
| `fn f(S { x }: S)`  | 类似于 `let`, 模式匹配也可用在函数参数上. 这里 `f(s)` 的 `x` 被绑定到 `s.x`.{{ esoteric() }}|

</fixed-2-column>


<footnotes>

<sup>*</sup> 展开后是 `match get() { Some(x) => {}, _ => () }`.

</footnotes>



{{ tablesep() }}

`match` 表达式的模式匹配分支. 左列的分支也可用于 `let` 表达式. 

<fixed-2-column class="color-header special_example">

| 匹配分支 | 说明 |
|---------|-------------|
|  `E::A => {}` | 匹配枚举变体 `A`. 参见**模式匹配**.{{ book(page="ch06-02-match.html") }} {{ ex(page="flow_control/match.html") }} {{ ref(page="expressions/match-expr.html") }} |
|  `E::B ( .. ) => {}` | 匹配枚举元组变体 `B`, 通配所有下标. |
|  `E::C { .. } => {}` | 匹配枚举结构变体 `C`, 通配所有字段. |
|  `S { x: 0, y: 1 } => {}` | 匹配含特定值的结构体(仅匹配 `s` 的 `s.x` 为 `0` 且 `s.y` 为 `1` 的情况). |
|  `S { x: a, y: b } => {}` | 匹配为**任意**(!)值的该类型结构体, 并绑定 `s.x` 到 `a`, 绑定 `s.y` 到 `b`. |
|  {{ tab() }} `S { x, y } => {}` | 同上, 但将 `s.x` 和 `s.y` 分别简写地绑定为 `x` 和 `y`. |
|  `S { .. } => {}` | 匹配任意值的该类型结构体. |
|  `D => {}` | 匹配枚举变体 `E::D`.仅当 `D` 已由 `use` 引入. |
|  `D => {}` | 匹配任意事物并绑定到 `D`.如果 `D` 没被 `use` 进来, 怕不是个 `E::D` 的假朋友.{{ bad() }} |
|  `_ => {}` | 通配所有, 或者所有剩下的. |
| <code>0 &vert; 1 => {}</code> | 可选模式列表, **或模式**. {{ rfc( page ="2535-or-patterns.html") }}|
| {{ tab() }}  <code>E::A &vert; E::Z </code> | 同上, 但为枚举变体. |
| {{ tab() }}  <code>E::C {x} &vert; E::D {x}</code> | 同上, 但如果所有变体都有 `x` 则绑定. |
| {{ tab() }}  <code>Some(A &vert; B)</code> | 同上, 可以嵌套匹配. |
|  `(a, 0) => {}` | 匹配元组, 绑定第一个值到 `a`, 要求第二个是 `0`. |
|  `[a, 0] => {}` | **切片模式**{{ ref(page="patterns.html?highlight=slice,pattern#slice-patterns") }} {{ link(url="https://doc.rust-lang.org/edition-guide/rust-2018/slice-patterns.html") }}. 绑定第一个值到 `a`, 要求第二个是 `0`. |
|  {{ tab() }} `[1, ..] => {}` | 匹配以 `1` 开始的数组, 剩下的不管. **子切片模式**.{{ todo() }} |
|  {{ tab() }} `[1, .., 5] => {}` | 匹配以 `1` 开始以 `5` 结束的数组. |
|  {{ tab() }} `[1, x @ .., 5] => {}` | 同上, 但将 `x` 绑定到中间部分的切片上(见匹配绑定)  |
|  {{ tab() }} `[a, x @ .., b] => {}` | 同上, 但可以指定任意上下界 `a`, `b`.  |
|  `1 .. 3 => {}` | **范围模式**, {{ book(page="ch18-03-pattern-syntax.html#matching-ranges-of-values-with-") }} {{ ref(page="patterns.html#range-patterns") }} 这里匹配 `1` 和 `2`. 尚不稳定. {{ experimental() }} |
|  {{ tab() }} `1 ..= 3 => {}` | 闭区间范围模式, 匹配 `1`, `2` 和 `3`. |
|  {{ tab() }} `1 .. => {}` | 开区间范围模式, 匹配 `1` 和更大的数字.  |
| `x @ 1..=5 => {}` | 绑定匹配到 `x`, 即**模式绑定**{{ book(page="ch18-03-pattern-syntax.html#-bindings") }} {{ ex(page="flow_control/match/binding.html#binding") }} {{ ref(page="patterns.html#identifier-patterns") }}. 这里 `x` 可以是 `1`, `2` 直到 `5`.  |
| {{ tab() }} `Err(x @ Error {..}) => {}` | 嵌套使用, 这里 `x` 绑定到 `Error`, 下常跟 `if`. |
| `S { x } if x > 10 => {}`  | 模式**匹配条件**{{ book(page="ch18-03-pattern-syntax.html#extra-conditionals-with-match-guards")}} {{ ex(page="flow_control/match/guard.html#guards")}} {{ ref(page="expressions/match-expr.html#match-guards") }}. 该匹配会要求这个条件也为真. |

</fixed-2-column>



<!-- This is more relevant for let D = ... cases, https://www.reddit.com/r/rust/comments/a1846o/rust_quiz_26_medium_to_hard_rust_questions_with/eaop291/ -->
<!-- |  `D => {}` | Match struct if `D` unit `struct D;`| -->



### 泛型 & 约束 {#generics-constraints}

泛型使得类型构造, trait 和函数更加可扩展. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `S<T>`  | **泛型**{{ book(page="ch10-01-syntax.html") }} {{ ex(page="generics.html") }}, 类型参数 `T` 是占位符. |
| `S<T: R>`  | 类型短 **trait 约束**{{ book(page="ch10-02-traits.html#using-trait-bounds-to-conditionally-implement-methods") }} {{ ex(page="generics/bounds.html") }}说明. (`R` _必须_ 是个实际的 trait). |
| {{ tab() }} `T: R, P: S`  | **独立 trait 约束**(这里一个对 `T`, 一个对 `P`). |
| {{ tab() }} `T: R, S`  | 编译错误{{ bad() }}. 可以用下面的 `R + S` 代替. |
| {{ tab() }} `T: R + S`  | **合并 trait 约束**{{ book(page="ch10-02-traits.html#specifying-multiple-trait-bounds-with-the--syntax") }} {{ ex(page="generics/multi_bounds.html") }}. `T` 必须同时满足 `R` 和 `S`. |
| {{ tab() }} `T: R + 'a`  | 同上, 但有生命周期. `T` 必须满足 `R`; 如果 `T` 有生命周期, 则必须长于 `'a`. |
| {{ tab() }} `T: ?Sized` | 指定一个预定义的 trait 绑定, 如这里是 `Sized`. {{ todo() }} |
| {{ tab() }} `T: 'a` | 类型**生命周期约束**{{ ex(page="scope/lifetime/lifetime_bounds.html") }}. `T` 应长于 `'a`. |
| {{ tab() }} `T: 'static` | 同上. 但 _不_ 意味着值 `t` _会_ {{ bad() }} 活在 `'static` 上, 仅在它可以的时候才行. |
| {{ tab() }} `'b: 'a` | 生命周期 `'b` 必须至少活得和 `'a` 一样长. |
| `S<const N: usize>` | **泛型常量绑定**. {{ todo() }} 使用类型 `S` 可提供常量值 `N`. |
| {{ tab() }} `S<10>` | 可以指定字面量. |
| {{ tab() }} `S<{5+5}>` | 表达式需要用花括号包起来. |
| `S<T> where T: R`  | 几乎等同于 `S<T: R>`, 但对于比较长的约束更容易阅读. |
| {{ tab() }} `S<T> where u8: R<T>`  | 还允许您创建涉及其他类型的条件语句.  |
| `S<T = R>` | **默认参数**. {{ book(page="ch19-03-advanced-traits.html#default-generic-type-parameters-and-operator-overloading") }} 保持扩展性的同时更易于使用. |
| {{ tab() }} `S<const N: u8 = 0>` | 常量默认参数. 如 `f(x: S) {}` 中参数 `N` 为 `0`. |
| {{ tab() }} `S<T = u8>` | 类型默认参数. 如 `f(x: S) {}` 中参数 `T` 为 `u8`. |
| `S<'_>` | 推断**匿名生命周期**. 让编译器 _“想办法”_ 明确生命周期.  |
| `S<_>` | 推断**匿名类型**. 比如 `let x: Vec<_> = iter.collect()`  |
| `S::<T>` | **Turbofish**{{ std(page="std/iter/trait.Iterator.html#method.collect")}} 消歧义类型调用. 如 `f::<u32>()` |
| `trait T<X> {}`  | `X` 的 trait 泛型.可以有多个 `impl T for S`(每个 `X` 一个). |
| `trait T { type X; }`  | 定义**关联类型**{{ book(page="ch19-03-advanced-traits.html#specifying-placeholder-types-in-trait-definitions-with-associated-types") }} {{ ref(page="items/associated-items.html#associated-types") }} `X`. 仅可有一个 `impl T for S` . |
| {{ tab() }} `type X = R;`  | 设置关联类型. 仅在 `impl T for S { type X = R; }` 内. |
| `impl<T> S<T> {}`  | 实现 `S<T>` 任意类型 `T` 的功能. |
| `impl S<T> {}`  | 实现确定 `S<T>` 的功能. 如 `S<u32>`. |
| `fn f() -> impl T`  | **Existential 类型** {{ book(page="ch10-02-traits.html#returning-types-that-implement-traits") }}. 返回一个对调用者未知的但 `impl T`的 `S`. |
| `fn f(x: &impl T)`  | Trait 约束, 「**impl trait**」{{ book(page="ch10-02-traits.html#trait-bound-syntax") }}.和 `fn f<S:T>(x: &S)` 有点类似. |
| `fn f(x: &dyn T)`  | **动态分发**标记{{ book(page="ch17-02-trait-objects.html#using-trait-objects-that-allow-for-values-of-different-types") }} {{ ref(page="types.html#trait-objects") }}. `f` 不再单态. |
| `fn f() where Self: R`  | 在 `trait T {}` 中标记 `f` 仅可由实现了 `impl R` 的类型访问. |
| {{ tab() }} `fn f() where Self: Sized;`  | 使用 `Sized` 可以指定 `f` 对于 `dyn T` 的 trait 对象对应的虚表. |
| {{ tab() }} `fn f() where Self: R {}`  | Other `R` useful w. dflt. methods (non dflt. would need be impl'ed anyway). |
</fixed-2-column>



### 高阶项目 {{ esoteric() }} {#higher-ranked-items}

_实际的_ 类型和 trait, 某些事物的抽象以及常用生命周期. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `for<'a>` | **高阶绑定**{{ nom(page="hrtb.html")}} {{ ref(page="trait-bounds.html#higher-ranked-trait-bounds")}}表记. {{ esoteric() }} |
| {{ tab() }} `trait T: for<'a> R<'a> {}` | 在任意生命周期下, 任意实现了 `impl T` 的 `S` 都应满足 `R`. |
| `fn(&'a u8)` | _函数指针_ 类型, 持有可调用 fn 以及**指定的**生命周期 `'a`. |
| `for<'a> fn(&'a u8)` | **高阶类型**<sup>1</sup> {{ link(url="https://github.com/rust-lang/rust/issues/56105") }} 持有可调用 fn  **任意** _小于_ 上述生命周期的参数; 上面的子类型. |
| {{ tab() }} `fn(&'_ u8)` | 同上, 自动展开为类型 `for<'a> fn(&'a u8)`. |
| {{ tab() }} `fn(&u8)` | 同上, 自动展开为类型 `for<'a> fn(&'a u8)`. |
| `dyn for<'a> Fn(&'a u8)` | 高阶 (trait 对象) 类型, 行为如上 `fn`. |
| {{ tab() }} `dyn Fn(&'_ u8)` | 同上, 自动展开为类型 `dyn for<'a> Fn(&'a u8)`. |
| {{ tab() }} `dyn Fn(&u8)` | 同上, 自动展开为类型 `dyn for<'a> Fn(&'a u8)`. |

<footnotes>

 <sup>1</sup> 没错, `for<>` 是类型的一部分, 这会导致你下面会写出来 `impl T for for<'a> fn(&'a u8)` 这样的代码.

</footnotes>

</fixed-2-column>


<div class="color-header special_example">
{{ tablesep() }}

| Trait 实现 | 说明 |
|---------|-------------|
| `impl<'a> T for fn(&'a u8) {}` | For fn 指针, 调用接受**指定** _小于_ `'a` 的参数, impl trait `T`.|
| `impl T for for<'a> fn(&'a u8) {}` | For fn 指针, 调用接受**任意** _小于_ 的参数, impl trait `T`. |
| {{ tab() }} `impl T for fn(&u8) {}` | 同上, 简写. |

</div>


### 字符串 & 字符 {#strings-chars}

Rust 提供了若干种创建字符串和字符字面量的办法. 


<fixed-2-column>

| 示例 | 说明 |
|--------|-------------|
| `"..."` | UTF-8 **字符串字面量**{{ ref(page="tokens.html#string-literals")}}<sup>, 1</sup>.会将 `\n` 等看作换行 `0xA` 等. |
| `r"..."` | UTF-8 **裸字符串字面量**{{ ref(page="tokens.html#raw-string-literals")}}<sup>, 1</sup>. 不会处理 `\n` 等. |
| `r#"..."#` 等 | UTF-8 裸字符串字面量. 但可以包含 `"`. |
| `b"..."` | **字节串字面量**{{ ref(page="tokens.html#byte-and-byte-string-literals")}}<sup>, 1</sup>, 由 ASCII `[u8]` 组成. 并不是字 _符_ 串. |
| `br"..."`, `br#"..."#` 等 | 裸字节串字面量, ASCII `[u8]`. 说明见上. |
| `'🦀'` | **字符字面量**{{ ref(page="tokens.html#character-and-string-literals")}}, 固定的 4 字节 Unicode '**字符**'.{{ std(page="std/primitive.char.html") }} |
| `b'x'` | ASCII **字节字面量**.{{ ref(page="tokens.html#byte-literals")}} |

</fixed-2-column>

<footnotes>

<sup>1</sup> 均支持多行字符串. 但要注意 `Debug`{{ below(target="#string-output") }} (例如 `dbg!(x)` 和 `println!("{x:?}")`) 会将换行符渲染成 `\n`, 而 `Display`{{ below(target="#string-output") }} (例如 `println!("{x}")`) 则会输出换行.

</footnotes>


### 文档 {#documentation}

调试器的天敌. 这玩意儿能避免 Bug.


<fixed-2-column>

| 示例 | 说明 |
|--------|-------------|
| `///` | 外部行级**文档注释**, {{ book(page="ch14-02-publishing-to-crates-io.html#making-useful-documentation-comments") }} {{ ex(page="meta/doc.html#documentation") }} {{ ref(page="comments.html#doc-comments")}} 用于类型, trait, 函数等. |
| `//!` | 内部行级文档注释, 多用于文档模块的文件头部. |
| `//` | 行内注释. 用于文档代码流内或 _内部组件_. |
| `/*...*/` | 块级注释. |
| `/**...*/` | 外部块级文档注释. |
| `/*!...*/` | 内部块级文档注释. |

</fixed-2-column>

<footnotes>

工具链命令{{ below(target="#tooling-directives") }}告诉你可以在文档注释中做什么.

</footnotes>



### 杂项 {#miscellaneous}

这些小技巧不属于其他分类但最好了解一下. 

<fixed-2-column>

| 示例 | 说明 |
|---------|-------------|
| `!` | 永远为空的 **never 类型**.{{ experimental() }} {{ book(page="ch19-04-advanced-types.html#the-never-type-that-never-returns") }} {{ ex(page="fn/diverging.html#diverging-functions") }} {{ std(page="std/primitive.never.html") }} {{ ref(page="types.html#never-type") }} |
| `_` | 无名变量绑定.如 <code>&vert;x, _&vert; {}</code>.|
| {{ tab() }} `let _ = x;`  | 匿名赋值等于无操作 (no-op), **不会**{{ bad() }}将 `x` 移出当前作用域! |
| `_x` | 变量绑定, 明确标记该变量未使用. |
| `1_234_567` | 为了易读加入的数字分隔符. |
| `1_u8` | **数字字面量**的类型说明符.{{ ex(page="types/literals.html#literals") }} {{ ref(page="tokens.html#number-literals") }} (又见 `i8`, `u16`等). |
| `0xBEEF`, `0o777`, `0b1001`  | 十六进制(`0x`), 八进制(`0o`)和二进制(`0b`) 整型字面量. |
| `r#foo` | **原始标识符** {{ book(page="appendix-01-keywords.html#raw-identifiers") }} {{ ex(page="compatibility/raw_identifiers.html#raw-identifiers") }}. 用于版本兼容. {{ esoteric() }} |
| `x;` | **语句**{{ ref(page="statements.html")}}终止符. 见**表达式**{{ ex(page="expression.html") }} {{ ref(page="expressions.html")}}. |

</fixed-2-column>




### 通用运算符 {#common-operators}

Rust 支持大部分其他语言也有的通用操作符(`+`, `*`, `%`, `=`, `==`...). 因为这在 Rust 里没什么太大差别所以这里不列出来了. Rust 也支持**运算符重载**.{{ std(page="std/ops/index.html")}}


---

<magic>

# 增强设施

可能会导致你的脑子爆炸的神秘知识点, 超级推荐.
## 抽象层 {#the-abstract-machine}

同 `C`/`C++`, Rust 基于一个 _抽象层_.


<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-abstract-machine-1" name="tab-group-abstract-machine" checked>
<label for="tab-abstract-machine-1"><b>概览</b></label>
<panel><div>


<div style="text-align: center;">

<mini-zoo class="zoo" style="text-align: center;">
    <entry>
        <machine class="bad">Rust</machine>
    </entry>
    <code style="text-align:center;">→</code>
    <entry>
        <machine class="bad">CPU</machine>
    </entry>
    <br/>
    <note>{{bad()}} 不太优雅</note>
</mini-zoo>

<mini-zoo class="zoo" style="text-align: center; margin-left: 80px;">
    <entry>
        <machine class="good">Rust</machine>
    </entry>
    <code style="text-align:center">→</code>
    <entry style="width: 120px;">
        <machine class="good">抽象层</machine>
    </entry>
    <code style="text-align:center">→</code>
    <entry>
        <machine class="good">CPU</machine>
    </entry>
    <br/>
    <note>优雅</note>
</mini-zoo>

</div>


{{ tablesep() }}


抽象层 (AM)
- 并非运行时, 并不会有任何运行时开销, 但它是一个 _计算模型的抽象_,
- 包含如内存分配(_栈_, ...)和运行语义等概念,
- _了解_ 和 _看到_ 你 CPU 并不关心的东西,
- 构建了程序员到机器之间的一道契约,
- 并且**综合上述内容进行优化**.


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-abstract-machine-2" name="tab-group-abstract-machine">
<label for="tab-abstract-machine-2"><b>杂项</b></label>
<panel><div>

<div class="color-header abstract-machine">

如果 Rust 直接发送给 CPU, 人们可能会错误地认为他们 _应该逃脱惩罚_ , 然而 _更加正确_ 的做法是:

{{ tablesep() }}

| 无抽象层 | 有抽象层 |
|---------|-------------|
| `0xffff_ffff` 会产生一个有效的 `char`. {{ bad() }} | 只是内存中的一段比特.  |
| `0xff` 和 `0xff` 是相同的指针. {{ bad() }} | 指针可以来自不同的 _域_.  |
| 在 `0xff` 的任意读写都是可行的. {{ bad() }} | 不能同时读写同一引用.  |
| 某些寄存器直接把 `0x0` 当做 null. {{ bad() }} | 在引用中保存 `0x0` 简直是克苏鲁.  |

</div>
</div></panel></tab>


</tabs>

<!--  -->
<!-- > Practically this means: -->
<!-- > - before assuming your **CPU** will do `A` when writing `B` you need positive proof **via documentation**(!), -->
<!-- > - if you don't have that any physical behavior is _coincidental_, -->
<!-- > - violate the abtract machine's contract and the optimizer makes your CPU do something **entirely else** &mdash; **undefined behavior**.{{ below(target="#unsafe-unsound-undefined")}} -->
<!--  -->


## 语法糖 {#language-sugar}

如果有什么东西让你觉得, “不该能用的啊”, 那可能就是这里的原因. 



<div class="color-header language-sugar">


| 名称 | 说明 |
|--------| -----------|
| **强转** {{ nom(page="coercions.html") }} | _隐式转换_ 类型以匹配签名, 如 `&mut T` 转为 `&T`. 见 _类型转换_. {{ below(target="#type-conversions") }}  |
| **解引用** {{ nom(page="vec-deref.html") }} {{ link(url="https://stackoverflow.com/questions/28519997/what-are-rusts-exact-auto-dereferencing-rules") }} | 连续[解引用](https://doc.rust-lang.org/std/ops/trait.Deref.html) `x: T` 直到 `*x`, `**x`, &hellip; 满足目标类型 `S`. |
| **Prelude** {{ std(page="std/prelude/index.html") }} | 自动导入基本项目, 如 `Option`, `drop`, ...
| **重新借用** | 即便 `x: &mut T` 不能复制, 也可以移动一个新的 `&mut *x` 代替. |
| **生命周期省略** {{ book(page="ch10-03-lifetime-syntax.html#lifetime-elision") }} {{ nom(page="lifetime-elision.html#lifetime-elision") }} {{ ref(page="lifetime-elision.html#lifetime-elision") }} | 自动将 `f(x: &T)` 标注为 `f<'a>(x: &'a T)`.|
| **方法重解析** {{ ref(page="expressions/method-call-expr.html") }} | 解引用或借用 `x` 直到 `x.f()` 可用. |
| **匹配引用简写** {{ rfc(page="2005-match-ergonomics.html") }} | 重复应用解引用到各个[选择肢](https://doc.rust-lang.org/stable/reference/glossary.html#scrutinee)上并添加 `ref` 和 `ref mut` 到绑定. |
| **右值静态提升** {{ rfc(page="1414-rvalue_static_promotion.html") }} | 使引用满足 `'static`, 如 `&42`, `&None`, `&mut []`. |


</div>

{{ tablesep() }}

> **作者按** {{ opinionated() }} &mdash; 上述功能会让你活得轻松些, 但却会扰乱你的理解. 如果任意有类型相关的操作让你觉得 _有些反常_, 那可能就是这里的语法糖在作怪了.

## 内存和生命周期 {#memory-lifetimes}


移动, 引用和生命周期到底是咋回事.


<tabs class="lifetimes">

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-1" name="tab-lt" checked>
<label for="tab-lt-1"><b>类型 & 移动</b></label>
<panel>
<div>


<lifetime-section>
<lifetime-example>
    <section-header>应用程序内存</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">S(1)</value>
        </values>
        <labels>
            <label class="" style="right: 10px;">&nbsp;</label>
        </labels>
        <subtext>应用程序内存</subtext>
    </memory-row>
</lifetime-example>
<explanation>

- 应用程序内存在底层就是一个字节数组.
- 操作系统经常将其划分为若干分区:
    - **栈区** (空间小, 低成本内存,<sup>1</sup> 多数 _变量_ 都在这里),
    - **堆区** (空间大, 可扩展内存, 但总会由类似 `Box<T>` 的栈代理来指向),
    - **静态区** (多用于存储组成 `&str` 的字符串 `str`),
    - **代码区** (你的函数二进制代码的存储区域).
- 这里面最富挑战的莫过于**栈的增长**, 这是我们关注的**重点**.

<footnotes>

<sup>1</sup> 对于固定大小的值, 栈的管理非常细致: _你需要的时候马上生成, 不需要的时候马上离开_. 然而这些 _短暂_ 分配的指针却是导致生命周期存在的 _本质_ 原因, 也是主导了本章后续所有内容.

</footnotes>

</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <section-header>变量</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">S(1)</value>
            <value class="t byte2" style="left: 97.5px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>t</code></label>
        </labels>
        <subtext>变量</subtext>
        <!-- <subtext><code>let t = S(1);</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let t = S(1);
```

- 分配内存空间, 名为 `t`, 类型为 `S`, 里面存储的值为 `S(1)`.
- 如果声明了 `let` 那空间将会分配在栈上. <sup>1</sup>
- 注意**语义歧义**,<sup>2</sup> 术语**变量**可能指的是:
    1. 源文件中定义的**名称** (“重命名某变量”),
    1. 已编译程序中的**位置**, `0x7` (“告诉我某变量的地址”),
    1. 里面包含的**值**, `S(1)` (“增加某变量”).
- 特别地, 对于编译器来说 `t` 指的是 `t` 的**位置** (这里是 `0x7`) 和 `t` 里面的 **值** (这里是 `S(1)`).

<footnotes>

<sup>1</sup> 上述{{ above(target="#data-structures" ) }}比较中仅针对于同步代码, 而 `async` 异步栈帧有可能被运行时放在堆上.

</footnotes>


</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <section-header>移动语义</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>t</code></label>
        </labels>
        <subtext>移动</subtext>
        <!-- <subtext><code>let a = t;</code></subtext> -->
    </memory-row>
</lifetime-example>

<explanation>

```
let a = t;
```

- 操作将**移动** `t` 里面的值到 `a` 的位置, 如果 `S` 是可 `Copy` 的则复制一份.
- `t` 的位置移动后将会**失效**且不能再被读取.
    - 技术上该位置的比特位并非完全置为 _空_, 但 _未定义_.
    - 如果你仍然通过 `unsafe` 访问 `t` 的话它仍有可能 _看起来_ 像是个有效的 `S`, 
    但任何把它当成有效 `S` 的操作都是未定义行为 (UB). {{ below(target="#unsafe-unsound-undefined") }}
- 这里没有提到 `Copy` 的影响, 虽然它会轻微影响上述规则:
    - 它们不会被析构.
    - '空'变量的位置永远不会离开作用域.

</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <section-header>类型安全</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <failed style="left: 231.5px;"><value class="atomic byte4">M { ... }</value></failed>
            <denied style="left: 141px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code></code></label>
            <label class="byte2" style="left: 170px;"><code>c</code></label>
        </labels>
        <subtext>类型安全</subtext>
        <!-- <subtext><code>let c: S = M::new();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>


```
let c: S = M::new();
```

- **变量的类型**指出了许多重要的期望, 它:
    1. 规定了如何解释底层的比特位,
    1. 仅允许被友好定义的操作去操作这些比特位,
    1. 防止其他随机变量或比特写到这个位置.
- 这里赋值语句将会编译失败, 因为 `M::new()` 的字节无法被有效地转换为 `S` 类型.
- **类型之间的直接转换 _总会_ 失败.** 但通常**允许某些例外** (强转或 `as` 转换等).

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <section-header>域 & 析构</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <drop><value class="t byte2" style="left: 57px;">S(1)</value><droparrow style="left:37px;">▼</droparrow></drop>
            <value class="t byte2 hide" style="left: 87.5px;">C(2)</value>
            <drop><value class="t byte2" style="left: 128px;">S(2)</value><droparrow style="left:107px;">▼</droparrow></drop>
            <failed style="left: -27.5px;"><value class="t byte2" style="left: 128px;">S(3)</value></failed>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code></code></label>
            <label class="byte2" style="left: 97.5px;"><code>t</code></label>
            <!-- <label class="byte2" style="left: 136.5px;"><code>c</code></label> -->
        </labels>
        <subtext>作用域 & 析构</subtext>
        <!-- <subtext><code>{ let a = ...; }</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
{
    let mut c = S(2);
    c = S(3);  // <- 赋值前将会对 `c` 进行析构.
    let t = S(1);
    let a = t;
}   // <- 这里退出了 `a`, `t`, `c` 的作用域, 将调用 `a`, `c` 的析构方法.
```

- 一旦一个未腾出空间的“变量名”离开其**作用域**, 其包含的值将被**析构**.
    - 首要规则: 当变量名离开其定义的 `{}` 块时执行,
    - 临时变量等尤为如此.
- 当新值赋值给已有变量位置时也会触发析构.
- 当调用了值对应位置的 **`Drop::drop()`** 时.
    - 上例中 `drop()` 在 `a` 上调用了一次, 在 `c` 上调用了两次, 但没有在 `t` 上调用过.
- 多数非 `Copy` 的值都在此时发生析构, 除非使用了 `mem::forget()`, `Rc` 之类或者 `abort()`.

</explanation>
</lifetime-section>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-2" name="tab-lt">
<label for="tab-lt-2"><b>调用栈</b></label>
<panel><div>

<lifetime-section>
<lifetime-example>
    <section-header>栈帧</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>x</code></label>
        </labels>
        <subtext>函数边界</subtext>
        <!-- <subtext><code>fn f(x: S) {}</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: S) { ... }

let a = S(1); // <- 在这里
f(a);
```

- 当**函数被调用**, 参数和返回值的内存将会保存在栈上.<sup>1</sup>
- 这里当调用 `f` 之前, `a` 中的值将会移动到“商量”好的栈位置, 当 `f` 执行时作为“局部变量” `x`.

<footnotes>

<sup>1</sup> 实际的位置取决于调用时的转换, 可能根本不会分配在栈上, 但这不影响此处的心智模型.

</footnotes>

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 131px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>x</code></label>
            <label class="byte2" style="left: 136px;"><code>x</code></label>
        </labels>
        <subtext>嵌套函数</subtext>
        <!-- <subtext><code>fn f(x: S) { ... f(x)... }</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: S) {
    if once() { f(x) } // <- 递归前在这里
}

let a = S(1);
f(a);
```

- 函数的**递归调用**, 或由其他函数调用, 都将会扩展栈帧.
- 过多的嵌套调用 (比如无限递归) 会使得栈不断增长, 以至于溢出并导致程序终止.

</explanation>
</lifetime-section>


<lifetime-section>

<lifetime-example class="not-first">
    <section-header>变量有效性</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t" style="opacity: 0.4;"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 131px;">S(1)</value>
            <value class="atomic byte4" style="left: 190px;">M { }</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>x</code></label>
            <label class="byte2" style="left: 174px;"><code>m</code></label>
        </labels>
        <subtext>内存重定义</subtext>
        <!-- <subtext><code>f(x); let m = M::new();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: S) {
    if once() { f(x) }
    let m = M::new() // <- 递归后在这里
}

let a = S(1);
f(a);
```

- 之前保有确定类型的栈将由函数或内部函数重新定义此处的用途.
- 这里 `f` 的递归产生的第二个 `x`, 将会在后续的递归里由 `m` 重新利用.

> 关键点在于, 有很多种方法来保证之前保有一个确定类型有效值内存位置在此期间不被使用.
> 简单来说就是实现了指针.

</explanation>
</lifetime-section>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-3" name="tab-lt">
<label for="tab-lt-3"><b>引用 & 指针</b></label>
<panel><div>

<lifetime-section>
<lifetime-example>
    <section-header class="arrowed">引用类型</section-header>
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(1)</value>
            <value class="ptr byte4" style="left: 171px;">0x3</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte4" style="left: 171px;"><code>r</code></label>
        </labels>
        <subtext>引用作为指针</subtext>
        <!-- <subtext><code>let r = &mut a;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let a = S(1);
let r: &S = &a;
```

- 类似 `&S` 或 `&mut S` 这样的**引用类型**持有某个 `s` 的**位置**.
- 这里类型 `&S` 绑定到了名称 `r`, 持有变量 `a` (`0x3`) 的 _位置_, 它的类型为 `S`, 通过 `&a` 获取.
- 如果你将变量 `c` 视为 _指定位置_, 引用 **`r` 就是 _位置的接入点_**.
- 引用的类型与其他类型类似, 通常可以被推断出来, 所以可以省略不写:
    ```
    let r: &S = &a;
    let r = &a;
    ```
<!-- - References on their own are **never** concerned with the _value within_ the location they point to. -->

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <section-header class="arrowed">(可变) 引用</section-header>
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(2)</value>
            <value class="ptr byte4" style="left: 171px;">0x3</value>
            <value class="t byte2" style="left: 213px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte4" style="left: 171px;"><code>r</code></label>
            <label class="byte4" style="left: 193px;"><code>d</code></label>
        </labels>
        <subtext>访问共享内存</subtext>
        <!-- <subtext><code>let d = r.clone(); *r = S(2);</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let mut a = S(1);
let r = &mut a;
let d = r.clone();  // 从 r 指向目标克隆或拷贝.
*r = S(2);          // 将 r 指向目标设置为新值 S.
```


- 引用可以**读取自**  (`&S`) 或**写入到** (`&mut S`) 它们指向的位置.
- *解引用* `*r` 表示既不使用 `r` 的 _位置_ 也不使用其包含的 _值_, 而是使用**位置 `r` 指向的目标**.
- 上例中, 克隆 `d` 是由 `*r` 创建的, 并且 `S(2)` 写入到了 `*r`.
    - 方法 `Clone::clone(&T)` 期望传入其自身的引用, 这就是我们使用 `r` 而非 `*r` 的原因.
    - 赋值语句 `*r = ...` 中的旧值也会被析构 (图中未说明).

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">S(2)</value>
            <value class="ptr byte4" style="left: 171px;">0x3</value>
            <value class="atomic byte4" style="top:-36px; left: 20px;">M { x }</value>
            <denied style="left: -71px; top:-36px;">⛔</denied>
            <denied style="left: -131px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte4" style="left: 171px;"><code>r</code></label>
            <label class="byte4" style="left: 193px;"><code>d</code></label>
        </labels>
        <subtext>引用对象保护</subtext>
        <!-- <subtext><code>let d = *r; *r = M::new();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let mut a = ...;
let r = &mut a;
let d = *r;       // 无法移出值, 否则 `a` 将为空.
*r = M::new();    // 无法存储非 S 类型值, 毫无意义.
```

- 当绑定保证总是 _持有_ 有效值时, 引用也总是保证一定 _指向_ 有效数据.
- 特别是 `&mut T` 必须和变量一样提供保证, 要知道它们并不能让指向的目标消失:
    - **不允许写无效**数据.
    - **不允许移出**数据 (否则会留下一个不知道所有者的空目标).

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px; border-color: red;">&nbsp;<tip style="color: red">▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">C(2)</value>
            <value class="ptr byte4 unsafe" style="left: 171px;">0x3</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 57px;"><code>c</code></label>
            <label class="byte4" style="left: 171px;"><code>p</code></label>
        </labels>
        <subtext>裸指针</subtext>
        <!-- <subtext><code>let p: *const S = ...;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let p: *const S = questionable_origin();
```

- 与引用不同, 指针不提供任何保证.
- 指针有可能指向无效数据或者不存在的数据.
- 解引用指针是 `unsafe` 的, 将无效的 `*p` 作为有效值来操作是未定义行为 (UB). {{ below(target="#unsafe-unsound-undefined") }}

</explanation>
</lifetime-section>

</div></panel></tab>




<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-10" name="tab-lt">
<label for="tab-lt-10"><b>生命周期</b></label>
<panel><div>


<lifetime-section>
<lifetime-example>
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">C(2)</value>
            <value class="ptr byte4 hide" style="left: 171px;">0x3</value>
        </values>
        <labels>
            <!-- <label class="byte2" style="left: 37px;"><code>'a</code></label>
            <label class="byte4" style="left: 59px;"><code>'b: 'c</code></label>
            <label class="byte2" style="left: 81px;"><code>'c</code></label>
            <label class="byte4" style="left: 139px;"><code>'d</code></label> -->
        </labels>
        <subtext>事物的“生命周期”</subtext>
        <!-- <subtext><code>f(); g(); h();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

- 程序中的每个实体都有其相关的临时或者长期的空间, 即 _生存_.
- 宽松地说, _生存时间_ 可以是<sup>1</sup>
    1. **项目可用**的**代码行** (LOC). (如模块名).
    1. 从 _位置_ 的**初始化**到位置被**丢弃**之间的**代码行**.
    1. 从位置第一次**确定性使用**到**停止使用**之间的**代码行**.
    1. 从创建 _值_ 到该值被析构之间的**代码行 (或实际时间)**.
- 本节剩余部分会将上面的项目分别称为:
    1. 项目**作用域**, 不重要.
    1. 变量或位置的**作用域**.
    1. 用法的**生命周期**<sup>2</sup>.
    1. 值的**生命周期**, 当和文件描述符打交道时非常有用, 但这里也不重要.
- 同样地, 代码中的生命周期参数 `r: &'a S`
    - 任意**位置 r _指向_** 的代码行导致的未确定态都要求可访问或被锁定;
    - 与 `r` 本身作为代码行的“存在时间”并无关联 (它只要存在得更短就行了).
- `&'static S` 意味着地址必须 _在所有代码行中有效_.

> <sup>1</sup> 文档中的 _作用域_ 和 _生命周期_ 有时存在歧义.
> 这里尝试作一定的区分, 但如果有更好的意见也欢迎提出.
>
> <sup>2</sup> _生存行_ 可能是个更好的说法...

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 192px; width: 120px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2 hide" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">0xa</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 37px;"><code>a</code></label>
            <label class="byte2 hide" style="left: 78px;"><code>b</code></label>
            <label class="byte2" style="left: 118px;"><code>c</code></label>
            <label class="byte4" style="left: 177px;"><code>r</code></label>
        </labels>
        <subtext><code>r: &'c S</code> 的含义</subtext>
        <!-- <subtext><code>r: &mut 'c S</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

- 假设你从哪里看到 `r: &'c S`, 它表示:
    - `r` 持有某个 `S` 的地址,
    - `r` 指向的任意地址会至少存在在 `'c` 期间,
    - 变量 `r` 本身不能活得比 `'c` 长.



</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 118px; width: 193px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">S(3)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">0x6</value>
            <denied style="left: -125px; top:-25px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte2" style="left: 78px;"><code>b</code></label>
            <label class="byte2" style="left: 118px;"><code>c</code></label>
            <label class="byte4" style="left: 177px;"><code>r</code></label>
        </labels>
        <subtext>生命周期与类型的相似性</subtext>
        <!-- <subtext><code>r = &mut b;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
{
    let b = S(3);
    {
        let c = S(2);
        let r: &'c S = &c;      // 不能如愿运行
        {                       // 因为函数体中的局部变量无法命名生命周期
            let a = S(0);       // 函数中的规则也类似

            r = &a;             // `a` 的位置在很多行都不存在 -> 不行.
            r = &b;             // `b` 的位置活在比 `c` 更大的范围 -> 可以.
        }
    }
}
```

- 假设你在哪里看到了 `mut r: &mut 'c S`.
    - 它表示一个可以持有一个可变引用的可变地址.
- 如上述, 引用必须保证目标内存有效.
- **`'c` 部分**和类型一样**限制了赋值到 `r` 的操作**.
- 将 `&b` (`0x6`) 赋值到 `r` 是有效的, 但 `&a` (`0x3`) 无效, 就因为 `&b` 生存时间大于等于 `&c`.

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 118px; width: 193px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">&nbsp;</value>
            <value class="t byte2 hide" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">0x6</value>
            <failed style="left: -40px;"><value class="t bytes">S(4)</value></failed>
            <denied style="left: -83px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 37px;"><code>a</code></label>
            <label class="byte2" style="left: 78px;"><code>b</code></label>
            <label class="byte2 hide" style="left: 118px;"><code>c</code></label>
            <label class="byte4 hide" style="left: 177px;"><code></code></label>
        </labels>
        <subtext>借用态</subtext>
    </memory-row>
</lifetime-example>
<explanation>

```
let mut b = S(0);
let r = &mut b;

b = S(4);   // 无效. 因为 `b` 处于借用态.

print_byte(r);
```

- 一旦变量地址被 `&b` 或 `&mut b` 捕获, 变量就会被标记为**已借用**.
- 借用时, 就不能再通过原始绑定 `b` 修改地址的内容.
- 一旦捕获了地址的 `&b` 或 `&mut b` 在上下文中不再使用, 原始绑定 `b` 将会恢复可用.


</explanation>
</lifetime-section>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-11" name="tab-lt">
<label for="tab-lt-11"><b>函数中的生命周期</b></label>
<panel>
<div>


<lifetime-section>
<lifetime-example>
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">?</value>
            <value class="ptr byte4" style="left: 201px;">0x6</value>
            <value class="ptr byte4" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 37px;"><code>a</code></label>
            <label class="byte4" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4" style="left: 139px;"><code>r</code></label>
            <label class="byte4" style="left: 165px;"><code>x</code></label>
            <label class="byte4" style="left: 188px;"><code>y</code></label>
        </labels>
        <subtext>函数参数</subtext>
        <!-- <subtext><code>let r = f(&b, &c);</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: &S, y:&S) -> &u8 { ... }

let b = S(1);
let c = S(2);

let r = f(&b, &c);
```

- 调用函数时会捕获返回的引用, 这里将会发生两件趣事:
    - 用到的局部变量将会置为借用态,
    - 但编译期间并不知道返回值的地址.



</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">?</value>
            <value class="ptr byte4 hide" style="left: 201px;">0x6</value>
            <value class="ptr byte4 hide" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte4" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4" style="left: 139px;"><code>r</code></label>
            <label class="byte4 hide" style="left: 165px;"><code>x</code></label>
            <label class="byte4 hide" style="left: 188px;"><code>y</code></label>
        </labels>
        <subtext>“借用态”传播的问题</subtext>
        <!-- <subtext><code>let a = b;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let b = S(1);
let c = S(2);

let r = f(&b, &c);

let a = b;   // 这样做可行吗?
let a = c;   // 谁才是真正被借用的?

print_byte(r);
```

- 因为 `f` 只能返回一个地址, 所以并不是所有情况下 `b` 和 `c` 都需要保持锁定态.
- 多数情况下我们是有更好的办法解决这个问题的.
    - 特别是当我们知道一个参数 _不能_ 再被用于返回值的时候.


</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 210px; width: 102px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 38px;">S(1)</value>
            <value class="t byte2 hide" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">y + _</value>
            <value class="ptr byte4 hide" style="left: 201px;">0x6</value>
            <value class="ptr byte4 hide" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte4" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4" style="left: 139px;"><code>r</code></label>
            <label class="byte4 hide" style="left: 165px;"><code>x</code></label>
            <label class="byte4 hide" style="left: 188px;"><code>y</code></label>
        </labels>
        <subtext>借用态传播生命周期</subtext>
        <!-- <subtext><code>f(x: &'x S, y: &'y S) -> &'y u8</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f<'b, 'c>(x: &'b S, y: &'c S) -> &'c u8 { ... }

let b = S(1);
let c = S(2);

let r = f(&b, &c); // 我们知道返回的引用是基于 `c` 的, 它必须保持锁定;
                   // 然而 `b` 却是可以自由移动的.

let a = b;

print_byte(r);
```

- 解决这个问题的办法就是签名中的生命周期参数 (比如上面的 `'c`).
- 它们的主要作用是:
    - **函数外**会用于描述生成的结果基于哪个输入地址和输出地址,
    - **函数内**来保证只有生存时间低于 `'c` 的地址允许被赋值.
- 实际的生命周期 `'b`, `'c` 会基于开发者给出的借用态变量被编译器透明地指派给**调用方**.
- 它并**不等同于** `b` 或 `c` 的 _作用域_ (可能是从初始化到结束之间的代码行), 但仅有一个最小子集可以作为该作用域的 _生命周期_, 即基于 `b` 和 `c` 需要借用于该调用和保存结果的最少代码行.
- 某些如 `f` 被 `'c: 'b` 替代, 仍不能区分出来的情况下, 两个都会保持锁定.

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 38px;">S(2)</value>
            <value class="t byte2 hide" style="left: 79px;">S(1)</value>
            <value class="t byte2 hide" style="left: 119px;">S(2)</value>
            <value class="ptr byte4 hide" style="left: 177px;">y + 1</value>
            <value class="ptr byte4 hide" style="left: 201px;">0x6</value>
            <value class="ptr byte4 hide" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte4 hide" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4 hide" style="left: 139px;"><code>r</code></label>
            <label class="byte4 hide" style="left: 165px;"><code>x</code></label>
            <label class="byte4 hide" style="left: 188px;"><code>y</code></label>
        </labels>
        <!-- <subtext><code>{ let r = ... }</code></subtext> -->
        <subtext>解锁</subtext>
    </memory-row>
</lifetime-example>
<explanation>

```
let mut c = S(2);

let r = f(&c);
let s = r;
                    // <- 不是这里, `s` 会延长 `c` 的锁定时间.

print_byte(s);

let a = c;          // <- 是这里, 不再使用 `r` 和 `s`.


```
- 一旦任意引用最后指向了结束, 变量位置将会再次 _解锁_.

</explanation>
</lifetime-section>

</div></panel></tab>
</tabs>


<footnotes>

↕️ 点击展开用例

</footnotes>



{{ tablesep() }}


</magic>


---


# 数据类型

通用数据类型的内存表示. 


## 基本类型 {#basic-types}

语言核心内建的必要类型. 


#### 数字类型 {{ ref(page="types/numeric.html") }}

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>u8</code>, <code>i8</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced" >
    <name><code>u16</code>, <code>i16</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum  class="spaced">
    <name><code>u32</code>, <code>i32</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum  class="spaced">
    <name><code>u64</code>, <code>i64</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum  class="spaced">
    <name><code>u128</code>, <code>i128</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>f32</code></name>
    <visual class="float">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>f64</code></name>
    <visual class="float">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>usize</code>, <code>isize</code></name>
    <visual class="sized">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte style="border-color: #888;"><code></code></byte>
        <byte style="border-color: #888;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
    </visual>
    <zoom>
        与平台的 <code>ptr</code> 一致. 
    </zoom>
</datum>



<br/>


{{ tablesep() }}


<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-1" name="tab-group-numeric" checked>
<label for="tab-numeric-1"><b>无符号类型</b></label>
<panel><div>



| 类型 | 最大值 |
|---|---|
|`u8`| `255` |
|`u16` | `65_535` |
|`u32`| `4_294_967_295` |
|`u64`| `18_446_744_073_709_551_615` |
|`u128`| `340_282_366_920_938_463_463_374_607_431_768_211_455` |
|`usize`| 取决于平台指针大小, 可以是 `u16`, `u32`, 或 `u64`. |


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-3" name="tab-group-numeric">
<label for="tab-numeric-3"><b>有符号类型</b></label>
<panel><div>



| 类型 | 最大值 |
|---|---|
|`i8`| `127` |
|`i16` | `32_767` |
|`i32`| `2_147_483_647` |
|`i64`| `9_223_372_036_854_775_807` |
|`i128`| `170_141_183_460_469_231_731_687_303_715_884_105_727` |
|`isize`| 取决于平台指针大小, 可以是 `i16`, `i32`, 或 `i64`. |

{{ tablesep() }}

| 类型 | 最小值 |
|---|---|
|`i8`| `-128` |
|`i16` | `-32_768` |
|`i32`| `-2_147_483_648` |
|`i64`| `-9_223_372_036_854_775_808` |
|`i128`| `-170_141_183_460_469_231_731_687_303_715_884_105_728` |
|`isize`| 取决于平台指针大小, 可以是 `i16`, `i32`, 或 `i64`. |


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-2" name="tab-group-numeric">
<label for="tab-numeric-2"><b>浮点类型</b>{{ esoteric() }}</label>
<panel><div>


`f32` 的位表示<sup>*</sup>: 

<!-- NEW ENTRY -->
<datum style="opacity:0.7; margin-bottom:10px;">
    <visual class="float">
    <bitgroup>
        <bit><code>S</code></bit>
    </bitgroup>
    <bitgroup>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
    </bitgroup>
    <bitgroup>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
    </bitgroup>
    </visual>
</datum>

{{ tablesep() }}

说明: 

| f32 | S (1) | E (8) | F (23) | 值 |
|------| ---------| ---------| ---------| ---------|
| 规格化数 | ± | 1 to 254 | 任意 | ±(1.F)<sub>2</sub> * 2<sup>E-127</sup>  |
| 非规格化数 | ± | 0 | 非零 | ±(0.F)<sub>2</sub> * 2<sup>-126</sup>  |
| 零 | ± | 0 | 0 | ±0  |
| 无穷大 | ± | 255 | 0 | ±∞  |
| NaN | ± | 255 | 非零 | NaN  |

{{ tablesep() }}

同样, 对于 <code>f64</code> 类型, 这将类似于: 


| f64 | S (1) | E (11) | F (52) | 值 |
|------| ---------| ---------| ---------| ---------|
| 规格化数 | ± | 1 to 2046 | 任意 | ±(1.F)<sub>2</sub> * 2<sup>E-1023</sup>  |
| 非规格化数 | ± | 0 | 非零 | ±(0.F)<sub>2</sub> * 2<sup>-1022</sup>  |
| 零 | ± | 0 | 0 | ±0  |
| 无穷大 | ± | 2047 | 0 | ±∞  |
| NaN | ± | 2047 | 非零 | NaN  |

<footnotes>
    <sup>*</sup> 浮点类型遵循 <a href="https://en.wikipedia.org/wiki/IEEE_754-2008_revision">IEEE 754-2008</a> 规范, 并取决于平台大小端序. 
</footnotes>

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-4" name="tab-group-numeric">
<label for="tab-numeric-4"><b>转换的陷阱</b> {{ bad() }}</label>
<panel><div class="">


| 转换<sup>1</sup> | 结果 | 说明 |
| --- | --- | --- |
| `3.9_f32 as u8` | `3` | 截断, 请优先使用 `x.round()`. |
| `314_f32 as u8` | `255` | 采用最接近的可用数字.  |
| `f32::INFINITY as u8` | `255` | 同上, 但会把 `INFINITY` 当做一个 _真正的_ 大数.|
| `f32::NAN as u8` | `0` | - |
| `_314 as u8` | `58` | 截断多余的位.  |
| `_200 as i8` | `56` | - |
| `_257 as i8` | `-1` | - |

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-5" name="tab-group-numeric">
<label for="tab-numeric-5"><b>运算的陷阱</b> {{ bad() }}</label>
<panel><div class="">

| 操作<sup>1</sup> | 结果 | 说明 |
| --- | --- | --- |
| `200_u8 / 0_u8` | 编译错误. | - |
| `200_u8 / _0` <sup>d</sup> | Panic. | 由于除以 0, 该计算会 panic. |
| `200_u8 / _0` <sup>r</sup> | Panic. | 同上. |
| `200_u8 + 200_u8` |  编译错误. | - |
| `200_u8 + _200` <sup>d</sup> | Panic. | 考虑换用 `checked_`, `wrapping_` 等方法 {{ std(page="std/primitive.isize.html#method.checked_add") }}|
| `200_u8 + _200` <sup>r</sup> | `144` | 在 release 模式下会溢出. |
| `1_u8 / 2_u8` | `0` | 整数除法会截断. |
| `0.8_f32 + 0.1_f32` | `0.90000004` | - |
| `1.0_f32 / 0.0_f32` | `f32::INFINITY` | - |
| `0.0_f32 / 0.0_f32` | `f32::NAN` | - |
| `x < f32::NAN` | `false` | `NAN` 的比较结果永远为假. |
| `x > f32::NAN` | `false` | - |
| `f32::NAN == f32::NAN` | `false` | - |

</div></panel></tab>


<!-- End tabs -->
</tabs>

<!-- End overflow prevention -->
</div></div>


<footnotes>

<sup>1</sup>表达式 `_100` 表示可能包含 `100` 值的任何内容, 例如 `100_i32`, 但对编译器是不透明的. <br/>
<sup>d</sup> 调试版本. <br/>
<sup>r</sup> 发布版本. <br/>

</footnotes>


{{ tablesep() }}



#### 文本类型 {{ ref(page="types/textual.html") }}


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>char</code></name>
    <visual class="char">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
    <description>任意 UTF-8 标量. </description>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>str</code></name>
    <visual>
        <note>...</note>
        <byte class="bytes"><code>U</code></byte>
        <byte class="bytes"><code>T</code></byte>
        <byte class="bytes"><code>F</code></byte>
        <byte class="bytes"><code>-</code></byte>
        <byte class="bytes"><code>8</code></byte>
        <note>...未指明条目</note>
    </visual>
    <description>很少单独见到, 常用 <code>&str</code> 代替. </description>
</datum>


{{ tablesep() }}

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-textual-3" name="tab-group-textual" checked>
<label for="tab-textual-3"><b>基本</b></label>
<panel><div>

| 类型 | 描述 |
|---------|-------------|
| `char` | 总是为 4 字节, 且仅包含一个 Unicode **标量值**{{ link(url="https://www.unicode.org/glossary/#unicode_scalar_value") }}.  |
| `str` | 未知长度的 `u8` 数组保证保存 **UTF-8 编码的码位**.  |

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-textual-1" name="tab-group-textual">
<label for="tab-textual-1"><b>用法</b></label>
<panel><div>



<!-- Notice how:

- `char` is always 4 bytes and only holds a single Unicode **scalar value** {{ link(url="https://www.unicode.org/glossary/#unicode_scalar_value") }}, thus possibly wasting space.
- `str` is a byte-array of unknown length guaranteed to hold **UTF-8 encoded code points** (but harder to index).
 -->

| 字符 | 描述 |
|---------|-------------|
| `let c = 'a';` | 通常一个 `char` (Unicode 标量) 就是你直觉上认为的 _字符_. |
| `let c = '❤';` | 它可以持有很多 Unicode 符号. |
| `let c = '❤️';` | 但并不总是如此. 比如一个 emoji 是由**两个** `char` (参见编码) 组成的, **并不能**{{ bad() }}存在 `c` 里.<sup>1</sup> |
| `c = 0xffff_ffff;` | 字符也**不允许**{{ bad() }}用一个随便的比特模式就表示了. |

<footnotes>
    <sup>1</sup> 有趣的是, <a href="https://zh.wikipedia.org/wiki/%E9%9B%B6%E5%AE%BD%E8%BF%9E%E5%AD%97">零宽连字</a> (⨝) 会让用户把这些连起来<i>看起来像个字符</i>: 👨‍👩‍👧 实际上是由 👨⨝👩⨝👧 这 5 个字符组成的, 渲染引擎也可以把它们显示成一个字符, 也可以分开显示成三个, 这取决于平台的能力.
</footnotes>


{{ tablesep() }}

| 字符串 | 描述 |
|---------|-------------|
| `let s = "a";` | 通常并不会直接使用 `str`, 而是像这里的 `s` 一样通过 `&str` 访问. |
| `let s = "❤❤️";` | 可以存储任意长度的文本, 但很难进行索引. |


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-textual-2" name="tab-group-textual">
<label for="tab-textual-2"><b>编码</b>{{ esoteric() }}</label>
<panel><div>


`let s = "I ❤ Rust"; ` <br>
`let t = "I ❤️ Rust";`

| 变体 | 内存表示<sup>2<sup> |
|---------|-------------|
| `s.as_bytes()` | `49` `20` <span class="force-code-color same-black"><b>`e2 9d a4`</b> </span> `20 52 75 73 74` <sup>3<sup> |
| `s.chars()`<sup>1<sup> | `49 00 00 00 20 00 00 00` <span class="force-code-color same-black"><b>`64 27 00 00` </b></span> `20 00 00 00 52 00 00 00 75 00 00 00 73 00` &hellip; |
| `t.as_bytes()` | `49` `20` <span class="force-code-color same-black"><b>`e2 9d a4`</b> </span> <span class="force-code-color same-red"><b>`ef b8 8f`</b></span> `20 52 75 73 74` <sup>4<sup> |
| `t.chars()`<sup>1<sup> | `49 00 00 00 20 00 00 00` <span class="force-code-color same-black"><b>`64 27 00 00`</b></span> <span class="force-code-color same-red"><b>`0f fe 01 00`</b></span> `20 00 00 00 52 00 00 00 75 00` &hellip; |

{{ tablesep() }}

<footnotes>
    <sup>1</sup> 结果会转为字节数组.<br>
    <sup>2</sup> 在 x86 平台上的十六进制表示.<br>
    <sup>3</sup> 注意 <code>❤</code> 对应一个 <a href="https://codepoints.net/U+2764">Unicode 代码点 (U+2764)</a>, 它在 <code>char</code> 中被表示为 <span class="force-code-color same-black"><b>64 27 00 00</b></span>, 但在 <code>str</code> 中则被表示为 <a href="https://zh.wikipedia.org/wiki/UTF-8#%E7%BB%93%E6%9E%84">UTF-8 编码</a> <span class="force-code-color same-black"><b>e2 9d a4</b></span>.<br>
    <sup>4</sup> 注意 emoji <a href="https://emojipedia.org/red-heart/">红心 <code>❤️</code></a> 其实是由心形 <code>❤</code> 和 <a href="https://codepoints.net/U+FE0F">U+FE0F Variation Selector</a> 组成的, 可以看到 <code>t</code> 比 <code>s</code> 拥有更多字符.
</footnotes>

{{ tablesep() }}


<footnotes>

> <sup>💬</sup> 尽管上面的 `s` 和 `t` 是不一样的, 但 Safari 和 Edge 都有把脚注 3 和 4 的心形符号渲染错误的 Bug.

</footnotes>

</div></panel></tab>


<!-- End tabs -->
</tabs>


{{ tablesep() }}


## 自定义类型 {#custom-types}

用户定义的基本类型. 它实际的<b>内存布局</b>{{ ref(page="type-layout.html") }}取决于<b>表示法</b>{{ ref(page="type-layout.html#representations") }}, 还有对齐. 


<!-- NEW ENTRY -->
<datum class="spaced">
    <name class="nogrow"><code>T</code></name>
    <name class="hidden">x</name>
    <visual>
       <framed class="any t"><code>T</code></framed>
    </visual>
    <description>有大小 {{ below(target = "#sized-types") }} </description>
</datum>

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>T: ?Sized</code></name>
    <visual>
       <framed class="any unsized"><code>T</code></framed>
    </visual>
    <description>也许是 DST {{ below(target = "#sized-types") }} </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>[T; n]</code></name>
    <visual>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <note>... n 次</note>
    </visual>
    <description>固定的 <code>n</code> 个元素的数组. </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>[T]</code></name>
    <visual>
       <note>...</note>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <note>...未指定条目</note>
    </visual>
    <description>未知多元素的<b>切片类型</b>.<br>既非 <code>Sized</code>  (不携带 <code>len</code> 信息) , <br>多数情况下以 <code>&[T]</code> 为参照. {{ below(target="#references-pointers-ui") }}</description>
</datum>

<!-- NEW ENTRY -->
<datum style="margin-right:70px;">
    <name class="nogrow"><code>struct S; </code></name>
    <name class="hidden"><code>;</code></name>
    <visual style="width: 15px;" class="zst">
        <code></code>
    </visual>
    <description>零大小 {{ below(target = "#sized-types") }} </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>(A, B, C)</code></name>
    <visual style="width: 182px;">
       <framed class="any"><code>A</code></framed>
       <framed class="any" style="width: 100px;"><code>B</code></framed>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
    </visual>
    <andor>或者也可能</andor>
    <visual style="width: 182px;">
       <framed class="any" style="width: 100px;"><code>B</code></framed>
       <framed class="any"><code>A</code></framed>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
    </visual>
    <description>除非强制表示 (例如通过 <code>#[repr(C)]</code>) <br>否则类型布局未指定. </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>struct S { b: B, c: C } </code></name>
    <visual style="width: 166px;">
       <framed class="any" style="width: 100px;"><code>B</code></framed>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
    </visual>
    <andor>或者也可能</andor>
    <visual>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
       <pad><code style="">↦</code></pad>
       <framed class="any" style="width: 100px;"><code>B</code></framed>
    </visual>
    <description>编译器还可以添加填充. </description>
</datum>



<blockquote>
<footnotes>

还需注意, 具有完全相同字段的两种类型 `A(X, Y)` 和 `B(X, Y)` 仍然可以具有不同的布局. 在没有使用 `#[repr()]` 限制其布局表示的情况下, 绝不能使用 `transmute()` 进行类型转换. 


</footnotes>
</blockquote>



{{ tablesep() }}

这些**合并类型**存有其一种子类型的值: 


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>enum E { A, B, C }</code></name>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any">
            <code>A</code>
        </framed>
    </visual>
    <andor>排他性或</andor>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 100px;">
            <code>B</code>
        </framed>
    </visual>
    <andor>排他性或</andor>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 50px;">
            <code>C</code>
        </framed>
    </visual>
    <description>
        安全地保存 A, B 或 C. <br>又名“标签联合”, 尽管编译器会忽略标签. 
    </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>union { ... }</code></name>
    <visual style="text-align: left;">
        <framed class="any">
            <code>A</code>
        </framed>
    </visual>
    <andor>不安全或</andor>
    <visual style="text-align: left;">
        <framed class="any" style="width: 100px;">
            <code>B</code>
        </framed>
    </visual>
    <andor>不安全或</andor>
    <visual style="text-align: left;">
        <framed class="any" style="width: 50px;">
            <code>C</code>
        </framed>
    </visual>
    <description>
        不安全地以多种方式解释同一块内存. <br>结果可能是未定义的. 
    </description>
</datum>



## 引用 & 指针 {#references-pointers-ui}

引用授权了对其他内存空间的安全访问. 裸指针则是不安全 `unsafe` 的访问. 
各自的 `mut` 类型是相同的. 



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a T</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <memory-entry>
        <memory-link style="left:46%;">|</memory-link>
        <memory class="anymem">
            <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>必须定位一些有效 <code>t</code> 的 <code>T</code>, <br> 并且任何这样的目标必须
至少存在<code>'a</code>. </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>*const T</code></name>
    <visual class="unsafe">
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <zoom>
        没有任何保证. 
    </zoom>
</datum>

<br/>


### 元指针 {#pointer-meta}

许多引用和指针类型可以携带一个额外的字段, 即**元数据指针**{{ std(page="nightly/std/ptr/trait.Pointee.html#pointer-metadata") }}. 
它可以是目标的元素长度或字节长度, 也可以是指向 <i>vtable</i> 的指针. 带有元数据的指针称为**胖指针**, 否则称为**瘦指针**. 

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a T</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <memory-entry>
        <memory-link style="left:46%;">|</memory-link>
        <memory class="anymem">
            <framed class="any t"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>没有大小目标的元 (瘦指针). </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a T</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry>
        <memory-link style="left:46%;">|</memory-link>
        <memory class="anymem">
            <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>若 <code>T</code> 是 DST <code>struct</code> (如 <code>S { x: [u8] }</code>), <br>
    元字段 <code>len</code> 则是动态大小内容的长度.</description>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a [T]</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:24%;">|</memory-link>
        <memory class="anymem">
            ...
            <framed class="any" style="width: 30px;"><code>T</code></framed>
            <framed class="any" style="width: 30px;"><code>T</code></framed>
            ...
        </memory>
    </memory-entry>
    <description>通常省略 <code>'a</code> 的<b>切片引用</b> <br>
    (即切片类型 <code>[T]</code> 的引用类型) {{ above (target="#custom-types") }} <br>
    常表示为 <code>&[T]</code>.</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a str</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:24%;">|</memory-link>
        <memory class="anymem">
            ...
            <byte class="bytes"><code>U</code></byte>
            <byte class="bytes"><code>T</code></byte>
            <byte class="bytes"><code>F</code></byte>
            <byte class="bytes"><code>-</code></byte>
            <byte class="bytes"><code>8</code></byte>
            ...
        </memory>
    </memory-entry>
    <description><b>字符串切片引用</b> (即字符串<br>类型 <code>str</code> 的引用),<br> 元字段 <code>len</code> 即为字节长度.</description>
</datum>

<br>

<!-- NEW ENTRY -->
<datum class="spaced" style="padding-bottom: 165px;">
    <name><code>&'a dyn Trait</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <ptr>
            <code>ptr</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <memory-entry>
        <memory-link style="left:49%;">|</memory-link>
        <memory class="anymem">
            <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <memory-entry style="width:220px; position: absolute;">
        <memory-link style="left:22%;">|</memory-link>
        <memory class="static-vtable" style="width: 210px;">
            <table>
                <tr class="vtable"><td><code>*Drop::drop(&mut T)</code></td></tr>
                <tr class="vtable"><td><code>size</code></td></tr>
                <tr class="vtable"><td><code>align</code></td></tr>
                <tr class="vtable"><td><code>*Trait::f(&T, ...)</code></td></tr>
                <tr class="vtable"><td><code>*Trait::g(&T, ...)</code></td></tr>
            </table>
        </memory>
        <description>元指针指向虚表, 其中 <code>*Drop::drop()</code>, <code>*Trait::f()</code> 等是它们各自 <code>impl</code> for <code>T</code> 的指针.</description>
    </memory-entry>

</datum>


## 闭包 {#closures-data}

闭包是一个临时函数, 定义闭包时, 它会自动管理数据**捕获**{{ ref(page="types/closure.html#capture-modes") }}环境中访问的内容. 例如: 

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>move |x| x + y.f() + z</code></name>
    <visual>
       <framed class="any" style="width: 100px;"><code>Y</code></framed>
       <framed class="any" style="width: 50px;"><code>Z</code></framed>
    </visual>
    <zoom>匿名闭包类型 C1</zoom>
    <!-- <description>Also produces anonymous <br><code>f<sub>c1</sub> (c: C1, x: T)</code>. Details depend<br> which <code>FnOnce</code>, <code>FnMut</code>, <code>Fn</code> is allowed.</description> -->
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>|x| x + y.f() + z</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <zoom>匿名闭包类型 C2</zoom>
    <memory-entry>
        <memory-link style="left:44%;">|</memory-link>
        <memory class="anymem">
            <framed class="any" style="width: 30px;"><code>Y</code></framed>
        </memory>
    </memory-entry>
    <memory-entry>
        <memory-link style="left:44%;">|</memory-link>
        <memory class="anymem">
            <framed class="any" style="width: 30px;"><code>Z</code></framed>
        </memory>
    </memory-entry>
    <!-- <description>Similar, but captured context by<br> reference. Details might differ <br> depending on types involved.</description> -->
</datum>

<!-- Little hack as description below was too cluttered. -->
<!-- <datum>
    <name>&nbsp;</name>
    <description>
    Also produces anonymous <code>fn</code> such as <code>f_c1 (C1, X)</code> or <br>
    <code>f_c2 (&C2, X)</code>. Details depend which <code>FnOnce</code>, <code>FnMut</code>, <code>Fn</code> ...<br>
    is supported, based on properties of captured types.
    </description>
</datum> -->

<blockquote>
<footnotes>

生成匿名函数 <code>fn</code> 如 <code>f<sub>c1</sub>(C1, X)</code> or <code>f<sub>c2</sub>(&C2, X)</code>. 具体细节取决于捕获类型的属性支持 <code>FnOnce</code>, <code>FnMut</code> 还是 <code>Fn</code> .等.

</footnotes>
</blockquote>



## 标准库类型 {#standard-library-types}

Rust 标准库为上面提到的基本类型扩展了更多有用的类型, 并定义了一些特殊的语义. 一些通用类型如下: 


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>UnsafeCell&lt;T&gt;</code></name>
    <visual class="cell">
           <framed class="any unsized"><code>T</code></framed>
    </visual>
    <description>魔术类型, 允许<br>别名可变性. </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Cell&lt;T&gt;</code></name>
    <visual>
           <framed class="any unsized celled"><code>T</code></framed>
    </visual>
    <description>允许 <code>T</code> 的<br>移动进出. </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>RefCell&lt;T&gt;</code></name>
    <visual>
        <sized class="celled"><code>borrowed</code></sized>
        <framed class="any unsized celled"><code>T</code></framed>
    </visual>
    <description>允许 <code>T</code> 的动态借用.<br>
    比如 <code>Cell</code> 是 <code>Send</code> 的,<br> 但不是 <code>Sync</code> 的.</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>AtomicUsize</code></name>
    <visual class="atomic">
        <ptr class="atomic">
            <code>usize</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <description>其他原子类型类似</description>
</datum>


<!-- NEW ENTRY -->
<datum>
    <name><code>Result&lt;T, E&gt;</code></name>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 50px;">
            <code>E</code>
        </framed>
    </visual>
    <andor>或者</andor>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 100px;">
            <code>T</code>
        </framed>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Option&lt;T&gt;</code></name>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
    </visual>
    <andor>或者</andor>
    <visual class="enum">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 100px;">
            <code>T</code>
        </framed>
    </visual>
    <description>对于确定的类型 T 可以省略<br>标签. 比如 <code>NonNull</code>.</description>
</datum>



{{ tablesep() }}


#### 通用堆存储器


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Box&lt;T&gt;</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <memory-entry>
        <memory-link style="left:49%;">|</memory-link>
        <memory class="heap">
        <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>对某些 <code>T</code> 栈代理可能会持有 <br>元数据{{ above (target="#custom-types") }} (比如 <code>Box<[T]></code>).</description>
</datum>

<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>Vec&lt;T&gt;</code></name>
    <!-- For some reason we need the width for mobile not to line break -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>capacity</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap capacity">
            <div>
                <framed class="any t"><code>T</code></framed>
                <framed class="any t"><code>T</code></framed>
                <note>... len</note>
            </div>
            <capacity>← <note>capacity</note> →</capacity>
        </memory>
    </memory-entry>
</datum>


{{ tablesep() }}


#### 所有字符串


<!-- NEW ENTRY -->
<datum>
    <name><code>String</code></name>
    <!-- For some reason we need the width for mobile not to line break -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>capacity</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap">
            <div>
                <byte class="bytes"><code>U</code></byte>
                <byte class="bytes"><code>T</code></byte>
                <byte class="bytes"><code>F</code></byte>
                <byte class="bytes"><code>-</code></byte>
                <byte class="bytes"><code>8</code></byte>
                <note>... len</note>
            </div>
            <capacity>← <note>capacity</note> →</capacity>
        </memory>
    </memory-entry>
    <description>观察 <code>String</code> 和 <code>&str</code> 以及 <code>&[char]</code> 的区别.</description>
</datum>

<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>CString</code></name>
    <!-- For some reason we need the width for mobile not to line break -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap">
            <div>
                <byte class="bytes"><code>A</code></byte>
                <byte class="bytes"><code>B</code></byte>
                <byte class="bytes"><code>C</code></byte>
                <note>... len ...</note>
                <byte class="bytes"><code>␀</code></byte>
            </div>
        </memory>
    </memory-entry>
    <description>以空字符结束, 但中间没有空字符. </description>
</datum>


<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>OsString</code> {{ todo() }}</name>
    <!-- For some reason we need the width for mobile not to line break -->
    <visual class="platformdefined">
        平台定义
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap">
            <div>
                <byte class="bytes"><code>?</code></byte>
                <byte class="bytes"><code>?</code></byte>
                /
                <word class="bytes"><code>?</code></word>
                <word class="bytes"><code>?</code></word>
            </div>
        </memory>
    </memory-entry>
    <description>操作系统对字符串表示的直接封装.<br> (比如 Windows 上的 UTF-16).</description>
</datum>

<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>PathBuf</code> {{ todo() }}</name>
    <!-- For some reason we need the width for mobile not to line break -->
    <visual class="platformdefined">
        <payload>
            <code>OsString</code>
        </payload>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:40%;">|</memory-link>
        <memory class="heap">
            <div>
                <byte class="bytes"><code>?</code></byte>
                <byte class="bytes"><code>?</code></byte>
                /
                <word class="bytes"><code>?</code></word>
                <word class="bytes"><code>?</code></word>
            </div>
        </memory>
    </memory-entry>
    <description>操作系统对路径表示的直接封装.</description>
</datum>


{{ tablesep() }}

#### 共享所有权

如果类型 `T` 不包含 `Cell`, 那它也会包含以下 `Cell` 类型的变体以允许共享实际可变性.

<!-- NEW ENTRY -->
<datum>
    <name><code>Rc&lt;T&gt;</code></name>
    <visual style="width: 180px;">
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <div>
        <memory-entry class="quad">
            <memory-link style="left:15%;">|</memory-link>
            <memory class="heap">
                <sized class="celled"><code>strng</code><sub>2/4/8</sub></sized>
                <sized class="celled"><code>weak</code><sub>2/4/8</sub></sized>
                <framed class="any unsized"><code>T</code></framed>
            </memory>
        </memory-entry>
    </div>
    <description>在同一个线程上共享 <code>T</code> 的所有权. 需要嵌套 <code>Cell</code>
    或 <br><code>RefCell</code> 以允许修改. 它既不是 <code>Send</code> 也不是 <code>Sync</code> 的.</description>
</datum>


<!-- NEW ENTRY -->
<datum>
    <name><code>Arc&lt;T&gt;</code></name>
    <visual style="width: 180px;">
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <div style="width: 0px;">
        <memory-entry class="quad">
            <memory-link style="left:15%;">|</memory-link>
            <memory class="heap">
                <sized class="atomicx"><code>strng</code><sub>2/4/8</sub></sized>
                <sized class="atomicx"><code>weak</code><sub>2/4/8</sub></sized>
                <framed class="any unsized"><code>T</code></framed>
            </memory>
        </memory-entry>
    </div>
    <description>同左. 但如果 T 是 <code>Send</code> 且 <code>Sync</code> 的, 则允许在线程间共享.</description>
</datum>

<br>

<!-- NEW ENTRY -->
<datum>
    <name><code>Mutex&lt;T&gt;</code> / <code>RwLock&lt;T&gt;</code></name>
    <visual style="width: 230px;">
        <ptr><code>ptr</code><sub>2/4/8</sub></ptr>
        <sized class="atomicx"><code>poison</code><sub>2/4/8</sub></sized>
        <framed class="any unsized celled"><code>T</code></framed>
    </visual>
    <memory-entry>
        <memory-link style="left:45%;">|</memory-link>
        <memory class="heap">
            <code>lock</code>
        </memory>
    </memory-entry>
    <description>需要包在 <code>Arc</code> 里以便在线程间共享, <br>
    总是 <code>Send</code> 且 <code>Sync</code> 的. <br>
    可用 <a href="https://crates.io/crates/parking_lot">parking_lot</a> 替代 (快且不占用堆).
    </description>
</datum>



---


# 标准库


## 基本准则 {#one-liners}

这些代码片段很通用但经常容易忘. 详情可以参考 **Rust Cookbook** {{ link(url="https://rust-lang-nursery.github.io/rust-cookbook/") }}.


<!--
PRs for this section are very welcome. Idea is:
- Should be `std` only for now, no 3rd party libs (maybe exception for `rand`?)
- "Most people" should have encountered the problem
- Is not just a trival method on an 'obvious' struct (e.g., Sort a slice by `x.sort()` is probably too obvious.)
-->

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">


<tabs>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-2" name="tab-api-sized" checked>
<label for="tab-api-2"><b>字符串</b></label>
<panel><div class="color-header one-liners cheats">

| 用途 | 代码 |
|---------|-------------|
| 连接字符串 (任何实现了 `Display`{{ below(target="#string-output") }} 的类型). <sup>1</sup>  {{ edition(ed="'21") }} | `format!("{x}{y}")` |
| 以给定匹配分割字符串. {{ std(page="std/str/pattern/trait.Pattern.html") }} {{ link(url="https://stackoverflow.com/a/38138985") }} | `s.split(pattern)` |
| {{ tab() }} ... 以 `&str` | `s.split("abc")` |
| {{ tab() }} ... 以 `char` | `s.split('/')` |
| {{ tab() }} ... 以闭包 | `s.split(char::is_numeric)`|
| 以空白分割. | `s.split_whitespace()` |
| 以换行分割. | `s.lines()` |
| 以正则表达式分割.<sup>2</sup> | ` Regex::new(r"\s")?.split("one two three")` |

<footnotes>

<sup>1</sup> 会产生内存分配. 如果 `x` 已经是 `String` 的情况下可能不是性能的最优解.<br>
<sup>2</sup> 依赖 [regex](https://crates.io/crates/regex) crate.

</footnotes>


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-1" name="tab-api-sized">
<label for="tab-api-1"><b>I/O</b></label>
<panel><div class="color-header one-liners cheats">

| 用途 | 代码 |
|---------|-------------|
| 创建新文件 | `File::create(PATH)?` |
| {{ tab() }}  同上, 但给出选项 | `OpenOptions::new().create(true).write(true).truncate(true).open(PATH)?` |

<!-- <footnotes>

<sup>*</sup> We're a bit short on space here, <code>t</code> means true.

</footnotes> -->

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-4" name="tab-api-sized">
<label for="tab-api-4"><b>宏</b></label>
<panel><div class="color-header one-liners cheats">

| 用途 | 代码 |
|---------|-------------|
| 具有变量参数的宏 | `macro_rules! var_args { ($($args:expr),*) => {{ }} }` |
| {{ tab() }} 应用 `args`, 如多次调用 `f`. | {{ tab() }} ` $( f($args); )*` |

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-3" name="tab-api-sized">
<label for="tab-api-3"><b>怪用法</b>{{ esoteric() }}</label>
<panel><div class="color-header one-liners cheats">

| 用途 | 代码 |
|---------|-------------|
| 清理闭包捕获 | <code>wants_closure({ let c = outer.clone(); move &vert;&vert; use_clone(c) })</code> |
| 修复 '`try`' 闭包内的类型推断 | <code>iter.try_for_each(&vert;x&vert; { Ok::<(), Error>(()) })?;</code> |
| 当 `T` 满足 Copy 时, 迭代 _并_ 修改 `&mut [T]` | `Cell::from_mut(mut_slice).as_slice_of_cells()` |
| 给定长度的切片 | `&original_slice[offset..][..length]` |
| 确保 trait `T` 是对象安全的写法 | `const _: Option<&dyn T> = None;` |


</div></panel></tab>


</tabs>


</div></div>



## 线程安全 {#thread-safety}


<!-- Shamelessly stolen from https://www.reddit.com/r/rust/comments/ctdkyr/understanding_sendsync/exk8grg/ -->
<table class="sendsync">
    <thead>
        <tr><th>例</th><th><code>Send</code><sup>*</sup></th><th><code>!Send</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Sync</code><sup>*</sup></td><td><i>多数类型</i> ... <code>Mutex&lt;T&gt;</code>, <code>Arc&lt;T&gt;</code><sup>1,2</sup></td><td><code>MutexGuard&lt;T&gt;</code><sup>1</sup>, <code>RwLockReadGuard&lt;T&gt;</code><sup>1</sup></td></tr>
        <tr><td><code>!Sync</code></td><td><code>Cell&lt;T&gt;</code><sup>2</sup>, <code>RefCell&lt;T&gt;</code><sup>2</sup></td><td><code>Rc&lt;T&gt;</code>, <code>&dyn Trait</code>, <code>*const T</code><sup>3</sup>, <code>*mut T</code><sup>3</sup></td></tr>
    </tbody>
</table>

<footnotes>

<sup>*</sup> **`T: Send`** 表示实例 `t` 可以移动到另一个线程; **`T: Sync`** 表示 `&t` 可以移动到另一个线程.<br>
<sup>1</sup> 如果 `T` 为 `Sync`. <br>
<sup>2</sup> 如果 `T` 为 `Send`.<br>
<sup>3</sup> 如果你要发送一个裸指针, 建议创建新类型 `struct Ptr(*const u8)` 并 `unsafe impl Send for Ptr {}`. 用来保证你 _可能_ 会发送它 (到其他线程).

</footnotes>



## 迭代器 {#iterators}

<tabs class="color-header std-green">

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-1" name="tab-group-trait-iter" checked>
<label for="tab-trait-iter-1"><b>获取迭代器</b></label>
<panel><div>



**基础**

假设有一个元素类型都为 `C` 的集合 `c`:

* **`c.into_iter()`** &mdash; 将集合 `c` 转为一个**`Iterator`** {{ std(page="std/iter/trait.Iterator.html") }} `i` 并**消费掉**<sup>*</sup> `c`. 要求实现 `C` 的 **`IntoIterator`** {{ std(page="std/iter/trait.IntoIterator.html") }}, 其元素类型取决于 `C`. 这是获取迭代器的“标准方式”.
* **`c.iter()`** &mdash; 对**某些**集合更友好的方法, 返回一个**借用**迭代器而不消费掉 `c`.
* **`c.iter_mut()`** &mdash; 同上, 但返回一个允许修改集合元素的**可变借用**迭代器.


**迭代**

一旦你获得了一个 `i`:

* **`i.next()`** &mdash; 如果下一个元素 `c` 存在则返回 `Some(x)`, 否则返回 `None` 表示结束.


**循环**

* **`for x in c {}`** &mdash; 语法糖, 相当于调用 `c.into_iter()` 并且循环 `i` 直到它变为 `None`.

<footnotes>

<sup>*</sup> 当类型是 `Copy` 的时, 迭代器会看起来并没有消费掉 `c`。比如, 调用 `(&c).into_iter()` 会在 `&c` 上调用 `.into_iter()` (会消费掉该引用并返回一个迭代器), 但本质上并没有去访问 `c`.

</footnotes>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-2" name="tab-group-trait-iter">
<label for="tab-trait-iter-2"><b>实现迭代器</b></label>
<panel><div>

**基础**

假设有一集合 `struct Collection<T> {}`.


* **`struct IntoIter<T> {}`** &mdash; 创建一个持有自定义迭代状态 (比如下标) 的结构体.
* **`impl Iterator for IntoIter {}`** &mdash; 实现能够产生元素的 `Iterator::next()`.

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted"><code>Collection&lt;T&gt;</code></type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-right: 20px;">
    <entry class="wide">
        <type class="generic dotted"><code>IntoIter&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">Iterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = T;</code></associated-type>
    </entry>
</mini-zoo>


---


**共享和可变迭代器**

* **`struct Iter<T> {}`** &mdash; 创建一个持有 `&Collection<T>` 的结构体用于共享迭代.
* **`struct IterMut<T> {}`** &mdash; 类似地, 但持有 `&mut Collection<T>` 用于可变迭代.
* **`impl Iterator for Iter<T> {}`** &mdash; 实现共享迭代.
* **`impl Iterator for IterMut<T> {}`** &mdash; 实现可变迭代.

另外, 建议实现如下方法以获取对应迭代器:

- `Collection::iter(&self) -> Iter`,
- `Collection::iter_mut(&mut self) -> IterMut`.



<mini-zoo class="zoo" style="margin-right: 20px;">
    <entry class="wide">
        <type class="generic dotted"><code>Iter&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">Iterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &T;</code></associated-type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-right: 20px;">
    <entry class="wide">
        <type class="generic dotted"><code>IterMut&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">Iterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &mut T;</code></associated-type>
    </entry>
</mini-zoo>

---

**实现循环**
* **`impl IntoIterator for Collection {}`** &mdash; 使得 `for x in c {}` 可用.
* **`impl IntoIterator for &Collection {}`** &mdash; 使得 `for x in &c {}` 可用.
* **`impl IntoIterator for &mut Collection {}`** &mdash; 使得 `for x in &mut c {}` 可用.

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted"><code>Collection&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">IntoIterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = T;</code></associated-type>
        <associated-type class="grayed"><code>To = IntoIter&lt;T&gt;</code></associated-type>
        <note>在 <code>T</code> 上迭代.</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted grayed"><code>&Collection&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">IntoIterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &T;</code></associated-type>
        <associated-type class="grayed"><code>To = Iter&lt;T&gt;</code></associated-type>
        <note>在 <code>&T</code> 上迭代.</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted grayed"><code>&mut Collectn&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">IntoIterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &mut T;</code></associated-type>
        <associated-type class="grayed"><code>To = IterMut&lt;T&gt;</code></associated-type>
        <note>在 <code>&mut T</code> 上迭代.</note>
    </entry>
</mini-zoo>

</div></panel></tab>


</tabs>



<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">
<div class="color-header number">


## 数字转换 {#number-conversions}


目前<b style="">正确</b>的数字转换.

| ↓ 原始 / 目标 → | `u8` &hellip; `i128` |  `f32` / `f64` | String |
| --- | --- |  --- |--- |
| `u8` &hellip; `i128` | `u8::try_from(x)?` <sup>1</sup> |  `x as f32` <sup>3</sup> | `x.to_string()` |
| `f32` / `f64` | `x as u8` <sup>2</sup> |  `x as f32` | `x.to_string()` |
| `String` | `x.parse::<u8>()?` | `x.parse::<f32>()?` | `x` |


<footnotes>

<sup>1</sup> 如果是其类型的真子集, `from()` 将会直接转换, 比如 `u32::from(my_u8)`. <br/>
<sup>2</sup> 见下, 这些转换将会截断 (`11.9_f32 as u8` 得到 `11`) 或缩容 (`1024_f32 as u8` 得到 `255`). <br/>
<sup>3</sup> 转换后会重新用二进制位表示 (`u64::MAX as f32`) 或产生无穷大 `Inf` (`u128::MAX as f32`).

</footnotes>


<!-- end overflow -->
</div>
</div>
</div>



## 字符串转换 {#string-conversions}


下面列出要转换到**目标**字符串类型的方法:

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">


<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-1" name="tab-group-str" checked>
<label for="tab-str-1"><code>String</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`x`|
|`CString`|`x.into_string()?` |
|`OsString`|`x.to_str()?.to_string()`|
|`PathBuf`|`x.to_str()?.to_string()`|
|`Vec<u8>` <sup>1</sup> |`String::from_utf8(x)?`|
|`&str`|`x.to_string()` <sup>`i`</sup> |
|`&CStr`|`x.to_str()?.to_string()` |
|`&OsStr`|`x.to_str()?.to_string()`|
|`&Path`|`x.to_str()?.to_string()`|
|`&[u8]` <sup>1</sup> |`String::from_utf8_lossy(x).to_string()`|

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-2" name="tab-group-str" >
<label for="tab-str-2"><code>CString</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`CString::new(x)?`|
|`CString`|`x`|
|`OsString` <sup>2</sup>|`CString::new(x.to_str()?)?`|
|`PathBuf`|`CString::new(x.to_str()?)?`|
|`Vec<u8>` <sup>1</sup> |`CString::new(x)?`|
|`&str`|`CString::new(x)?`|
|`&CStr`|`x.to_owned()` <sup>`i`</sup> |
|`&OsStr` <sup>2</sup> |`CString::new(x.to_os_string().into_string()?)?`|
|`&Path`|`CString::new(x.to_str()?)?`|
|`&[u8]` <sup>1</sup> |`CString::new(Vec::from(x))?`|
|`*mut c_char` <sup>3</sup> |`unsafe { CString::from_raw(x) }`|

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-3" name="tab-group-str" >
<label for="tab-str-3"><code>OsString</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`OsString::from(x)` <sup>`i`</sup> |
|`CString`|`OsString::from(x.to_str()?)`|
|`OsString`|`x`|
|`PathBuf`|`x.into_os_string()`|
|`Vec<u8>` <sup>1</sup> | {{ todo() }} |
|`&str`|`OsString::from(x)` <sup>`i`</sup>|
|`&CStr`|`OsString::from(x.to_str()?)`|
|`&OsStr`|`OsString::from(x)` <sup>`i`</sup>|
|`&Path`|`x.as_os_str().to_owned()`|
|`&[u8]` <sup>1</sup> | {{ todo() }} |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-35" name="tab-group-str" >
<label for="tab-str-35"><code>PathBuf</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`PathBuf::from(x)` <sup>`i`</sup>|
|`CString`|`PathBuf::from(x.to_str()?)`|
|`OsString`|`PathBuf::from(x)` <sup>`i`</sup>|
|`PathBuf`|`x`|
|`Vec<u8>` <sup>1</sup> | {{ todo() }} |
|`&str`|`PathBuf::from(x)` <sup>`i`</sup>|
|`&CStr`|`PathBuf::from(x.to_str()?)`|
|`&OsStr`|`PathBuf::from(x)` <sup>`i`</sup>|
|`&Path`|`PathBuf::from(x)` <sup>`i`</sup>|
|`&[u8]` <sup>1</sup> | {{ todo() }} |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-4" name="tab-group-str" >
<label for="tab-str-4"><code>Vec&lt;u8&gt;</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`x.into_bytes()`|
|`CString`|`x.into_bytes()`|
|`OsString`| {{ todo() }} |
|`PathBuf`| {{ todo() }} |
|`Vec<u8>` <sup>1</sup> |`x`|
|`&str`|`Vec::from(x.as_bytes())`|
|`&CStr`|`Vec::from(x.to_bytes_with_nul())`|
|`&OsStr`| {{ todo() }} |
|`&Path`| {{ todo() }} |
|`&[u8]` <sup>1</sup> |`x.to_vec()`|

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-5" name="tab-group-str" >
<label for="tab-str-5"><code>&str</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`x.as_str()`|
|`CString`|`x.to_str()?`|
|`OsString`|`x.to_str()?`|
|`PathBuf`|`x.to_str()?`|
|`Vec<u8>` <sup>1</sup> |`std::str::from_utf8(&x)?`|
|`&str`|`x`|
|`&CStr`|`x.to_str()?`|
|`&OsStr`|`x.to_str()?`|
|`&Path`|`x.to_str()?`|
|`&[u8]` <sup>1</sup> |`std::str::from_utf8(x)?`|

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-6" name="tab-group-str" >
<label for="tab-str-6"><code>&CStr</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`CString::new(x)?.as_c_str()`|
|`CString`|`x.as_c_str()`|
|`OsString` <sup>2</sup>|`x.to_str()?`|
|`PathBuf`| {{ todo() }}<sup>,4</sup> |
|`Vec<u8>` <sup>1</sup><sup>,5</sup> |`CStr::from_bytes_with_nul(&x)?`|
|`&str`| {{ todo() }}<sup>,4</sup> |
|`&CStr`|`x`|
|`&OsStr` <sup>2</sup>| {{ todo() }} |
|`&Path`| {{ todo() }} |
|`&[u8]` <sup>1</sup><sup>,5</sup> |`CStr::from_bytes_with_nul(x)?`|
|`*const c_char` <sup>1</sup> |`unsafe { CStr::from_ptr(x) }`|

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-8" name="tab-group-str" >
<label for="tab-str-8"><code>&OsStr</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`OsStr::new(&x)`|
|`CString`| {{ todo() }} |
|`OsString`|`x.as_os_str()`|
|`PathBuf`|`x.as_os_str()`|
|`Vec<u8>` <sup>1</sup> | {{ todo() }} |
|`&str`|`OsStr::new(x)`|
|`&CStr`| {{ todo() }} |
|`&OsStr`|`x`|
|`&Path`|`x.as_os_str()`|
|`&[u8]` <sup>1</sup> | {{ todo() }} |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-85" name="tab-group-str" >
<label for="tab-str-85"><code>&Path</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`Path::new(x)` <sup>`r`</sup>|
|`CString`|`Path::new(x.to_str()?)` |
|`OsString`|`Path::new(x.to_str()?)` <sup>`r`</sup>|
|`PathBuf`|`Path::new(x.to_str()?)` <sup>`r`</sup>|
|`Vec<u8>` <sup>1</sup> | {{ todo() }} |
|`&str`|`Path::new(x)` <sup>`r`</sup>|
|`&CStr`|`Path::new(x.to_str()?)` |
|`&OsStr`|`Path::new(x)` <sup>`r`</sup>|
|`&Path`|`x`|
|`&[u8]` <sup>1</sup> | {{ todo() }} |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-7" name="tab-group-str" >
<label for="tab-str-7"><code>&[u8]</code></label>
<panel><div class="stringconversion">

| **原始**类型 `x`| 转换方法 |
| --- | --- |
|`String`|`x.as_bytes()`|
|`CString`|`x.as_bytes()`|
|`OsString`| {{ todo() }} |
|`PathBuf`| {{ todo() }} |
|`Vec<u8>` <sup>1</sup> |`&x`|
|`&str`|`x.as_bytes()`|
|`&CStr`|`x.to_bytes_with_nul()`|
|`&OsStr`| `x.as_bytes()` <sup>2</sup> |
|`&Path`| {{ todo() }} |
|`&[u8]` <sup>1</sup> |`x`|

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-9" name="tab-group-str" >
<label for="tab-str-9"><b>其他</b></label>
<panel><div class="stringconversion">

| **目标**类型 | **原始**类型 `x` | 转换方法 |
| --- | --- | --- |
|<b>`*const c_char`</b>|<b>`CString`</b>|`x.as_ptr()`|


</div></panel></tab>

<!-- End tabs -->
</tabs>

<!-- End overflow protection -->
</div></div>


<footnotes>

<sup>i</sup> 如果可以推断出类型则可简写为 `x.into()`. <br>
<sup>r</sup> 如果可以推断出类型则可简写为 `x.as_ref()`.

<sup>1</sup> 该调用应当也必然为 `unsafe` 的, 请确保原始数据是对应字符串类型的有效表示 (比如 `String` 必须是 UTF-8 编码). {{ link(url="https://people.gnome.org/~federico/blog/correctness-in-rust-reading-strings.html") }}


<sup>2</sup> 仅在某些平台上 `std::os::<your_os>::ffi::OsStrExt` 支持通过辅助方法获取底层 `OsStr` 的原始 `&[u8]` 表示. 例如:

```
use std::os::unix::ffi::OsStrExt;
let bytes: &[u8] = my_os_str.as_bytes();
CString::new(bytes)?
```

<sup>3</sup> `c_char` **必须**由前一个 `CString` 生成. 如果是从 FFI 来的则换用 `&CStr`.

<sup>4</sup> 如果没有结尾 `0x0` 的话是没法简单地转换为 `x` 的. 最好的办法是通过 `CString` 转一道.

<sup>5</sup> 必须保证数组以 `0x0` 结束.

</footnotes>


## 字符串输出 {#string-output}

将类型转换为 `String` 或输出出来.

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-strop-1" name="tab-group-strop" checked>
<label for="tab-strop-1"><b>API</b></label>
<panel><div class="color-header undefined-color-3">

Rust 拥有一系列将类型转化为字符串输出的 API, 统称为 _格式化_ 宏:

| 宏 | 输出 | 说明 |
| --- | --- | --- |
|`format!(fmt)` | `String` | 全功能的“转为 `String`”. |
|`print!(fmt)`| 控制台 | 写到标准输出. |
|`println!(fmt)`| 控制台 | 写到标准输出. |
|`eprint!(fmt)`| 控制台 | 写到标准错误输出. |
|`eprintln!(fmt)`| 控制台 | 写到标准错误输出. |
|`write!(dst, fmt)` | 缓冲区 | 别忘了要引入 `use std::io::Write;` |
|`writeln!(dst, fmt)` | 缓冲区 | 别忘了要引入 `use std::io::Write;` |

{{ tablesep() }}

| 方法 | 说明 |
| --- | --- |
|`x.to_string()` {{ std(page="std/string/trait.ToString.html") }} | 产生 `String`, 对每个 `Display` 类型都作了实现. |

{{ tablesep() }}

这里 `fmt` 是个类似于 `"hello {}"` 字符串字面量, 它可以指定输出 (参见“格式化”) 和附加参数.


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-strop-2" name="tab-group-strop">
<label for="tab-strop-2"><b>可打印类型</b></label>
<panel><div class="color-header undefined-color-3">

这里列出了在 `format!` 和类似命令中, 通过 trait `Display` `"{}"` {{ std(page="std/fmt/trait.Display.html") }} 或 `Debug` `"{:?}"` {{ std(page="std/fmt/trait.Debug.html") }} 实现的类型转换 (并不全面):

| 类型 | 实现 |  |
| --- | --- | --- |
|`String`| `Debug, Display` | |
|`CString`| `Debug` | |
|`OsString`| `Debug` | |
|`PathBuf`| `Debug` |  |
|`Vec<u8>` | `Debug` | |
|`&str`|`Debug, Display` | |
|`&CStr`|`Debug` | |
|`&OsStr`| `Debug` | |
|`&Path`| `Debug` | |
|`&[u8]` |`Debug` | |
|`bool` |`Debug, Display` | |
|`char` |`Debug, Display` | |
|`u8` &hellip; `i128` |`Debug, Display` | |
|`f32`, `f64` |`Debug, Display` | |
|`!` |`Debug, Display` | |
|`()` |`Debug` | |

{{ tablesep() }}

简而言之, `Debug` 打印出详细信息; 而 _特殊_ 类型需要特别指定如何转换到 {{ above(target="#string-conversions" ) }} `Display`.

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-strop-3" name="tab-group-strop">
<label for="tab-strop-3"><b>格式化</b></label>
<panel><div>

格式化宏中的各参数指示器可以是 `{}`, `{argument}` 或后续下述基本[**语法**](https://doc.rust-lang.org/std/fmt/index.html#syntax):


```
{ [argument] ':' [[fill] align] [sign] ['#'] [width [$]] ['.' precision [$]] [type] }
```

<div class="color-header undefined-color-3">

| 元素 |  说明 |
|---------| ---------|
| `argument` |  数字 (`0`, `1`, ...), 参数 {{ edition(ed="'21") }} 或名称,{{ edition(ed="'18") }} 如 `print!("{x}")`. |
| `fill` | 当指定 `width` 时该字符串将用于填充空白 (如 `0`). |
| `align` | 当指定宽度时表示左 (`<`), 中 (`^`), 右 (`>`). |
| `sign` | Can be `+` for sign to always be printed. |
| `#` | [增强格式化](https://doc.rust-lang.org/std/fmt/index.html#sign0), 如更美观的 `Debug`{{ std(page="std/fmt/trait.Debug.html") }} 格式化 `?` 或十六进制前导符 `0x`. |
| `width` | 最小宽度 (&geq; 0), 用 `fill` 填充 (默认为空格). 如果以 `0` 开头则用 0 填充. |
| `precision` | 数字类型的十进制位数 (&geq; 0), 或非数值类型的最大宽度. |
| `$` | 将 `width` 或 `precision` 解释为参数标识符以允许动态格式化. |
| **`type`** | `Debug`{{ std(page="std/fmt/trait.Debug.html") }} (`?`) 格式化, 十六进制 (`x`), 二进制 (`b`), 八进制 (`o`), 指针 (`p`), 科学计数法 (`e`)... [见此](https://doc.rust-lang.org/std/fmt/index.html#traits). |

</div>


{{ tablesep() }}


<div class="color-header undefined-color-3">

| 格式举例 | 说明 |
|---------|-------------|
| `{}` | 使用 `Display` 打印下一个参数.{{ std(page="std/fmt/trait.Display.html") }} |
| `{x}` | 同上, 但使用作用域中的 `x`. {{ edition(ed="'21") }} |
| `{:?}` | 使用 `Debug` 打印下一个参数.{{ std(page="std/fmt/trait.Debug.html") }} |
| `{2:#?}` | 用 `Debug`{{ std(page="std/fmt/trait.Debug.html") }} 格式化美观打印第三个参数. |
| `{val:^2$}` | 将参数 `val` 居中, 其宽度由第三个参数指定. |
| `{:<10.3}` | 以宽度 10 进行左对齐, 小数位数是 3.|
| `{val:#x}` | 用十六进制格式化 `val` 参数, 并带有前导 `0x` (`x` 的增强格式). |

</div>

{{ tablesep() }}


<div class="color-header undefined-color-3">

| 用法举例 | 说明 |
|---------|-------------|
| `println!("{}", x)` | 用 `Display`{{ std(page="std/fmt/trait.Display.html") }} 打印 `x` 到标准输出并换行. {{ edition(ed="'15") }} |
| `println!("{x}")` | 同上, 但使用作用域的 `x`. {{ edition(ed="'21") }}  |
| `format!("{a:.3} {b:?}")` | 将 `PI` 转为小数点后 3 位, 中间加一个空格后, 用 `Debug` {{ std(page="std/fmt/trait.Debug.html") }} 打印 `b`, 返回 `String`.  {{ edition(ed="'21") }} |

</div>


</div></panel></tab>


</tabs>

{{ tablesep() }}




---

# 工具链


## 项目结构 {#project-anatomy}

基本项目布局, 以及 `cargo` 常用的文件和目录. {{ below(target="#cargo") }}

<div class="color-header red">

| 项目 | 代码 |
|--------| ---- |
| 📁 `.cargo/` | **项目本地 cargo 配置**, 可以包含 **`config.toml`**. {{ link( url="https://doc.rust-lang.org/cargo/reference/config.html") }} {{ esoteric() }} |
| 📁 `benches/` | 存放该 crate 的性能测试, 通过 **`cargo bench`** 运行, 默认要求 nightly. <sup>*</sup> {{ experimental() }} |
| 📁 `examples/` | 使用该 crate 的例程, 其中的代码视该 crate 层级如用户.  |
| {{ tab() }} `my_example.rs` | 每个独立的例程可以通过 **`cargo run --example my_example`** 来运行. |
| 📁 `src/` | 项目实际源代码. |
| {{ tab() }} `main.rs` | 应用程序默认入口, 即 **`cargo run`** 运行的内容. |
| {{ tab() }} `lib.rs` | 库默认入口. 即 `my_crate::f()` 对应查找的内容. |
| 📁 `src/bin/` | 额外的二进制程序, 在库项目中也可以有. |
| {{ tab() }} `x.rs` | 二进制程序可通过 `cargo run --bin x` 来运行. |
| 📁 `tests/` | 集成测试, 通过 **`cargo test`** 调用. 单元测试则通常直接放在 `src/` 的文件里. |
| `.rustfmt.toml` | [**自定义**](https://rust-lang.github.io/rustfmt/) **`cargo fmt`** 的运行方式. |
| `.clippy.toml` | 对特定 [**clippy lint**](https://rust-lang.github.io/rust-clippy/master/index.html) 的特殊配置, 通过 **`cargo clippy`** 调用  {{ esoteric() }} |
| `build.rs` |  **预编译脚本**, {{ link(url="https://doc.rust-lang.org/cargo/reference/build-scripts.html") }} 当编译 C/FFI 等时常用. |
| <code class="ignore-auto language-bash">Cargo.toml</code> | 主**项目清单**, {{ link(url="https://doc.rust-lang.org/cargo/reference/manifest.html") }} 定义了依赖和架构等. |
| <code class="ignore-auto language-bash">Cargo.lock</code> | 用于可重复构建的依赖详情, 对于应用程序建议加入 `git` 版本控制, 但库不需要. |
| `rust-toolchain.toml` |  定义项目的**工具链覆盖**{{ link(url="https://rust-lang.github.io/rustup/overrides.html" )}} (频道, 组件, 目标). |
</div>

<footnotes>

<sup>*</sup> stable 可以考虑 [Criterion](https://github.com/bheisler/criterion.rs).

</footnotes>


{{ tablesep() }}


各种不同入口的**最简单样例**如下:

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-1" name="tab-group-anatomy" checked>
<label for="tab-anatomy-1"><b>应用程序</b></label>
<panel><div>


<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/main.rs (默认应用程序入口点)

fn main() {
    println!("Hello, world!");
}
```

</div></div></div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-2" name="tab-group-anatomy" >
<label for="tab-anatomy-2"><b>库</b></label>
<panel><div>

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/lib.rs (默认库入口点)

pub fn f() {}      // 根下的公共条目, 可被外部访问.

mod m {
    pub fn g() {}  // 根下非公开 (`m` 不公开), 
}                  // 所以 crate 外不可访问.
```
</div></div></div></panel></tab>





<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-3" name="tab-group-anatomy" >
<label for="tab-anatomy-3"><b>单元测试</b></label>
<panel><div>

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/my_module.rs (项目中任意文件)

fn f() -> u32 { 0 }

#[cfg(test)]
mod test {
    use super::f;           // 需要从父模块导入.
                            // 可以访问非公共成员.
    #[test]
    fn ff() {
        assert_eq!(f(), 0);
    }
}
```
</div></div></div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-4" name="tab-group-anatomy" >
<label for="tab-anatomy-4"><b>集成测试</b></label>
<panel><div>

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// tests/sample.rs (例程测试样例)

#[test]
fn my_sample() {
    assert_eq!(my_crate::f(), 123); // 集成和性能测试对 crate 的依赖
}                                   // 与依赖第三方库是一样的. 因此仅可访问公开项.
```
</div></div></div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-5" name="tab-group-anatomy" >
<label for="tab-anatomy-5"><b>性能测试</b></label>
<panel><div>


<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// benches/sample.rs (性能测试样例)

#![feature(test)]   // #[bench] 依然是实验性的

extern crate test;  // 出于某些原因在 '18 版本仍需要.
                    // 虽然通常情况下可能不需要.

use test::{black_box, Bencher};

#[bench]
fn my_algo(b: &mut Bencher) {
    b.iter(|| black_box(my_crate::f())); // `black_box` 防止 `f` 被优化掉.
}
```
</div></div></div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-6" name="tab-group-anatomy" >
<label for="tab-anatomy-6"><b>构建脚本</b></label>
<panel><div>

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// build.rs (预编译脚本样例)

fn main() {
    // 通过 env 环境变量获取编译目标; 也可使用 `#[cfg(...)]`.
    let target_os = env::var("CARGO_CFG_TARGET_OS");
}
```

<sup>*</sup>环境变量详见[该表](https://doc.rust-lang.org/cargo/reference/environment-variables.html#environment-variables-cargo-sets-for-build-scripts).

</div></div></div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-25" name="tab-group-anatomy" >
<label for="tab-anatomy-25"><b>过程宏</b>{{ esoteric() }}</label>
<panel><div>


<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/lib.rs (过程宏默认入口)

extern crate proc_macro;  // 需要显式引入.

use proc_macro::TokenStream;

#[proc_macro_attribute]   // 此时可以通过 `#[my_attribute]` 使用
pub fn my_attribute(_attr: TokenStream, item: TokenStream) -> TokenStream {
    item
}
```


```
// Cargo.toml

[package]
name = "my_crate"
version = "0.1.0"

[lib]
proc-macro = true
```


</div></div></div></panel></tab>


</tabs>



{{ tablesep() }}


模块树和导入规则:

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-module-import-1" name="tab-group-module-import" checked>
<label for="tab-module-import-1"><b>模块树</b></label>
<panel><div>


<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

**模块**{{ book(page="ch07-02-defining-modules-to-control-scope-and-privacy.html") }} {{ ex(page="mod.html#modules") }} {{ ref(page="items/modules.html#modules") }}和**源文件**行为如下:

- **模块树**要求显式定义, **无法**被隐式地从**文件系统树**中构建. {{ link(url="http://www.sheshbabu.com/posts/rust-module-system/") }}
- **模块树根**等同于库或应用程序的入口点 (如 `lib.rs`).

实际的**模块定义**行为如下:
- 一个 **`mod m {}`** 会定义一个文件内模块, 而当使用 **`mod m;`** 时则会读取 `m.rs` 或 `m/mod.rs`.
- `.rs` 的路径取决于**嵌套层级**, 如 `mod a { mod b { mod c; }}}` 指向 `a/b/c.rs` 或 `a/b/c/mod.rs`.
- 某些在模块树根中路径不对应文件的 `mod m;` 并不会被编译器检查到! {{ bad() }}

<!-- - **Visibility** of items (e.g., functions, fields) between modules governed by: "Is there visible path to item?"
    - Visibility like `pub fn f() {}` does not mean "`f` is public", but "`f` at most public if all parents public`. -->


</div></div></div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-module-import-2" name="tab-group-module-import">
<label for="tab-module-import-2"><b>命名空间</b>{{ esoteric() }}</label>
<panel><div>


Rust 有如下三种**命名空间**:

<table>
    <thead>
        <tr>
            <th>命名空间 <i>类型</i></th>
            <th>命名空间 <i>函数</i></th>
            <th>命名空间 <i>宏</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>mod X {}</code></td>
            <td><code>fn X() {}</code></td>
            <td><code>macro_rules! X { ... }</code></td>
        </tr>
        <tr>
            <td><code>X</code> (crate)</td>
            <td><code>const X: u8 = 1;</code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>trait X {}</code></td>
            <td><code>static X: u8 = 1;</code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>enum X {}</code></td>
            <td><code></code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>union X {}</code></td>
            <td><code></code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>struct X {}</code></td>
            <td><code></code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td colspan="2" style="text-align: center;"><code>struct X;</code><sup>1</sup></td>
            <td></td>
        </tr>
        <tr>
            <td colspan="2" style="text-align: center;"><code>struct X();</code><sup>1</sup></td>
            <td></td>
        </tr>
    </tbody>
</table>

<footnotes>

<sup>1</sup> 既可以算作 <i>类型</i> 也算作 <i>函数</i>.

</footnotes>

- 在给定作用域中 (如在某个模块中), 每个命名空间类型下只能有一个项, 如:
    - `enum X {}` 和 `fn X() {}` 冲突
    - `struct X;` 和 `const X` 不冲突
- 当使用 `use my_mod::X;` 时, 所有叫作 `X` 的项都会被导入.

> 出于存在名称转换 (如 `fn` 何 `mod` 都会被转为小写), 以及 _常识_ (开发者不太会命名多个 `X`) 的考虑, 在多数 crate 中通常并不需要担心这些 _情况_. 但在设计宏的时候, 这是需要考虑的一点.


</div></panel></tab>


</tabs>


{{ tablesep() }}



## Cargo

常用命令行工具.


<div class="color-header tooling">

| 命令 | 说明 |
|--------| ---- |
| `cargo init` | 基于最新的版本创建新项目.  |
| <code>cargo <span class="cargo-prefix">b</span>uild</code> | 调试模式构建项目 (<code>--<span class="cargo-prefix">r</span>elease</code> 启用所有优化). |
| <code>cargo <span class="cargo-prefix">c</span>heck</code> | 检查项目是否通过编译 (比构建更快)). |
| <code>cargo <span class="cargo-prefix">t</span>est</code> | 运行项目测试用例. |
| <code>cargo <span class="cargo-prefix">d</span>oc --open</code> | 生成并打开代码和相关依赖的本地文档. |
| <code>cargo <span class="cargo-prefix">r</span>un</code> | 编译出二进制文件并运行 (main.rs). |
| {{ tab() }} `cargo run --bin b` | 运行二进制程序 `b`. 统一 feature 和其他依赖 (可能会产生冲突). |
| {{ tab() }} `cargo run -p w` | 在子工作空间中 `w` 运行主程序. 对待 feature 可能更如你所愿. |
| `cargo tree` | 显示依赖树. |
| <code>cargo +{nightly, stable} ...</code>  | 命令使用给定工具链, 如对某些 'nightly only' 的工具. |
| `cargo +nightly ...` | 某些 nightly-only 命令 (如下替换 `...`) |
| {{ tab() }}  <code>build -Z timings</code> | 显示哪个 crate 导致你编译那么久, 很有用. {{ experimental() }} {{ hot() }} |
| {{ tab() }} `rustc -- -Zunpretty=expanded` |  显示宏展开. {{ experimental() }} |
| `rustup doc` | 打开离线 Rust 文档 (包括官方手册), “云”上编程! |

</div>

<footnotes>

这里 <code>cargo <span class="cargo-prefix">b</span>uild</code> 表示可以输入 `cargo build` 或者简写成 `cargo b`; <code>--<span class="cargo-prefix">r</span>elease</code> 表示可以简写成 `-r`.

</footnotes>


{{ tablesep() }}


可选的 `rustup` 组件.
通过 `rustup component add [tool]` 安装.


<div class="color-header tooling">

| 工具 | 说明 |
|--------| ---- |
| `cargo clippy` | 额外([lints](https://rust-lang.github.io/rust-clippy/master/)) 检查通用 API 误用和非惯用代码.{{ link(url = "https://github.com/rust-lang/rust-clippy") }} |
| `cargo fmt` | 自动代码格式化.(`rustup component add rustfmt`) {{ link(url = "https://github.com/rust-lang/rustfmt") }} |

</div>

{{ tablesep() }}

更多 cargo 插件可以在[**这里**](https://crates.io/categories/development-tools::cargo-plugins?sort=downloads)找到.


{{ tablesep() }}


## 交叉编译 {#cross-compilation}

<!-- <div class="steps"> -->

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

🔘 检查[目标是否支持](https://doc.rust-lang.org/rustc/platform-support.html).

🔘 安装目标依赖: **`rustup target install X`**.

🔘 安装本地工具链(取决于目标可能需要**链接**).

应从目标供应商(Google, Apple 等)获取这些资源.也可能不支持本地宿主环境(比如, Windows 不支持 iOS 工具链).

**某些工具链需要额外的构建步骤** (比如 Android 的 `make-standalone-toolchain.sh`).

🔘 修改 **`~/.cargo/config.toml`** 如下: 

```
[target.aarch64-linux-android]
linker = "[PATH_TO_TOOLCHAIN]/aarch64-linux-android/bin/aarch64-linux-android-clang"
```

   或者

```
[target.aarch64-linux-android]
linker = "C:/[PATH_TO_TOOLCHAIN]/prebuilt/windows-x86_64/bin/aarch64-linux-android21-clang.cmd"
```

🔘 设置**环境变量** (可选, 编译器不报错则可以跳过):

```
set CC=C:\[PATH_TO_TOOLCHAIN]\prebuilt\windows-x86_64\bin\aarch64-linux-android21-clang.cmd
set CXX=C:\[PATH_TO_TOOLCHAIN]\prebuilt\windows-x86_64\bin\aarch64-linux-android21-clang.cmd
set AR=C:\[PATH_TO_TOOLCHAIN]\prebuilt\windows-x86_64\bin\aarch64-linux-android-ar.exe
...
```

如何设置取决于编辑器提示, 并非所有步骤都是必须的.

> 某些平台和配置可能对路径表示**极其敏感** (比如) `\` 和 `/`).


✔️ 通过 **`cargo build --target=X`** 编译.


<!-- End overflow area -->
</div>
</div>

<!-- End steps  -->
<!-- </div> -->

{{ tablesep() }}




## 工具链命令 {#tooling-directives}

源代码中用于工具链或预处理的内嵌的特殊标识符.

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-1" name="tab-group-preprocessing" checked>
<label for="tab-preprocessing-1"><b>宏</b></label>
<panel><div class="color-header undefined-color-3">

<fixed-2-column class="color-header special_example">

<!-- Tool: **Preprocessor (Automatic)** -->


<!-- ```
macro_rules! my_macro {
    ($x:ty) => { ... }
}
``` -->

**声明**{{ book(page="ch19-06-macros.html#declarative-macros-with-macro_rules-for-general-metaprogramming") }}**宏** {{book(page="ch19-06-macros.html")}} {{ex(page="macros.html#macro_rules")}} {{ref(page="macros-by-example.html")}} 使用 `macro_rules!`:

| 写法 |  说明 |
|---------|---------|
| `$x:ty`  | 宏捕获 (此处捕获一个类型). |
| {{ tab() }} `$x:item`    | 项, 比如一个函数, 结构体或模块等. |
| {{ tab() }} `$x:block`   | 语句或表达式块 `{}`, 如 `{ let x = 5; }` |
| {{ tab() }} `$x:stmt`    | 语句, 如 `let x = 1 + 1;`, `String::new();` 或 `vec![];` |
| {{ tab() }} `$x:expr`    | 表达式, 如 `x`, `1 + 1`, `String::new()` 或 `vec![]` |
| {{ tab() }} `$x:pat`     | 模式, 如 `Some(t)`, `(17, 'a')` 或 `_`. |
| {{ tab() }} `$x:ty`      | 类型, 如 `String`, `usize` 或 `Vec<u8>`. |
| {{ tab() }} `$x:ident`   | 标识符, 比如在 `let x = 0;` 中标识符是 `x`. |
| {{ tab() }} `$x:path`    | 路径 (如 `foo`, `::std::mem::replace`, `transmute::<_, int>`). |
| {{ tab() }} `$x:literal` | 字面量 (如 `3`, `"foo"`, `b"bar"` 等.). |
| {{ tab() }} `$x:lifetime` | 生命周期 (如 `'a`, `'static` 等.). |
| {{ tab() }} `$x:meta`    | 元项; 用在 `#[...]` 和 `#![...]` 属性声明里. |
| {{ tab() }} `$x:vis`    | 可见修饰符;  `pub`, `pub(crate)` 等. |
| {{ tab() }} `$x:tt`      | 单个 token 树, 详情[见此](https://stackoverflow.com/a/40303308). |
| `$crate` | 特殊保留变量, 宏定义所在的 crate. {{ todo() }} |

</fixed-2-column>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-2" name="tab-group-preprocessing">
<label for="tab-preprocessing-2"><b>文档</b></label>
<panel><div class="color-header undefined-color-2">

<fixed-2-column  class="color-header special_example">

<!-- ```
/// Accepts an [`S`].
///
/// ```rust
///     f(s);
/// ```
``` -->

**文档注释**{{ book(page="ch14-02-publishing-to-crates-io.html#making-useful-documentation-comments") }} {{ ex(page="meta/doc.html#documentation") }} {{ ref(page="comments.html#doc-comments")}}中的写法如下:

| 写法 | 说明 |
|--------|-------------|
| ` ```...``` ` | 包含一个[**文档测试**](https://doc.rust-lang.org/rustdoc/documentation-tests.html) (文档代码通过 `cargo test` 运行). |
| ` ```X,Y ...``` ` | 同上, 但包含可选项 `X`, `Y` 如下 ... |
| {{ tab() }} <code style="color: gray;">rust</code> | 明确该测试是由 Rust 编写的; 可以通过 Rust 工具链解析. |
| {{ tab() }} <code style="color: gray; opacity: 0.3;">-</code> | 编译测试. 运行测试. 当 panic 时失败. **默认行为**. |
| {{ tab() }} <code style="color: gray;">should_panic</code> | 编译测试. 运行测试. 执行应当 panic. 否则测试失败. |
| {{ tab() }} <code style="color: gray;">no_run</code> | 编译测试. 编译失败则测试失败, 不会运行测试. |
| {{ tab() }} <code style="color: gray;">compile_fail</code> | 编译测试. 但如果代码 _能够_ 通过编译则失败. |
| {{ tab() }} <code style="color: gray;">ignore</code> | 不要编译. 不要运行. 忽略. |
| {{ tab() }} <code style="color: gray;">edition2018</code> | 在 Rust '18 版本下运行; 默认是 '15. |
| `#` | 文档中注释某行 (` ```   # use x::hidden; ``` `). |
| <code>[&#96;S&#96;]</code> | 创建一个链接指向结构体, 枚举, trait, 函数, &hellip; 的 `S`. |
| <code>[&#96;S&#96;]&#40;crate::S&#41;</code> | 可以使用 Markdown 语法指定链接路径. |


</fixed-2-column>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-7" name="tab-group-preprocessing">
<label for="tab-preprocessing-7"><b><code>#![globals]</code></b></label>
<panel><div class="color-header undefined-color-3">

<!-- ```
// Attributes usually found in toplevel project file.
#![no_std]
#![feature(xxx)]
``` -->
<fixed-3-column  class="color-header special_example">

这些属性对整个 crate 或应用程序都生效:

| 外部可选项   | 作用 | 说明 |
|--------|---| ----------|
| `#![no_std]` | `C` | 不自动引入 **`std`**{{ std(page="std/") }} ; 而使用 **`core`**{{ std(page="core/") }} . {{ ref(page="names/preludes.html#the-no_std-attribute") }} |
| `#![no_implicit_prelude]` | `CM` | 不添加 **`prelude`**{{ std(page="std/prelude/index.html") }}, 需要手动引入 `None`, `Vec` 等 {{ ref(page="names/preludes.html#the-no_implicit_prelude-attribute") }} |
| `#![no_main]` |  `C` | 不触发应用程序中的 `main()`, 允许自定义启动. {{ ref(page="crates-and-source-files.html#the-no_main-attribute") }}|

<!-- | `#![no_builtins]` | `C` | Does ... something ... probably important. {{ todo() }} {{ ref(page="attributes/codegen.html#the-no_builtins-attribute") }}| -->

{{ tablesep() }}

| 内部可选项   | 作用 | 说明 |
|--------|---| ----------|
| `#![feature(a, b, c)]` | `C` | 依赖于某个永远无法被稳定下来的特性, _参见_ [**Unstable Book**](https://doc.rust-lang.org/unstable-book/the-unstable-book.html). {{ experimental() }} |

{{ tablesep() }}

| 构建选项   | 作用 | 说明 |
|--------|---| ----------|
| `#![windows_subsystem = "x"]` | `C` | 在 Windows 上创建 `console` 或 `windows` 应用程序. {{ ref(page="runtime.html#the-windows_subsystem-attribute") }} {{ esoteric() }} |
| `#![crate_name = "x"]` | `C`  | 当不使用 `cargo` 时指定当前 crate 名. {{ todo() }} {{ ref(page="crates-and-source-files.html#the-crate_name-attribute") }} {{ esoteric() }} |
| `#![crate_type = "bin"]` | `C`  | 指定当前 crate 类型 (`bin`, `lib`, `dylib`, `cdylib`, ...). {{ ref(page="linkage.html") }} {{ esoteric() }} |
| `#![recursion_limit = "123"]` | `C` | 设置解引用和宏展开等的 _编译期_ 递归限制 {{ ref(page="attributes/limits.html#the-recursion_limit-attribute") }} {{ esoteric() }} |
| `#![type_length_limit = "456"]` | `C` | 限制类型替换的最大数量. {{ ref(page="attributes/limits.html#the-type_length_limit-attribute") }} {{ esoteric() }} |


{{ tablesep() }}

| Handler   | 作用 | 说明 |
|--------|---|----------|
| `#[panic_handler]` | `F` | 使函数 `fn f(&PanicInfo) -> !` 作为 **panic handler**. {{ ref(page="runtime.html#the-panic_handler-attribute") }} |
| `#[global_allocator]` | `S` | 标记静态实例. `GlobalAlloc` {{ std(page="alloc/alloc/trait.GlobalAlloc.html") }} **全局分配器**. {{ ref(page="runtime.html#the-global_allocator-attribute") }}|


</fixed-3-column>


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-4" name="tab-group-preprocessing">
<label for="tab-preprocessing-4"><b><code>#[code]</code></b></label>
<panel><div class="color-header undefined-color-3">

这些属性主要用于控制相关代码:

<fixed-3-column  class="color-header special_example">

| 开发者体验 | 作用 | 说明 |
|-------|---|-------------|
| `#[non_exhaustive]` | `T` | 标记 `struct` 或 `enum` 未来有可能发生变更. {{ ref(page="attributes/type_system.html#the-non_exhaustive-attribute") }}|
| `#[path = "x.rs"]` | `M` | 从非标准文件中获取模块. {{ ref(page="items/modules.html#the-path-attribute") }}|

{{ tablesep() }}

| 代码生成 | 作用 | 声明 |
|-------|---|-------------|
| `#[inline]` | `F` | 建议编译器将函数调用编译为内嵌代码. {{ ref(page="attributes/codegen.html#the-inline-attribute") }}|
| `#[inline(always)]` | `F` | 要求编译器必须将此函数调用内嵌. {{ ref(page="attributes/codegen.html#the-inline-attribute") }}|
| `#[inline(never)]` | `F` | 告诉编译器即便该函数可以内嵌也不要这么做. {{ ref(page="attributes/codegen.html#the-inline-attribute") }} |
| `#[cold]` | `F` | 标记该函数可能并不需要被调用. {{ ref(page="codegen.html#the-cold-attribute") }}|
| `#[target_feature(enable="x")]` | `F` | 启用 `unsafe fn` 下支持的某些 CPU 特性 (如 `avx2`). {{ ref(page="attributes/codegen.html#the-target_feature-attribute") }}|
| `#[track_caller]` | `F` | 允许 `fn` 追溯调用者 **`caller`**{{ std(page="core/panic/struct.Location.html#method.caller") }}  已获得更详细的 panic 信息. {{ ref(page="attributes/codegen.html#the-track_caller-attribute") }}|
| `#[repr(X)]`<sup>1</sup>  | `T`  | 用另一种指定的表示法来替换 **`rust`** {{ ref(page="type-layout.html#the-default-representation") }} 默认的: |
| {{ tab() }} `#[repr(C)]` | `T`  | 使用兼容 C (当 FFI) 且可预测的 (当 `transmute`) 内存布局. {{ ref(page="type-layout.html#the-c-representation") }}|
| {{ tab() }} `#[repr(C, u8)]` | `enum`  | 使得该 `enum` 变体以指定类型表示. {{ ref(page="type-layout.html#the-c-representation") }}|
| {{ tab() }} `#[repr(transparent)]` | `T`  | 使得单元素类型内存布局与其内部字段一致. {{ ref(page="type-layout.html#the-transparent-representation") }}|
| {{ tab() }} `#[repr(packed(1))]` | `T`  | 结构体及其字段向低位对齐, 可能会 UB. {{ ref(page="type-layout.html#the-alignment-modifiers") }}|
| {{ tab() }} `#[repr(align(8))]` | `T`  | 结构体对齐提升, 比如用于 SIMD 类型. {{ ref(page="type-layout.html#the-alignment-modifiers") }}|

<!-- {{ tablesep() }}

| Representation | On | Explanation |
|-------|---|-------------|
| `-` | `T`  | In absence of `#[repr]` the **`rust` representation** is used {{ ref(page="type-layout.html#the-default-representation") }} |
| `#[repr(C)]` | `T`  | Use a predictable, C-compatible representation. {{ ref(page="type-layout.html#the-c-representation") }}|
| `#[repr(C, u8)]` | `enum`  | Give `enum` discriminant the specified type. {{ ref(page="type-layout.html#the-c-representation") }}|
| `#[repr(transparent)]` | `T`  | Give single-element type same layout as contained field. {{ ref(page="type-layout.html#the-transparent-representation") }}|
| `#[repr(packed(1))]` | `T`  | Lower alignment of struct and contained fields, mildly UB prone. {{ ref(page="type-layout.html#the-alignment-modifiers") }}|
| `#[repr(align(8))]` | `T`  | Raise alignment of struct to given value, e.g., for SIMD types. {{ ref(page="type-layout.html#the-alignment-modifiers") }}| -->

<footnotes>

<sup>1</sup> 某些标识装饰器可以合并在一起写, 如 `#[repr(C, packed(1))]`.

</footnotes>

{{ tablesep() }}

| 链接 | 作用 | 说明 |
|-------|---|-------------|
| `#[no_mangle]` | `*` | 使该项编译后如其名, 不添加乱七八糟的字符.  {{ ref(page="abi.html#the-no_mangle-attribute") }}|
| `#[no_link]` | `X` | 当仅使用宏时不链接 `extern crate`. {{ ref(page="items/extern-crates.html#the-no_link-attribute") }}|
| `#[link(name="x", kind="y")]` | `X`  | 链接本地库, 表明符号表将从这里查找. {{ ref(page="items/external-blocks.html#the-link-attribute") }}|
| `#[link_name = "foo"]` | `F`  | 结息 `extern fn` 用的符号名. {{ ref(page="items/external-blocks.html#the-link_name-attribute") }}|
| `#[link_section = ".sample"]` | `FS`  | 指定对象文件的段名. {{ ref(page="abi.html#the-link_section-attribute") }}|
| `#[export_name = "foo"]` | `FS` | 将 `fn` 或 `static` 以别名导出. {{ ref(page="abi.html#the-export_name-attribute") }}|
| `#[used]` | `S`  | 不要优化掉看似未使用过的 `static` 变量. {{ ref(page="abi.html#the-used-attribute") }}|



</fixed-3-column>

</div></panel></tab>




<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-3" name="tab-group-preprocessing">
<label for="tab-preprocessing-3"><b><code>#[quality]</code></b></label>
<panel><div class="color-header undefined-color-3">

Rust 工具链利用这些属性提升代码质量:

<fixed-3-column  class="color-header special_example">

| 代码模式 | 作用 | 说明 |
|-------|---|-------------|
| `#[allow(X)]` | `*` | 让 `rustc` 或 `clippy` ... 允许 `X` 可能导致的警告. {{ ref(page="attributes/diagnostics.html#lint-check-attributes") }} |
| `#[warn(X)]` <sup>1</sup> | `*` |  ... 产生警告, 结合 `clippy` lint. {{ hot() }} {{ ref(page="attributes/diagnostics.html#lint-check-attributes") }} |
| `#[deny(X)]` <sup>1</sup> | `*` |  ... 编译失败. {{ ref(page="attributes/diagnostics.html#lint-check-attributes") }} |
| `#[forbid(X)]` <sup>1</sup> | `*` | ... 编译失败并禁用后续的 `allow` 声明. {{ ref(page="attributes/diagnostics.html#lint-check-attributes") }} |
| `#[deprecated = "msg"]` | `*` | 让用户知道你曾经犯了个错误. {{ ref(page="diagnostics.html#the-deprecated-attribute") }}|
| `#[must_use = "msg"]` | `FTX` |  让编译器检查返回值确被调用者 _处理过_ 了. {{ hot() }} {{ ref(page="attributes/diagnostics.html#the-must_use-attribute") }}|

<footnotes>

<sup>1</sup> 关于在 crate 中什么是 _最佳实践_ 上有过不少争论. 通常多人活跃维护的 crate 可能会提供更激进的 `deny` 或 `forbid` lint; 不定期更新的项目则可能只标记一个 `warn` (不保证未来的编译器或者 `clippy` 不会突然对此产生警告).

</footnotes>

{{ tablesep() }}

</fixed-3-column>

<fixed-3-column  class="color-header special_example">

| 测试 | 作用 | 说明 |
|-------|---|-------------|
| `#[test]` | `F` | 标记该函数为测试, 通过 `cargo test` 运行. {{ hot() }} {{ ref(page="attributes/testing.html#the-test-attribute") }}|
| `#[ignore = "msg"]` | `F` | 编译但目前不运行某些 `#[test]`. {{ ref(page="attributes/testing.html#the-ignore-attribute") }}|
| `#[should_panic]` | `F` | 该测试必须 `panic!()` 才算成功. {{ ref(page="attributes/testing.html#the-ignore-attribute") }}|
| `#[bench]` | `F` | 在 `bench/` 中标记该函数为性能测试, 通过 `cargo bench` 运行. {{ experimental() }} {{ ref(page="") }}|

{{ tablesep() }}


| 格式化 | 作用 | 说明 |
|-------|---|-------------|
| `#[rustfmt::skip]` |  `*` | 防止 `cargo fmt` 自动清理该项. {{ link(url="https://github.com/rust-lang/rustfmt") }}|
| `#![rustfmt::skip::macros(x)]` |  `CM` | ... 防止自动清理宏 `x`. {{ link(url="https://github.com/rust-lang/rustfmt") }}|
| `#![rustfmt::skip::attributes(x)]` |  `CM` | ... 防止自动清理属性 `x`. {{ link(url="https://github.com/rust-lang/rustfmt") }}|

</fixed-3-column>

{{ tablesep() }}

<fixed-3-column class="color-header special_example extra-wide">


| 文档 | 作用 | 说明 |
|-------|---|-------------|
| `#[doc = "Explanation"]` | `*` | 与 `///` 文档注释效果相同. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html") }} |
| `#[doc(alias = "other")]` | `*` | 让用户用该别名也能在文档中搜索到该项. {{ link(url="https://github.com/rust-lang/rust/issues/50146") }} |
| `#[doc(hidden)]` | `*` | 在文档中隐藏. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#dochidden") }} |
| `#![doc(html_favicon_url = "")]` | `C` | 设置文档图标 `favicon`. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#html_favicon_url") }}|
| `#![doc(html_logo_url  = "")]` | `C` | 设置文档 Logo. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#html_logo_url") }}|
| `#![doc(html_playground_url  = "")]` | `C` | 用给定服务生成 `运行` 按钮. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#html_playground_url") }}|
| `#![doc(html_root_url  = "")]` | `C` | 外部 crate 的基础链接. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#html_root_url") }}|
| `#![doc(html_no_source)]` | `C` | 生成的文档中不要包含源代码. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#html_no_source") }}|

<!-- | `#![doc(issue_tracker_base_url  = "")]` | `C` | Mostly for `std::`, where issue numbers link. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#issue_tracker_base_url") }}| -->

</fixed-3-column>




</div></panel></tab>




<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-8" name="tab-group-preprocessing">
<label for="tab-preprocessing-8"><b><code>#[macros]</code></b></label>
<panel><div class="color-header undefined-color-3">

<fixed-3-column  class="color-header special_example">

这些属性用于创建或者修饰宏:

| 声明宏 | 作用 | 说明 |
|-------|---|-------------|
| `#[macro_export]` |  `!` | 将 `macro_rules!` 导出为 `pub` 到 crate 层级 {{ ref(page="macros-by-example.html#path-based-scope") }}|
| `#[macro_use]` | `MX` | 让宏得以运行在模块里; 或从 `extern crate` 导入. {{ ref(page="macros-by-example.html#the-macro_use-attribute") }}|

{{ tablesep() }}

| 过程宏 | 作用 | 说明 |
|-------|---|-------------|
| `#[proc_macro]` | `F`  | 标记 `fn` 为 **函数式** 过程宏, 调用方式如 `m!()`. {{ ref(page="procedural-macros.html#function-like-procedural-macros") }}|
| `#[proc_macro_derive(Foo)]` | `F`  | 标记 `fn` 为 **Derive 宏**, 调用方式如 `#[derive(Foo)]`. {{ ref(page="procedural-macros.html#derive-macros") }}|
| `#[proc_macro_attribute]` | `F`  | 标记 `fn` 为 **属性宏**, 调用方式如一个新的 `#[x]`. {{ ref(page="procedural-macros.html#attribute-macros") }}|

{{ tablesep() }}

| Derive | 作用 | 说明 |
|-------|---|-------------|
| `#[derive(X)]` | `T` | 通过某些过程宏提供 `trait X` 的 `impl` . {{ hot() }} {{ ref(page="") }}|

<!-- | `#[derive(Eq)]` |  | xxx{{ ref(page="") }}|
| `#[derive(PartialEq)]` | |  xxx|
| `#[derive(Ord)]` | |  xxx|
| `#[derive(PartialOrd)]` | |  xxx|
| `#[derive(Clone)]` | |  xxx|
| `#[derive(Copy)]` | |  xxx|
| `#[derive(Hash)]` | |  xxx|
| `#[derive(Default)]` | |  xxx|
| `#[derive(Debug)]` | |  xxx| -->


</fixed-3-column>


</div></panel></tab>






<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-5" name="tab-group-preprocessing">
<label for="tab-preprocessing-5"><b><code>#[cfg]</code></b></label>
<panel><div class="color-header undefined-color-3">

这些属性用于条件编译:

<fixed-3-column class="color-header special_example extra-wide">

| 配置属性 | 作用 | 说明 |
|-------|---|-------------|
| `#[cfg(X)]` | `*` | 如果提供了配置 `X` 则编译. {{ ref(page="conditional-compilation.html#the-cfg-attribute") }}|
| `#[cfg(all(X, Y, Z))]` | `*` | 如果提供了所有配置则编译. {{ ref(page="conditional-compilation.html#conditional-compilation") }}|
| `#[cfg(any(X, Y, Z))]` | `*` | 如果提供了任意配置则编译. {{ ref(page="conditional-compilation.html#conditional-compilation") }}|
| `#[cfg(not(X))]` | `*` | 如果未提供 `X` 则编译. {{ ref(page="conditional-compilation.html#conditional-compilation") }}|
| `#[cfg_attr(X, foo = "msg")]` | `*` | 如果提供了 `X` 则标记 `#[foo = "msg"]`. {{ ref(page="conditional-compilation.html#the-cfg_attr-attribute") }}|

{{ tablesep() }}

> ⚠️ Note, options can generally be set multiple times, i.e., the same key can show up with multiple values. One can expect `#[cfg(target_feature = "avx")]` **和** `#[cfg(target_feature = "avx2")]` to be true at the same time.

{{ tablesep() }}

| 已知选项 | 作用 | 说明 |
|-------|---|-------------|
| `#[cfg(target_arch = "x86_64")]` | `*` | 指定编译目标 CPU 架构. {{ ref(page="conditional-compilation.html#target_arch") }}|
| `#[cfg(target_feature = "avx")]` | `*` | 判断某类指令集是否可用. {{ ref(page="conditional-compilation.html#target_feature") }}|
| `#[cfg(target_os = "macos")]` | `*` | 运行的目标操作系统. {{ ref(page="conditional-compilation.html#target_os") }}|
| `#[cfg(target_family = "unix")]` | `*` | 运行的某一类目标操作系统. {{ ref(page="conditional-compilation.html#target_family") }}|
| `#[cfg(target_env = "msvc")]` | `*` | 指定如何让操作系统链接 DLL 和函数. {{ ref(page="conditional-compilation.html#target_env") }}|
| `#[cfg(target_endian = "little")]` | `*` | 你优秀的无开销自定义协议失败的主要原因. {{ ref(page="conditional-compilation.html#target_endian") }}|
| `#[cfg(target_pointer_width = "64")]` | `*` | 指针位数, 即 `usize` 和 CPU 字长. {{ ref(page="conditional-compilation.html#target_pointer_width") }}|
| `#[cfg(target_vendor = "apple")]` | `*` |  目标设备制造商. {{ ref(page="conditional-compilation.html#target_vendor") }}|
| `#[cfg(debug_assertions)]` | `*` | 标记为 `debug_assert!()` 的和类似调试语句将会 panic. {{ ref(page="conditional-compilation.html#debug_assertions") }}|
| `#[cfg(proc_macro)]` | `*` | 当 crate 编译为过程宏时. {{ ref(page="conditional-compilation.html#proc_macro") }}|
| `#[cfg(test)]` | `*` | 当 `cargo test` 时编译. {{ hot() }} {{ ref(page="conditional-compilation.html#test") }}|
| `#[cfg(feature = "serde")]` | `*` | 当 crate 启用了编译选项 `serde` 时. {{ hot() }} {{ ref(page="conditional-compilation.html#conditional-compilation") }}|

</fixed-3-column>



</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-6" name="tab-group-preprocessing">
<label for="tab-preprocessing-6"><b><code>build.rs</code></b></label>
<panel><div class="color-header undefined-color-3">

预编译脚本可用的环境变量和输出配置.

<fixed-2-column class="color-header special_example extra-wide">

| 输入环境 | 说明 {{ link(url="https://doc.rust-lang.org/cargo/reference/environment-variables.html") }} |
|-------|-------------|
| `CARGO_FEATURE_X` |  每个启用的 `x` 都将设置一个这样的环境变量.  |
| {{ tab() }} `CARGO_FEATURE_SERDE` |  如果启用了 `serde` 特性. |
| {{ tab() }} `CARGO_FEATURE_SOME_FEATURE` | 如果启用了 `some-feature` 特性; 横线 `-` 会转为下划线 `_`. |
| `CARGO_CFG_X` | Exposes cfg's; joins mult. opts. by `,` and converts `-` to `_`.|
| {{ tab() }} `CARGO_CFG_TARGET_OS=macos` |  如果 `target_os` 为 `macos`. |
| {{ tab() }} `CARGO_CFG_TARGET_FEATURE=avx,avx2` |  如果 `target_feature` 设置为了 `avx` 和 `avx2`. |
| `OUT_DIR` |  输出目录. |
| `TARGET` |  编译结果目录. |
| `HOST` |  指定运行该构建脚本的编译器. |
| `PROFILE` |  可以是 `debug` 或者 `release`. |

<footnotes>

在 `build.rs` 通过 `env::var()?` 可以访问. 列表不完整.

</footnotes>

</fixed-2-column>

<fixed-2-column class="color-header special_example extra-wide">

{{ tablesep() }}

| 输出字符串 | 说明 {{ link(url="https://doc.rust-lang.org/cargo/reference/build-scripts.html") }} |
|-------|-------------|
| `cargo:rerun-if-changed=PATH` | (仅当) `PATH` 变化时运行 `build.rs`. |
| `cargo:rerun-if-env-changed=VAR` | (仅当) 环境 `VAR` 变化时运行 `build.rs`. |
| `cargo:rustc-link-lib=[KIND=]NAME` | 通过 `-l` 选项链接到本地库. |
| `cargo:rustc-link-search=[KIND=]PATH` | 通过 `-L` 选项设置本地库搜索路径. |
| `cargo:rustc-flags=FLAGS` | 为编译器添加自定义标识. {{ todo() }} |
| `cargo:rustc-cfg=KEY[="VALUE"]` | 声明给定 `cfg` 选项以用于后续编译. |
| `cargo:rustc-env=VAR=VALUE ` | 声明在 crate 编译期间可以通过 `env!()` 访问的变量. |
| `cargo:rustc-cdylib-link-arg=FLAG ` | 当构建 `cdylib` 时的连接器标识. |
| `cargo:warning=MESSAGE` | 产生编译器警告. |

<footnotes>

在 `build.rs` 通过 `println!()` 调用. 列表不完整.

</footnotes>

</fixed-2-column>

</div></panel></tab>


</tabs>


<footnotes>

表格列 _作用_ 说明如下: <br>
`C` 标识作用在 crate 层级上 (常在顶级文件中声明作 `#![my_attr]`). <br>
`M` 标识作用在模块上. <br>
`F` 标识作用在函数上. <br>
`S` 标识作用在静态区上. <br>
`T` 标识作用在类型上. <br>
`X` 标识某些特殊场景上. <br>
`!` 标识作用在宏上. <br>
`*` 标识作用在任意项上. <br>

</footnotes>


---

# 与类型打交道


## 类型, Trait, 泛型 {#types-traits-generics}

允许用户 _自定义类型_ 并减少代码重复.

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-types-1" name="tab-group-types" checked>
<label for="tab-types-1"><b>类型 & Trait</b></label>
<panel><div>


<!-- Section -->
<generics-section id="ttg-types">
<header>类型</header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
    </entry>
    <entry>
        <type class="composed"><code>String</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Device</code></type>
    </entry>
</mini-zoo>

- 以给定语句或布局设置值.

<mini-table>

| 类型 |   值 |
| --- | --- |
| `u8`  |  <code>{ 0<sub>u8</sub>, 1<sub>u8</sub>, ..., 255<sub>u8</sub> }</code> |
| `char`  | `{ 'a', 'b', ... '🦀' }` |
| `struct S(u8, char)`  | <code>{ (0<sub>u8</sub>, 'a'), ... (255<sub>u8</sub>, '🦀') }</code> |

<subtitle>样例类型和值</subtitle>

</mini-table>

</description>
</generics-section>


<!-- Section -->
<generics-section id="ttg-equivalence">
<header>类型等价和转换</header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
    </entry>
    <entry>
        <type class="primitive"><code>&u8</code></type>
    </entry>
    <entry>
        <type class="primitive"><code>&mut u8</code></type>
    </entry>
    <entry>
        <type class="primitive"><code>[u8; 1]</code></type>
    </entry>
    <entry>
        <type class="composed"><code>String</code></type>
    </entry>
</mini-zoo>



<!-- - Question: which of the types above is different from all others?
    - Trick question: all of these types are totally different -->
- 看起来类似却完全不同的 &nbsp; `u8`, &nbsp;&nbsp; `&u8`, &nbsp;&nbsp; `&mut u8` 类型.
- 任意 `t: T` 仅接受精确类型 `T` 的值, 如:
    - `f(0_u8)` 不能以 `f(&0_u8)` 调用,
    - `f(&mut my_u8)` 不能以 `f(&my_u8)` 调用,
    - `f(0_u8)` 不能以 `f(0_i8)` 调用.

>  确实, 作为类型而言, `0 != 0` (在数学层面)! 在语言层面, 并没有为了你愉快地使用而定义了这样一个相等比较 <code>==(0<sub>u8</sub>, 0<sub>u16</sub>)</code>.

<mini-table>

| 类型 | 值 |
| --- | --- |
| `u8`  | <code>{ 0<sub>u8</sub>, 1<sub>u8</sub>, ..., 255<sub>u8</sub> }</code> |
| `u16`  | <code>{ 0<sub>u16</sub>, 1<sub>u16</sub>, ..., 65_535<sub>u16</sub> }</code> |
| `&u8`  | <code>{ 0xffaa<sub>&u8</sub>, 0xffbb<sub>&u8</sub>, ... }</code> |
| `&mut u8`  | <code>{ 0xffaa<sub>&mut u8</sub>, 0xffbb<sub>&mut u8</sub>, ... }</code> |

<subtitle>值和类型的不同</subtitle>

</mini-table>



- 不过在某些情况下, Rust 可能会进行 **类型转换**<sup>1</sup>
    - **转换** 指的是手动进行类型转换, `0_i8 as u8`
    - **强转** {{ above(target="#language-sugar") }} 将在安全的情况下自动转换 <sup>2</sup>, `let x: &u8 = &mut 0_u8;`




<footnotes>

<sup>1</sup> 从一类值 (如 `u8`) 转换和强转到另一类值 (如 `u16`) 时有可能会增加 CPU 指令以完成该操作; 一个类型是某一个类型一部分的叫做**子类型** (比如 `u8` 是 `u16` 的子类型所以 `0_u8` 和 `0_u16` 形式一致), 这种转换在编译期间就可以完成. Rust 并不为规则类型实现子类型转换 (`0_u8` _确实_ 不同于 `0_u16`), 但生命周期却是有的. {{ link(url = "https://featherweightmusings.blogspot.com/2014/03/subtyping-and-coercion-in-rust.html") }}

<sup>2</sup> 安全并不仅是简单的物理保证 (比如 <code>&u8</code> 无法变为 <code>&u128</code>), 并且告诉我们“历史经验表明这样转换确实会导致编程错误”.

</footnotes>

</description>
</generics-section>



<!-- Section -->
<generics-section id="ttg-impl-s">
<header>实现 &mdash; <code>impl S { }</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
        <impl><code>impl { ... }</code></impl>
    </entry>
    <entry>
        <type class="composed"><code>String</code></type>
        <impl><code>impl { ... }</code></impl>
    </entry>
    <entry>
        <type class="composed"><code>Port</code></type>
        <impl><code>impl { ... }</code></impl>
    </entry>
</mini-zoo>

```
impl Port {
    fn f() { ... }
}
```

- 类型总要有对应的实现, 比如 `impl Port {}` 的类型 _关联_ 行为有:
    - **关联函数** `Port::new(80)`
    - **方法** `port.close()`

> 这里的 _关联_ 更像是一个哲学概念而非技术概念, 没什么能阻止你使用 `u8::play_sound()` (只要你乐意).


</description>
</generics-section>


<!-- Section -->
<generics-section id="ttg-traits">
<header>Trait &mdash; <code>trait T { }</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
    <entry>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
    </entry>
    <entry>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
    </entry>
    <entry>
        <trait-impl>⌾ <code>ShowHex</code></trait-impl>
    </entry>
</mini-zoo>

- **Trait**
    - 是一种“抽象”行为,
    - trait 作者语义上声明了 _该 trait 意为 X_,
    - 别人也可以为其他类型实现相关行为 (“特化”).
- 可以认为 trait 是类型的一种“成员列表”:


<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Copy Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>u16</code></td></tr>
        <tr><td><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Clone Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>String</code></td></tr>
        <tr><td><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Sized Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>char</code></td></tr>
        <tr><td><code>Port</code></td></tr>
        <tr><td><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>

<subtitle>Trait 作为成员列表, <code>Self</code> 指向其包含的类型.</subtitle>

</mini-table>


- **无论谁是该成员列表的一部分, 都将遵守列表的行为.**
- Trait 也可以包含关联方法和函数等.

```
trait ShowHex {
    // 要求按文档描述实现.
    fn as_hex() -> String;

    // 由 trait 作者提供.
    fn print_hex() {}
}
```

<mini-zoo class="zoo">
    <entry>
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
</mini-zoo>

```
trait Copy { }
```

- 无方法 Trait 通常叫做 **标记 trait**.
- `Copy` 是一种标记 trait, 表示 _内存可以被按位复制_.

<mini-zoo class="zoo">
    <entry>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
    </entry>
</mini-zoo>


- 某些 trait 完全脱离显式控制.
- `Sized` 是由编译器提供用于 _已知大小_ 的类型; 类型大小要么已知, 要么未知.


</description>
</generics-section>


<!-- Section -->
<generics-section id="xxx">
<header>为类型实现 Trait &mdash; <code>impl T for S { }</code></header>
<description>


```
impl ShowHex for Port { ... }
```
- 实现“某些”类型的 Trait.
- 实现 `impl A for B` 将添加类型 `B` 到该 Trait 的成员列表:

<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>ShowHex Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Port</code></td></tr>
    </tbody>
</table>

</mini-table>
</mini-table>

- 你可以认为类型被打上了不同的“标签”:

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
        <impl><code>impl { ... }</code></impl>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
    <entry>
        <type class="composed"><code>Device</code></type>
        <impl><code>impl { ... }</code></impl>
        <trait-impl>⌾ <code>Transport</code></trait-impl>
    </entry>
    <entry>
        <type class="composed"><code>Port</code></type>
        <impl><code>impl { ... }</code></impl>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
        <trait-impl>⌾ <code>ShowHex</code></trait-impl>
    </entry>
</mini-zoo>

</description>
</generics-section>




<!-- Section -->
<generics-section id="xxx">
<header>Trait vs. 接口</header>
<description>


<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Venison</code></type>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px; width: 130px;">
    <person></person>
    <entry>
        <code style="text-align:center; width: 100%;"></code>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>venison.eat()</code>
    </entry>
</mini-zoo>

{{ tablesep() }}

**接口 (Interface)**

- 在 **Java** 中, Alice 创建了接口 `Eat`.
- 当 Bob 实现 `Venison` 时, 他需要决定是否为 `Venison` 实现 `Eat`.
- 换言之, 所有关系必须显式地在类型定义时就表明.
- 当使用 `Venison` 时, Santa 才可以使用由 `Eat` 定义的行为:

```
// Santa 导入 `Venison` 创建的对象可以 `eat()`.
import food.Venison;

new Venison("rudolph").eat();
```


{{ tablesep() }}
{{ tablesep() }}


<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Venison</code></type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>👩‍🦰</person> / <person>🧔</person>
    <entry>
        <type class="composed"><code>Venison</code></type>
        <code style="text-align:center; width: 100%;">+</code>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>venison.eat()</code>
    </entry>
</mini-zoo>

{{ tablesep() }}

**Trait**

- 在 **Rust** 中, Alice 创建了 trait `Eat`.
- Bob 创建了类型 `Venison` 并决定暂不实现 `Eat` (他甚至不知道有 `Eat` 这么个东西).
- 某人<sup>*</sup> 后来觉得为 `Venison` 添加 `Eat` 是个好主意.
- 那么当 Santa 使用 `Venison` 时需要另外导入 `Eat`:

```
// Santa 需要导入 `Venison` 用于创建, 并导入 `Eat` 用于调用 trait 方法.
use food::Venison;
use tasks::Eat;

// 吼吼吼
Venison::new("rudolph").eat();
```

<footnotes>

<sup>*</sup> 为避免两个人实现不同的 `Eat`, Rust 限制了 Alice 和 Bob 能做的事情; 即, 一个 `impl Eat for Venison` 仅能在 `Venison` 所在的 crate 或 `Eat` 所在的 crate 中实现. 这被称作 trait 实现的“孤儿原则”. {{todo()}}

</footnotes>


</description>
</generics-section>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-types-2" name="tab-group-types">
<label for="tab-types-2"><b>泛型</b></label>
<panel><div>


<!-- Section -->
<generics-section id="xxx">
<header>类型构造 &mdash; <code>Vec&lt;&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Vec&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Vec&lt;char&gt;</code></type>
    </entry>
</mini-zoo>

- `Vec<u8>` 是“字节向量”类型; `Vec<char>` 是“字符向量”类型, 但 `Vec<>` 是什么?

<mini-table>

| 构造 |   值 |
| --- | --- |
| `Vec<u8>`  |  `{ [], [1], [1, 2, 3], ... }` |
| `Vec<char>`  |  `{ [], ['a'], ['x', 'y', 'z'], ... }` |
| `Vec<>`  |  - |

<subtitle>类型和类型构造</subtitle>

</mini-table>



<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>Vec&lt;&gt;</code></type>
    </entry>
</mini-zoo>

- `Vec<>` 为非类型, 不占内存, 也不会生成代码.
- `Vec<>` 为 **类型构造器**, 是“模板”或者“创建类型的表单”
    - 允许第三方通过参数构造特定类型,
    - 仅当声明 `Vec<UserType>` 时才成为真正的类型.

</description>
</generics-section>


<!-- Section -->
<generics-section id="xxx">
<header>泛型参数 &mdash; <code>&lt;T&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>[T; 128]</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&T</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&mut T</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>S&lt;T&gt;</code></type>
    </entry>
</mini-zoo>

- `Vec<>` 的参数常作 `T` 故有 `Vec<T>`.
- `T` “类型的变量名”可以特化为 `Vec<f32>`, `S<u8>`, &hellip;


<mini-table>

| 类型构造器 |  产生一类 |
| --- | --- |
| `struct Vec<T> {}`  |  `Vec<u8>`, `Vec<f32>`, `Vec<Vec<u8>>`, ... |
| `[T; 128]`  |  `[u8; 128]`, `[char; 128]`, `[Port; 128]` ... |
| `&T`  |  `&u8`, `&u16`, `&str`,  ... |

<subtitle>类型和类型构造器</subtitle>

</mini-table>


```
// S<> 是个带有参数 T 的类型构造器; 用户可以提供 T 的任意实际类型.
struct S<T> {
    x: T
}

// 实际使用中必须为 T 指定实际类型.
fn f() {
    let x: S<f32> = S::new(0_f32);
}

```

</description>
</generics-section>


<!-- Section -->
<generics-section id="xxx">
<header>常量泛型 &mdash; <code>[T; N]</code> and <code>S&lt;const N: usize&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>[T; n]</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>S&lt;const N&gt;</code></type>
    </entry>
</mini-zoo>

- 某些类型构造器不仅接受指定类型, 还接受 **指定常量**.
- `[T; n]` 构造出一个有 `n` 个 `T` 类型元素的数组.
- 自定义类型可声明为 `MyArray<T, const N: usize>`.

<mini-table>

| 类型构造器 |  产生一类 |
| --- | --- |
| `[u8; N]`  |  `[u8; 0]`, `[u8; 1]`, `[u8; 2]`, ... |
| `struct S<const N: usize> {}`  |  `S<1>`, `S<6>`, `S<123>`,  ... |

<subtitle>基于常量的类型构造器</subtitle>

</mini-table>


```
let x: [u8; 4]; // "4 字节数组"
let y: [f32; 16]; // "16 浮点数组"

// `MyArray` 是个需要特定类型 `T` 和特定大小 `N` 的类型构造器.
struct MyArray<T, const N: usize> {
    data: [T; N],
}
```

</description>
</generics-section>


<!-- Section -->
<!-- <generics-section id="xxx">
<header>Generics in Types</header>
<description>

</description>
</generics-section> -->




<!-- Section -->
<generics-section id="xxx">
<header>约束 (简单) &mdash; <code>where T: X</code></header>
<description>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="generic dotted"><code>Num&lt;T&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <person>🎅</person>
    <entry>
        <type class="composed"><code>Num&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Num&lt;f32&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Num&lt;Cmplx&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 50px;">&nbsp;</code>
    </narrow-entry>
    <entry class="">
        <type class="primitive"><code>u8</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Dim</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="composed"><code>Port</code></type>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
        <trait-impl>⌾ <code>ShowHex</code></trait-impl>
    </entry>
</mini-zoo>

- 如果 `T` 可以为任意类型, 那我们怎么确定能为它实现这么一个 `Num<T>`?
- 参数**约束**:
    - 限制了允许什么样的类型 (**trait 约束**) 或值 (**常量约束** {{ todo() }}),
    - 然后就可以应用这些限制了!
- Trait 约束像是一种“行为检查”:

<mini-table>

<div style="display: inline-block;">

```
// 类型仅能由某些实现了 `Absolute` 的 `T` 实现.
struct Num<T> where T: Absolute {
    ...
}

```

</div>


<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Absolute Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>u16</code></td></tr>
        <tr><td><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>
</mini-table>


<!--
// Constant `N` must be `usize`
struct Arrayf32<const N: usize> {
    data: [f32; N],
} -->

<footnotes>

此处我们为该结构体添加了约束. 实践中则最好在 impl 块中添加约束, 详见下文.

</footnotes>

<!-- > Note to self, is `const N: usize` a "const bound"? It seemingly acts as one, limiting the choice of values for N (albeit to specific types only). -->

</description>
</generics-section>


<!-- Section -->
<generics-section id="xxx">
<header>约束 (计算) &mdash; <code>where T: X + Y</code></header>
<description>

<mini-zoo class="zoo">
    <entry class="grayed">
        <type class="primitive"><code>u8</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Dim</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="primitive"><code>f32</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="primitive"><code>char</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Cmplx</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Dim</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
        <trait-impl>⌾ <code>DirName</code></trait-impl>
        <trait-impl>⌾ <code>TwoD</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="composed"><code>Car</code></type>
        <trait-impl>⌾ <code>DirName</code></trait-impl>
    </entry>
</mini-zoo>



```
struct S<T>
where
    T: Absolute + Dim + Mul + DirName + TwoD
{ ... }
```

- 过长的 trait 约束像是一种威胁.
- 实践中, 每个 `+ X` 声明都会减少这里能用的类型.

</description>
</generics-section>



<!-- Section -->
<generics-section id="xxx">
<header>实现一类 &mdash; <code>impl&lt;&gt;</code></header>
<description>

{{ tablesep() }}

```
impl<T> S<T> where T: Absolute + Dim + Mul {
    fn f(&self, x: T) { ... };
}
```
可以读作:
- 这里是对任意类型 `T` 一个实现 (即 `impl <T>` 部分),
- 该类型必须同时满足 `Absolute + Dim + Mul` 这些 Trait 约束,
- 可以添加一个实现块 `S<T>`,
- 以及包含更多方法 ...

可以将类如 `impl<T> ... {} ` 的代码看作**对一类行为的抽象实现**. 尤其使得第三方透明地实例化与类型构造器如何实例化类似:

```
// 当编译器遇到如下代码时将会
// - 检查 `0` 和 `x` 是否满足 `T` 的要求
// - 创建两个版本的 `f`, 一个给 `char`, 另一个给 `u32`.
// - 并基于“一类实现”来提供
s.f(0_u32);
s.f('x');
```


</description>
</generics-section>


<!-- Section -->
<generics-section id="xxx">
<header>一揽子实现 &mdash; <code>impl&lt;T&gt X for T { ... }</code></header>
<description>

{{ tablesep() }}

也可以针对多种类型编写针对某“一类的实现”:

```
// 为任意已经实现过 ToHex 的类型实现 Serialize
impl<T> Serialize for T where T: ToHex { ... }
```

这称为**一揽子实现**.

<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>ToHex</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Port</code></td></tr>
        <tr><td><code>Device</code></td></tr>
        <tr><td><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>

<div style="display: inline-block; width: 100px;">

→  左边的类型总能根据该 `impl` 实现到右边 →

</div>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Serialize Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>Port</code></td></tr>
        <tr><td><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>

</mini-table>

这样可以用一种模块化的方法为已经实现了其他接口的给定外部类型提供一种优雅的实现.

</description>
</generics-section>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-types-3" name="tab-group-types">
<label for="tab-types-3"><b>进阶概念</b>{{ esoteric() }}</label>
<panel><div>


<!-- Section -->
<!-- <generics-section id="xxx">
<header>Pseudo-Specialization</header>
<description>

</description>
</generics-section> -->




<!-- Section -->
<generics-section id="xxx">
<header>Trait 参数 &mdash; <code>Trait&lt;In&gt; { type Out; } </code></header>
<description>

{{ tablesep() }}

注意某些 Trait 会被“附加”多次, 而有些又只有一次?

<mini-zoo class="zoo">
    <entry style="left:300px; top: 25px;">
        <type class="composed"><code>Port</code></type>
        <trait-impl class="">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <trait-impl class="">⌾ <code>From&lt;u16&gt;</code></trait-impl>
    </entry>
    <entry style="left:400px; top: 25px;">
        <type class="composed"><code>Port</code></type>
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>type u8;</code></associated-type>
    </entry>
</mini-zoo>

<!--
<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>A&lt;T&gt;</code></trait-impl>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <trait-impl class="">⌾ <code>A&lt;u8&gt;</code></trait-impl>
    </entry>
    <entry>
        <trait-impl class="">⌾ <code>A&lt;f32&gt;</code></trait-impl>
    </entry>
    <entry>
        <trait-impl class="">⌾ <code>A&lt;str&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<br>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>type T;</code></associated-type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>T = u8;</code></associated-type>
    </entry>
</mini-zoo> -->

<br>

{{ tablesep() }}

为什么?

- Trait 本身通过两类 **参数类型** 实现泛型:
    - `trait From<I> {}`
    - `trait Deref { type O; }`
- 还记得我们说过 Trait 是类型的“成员列表”并且通过 `Self` 调用的吗?
- 转到现在, 就可以认为参数 `I` (即**输入**) 和 `O` (即**输出**) 不过是该 Trait 列表的另外一 _列_ 罢了:

```
impl From<u8> for u16 {}
impl From<u16> for u32 {}
impl Deref for Port { type O = u8; }
impl Deref for String { type O = str; }
```


<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">From</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>I</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u16</code></td><td><code>u8</code></td></tr>
        <tr><td><code>u32</code></td><td><code>u16</code></td></tr>
        <tr><td colspan="2"><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>


<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">Deref</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>O</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Port</code></td><td><code>u8</code></td></tr>
        <tr><td><code>String</code></td><td><code>str</code></td></tr>
        <tr><td colspan="2"><code>...</code></td></tr>
    </tbody>
</table>

</mini-table>

<subtitle>输入和输出参数</subtitle>

</mini-table>


这里会有点绕,
- **任意输出 `O` 参数必须由输入参数 `I` 唯一确定**,
- (同样地, 关系 `X Y` 会表现为一个函数),
- `Self` 作为输入.

一个更复杂的样例:

```
trait Complex<I1, I2> {
    type O1;
    type O2;
}
```

- 此处创建了一个具有关联类型的 `Complex`,
- 它有 3 个输入 (`Self` 也是输入) 和 2 两个输出, 可以表示为 `(Self, I1, I2) => (O1, O2)`

<mini-table>

<table>
    <thead>
        <tr style=""><th colspan="5">Complex</th></tr>
        <tr class="subheader"><th><code>Self [I]</code></th><th><code>I1</code></th><th><code>I2</code></th><th><code>O1</code></th><th><code>O2</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Player</code></td><td><code>u8</code></td><td><code>char</code></td><td><code>f32</code></td><td><code>f32</code></td></tr>
        <tr><td><code>EvilMonster</code></td><td><code>u16</code></td><td><code>str</code></td><td><code>u8</code></td><td><code>u8</code></td></tr>
        <tr><td><code>EvilMonster</code></td><td><code>u16</code></td><td><code>String</code></td><td><code>u8</code></td><td><code>u8</code></td></tr>
        <tr><td><code>NiceMonster</code></td><td><code>u16</code></td><td><code>String</code></td><td><code>u8</code></td><td><code>u8</code></td></tr>
        <tr><td><code>NiceMonster</code><sup>{{ bad() }}</sup></td><td><code>u16</code></td><td><code>String</code></td><td><code>u8</code></td><td><code>u16</code></td></tr>
    </tbody>
</table>

<subtitle>各种 Trait 实现. 最后一个对 `(NiceMonster, u16, String)` 无效, <br> 因为已经由输出唯一确定了.</subtitle>

</mini-table>

</description>
</generics-section>



<!-- Section -->
<generics-section id="xxx">
<header>Trait 设计准则 (抽象)</header>
<description>

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="dotted">⌾ <code>A&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>👩‍🦰</person> / <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
        <trait-impl class="dotted">⌾ <code>A&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>car.a(0_u8)</code>
        <code>car.a(0_f32)</code>
    </entry>
</mini-zoo>

<br>

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>👩‍🦰</person> / <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>T = u8;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>car.b(0_u8)</code>
        <code style="text-decoration: line-through;">car.b(0_f32)</code>
    </entry>
</mini-zoo>

- 参数的选择 (输入还是输出) 仍然决定了谁会被允许加入成员:
    - `I` 参数允许“一类实现”转发给用户 (Santa),
    - `O` 参数必须由 Trait 实现者确定 (Alice 或 Bob).

```
trait A<I> { }
trait B { type O; }

// 实现者将 (X, u32) 添加到 A.
impl A<u32> for X { }

// 实现者将一类 impl (X, ...) 添加到 A, 用户则可以特化之.
impl<T> A<T> for Y { }

// 实现者必须决定将指定入口 (X, O) 添加到 B.
impl B for X { type O = u32; }
```



<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">A</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>I</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>X</code></td><td><code>u32</code></td></tr>
        <tr><td><code>Y</code></td><td><code>...</code></td></tr>
    </tbody>
</table>

<subtitle>Santa 通过提供他自己类型为 <code>T</code> 添加更多成员.</subtitle>

</mini-table>


<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">B</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>O</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Player</code></td><td><code>String</code></td></tr>
        <tr><td><code>X</code></td><td><code>u32</code></td></tr>
    </tbody>
</table>

<subtitle>给定输入集合 (此处为 <code>Self</code>), 实现者必须预先选择 <code>O</code>.</subtitle>

</mini-table>

</mini-table>


</description>
</generics-section>


<!-- Section -->
<generics-section id="trait-authoring-examples">
<header>Trait 设计准则 (举例)</header>
<description>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>



{{ tablesep() }}

参数选择取决于 Trait 的作用.

<hr>


**无额外参数**

```
trait Query {
    fn search(&self, needle: &str);
}

impl Query for PostgreSQL { ... }
impl Query for Sled { ... }

postgres.search("SELECT ...");
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

{{ tablesep() }}

Trait 作者假设:
- 实现者和用户都不允许自定义 API.

{{ tablesep() }}

<hr>

**输入参数**

```
trait Query<I> {
    fn search(&self, needle: I);
}

impl Query<&str> for PostgreSQL { ... }
impl Query<String> for PostgreSQL { ... }
impl<T> Query<T> for Sled where T: ToU8Slice { ... }

postgres.search("SELECT ...");
postgres.search(input.to_string());
sled.search(file);
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query&lt;&str&gt;</code></trait-impl>
        <trait-impl class="">⌾ <code>Query&lt;String&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="dotted">⌾ <code>Query&lt;T&gt;</code></trait-impl>
        <note><span style="margin-left: 10px; display: inline-block; transform: rotate(90deg); font-size: 100%">↲</span> where <code>T</code> is <code>ToU8Slice</code>.</note>
    </entry>
</mini-zoo>


{{ tablesep() }}

Trait 作者假设:
- 实现者可以为相同的 `Self` 类型提供多个自定义 API 实现,
- 用户来决定哪种 `I` 类型行为可用.

{{ tablesep() }}


<hr>


**输出参数**

```
trait Query {
    type O;
    fn search(&self, needle: Self::O);
}

impl Query for PostgreSQL { type O = String; ...}
impl Query for Sled { type O = Vec<u8>; ... }

postgres.search("SELECT ...".to_string());
sled.search(vec![0, 1, 2, 4]);
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>O = String;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>O = Vec&lt;u8&gt;;</code></associated-type>
    </entry>
</mini-zoo>


{{ tablesep() }}

Trait 作者假设:
- 实现者可以为 `Self` 类型自定义 API (但只有一种办法),
- 用户不需要也不应该能够影响指定 `Self` 的自定义.

> 如你所见, 对于函数而言 **输入** 或 **输出** 项都 **不一定** (除非有必要) 是 `I` 或 `O`!

{{ tablesep() }}

<hr>

**多个输入输出参数**

```
trait Query<I> {
    type O;
    fn search(&self, needle: I) -> Self::O;
}

impl Query<&str> for PostgreSQL { type O = String; ... }
impl Query<CString> for PostgreSQL { type O = CString; ... }
impl<T> Query<T> for Sled where T: ToU8Slice { type O = Vec<u8>; ... }

postgres.search("SELECT ...").to_uppercase();
sled.search(&[1, 2, 3, 4]).pop();
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query&lt;&str&gt;</code></trait-impl>
        <associated-type class=""><code>O = String;</code></associated-type>
        <trait-impl class="">⌾ <code>Query&lt;CString&gt;</code></trait-impl>
        <associated-type class=""><code>O = CString;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="dotted">⌾ <code>Query&lt;T&gt;</code></trait-impl>
        <associated-type class=""><code>O = Vec&lt;u8&gt;;</code></associated-type>
        <note><span style="margin-left: 10px; display: inline-block; transform: rotate(90deg); font-size: 100%">↲</span> where <code>T</code> is <code>ToU8Slice</code>.</note>
    </entry>
</mini-zoo>


{{ tablesep() }}

如上例, 通常 Trait 作者假设:
- 用户来决定哪种 `I` 类型行为可用,
- 对于给定的输入, 实现者需要自己确定输出类型.


</description>
</generics-section>



<!-- Section -->
<generics-section id="xxx">
<header>动态大小 / 零大小类型</header>
<description>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="composed"><code>MostTypes</code></type>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <note>普通类型</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry style="width: 60px;">
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="zero"><code>Z</code></type>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <note>零大小</note>
    </entry>
</mini-zoo>


<mini-zoo class="zoo">
    <narrow-entry style="width: 60px;">
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>str</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
        <note>动态大小</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>[u8]</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>dyn Trait</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>...</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
    </entry>
</mini-zoo>


- 如果编译期能够知道用多少个字节表示, 那么类型 `T` 就是 **`Sized`** {{ std(page="std/marker/trait.Sized.html") }} 的, `u8` 和 `&[u8]` 是有大小的, `[u8]` 则不是.
- 有大小 `Sized` 意味着存在 `impl Sized for T {}`. 这个会自动实现且也不能由用户实现.
- 非 `Sized` 的类型称为 **动态大小类型** {{ book(page="ch19-04-advanced-types.html#dynamically-sized-types-and-the-sized-trait") }} {{ nom(page="exotic-sizes.html#dynamically-sized-types-dsts") }}  {{ ref(page="dynamically-sized-types.html#dynamically-sized-types") }} (DST), 有时是 **无大小的**.
- 无数据的类型称为 **零大小类型** {{ nom(page="exotic-sizes.html#zero-sized-types-zsts") }} (ZST), 不分配空间.

<div class="color-header sized cheats">

| 示例 | 说明 |
|---------|-------------|
| `struct A { x: u8 }` | 类型 `A` 有大小, 即存在 `impl Sized for A`, 是最“规则”的类型. |
| `struct B { x: [u8] }` | 因为 `[u8]` 是 DST, `B` 就会变成 DST, 即不存在 `impl Sized`. |
| `struct C<T> { x: T }` | 类型参数 **具有** 隐式的 `T: Sized` 约束, 如 `C<A>` 有效, `C<B>` 无效. |
| `struct D<T: ?Sized> { x: T }` | 使用 **`?Sized`** {{ ref(page="trait-bounds.html#sized") }} 会取消大小约束, 即 `D<B>` 也是有效的. |
| `struct E;` | 类型 `E` 是零大小的 (也是有确定大小的 `Sized`) 且不会耗费内存. |
| `trait F { fn f(&self); }` | Trait **没有** 隐式声明 `Sized` 约束, 即 `impl F for B {}` 有效.  |
| {{ tab() }} `trait F: Sized {}` | Trait 具有 `Sized` 父 Trait.{{ above(target="#functions-behavior") }} |
| `trait G { fn g(self); }` | 对 `Self` 类似参数 DST `impl` 仍无效, 因为参数不能进栈.  |

</div>


</description>
</generics-section>


<!-- Section -->
<generics-section id="xxx">
<header><code>?Sized</code></header>
<description>


<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;T&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <type class="composed"><code>S&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;char&gt;</code></type>
    </entry>
    <entry>
        <type class="composed grayed"><code>S&lt;str&gt;</code></type>
    </entry>
</mini-zoo>

```
struct S<T> { ... }
```

- `T` 可为任意确定类型.
- 然而这里存在隐式约束 `T: Sized`, 故 `S<str>` 不可用.
- 可以改为 `T : ?Sized` 以取消该默认约束:

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;T&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <type class="composed"><code>S&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;char&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;str&gt;</code></type>
    </entry>
</mini-zoo>

```
struct S<T> where T: ?Sized { ... }
```



</description>
</generics-section>


<!-- Section -->
<generics-section id="xxx">
<header>泛型和生命周期 &mdash; <code>&lt;'a&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;'a&gt;</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&'a f32</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&'a mut u8</code></type>
    </entry>
</mini-zoo>

- 生命周期与类型参数使用方法<sup>*</sup>类似:
    - 用户必须为特定类型指定 `'a` (编译器会在方法中提供帮助),
    - 由于 `Vec<f32>` 和 `Vec<u8>` 是不同的类型, 故记为 `S<'p>` 和 `S<'q>`,
    - 这意味着你不能仅分配类型 `S<'a>` 的值而不管 `S<'b>` (异常: 生命周期的“子类型”关系, 如 `'a` 长于 `'b`).


<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;'a&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <type class="composed"><code>S&lt;'auto&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;'static&gt;</code></type>
    </entry>
</mini-zoo>


- `'static` 是仅有的 _类型空间_ 中的具名生命周期.

```
// `'a 是这里的自由参数 (用户可以在任意生命周期上使用)
struct S<'a> {
    x: &'a u32
}

// 非泛型代码中, 'static 是这里仅有的能使用的具名声明周期.
let a: S<'static>;

// 非泛型代码中我们无需指定 'a 并使得 Rust 通过右值自动推断出 'a.
let b: S;
```

<footnotes>

<sup>*</sup> 这里有些微妙的不同, 比如显式地创建一个类型为 `u32` 的实例 `0`, 但由于 `'static` 的例外你并不能创建一个生命周期, 比如 "lines 80 - 100", 编译器会自动帮你完成这些工作. {{ link(url="https://medium.com/nearprotocol/understanding-rust-lifetimes-e813bcd405fa" )}}

</footnotes>


> Note to self and TODO: that analogy seems somewhat flawed, as if `S<'a>` is to `S<'static>` like `S<T>` is to `S<u32>`, then `'static` would be a _type_; but then what's the value of that type?

</description>
</generics-section>


<!-- Section -->
<!-- <generics-section id="xxx">
<header>Another <code>?X</code></header>
<description>

- `Sized` is trait, automatically implemented **and** automatically used as default bound
- Could there (ever) be another trait `T` so that:
    - `S<T>` means `S<T> where T: Sized + X` by default and
    - you'd have to opt out with `S<T> where T: ?X` ?
- Issue:
    - Any `S<T>` written today does not know `X`, so can't opt into supporting it
    - If `X` were introduced and not implemented for any existing type, `S<T>` would stop working on that type

</description>
</generics-section> -->


<!-- Section -->
<!-- <generics-section id="xxx">
<header>GAT {{ experimental() }}</header>
<description>


</description>
</generics-section> -->



<!-- Section -->
<!-- <generics-section id="xxx">
<header>(Co-/Contra-) Variance </header>
<description>


</description>
</generics-section>
 -->

<!-- Section -->
<!-- <generics-section id="zoo_todo">
<header>Todo</header>
<description>


</description>
</generics-section>
 -->


</div></panel></tab>

</tabs>

<footnotes>

点击展开样例.

</footnotes>




## 类型乐园 {#type-zoo}

A visual overview of types and traits in crates.

<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 750px;">


<zoo class="zoo">

<!-- REGION -->
<region style="height: 310px;">
<!-- Primitives -->
<group style="left:6%; width: 200px;">
    <entry style="left:100px; top: 10%;">
        <type class="primitive"><code>u8</code></type>
    </entry>
    <entry style="left:20px; top: 32%;">
        <type class="primitive"><code>u16</code></type>
    </entry>
    <entry style="left:30px; top: 20%;">
        <type class="primitive"><code>f32</code></type>
    </entry>
    <entry style="left:0px; top: 7%;">
        <type class="primitive"><code>bool</code></type>
    </entry>
    <entry style="left:120px; top: 32%;">
        <type class="primitive"><code>char</code></type>
    </entry>
    <label style="left:8px; top: 43%;">Primitive Types</label>
</group>
<!-- Composed -->
<group style="left:50%; width: 350px;">
    <entry style="left:110px; top: 60px;">
        <type class="composed"><code>File</code></type>
    </entry>
    <entry style="left:180px; top: 34%;">
        <type class="composed"><code>String</code></type>
    </entry>
    <entry style="left:230px; top: 13%;">
        <type class="composed"><code>Builder</code></type>
    </entry>
    <label style="left:150px; top: 43%;">Composite Types</label>
</group>
<!-- Type constructors -->
<group style="left: 30px; top:53%; width: 200px;">
    <!-- Group -->
    <entry style="left:50px; top: 8%;">
        <type class="composed"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <entry style="left:45px; top: 9%;">
        <type class="composed"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <entry style="left:40px; top: 10%;">
        <type class="generic dotted"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <!-- Group -->
    <entry style="left:170px; top: 2%;">
        <type class="primitive"><code>&'a T</code></type>
    </entry>
    <entry style="left:165px; top: 3%;">
        <type class="primitive"><code>&'a T</code></type>
    </entry>
    <entry style="left:160px; top: 4%;">
        <type class="generic dotted"><code>&'a T</code></type>
    </entry>
    <!-- Group -->
    <entry style="left:140px; top: 18%;">
        <type class="primitive"><code>&mut 'a T</code></type>
    </entry>
    <entry style="left:135px; top: 19%;">
        <type class="primitive"><code>&mut 'a T</code></type>
    </entry>
    <entry style="left:130px; top: 20%;">
        <type class="generic dotted"><code>&mut 'a T</code></type>
    </entry>
    <!-- Group -->
    <entry style="left:40px; top: 28%;">
        <type class="primitive"><code>[T; n]</code></type>
    </entry>
    <entry style="left:35px; top: 29%;">
        <type class="primitive"><code>[T; n]</code></type>
    </entry>
    <entry style="left:30px; top: 30%;">
        <type class="generic dotted"><code>[T; n]</code></type>
    </entry>
    <label style="left:80px; top: 40%;">Type Constructors</label>
</group>
<!-- Functrions -->
<group style="left: 50%; top:53%; width: 200px;">
    <!-- Group -->
    <entry style="left:10px; top: 8%;">
        <function class=""><code>Vec&lt;T&gt;</code></function>
    </entry>
    <entry style="left:5px; top: 9%;">
        <function class=""><code>Vec&lt;T&gt;</code></function>
    </entry>
    <entry style="left:0px; top: 10%;">
        <function class="dotted"><code>f&lt;T&gt;() {}</code></function>
    </entry>
    <!-- Group -->
    <entry style="left:20px; top: 24%;">
        <function><code>drop() {}</code></function>
    </entry>
    <label style="left:10px; top: 40%;">Functions</label>
</group>
<!-- Unsized -->
<!-- <group style="left: 50%; top:53%;">
    <entry style="left:30%; top: 10%;">
        <type class="unsized"><code>str</code></type>
    </entry>
    <entry style="left:35%; top: 20%;">
        <type class="unsized"><code>[u8]</code></type>
    </entry>
    <entry style="left:28%; top: 30%;">
        <type class="unsized"><code>dyn Trait</code></type>
    </entry>
    <label style="left:30%; top: 40%;">Unsized Types</label>
</group> -->
<!-- Macros -->
<group class="grayed" style="left: 80%; top:53%; width: 140px;">
    <entry style="left:5px; top: 15%;">
        <macro><code>PI</code></macro>
    </entry>
    <entry style="left:0px; top: 28%;">
        <macro><code>dbg!</code></macro>
    </entry>
    <label style="left:20px; top: 40%;">Other</label>
</group>
<!-- Traits -->
<group style="left:36%; width: 30px;">
    <entry style="left:20px; top: 20px;">
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
    <entry style="left:60px; top: 90px;">
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class=""><code>type Tgt;</code></associated-type>
    </entry>
    <entry style="left:90px; top: 50px;">
        <trait-impl class="">⌾ <code>From&lt;T&gt;</code></trait-impl>
    </entry>
    <entry style="left:85px; top: 55px;">
        <trait-impl class="">⌾ <code>From&lt;T&gt;</code></trait-impl>
    </entry>
    <entry style="left:80px; top: 60px;">
        <trait-impl class="dotted">⌾ <code>From&lt;T&gt;</code></trait-impl>
    </entry>
    <label style="left:60px; top: 43%;">Traits</label>
</group>
</region>
<region-label>Items defined in upstream crates.</region-label>

<!-- REGION -->
<region class="your-crate" style="height: 190px;">
<!-- traits -->
<group style="left:5px; width: 200px;">
    <entry style="left:10px; top: 25px;">
        <trait-impl class="">⌾ <code>Serialize</code></trait-impl>
    </entry>
    <entry style="left:30px; top: 65px;">
        <trait-impl class="">⌾ <code>Transport</code></trait-impl>
    </entry>
    <entry style="left:15px; top: 105px;">
        <trait-impl class="">⌾ <code>ShowHex</code></trait-impl>
    </entry>
    <!-- <label style="left:60px; top: 165px">Traits</label> -->
</group>
<!-- types -->
<group style="left:150px; width: 200px;">
    <entry style="left:0px; top: 25px;">
        <type class="composed"><code>Device</code></type>
        <trait-impl class="grayed">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <!-- <trait-impl class="grayed">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>type Thing;</code></associated-type> -->
        <note>Foreign trait impl. for local type.</note>
    </entry>
    <entry style="left:100px; top: 25px;">
        <type class="grayed composed"><code>String</code></type>
        <trait-impl class="">⌾ <code>Serialize</code></trait-impl>
        <note>Local trait impl. for foreign type.</note>
    </entry>
    <entry style="left:200px; top: 25px;">
        <type class="composed grayed"><code>String</code></type>
        <trait-impl class="grayed">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <note>{{ bad() }} Illegal, foreign trait for f. type.</note>
    </entry>
    <entry style="left:200px; top: 110px;">
        <type class="composed grayed"><code>String</code></type>
        <trait-impl class="grayed">⌾ <code>From&lt;Port&gt;</code></trait-impl>
        <note>Exception: Legal if used type local.</note>
    </entry>
    <entry style="left:300px; top: 25px;">
        <type class="composed"><code>Port</code></type>
        <trait-impl class="">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <trait-impl class="">⌾ <code>From&lt;u16&gt;</code></trait-impl>
        <note>Mult. impl. of trait with differing <b>IN</b> params.</note>
    </entry>
    <entry style="left:400px; top: 25px;">
        <type class="composed"><code>Container</code></type>
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>Tgt = u8;</code></associated-type>
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>Tgt = f32;</code></associated-type>
        <note>{{ bad() }} Illegal impl. of trait with differing <b>OUT</b> params.</note>
    </entry>
    <entry style="left:510px; top: 15px;">
        <type class="composed"><code>T</code></type>
    </entry>
    <entry style="left:505px; top: 20px;">
        <type class="composed"><code>T</code></type>
    </entry>
    <entry style="left:500px; top: 25px;">
        <type class="generic dotted"><code>T</code></type>
        <trait-impl class="">⌾ <code>ShowHex</code></trait-impl>
        <note>Blanket impl. of trait for any type.</note>
    </entry>
</group>
</region>
<region-label>Your crate.</region-label>

<!-- REGION -->
<!-- <region style="height: 90px;">
<group style="left:324px; width: 200px;">
    <entry style="left:20px; top: 30px;">
        <code>ccc.f();</code>
    </entry>
</group>
</region>
<region-label>Downstream crates.</region-label> -->

</zoo>

<footnotes>

A walk through the jungle of types, traits, and implementations that (might possibly) exist in your application.

</footnotes>



<!-- End scrollable overflow-->
</div>
</div>




## Type Conversions

How to get `B` when you have `A`?

<div class="color-header variance">

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-1" name="tab-variance" checked>
<label for="tab-variance-1"><b>Intro</b></label>
<panel><div>

```
fn f(x: A) -> B {
    // How can you obtain B from A?
}
```

| Method | Explanation |
|--------| -----------|
| **Identity** | Trivial case, `B` **is exactly** `A`. |
| **Computation** | Create and manipulate instance of `B` by **writing code** transforming data. |
| **Casts** | **On-demand** conversion between types where caution is advised. |
| **Coercions** | **Automatic** conversion within _'weakening ruleset'_.<sup>1</sup> |
| **Subtyping** | **Automatic** conversion within _'same-layout-different-lifetimes ruleset'_.<sup>1</sup> |

{{ tablesep() }}

<footnotes>

<sup>1</sup> While both convert `A` to `B`, **coercions** generally link to an _unrelated_ `B` (a type "one could reasonably expect to have different methods"),
while **subtyping** links to a `B` differing only in lifetimes.

</footnotes>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-2" name="tab-variance">
<label for="tab-variance-2"><b>Computation (Traits)</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x.into()
}
```

_Bread and butter_ way to get `B` from `A`. Some traits provide canonical, user-computable type relations:

| Trait | Example | Trait implies ... |
|--------| -----------|-----------|
| `impl From<A> for B {}` | `a.into()` | _Obvious_, always-valid relation. |
| `impl TryFrom<A> for B {}` | `a.try_into()?` | _Obvious_, sometimes-valid relation. |
| `impl Deref for A {}` | `*a` | `A` is smart pointer carrying `B`; also enables coercions.  |
| `impl AsRef<B> for A {}` | `a.as_ref()` | `A` can be _viewed_ as `B`. |
| `impl AsMut<B> for A {}` | `a.as_mut()` | `A` can be mutably viewed as `B`. |
| `impl Borrow<B> for A {}` | `a.borrow()` | `A` has borrowed _analog_ `B` (behaving same under `Eq`, ...). |
| `impl ToOwned for A { ... }` | `a.to_owned()` | `A` has owned analog `B`. |


<!--
<footnotes>

<sup>1</sup> Pretty much any function, like `is_signed(x)`, puts values of two types in a _specific_ relationship, especially if their _meaning_ is highly _overloaded_ (e.g., `true` in the `is_signed` relation is proxy for a different concept than `true` in an `is_odd` one). In contrast, the traits above (and type conversions in general) are mainly about unambiguous conversions across any possible meaning.

</footnotes>
 -->

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-3" name="tab-variance">
<label for="tab-variance-3"><b>Casts</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x as B
}
```

Convert types **with keyword `as`** if conversion _relatively obvious_ but **might cause issues**. {{ nom(page="casts.html") }}


|  A | B | 示例 | 说明 |
|----|----| ----| -----------|
| `Ptr` | `Ptr` | `device_ptr as *const u8` | If `*A`, `*B` are `Sized`. |
| `Ptr` | `Integer` | `device_ptr as usize` |  |
| `Integer` | `Ptr` | `my_usize as *const Device` |  |
| `Number` | `Number` | `my_u8 as u16` | Often surprising behavior. {{ above(target="#numeric-types-ref") }} |
| `enum` w/o fields | `Integer` | `E::A as u8` |  |
| `bool` | `Integer` | `true as u8` |  |
| `char` | `Integer` | `'A' as u8` |  |
| `&[T; N]` | `*const T` | `my_ref as *const u8` |  |
| `fn(...)` | `Ptr` | `f as *const u8` | If `Ptr` is `Sized`.  |
| `fn(...)` | `Integer` | `f as usize` |  |

{{ tablesep() }}

<footnote>

Where `Ptr`, `Integer`, `Number` are just used for brevity and actually mean:
- `Ptr` any `*const T` or `*mut T`;
- `Integer` any countable `u8` ... `i128`;
- `Number` any `Integer`, `f32`, `f64`.

</footnote>

> **Opinion** {{ opinionated() }} &mdash; Casts, esp. `Number` - `Number`, can easily go wrong.
> If you are concerned with correctness, consider more explicit methods instead.

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-4" name="tab-variance">
<label for="tab-variance-4"><b>Coercions</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x
}
```

Automatically **weaken** type `A` to `B`; types can be _substantially_<sup>1</sup> different. {{ nom(page="coercions.html") }}


|  A | B |  Explanation |
|----|----| -----------|
| `&mut T` | `&T` | **Pointer weakening**. |
| `&mut T` | `*mut T` | - |
| `&T` | `*const T` | - |
| `*mut T` | `*const T` | - |
| `&T` | `&U` | **Deref**, if `impl Deref<Target=U> for T`. |
| `T` | `U` | **Unsizing**, if `impl CoerceUnsized<U> for T`.<sup>2</sup> {{ experimental() }} |
| `T` | `V` | **Transitivity**, if `T` coerces to `U` and `U` to `V`. |
| <code>&vert;x&vert; x + x</code> | `fn(u8) -> u8` | **Non-capturing closure**, to equivalent `fn` pointer. |

{{ tablesep() }}

<footnote>

<sup>1</sup> _Substantially_ meaning one can regularly expect a coercion result `B` to be _an entirely different type_ (i.e., have entirely different methods) than the original type `A`.

<sup>2</sup> Does not quite work in example above as unsized can't be on stack; imagine `f(x: &A) -> &B` instead. Unsizing works by default for:
- `[T; n]` to `[T]`
- `T` to `dyn Trait` if `impl Trait for T {}`.
- `Foo<..., T, ...>` to `Foo<..., U, ...>` under arcane {{ link(url="https://doc.rust-lang.org/nomicon/coercions.html") }} circumstances.

</footnote>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-5" name="tab-variance">
<label for="tab-variance-5"><b>Subtyping</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x
}
```

Automatically converts `A` to `B` for types **only differing in lifetimes** {{ nom(page="subtyping.html") }} - subtyping **examples**:


| A<sup>(subtype)</sup>  | B<sup>(supertype)</sup> | Explanation |
|--------| -----------| -----------|
| `&'static u8` | `&'a u8` | Valid, <i>forever-</i>pointer is also <i>transient-</i>pointer. |
| `&'a u8` | `&'static u8` | {{ bad() }} Invalid, transient should not be forever. |
| `&'a &'b u8` | `&'a &'b u8` | Valid, same thing. **But now things get interesting. Read on.** |
| `&'a &'static u8` | `&'a &'b u8` | Valid, `&'static u8` is also `&'b u8`; **covariant** inside `&`.  |
| `&'a mut &'static u8` | `&'a mut &'b u8` | {{ bad() }} Invalid and surprising; **invariant** inside `&mut`. |
| `Box<&'a static>` | `Box<&'a u8>` | Valid, box with forever is also box with transient; covariant. |
| `Box<&'a u8>` | `Box<&'static u8>` | {{ bad() }} Invalid, box with transient may not be with forever. |
| `Box<&'a mut u8>` | `Box<&'a u8>` | {{ bad() }} <sup>⚡</sup> Invalid, see table below, `&mut u8` never _was a_ `&u8`. |
| `Cell<&'a static>` | `Cell<&'a u8>` | {{ bad() }} Invalid, cells are **never** something else; invariant. |
| `fn(&'static u8)` | `fn(&'u8 u8)` | {{ bad() }} If `fn` needs forever it may choke on transients; **contravar.**|
| `fn(&'a u8)` | `fn(&'static u8)` |  But sth. that eats transients **can be**(!) sth. that eats forevers. |
| `for<'r> fn(&'r u8)` | `fn(&'a u8)` | Higher-ranked type `for<'r> fn(&'r u8)` is also `fn(&'a u8).` |


{{ tablesep() }}

In contrast, these are **not**{{ bad() }} examples of subtyping:

|  A | B |  Explanation |
|----|----| -----------|
| `u16` | `u8` | {{ bad() }} **Obviously invalid**; `u16` should never automatically be `u8`. |
| `u8` | `u16` | {{ bad() }} Invalid **by design**; types w. different data still never subtype even if they _could_. |
| `&'a mut u8` | `&'a u8` | {{ bad() }} Trojan horse, not subtyping; but coercion (still works, just not subtyping). |

{{ tablesep() }}

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-8" name="tab-variance">
<label for="tab-variance-8"><b>Variance</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x
}
```

Automatically converts `A` to `B` for types **only differing in lifetimes** {{ nom(page="subtyping.html") }} -  subtyping **variance rules**:

- A longer lifetime `'a` that outlives a shorter `'b` is a subtype of `'b`.
- Implies `'static` is subtype of all other lifetimes `'a`.
- Whether types with parameters (e.g., `&'a T`) are subtypes of each other the following variance table is used:

| Construct<sup>1</sup> | `'a` | `T` | `U` |
|--------| -----------| -------| -------|
| `&'a T` | covariant | covariant |  |
| `&'a mut T` | covariant | invariant |  |
| `Box<T>` |  | covariant |  |
| `Cell<T>` |  | invariant |  |
| `fn(T) -> U` |  | **contra**variant | covariant |
| `*const T` |  | covariant |  |
| `*mut T` |  | invariant |  |

<footnotes>

**Covariant** means if `A` is subtype of `B`, then `T[A]` is subtype of `T[B]`. <br>
**Contravariant** means if `A` is subtype of `B`, then **`T[B]`** is subtype of `T[A]`. <br>
**Invariant** means even if `A` is subtype of `B`, neither `T[A]` nor `T[B]` will be subtype of the other.<br>
<!-- <br> -->

<sup>1</sup> Compounds like `struct S<T> {}` obtain variance through their used fields, usually becoming invariant if multiple variances are mixed.<br>

</footnotes>

> 💡 **In other words**, 'regular' types are never subtypes of each other (e.g., `u8` is not subtype of `u16`),
> and a `Box<u32>` would never be sub- or supertype of anything.
> However, generally a `Box<A>`, _can_ be subtype of `Box<B>` (via covariance) if `A` is a subtype
> of `B`, which can only happen if `A` and `B` are 'sort of the same type that only differed in lifetimes', e.g., `A` being `&'static u32` and `B` being `&'a u32`.

</div></panel></tab>

</tabs>

</div>


{{ tablesep() }}




---

# 编码指南


## Rust 惯用法 {#idiomatic-rust}

Java 或 C 的使用者需要转换下思维: 

<div class="color-header blue">

| 习语 | 代码 |
|--------| ---- |
| **用表达式思考** | `x = if x { a } else { b };` |
|  | `x = loop { break 5 };`  |
|  | `fn f() -> u32 { 0 }`  |
| **用迭代器思考** | `(1..10).map(f).collect()` |
|  | <code>names.iter().filter(&vert;x&vert; x.starts_with("A"))</code> |
| **用 `?` 捕获异常** | `x = try_something()?;` |
|  | `get_option()?.run()?` |
| **使用强类型** | `enum E { Invalid, Valid { ... } }` 之于 `ERROR_INVALID = -1` |
|  | `enum E { Visible, Hidden }` 之于 `visible: bool` |
|  | `struct Charge(f32)` 之于 `f32` |
| **提供生成器** | `Car::new("Model T").hp(20).run();` |
| **分离实现** | 泛型 `S<T>` 可以对每个 `T` 都有不同的实现. |
|   | Rust 没有面向对象, 但通过 `impl` 可以实现特化. |
| **Unsafe** | 尽量避免 `unsafe {}`, 因为总是会有更快更安全的解决方案的.除了 FFI. |
| **实现 Trait** | `#[derive(Debug, Copy, ...)]`.根据需要实现 `impl`.|
| **工具链** | 利用 [**clippy**](https://github.com/rust-lang/rust-clippy) 可以提升代码质量. |
|  | 用 [**rustfmt**](https://github.com/rust-lang/rustfmt) 格式化可以帮助别人看懂你的代码. |
|  | 添加**单元测试** {{ book(page="ch11-01-writing-tests.html") }}(`#[test]`), 确保代码正常运行. |
|  | 添加**文档测试** {{ book(page="ch14-02-publishing-to-crates-io.html") }}(` ``` my_api::f() ``` `), 确保文档匹配代码. |
| **文档** | 以文档注解的 API 可显示在 [**docs.rs**](https://docs.rs) 上. |
|  | 不要忘记在开始加上**总结句**和**例程**. |
|  | 如果有这些也加上: **Panics**, **Errors**, **Safety**, **Abort** 和**未定义行为**. |

</div>



{{ tablesep() }}

> 🔥 **强烈**建议对所有共享项目都遵循
> [**API 指南**](https://rust-lang.github.io/api-guidelines/)([**检查列表**](https://rust-lang.github.io/api-guidelines/checklist.html))！ 🔥


{{ tablesep() }}



## Async-Await 101

类似于 C# 或 TypeScript 的 async / await, 但又有所不同: 


<tabs class="color-header orange">

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-async-1" name="tab-async" checked>
<label for="tab-async-1"><b>Basics</b></label>
<panel><div>



| 语法 | 说明 |
|---------|-------------|
| `async`  | Anything declared `async` always returns an `impl Future<Output=_>`. {{ std(page="std/future/trait.Future.html") }} |
| {{ tab() }} `async fn f() {}`  | Function `f` returns an `impl Future<Output=()>`. |
| {{ tab() }} `async fn f() -> S {}`  | Function `f` returns an `impl Future<Output=S>`. |
| {{ tab() }} `async { x }`  | Transforms `{ x }` into an `impl Future<Output=X>`. |
| `let sm = f();   ` | Calling `f()` that is `async` will **not** execute `f`, but produce state machine `sm`. {{ note(note="1") }} {{ note(note="2") }} |
| {{ tab() }} `sm = async { g() };`  | Likewise, does **not** execute the `{ g() }` block; produces state machine. |
| `runtime.block_on(sm);`  | Outside an `async {}`, schedules `sm` to actually run. Would execute `g()`. {{ note(note="3") }} {{ note(note="4") }}|
| `sm.await` | Inside an `async {}`, run `sm` until complete. Yield to runtime if `sm` not ready. |



<footnotes>

<sup>1</sup> Technically `async` transforms following code into anonymous, compiler-generated state machine type; `f()` instantiates that machine. <br>
<sup>2</sup> The state machine always `impl Future`, possibly `Send` & co, depending on types used inside `async`. <br>
<sup>3</sup> State machine driven by worker thread invoking `Future::poll()` via runtime directly, or parent `.await` indirectly. <br>
<sup>4</sup> Rust doesn't come with runtime, need external crate instead, e.g., [async-std](https://github.com/async-rs/async-std) or [tokio 0.2+](https://crates.io/crates/tokio). Also, more helpers in [futures crate](https://github.com/rust-lang-nursery/futures-rs).

</footnotes>



</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-async-2" name="tab-async">
<label for="tab-async-2"><b>Execution Flow</b></label>
<panel><div>


对每个 `x.await`, 状态机将会通过控制转移到状态机 `x`.有时, 由 `.await` 调用的低级状态机并未就绪, 此时, 工作线程直接返回到运行时, 以使得它可以驱动另一个 Future.一段时间后, 运行时: 
- **可能**恢复执行.常见于此, 除非 `sm` / `Future` 已析构.
- **可能**由前一个**或另一个**工作线程恢复执行(取决于运行时).

`async` 代码块内部代码的简易流程图如下: 


<!-- Create a horizontal scrollable area on small displays to preserve layout-->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
       consecutive_code();           consecutive_code();           consecutive_code();
START --------------------> x.await --------------------> y.await --------------------> READY
// ^                          ^     ^                               Future<Output=X> 就绪 -^
// 由运行时调用                 |     |
// 或由外部 .await 调用         |     会由另一个线程恢复(下一个最佳可用的), 
//                            |     或者当 Future 已析构时根本不会执行.
//                            |
//                            执行 `x`.若已就绪, 则继续执行.
//                            若未就绪, 返回当前线程到运行时.
```

</div>
</div>

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-async-3" name="tab-async">
<label for="tab-async-3"><b>Caveats</b></label>
<panel><div>


With the execution flow in mind, some considerations when writing code inside an `async` construct:

<div class="color-header orange">


| 语法 {{ note(note="1") }} | 说明 |
|---------|-------------|
| `sleep_or_block();` | 显然不对{{ bad() }}, 当前线程永不终止, 阻碍执行器. |
| `set_TL(a); x.await; TL();` | 显然不对{{ bad() }}, `await` 会由其他线程返回, [thread local](https://doc.rust-lang.org/std/macro.thread_local.html) 无效. |
| `s.no(); x.await; s.go();` | 可能不对{{ bad() }}, 如果等待时 `Future` 被析构, 则 `await` [不会返回](http://www.randomhacks.net/2019/03/09/in-nightly-rust-await-may-never-return/).{{ note(note="2") }} |
| `Rc::new(); x.await; rc();` | 非 `Send` 类型拒绝实现 `impl Future`.兼容性差. |

</div>

<footnotes>

<sup>1</sup> Here we assume `s` is any non-local that could temporarily be put into an invalid state;
`TL` is any thread local storage, and that the `async {}` containing the code is written
without assuming executor specifics. <br/>
<sup>2</sup> Since [Drop](https://doc.rust-lang.org/std/ops/trait.Drop.html) is run in any case when `Future` is dropped, consider using drop guard that cleans up / fixes application state if it has to be left in bad condition across `.await` points.

</footnotes>

</div></panel></tab>

<!-- end tabs -->
</tabs>


{{ tablesep() }}


## 闭包 API {#closures-in-apis}

There is a subtrait relationship `Fn` : `FnMut` : `FnOnce`. That means a closure that
implements `Fn` {{ std(page="std/ops/trait.Fn.html") }} also implements `FnMut` and `FnOnce`. Likewise a closure
that implements `FnMut` {{ std(page="std/ops/trait.FnMut.html") }} also implements `FnOnce`. {{ std(page="std/ops/trait.FnOnce.html") }}

从调用者的角度来看这意味着: 

<div class="color-header green">

| Signature | Function `g` can call &hellip; |  Function `g` accepts &hellip; |
|--------| -----------| -----------|
| `g<F: FnOnce()>(f: F)`  | &hellip; `f()` once. |  `Fn`, `FnMut`, `FnOnce`  |
| `g<F: FnMut()>(mut f: F)`  | &hellip; `f()` multiple times. | `Fn`, `FnMut` |
| `g<F: Fn()>(f: F)`  | &hellip; `f()` multiple times.  | `Fn` |

</div>

<footnotes>

注意, 对调用者来说, 如何**确定** `Fn` 闭包, 是最为严格的.但是一个**包含** `Fn` 的闭包, 对调用者来説, 是对任意函数都最兼容的.

</footnotes>



{{ tablesep() }}

站在定义闭包的角度来看: 

<div class="color-header green">

| 闭包 | 实现<sup>*</sup> | 说明 |
|--------| -----------| --- |
| <code> &vert;&vert; { moved_s; } </code> | `FnOnce` | 调用者必须放弃 `moved_s` 的所有权. |
| <code> &vert;&vert; { &mut s; } </code> | `FnOnce`, `FnMut` | 允许 `g()` 改变调用者的局部状态 `s`. |
| <code> &vert;&vert; { &s; } </code> | `FnOnce`, `FnMut`, `Fn` | 可能不会导致状态改变, 但可能会共享和重用 `s`. |

</div>

<div class="footnotes">

<sup>*</sup> Rust [偏向于以索引捕获](https://doc.rust-lang.org/stable/reference/expressions/closure-expr.html)(在调用者视角上最「兼容」 `Fn` 的闭包), 但也可以用 `move || {}` 语法通过复制或者移动捕获相关环境变量..

</div>

{{ tablesep() }}

这会带来如下优势和劣势: 

<div class="color-header green">

| 要求 | 优势 | 劣势 |
|--------| -----------| -----------|
| `F: FnOnce`  | <span class="good">容易满足调用者.</span> | <span class="bad">仅用一次, `g()` 仅会调用 `f()` 一次.</span> |
| `F: FnMut`  | <span class="good">允许 `g()` 改变调用者状态.</span> | <span class="bad">调用者不能在 `g()` 期间重用捕获.</span> |
| `F: Fn`  | <span class="good">可同时存在多个.</span> | <span class="bad">最难由调用者生成.</span> |

</div>


{{ tablesep() }}



<!-- ## Macro Hygiene -->
<!-- {{ tablesep() }} -->





## Unsafe, Unsound, Undefined

Unsafe 导致 unsound, unsound 导致 undefined, undefined 是一切原力的阴暗面.



<tabs>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-unsafe-1" name="tab-unsafe" checked>
<label for="tab-unsafe-1"><b>Unsafe Code</b></label>
<panel><div>


**Unsafe 代码**

- 标记为 `unsafe` 的代码有特权.比如, 解引用裸指针, 或调用其他 `unsafe` 函数.
- 这是一份特殊的**作者必须给编译器的承诺**, 编译器**会**相信你.
- `unsafe` 代码自身并非有害, 但危险的是 FFI 使用方或者异常的数据结构.

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```rust
// `x` must always point to race-free, valid, aligned, initialized u8 memory.
unsafe fn unsafe_f(x: *mut u8) {
    my_native_lib(x);
}
```
</div></div></div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-unsafe-2" name="tab-unsafe" >
<label for="tab-unsafe-2"><b>Undefined Behavior</b></label>
<panel><div>


**未定义行为 (UB)**
- 如前所述, `unsafe` 代码意味着对编译器的[特殊承诺](https://doc.rust-lang.org/stable/reference/behavior-considered-undefined.html)(否则它就不需要是 `unsafe` 的了).
- 不遵守承诺会使编译器产生错误的代码, 执行错误的代码会导致未定义行为.
- 在触发未定义行为之后, **任何**事情都可能发生.这种不知不觉的影响可能1)难以捉摸, 2)明显远离事发现场, 或3)只有在某些条件下才会被发现.
- 一个表面上**可以运行**的程序(包括任意数量的单元测试), 并不能证明含有未定义行为的代码不会因为一些偶然原因而失败.
- 含有未定义行为的代码在客观上是危险的, 无效的, 根本不应该存在.

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">


```rust
if should_be_true() {
   let r: &u8 = unsafe { &*ptr::null() };    // 一旦运行, 整个程序都会处于未定义状态.
} else {                                     // 尽管这一行看似什么都没干, 程序可能两条路径
    println!("the spanish inquisition");     // 都运行了, 然后破坏掉数据, 或者发生别的.
}
```
</div></div></div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-unsafe-3" name="tab-unsafe" >
<label for="tab-unsafe-3"><b>Unsound Code</b></label>
<panel><div>


**Unsound 代码**
- 任何会由于用户输入而导致 _safe_ Rust 产生未定义行为的都是 **unsound**(不健全)的(尽管仅仅可能是理论上的).
- 比如 `unsafe` 代码可能违反上述承诺而产生未定义行为.
- Unsound 代码对稳定性和安全性造成风险, 且违背了大部分 Rust 用户的基本假设.

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```rust
fn unsound_ref<T>(x: &T) -> &u128 {      // Signature looks safe to users. Happens to be
    unsafe { mem::transmute(x) }         // ok if invoked with an &u128, UB for practically
}                                        // everything else.
```

</div></div></div></panel></tab>

</tabs>

{{ tablesep() }}

>
> **负责任地使用 unsafe** {{ opinionated() }}
>
> - 除非非用不可, 不要使用 `unsafe`.
> - Follow the [Nomicon](https://doc.rust-lang.org/nightly/nomicon/), [Unsafe Guidelines](https://rust-lang.github.io/unsafe-code-guidelines/), **always** uphold **all** safety invariants, and **never** invoke [UB](https://doc.rust-lang.org/stable/reference/behavior-considered-undefined.html).
> - 最小化 `unsafe` 用例, 封装成易于评审的小的, 优雅的模块.
> - Never create unsound abstractions; if you can't encapsulate `unsafe` properly, don't do it.
> - 每个 `unsafe` 用例应当同时提供关于其安全性的纯文本理由提要.


{{ tablesep() }}



## API 稳定性 {#api-stability}

When updating an API, these changes can break client code.{{ rfc(page="1105-api-evolution.html") }} Major changes (🔴) are **definitely breaking**, while minor changes (🟡) **might be breaking**:

<div class="color-header api-stability">


{{ tablesep() }}

| Crate |
|---------|
| 🔴 编写一个 _stable_ 的 crate 但却依赖了 _nightly_. |
| 🟡 修改了 Cargo 的功能(比如添加或移除功能) |

{{ tablesep() }}


| 模块 |
|---------|
| 🔴 重命名, 移动, 移除任何公开项. |
| 🟡 添加新的公开项, 因为 `use your_crate::*` 可能会破坏现有代码. |

{{ tablesep() }}

| 结构体 |
|---------|
| 🔴 当所有字段都为公开时添加私有字段. |
| 🔴 当没有私有字段时添加公开字段. |
| 🟡 当至少有一个字段时添加或移除私有字段(在更改前或更改后). |
| 🟡 将有私有字段(至少有一个字段)的元组结构转换到普通结构, 或反之. |

{{ tablesep() }}

| 枚举 |
|---------|
| 🔴 Adding new variants; can be mitigated with early `#[non_exhaustive]` {{ ref(page="attributes/type_system.html#the-non_exhaustive-attribute") }} |
| 🔴 Adding new fields to a variant. |


{{ tablesep() }}

| Trait |
|---------|
| 🔴 添加非默认项, 将会破坏已有的 `impl T for S {}`. |
| 🔴 任何不必要的项签名修改, 都会影响到使用者或者实现方. |
| 🟡 添加一个默认项, 可能会和另一个 trait 产生歧义. |
| 🟡 添加默认类型参数. |

{{ tablesep() }}

| Trait |
|---------|
| 🔴 实现任何「基本」trait.**不去**实现一个基本 trait 是一种最基本的承诺. |
| 🟡 实现任何非基本的 trait, 可能会导致歧义. |

{{ tablesep() }}

| 固有实现 |
|---------|
| 🟡 添加内部项, 可能会导致客户端倾向于调用这个 trait 的 fn 而导致编译错误. |

{{ tablesep() }}

| 类型定义签名 |
|---------|
| 🔴 强约束(如 `<T>` 到 `<T: Clone>`). |
| 🟡 弱约束. |
| 🟡 添加默认类型参数. |
| 🟡 泛型归纳. |

| 函数签名 |
|---------|
| 🔴 添加或移除参数. |
| 🟡 引入新的类型参数. |
| 🟡 泛型归纳. |


{{ tablesep() }}

| 行为更改 |
|---------|
| 🔴 / 🟡 **改变语义可能不会导致编译器错误, 但可能会使用户产生错误的逻辑.** |


</div>


{{ tablesep() }}


<!-- ## Authoring Quality Crates

> **Note** <sup>💬</sup> &mdash; This chapter is mildly **subjective**. That said, it tries to be observational with respect to successful Rust crates (i.e., crates with most downloads should check most of these boxes).


<div class="color-header quality_crate">

#### Code Patterns

| What | Why |
|--------| ---- |
| ☐ Write idiomatic code, follow API guides. |  |
| ☐ Regularly use `clippy`, `fmt` |   |
| ☐ Err on the side of `#[deny]`, not `#[allow]` | asdasd |


#### Infrastructure

| What | Why |
|--------| ---- |
| ☐ Minimize dependencies. | asds |
| ☐ Add optional deps. to essential `trait` crates |  asds |
| ☐ Have unit & integration tests |  asds |
| ☐ Have benchmarks |  asds |


#### Site

| What | Why |
|--------| ---- |
| ☐ Feature **prominent** API example, screenshot ... | asds |
| ☐ Have permissive license for libs. | asds |

</div>

<footnotes>


</footnotes> -->


<!-- Don't render this section for printing, won't be helpful -->
<noprint>

---

# 附录


## 外链和服务 {#links-services}

这里列出了其他的优秀指南和图表.

<div class="color-header lavender">


<!-- This is for major other "cheat sheet" like material on the web. Main question when adding: does it add something
    significant not found elsewhere? -->
| 备忘清单 | 说明 |
|--------| -----------|
| [Rust Learning⭐](https://github.com/ctjhoa/rust-learning) ([中文](https://github.com/ctjhoa/rust-learning/blob/master/zh_CN.md)) | 可能是学习 Rust 最好的链接合集. |
| [Functional Jargon in Rust](https://github.com/JasonShin/functional-programming-jargon.rs) | Rust 的函数式编程术语解释合集. |
| [Periodic Table of Types](http://cosmic.mearie.org/2014/01/periodic-table-of-rust-types) | 解释各种类型和引用是如何联系在一起的. |
| [Futures](https://rufflewind.com/img/rust-futures-cheatsheet.html) | 如何使用 Future. |
| [Rust Iterator Cheat Sheet](https://danielkeep.github.io/itercheat_baked.html) | `std::iter` 和 `itertools` 的迭代器相关方法总结. |
| [Type-Based Rust Cheat Sheet](https://upsuper.github.io/rust-cheatsheet/) | 常见类型和方法表. 可以打印下来挂墙上. |

</div>


{{ tablesep() }}


多数 Rust 资料都由社区开发.


<div class="color-header lavender">

<!-- Official Rust online "books" about Rust itself or major components (e.g., WebAssembly, Embedded, ...). Good test
    for inclusion can be official community involvement, +1k Github stars, ... -->
| 书记&nbsp;️📚  | 说明 |
|--------| -----------|
| [The Rust Programming Language](https://doc.rust-lang.org/stable/book/) ([中文](https://kaisery.github.io/trpl-zh-cn/)) | 《Rust 程序设计语言》, **入门必备**. |
| {{ tab() }} [API Guidelines](https://rust-lang.github.io/api-guidelines/) | 如何编写符合惯例可复用的 Rust. |
| {{ tab() }} [Asynchronous Programming](https://rust-lang.github.io/async-book/)  {{ experimental() }} | 解释 `async` 代码, `Futures`, ... |
| {{ tab() }} [Design Patterns](https://rust-unofficial.github.io/patterns//) | 惯例, 模式和反模式. |
| {{ tab() }} [Edition Guide](https://doc.rust-lang.org/nightly/edition-guide/) | 与 Rust 2015, Rust 2018 等各版本打交道.  |
| {{ tab() }} [Guide to Rustc Development](https://rustc-dev-guide.rust-lang.org/index.html) | 解释编译器内部如何工作. |
| {{ tab() }} [Little Book of Rust Macros](https://veykril.github.io/tlborm/introduction.html) | 社区对 Rust 宏的经验总结. |
| {{ tab() }} [Reference](https://doc.rust-lang.org/stable/reference/) {{ experimental() }} ([中文](https://rustwiki.org/zh-CN/reference/))  | 《Rust 参考手册》.  |
| {{ tab() }} [RFC Book](https://rust-lang.github.io/rfcs/) | 已接受的 RFC 文档, 可以看到它们是如何影响语言的. |
| {{ tab() }} [Performance Book](https://nnethercote.github.io/perf-book/) | 改进速度与内存使用的技术. |
| {{ tab() }} [Rust Cookbook](https://rust-lang-nursery.github.io/rust-cookbook/) | 已被证明是良好实践的例程集. |
| {{ tab() }} [Rust in Easy English](https://dhghomon.github.io/easy_rust/Chapter_3.html) | 用入门级的英语讲的 Rust, **适合入门**, 也适合英语初学者. |
| {{ tab() }} [Rust for the Polyglot Programmer](https://www.chiark.greenend.org.uk/~ianmdlvl/rust-polyglot/index.html) | 经验者的指南. |
| {{ tab() }} [Rustdoc Book](https://doc.rust-lang.org/stable/rustdoc/) | 如何自定义 `cargo doc` 和 `rustdoc`. |
| {{ tab() }} [Rustonomicon](https://doc.rust-lang.org/nomicon/) ([中文](https://nomicon.purewhite.io/)) | 《Rust 秘典》, 旧称《死灵书》, 讲述 Rust unsafe 编程的暗黑艺术. |
| {{ tab() }} [Unsafe Code Guidelines](https://rust-lang.github.io/unsafe-code-guidelines/)  {{ experimental() }} | 编写 `unsafe` 代码的简要指南. |
| {{ tab() }} [Unstable Book](https://doc.rust-lang.org/unstable-book/index.html) | 关于 unstable 的信息, 如 `#![feature(...)]`.  |
| [The Cargo Book](https://doc.rust-lang.org/cargo/) | 如何使用 `cargo` 以及修改 `Cargo.toml`. |
| [The CLI Book](https://rust-lang-nursery.github.io/cli-wg/) | 如何创建 CLI 工具. |
| [The Embedded Book](https://docs.rust-embedded.org/book/intro/index.html) | 在嵌入式和 `#![no_std]` 下工作. |
| {{ tab() }} [The Embedonomicon](https://docs.rust-embedded.org/embedonomicon/) | 运行在 Cortex-M 的首个 `#![no_std]` 指南. |
| [The WebAssembly Book](https://rustwasm.github.io/docs/book/) | 和 Web 以及 `.wasm` 打交道. |
| {{ tab() }} [The `wasm-bindgen` Guide](https://rustwasm.github.io/docs/wasm-bindgen/) | 如何生产 Rust 和 JavaScript API 的绑定. |

</div>

<footnotes>

其他非官方书籍参见 [Little Book of Rust Books](https://lborb.github.io/book/title-page.html).

</footnotes>

<!-- Disabled for now as looks abandoned w/o content -->
<!-- | {{ tab() }} [SIMD Performance Guide](https://rust-lang.github.io/packed_simd/perf-guide/) {{ experimental() }} | Work with `u8x32` or `f32x8` to speed up your computations.  | -->


{{ tablesep() }}

通用组件的综合查找表.

<div class="color-header lavender">

<!-- Table-like sites, often auto-generated. -->
| 列表&nbsp;📋| 说明 |
|--------| -----------|
| [Rust Changelog](https://github.com/rust-lang/rust/blob/master/RELEASES.md) | 查找某个特定版本的变更记录. |
| [Rust Forge](https://forge.rust-lang.org/) | 列出了为编译器奋斗的组织和贡献者. |
| {{ tab() }} [Rust Platform Support](https://doc.rust-lang.org/rustc/platform-support.html) | 所有支持的平台和优先级 (Tier). |
| {{ tab() }} [Rust Component History](https://rust-lang.github.io/rustup-components-history/) | 检查某个平台上 Rust 工具链在 **nightly** 能否正常工作. |
| [ALL the Clippy Lints](https://rust-lang.github.io/rust-clippy/master/) | 列出了所有你可能感兴趣的 [**clippy**](https://github.com/rust-lang/rust-clippy) lints. |
| [Configuring Rustfmt](https://rust-lang.github.io/rustfmt/) | 列出了所有你可以在 `.rustfmt.toml` 中设置的 [**rustfmt**](https://github.com/rust-lang/rustfmt) 选项. |
| [Compiler Error Index](https://doc.rust-lang.org/error-index.html) | 想要知道 `E0404` 什么意思吗? |
</div>

{{ tablesep() }}


提供信息或工具的在线服务.

<div class="color-header lavender">

<!-- Other online web services related to Rust. As a heuristic, things here should
    be essential (or at least address a major concern as "best of class") and be
    a self-contained, user-facing web site. -->
| 服务&nbsp;⚙️ | 说明 |
|--------| -----------|
| [crates.io](https://crates.io/) | Rust 的所有第三方库. |
| [std.rs](https://std.rs/) | 标准库 `std` 文档短链接. |
| [docs.rs](https://docs.rs/) | 第三方库文档, 都是自动从源码构建的. |
| [lib.rs](https://lib.rs/) | Rust 非官方的库和应用. |
| [caniuse.rs](https://caniuse.rs/) | 检查某个特性在哪个 Rust 版本引入或稳定. |
| [Rust Playground](https://play.rust-lang.org/) | 分享一些 Rust 代码片段. |
| [Rust Search Extension](https://rust.extension.sh/) | 用于搜索文档, crate, 属性和书籍的浏览器插件. |

</div>

{{ tablesep() }}


## 打印 PDF {#printing-pdf}


> 点击<a href="https://github.com/kingfree/cheats.rs/releases/"><b>这里</b></a>找到最新的 PDF 文件下载即可. 自己也可以直接通过<i>文件 > 打印</i>并选择“保存成 PDF”(Chrome 和 Edge 是可以的, Firefox 可能有点问题).

</noprint>

<footer>

[Ralf Biedert](https://xr.io), {{ year() }} – [cheats.rs](https://cheats.rs)
<br/>
中文翻译 [Kingfree](https://github.com/kingfree)
<br/>
<noprint>

[许可证](legal)

</noprint>

</footer>
