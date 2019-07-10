#  PHP学习笔记—第一章

### PHP环境搭建和调试：（LAMP和LNMP）

> 1.LAMP
>
> > L：Linux 服务器
> >
> > A：Apeche web 服务器
> >
> > M：Mysql 数据库
> >
> > P：PHP 动态程序

> 2.LNMP
>
> > L：Linux 服务器
> >
> > N：Nginx web 服务器
> >
> > M：Mysql 数据库
> >
> > P：PHP 动态程序

> 3.WAMP
>
> > W：Windows 服务器
> >
> > A：Apeche web 服务器
> >
> > M：Mysql 数据库
> >
> > P：PHP 动态程序

> 4.WNMP
>
> >W：Windows 服务器
> >
> >N：Nginx web 服务器
> >
> >M：Mysql 数据库
> >
> >P：PHP 动态程序

### Apache和Nginx web服务器优缺点：

- Apache
  - 稳定性好
  - 并发性能低（3000）
  - 配置简单

- Nginx
  - 稳定性差
  - 并发性能高（30000）
  - 配置复杂

### Windows下PHP环境配置（WAMP）：

1. appserv
2. wampserver
3. phpstudy
4. easyphp
5. xampp
6. phpnow

### Linux下php环境配置（LAMP）：

1. 源代码分别安装：apache，mysql，php软件包（gz，zip，bz2）
2. LAMP集成包：phpstudy

### AMP作用机制：

1. 客户端通过浏览器去访问服务器。
2. 访问Apache web 服务器。
3. Apache去寻找HTML文件，则Apache直接把该文件返回给客户端浏览器即可。
4. Apache去寻找PHP文件，则Apache会利用PHP解析器去解析该PHP脚本，然后把解析后的HTML返回给客户端浏览器。
5. Apache去寻找PHP文件，并且其中含有Mysql动态数据，则Apache会利用PHP解析器去解析该PHP脚本，同时PHP脚本会连接Mysql数据库并获取动态数据，然后再解析成HTML文件返回给客户端浏览器。

### 静态网页和动态网页区别：

1. 直接访问HTML文件并返回给客户端。
2. 需要利用PHP，ASP，JSP解析器先解析PHP，ASP，JSP动态脚本的为动态网页。

### 安装调试Windows下AMP集成环境：（appserv）

1. 常规方法

   1. 计算机->右键->管理->服务：
      1. apache24 是否启动
      2. mysql57 是否启动

   2. 任务管理器
      1. http
      2. mysql

2. DOS方法
   1. win + r输入cmd进入dos环境。
   2. tasklist | find ”http“
   3. tasklist | find ”mysql“

3. 如何关闭Apache和mysql服务

   1. 常规方法
      1. 在计算机服务列表进行关闭

   2. dos命令
      1. net stop apache24
      2. net stop mysql57

4. 如何开启apache和mysql服务

   1. 常规方法
      1. 在计算机服务列表进行开启

   2. dos命令
      1. net start apache24
      2. net start mysql57

### 写下第一段PHP程序：（index.php）

```php
<?php
	//php代码
	phpinfo();
?>
```

### 如何在appserv下切换php版本：

1. 查找apache配置文件
   - AppServ\Apache24\conf\httpd.conf

2. 设置php7解析器
   - #LoadModule php5_module C:/AppServ/php5/php5apache2_4.dll
   - LoadModule php7_module C:/AppServ/php7/php7apache2_4.dll

3. 设置php7的配置文件
   - #PHPIniDir "C:/AppServ/php5/"
   - PHPIniDir "C:/AppServ/php7/"