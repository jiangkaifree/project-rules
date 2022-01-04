# `Sass`/`Less` 风格规范

## 目录

+ 1. 术语
  + 声明规则
  
  + 选择器
  
  + 属性

+ 2. CSS
  - 格式化
  
  - 注释
  
  - oocss 和 BEM
  
  - ID 选择器
  
  - jsvascriopt hooks
  
  - 边框

+ Sass
  
  - 语句
  
  - 属性声明的排序
  
  - 变量
  
  - minxs
  
  - 扩展指令
  
  - 嵌套选择器



## 术语

### 声明规则

声明规则指的是 给予一个选择器(或一组选择器)和一组相伴的属性。下面是一个例子：

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}

```

### 选择器

在规则声明中，“选择器”是决定 `DOM` 树中哪些元素将被定义的属性设置样式的位。选择器可以匹配 `HTML` 元素，以及元素的类、`ID` 或其任何属性。下面是一个例子：

```css
.my-element-class {
  /* ... */
}

[aria-hidden] {
  /* ... */
}


#app {
  ...
}
```

### 属性

最后，属性赋予规则声明的选定元素其样式。属性是键值对，规则声明可以包含一个或多个属性声明，下面是一个小栗子：

```css
/* some selector */ {
  background: #f1f1f1;
  color: #333;
  ... other
}
```

**[⬆ back to top](#目录)**

## CSS

### 格式化

- 使用 `Tab` (2 个 `space`)  进行缩减

- 在类名中，使用 破折号 优于 驼峰命名法。
  
  + 如果您使用 BEM，则下划线和 大驼峰命名法 没问题（请参阅下面的 OOCSS 和 BEM）

- 不要使用 `ID` 选择器

- 在规则声明中使用多个选择器时，给每个选择器各自一行

- 在规则声明的开括号 `{` 前面放置一个空格

- 在属性中，在 `:` 字符之后而不是之前放置一个空格。

- 将规则声明的结束括号 `}` 放在新行上。

#### Bad

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}

```

#### Good

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}

```

### 注释

- 更喜欢使用 `//` 来注释。

- 更喜欢在他们自己的行上发表评论。避免行尾注释。

- 为不是自我记录的代码编写详细的注释
  
  - `z-index` 的用途
  
  - 兼容性或特定于浏览器

### OOCSS 和 BEM

+ 出于以下原因，我们鼓励将 `OOCSS` 和 `BEM` 结合起来:
  
  + 它有助于在 `CSS` 和 `HTML` 之间创建清晰、严格的关系
  
  + 它帮助我们创建可重用、可组合的组件。
  
  + 它允许更少的嵌套和更低的特异性
  
  + 它有助于构建可扩展的样式表

`OOCSS` 即 ”Block-Element-Modifier”, 是一种编写 `CSS` 的方法，它鼓励你把你的样式表看作是“对象”的集合: 可重复使用的、可重复使用的片段，可以在整个网站中独立使用。

