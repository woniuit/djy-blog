---
sidebar: auto


---
# sql

## MongoDB

**[安装](https://yangyongli.blog.csdn.net/article/details/113917773?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&utm_relevant_index=2)**

### **常用的语句**

**查看当前数据库列表**

```mysql
show dbs
```

**查看当前操作的数据库**

```mysql
db
```

**切换数据库（如果没有这个数据库 会 创建数据库）**

```
use 数据库名称
```

如果真的想把这个数据库创建成功，那么必须插入一个数据。 数据库中不能直接插入数据，只能往[集合](https://so.csdn.net/so/search?q=集合&spm=1001.2101.3001.7020)(collections)中插入数据。
下面命令表示给 itying 数据库的 user 表中插入数据。

```mysql
db.user.insert({"name":"xiaoming"});
```

**显示当前的数据集合**

```mysql
show collections
```

**删除指定的集合 删除表**

```mysql
db.user.drop();
```

**删除当前所在的数据库**

```mysql
db.dropDatabase();
```

**插入（增加）数据**

```mysql
db.表名.insert({"name":"zhangsan"，"age":20});
```

**查询所有记录**

```mysql
db.user.find();
```

**查询 age = 22 的记录**

```mysql
db.user.find({"age": 22});
```

**查询 age > 22 的记录**

```mysql
db.user.find({"age": {$gt: 22}});
```

**查询 age < 22 的记录**

```mysql
db.user.find({"age": {$lt: 22}});
```

**查询 age >= 25 的记录**

```mysql
db.user.find({"age": {$gte: 25}});
```

**查询 age <= 25 的记录**

```mysql
db.user.find({"age": {$lte: 25}});
```

**查询 age >= 23 并且 age <= 26**

```mysql
db.user.find({"age": {$gte: 23, $lte: 26}});
```

**查询 name 中包含 mongo 的数据 模糊查询用于搜索**

```mysql
db.user.find({"name": /mongo/});
```

**查询 name 中以 mongo 开头的**

```mysql
db.user.find({"name": /^mongo/});
```

**查询 name 中以 mongo 结尾的**

```mysql
db.user.find({"name": /mongo$/});
```

[更多语句](https://blog.csdn.net/ZYS10000/article/details/116425819)

### mongoose

**安装**

```
npm install mongoose --save
```

```js
const mongoose = require("mongoose");
async function main() {
    await mongoose.connect("mongodb://localhost:27017/test");
}
main()
    .then((res) => {
        console.log("连接成功", res);
    })
    .catch((err) => {
        console.log("连接失败", err);
    });

const cc = new mongoose.Schema({
    name: {
        type: String,
        require:true
    },
    age: {
        type: Number,
        require:true
    }
});
const modelName = mongoose.model('djyTest', cc);
modelName.create({
    name:"学习完成1",
    age:20
},function (err) {
    if (!err){
        console.log('插入成功')
    }else {
        console.log('失败')
    }
 
})

```

## mysql

### 常见的数据库

通常将数据划分成两类：关系型数据库和非关系型数据库。

关系型数据库：MySQL、Oracle、DB2、SQL Server、Postgre SQL等

- 关系型数据库通常我们会创建很多个二维数据表
- 数据表之间相互关联起来，形成一对一、一对多、多对对等关系；
- 之后可以利用SQL语句在多张表中查询我们所需的数据
- 支持事务，对数据的访问更加的安全

非关系型数据库：MongoDB、Redis、Memcached、HBse等；

- 非关系型数据库的英文其实是Not only SQL，也简称为NoSQL；
- 相当而已非关系型数据库比较简单一些，存储数据也会更加自由（甚至我们可以直接将一个复杂的json对象直接塞入到数据库中）；
- NoSQL是基于Key-Value的对应关系，并且查询的过程中不需要经过SQL解析，所以性能更高；
- NoSQL通常不支持事物，需要在自己的程序中来保证一些原子性的操作

如何在开发中选择他们呢？具体的选择会根据不同的项目进行综合的分析，

- 目前在公司进行后端开发（Node、Java、Go等），还是以关系型数据库为主
- 比较常用的用到非关系型数据库的，在爬取大量的数据进行存储时，会比较常见；

### 安装

[下载地址](https://dev.mysql.com/downloads/mysql/)

选择```GO to Download Page```下载



### Gut工具

Navicat

### mysql的操作

**查看当前数据库**

```sql
#查看所有的数据库
SHOW DATABASES

# 使用某一个数据
USE coderhub(数据库名称);

# 查看当前正在使用的数据库
SELECT DATABASE()
```

**创建新的数据库**

```sql
# 创建数据库语句
CREATE DATABASE IF NOT EXISTS bilibili;
```

**删除数据库**

```sql
# 删除数据库
DROP DATABASE IF EXIT bilibili;
```

**修改数据库**

```sql
# 修改数据库的字符集和排序规则
ALTER DATABASE bilibili CHARACTER SET = utf8 COLLATE = utf8_unicode_ci;
```

### 数据库表的操作

**查看数据表**

```sql
# 查看所有的数据表
SHOW TABLES;
# 查看某一个表结构
DESC user
```

**创建数据表**

```sql
CREATE TABLE IF NOT EXISTS `users`(
name VARCHAR(20),
age INT,
height DOUBLE
);

```

