# javaWeb
# day 1
静态web：html，css

动态web：servlet/jsp,asp,php

动态web开发简称为javaweb

web应用由多部分组成

jsp,asp,b/s,c/s

# day2
Web服务器：
- iis
- tomcat配置：默认端口号8080，配置端口号，配置主机名称

发布一个网站

网站结构：
<center>
<img src="https://user-images.githubusercontent.com/91414286/218453878-53a9df07-5ce2-478b-b569-26f2fc9b68f4.png" width="30%" height="30%" />
</center>

http超文本传输协议，80端口

https，443端口

请求-响应

# day3
maven:架构管理工具，用于主动配置和导入jar包

核心思想：约定大于配置

阿里云镜像，本地仓库

配置maven

配置tomcat

# day 4
servlet：实现servlet接口的java程序叫servlet

maven环境优化：修改web.xml，搭建maven结构

servlet编写一个普通类，继承接口

mapping：映射，指定路径比通配符优先级高

servletcontext类：
- 上下文，启动时为每个web对象创立一个context对象
- 设置web.xml，然后启动
- 读取资源文件


HttpServletRequest类：web服务器接收到请求，创建代表请求的`request`对象和代表响应的`response`对象
1. 代表客户端请求，通过request方法，可以获得所有信息，转发




HttpServletResponse类：web服务器接收到请求，创建代表请求的`request`对象和代表响应的`response`对象
1. 分类：向浏览器发送数据
2. 响应状态码：200成功，3xx重定向，4xx找不到资源，5xx服务器错误
3. 下载文件：<center>
<img src="https://user-images.githubusercontent.com/91414286/219865176-a8d8f159-b2ae-48e6-83b3-1dd89e780b53.png" width="30%" height="30%" />
</center>

5. 验证码
6. response重定向：常见场景，用户登录  
7. 重定向302与转发307
- 相同点：转发url不会变化，重定向会变化
- 重定向会转到根路径，转发是相对路径

## cookie
会话：打开浏览器，点击超链接，访问web，关闭浏览器，称为一次会话

有状态会话：重复登录访问过的网站

cookie是客户端技术（请求，响应）

cookies：从请求中拿到cookie，服务器响应cookie

# day5
## session（重点）

session是服务器技术，可以保存用户的会话信息，可以把信息或数据放在session

session：服务器给每个用户（浏览器）创建一个session对象，一个session独占一个浏览器

有效时间在web.xml里面设置，自动过期


## JSP
java server pages(JSP) ：用于开发动态web

jsp原理

`<%= %>`jsp表达式：将程序的结果输出到客户端
`<%  %>`jsp脚本片段，脚本片段的代码必须保证java语法的正确性

jsp声明

定制错误页面

`pageContext`, `request`, `session`, `application`

EL表达式：${}，获取数据，执行运算，获得对象

JSTL标签:`<c:foreach >`,`<c:if >`,`<c:out >`


## day6
javabean

ORM:对象关系映射，表-类，字段-属性，行记录-对象

MVC三层架构:model, view, controller模型，视图，控制器
servlet专注于处理请求，JSP专注于显示数据

model:
- 业务处理（service）
- 数据持久层（Dao）

view：
- 展示数据
- 提供链接发起servlet请求

controller：
- 接收用户的请求 （req，session..）
- 交给业务层处理代码
- 控制视图跳转

filter 过滤器：用来过滤网站的数据，实现filter接口，重写方法，`chain.dofilter`

listener 监听器

提取常量

## 回顾JDBC

```    
//1.加载驱动
Class.forName("com.mysql.jdbc.Driver");
//2.连接数据库
Connection connection = DriverManager.getConnection(url, username, password);
//3.向数据库发送sql的对象
Statement statement = connection.createStatement();
//4.编写sql
String sql = "select * from users";
//5.执行查询sql，返回结果集
ResultSet resultSet = statement.executeQuery(sql);
//6.关闭连接
.close
```

## day7
***junit，在方法上加@Test直接测试***
<br>
SMBMS（超市订单管理系统）:  
项目搭建：
1. 搭建maven web项目
2. 配置tomcat
3. 测试项目是否能运行
4. 导入项目中需要的jar包
5. 创建项目包结构
6. 编写实体类：ORM映射
7. 编写基础公共类：1.数据库配置文件 2.编写数据库的公共类 3.编写字符编码过滤器
8. 导入静态资源 
<br>

登录功能


