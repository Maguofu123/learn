# springcloud
# day1
知道地址后，基于Restful风格，通过远程调用实现微服务

CAP原则：
- c 强一致性
- a 可用性
- p 分区可用性

这三个特性最多同时实现两个点，不可能三个同时实习

zookeeper保证cp， eureka保证ap

# day2
**负载均衡** load balance
- 集中式负载均衡，nginx
- 进程式负载均衡，ribbon

ribbon 默认轮询算法
