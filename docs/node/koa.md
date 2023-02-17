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

```shell
# 下载 Jenkins 资源
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
# 获取并导入信任 的包制作者的秘钥
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
# 升级 yum 源中的所有包
sudo yum upgrade
# Jenkins 依赖于 java 所以需要安装 JDK
sudo yum install java-11-openjdk
# 安装 Jenkins
sudo yum install jenkins
```

如果最终 `Jenkins` 没有找到包而导致没有安装成功，检查第一步和第二部执行结果并重新执行。

#### 启动Jenkins

```shell
# 启动 Jenkins 服务
systemctl start jenkins
# 重启 Jenkins 服务
systemctl restart jenkins
# 停止 Jenkins 服务
systemctl stop jenkins
# 查看 Jenkins 服务状态
systemctl status jenkins
```

启动成功之后在浏览器输入服务器ip地址加上在安全组配置的8080端口

```shell
8.134.23.237:8080
```
![1](/38.png)

`cat /var/lib/jenkins/secrets/initialAdminPassword` 查看密码

随后进入插件安装页面，暂时安装系统推荐插件即可,然后创建用户

## nginx安装和配置

### 安装

**安装相应的工具包和库**

```shell
yum -y install gcc gcc-c++ autoconf pcre-devel make automake
yum -y install wget httpd-tools vim
```

基本上没什么大问题就会显示“Complete!”

恭喜你，服务器环境基本安装完毕～

#### **搭建Nginx配置**

首先看看服务器内yum内的Nginx源的版本

```shell
yum list | grep nginx
```

在终端输入如下

```shell
vim /etc/yum.repos.d/nginx.repo
```

后填入下列代码，注意，我的centos是7.x版本，所以我写的是7，同学们可以按照自己的版本来

![1](/56.png)

保存退出，然后安装 nginx

```shell
yum install nginx
nginx -v
```

#### **Nginx的配置文件**

通过`rpm -ql nginx` 指令查看 Nginx 都安装到了哪些目录

解释一下 `/etc/nginx/nginx.conf`，因为这个是 Nginx 的主配置，比较重要

输入命令行

```shell
cd /etc/nginx
vim nginx.conf
```

然后输入i编辑

把user后面的改成root
![1](/4.png)

```shell
server {
        listen       80;
        listen       [::]:80;
        server_name  _;
        root         /usr/share/nginx/html;  //这个就是我们默认访问的页面

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }
    }
```

```shell
server {
        listen       80;
        listen       [::]:80;
        server_name  _;
       注释掉 root         /usr/share/nginx/html;  //这个就是我们默认访问的页面 

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;
        添加
         location / {
           root /root/djycms; //我们文件地址
           index index.html;
        }

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }
    }
```

然后保存，输入`nginx -s reload` 会报错`nginx: [error] open() "/var/run/nginx.pid" failed (2: No such file or directory)`， 这个时候可以如下

```shell
// 先输入
nginx
nginx -s reload
```

或者是如果你使用 iTerm 的话，可以配置 .bashrc 文件，添加一个 alias 的配置来简化运行nginx指令；或者是通过指令 `systemctl start nginx.service` 启动 nginx 服务，通过指令 `ps aux | grep nginx` 查看 nginx 是否是否启动；还有很多 nginx 的指令，大家自行去官网查看





启动nginx：

```shell
systemctl start nginx
systemctl status nginx
systemctl enable nginx
```

然后cd

```shell
cd /root/
```

```shell
mkdir djycms  //ls查看是否创建文件夹成功
```

```shell
touch index.html //ls查看是否创建成功
```

如果遇到问题先查看nginx是否在运行

```shell
ps -ef | grep nginx //查看是否运行
service nginx stop //停止
ps -ef |grep nginx //查看是否运行
nginx -s stop //停止
service nginx stop //停止
chkconfig nginx off
rm -rf /etc/init.d/nginx
find / -name nginx //查找关于nginx文件
rm -rf /usr/sbin/nginx //删除关于nginx的文件
yum remove nginx
systemctl status nginx
yum install -y nginx //重新安装
systemctl start nginx //启动
cd /etc/nginx/ //进入nginx的conf目录（按照自己实际的路径来） nginx -t查找文件夹
vim nginx.conf
```

#### 安装git

```shell
dnf install git
```




然后用vscode中的remote-ssh插件连接远程服务器

![1](/38.png)

就可以看到刚才创建的djycms文件夹了

## Jenkins建项目

左边的新建任务
![1](/54.png)
![1](/55.png)
![1](/57.png)
![1](/58.png)
![1](/59.png)
![1](/60.png)
![1](/61.png)
![1](/62.png)
![1](/63.png)
![1](/64.png)
![1](/65.png)
![1](/66.png)

#### 构建触发器

这里的触发器规则是这样的：

* 定时字符串从左往右分别是：分 时 日 月 周

```shell
#每半小时构建一次OR每半小时检查一次远程代码分支，有更新则构建
H/30 * * * *

#每两小时构建一次OR每两小时检查一次远程代码分支，有更新则构建
H H/2 * * *

#每天凌晨两点定时构建
H 2 * * *

#每月15号执行构建
H H 15 * *

#工作日，上午9点整执行
H 9 * * 1-5

#每周1,3,5，从8:30开始，截止19:30，每4小时30分构建一次
H/30 8-20/4 * * 1,3,5
```

![1](/68.png)
![1](/69.png)

安装完后勾选重启
![1](/70.png)
![1](/71.png)

然后点击保存
![1](/72.png)
![1](/73.png)
![1](/74.png)
![1](/75.png)
![1](/76.png)

```shell
pwd
node -v
npm -v
npm install
npm run build
echo '构建完成'
ls
mv -rf ./dist/*/root/djycms    //把dist文件强制移到远程服务器root的djycms下面
```

然后点击保存，再点击左边的立即构建

