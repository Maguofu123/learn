# javascript
# day 1

**引入**

alert弹窗

内部标签`<script src> js代码 </script>`

外部引入`<script src=''></script>`

**基本语法**

所有变量都用var定义

javascript严格区分大小写

console.log()在控制台里打印元素

js不区分小数和整数

number包含整数，浮点数，布尔数，NaN，数组，对象

null和undefined

浮点数存在精度问题

# day 2

严格检查模式，第一行写`'use strict'`

数据类型

**字符串**

substring从第一个字符串截取到最后的字符串

**数组**

`indexOf()`获取索引下标，`slice()`截取arr的一部分，返回一个数组

`pop()``push()`尾部弹出和插入，`unshift()``shift()`头部弹出和插入

`sort()`排序

`reverse()`元素反转

`concat`

`join`打印拼接数组，使用特定字符串连接

``多维数组

## 对象类型
键是字符串，值是任意属性

**赋值**

`var 对象名={属性名：属性值，
           属性名：属性值}`

**动态删减属性**

`delete`删除对象属性

**动态添加属性**

直接给新属性赋值

**判断属性值是否在对象中**

`'xx' in xx`

**判断一个属性是否是这个对象自身拥有的**

`hasOwnproperty()`

## 流程控制
for,while,foreach,for(index in)

**map**和**set**

map键值对，类似字典

`set`添加元素，`delete`删除元素


set无序不重复的集合

`add`添加,`delete`删除，`has`是否含有

# day 3
## 定义函数
如果没有return，返回undefined

**方式1**

`function f(x){[return]}`

**方式2**

`var f = function(x){[return]}`这是一个匿名函数，把结果赋值给f，通过f调用函数

`arguments`获得所有参数

`...rest`参数放在函数最后，获取已经定义的参数之外的所有参数

## 变量作用域
var如果在函数体内定义，在函数体外不可用

函数查找由内层函数向外层函数查找

变量定义在函数体外部即全局变量

全局对象window

变量向外查找，函数体内→全局window

## 规范
如何减少不同js文件的冲突

把自己的代码放入自己定义的唯一空间中，降低命名冲突

**局部作用域**

使用`let`定义局部作用域

**常量**

`const`

**方法**

方法就是把函数放在对象里面，对象有方法和属性两个东西

this默认指向调用它的对象

`apply(object,arguments)`控制this指向

## 内部对象

日期Date，  `Date.Time`是时间戳


- 对象都用{}
- 数组都用[]
- 所有的键值对都是用key:value

## JSON

json和js对象的转换

json.stringify()

json.parse()

**json和js对象的区别**

![image](https://user-images.githubusercontent.com/91414286/205037894-a4b79a1b-e432-472c-8060-7ad68118021d.png)
js对象

![image](https://user-images.githubusercontent.com/91414286/205038026-1c41cd3a-6d2e-4503-b4c2-bba8b2577aee.png)
json

**Ajax**

## 面向对象编程

- 原型继承：`object.__proto__`

- class继承：定义一个类，属性，方法 和 java类似

**原型链**


## 操作BOM
浏览器对象模型：
内核ie，chrome，safari，firefox

window代表浏览器窗口

`Navigator`

`screen`

`location`**（重要）** 代表当前页面的URL信息

`document`当前页面信息，获取文档树节点，获取网页cookie

`history`

## 操作DOM

使用`document`

# day 3

通过获取的节点进行innerText等操作修改网页

**删除节点**

先获取自己，再获取父节点，再删除子节，*删除是动态的*（注意）

**插入节点**

注意会产生覆盖

追加`.append()`，创建一个新标签实现插入

# day 4
## 操作表单（验证）

value获得值，单选框checked检查是否选择

**提交表单**

绑定事件，按钮级别`onclick=function()`，表单级别`onsubmit=function()`

md5加密

## jQuery

里面存在大量的js函数 

公式`$(selector).action()`，选择器就是css的选择器

原生js选择器少

## action()事件

获取鼠标当前坐标

## 操作DOM