+ Nicole Sullivan 的 [OOCSS](https://github.com/stubbornella/oocss/wiki)

+ Smashing Magazine 的 [OOCSS 的介绍](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)

`BEM` 即 “Blocks-Element-Modify” ，是 `HTML` 和 `CSS` 类的命名约定。它最初由 `Yandex` 开发，考虑到大型代码库和可扩展性，可以作为一套实现 `OOCSS` 的可靠指南。

+ ([BEM 101 | CSS-Tricks - CSS-Tricks](https://css-tricks.com/bem-101/))

+ 哈里 罗伯茨 的 [BEM简介]([MindBEMding – getting your head ’round BEM syntax &ndash; CSS Wizardry &ndash; Web Performance Optimisation](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/))

我们推荐一种带有 PascalCased “block”的 `BEM` 变体，它在与组件（例如 `React`）结合时效果特别好。下划线和破折号仍然用于修饰符和子项。

### 例子

```jsx
// ListingCard.jsx
function ListingCard() {
  return (
    <article class="ListingCard ListingCard--featured">

      <h1 class="ListingCard__title">Adorable 2BR in the sunny Mission</h1>

      <div class="ListingCard__content">
        <p>Vestibulum id ligula porta felis euismod semper.</p>
      </div>

    </article>
  );
}

```

```css
/* ListingCard.css */
.ListingCard { }
.ListingCard--featured { }
.ListingCard__title { }
.ListingCard__content { }

```

+ `.ListingCard` 是块级并代表更高级别的组件

+ `.ListingCard__title` 是一个“元素”，代表 `.ListingCard` 的后代，有助于将块组合成一个整体。

+ `ListingCard--featured` 是一个“修饰符”，代表 `.ListingCard` 块的不同状态或变化。

### ID 选择器

虽然可以在 CSS 中通过 ID 选择元素，但通常应将其视为反模式。 ID 选择器为您的规则声明引入了不必要的高级别特异性，并且它们不可重用。



有关此主题的更多信息，请阅读 [CSS Wizardry的关于处理特殊性]([Hacks for dealing with specificity &ndash; CSS Wizardry &ndash; Web Performance Optimisation](https://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/))的文章。

### javascript hooks



避免在 CSS 和 JavaScript 中绑定到同一个类。将两者混为一谈通常至少会导致在重构期间浪费时间，因为开发人员必须交叉引用他们正在更改的每个类，最糟糕的是，开发人员害怕进行更改，因为害怕破坏功能。



我们建议创建特定于 `JavaScript` 的类来绑定，以 `.js-` 为前缀：



```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>

```

### border



#### Bad

```css
.foo {
  border: none;
}

```

#### Good



```css
.foo {
  border: 0;
}

```

**[⬆ back to top](#%E7%9B%AE%E5%BD%95)**



### Sass

#### 语句

+ 使用 `.scss` 语法，而不是原始的 `.sass` 语法

+ 按逻辑顺序排列您的常规 `CSS` 和 `@include` 声明（见下文）

#### 属性声明的排序

1. 属性声明

    列出所有标准属性声明，任何不是 `@include` 或嵌套选择器的声明

```css
.btn-green {
  background: green;
  font-weight: bold;
  // ...
}

```

2. `@include` 声明

最后将 `@includes` 分组可以更容易地阅读整个选择器。

```css
.btn-green {
  background: green;
  font-weight: bold;
  @include transition(background 0.5s ease);
  // ...
}

```

3. 如果需要，嵌套的选择器最后出现，没有什么可以跟上它们。在规则声明和嵌套选择器之间以及相邻嵌套选择器之间添加空格。对嵌套选择器应用与上面相同的指导原则

```css
.btn {
  background: green;
  font-weight: bold;
  @include transition(background 0.5s ease);

  .icon {
    margin-right: 10px;
  }
}

```

#### 变量

比起 驼峰命名法 或 蛇形命名法 命名变量名，更喜欢使用短括号的变量名(例如 `$my-variable`)。可以在只在同一文件中使用的变量名前面加上下划线(例如`$_ my-variable`)。



#### Mixins

`Mixins` 应该用于干燥你的代码、增加清晰度或抽象复杂性——与命名良好的函数大致相同。不接受参数的 `Mixin` 对此很有用，但请注意，如果您不压缩有效负载（例如 `gzip`），这可能会导致生成的样式中出现不必要的代码重复。



#### 扩展指令



`@extend` 应该避免使用，因为它具有不直观和潜在危险的行为，尤其是在与嵌套选择器一起使用时。如果选择器的顺序后来改变（例如，如果它们在其他文件中并且文件的加载顺序发生变化），即使扩展顶级占位符选择器也会导致问题。 Gzipping 应该可以处理您使用 `@extend` 获得的大部分节省，并且您可以使用 `mixins` 很好地干燥样式表。



#### 嵌套选择器

嵌套选择器的深度不要超过三层！

```js
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}

```

当选择器变得这么长的时候，您可能正在编写的 `CSS` 是:

+ 与 HTML 强耦合 或者 弱耦合

+ 过于具体 ，强大

+ 不可重复使用

再说一遍：永远不要嵌套 ID 选择器！



如果您必须首先使用 ID 选择器（并且您真的应该尽量不要），它们不应该被嵌套。如果你发现自己这样做了，你需要重新审视你的标记，或者弄清楚为什么需要如此强的特异性。如果您正在编写格式良好的 HTML 和 CSS，则永远不需要这样做。

**[⬆ back to top](#%E7%9B%AE%E5%BD%95)**
