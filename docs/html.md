# HTML 代码规范指南

尽量遵循 `HTML` 标准和语义，但是不要以牺牲实用性为代价。任何时候都要尽量使用最少的标签并保持最小的复杂度。

## 通用约定

### 标签

- 自闭合（self-closing）标签，无需闭合 ( 例如： `img` `input` `br` `hr` 等 )；

- 可选的闭合标签（closing tag），需闭合 ( 例如：`</li>` 或 `</body>` )；

- 尽量减少标签数量；

```html
<img
    src="https://atts.w3cschool.cn/attachments/image/cimg/google.png"
    alt="Google"
/>
<input type="text" name="title" />

<ul>
    <li>Style</li>
    <li>Guide</li>
</ul>

<!-- 坏的 -->
<span class="avatar">
    <img src="..." />
</span>

<!-- 好的 -->
<img class="avatar" src="..." />
```

### `Class` 和 `ID`

- `class` 应以功能或内容命名，不以表现形式命名；
- `class` 与 `id` 单词字母小写，多个单词组成时，采用中划线-分隔；
- 使用唯一的 `id` 作为 在 `javascript` 中使用, 同时避免创建无样式信息的 `class`；

```html
<!-- 不好 -->
<div class="j-hook left contentWrapper"></div>

<!-- 好的 -->
<div id="j-hook" class="sidebar content-wrapper"></div>
```

### 属性顺序

HTML 属性应该按照特定的顺序出现以保证易读性。

- id
- class
- name
- data-xxx
- src, for, type, href
- title, alt
- aria-xxx, role

```html
<a id="..." class="..." data-modal="toggle" href="###"></a>

<input class="form-control" type="text" />

<img src="..." alt="..." />
```

### 引号

属性的定义，统一使用双引号。

```html
<!-- 坏的 -->
<span id="j-hook" class="text">Google</span>

<!-- 好的 -->
<span id="j-hook" class="text">Google</span>
```

### 嵌套

**`a` 不允许嵌套 `div`** 这种约束属于语义嵌套约束，与之区别的约束还有严格嵌套约束，比如 **`a` 不允许嵌套 `a`**。

严格嵌套约束在所有的浏览器下都不被允许；而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样。

语义嵌套约束:

- `<li>` 用于 `<ul>` 或 `<ol>` 下；
- `<dd>`, `<dt>` 用于 `<dl>` 下；
- `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<td>` 用于 `<table>` 下；

严格嵌套约束：

- inline-Level 元素，仅可以包含文本或其它 inline-Level 元素;
- `<a>` 里不可以嵌套交互式元素 `<a>`、`<button>` 、`<select>` 等;
- `<p>` 里不可以嵌套块级元素 `<div>`、`<h1>~<h6>`、`<p>`、`<ul>`/`<ol>`/`<li>`、`<dl>`/`<dt>`/`<dd>`、`<form>`等。

### 布尔值属性

HTML5 规范中 `disabled`、`checked`、`selected` 等属性不用设置值。

```html
<input type="text" disabled />

<input type="checkbox" value="1" checked />

<select>
    <option value="1" selected>1</option>
</select>
```

## 语义化

没有 `CSS` 的 `HTML` 是一个语义系统而不是 UI 系统。

通常情况下，每个标签都是有语义的，所谓语义就是你的衣服分为外套， 裤子，裙子，内裤等，各自有对应的功能和含义。所以你总不能把内裤套在脖子上吧。

此外语义化的 `HTML` 结构，有助于机器（搜索引擎）理解，另一方面多人协作时，能迅速了解开发者意图。

常见标签语义：

| 标签              | 语义       |
| --------------- | -------- |
| `<a>`           | 链接       |
| `<p>`           | 段落       |
| `<h1>` ~ `<h6>` | 标题       |
| `<ul>`          | 无序列表     |
| `ol`            | 有序列表     |
| `<strong>`      | 为强调内容而加粗 |

当你构建页面当作一本书，讲标签的语义对应其功能和含义：

- 书的名称：`<h1>`
- 书的每个章节标题: `<h2>`
- 章节内的文章标题: `<h3>`
- 小标题/副标题: `<h4>` `<h5>` `<h6>`
- 章节的段落: `<p>`
