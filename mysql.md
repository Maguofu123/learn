# mysql

# day1
安装mysql和sqlyog，配置环境

# day2
## 命令行操作
使用分号结尾;

查看所有库`show databases`，切换数据库`use`，显示表中的信息`describe`

`exit`退出连接

`--`单行注释，`/**/`多行注释

**CRUD**增删改查

DDL定义语言，DML管理语言，DQL查询语言，DCL控制语言

# day3
mysql不区分大小写

基本格式：
`create table if not exists 表名(
字段名 列类型 [属性] [索引] [注释],
字段名 列类型 [属性] [索引] [注释],
字段名 列类型 [属性] [索引] [注释]
)`[表类型][字符集设置][注释]

# day4
alter 修改命令[rename as] [add] [modify] [change] [drop]

drop 删除命令

**DML语言：**
- insert into 表名([字段],[字段]) values(''),(''),('...') 默认一一匹配，可以用default和null占位
- update 表名 set column_name1 = value1,column_name2 = value2  where [条件] *操作符* between and闭合区间，and, or 
- delete from 
- truncate 重新设置自增列，计数器清空

！**DQL语言** 最重点，最核心的语言

- select 表达式(\*是通配符) from 表   表达式包括：文本值，列，null，函数，计算表达式，系统变量
- 别名 as 字段可以别名，表也可以
- 连接 concat 连接自定义名字和字段
- 去重 distinct 去除重复的数据

where 条件子句 逻辑运算符 

模糊查询 本质是比较运算符 is null, is not null, between and, like 注意%和_, in 在多个范围内

联表查询 [xx] join on
外连接，内连接

# day 5
- 分页limit (a,b)a是起始，b是数量
- 排序order by [desc降序][asc升序]默认升序

子查询，可以嵌套

*MySQL函数*
1. 常用函数

数学运算 ceiling向上取整 floor向下取整 current_time时间

**聚合函数**包括 计数count()，平均值avg()，最大（小）值 max(),min()

count(字段)会忽略null值

group by 分组

having过滤条件              

where不能使用*聚合函数*

md5加密

# day 6
**事务** 
ACID原则，原子性，一致性，持久性，隔离性
脏读，不可重复读，幻读

mysql默认开启事务 set autocommit = 1

start transaction 开启一个事务
commit 提交
rollback 回滚

set autocommit = 0


**索引**
- 主键索引(primary key) 不能重复
- 唯一索引 unique 避免重复的列出现
- 常规索引 index/key
- 全文索引 fulltext 快速定位数据

delimiter 关键字

# day7
用户管理：对mysql数据库里的user表进行修改

备份：
- 命令行 mysqldump
- sqlyog可视化操作

导入：
命令行导入，切换到数据库，source 备份文件

数据库设计：
例如：*个人博客*

三大范式
第一范式：原子性，不可再分

第二范式：前提，满足第一范式，每张表只描述一件事情

第三范式：前提，满足第一和第二范式，非主键和主键必须直接相关，不能间接相关        

性能和规范要进行适当的取舍

**JDBC**

数据库驱动

# day 8
创建项目

步骤：
       `
       //1.加载驱动
        Class.forName("com.mysql.cj.jdbc.Driver");

        //2.用户信息和url
        String url = "jdbc:mysql://localhost:3306/jdbcstudy?useUnicode=true&characterEncoding=utf8&useSSL=true";
        String username = "root";
        String password = "123456";

        //3.连接成功，数据库对象
        Connection connection = DriverManager.getConnection(url,username,password);

        //4.执行sql的对象 statement
        Statement statement = connection.createStatement();

        //5.执行sql的对象，查看返回结果
        String sql = "select * from users";

        statement.executeQuery(sql);

        ResultSet resultSet = statement.executeQuery(sql);

        while (resultSet.next()){
            System.out.println("id=" +resultSet.getObject("id"));
            System.out.println("name=" +resultSet.getObject("name"));
            System.out.println("pwd=" +resultSet.getObject("password"));
            System.out.println("email=" +resultSet.getObject("email"));
            System.out.println("birth=" +resultSet.getObject("birthday"));
            System.out.println("=======================================");
        }

        //6.释放连接
        resultSet.close();
        statement.close();
        connection.close();`

- drivemanager 加载驱动
- url 主机地址，端口号
- connection 对象代表数据库
- statement 代表执行sql对象
- sql 编写sql
- ResultSet 查询的结果集，获得指定的结果类型，指针 .next()  .absolute(row)  
- .close 释放资源，连接消耗资源，必须关掉

**statement**对象

增删改 executeUpdate, 查询 executeQuery

sql注入，存在漏洞

**preparedStatement**

可以防止sql注入，并且效率更高

连接数据库
