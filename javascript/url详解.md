## URL详解

标签： url 浏览器知识

格式：

```
scheme://host:port/path?query#fragment
```

* scheme      指定低层使用的协议(例如：http, https, ftp)

* host           HTTP服务器的IP地址或者域名

* port           HTTP服务器的默认端口是80，这种情况下端口号可以省略。如果使用了别的端口

* path          访问资源的路径

* query        查询，用于给动态网页传递参数，多个用&分开，发送给http服务器的数据

* fragment-      信息片段，用于指定网络资源中的片段

## 域名
* 域名系统采用层次结构，按地理域或机构域进行分层，用小数点将各个层次隔开，从右到左依次为最高域名段、次高域名段等，最左的一个字段为主机名。
* 一级域名由主域名加 "." 加顶级域名组成，即（主域名）+( . )+(顶级域名)。
* 顶级域名 中国是cn，美国是us，日本是jp 工商企业的 .Com，网络提供商的.net，非盈利组织的.org
* 二级域名 二级域名是指顶级域名之下的域名，com，.top，edu，gov，net
* 三级域名 三级域名用字母（ A～Z，a～z，大小写等）、数字（0～9）和连接符（－）组成
* IIS Internet Information Services的缩写，意为互联网信息服务，是由微软公司提供的基于运行Microsoft Windows的互联网基本服务，Windows 环境中的，网站服务器组建。
* DNS DNS（Domain Name System，域名系统），因特网上作为域名和IP地址相互映射的一个分布式数据库，能够使用户更方便的访问互联网，而不用去记住能够被机器直接读取的IP数串。


## HTTP协议是无状态的

 http协议是无状态的，同一个客户端的这次请求和上次请求是没有对应关系，对http服务器来说，它并不知道这两个请求来自同一个客户端。

## Get和Post方法的区别

GET一般用于获取/查询资源信息，而POST一般用于更新资源信息。

* GET提交的数据会放在URL之后，以?分割URL和传输数据，参数之间以&相连，如EditPosts.aspx?name=test1&id=123456.  POST方法是把提交的数据放在HTTP包的Body中。

* GET提交的数据大小有限制（因为浏览器对URL的长度有限制），而POST方法提交的数据没有限制。

* GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值。

* GET方式提交数据，会带来安全问题，比如一个登录页面，通过GET方式提交数据时，用户名和密码将出现在URL上，如果页面可以被缓存或者其他人可以访问这台机器，就可以从历史记录获得该用户的账号和密码。

## 状态码

```
1XX  提示信息 - 表示请求已被成功接收，继续处理

2XX  成功 - 表示请求已被成功接收，理解，接受

3XX  重定向 - 要完成请求必须进行更进一步的处理

4XX  客户端错误 -  请求有语法错误或请求无法实现

5XX  服务器端错误 -   服务器未能实现合法的请求

```

##### 常见状态码

* 　200 OK

* 　302 Found  重定向，新的URL会在response中的Location中返回，浏览器将会        使用新的URL发出新的Request。

 　　例如在IE中输入http://www.google.com. HTTP服务器会返回304， IE取到Response中Location header的新URL, 又重新发送了一个Request.

* 　304 Not Modified 代表上次的文档已经被缓存了， 还可以继续使用，


* 　400 Bad Request  客户端请求与语法错误，不能被服务器所理解

* 　403 Forbidden 服务器收到请求，但是拒绝提供服务

* 　404 Not Found

* 　500 Internal Server Error 服务器发生了不可预期的错误

* 　503 Server Unavailable 服务器当前不能处理客户端的请求，一段时间后可能恢复正常

## 同源策略

URL1 | URL2|说明|通信
---|---|---|---
http://wwww.a.com/a.js |http://wwww.a.com/b.js |同一域名|可以
http://wwww.a.com/aa/a.js: | http://wwww.a.com/bb/b.js|同一域名下不同文件夹|可以
http://wwww.a.com:8080/a.js|http://wwww.a.com:9999/a.js|同一域名，不同端口|不可以
http://wwww.a.com/a.js|https://wwww.a.com/a.js|同一域名，不同协议|不可以
http://wwww.a.com/a.js|http://170.2.2.2/a.js|域名和域名对应ip|不可以
http://wwww.a.com/a.js|http:/mmm.a.com/a.js|主域相同，子域不同|不可以
http://wwww.a.com/a.js|http:/a.com/a.js|同一域名，不同二级域名|不可以
http://wwww.a.com/a.js|http://wwww.b.com/a.js|不同域名|不可以









