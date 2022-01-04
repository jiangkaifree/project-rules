# 快速上手

## 必要的

### 1. README.md

项目必须包含一个 `README.md` 文件，该文件必须包含项目的标题及简要说明：

```md
# ipsec 管理后台
该项目使用 umi + antd + hooks + ts 搭建。基于 webpack 打包构建。遵守 ESlint 规范。使用 Prettier 进行代码格式化。项目部署地址 http://192.168.20.111:3000 ......
```

以及包含下面的二级标题内容：

- 文件目录介绍

```md
|--- flkjs    原工程文件
|
|--- public   公共文件
|
|--- src      新工程开发文件
|---  |
|---  |--- sm2.back.js  sm2文件对应原文件
|---  |--- wte.back.js  wte文件对应原文件
|---  |--- README.md  原工程README文件
|
|--- gulpfile.js  gulp配置文件
|
|--- webpack.config.js  webpack配置文件
|
|--- UPDATE.md  针对客户系统进行调试问题记录文件
```

- 项目运行

下面是一个简单的示例：

```md
1. 安装
使用 yarn 或者 npm 安装依赖，推荐使用 yarn 。

2. 运行
在项目根目录下执行 yarn dev 或者 npm run dev 命令，运行项目。

3. 打包部署
执行 yarn build 或 npm run build 命令，生成项目部署文件。

···
```

### 2. 使用 `ES6` 语法

项目应当尽量使用 `ES6` 相关语法：

```js
// 使用 const 声明
// 坏的
var num = 1;

// 好的
let num = 1;
const num = 1;
```

```js
// 使用结构赋值
const obj = {
  a: 1,
  b: 2,
};

// 坏的
const a = obj.a
const b = obj.b

// 好的
const {a, b} = obj
```

```js
// 使用模板字符串

// 坏的
const str = 'hello' + name + '!'

// 好的
const str = `hello ${name}!`
```

## 建议的
