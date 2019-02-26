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
MySQL 为关系型数据库(Relational Database Management System), 这种所谓的"关系型"可以理解为"表格"的概念, 一个关系型数据库由一个或数个表格组成, 如图所示的一个表格:

- **表头(header):** 每一列的名称;
- **列(row):** 具有相同数据类型的数据的集合;
- **行(col):** 每一行用来描述某个人/物的具体信息;
- **值(value):** 行的具体信息, 每个值必须与该列的数据类型相同;
- **键(key):** 表中用来识别某个特定的人\物的方法, 键的值在当前列中具有唯一性。

## 参考
[MySQL入门](http://www.cnblogs.com/mr-wid/archive/2013/05/09/3068229.html#c1)
