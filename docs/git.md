# git commit message 提交规范指引

`git` 规范的提交能让你迅速的找到相关的提交内容，以及清晰明了的看到每次的改动内容。本指引阐述 `git` 提交的相关规范内容。使用比较多的是 [`Angular` 团队的规范](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines)。

## Commit Message 格式

`Commit Message` 包括三个部分： **Header** ，**Body** ， **Footer**。格式如下：

```shell
<Header>
// 空一行
<body>
// 空一行
<Footer>
```

其中 `Header` 板块是必须的，简单地说 他相当于 `html` 中的 `h1` 标签。`Body` 和 `Footer` 则可以不写。

> 注意： 提交信息的任何一行不能超过 100 个字符！这使得消息在 `GitHub` 以及各种 `git` 工具中更易于阅读。

## Header

`Header` 包括三个部分， `type`， `scope`， `subject` 。其中 `scope`  是可选项。

```shell
<type>(<scope>): <subject>
feat($route): add support for the `reloadOnUrl` configuration option
```

### type

`type` 用于说明 `commit` 的类别，具体标识如下：

+ `feat`：一个新的功能 （`feature`）
+ `fix` ：修改 `bug`
+ `docs` ：修改文档部分，比如 `README.md`。
+ `style`：修改代码格式，不影响代码含义的修改（白字、格式化、缺少分号等）。
+ `refactor`：代码的重构，一个既没有修复错误也没有增加功能的代码修改。
+ `perf`： 提高性能的代码更改。
+ `test`：添加缺失或纠正现有测试。
+ `chore`： 对构建过程或辅助工具和库（例如文档生成）的更改。
+ `revert`：版本代码回退，后跟还原提交的标头。在 `body` 中它应该说：This reverts commit <hash>.，其中哈希是要恢复的提交的 SHA。
+ `build`： 修改影响项目构建文件或外部依赖项，比如`npm`、`gulp`、`webpack`、`broccoli`等。
+ `merge` 代码合并

### scope

`scope`是用于说明`commit`的影响范围，比如数据层、控制层、视图层等等，视项目不同而不同。

如果你的修改影响了不止一个`scope`，就可以使用`*`代替。

### subject

主题包含对更改的简洁描述:

1. 使用祈使语气，现在时：“change” 不是 “changed” 也不是 “changes”
2. 第一个字母不要大写
3. 末尾没有点（.）或者句号（。）

## Body

+ `Body` 应当是对本次 `commit` 的详细描述，可以分为多行。
+ 就像在主语中一样，使用祈使式现在时：“change”不是“changed”也不是“changes”。
+ 应该包括改变的动机，并将其与以前的行为进行对比。

下面是应该简单的示例：

```shell
增加axios封装板块，增加api接口模块

- 进一步封装有利于请求响应的拦截，错误处理
```

## Footer

页脚应包含有下面两个部分： 1. 关重大更改的任何信息 (BREAKING CHANGE)，2. 处理 `Issue`。

不兼容之处应该以 `BREAKING CHANGE:` 开头，带有一个空格或两个换行符。然后将提交消息的其余部分用于此目的。详细的解释可以在这个文档中找到。

### 不兼容变动

```shell
BREAKING CHANGE:  不再兼容ie10以下浏览器
```


### 处理 Issue

如果当前`commit`是针对处理某个`issue`，那么可以在`Footer`部分标注处理的`issue`。

```shell
Fix #111
```

## 例子

这是一些简单的示例

feat
```shell
feat: 增加新的接口api
```

fix
```shell
fix(create): 修改创建初始化xhr参数问题
```

reverts
```shell
revert: feat: 增加新的接口api

This reverts commit 667ecc1654a317a13331b17617d973392f415f02.
```

这是一些包含 `body`, `footer` 的例子

```shell
test: 增加jest测试
 
增加createAxios 测试。增加init 参数

BREAKING CHANGE： create api 增加参数

before： create({
    methods: 'get'
})

now： create()

不在需要默认参数
```

```shell
build: 修改webpack config, 去除语法转换

不再支持ie浏览器

FIX #231, #342, #123
```

## 相关插件

[`Commitzen` 快速编写我们的 commit message](https://github.com/commitizen/cz-cli)

[`commitlint` 规范项目commit message](https://github.com/conventional-changelog/commitlint)



## 参考资料

[conventionalcommits](https://www.conventionalcommits.org/zh-hans/v1.0.0/)

