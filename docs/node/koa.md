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

### 安装mysql

```shell
# 查找MySQL
dnf search mysql-server

# 查看MySQL，这里的版本是8.0.30
dnf info mysql-server

# 安装MySQL，这里加-y的意思是依赖的内容也安装
dnf install mysql-server -y
```

### 启动mysql-server：

```shell
# 开启MySQL后台服务
systemctl start mysqld

# 查看MySQL服务：active (running)表示启动成功
systemctl status mysqld

# 随着系统一起启动
systemctl enable mysqld
```

### 配置MySQL

```shell
mysql_secure_installation

# 接下来有一些选项，比如密码强度等等一些
# MySQL8开始通常设置密码强度较强，选择2
# 其他的选项可以自行选择
```
![1](/30.png)

选择y,然后2，设置密码，Dengjunyu123.
![1](/31.png)
![1](/32.png)

**连接数据库**

```shell
mysql -uroot -p
```

这个时候必须要配置root可以远程连接：

```shell
# 使用mysql数据库
use mysql;
# 查看user表中，连接权限，默认看到root是localhost
select host, user from user;
# 修改权限
update user set host = '%' where user = 'root';

# 配置生效
FLUSH PRIVILEGES;
```

但是呢，阿里云默认有在安全组中禁止掉3306端的连接的：

这时候我们需要去安全组中添加3306端口

![1](/32.png)

### 数据库迁移

![1](/34.png)

然后新建一个数据库
![1](/35.png)
![1](/36.png)

### 部署node项目

在vscode中安装```remote-ssh```插件
![1](/37.png)

### pm2启动node程序

刚才我们是通过终端启动的node程序，那么如果终端被关闭掉了呢？

* 那么这个时候相当于启动的Node进程会被关闭掉；
* 我们将无法继续访问服务器；

在真实的部署过程中，我们会使用一个工具pm2来管理Node的进程：

* PM2是一个Node的进程管理器；
* 我们可以使用它来管理Node的后台进程；
* 这样在关闭终端时，Node进程会继续执行，那么服务器就可以继续为前端提供服务了；

安装pm2：

```shell
npm install pm2 -g
```

pm2常用的命令：

```shell
# 命名进程
pm2 start ./src/main.js --name my-api 
# 显示所有进程状态
pm2 list               
# 停止指定的进程
pm2 stop 0       
# 停止所有进程
pm2 stop all           
# 重启所有进程
pm2 restart all      
# 重启指定的进程
pm2 restart 0          

# 杀死指定的进程
pm2 delete 0           
# 杀死全部进程
pm2 delete all   

#后台运行pm2，启动4个app.js，实现负载均衡
pm2 start app.js -i 4 
```

###  jenkins自动化部署

#### 安装Java环境

Jenkins本身是依赖Java的，所以我们需要先安装Java环境：

* 这里我安装了Java1.8的环境

```shell
dnf search java-1.8
dnf install java-1.8.0-openjdk.x86_64
然后敲java验证是否安装成功
```

#### 安装Jenkins

因为Jenkins本身是没有在dnf的软件仓库包中的，所以我们需要连接Jenkins仓库：

* wget是Linux中下载文件的一个工具，-O表示输出到某个文件夹并且命名为什么文件；
* rpm：全称为**The RPM Package Manage**，是Linux下一个软件包管理器；

```shell
wget –O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
#然后输入ls查看是否安装成功
#修改文件路径
mv jenkins.repo /etc/yum.repos.d/
# 导入GPG密钥以确保您的软件合法
rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
# 或者
rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
```

编辑一下文件/etc/yum.repos.d/jenkins.repo

* 可以通过vim编辑

  ```shell
  vi jenkins.rep
  ```

  