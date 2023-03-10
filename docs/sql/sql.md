---
sidebar: auto
---
# sql

## MongoDB

**[安装](https://yangyongli.blog.csdn.net/article/details/113917773?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&utm_relevant_index=2)**

### **常用的语句**

**查看当前数据库列表**

```sql
show dbs
```

**查看当前操作的数据库**

```sql
db
```

**切换数据库（如果没有这个数据库 会 创建数据库）**

```sql
use 数据库名称
```

如果真的想把这个数据库创建成功，那么必须插入一个数据。 数据库中不能直接插入数据，只能往[集合](https://so.csdn.net/so/search?q=集合&spm=1001.2101.3001.7020)(collections)中插入数据。
下面命令表示给 itying 数据库的 user 表中插入数据。

```sql
db.user.insert({"name":"xiaoming"});
```

**显示当前的数据集合**

```sql
show collections
```

**删除指定的集合 删除表**

```sql
db.user.drop();
```

**删除当前所在的数据库**

```sql
db.dropDatabase();
```

**插入（增加）数据**

```sql
db.表名.insert({"name":"zhangsan"，"age":20});
```

**查询所有记录**

```sql
db.user.find();
```

**查询 age = 22 的记录**

```sql
db.user.find({"age": 22});
```

**查询 age > 22 的记录**

```sql
db.user.find({"age": {$gt: 22}});
```

**查询 age < 22 的记录**

```sql
db.user.find({"age": {$lt: 22}});
```

**查询 age >= 25 的记录**

```sql
db.user.find({"age": {$gte: 25}});
```

**查询 age <= 25 的记录**

```sql
db.user.find({"age": {$lte: 25}});
```

**查询 age >= 23 并且 age <= 26**

```sql
db.user.find({"age": {$gte: 23, $lte: 26}});
```

**查询 name 中包含 mongo 的数据 模糊查询用于搜索**

```sql
db.user.find({"name": /mongo/});
```

**查询 name 中以 mongo 开头的**

```sql
db.user.find({"name": /^mongo/});
```

**查询 name 中以 mongo 结尾的**

```sql
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

推荐大家直接下载安装版本，在安装过程中会配置一些环境变量；

- Windows推荐下载MSI的版本；
- Mac推荐下载DMG的版本；
![1](/3-1.png)

**Windows安装过程**
![1](/3-2.png)
![1](/3-3.png)
![1](/3-4.png)
![1](/3-5.png)
![1](/3-6.png)

**mysql的连接操作**

一、环境变量配置

在任务栏搜索中搜索MySQL

![1](/3-7.png)
![1](/3-8.png)

二、终端连接数据库

```mysql -uroot -p```
![1](/3-9.png)
如上图连接成功

三、终端数据库操作

```show databases;```//查看数据库



### Gut工具Navicat

[下载地址](https://www.navicat.com.cn/download/direct-download?product=navicat_premium_cs_x64.exe&location=1)

使用

点击新建连接，创建连接，然后点击查询，新建查询就可以操作sql语句。



### 数据库的操作

查看当前数据库：

```sql
# 查看所有的数据
SHOW DATABASES;
# 使用某一个数据
USE coderhub;
# 查看当前正在使用的数据库
SELECT DATABASE();
```

创建新的数据库：

```sql
CREATE DATABASE IF NOT EXISTS bilibili
DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci;
```

删除数据库：

```sql
# 删除数据库
DROP DATABASE bilibili;
DROP DATABASE IF EXIT bilibili;
```

修改数据库：

```sql
# 修改数据库的字符集和排序规则
ALTER DATABASE bilibili CHARACTER SET = utf8 COLLATE = utf8_unicode_ci;
```

### 数据表的操作

查看数据表

```sql
# 查看所有的数据表
SHOW TABLES;
# 查看某一个表结构
DESC user
```

创建数据表

```sql
CREATE TABLE IF NOT EXISTS `users`(
name VARCHAR(20),
age INT,
height DOUBLE
);
```

删除数据表

```sql
# 删除数据库
DROP TABLE users;
DROP TABLE IF EXISTS users;
```

修改表

```sql
# 1.修改表名
ALTER TABLE `moments` RENAME TO `moment`;
# 2.添加一个新的列
ALTER TABLE `moment` ADD `publishTime` DATETIME;
ALTER TABLE `moment` ADD `updateTime` DATETIME;
# 3.删除一列数据
ALTER TABLE `moment` DROP `updateTime`;
# 4.修改列的名称
ALTER TABLE `moment` CHANGE `publishTime` `publishDate` DATE;
# 5.修改列的数据类型
ALTER TABLE `moment` MODIFY `id` INT
```

插入数据

```sql
INSERT INTO `products` (`title`, `description`, `price`, `publishTime`) 
VALUES ('iPhone', 'iPhone12只要998', 998.88, '2020-10-10'); 
INSERT INTO `products` (`title`, `description`, `price`, `publishTime`) 
VALUES ('huawei', 'iPhoneP40只要888', 888.88, '2020-11-11');
```

删除数据

```sql
# 删除数据
# 会删除表中所有的数据
DELETE FROM `products`;
# 会删除符合条件的数据
DELETE FROM `products` WHERE `title` = 'iPhone';
```

修改数据

```sql
# 修改数据
# 会修改表中所有的数据
UPDATE `products` SET `title` = 'iPhone12', `price` = 1299.88;
# 会修改符合条件的数据
UPDATE `products` SET `title` = 'iPhone12', `price` = 1299.88 WHERE `title` = 'iPhone';
```

如果我们希望修改完数据后，直接可以显示最新的更新时间：

```sql
ALTER TABLE `products` ADD `updateTime` TIMESTAMP 
DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP;
```

### 数据查询

结合下面代码连接数据库操作

查询所有的数据并且显示所有的字段：

```sql
SELECT * FROM `products`;
```

查询指定字段

```sql
SELECT 字段1,字段2
SELECT title, brand, price FROM `products`;
```

我们也可以给字段起别名： 别名一般在多张表或者给客户端返回对应的key时会使用到

```sql
SELECT title as t, brand as b, price as p FROM `products`;
```

#### **条件查询**

条件查询会使用 WEHRE查询子句

**WHERE的比较运算符**

```sql
# 查询价格小于1000的手机
SELECT * FROM `products` WHERE price < 1000;
# 查询价格大于等于2000的手机
SELECT * FROM `products` WHERE price >= 2000;
# 价格等于3399的手机
SELECT * FROM `products` WHERE price = 3399;
# 价格不等于3399的手机
SELECT * FROM `products` WHERE price != 3399;
# 查询华为品牌的手机
SELECT * FROM `products` WHERE `brand` = '华为';
```

**WHERE的逻辑运算符**

```sql
# 查询品牌是华为，并且小于2000元的手机
SELECT * FROM `products` WHERE `brand` = '华为' and `price` < 2000;
SELECT * FROM `products` WHERE `brand` = '华为' && `price` < 2000;
# 查询1000到2000的手机（不包含1000和2000）
SELECT * FROM `products` WHERE price > 1000 and price < 2000;
# OR: 符合一个条件即可
# 查询所有的华为手机或者价格小于1000的手机
SELECT * FROM `products` WHERE brand = '华为' or price < 1000;
# 查询1000到2000的手机（包含1000和2000）
SELECT * FROM `products` WHERE price BETWEEN 1000 and 2000;
# 查看多个结果中的一个
SELECT * FROM `products` WHERE brand in ('华为', '小米')
```

**模糊查询**使用LIKE关键字，结合两个特殊的符号：

%表示匹配任意个的任意字符；

 _表示匹配一个的任意字符

```sql
# 查询所有以v开头的title
SELECT * FROM `products` WHERE title LIKE 'v%';
# 查询带M的title
SELECT * FROM `products` WHERE title LIKE '%M%';
# 查询带M的title必须是第三个字符
SELECT * FROM `products` WHERE title LIKE '__M%';
```

#### 查询结果排序

当我们查询到结果的时候，我们希望讲结果按照某种方式进行排序，这个时候使用的是ORDER BY

ORDER BY有两个常用的值：

ASC：升序排列；

DESC：降序排列；

```sql
SELECT * FROM `products` WHERE brand = '华为' or price < 1000 ORDER BY price ASC;
```

#### 分页查询

当数据库中的数据非常多时，一次性查询到所有的结果进行显示是不太现实的：

在真实开发中，我们都会要求用户传入offset、limit或者page等字段；

它们的目的是让我们可以在数据库中进行分页查询；

它的用法有[LIMIT {[offset,] row_count | row_count OFFSET offset}]

```sql
SELECT * FROM `products` LIMIT 30 OFFSET 0;
SELECT * FROM `products` LIMIT 30 OFFSET 30;
SELECT * FROM `products` LIMIT 30 OFFSET 60;
# 另外一种写法：offset, row_count
SELECT * FROM `products` LIMIT 90, 30
```



### 代码连接数据库

创建一个mysql文件夹，```npm init -y```,然后```npm install mysql2```

创建一张新的表

```sql
CREATE TABLE IF NOT EXISTS `products` (
id INT PRIMARY KEY AUTO_INCREMENT,
brand VARCHAR(20),
title VARCHAR(100) NOT NULL,
price DOUBLE NOT NULL,
score DECIMAL(2,1),
voteCnt INT,
url VARCHAR(100),
pid INT
);
```



创建一个```phone.json```文件，数据如下

```json
[
  {
    "brand": "华为",
    "title": "华为nova 3（全网通） ",
    "price": 2699,
    "score": 6.7,
    "voteCnt": 65,
    "url": "http://detail.zol.com.cn/cell_phone/index1185512.shtml",
    "pid": "1185512"
  },
  {
    "brand": "华为",
    "title": "华为P20 Pro（6GB RAM/全网通） ",
    "price": 4488,
    "score": 8.3,
    "voteCnt": 103,
    "url": "http://detail.zol.com.cn/cell_phone/index1207038.shtml",
    "pid": "1207038"
  },
  {
    "brand": "华为",
    "title": "华为P20（全网通） ",
    "price": 3388,
    "score": 8.4,
    "voteCnt": 127,
    "url": "http://detail.zol.com.cn/cell_phone/index1175779.shtml",
    "pid": "1175779"
  },
  {
    "brand": "华为",
    "title": "华为nova 3i（4GB RAM/全网通） ",
    "price": 1999,
    "score": 7,
    "voteCnt": 9,
    "url": "http://detail.zol.com.cn/cell_phone/index1222100.shtml",
    "pid": "1222100"
  },
  {
    "brand": "华为",
    "title": "华为Mate 10（4GB RAM/全网通） ",
    "price": 3399,
    "score": 8.3,
    "voteCnt": 125,
    "url": "http://detail.zol.com.cn/cell_phone/index1165672.shtml",
    "pid": "1165672"
  },
  {
    "brand": "华为",
    "title": "华为nova 3e（全网通） ",
    "price": 1999,
    "score": 8.8,
    "voteCnt": 71,
    "url": "http://detail.zol.com.cn/cell_phone/index1207608.shtml",
    "pid": "1207608"
  },
  {
    "brand": "华为",
    "title": "华为nova 2s（4GB RAM/全网通） ",
    "price": 2399,
    "score": 7.5,
    "voteCnt": 97,
    "url": "http://detail.zol.com.cn/cell_phone/index1204363.shtml",
    "pid": "1204363"
  },
  {
    "brand": "华为",
    "title": "华为Mate 10 Pro（全网通） ",
    "price": 3599,
    "score": 8.7,
    "voteCnt": 92,
    "url": "http://detail.zol.com.cn/cell_phone/index1181128.shtml",
    "pid": "1181128"
  },
  {
    "brand": "华为",
    "title": "华为畅享8（3GB RAM/全网通） ",
    "price": 1099,
    "score": 5.3,
    "voteCnt": 28,
    "url": "http://detail.zol.com.cn/cell_phone/index1208286.shtml",
    "pid": "1208286"
  },
  {
    "brand": "华为",
    "title": "华为P10（VTR-AL00/全网通） ",
    "price": 3488,
    "score": 7.2,
    "voteCnt": 395,
    "url": "http://detail.zol.com.cn/cell_phone/index1160028.shtml",
    "pid": "1160028"
  },
  {
    "brand": "华为",
    "title": "华为畅享8 Plus（全网通） ",
    "price": 1499,
    "score": 5.8,
    "voteCnt": 11,
    "url": "http://detail.zol.com.cn/cell_phone/index1210102.shtml",
    "pid": "1210102"
  },
  {
    "brand": "华为",
    "title": "华为麦芒7（全网通） ",
    "price": 2399,
    "score": 7.6,
    "voteCnt": 5,
    "url": "http://detail.zol.com.cn/cell_phone/index1227167.shtml",
    "pid": "1227167"
  },
  {
    "brand": "华为",
    "title": "华为Mate 9（MHA-AL00/4GB RAM/全网通） ",
    "price": 1788,
    "score": 7.8,
    "voteCnt": 449,
    "url": "http://detail.zol.com.cn/cell_phone/index1143413.shtml",
    "pid": "1143413"
  },
  {
    "brand": "华为",
    "title": "华为nova 3i（6GB RAM/全网通） ",
    "price": 2199,
    "score": 7,
    "voteCnt": 9,
    "url": "http://detail.zol.com.cn/cell_phone/index1224424.shtml",
    "pid": "1224424"
  },
  {
    "brand": "华为",
    "title": "华为Mate RS保时捷版（全网通） ",
    "price": 9999,
    "score": 6.1,
    "voteCnt": 16,
    "url": "http://detail.zol.com.cn/cell_phone/index1210089.shtml",
    "pid": "1210089"
  },
  {
    "brand": "华为",
    "title": "华为nova 2（PIC-AL00/全网通） ",
    "price": 1228,
    "score": 8,
    "voteCnt": 209,
    "url": "http://detail.zol.com.cn/cell_phone/index1170042.shtml",
    "pid": "1170042"
  },
  {
    "brand": "华为",
    "title": "华为麦芒6（全网通） ",
    "price": 2199,
    "score": 6.1,
    "voteCnt": 57,
    "url": "http://detail.zol.com.cn/cell_phone/index1182274.shtml",
    "pid": "1182274"
  },
  {
    "brand": "华为",
    "title": "华为P9（EVA-AL00/标准版/全网通） ",
    "price": 1448,
    "score": 7.8,
    "voteCnt": 648,
    "url": "http://detail.zol.com.cn/cell_phone/index404275.shtml",
    "pid": "404275"
  },
  {
    "brand": "华为",
    "title": "华为nova（CAZ-AL10/高配版/全网通） ",
    "price": 988,
    "score": 6.9,
    "voteCnt": 198,
    "url": "http://detail.zol.com.cn/cell_phone/index1154505.shtml",
    "pid": "1154505"
  },
  {
    "brand": "华为",
    "title": "华为畅享8e（全网通） ",
    "price": 999,
    "score": 4.8,
    "voteCnt": 4,
    "url": "http://detail.zol.com.cn/cell_phone/index1210103.shtml",
    "pid": "1210103"
  },
  {
    "brand": "华为",
    "title": "华为麦芒5（MLA-AL10/高配版/全网通） ",
    "price": 1099,
    "score": 6.8,
    "voteCnt": 136,
    "url": "http://detail.zol.com.cn/cell_phone/index1148829.shtml",
    "pid": "1148829"
  },
  {
    "brand": "华为",
    "title": "华为P10 Plus（VKY-AL00/6GB RAM全网通） ",
    "price": 2488,
    "score": 7.5,
    "voteCnt": 186,
    "url": "http://detail.zol.com.cn/cell_phone/index1163813.shtml",
    "pid": "1163813"
  },
  {
    "brand": "华为",
    "title": "华为Mate 9 Pro（4GB RAM/全网通） ",
    "price": 2799,
    "score": 8,
    "voteCnt": 136,
    "url": "http://detail.zol.com.cn/cell_phone/index1159578.shtml",
    "pid": "1159578"
  },  {
    "brand": "vivo",
    "title": "vivo X7 Plus（全网通） ",
    "price": 2350,
    "score": 8.2,
    "voteCnt": 484,
    "url": "http://detail.zol.com.cn/cell_phone/index1147812.shtml",
    "pid": "1147812"
  },
  {
    "brand": "vivo",
    "title": "vivo X9s Plus（全网通） ",
    "price": 2498,
    "score": 7.4,
    "voteCnt": 523,
    "url": "http://detail.zol.com.cn/cell_phone/index1170837.shtml",
    "pid": "1170837"
  },
  {
    "brand": "vivo",
    "title": "vivo Y51A（高配版/全网通） ",
    "price": 998,
    "score": 6.6,
    "voteCnt": 306,
    "url": "http://detail.zol.com.cn/cell_phone/index1115625.shtml",
    "pid": "1115625"
  },
  {
    "brand": "vivo",
    "title": "vivo X7（全网通） ",
    "price": 1799,
    "score": 7.7,
    "voteCnt": 736,
    "url": "http://detail.zol.com.cn/cell_phone/index1145877.shtml",
    "pid": "1145877"
  },
  {
    "brand": "vivo",
    "title": "vivo X9s（全网通） ",
    "price": 1998,
    "score": 8.9,
    "voteCnt": 563,
    "url": "http://detail.zol.com.cn/cell_phone/index1174429.shtml",
    "pid": "1174429"
  },
  {
    "brand": "vivo",
    "title": "vivo Y66i（全网通） ",
    "price": 1198,
    "score": 6.3,
    "voteCnt": 161,
    "url": "http://detail.zol.com.cn/cell_phone/index1204388.shtml",
    "pid": "1204388"
  },
  {
    "brand": "vivo",
    "title": "vivo X9s  L（移动全网通） ",
    "price": 1998,
    "score": 8.9,
    "voteCnt": 563,
    "url": "http://detail.zol.com.cn/cell_phone/index1175257.shtml",
    "pid": "1175257"
  },
  {
    "brand": "vivo",
    "title": "vivo X9L（移动全网通）  ",
    "price": 1998,
    "score": 8.5,
    "voteCnt": 1362,
    "url": "http://detail.zol.com.cn/cell_phone/index1170124.shtml",
    "pid": "1170124"
  },
  {
    "brand": "vivo",
    "title": "vivo X20Plus屏幕指纹版（全网通） ",
    "price": 3598,
    "score": 6.2,
    "voteCnt": 17,
    "url": "http://detail.zol.com.cn/cell_phone/index1205808.shtml",
    "pid": "1205808"
  },
  {
    "brand": "vivo",
    "title": "vivo Y75（4GB RAM/全网通） ",
    "price": 1098,
    "score": 7.5,
    "voteCnt": 27,
    "url": "http://detail.zol.com.cn/cell_phone/index1208237.shtml",
    "pid": "1208237"
  },
  {
    "brand": "vivo",
    "title": "vivo X20（旗舰版/全网通） ",
    "price": 2598,
    "score": 9.1,
    "voteCnt": 1075,
    "url": "http://detail.zol.com.cn/cell_phone/index1184293.shtml",
    "pid": "1184293"
  },
  {
    "brand": "vivo",
    "title": "vivo Y55（全网通） ",
    "price": 999,
    "score": 6.4,
    "voteCnt": 126,
    "url": "http://detail.zol.com.cn/cell_phone/index1156093.shtml",
    "pid": "1156093"
  },
  {
    "brand": "vivo",
    "title": "vivo Y75（3GB RAM/全网通） ",
    "price": 1298,
    "score": 7.5,
    "voteCnt": 27,
    "url": "http://detail.zol.com.cn/cell_phone/index1185212.shtml",
    "pid": "1185212"
  },
  {
    "brand": "vivo",
    "title": "vivo Xplay6（全网通） ",
    "price": 3498,
    "score": 8.7,
    "voteCnt": 691,
    "url": "http://detail.zol.com.cn/cell_phone/index1159623.shtml",
    "pid": "1159623"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R17（8GB RAM/全网通） ",
    "price": 3499,
    "score": 9.5,
    "voteCnt": 173,
    "url": "http://detail.zol.com.cn/cell_phone/index1225806.shtml",
    "pid": "1225806"
  },
  {
    "brand": "OPPO",
    "title": "OPPO Find X（标准版/全网通） ",
    "price": 4999,
    "score": 9.5,
    "voteCnt": 774,
    "url": "http://detail.zol.com.cn/cell_phone/index1213467.shtml",
    "pid": "1213467"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R15（6GB RAM/全网通） ",
    "price": 2699,
    "score": 9.2,
    "voteCnt": 1055,
    "url": "http://detail.zol.com.cn/cell_phone/index1206990.shtml",
    "pid": "1206990"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A3（全网通） ",
    "price": 1799,
    "score": 8.9,
    "voteCnt": 366,
    "url": "http://detail.zol.com.cn/cell_phone/index1211599.shtml",
    "pid": "1211599"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A5（全网通） ",
    "price": 1500,
    "score": 8.7,
    "voteCnt": 357,
    "url": "http://detail.zol.com.cn/cell_phone/index1221126.shtml",
    "pid": "1221126"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R11（标准版/全网通） ",
    "price": 1553,
    "score": 9.1,
    "voteCnt": 1346,
    "url": "http://detail.zol.com.cn/cell_phone/index1150077.shtml",
    "pid": "1150077"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A1（3GB RAM/全网通） ",
    "price": 1000,
    "score": 7.4,
    "voteCnt": 86,
    "url": "http://detail.zol.com.cn/cell_phone/index1209829.shtml",
    "pid": "1209829"
  },
  {
    "brand": "OPPO",
    "title": "OPPO Find X兰博基尼版（全网通） ",
    "price": 9999,
    "score": 9.7,
    "voteCnt": 89,
    "url": "http://detail.zol.com.cn/cell_phone/index1220645.shtml",
    "pid": "1220645"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R17 Pro（全网通） ",
    "price": 4299,
    "score": 9.4,
    "voteCnt": 91,
    "url": "http://detail.zol.com.cn/cell_phone/index1225826.shtml",
    "pid": "1225826"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A7x（全网通） ",
    "price": 1999,
    "score": 8.7,
    "voteCnt": 48,
    "url": "http://detail.zol.com.cn/cell_phone/index1230724.shtml",
    "pid": "1230724"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R11s（4GB RAM/全网通） ",
    "price": 2299,
    "score": 9.2,
    "voteCnt": 1310,
    "url": "http://detail.zol.com.cn/cell_phone/index1184068.shtml",
    "pid": "1184068"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A83 (全网通) ",
    "price": 1199,
    "score": 5.8,
    "voteCnt": 38,
    "url": "http://detail.zol.com.cn/cell_phone/index1205003.shtml",
    "pid": "1205003"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A57（全网通） ",
    "price": 799,
    "score": 7.6,
    "voteCnt": 577,
    "url": "http://detail.zol.com.cn/cell_phone/index1160598.shtml",
    "pid": "1160598"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A73（全网通） ",
    "price": 1499,
    "score": 8.4,
    "voteCnt": 380,
    "url": "http://detail.zol.com.cn/cell_phone/index1205054.shtml",
    "pid": "1205054"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R17（雾光渐变色/8GB RAM/全网通） ",
    "price": 3599,
    "score": 9.5,
    "voteCnt": 171,
    "url": "http://detail.zol.com.cn/cell_phone/index1229193.shtml",
    "pid": "1229193"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R11s Plus（全网通） ",
    "price": 1899,
    "score": 9,
    "voteCnt": 669,
    "url": "http://detail.zol.com.cn/cell_phone/index1184231.shtml",
    "pid": "1184231"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R15梦镜版（梦境红/全网通） ",
    "price": 2999,
    "score": 9.2,
    "voteCnt": 1032,
    "url": "http://detail.zol.com.cn/cell_phone/index1208720.shtml",
    "pid": "1208720"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R17（6GB RAM/全网通） ",
    "price": 3199,
    "score": 9.5,
    "voteCnt": 171,
    "url": "http://detail.zol.com.cn/cell_phone/index1229159.shtml",
    "pid": "1229159"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R11 Plus（全网通） ",
    "price": 1788,
    "score": 9.2,
    "voteCnt": 546,
    "url": "http://detail.zol.com.cn/cell_phone/index1170222.shtml",
    "pid": "1170222"
  },
  {
    "brand": "OPPO",
    "title": "OPPO R15梦镜版（陶瓷黑/梦境紫/全网通） ",
    "price": 3299,
    "score": 9.2,
    "voteCnt": 1032,
    "url": "http://detail.zol.com.cn/cell_phone/index1210656.shtml",
    "pid": "1210656"
  },
  {
    "brand": "OPPO",
    "title": "OPPO A79（全网通） ",
    "price": 1699,
    "score": 8.7,
    "voteCnt": 339,
    "url": "http://detail.zol.com.cn/cell_phone/index1203640.shtml",
    "pid": "1203640"
  },
  {
    "brand": "小米",
    "title": "小米8（6GB RAM/全网通） ",
    "price": 2599,
    "score": 5.1,
    "voteCnt": 308,
    "url": "http://detail.zol.com.cn/cell_phone/index1213787.shtml",
    "pid": "1213787"
  },
  {
    "brand": "小米",
    "title": "小米6X（4GB RAM/全网通） ",
    "price": 1349,
    "score": 5.3,
    "voteCnt": 106,
    "url": "http://detail.zol.com.cn/cell_phone/index1170480.shtml",
    "pid": "1170480"
  },
  {
    "brand": "小米",
    "title": "小米8 SE（4GB RAM/全网通） ",
    "price": 1699,
    "score": 5.3,
    "voteCnt": 76,
    "url": "http://detail.zol.com.cn/cell_phone/index1217453.shtml",
    "pid": "1217453"
  },
  {
    "brand": "小米",
    "title": "小米8青春版（4GB RAM/全网通） ",
    "price": 1399,
    "score": 6,
    "voteCnt": 18,
    "url": "http://detail.zol.com.cn/cell_phone/index1231048.shtml",
    "pid": "1231048"
  },
  {
    "brand": "小米",
    "title": "小米红米Note 5（3GB RAM/全网通） ",
    "price": 999,
    "score": 5.5,
    "voteCnt": 98,
    "url": "http://detail.zol.com.cn/cell_phone/index1175353.shtml",
    "pid": "1175353"
  },
  {
    "brand": "小米",
    "title": "小米MIX 2s（6GB RAM/全网通） ",
    "price": 2999,
    "score": 5.6,
    "voteCnt": 134,
    "url": "http://detail.zol.com.cn/cell_phone/index1202983.shtml",
    "pid": "1202983"
  },
  {
    "brand": "小米",
    "title": "小米6（6GB RAM/全网通） ",
    "price": 2409,
    "score": 6.2,
    "voteCnt": 526,
    "url": "http://detail.zol.com.cn/cell_phone/index1161066.shtml",
    "pid": "1161066"
  },
  {
    "brand": "小米",
    "title": "小米红米6 Pro（3GB RAM/全网通） ",
    "price": 969,
    "score": 6.1,
    "voteCnt": 21,
    "url": "http://detail.zol.com.cn/cell_phone/index1220665.shtml",
    "pid": "1220665"
  },
  {
    "brand": "小米",
    "title": "小米8透明探索版（全网通） ",
    "price": 3699,
    "score": 5.4,
    "voteCnt": 48,
    "url": "http://detail.zol.com.cn/cell_phone/index1216973.shtml",
    "pid": "1216973"
  },
  {
    "brand": "小米",
    "title": "小米Max 3（4GB RAM/全网通） ",
    "price": 1699,
    "score": 5.1,
    "voteCnt": 66,
    "url": "http://detail.zol.com.cn/cell_phone/index1205304.shtml",
    "pid": "1205304"
  },
  {
    "brand": "小米",
    "title": "小米MIX 2（全网通） ",
    "price": 2299,
    "score": 5.4,
    "voteCnt": 147,
    "url": "http://detail.zol.com.cn/cell_phone/index1160797.shtml",
    "pid": "1160797"
  },
  {
    "brand": "小米",
    "title": "小米Max 2（全网通） ",
    "price": 939,
    "score": 6.2,
    "voteCnt": 119,
    "url": "http://detail.zol.com.cn/cell_phone/index1165765.shtml",
    "pid": "1165765"
  },
  {
    "brand": "小米",
    "title": "小米红米6（3GB RAM/全网通） ",
    "price": 769,
    "score": 5.4,
    "voteCnt": 11,
    "url": "http://detail.zol.com.cn/cell_phone/index1215069.shtml",
    "pid": "1215069"
  },
  {
    "brand": "小米",
    "title": "小米红米5 Plus（3GB RAM/全网通） ",
    "price": 800,
    "score": 5.8,
    "voteCnt": 75,
    "url": "http://detail.zol.com.cn/cell_phone/index1183689.shtml",
    "pid": "1183689"
  },
  {
    "brand": "小米",
    "title": "小米红米Note 5（4GB RAM/全网通） ",
    "price": 1299,
    "score": 5.5,
    "voteCnt": 98,
    "url": "http://detail.zol.com.cn/cell_phone/index1209455.shtml",
    "pid": "1209455"
  },
  {
    "brand": "小米",
    "title": "小米红米Note 4X（3GB RAM/全网通） ",
    "price": 999,
    "score": 5.7,
    "voteCnt": 285,
    "url": "http://detail.zol.com.cn/cell_phone/index1163122.shtml",
    "pid": "1163122"
  },
  {
    "brand": "小米",
    "title": "小米Note 3（6GB RAM/全网通） ",
    "price": 1849,
    "score": 5.8,
    "voteCnt": 92,
    "url": "http://detail.zol.com.cn/cell_phone/index1164780.shtml",
    "pid": "1164780"
  },
  {
    "brand": "小米",
    "title": "小米5X（全网通） ",
    "price": 1129,
    "score": 5.8,
    "voteCnt": 98,
    "url": "http://detail.zol.com.cn/cell_phone/index1175015.shtml",
    "pid": "1175015"
  },
  {
    "brand": "小米",
    "title": "小米红米6A（2GB RAM/全网通） ",
    "price": 549,
    "score": 6.1,
    "voteCnt": 3,
    "url": "http://detail.zol.com.cn/cell_phone/index1216196.shtml",
    "pid": "1216196"
  },
  {
    "brand": "小米",
    "title": "小米6X（6GB RAM/全网通） ",
    "price": 1709,
    "score": 5.3,
    "voteCnt": 106,
    "url": "http://detail.zol.com.cn/cell_phone/index1212271.shtml",
    "pid": "1212271"
  },
  {
    "brand": "小米",
    "title": "小米MIX（全网通） ",
    "price": 2900,
    "score": 5.3,
    "voteCnt": 173,
    "url": "http://detail.zol.com.cn/cell_phone/index1158428.shtml",
    "pid": "1158428"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone XS（全网通） ",
    "price": 8699,
    "score": 5.5,
    "voteCnt": 51,
    "url": "http://detail.zol.com.cn/cell_phone/index1229519.shtml",
    "pid": "1229519"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone X（全网通） ",
    "price": 6898,
    "score": 8,
    "voteCnt": 193,
    "url": "http://detail.zol.com.cn/cell_phone/index1182639.shtml",
    "pid": "1182639"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone XR（全网通） ",
    "price": 6499,
    "score": 4.6,
    "voteCnt": 35,
    "url": "http://detail.zol.com.cn/cell_phone/index1205394.shtml",
    "pid": "1205394"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 8 Plus（全网通） ",
    "price": 5468,
    "score": 8.5,
    "voteCnt": 84,
    "url": "http://detail.zol.com.cn/cell_phone/index1182632.shtml",
    "pid": "1182632"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone XS Max（全网通） ",
    "price": 9599,
    "score": 5.8,
    "voteCnt": 30,
    "url": "http://detail.zol.com.cn/cell_phone/index1229520.shtml",
    "pid": "1229520"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 8（全网通） ",
    "price": 4528,
    "score": 6.8,
    "voteCnt": 254,
    "url": "http://detail.zol.com.cn/cell_phone/index394162.shtml",
    "pid": "394162"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 7（全网通） ",
    "price": 3628,
    "score": 8,
    "voteCnt": 475,
    "url": "http://detail.zol.com.cn/cell_phone/index384973.shtml",
    "pid": "384973"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 7 Plus（全网通） ",
    "price": 4499,
    "score": 8.1,
    "voteCnt": 335,
    "url": "http://detail.zol.com.cn/cell_phone/index1104332.shtml",
    "pid": "1104332"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 6S Plus（全网通） ",
    "price": 3000,
    "score": 8,
    "voteCnt": 279,
    "url": "http://detail.zol.com.cn/cell_phone/index398690.shtml",
    "pid": "398690"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 5S（双4G） ",
    "price": 1199,
    "score": 8.2,
    "voteCnt": 2964,
    "url": "http://detail.zol.com.cn/cell_phone/index340414.shtml",
    "pid": "340414"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 8 Plus（国际版/全网通） ",
    "price": 5188,
    "score": 8.5,
    "voteCnt": 84,
    "url": "http://detail.zol.com.cn/cell_phone/index1204817.shtml",
    "pid": "1204817"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 7 Plus（双4G） ",
    "price": 4388,
    "score": 8.1,
    "voteCnt": 335,
    "url": "http://detail.zol.com.cn/cell_phone/index1177080.shtml",
    "pid": "1177080"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 8（国际版/全网通） ",
    "price": 4688,
    "score": 6.8,
    "voteCnt": 254,
    "url": "http://detail.zol.com.cn/cell_phone/index1204816.shtml",
    "pid": "1204816"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone X（国际版/全网通） ",
    "price": 6888,
    "score": 8,
    "voteCnt": 191,
    "url": "http://detail.zol.com.cn/cell_phone/index1204818.shtml",
    "pid": "1204818"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 7 Plus（国际版/全网通） ",
    "price": 4749,
    "score": 8.1,
    "voteCnt": 335,
    "url": "http://detail.zol.com.cn/cell_phone/index1155434.shtml",
    "pid": "1155434"
  },
  {
    "brand": "苹果",
    "title": "苹果iPhone 6S（国际版/双4G） ",
    "price": 2320,
    "score": 7.3,
    "voteCnt": 551,
    "url": "http://detail.zol.com.cn/cell_phone/index1100448.shtml",
    "pid": "1100448"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro 2S（4GB RAM/全网通） ",
    "price": 1798,
    "score": 6.3,
    "voteCnt": 22,
    "url": "http://detail.zol.com.cn/cell_phone/index1227474.shtml",
    "pid": "1227474"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果R1（6GB RAM/全网通） ",
    "price": 3499,
    "score": 5.1,
    "voteCnt": 64,
    "url": "http://detail.zol.com.cn/cell_phone/index1162957.shtml",
    "pid": "1162957"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro 2（4GB RAM/全网通） ",
    "price": 1399,
    "score": 7.4,
    "voteCnt": 85,
    "url": "http://detail.zol.com.cn/cell_phone/index1202624.shtml",
    "pid": "1202624"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果3（全网通） ",
    "price": 1099,
    "score": 5.5,
    "voteCnt": 42,
    "url": "http://detail.zol.com.cn/cell_phone/index1209757.shtml",
    "pid": "1209757"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro 2S（6GB RAM/全网通） ",
    "price": 1998,
    "score": 6.3,
    "voteCnt": 22,
    "url": "http://detail.zol.com.cn/cell_phone/index1228692.shtml",
    "pid": "1228692"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro（64GB ROM/全网通） ",
    "price": 1179,
    "score": 7.3,
    "voteCnt": 188,
    "url": "http://detail.zol.com.cn/cell_phone/index1166591.shtml",
    "pid": "1166591"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果R1（8GB RAM/全网通） ",
    "price": 4499,
    "score": 5.1,
    "voteCnt": 64,
    "url": "http://detail.zol.com.cn/cell_phone/index1214020.shtml",
    "pid": "1214020"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro 2特别版（全网通） ",
    "price": 1449,
    "score": 7.4,
    "voteCnt": 85,
    "url": "http://detail.zol.com.cn/cell_phone/index1213907.shtml",
    "pid": "1213907"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro（128GB ROM/全网通） ",
    "price": 1499,
    "score": 7.3,
    "voteCnt": 188,
    "url": "http://detail.zol.com.cn/cell_phone/index1170719.shtml",
    "pid": "1170719"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro 2（6GB RAM/全网通） ",
    "price": 1949,
    "score": 7.4,
    "voteCnt": 85,
    "url": "http://detail.zol.com.cn/cell_phone/index1202737.shtml",
    "pid": "1202737"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技M1（全网通） ",
    "price": 1800,
    "score": 8,
    "voteCnt": 148,
    "url": "http://detail.zol.com.cn/cell_phone/index1138532.shtml",
    "pid": "1138532"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技M1L（高配版/全网通） ",
    "price": 2399,
    "score": 8,
    "voteCnt": 148,
    "url": "http://detail.zol.com.cn/cell_phone/index1157726.shtml",
    "pid": "1157726"
  },
  {
    "brand": "锤子科技",
    "title": "锤子科技坚果Pro（32GB ROM/全网通） ",
    "price": 1099,
    "score": 7.3,
    "voteCnt": 188,
    "url": "http://detail.zol.com.cn/cell_phone/index1170718.shtml",
    "pid": "1170718"
  }
]
```

创建一个index.js文件,如下

```js
const mysql = require('mysql2');
 
const connection = mysql.createConnection({
  host: 'localhost',
  port: 3306,
  user: 'root',
  password: 'Dengjunyu123.',
  database: 'bilibili'  //数据库名称
});

const statement = `INSERT INTO products SET ?;` //表名称，插到哪个表中
const phoneJson = require('./phone.json');

for (let phone of phoneJson) {
  connection.query(statement, phone);
}

```

然后执行```node index.js```，去刷新数据库中对应的表就可以看到数据添加成功

### 聚合函数

聚合函数表示对 值的集合 进行操作的 组（集合）函数。

```sql
# 华为手机价格的平均值
SELECT AVG(price) FROM `products` WHERE brand = '华为';
# 计算所有手机的平均分
SELECT AVG(score) FROM `products`;
# 手机中最低和最高分数
SELECT MAX(score) FROM `products`;
SELECT MIN(score) FROM `products`;
# 计算总投票人数
SELECT SUM(voteCnt) FROM `products`;
# 计算所有条目的数量
SELECT COUNT(*) FROM `products`;
# 华为手机的个数
SELECT COUNT(*) FROM `products` WHERE brand = '华为';
```

### Group By

#### 认识Group By

**事实上聚合函数相当于默认将所有的数据分成了一组：**

我们前面使用avg还是max等，都是将所有的结果看成一组来计算的；

那么如果我们希望划分多个组：比如华为、苹果、小米等手机分别的平均价格，应该怎么来做呢？

这个时候我们可以使用 GROUP BY；

**GROUP BY通常和聚合函数一起使用：**

表示我们先对数据进行分组，再对每一组数据，进行聚合函数的计算；

**我们现在来提一个需求：**

根据品牌进行分组；

计算各个品牌中：商品的个数、平均价格；

也包括：最高价格、最低价格、平均评分；

```sql
SELECT brand, 
COUNT(*) as count, 
ROUND(AVG(price),2) as avgPrice,
MAX(price) as maxPrice,
MIN(price) as minPrice,
AVG(score) as avgScore
FROM `products` GROUP BY brand;
```

#### Group By的约束条件

如果我们希望给Group By查询到的结果添加一些约束，那么我们可以使用：```HAVING```。

比如：如果我们还希望筛选出平均价格在4000以下，并且平均分在7以上的品牌：

```sql
SELECT brand, 
COUNT(*) as count, 
ROUND(AVG(price),2) as avgPrice,
MAX(price) as maxPrice,
MIN(price) as minPrice,
AVG(score) as avgScore
FROM `products` GROUP BY brand 
HAVING avgPrice < 4000 and avgScore > 7;
```

### 创建多张表

假如我们的上面的商品表中，对应的品牌还需要包含其他的信息：

比如品牌的官网，品牌的世界排名，品牌的市值等等；

如果我们直接在商品中去体现品牌相关的信息，会存在一些问题：

一方面，products表中应该表示的都是商品相关的数据，应该又另外一张表来表示brand的数据；

另一方面，多个商品使用的品牌是一致时，会存在大量的冗余数据；

所以，我们可以将所有的品牌数据，单独放到一张表中，创建一张品牌的表

```sql
CREATE TABLE IF NOT EXISTS `brand`(
id INT PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(20) NOT NULL,
website VARCHAR(100),
worldRank INT
);
```

插入模拟数据

```sql
INSERT INTO `brand` (name, website, worldRank) VALUES ('华为', 'www.huawei.com', 1);
INSERT INTO `brand` (name, website, worldRank) VALUES ('小米', 'www.mi.com', 10);
INSERT INTO `brand` (name, website, worldRank) VALUES ('苹果', 'www.apple.com', 5);
INSERT INTO `brand` (name, website, worldRank) VALUES ('oppo', 'www.oppo.com', 15);
INSERT INTO `brand` (name, website, worldRank) VALUES ('京东', 'www.jd.com', 3);
INSERT INTO `brand` (name, website, worldRank) VALUES ('Google', 'www.google.com', 8);
```

#### 创建外键

将两张表联系起来，我们可以将products中的brand_id关联到brand中的id：

如果是创建表添加外键约束，我们需要在创建表的()最后添加如下语句；

```sql
FOREIGN KEY (brand_id) REFERENCES brand(id)
```

如果是表已经创建好，额外添加外键：

```sql
ALTER TABLE `products` ADD `brand_id` INT;
ALTER TABLE `products` ADD FOREIGN KEY (brand_id) REFERENCES brand(id);
```

现在我们可以将products中的brand_id关联到brand中的id的值：

```sql
UPDATE `products` SET `brand_id` = 1 WHERE `brand` = '华为';
UPDATE `products` SET `brand_id` = 4 WHERE `brand` = 'OPPO';
UPDATE `products` SET `brand_id` = 3 WHERE `brand` = '苹果';
UPDATE `products` SET `brand_id` = 2 WHERE `brand` = '小米';
```

#### 外键存在时更新和删除数据

先找到外键名

```sql
SHOW CREATE TABLE `products`;
```

删除外键

```sql
ALTER TABLE `products` DROP FOREIGN KEY products_ibfk_1; //外键名products_ibfk_1
```

重新设置

```sql
ALTER TABLE `products` ADD FOREIGN KEY (brand_id) REFERENCES brand(id) 
ON UPDATE CASCADE 
ON DELETE CASCADE;
```

**CASCADE**：当更新或删除某个记录时，会检查该记录是否有关联的外键记录，有的话： 

✓ 更新：那么会更新对应的记录； ✓ 删除：那么关联的记录会被一起删除掉；

### 多表查询

我们希望查询到产品的同时，显示对应的品牌相关的信息，因为数据是存放在两张表中，所以这个时候就需要进行多表查询。

如果我们直接通过查询语句希望在多张表中查询到数据，这个时候是什么效果呢？

```sql
SELECT * FROM `products`, `brand`;//两张表会合在一起，事实上很多的数据是没有意义的
```

使用where来进行筛选

```sql
SELECT * FROM `products`, `brand` WHERE `products`.brand_id = `brand`.id;
```

事实上我们想要的效果并不是这样的，而且表中的某些特定的数据，这个时候我们可以使用 SQL JOIN 操作：

也就是下面的多表连接

#### 多表连接
![1](/24.png)

**左连接**

如果我们希望获取到的是左边所有的数据（以左表为主）：

这个时候就表示无论左边的表是否有对应的brand_id的值对应右边表的id，左边的数据都会被查询出来；

这个也是开发中使用最多的情况，它的完整写法是LEFT [OUTER] JOIN，但是OUTER可以省略的；

```sql
SELECT * FROM `products` LEFT JOIN `brand` ON `products`.brand_id = `brand`.id;
SELECT * FROM `products` LEFT JOIN `brand` ON `products`.brand_id = `brand`.id
WHERE brand.id IS NULL
```

**右连接**

```sql
SELECT * FROM `products` RIGHT JOIN `brand` ON `products`.brand_id = `brand`.id;
SELECT * FROM `products` RIGHT JOIN `brand` ON `products`.brand_id = `brand`.id
WHERE products.id IS NULL;
```

**内连接**

事实上内连接是表示左边的表和右边的表都有对应的数据关联：

 内连接在开发中偶尔也会有一些场景使用，看自己的场景。

内连接有其他的写法：CROSS JOIN或者 JOIN都可以；

```sql
SELECT * FROM `products` INNER JOIN `brand` ON `products`.brand_id = `brand`.id
```

**全连接**

```sql
(SELECT * FROM `products` LEFT JOIN `brand` ON `products`.brand_id = `brand`.id)
UNION
(SELECT * FROM `products` RIGHT JOIN `brand` ON `products`.brand_id = `brand`.id);
```

#### 多对多关系数据准备

在开发中我们还会遇到多对多的关系：

比如学生可以选择多门课程，一个课程可以被多个学生选择；

 这种情况我们应该在开发中如何处理呢？

我们先建立好两张表

```sql
# 创建学生表
CREATE TABLE IF NOT EXISTS `students`(
id INT PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(20) NOT NULL,
age INT
);
# 创建课程表
CREATE TABLE IF NOT EXISTS `courses`(
id INT PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(20) NOT NULL,
price DOUBLE NOT NULL
);
INSERT INTO `students` (name, age) VALUES('why', 18);
INSERT INTO `students` (name, age) VALUES('tom', 22);
INSERT INTO `students` (name, age) VALUES('lilei', 25);
INSERT INTO `students` (name, age) VALUES('lucy', 16);
INSERT INTO `students` (name, age) VALUES('lily', 20);
INSERT INTO `courses` (name, price) VALUES ('英语', 100);
INSERT INTO `courses` (name, price) VALUES ('语文', 666);
INSERT INTO `courses` (name, price) VALUES ('数学', 888);
INSERT INTO `courses` (name, price) VALUES ('历史', 80);
```

#### 创建关系表

我们需要一个关系表来记录两张表中的数据关系：

```sql
# 创建关系表
CREATE TABLE IF NOT EXISTS `students_select_courses`(
id INT PRIMARY KEY AUTO_INCREMENT,
student_id INT NOT NULL,
course_id INT NOT NULL,
FOREIGN KEY (student_id) REFERENCES students(id) ON UPDATE CASCADE,
FOREIGN KEY (course_id) REFERENCES courses(id) ON UPDATE CASCADE
);
```

```sql
# why 选修了 英文和数学
INSERT INTO `students_select_courses` (student_id, course_id) VALUES (1, 1);
INSERT INTO `students_select_courses` (student_id, course_id) VALUES (1, 3);
# lilei选修了 语文和数学和历史
INSERT INTO `students_select_courses` (student_id, course_id) VALUES (3, 2);
INSERT INTO `students_select_courses` (student_id, course_id) VALUES (3, 3);
INSERT INTO `students_select_courses` (student_id, course_id) VALUES (3, 4);
```

#### 查询多对多数据（一）

查询多条数据：

```sql
# 查询所有的学生选择的所有课程
SELECT 
stu.id studentId, stu.name studentName, cs.id courseId, cs.name courseName, cs.price coursePrice
FROM `students` stu
JOIN `students_select_courses` ssc
ON stu.id = ssc.student_id
JOIN `courses` cs 
ON ssc.course_id = cs.id; 
# 查询所有的学生选课情况
SELECT 
stu.id studentId, stu.name studentName, cs.id courseId, cs.name courseName, cs.price coursePrice
FROM `students` stu
LEFT JOIN `students_select_courses` ssc
ON stu.id = ssc.student_id
LEFT JOIN `courses` cs 
ON ssc.course_id = cs.id; 
```

#### 查询多对多数据（二）

查询单个学生选择了什么课

```sql
# why同学选择了哪些课程
SELECT 
stu.id studentId, stu.name studentName, cs.id courseId, cs.name courseName, cs.price coursePrice
FROM `students` stu
JOIN `students_select_courses` ssc
ON stu.id = ssc.student_id
JOIN `courses` cs 
ON ssc.course_id = cs.id
WHERE stu.id = 1; 
# lily同学选择了哪些课程(注意，这里必须用左连接，事实上上面也应该使用的是左连接)
SELECT 
stu.id studentId, stu.name studentName, cs.id courseId, cs.name courseName, cs.price coursePrice
FROM `students` stu
LEFT JOIN `students_select_courses` ssc
ON stu.id = ssc.student_id
LEFT JOIN `courses` cs 
ON ssc.course_id = cs.id
WHERE stu.id = 5;
```

#### 查询多对多数据（三）

查询哪些学生没有选择和哪些课程没有被选择：

```sql
# 哪些学生是没有选课的
SELECT 
stu.id studentId, stu.name studentName, cs.id courseId, cs.name courseName, cs.price coursePrice
FROM `students` stu
LEFT JOIN `students_select_courses` ssc
ON stu.id = ssc.student_id
LEFT JOIN `courses` cs
ON ssc.course_id = cs.id
WHERE cs.id IS NULL;
# 查询哪些课程没有被学生选择
SELECT 
stu.id studentId, stu.name studentName, cs.id courseId, cs.name courseName, cs.price coursePrice
FROM `students` stu
RIGHT JOIN `students_select_courses` ssc
ON stu.id = ssc.student_id
RIGHT JOIN `courses` cs
ON ssc.course_id = cs.id
WHERE stu.id IS NULL
```

前面我们学习的查询语句，查询到的结果通常是一张表，比如查询手机+品牌信息,但是在真实开发中，实际上品牌信息的部分应该放入到一个对象中，那么我们可以使用下面的查询方式

这个时候我们要用 JSON_OBJECT

```sql
SELECT products.id as id, products.title as title, products.price as price, products.score as score, 
JSON_OBJECT('id', brand.id, 'name', brand.name, 'website', brand.website) as brand
FROM products LEFT JOIN brand ON products.brand_id = brand.id;
```

#### 多对多转成数组

在多对多关系中，我们希望查询到的是一个数组：

 这个时候我们要 JSON_ARRAYAGG和JSON_OBJECT结合来使用；

```sql
SELECT stu.id, stu.name, stu.age, 
JSON_ARRAYAGG(JSON_OBJECT('id', cs.id, 'name', cs.name)) as courses 
FROM students stu
LEFT JOIN students_select_courses ssc ON stu.id = ssc.student_id
LEFT JOIN courses cs ON ssc.course_id = cs.id
GROUP BY stu.id;
```

### mysql2

安装mysql2

```
npm install mysql2
```

创建连接

```js
const mysql = require('mysql2')
const connection = mysql.createConnection({
  host: 'localhost',
  port: 3306,
  user: 'root',
  password: 'Dengjunyu123.',
  database: 'bilibili'  //数据库名称
});
```

执行sql语句

```js
// 2.执行操作语句, 操作数据库
const statement = 'SELECT * FROM `students`;'
// structure query language: DDL/DML/DQL/DCL
connection.query(statement, (err, values, fields) => {
  if (err) {
    console.log('查询失败:', err)
    return
  }
  // 查看结果
  console.log(values)
  // console.log(fields)
})
```

预处理语句

```js
// 2.执行一个SQL语句: 预处理语句
const statement = 'SELECT * FROM `products` WHERE price > ? AND score > ?;'  //[1000, 8]传给??
connection.execute(statement, [1000, 8], (err, values) => {
  console.log(values)
})
```

连接池

前面我们是创建了一个连接（connection），但是如果我们有多个请求的话，该连接很有可能正在被占用，那么我们是否需要 每次一个请求都去创建一个新的连接呢？

 事实上，mysql2给我们提供了连接池（connection pools）；

连接池可以在需要的时候自动创建连接，并且创建的连接不会被销毁，会放到连接池中，后续可以继续使用；

我们可以在创建连接池的时候设置LIMIT，也就是最大创建个数；

```js
// 1.创建一个连接
const connectionPool = mysql.createPool({
  host: 'localhost',
  port: 3306,
  database: 'music_db',
  user: 'root',
  password: 'Coderwhy123.',
  connectionLimit: 5
})

// 2.执行一个SQL语句: 预处理语句
const statement = 'SELECT * FROM `products` WHERE price > ? AND score > ?;'
connectionPool.execute(statement, [1000, 8], (err, values) => {
  console.log(values)
})
```

promise方式

目前在JavaScript开发中我们更习惯Promise和await、async的方式，mysql2同样是支持的：

```js
const mysql = require('mysql2')

// 1.创建一个连接
const connectionPool = mysql.createPool({
  host: 'localhost',
  port: 3306,
  database: 'music_db',
  user: 'root',
  password: 'Coderwhy123.',
  connectionLimit: 5
})

// 2.执行一个SQL语句: 预处理语句
const statement = 'SELECT * FROM `products` WHERE price > ? AND score > ?;'

connectionPool.promise().execute(statement, [1000, 9]).then((res) => {
  const [values, fields] = res
  console.log('-------------------values------------------')
  console.log(values)
  console.log('-------------------fields------------------')
  console.log(fields)
}).catch(err => {
  console.log(err)
})

```

项目中应用

```js
const mysql = require('mysql2')
// 1.创建一个连接
const connectionPool = mysql.createPool({
    host: 'localhost',
    port: 3306,
    database: 'codehub',
    user: 'root',
    password: 'Dengjunyu123.',
    connectionLimit: 5
})
// 2.获取连接是否成功
connectionPool.getConnection((err, connection) => {
    // 1.判断是否有错误信息
    if (err) {
      console.log('获取连接失败~', err)
      return
    }
  
    // 2.获取connection, 尝试和数据库建立一下连接
    connection.connect(err => {
      if (err) {
        console.log('和数据库交互失败', err)
      } else {
        console.log('数据库连接成功, 可以操作数据库~')
      }
    })
})
  // 3.获取连接池中连接对象(promise)
const connection = connectionPool.promise()
module.exports = connection
```

