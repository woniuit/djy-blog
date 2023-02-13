---
sidebar: auto


---
# koa

## 安装

```
npm install koa
```

`https://github.com/koajs/koa`

## 初体验Hello koa

```js
const Koa = require("koa");
const app = new Koa();

// response
app.use((ctx) => {
    ctx.body = "Hello Koa";
});

app.listen(8000, () => {
    console.log("koa初体验服务器启动成功~");
});

```

## 中间件

```js
const Koa = require('koa');

const app = new Koa();

// use注册中间件
app.use((ctx, next) => {
  if (ctx.request.url === '/login') {
    if (ctx.request.method === 'GET') {
      console.log("来到了这里~");
      ctx.response.body = "Login Success~";
    }
  } else {
    ctx.response.body = "other request~";
  }
});

// 没有提供下面的注册方式
// methods方式: app.get()/.post
// path方式: app.use('/home', (ctx, next) => {})
// 连续注册: app.use((ctx, next) => {
// }, (ctx, next) => {
// })

app.listen(8000, () => {
  console.log("koa初体验服务器启动成功~");
});

```

## 路由

依赖```koa-router```

安装

```
npm install koa-router
```

router.js

```js
const Router = require('koa-router');

const router = new Router({prefix: "/users"});

router.get('/', (ctx, next) => {
  ctx.response.body = "User Lists~";
});

router.put('/', (ctx, next) => {
  ctx.response.body = "put request~";
});


module.exports = router;

```

使用

```js
const Koa = require('koa');

const userRouter = require('./router/user');

const app = new Koa();

app.use((ctx, next) => {
  // ctx.response.body = "Hello World";
  next();
});

app.use(userRouter.routes());
app.use(userRouter.allowedMethods());

app.listen(8000, () => {
  console.log("koa路由服务器启动成功~");
});

```

## 参数解析-query-params

```js
const Koa = require('koa');

const app = new Koa();
const Router = require('koa-router');

const userRouter = new Router({prefix: '/users'});

userRouter.get('/:id', (ctx, next) => {
  console.log(ctx.request.params);
  console.log(ctx.request.query);
})

// app.use((ctx, next) => {
//   console.log(ctx.request.url);
//   console.log(ctx.request.query);
//   console.log(ctx.request.params);
//   ctx.response.body = "Hello World";
// });

app.use(userRouter.routes());

app.listen(8000, () => {
  console.log("参数处理服务器启动成功~");
});

```

## 参数解析-json-urlencoded-formdata

依赖```koa-bodyparser```

安装

```
npm install koa-bodyparser
```

```js
const Koa = require('koa');
const bodyParser = require('koa-bodyparser');


const app = new Koa();



app.use(bodyParser());


app.use((ctx, next) => {
  console.log(ctx.request.body);
  console.log(ctx.req.body);
  ctx.response.body = "Hello World";
});

app.listen(8000, () => {
  console.log("koa初体验服务器启动成功~");
});

```

## 文件上传

依赖```koa-multer```

```
npm install koa-multer
```

```js
const Koa = require('koa');
const Router = require('koa-router');
const multer = require('koa-multer');

const app = new Koa();
const uploadRouter = new Router({prefix: '/upload'});

// const storage = multer.diskStorage({
//   destination,
//   filename,
// })

const upload = multer({
  dest: './uploads/'
});

uploadRouter.post('/avatar', upload.single('avatar'), (ctx, next) => {
  console.log(ctx.req.file);
  ctx.response.body = "上传头像成功~";
});

app.use(uploadRouter.routes());

app.listen(8000, () => {
  console.log("koa初体验服务器启动成功~");
});

```

## 响应内容

```js
const Koa = require('koa');

const app = new Koa();

app.use((ctx, next) => {
  // ctx.request.query
  // ctx.query

  // 设置内容
  // ctx.response.body
  // ctx.response.body = "Hello world~"
  // ctx.response.body = {
  //   name: "coderwhy",
  //   age: 18,
  //   avatar_url: "https://abc.png"
  // };
  // 设置状态码
  // ctx.response.status = 400;
  // ctx.response.body = ["abc", "cba", "nba"];

  // ctx.response.body = "Hello World~";
  ctx.status = 404;
  ctx.body = "Hello Koa~";
});

app.listen(8000, () => {
  console.log("koa初体验服务器启动成功~");
});

```

## 静态服务器

```js
const Koa = require('koa');
const staticAssets = require('koa-static');

const app = new Koa();

app.use(staticAssets('./build'));

app.listen(8000, () => {
  console.log("koa初体验服务器启动成功~");
});

```

## 部署

### 连接云服务器

用git bash ssh工具

```shell
ssh root@ip地址公
```
![1](/25.png)

### 安装nodejs

```shell
# 搜索软件包
dnf search nodejs

# 查看软件包信息: nodejs的版本是10.21.0
dnf info nodejs

# 安装nodejs
dnf install nodejs
```

