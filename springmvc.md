# day1
MVC:model view controller

# day2
注解开发步骤：
1. 新建web项目
2. 导入jar包
3. 编写web.xml，注册dispatcherservlet
4. 编写springmvc配置文件
5. 创建对应的控制类controller
6. 完善前端视图和controller对应
7. 测试运行调试

Restful风格
@RequestMapping
`@PathVariable`注解

默认转发，手动转发`forward:`，重定向`redirect:`

数据处理：可以传递值或者传递对象，传递对象时一一匹配

***JSON***
前后端分离：后端部署，提供接口，提供数据，前端部署，渲染数据

json键值对  
工具类  
`objectMapper`

# day3
fastJSON

**整合**
- mybatis层，model层
1. 导入依赖
2. 连接数据库
3. 建立包文件夹
4. mybatis配置文件，spring配置文件，数据库连接配置db.properties
5. 建pojo实体类
6. dao层写接口，接口方法操作数据，再写mapper.xml数据库语句实现接口，并在mybatis-config.xml中注册
7. service层写接口，之后写实现方法，调用dao层（组合方法），调用dao方法
- spring层
1. 配置spring-dao：关联配置文件，连接池，sqlSessionFactory，配置dao接口扫描包
2. 配置spring-service：扫描service下的包，业务类注入spring，声明式事务，aop事务
- mvc
1. 配置web.xml：dispatcherServlet，乱码过滤，session
2. 配置spring-mvc：注解驱动，静态资源过滤，扫描包，视图解析器
- ssm整合
1. 编写controller层代码，实现数据交互
2. 测试

美化页面
bootstrap

**代码顺序**
人→前端→controller→service→dao→数据库  
写业务顺序相反  
CRUD到此结束  

**ajax**
异步js和xml

# day4
ajax
`$.ajax({url:"",data:"",success:"",error:""})`

异步加载数据，登录请求

拦截器：继承`HandlerInterceptor`，第一个拦截前 `return true`放行 `return false`拦截 ，后面两个拦截后和清理相当于日志

WEB-INF下的资源和页面，只能通过controller和servlet访问

**登录验证**

**文件上传和下载**
