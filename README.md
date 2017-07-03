# 编写可维护的Javascript代码

- [欢迎来提issue进行改进](https://github.com/Kelichao/work.expressive)

- [参考《编写可维护的JavaScript》](http://baike.baidu.com/link?url=zn9j-dvLCZyZ-BsCdBr5kO674AagHo4iMdq6zR1KDvxnDCV4VzlDZ_IBnMeg7fhOutujqk_zomnsWG-sFcfrZjwyVb-T8BfsDLFUAB99w72UdOEaIbcLMkA9_JnoF_ghH0ZxSQmn_vG_-POH2THmxWWkkTgeev2Yb0x6euwyNvK)

- [wiki前端框架的基本的架构方案]( http://wiki.evun.cn/pages/viewpage.action?pageId=3933068)

> 代码风格根据团队内部成员总结所得，大家有好的意见或建议可以一起来进行定制O(∩_∩)O



### 目录
```
|--1.基本的格式化
|   |--1.1缩进
|   |--1.2语句结尾分号
|   |--1.3 行的长度
|   |--1.4 换行
|   |--1.5空行
|   |--1.6命名
|       |--1.6.1变量和函数
|   |--1.7直接量换行
|--2.注释
|   |--2.1单行注释
|   |--2.1多行注释
|   |--2.1特殊注释
|   |--2.1函数注释
|--3.语句和表达式格式
|   |--3.1对齐花括号
|   |--3.2循环语句中的变量提前
|   |--3.3运算符间距
|   |--3.4三元运算符的处理
|--4.变量声明规范
|   |--4.1 多var变量声明
|   |--4.2全等(===)代替双等（==）
```


# 一、基本的格式化
## 1.1缩进
> 推荐的是一个tab，优点是比较便捷，而且层级明显，缺点是不同的编辑器对tab Size的理解不一样。某些书籍推荐使用4个空格做缩进，优点是不会被代码编辑器缩进所干扰，缺点是要敲比较多的空格

```js
if (1) {
    if (2) {
        if (3) {
            // some code
        }
    }
}
``` 
## 1.2语句结尾分号
> 推荐在非条件语句结束时统一加上分号“;”

```js
// 推荐
var name = "Bob";
// 不推荐
var age = 100

// 缺分号的后果
// 如果当前函数以闭包形式编写，前面的代码没有分号会报错
// 所以很多以闭包形式编写的插件会在开头添加分号，以防止错误
;(function() {
	// somecode
})();
```

## 1.3 行的长度
> 推荐将行的长度限制在80个字符

## 1.4 换行
> 换行后需要两个tab，并且逗号需要留在上一行

```js
// 换行后需要两个tab，并且逗号需要留在上一行
doit(element, window, document, "some code", true, 
        "abc", "def");
```
## 1.5空行
1. 在方法之间。
2. 在方法中的局部变量和第一条语句之间。
3. 在多行或单行注释之前。
4. 在方法内的逻辑片段之间插入空行，提高可读性。

## 1.6命名

```js
// 驼峰法用于普通变量，功能函数
var anotherNames;

// 首字符大写用于构造函数
function Model(){// somecode}

// 全大写字母用于常量
var PERSON_COUNT = 10;

// #新型命名法

// 1. 字符串
var s_myString = "asdf";

// 2. 数组
var a_myArray = [1, 2, 3, 4];

// 3. 对象
var o_myObject = {a: 1, b: 2};

```
## 1.6.1变量和函数
> 变量名前缀应当为名词

```js
var count = 10;
var myName = "Bob";
```

> 方法函数名应该以动词开头

```js
function getName() {
    // some code
}
```

<table>
    <tr>
        <td>动词</td>
        <td>含义</td>
    </tr>
    <tr>
        <td>can</td>
        <td>返回布尔值</td>
    </tr>
    <tr>
        <td>has</td>
        <td>返回布尔值</td>
    </tr>
    <tr>
        <td>is</td>
        <td>返回布尔值</td>
    </tr>
    <tr>
        <td>get</td>
        <td>返回一个非布尔值</td>
    </tr>
    <tr>
        <td>set</td>
        <td>用于保存值</td>
    </tr>
</table>

## 1.6.2前后台变量名不一致
```js
// 预先进行缓存
var productionSeqNumber = "productId";

var data = {
    productId: 12345678
};

var final = {
    productionSeqNumber: ""
};

// 一一对应，防止混淆
final.productionSeqNumber = data[productionSeqNumber];
```

## 1.6.3 异步请求变量缓存
> 将单纯的数组存储方式改为用单一有效值数据对象进行存储
[demo](https://github.com/Kelichao/javascript.basics/issues/49)

## 1.7直接量换行
> 换行

```js
//合法，但不推荐
var str = "asdfghjklzxc\
vbnbm";

// 推荐 "+" 分割
var str = "asdfghjklzxc" + 
          "vbnbm";
```

# 二、注释

## 2.1单行注释
> 单行注释

```js

// 我是单行注释
fn();
```

## 2.2多行注释
> 多行注释

```js

/*
 * 这是一个多行注释
 * 星号后面要留空格
 */
fn();
```
## 2.3特殊注释
> 特殊注释

```js
/*
 * TODO: 说明代码还未完成，应当包含下一步要做的事。
 * HACK: 该问题可能有更好的解决办法
 * XXX：说明代码是有问题的，应当尽快修复
 * FIXME: 有问题，要紧程度比XXX低
 * REVIEW: 说明代码任何可能的改动都需要评审
 */
```

## 2.4函数注释

> 函数注释

- 函数注释包括了函数功能与函数参数的代表意义

```js
/**
 * @功能： 	渲染步骤，并返回一个增加后的步数
 * @param    {number}  nowStep   当前步骤序号
 * @param    {number}  total     总的步骤数
 */
increaseStep: function(nowStep, total) {
	$(".now-step").html(nowStep);
	$(".step-total").html(total);
	return ++nowStep;
}
```

> JS文件头注释

```js
/*!
 * @description: 较为常用的工具集合
 * @author: kelichao
 * @update: 2016-12-28 / 增加了埋点文件以及调用客户端接口文件的方法
 * @https://github.com/Kelichao/kit.js
 */

```
# 三、语句和表达式格式
## 3.1对齐花括号

> 注意空格，对齐花括号

```js
if (condiction) {

}
```

## 3.2循环语句中的变量提前
```js
var i;
for (i = 0; i < 10; i++) {
    // some code
}
```

## 3.3运算符间距
```js
var fond = (value1 === value2);
```

## 3.4三元运算符的处理
```js
 var instanceData = typeof childVal === 'function'
 ? childVal.call(vm)
 : childVal;
```
# 四、变量声明规范
## 4.1 多var变量声明
```js
// 推荐多var方式声明变量
// 且统一放在函数体顶部
var a = 1;
var b = 2;
var c = 3;

// 目前不推荐单var声明
// 原因是需要注意结尾逗号与分号，如果一不留神写了分号，则声明为全局变量
// 例如：
var d = 4,
    e = 5;
    f = 6;// 意外变为全局变量
```

## 4.2全等(===)代替双等（==）

>推荐用全等(===)代替双等（==）
```js
if (1 === "1") {
    // some code
}
```


