# SpringBoot
# day1
微服务：
- javase：oop思想
- mysql：数据持久化
- html+css+js+jquery+框架
- javaweb
- ssm
- springboot
- springcloud

# day2
搭建环境：
- jdk 1.8
- maven 3.6.1
- springboot
- IDEA

自动配置原理：
- pom.xml存放了
- 启动器：要使用某一功能，找到对应的启动器就行了

springboot所有自动配置在启动时扫描并加载

Run

尽量使用yml语法：`name: xx`

# day3
松散绑定：中划线-和驼峰命名一样的效果

JSR303：检查字符 validation里查看具体类型

**自动装配** 
- xxxProperties → xxxAutoConfiguration  
- xxxProperties：自动配置类，装配配置文件中的一些自定义内容
- xxxAutoConfiguration ：向容器中自动装配组件
- 在启动时加载大量自动配置，如果不存在，需要手动配置

springboot web开发 流程
1. 导入静态资源，可以使用以下方法webjars，public，/\*\*，resources
2. 首页
3. jsp，模板thymeleaf
4. 装配springmvc

thymeleaf：放在templates文件夹下，语法和vue较为接近

扩展mvc

# day4
页面国际化：
1. 配置i18n文件
2. 自定义组件LocaleResolver
3. 将组件配置到spring容器`@Bean`中

伪装html页面`addViewController("/xx.html").setViewName("xx")`

登录拦截器

**员工管理系统：**
1. 首页配置
2. 页面国际化
3. 登录器，拦截器
4. 员工页面展示：提取公共页面，列表循环展示
5. 添加员工：按钮提交，跳转到添加页面，添加员工成功，返回首页
6. CRUD
7. 404

# day5
整合mybatis
1. 导入包
2. 配置文件
3. mybatis配置
4. 编写sql
5. service层调用dao层
6. Controller调用service层

**springsecurity（安全）**
1. 功能权限
2. 访问权限
3. 菜单权限
4. 拦截器，过滤器

几个类：
- WebSecurityConfigurerAdapter
- AuthenticationManagerBuilder
- @EnableWebsecurity

# day6
shiro框架

# day7
swagger  
配置Docket类，配置ApiInfo

邮件功能

异步任务 `@EnableAsync`
定时任务 `@EnableScheduling` `\/秒 分 时 日 月 周`

**分布式：**
- ngix代理服务器

# day8
RPC核心模块：通讯，序列化

dubbo：RPC框架

zookeeper：
