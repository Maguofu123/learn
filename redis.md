# redis
## day1
Nosql：not only sql
- 不仅仅是数据库
- 没有固定的查询语言
- 键值对存储，列存储，文档存储，图形数据库（社交关系）
- 最终一致性
- CAP和BASE （异地多活）

## day2
本地源码编译

> redis命令
- `select [index]`选择数据库
- `flushdb`清除数据库，`flushall`清楚所有数据库
- 基本命令`set`,`move`,`del`,`keys`,`exists`,`expire`,`type`

> 数据类型
**String**
- `incr`,`decr`,`incrby`,`decrby`,`getrange`,`setrange`
- `setex`(set with expire),`setnx`(set if not exist)

## day3
**List** 无序可重复
- `lpush`,`lrange`,`lpop`
- `rpush`,`rpop`
- `ltrim`,
- `lset`
- `linsert`
- `rpoplpush`
- `lrem`
- `llen`,`lindex`

## day4
**Set** 无序不重复
- `sadd`, `smembers`,`sismembers`
- `scard`,`srem`,`srandmember`
- `spop`随机移除一个元素
- `sdiff`差集,`sinter`交集,`sunion`并集

**Hash** 键值对
- `hset`,`hget`,`hmset`,`hmget`,`hgetall`
- `hdel`
- `hlen`,`hexists`
- `hkeys`,`hvals`
- `incr`,`decr`

**Zest** 有序集合
- `zset`
- `zrange`
- `zrem`,`zcard`,`zrevrange`
- `zcount`

三种特殊类型
**geospatial**
- `geoadd`
- `geopos`,`geodist`
geo 底层实现是zset，可以使用zset来操作geo

**Hyperloglog** 基数统计算法
-  基数是不重复的元素，
-  `pfadd`, `pfcount`
-  `pfmerge`

**Bitmaps** 位存储
- `setbit`, `getbit`

**事务** 本质：一组命令的集合，一次性，顺序性，排他性
- 所有命令会被序列化，会按照顺序执行
- 单条命令是*原子性*的，事务*不是原子性*的
- 没有隔离级别的概念

> 执行事务
1. 开启事务 multi
2. 命令入队
3. 执行事务 exec 

> 放弃事务
- `discard` 

编译型异常（代码有问题），编译时事务报错，所有命令都不会被执行

运行时异常（语法性问题），执行时事务报错，其他命令可以执行

**锁**
- 悲观锁，认为什么时候都会出现问题，无论做什么都会加锁
- 乐观锁，认为不会出现问题，不会加锁

`watch` 监视对象，加乐观锁

jedis
远程连接服务器redis：重写redis.conf配置文件→注释127.0.0.1，设置密码，protected-mode设置为no，开放端口号，重启redis-server服务  
`redis-cli shutdown`,`redis-server myconfig/redis.conf`, `redis-cli -h ip地址 -p 端口号，一般为6379`，`auth 密码`

## day5
springboot整合redis
1. 导入依赖
2. 配置连接
3. 测试

注入redisTemplate

**序列化**：
自己编写redisTemplate模板，使用jackson

持久化：
在规定时间内，执行了多少次操作，则会持久化到文件 .rdb .aof

**RDB（redis database）持久化** dump.rdb
- save会触发rdb
- 执行flushall，触发rdb规则
- 退出redis，产生rdb文件

**AOF（append only file）持久化** 记录所有的写操作，appendonly.aof
- 记录所有的命令
- aof有错误则redis无法启动

## day6
redis发布
**订阅** 
 通信 队列 发送者 订阅者
- 频道发布内容
- 实时聊天

**主从复制**
- 搭建集群，真实项目中不可能单机使用redis
- 配置环境：只配置从库，不用配置主库 `info replication`查看信息，修改从机配置文件
- 主机可以写，从机只能读
- 主机断开，从机依旧连接到主机；主机恢复，从机依旧可以读取到主机的信息
- 如果是使用命令行配置的主从，从机断开后就会变成主机
- 只要变为从机，则从主机中获得值

复制原理
- sync同步命令
- 全量复制
- 增量复制

**集群模型**
- 一对多
- 链路模型

**哨兵模式**
- 配置哨兵文件
- 开启哨兵进程

**缓存穿透和雪崩**
- 缓存中没有命中，于是查询数据库，给数据库带来很大压力而崩溃
- 布隆过滤器，缓存空对象
- 雪崩：缓存集中过期，服务器宕机

redis高可用，限流降级，数据预热