# MySQL 安装
## Ubuntu MySQL 安装
ubuntu上安装mysql非常简单只需要几条命令就可以完成。
```
sudo apt-get install mysql-server
 
sudo apt-get isntall mysql-client
 
sudo apt-get install libmysqlclient-dev
```
安装过程中会提示设置密码什么的，注意设置了不要忘了，安装完成之后可以使用如下命令来检查是否安装成功：
`sudo netstat -tap | grep mysql`
通过上述命令检查之后，如果看到有mysql 的socket处于 listen 状态则表示安装成功。

登陆mysql数据库可以通过如下命令:
`mysql -u root -p `
-u 表示选择登陆的用户名， -p 表示登陆的用户密码，上面命令输入之后会提示输入密码，此时输入密码就可以登录到mysql。

## MySQL的相关概念介绍
MySQL 为关系型数据库(Relational Database Management System), 这种所谓的"关系型"可以理解为"表格"的概念, 一个关系型数据库由一个或数个表格组成。
- **表头(header):** 每一列的名称;
- **列(row):** 具有相同数据类型的数据的集合;
- **行(col):** 每一行用来描述某个人/物的具体信息;
- **值(value):** 行的具体信息, 每个值必须与该列的数据类型相同;
- **键(key):** 表中用来识别某个特定的人\物的方法, 键的值在当前列中具有唯一性。

## MySQL数据库管理系统

MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一

- **数据库：** 数据库是一些关联表的集合。
- **数据表：** 表是数据的矩阵。在一个数据库中的表看起来像一个简单的电子表格。
- **视图：** 视图是对若干张基本表的引用，一张虚表，查询语句执行的结果，不存储具体的数据（基本表数据发生了改变，视图也会跟着改变）
- **存储过程：** sql语句需要先编译然后执行，而存储过程时一组为了完成特定功能的sql语句集，经编译存储在数据库中，用户通过执行存储过程的名字并给定参数，来调用执行它

存储过程是可编程的函数，在数据库中创建并保存，可以有sql语句和控制结构组成，当想要在不同的应用程序或者平台上执行相同的函数，或者封装特定功能时，存储或称是十分有用的，数据库的村粗过程可以看作是编程中面向对象方法的模拟，它允许控制数据的访问方式。

## 参考
[MySQL入门](http://www.cnblogs.com/mr-wid/archive/2013/05/09/3068229.html#c1)

