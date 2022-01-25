# `CSS` 代码风格指南

## 通用约定

### Class 和 ID

- 使用语义化、通用的命名方式；
- 使用连字符 - 作为 `ID`、`Class` 名称界定符，不要驼峰命名法和下划线；
- 避免选择器嵌套层级过多，尽量少于 **3** 级；
- 避免选择器和 `Class`、`ID` 叠加使用；

出于性能考量，在没有必要的情况下避免元素选择器叠加 `Class`、`ID` 使用。

元素选择器和 `ID`、`Class` 混合使用也违反关注分离原则。如果 `HTML` 标签修改了，就要再去修改 `CSS` 代码，不利于后期维护。

```css
/* 不好的 */
.red {
}
.box_green {
}
.page .header .login #username input {
}
ul#example {
}

/* 好的 */
#nav {
}
.box-video {
}
#username input {
}
#example {
}
```

### 声明块格式

- 选择器分组时，保持独立的选择器占用一行；
- 声明块的左括号 `{` 前添加一个空格；
- 声明块的右括号 `}` 应单独成行；
- 声明语句中的 `:` 后应添加一个空格；
- 声明语句应以分号 `;` 结尾
- 一般以逗号分隔的属性值，每个逗号后应添加一个空格；
- `rgb()`、`rgba()`、`hsl()`、`hsla()` 或 `rect()` 括号内的值，逗号分隔，但逗号后不添加一个空格；
- 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；`-.5px` 代替 `-0.5px` ）；
- 十六进制值应该全部小写和尽量简写，例如，`#fff` 代替 `#ffffff`；
- 避免为 0 值指定单位，例如，用 `margin: 0`; 代替 `margin: 0px;` ；

```css
/*  不好的  */
.selector,
.selector-secondary,
.selector[type="text"] {
    padding: 15px;
    margin: 0px 0px 15px;
    background-color: rgba(0, 0, 0, 0.5);
    box-shadow: 0px 1px 2px #ccc, inset 0 1px 0 #ffffff;
}

/* 好的 */
.selector,
.selector-secondary,
.selector[type="text"] {
    padding: 15px;
    margin-bottom: 15px;
    background-color: rgba(0, 0, 0, 0.5);
    box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

### 声明顺序

相关属性应为一组，推荐的样式编写顺序

1. Positioning
2. Box model
3. Typographic
4. Visual

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型决定了组件的尺寸和位置，因此排在第二位。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

```css
.declaration-order {
    /* Positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    /* Box model */
    display: block;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 1px solid #e5e5e5;
    border-radius: 3px;
    margin: 10px;
    float: right;
    overflow: hidden;

    /* Typographic */
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    text-align: center;

    /* Visual */
    background-color: #f5f5f5;
    color: #fff;
    opacity: 0.8;

    /* Other */
    cursor: pointer;
}
```

### 引号使用

`url()` 、属性选择符、属性值使用双引号。避免 `url` 中包含特殊字符，例如 `()\`，转义后导致错误。

> 

```css
/* 不好的 */
@import url(//www.google.com/css/maia.css);

html {
    font-family: "open sans", arial, sans-serif;
}

/* 好的 */
@import url("//www.google.com/css/maia.css");

html {
    font-family: "open sans", arial, sans-serif;
}

.selector[type="text"] {
}
```

### 媒体查询

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。

```css
.element {
    ...;
}
.element-avatar {
    ...;
}
.element-selected {
    ...;
}

@media (max-width: 768px) {
    .element {
        ...;
    }
    .element-avatar {
        ...;
    }
    .element-selected {
        ...;
    }
}
```

### 不要使用 `@import`

与 `<link>` 相比，`@import` 要慢很多，不光增加额外的请求数，还会导致不可预料的问题。替换方法：

- 使用多个 元素；
- 通过 `Sass` 或 `Less` 类似的 `CSS` 预处理器将多个 `CSS` 文件编译为一个文件；
- 其他 `CSS` 文件合并工具；

### 无需添加浏览器厂商前缀

使用 `Autoprefixer` 自动添加浏览器厂商前缀，编写 `CSS` 时不需要添加浏览器前缀，直接使用标准的 `CSS` 编写。
`Autoprefixer` 通过 [Can I use](https://caniuse.com/)，按兼容的要求，对相应的 `CSS` 代码添加浏览器厂商前缀。