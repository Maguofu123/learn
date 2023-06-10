# vue
# day1
SOC原则（关注度分离）：
- HTML+CSS+JS，视图层
- 网络通信：axios
- 页面跳转：vue-router
- 状态管理：vuex
- VUE-UI：ICE

vue：MVVM+DOM，独特功能：计算属性

vm对象：监视视图

vue7个属性：el，data，methods，

双向绑定-视图发生变化，则数据也发生变化

**vue语句**
1. v-if
2. v-for
3. v-on
4. v-model

组件：`vue.component`

axios：异步通信，获取数据`axios.get('../data.json').then(response=>(this.xx=response.data));`

计算属性：缓存，节省资源

# day2
插槽slot：调用vue实例的方法

自定义事件:`$.emit`

vue-cli：vue脚手架

web-pack打包

**vue-router**：跳转到不同的组件component

路由嵌套

**参数传递**
通过props传递参数，${{}}获取参数

钩子：相当于拦截器
