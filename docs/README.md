# 项目开发规范指引

## 写在前面的话

这是一个项目规范的指引, 并不局限于某一种语言规范。 如果你不知道相关规范, 你可以试着看看或许会有所收获。如果你的团队或者公司有相关的开发规范,请遵循公司团队的标准, 这只是提供个人开发,或者是不了解开发相关规范的一个指引。让你更快的了解一些基础规范。

## 代码命名

请参考链接，里面比较详细的介绍了命名相关的规范 [掘金地址](https://juejin.cn/post/7008071619109191693)。

## 代码注释

下面是一个代码基本的函数注释：

```js
/**
 * TODO  时间格式化
 * @param {number} timestamp 时间戳
 * @param {string} form 时间格式字符串
 * @param {string} [form = 'YYYY-MM-DD'] 时间格式字符串
 * @param {number} type 类型 0:表示失败，1:表示成功
 * @param {array} [date] 日期
 * @param {object} userInfo 用户信息
 * @param {string} userInfo.name 名称
 * @param {number} userInfo.age 年龄
 * @param {string ｜ string[]} [date]
 * @methods getDate 获取当前时间
 * @returns {string} 对应格式化的时间
 */
```

更多指引 [JSDoc](http://yuri4ever.github.io/jsdoc/#@desc)

## 文件注释

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
 * @Date:   2016-07-29 15:57:29
 * @Last Modified by: 小菜鸡
 * @Last Modified time: 2016-08-09 13:29:41
 */
```

## 项目规范

1. 项目必须要有一个 `readme.md`。

拥有 `readme` 文件的原因很简单，就是让不熟悉此项目的人，通过 `readme` 快速了解项目。