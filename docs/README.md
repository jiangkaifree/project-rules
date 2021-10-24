# 项目开发规范指引

## 写在前面的话

这是一个项目规范的指引, 并不局限于某一种语言规范。 如果你不知道相关规范, 你可以试着看看或许会有所收获。如果你的团队或者公司有相关的开发规范,请遵循公司团队的标准, 这只是提供个人开发,或者是不了解开发相关规范的一个指引。让你更快的了解一些基础规范。

## 规范的命名

请参考链接，里面比较详细的介绍了命名相关的规范 [掘金地址](https://juejin.cn/post/7008071619109191693)。

基于上文再进行如下补充：

1. 全局常量的命名

项目当中会用到全局范围内的静态常量，这时候我们应当进行全大写，这意味着这个变量时全局性质的，如：

```js
const BASEURL = 'http:localhost:3000/api'
```

## 规范的注释

### 基本的函数注释

```js
/**
 * TODO  时间格式化
 * @param {number} timestamp 时间戳
 * @param {string} form 时间格式字符串
 * @param {string} [form = 'YYYY-MM-DD'] 时间格式字符串
 * @param {number} type 类型 0:表示失败，1:表示成功
 * @param {string[]} time 时间戳
 * @param {object} userInfo 用户信息
 * @param {string} userInfo.name 名称
 * @param {number} userInfo.age 年龄
 * @methods or @func getDate 获取当前时间
 * @returns {string} 对应格式化的时间YYYY-MM-DD HH:mm:ss
 */
```

* 第一行： 简述方法实现功能。

* 第二行： 参数`timestamp` 是时间戳，类型是 `number` 。

* 第三行：参数 `form` 是要转换的格式，类型是 `string`。

* 第四行：参数 `form` 是要转换的格式，它有一个默认值 `YYYY-MM-DD` ,类型是 `string`。

* 第五行：参数 `type` 是枚举类型，要么是 `0`, 要么是 `1` , 分别代表失败和成功。类型是 `number`。

* 第六行：参数 `time` 表示时间戳，但是它的类型是 `string` 数组。

* 第七行：参数 `userInfo` 表示用户信息的参数，是一个 `object` 类型。

* 第七行：参数 `userInfo` 的 `name` 属性表示名称，是 `string` 类型。

* 第七行：参数 `userInfo` 的 `age` 属性表示年龄，是 `number` 类型。

* 第八行：此方法使用到了 `getDate` 方法，这是一个获取当前时间的方法，也可以使用 `@func` 表示。

* 第九行： 此方法返回一个 `string` 类型的格式化的时间，形如 YYYY-MM-DD HH:mm:ss。

### 单行注释

单行注释通常后接一个空格

```js
// 这是说明内容
```

我们通常在语句逻辑间进行使用，进行更为细节性的解释说明。举例：

```js
onOk() {
  if (val === true) {
    // 当val为true时，进行相对的操作

  }else {
    // 否则，进行。。。。
  }
}
```

我们应当尽量避免注释过于繁琐，注释应该简洁明了，首先我们应当通过函数名，以及变量名来获取 **大概信息**。应当避免重复性的上下文内容出现。

更多指引 [JSDoc](http://yuri4ever.github.io/jsdoc/#@desc)

## 规范的文件注释

通常我们会有一些处理的函数, 例如：时间格式化的方法。通常我们会提取到一个 `utils.js` 文件中来。这样的目的有两个：

1. 可能我们多个地方需要用的，统一处理，来源唯一。

2. 代码抽离，减少代码量, 方便后期扩展。

下面是一个时间格式化的方法：

```js
/**
 * TODO  时间格式化
 * @param timestamp 时间戳
 * @param form 时间格式
 * @returns 对应格式化的时间
 */
export const timeFormat = (
  timestamp: number,
  form: string = "YYYY-MM-DD HH:mm:ss"
) => {
  const time = dayjs(timestamp).format(form);
  return time;
};
```

那么，我们最好需要为文件生成一个文件头信息。来告示这个文件是干什么的。当然了，通过文件名我们也可以对这份文件的功能进行大概的了解。文件头信息可以记录的更为详细具体。
下面是一个文件头信息：

```js
/*
 * 工具函数方法文件
 * @Author 小菜鸡
 * ？@Date 2021-10-14 21:34:52
 * ？@version 版本号
 * ？@description 该版本改动信息
 */
```

上面的例子中：

* 第一行文件功能介绍

* 第二行文件作者

* 第三行可选 文件生成时间（可选）

* 第四行版本号 （可选）

* 第五行版本改动信息（可选）

这里相关的文件头部信息可以使用 `vscode` 相关插件来配置生成。 `vscode-fileHeader` `koroFileHeader` 。同时为我们记录谁修改了文件，修改的时间：

```js
/*
 * @Author: 小菜鸡
 * @Date: 2016-07-29 15:57:29
 * @Last Modified by: 小菜鸡
 * @Last Modified time: 2016-08-09 13:29:41
 */
```

## 项目的规范

### 项目必须有一个 `readme.md`

拥有 `readme` 文件的原因很简单，就是让不熟悉此项目的人，通过 `readme` 快速了解项目。

## `Vue`项目的规范

[Vue官网文档指引](https://cn.vuejs.org/v2/style-guide/)

## 其他

大厂公司的代码标准也是值得我们看看了解到。

[腾讯](https://tgideas.qq.com/doc/index.html) [京东凹凸](https://guide.aotu.io/index.html) [网易](http://nec.netease.com/standard) [爱彼迎](https://github.com/airbnb/javascript)

同时, 还有一些编辑器插件能够让我们形成统一的代码风格。

[ESlint](https://eslint.bootcss.com/)  [Prettier](https://prettier.io/)。