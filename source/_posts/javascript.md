---
title: JavaScript
toc: true
comments: true
date: 2020-09-28 09:41:49
tags: [javascript]
categories:
keywords:
description:
---

# JavaScript

JavaScript（JS）是一种具有函数优先的轻量级，解释型或即时编译型的编译语言。JavaScript是一种基于原型编程、多范式动态脚本语言，并且支持面向对象、命令式和声明式风格。

JavaScript的标准是ECMAScript。截止2012年，所有的现代浏览器都完整的支持ECMAScript 5.1，旧版本的浏览器至少支持ECMAScript 3 标准。2015年6月17日，ECMA国际组织发布了 ECMAScript 的第六版，该版本正式名称为 ECMAScript 2015，但通常被称为 `ECMAScript 6` 或者 `ES6`。自此，ECMAScript 每年发布一次新标准。本文档目前覆盖了最新 ECMAScript 的草案，也就是 ECMAScript2020。

## 引入

内嵌脚本，使用`script标签`嵌入javascript代码

```
<script>
	alert('xxx');
</script>
```

外部文件

> 引用外部文件时，不要在当前标签中嵌入JavaScript代码。

```
<script src="index.js"></script>
```

推荐script标签放入body中的最后。

## 变量

定义变量

```
let myVar; //声明变量
myVar = 1;	//变量赋值

let myVar = 1; //声明的同时赋值
```

### 数据类型

| 变量    | 描述   | 示例                             |
| ------- | ------ | -------------------------------- |
| String  | 字符串 | let myVar = "xx";                |
| Number  | 数字   | let myVar = 1;                   |
| Boolean | 布尔值 | let myVar = true;                |
| Array   | 数组   | let myVar = [1,"ds",2];          |
| Object  | 对象   | let myVar = {name: "xx",age: 18} |

### 类型检查

#### typeof

返回原始类型

- Number/string/boolean
- function
- object
- undefined

#### Instanceof

**`instanceof`** 运算符用于检测构造函数的 `prototype` 属性是否出现在某个实例对象的原型链上。

```
let hd = [];
let houdunren = {};
console.log(hd instanceof Array); //true
console.log(houdunren instanceof Array); //false
```

### 隐式转换

基本上所有类型都可以隐式转换为Boolean类型。

| 数据类型  | true           | false            |
| --------- | -------------- | ---------------- |
| String    | 非空字符串     | 空字符串         |
| Number    | 非0的数值      | 0、NaN           |
| Array     | 数组不参与比较 | 参与比较的空数组 |
| Object    | 所有对象       |                  |
| undefined | 无             | undefined        |
| null      | 无             | null             |
| NaN       | 无             | NaN              |

### String

```
let a = new String("xxx");

let a = "xxx";

a.length	// 获取字符串的长度

a.toString()	//获取字符串

"Are" + " you" +"OK?" // 拼接字符串

a += "1234" // 在字符串上追加

function show(title) {
	return `xxx`;
}
console.log(`${show()}`)

a.toUpperCase // 全部转换为答谢

a.toLowerCase	// 全部转换为小写

a.trim()	//删除字符串左右的空白字符

a.trimLeft() //删除字符串的左边的空白

a.trimRight() //删除字符串右边的空白
 
a.charAt(3) // 通过index获取字符串中的字符

a[3] //通过下标也可以直接获取字符

// 截取字符串
let a = "zhongguoren";

console.log(a.slice(3)); // 获取index 3 之后的所有字符
console.log(a.slice(3,6));  //左闭右开, 获取index 3,4,5 字符
console.log(a.slice(3,-1)); // 获取index 3 到 index =1(表示最后一个字符的index) ，3之后的所有字符
console.log(a.slice(-2)); // 获取index -2 -1 ，最后两个字符


console.log(a.substring(3));  //左闭右开
console.log(a.substring(3,6));  //左闭右开, 获取index 3,4,5 字符
console.log(a.substring(3,-9)); // 将-9 转换为0， 相当于a.substring(3,0)


console.log(a.substr(3,0)) // 相当于a.substr(0,3)
console.log(a.substr(3,6));  // 从index 往后获取6位
console.log(a.substr(-3,2)); // 获取-3，-2 

// 查找字符串
console.log(a.indexOf("o")); // 查找字符串中第一个遇到o字符的位置
console.log(a.indexOf("o",3)); //从index 3之后开始找第一个遇到的0字符的位置 

console.log(a.lastIndexOf("o")); //逆向查找
console.log(a.lastIndexOf("o",7)); //从第index 7字符向前搜索


console.log(a.search("ren"));
console.log(a.search(/\.ren/i));


console.log(a.includes("ren")); // 判断是否包含子字符串
console.log(a.includes("ren", 5)); //从指定index 位置开始查询


console.log(a.startsWith("z")); //从第一个字符开始匹配，一旦有字符串不匹配返回false，否则返回true
console.log(a.startsWith("h",1)); // 指定从第几个index 开始匹配

console.log(a.endsWith("n")); //从最后一个字符开始往前匹配，不匹配返回false，否则返回true
console.log(a.endsWith("e", 10));

//替换字符串
let c = a.replace("zhongguo","jiangsu")
console.log(c);

// console.log(str.replace(/\//g, "-")); 可以使用正则表达式

// 重复生成
console.log("*".repeat(3));

// 分割字母
console.log(a.split("")); //将字符串转换成一个个字符，放在数组中

//将字符串转换为数组
console.log("1,2,3".split(",")) //[1,2,3]

let d = 11 + "10";
console.log(typeof d,d); //将Number转换成字符串再进行拼接
```

### Number

```
let a = new Number(3);

let a = 100;

//判断是否是整数
Number.isInteger(11);

//指定返回的小数位数可以四舍五入
(21.212).toFixed(2); //21.21

//提取字符串开始去除空白后的数字转为整数。
parseInt("  123dsds") // 123
parseInt("123.11"); 123

//转换字符串Wie浮点数，忽略字符串空白字符
console.log(parseFloat(" 11dsds")); 99
console.log(parseFloat("121.21")); 121.21

//获取最大值、最小值
console.log(Math.min(1,2,3));
console.log(Math.max(1,2,3));
console.log(Math.max.apple(Math,[1,2,3])); 

//舍入处理
console.log(Math.ceil(1.111));	// 向上取整

console.log(Math.floor(1.555));	// 向下取整

console.log(Math.round(1.5));	// 四舍五入处理

//随机数
const number = Math.floor(Math.random() * 5);	//0~5的随机数，不包括5
console.log(number);

const number = Math.floor(Math.random() * (5+1));	//返回0~5的随机数，包括5
console.log(number);

const number = Math.floor(Math.random() * (5 - 2)) + 2;
console.log(number);

//下面取2~5的随机数（不包括5）
const number = Math.floor(Math.random() * (5 - 2)) + 2;
console.log(number);

//下面取2~5的随机数
const number = Math.floor(Math.random() * (5 - 2 + 1)) + 2;
console.log(number);

//随机点名
let stus = ['小明', '张三', '王五', '爱情'];
let pos = Math.floor(Math.random() * stus.length);
console.log(stus[pos]);

//
let stus = ['小明', '张三', '王五', '爱情'];
let pos = Math.floor(Math.random() * (3-1)) + 1;
console.log(stus[pos]);

```

#### NaN

> 无效的数值

```
Number("dsjkds"); //NaN

Number.isNaN()	// 判断是否是NaN
```

#### 浮点精度处理

大部分变成语言在浮点数计算是都会有精度误差问题

```
let hd = 0.1 + 0.2
console.log(hd)// 结果：0.30000000000000004
```

处理方式

```
console.log((0.1 + 0.2).toFixed(2)) //0.3

console.log(1.0 - 0.9) //0.09999999999999998
console.log((1.0 - 0.9).toFixed(2)) //0.10
```

将小数转为整数进行计算后，再转为小数也可以解决精度问题

```
Number.prototype.add = function (num) {
	//取两个数值中小数位最大的
  let n1 = this.toString().split('.')[1].length
  let n2 = num.toString().split('.')[1].length
  
  //得到10的N次幂
  let m = Math.pow(10, Math.max(n1, n2))

  return (this * m + num * m) / m
}
console.log((0.1).add(0.2))
```

**推荐做法**

市面上已经存在很多针对数学计算的库 [mathjs](https://mathjs.org/examples/browser/basic_usage.html.html)、[decimal.js](http://mikemcl.github.io/decimal.js)等，我们就不需要自己构建了。下面来演示使用 [decimal.js](http://mikemcl.github.io/decimal.js)进行浮点计算。

```
<script src="https://cdn.bootcss.com/decimal.js/10.2.0/decimal.min.js"></script>

<script>
	console.log(Decimal.add(0.1, 0.2).valueOf())
</script>
```

#### Date

网站中处理时间是很常用的功能，通过Date类型提供的丰富功能可以非常方便的操作

```
let now = new Date();
console.log(now);
console.log(typeof date); //object
console.log(now * 1); //获取时间戳

//直接使用函数获取当前时间
console.log(Date());
console.log(typeof Date()); //string

//获取当前时间戳单位毫秒
console.log(Date.now());
```

计算脚本执行时间

```
const start = Date.now();
for (let i = 0; i < 2000000; i++) {}
const end = Date.now();
console.log(end - start);
```

当前也可以使用控制台测试

```
console.time("testFor");
for (let i = 0; i < 20000000; i++) {}
console.timeEnd("testFor");
```

根据指定的日期与时间定义日期对象

```
let now = new Date('2028-02-22 03:25:02');
console.log(now);

now = new Date(2028, 4, 5, 1, 22, 16);
console.log(now);
```

使用展示运算符处理更方便

```
let info = [2020, 2, 20, 10, 15, 32];
let date = new Date(...info);
console.dir(date);
```

类型转换

将日期转为数值类型就是转为时间戳单位是毫秒

```
let hd = new Date("2020-2-22 10:33:12");
console.log(hd * 1);

console.log(Number(hd));

console.log(hd.valueOf())

console.log(date.getTime());
```

将时间戳转换为标准日期的方法

```
const param = [1990, 2, 22, 13, 22, 19];
const date = new Date(...param);
const timestamp = date.getTime();
console.log(timestamp);
console.log(new Date(timestamp));
```

对象方法

```
//格式化输出日期
let time = new Date();
console.log(
  `${time.getFullYear()}-${time.getMonth()}-${time.getDate()} ${time.getHours()}:${time.getMinutes()}:${time.getSeconds()}`
);
```

封装函数用于复用

```
function dateFormat(date, format = "YYYY-MM-DD HH:mm:ss") {
  const config = {
    YYYY: date.getFullYear(),
    MM: date.getMonth() + 1,
    DD: date.getDate(),
    HH: date.getHours(),
    mm: date.getMinutes(),
    ss: date.getSeconds()
  };
  for (const key in config) {
    format = format.replace(key, config[key]);
  }
  return format;
}
console.log(dateFormat(new Date(), "YYYY年MM月DD日"));
```

下面是系统提供的日期时间方法，更多方法请查看 [MDN官网](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date)

#### moment.js

Moment.js是一个轻量级的JavaScript时间库，它方便了日常开发中对时间的操作，提高了开发效率。

### 数组类型

创建数组

```
new Array(1,2,3);

const array = ["ds","ddd"]

const array = [["hdcms"], ["houdunren"]];
```

方法

```
const array = ["ds","ddd"];

array.length;
```

Array.of

```
let hd = Array.of(3);
console.log(hd);

hd = Array.of(1,2,3);
console.log(hd);
```

类型检测

```
Array.isArray([1,"后盾人","hdcms"]);
Array.isArray(9);
```

字符串

 大部分数据类型都可以使用，.toString() 函数转换为字符串

```
console.log(([1, 2, 3]).toString()); // 1,2,3
```

也可以使用函数String转换为字符串

```
console.log(String([1,2,3]))
```

或使用join连接字符串

```
[1,2,3].join("-");
```



#### Array.from

使用Array.from 可将类数组转换为数组，类数组指包含length 属性或可迭代的对象

- 第一个参数为要转换为数据，第二个参数为类似于map函数的回调


```
let str = 'xxx';
console.log(Array.from(str)); //["x", "x", "x"]
```

#### 数组合并

```
let a = [1, 2, 3];
let b = ['a', 'xx', ...a];
console.log(b); //["a", "xx", 1, 2, 3]


function hd(...args) {
  console.log(args);
}
hd(1, 2, 3, "xx"); //[1, 2, 3, "xx"]

function hd(site, ...args) {
  console.log(site, args); //xx (3) [1, 2, 3]
}
hd("xx", 1, 2, 3);
```

#### 解构赋值

```
let [name,url] = ["xx","123"];
console.log(name);

function hd() {
	return ['houdunren', 'hdcms'];
}
let [a, b] = hd();
console.log(a); //houdunren

let [a, ...b] = ['xx', 'houdunren', 'hdcms'];
console.log(b);

let web = "后盾人";
[web, url] = ["hdcms.com", "houdunren.com"];
console.log(web);
```

字符串解构

```
const [...a] = "houdunren.com";
console.log(a); //Array(13)
```

```
let [,url]=['后盾人','houdunren.com'];
console.log(url);//houdunren.com

let [name, ...arr] = ['后盾人', 'hdcms', 'houdunren.com'];
console.log(name, arr); //后盾人 (2) ["hdcms", "houdunren.com"]
```

数组参数

```
function hd([a, b]) {
	console.log(a, b);
}
hd(['后盾人', 'hdcms']);
```

#### 循环

```
lessons.forEach((item, index, array) => {
    item.title = item.title.substr(0, 5);
});let a = [1,2,3,4,5];

for (let i = 0; i < a.length; ++i) {
	console.log(a[i]);
	a[i] = 1;
}


a.forEach((item, index, array) => {

});

for (const key in a) {
    
}

for (const item of a) {}

for (const [key, value] of a.entries()) {}
```





## JavaScript中函数定义方式

函数声明

```javascript
function func(param){
//somethings
}
```

函数表达式

```javascript
var func = function(a,b) {
	//somthings
}
```

函数构造函数

```javascript
var func = new Function('param1','parma2','somethings');

var x = func(1,2);
```

自调用函数 （不需要调用自己会执行）

```javascript
(function () {
	//somethings
})();
```

箭头函数

```javascript
const func = (params) => {
	//函数体
}
```

## 类

> JavaScript语言中，生成示例对象的传统方法是通过构造函数。

```javascript
function person(weight, height) {
  this.weight = weight;
  this.height = height;
}

person.prototype.toString = function () {
  return '(' + this.weight + ', ' + this.height + ')';
};

var b = new person(100, 200);
console.log(b.weight);	//100
console.log(b.height);	//200
console.log(b.toString());	//(100,200)
```

这种写法和传统的面向对象语言（C++和java）差异很大，明明是一个函数怎么变成了类，很容易让人感到困惑。

### class

`ES6`的`class`可以看作只是一个语法糖，它的绝大部分功能，ES5都可以做到，新的`class`写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

```javascript
class person{
  //构造函数
	constructor(weight,height) {
		this.weight = weight;
  	this.height = height;
	}
  
  //成员函数
  toString() {
    return '(' + this.weight + ', ' + this.height + ')';
  }
}
console.log(b.weight);	//100
console.log(b.height);	//200
console.log(b.toString());	//(100,200)
console.log(typeof person)	//function
console.log(person.prototype.constructor == b.constructor)	//true
```

这两种方式是一样的。

### 类的声明

```javascript
// 正常声明一个类
class person {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
// 匿名一个类
let person1 = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
// 具名一个类
let person2 = class person {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

### prototype

prototype属性，在ES6的类上面继续存在，事实上，类的所有方法都定义在类的prototype属性上。

可以通过prototype对象`添加类的方法`

```javascript
person.prototype = {
	constructor() {},
  toString() {},
  toValue() {},
}
```

`object.assign`方法也可以很方便地一次向类`添加多个方法`。

```
Object.assign(person.prototype, {
  toString(){},
  toValue(){}
});
```

`deleteProperty`

```
Reflect.deleteProperty(person.prototype, 'toString')
```

`prototype`对象的`constructor`属性，直接指向`类`的本身，这与 ES5 的行为是一致的。

```
person.prototype.constructor === person
```

### constructor

`constructor`方法是类的默认方法，通过`new`命令生成对象实例时，自动调用该方法。一个类必须有`constructor`方法，如果没有显示定义，一个空的constructor方法会被默认添加。

### 类的实例

```javascript
//定义类
class person {

  constructor(x, y) {
    this.weight = x;
    this.height = y;
  }

  toString() {
    return '(' + this.weight + ', ' + this.height + ')';
  }

}

var person_obj = new person(2, 3);

person_obj.toString() // (2, 3)

person_obj.hasOwnProperty('weight') // true
person_obj.hasOwnProperty('height') // true
person_obj.hasOwnProperty('toString') // false
person_obj.__proto__.hasOwnProperty('toString') // true
```

![image-20210122103451604](https://gitee.com/Cooper001/blog-img/raw/master/img/image-20210122103451604.png)

x和y都是实例对象person自身的属性(因为定义在this变量上)，所以`hasOwnProperty`方法返回true，而toString是原型对象的属性，所以返回false。

![image-20210124162001072](https://gitee.com/Cooper001/blog-img/raw/master/img/image-20210124162001072.png)



### static

> 静态属性，class本身的属性，即直接定义在类内部的属性，不需要实例化

```javascript
//声明一个带有静态属性的类
class person {
	static a = 1;
}

//类本身可以直接调用
person.a; // 1
person.b = 2;
person.b; // 2
```

> 通过new关键字生成的对象，无法调用该方法

```javascript
class Point {
  constructor(x, y) {
    this.x = x
    this.y = y
  }

  static distance(a, b) {
    const dx = a.x - b.x
    const dy = a.y - b.y
    return Math.hypot(dx, dy) // 毕达哥拉斯定理
  }
}

const p1 = new Point(5, 5)
const p2 = new Point(10, 10)
console.log(p1);
console.log(p2);
console.log(Point.distance(p1, p2)) // 7.0710678118654755
```

> 在p1、p2对象中找不到静态方法distance

### name

该属性能获取或者返回class的类名

```
var a = new person();
console.log(a.name);
```

### get和set

下面我们通过get Dheight中获取两倍的height，set Dheight中缩小两倍存入height

```javascript
class person {
constructor(weight, height) {
  this.height = height;
  this.weight = weight;
  }

  get Dheight() {
  	return this.height * 2;
  }

  set Dheight(value) {
  this.height = value / 2;
  }
}
var obj = new person(100, 200);
console.log(obj.height);
console.log(obj.Dheight);
obj.Dheight = 400;
console.log(obj.height);
```

```javascript
class A {
  constructor(a, b) {
    this.a = a;
    this.b = b;
  }

  get a() {
    console.log("getter");
    return this._a;
  }
  set a(value) {
      console.log("setter");
      this._a = value;
  }
}
var obj = new A(1, 2);
console.log(obj);
```

> getter不可单独出现

```javascript
class Father {
  constructor() {}
  get a() {
    return this._a
  }
}
class Child extends Father {
  constructor() {
    super()
  }
  set a(a) {
    this._a = a
  }
}
let test = new Child()
test.a = 2
console.log(test.a) // undefined

class Father1 {
  constructor() {}
  // 或者都放在子类中
  get a() {
    return this._a
  }
  set a(a) {
    this._a = a
  }
}
class Child1 extends Father1 {
  constructor() {
    super()
  }
}
let test1 = new Child1()
test1.a = 2
console.log(test1.a) // 2
```

> getter 与 setter 必须同级出现

### 静态方法、原型方法与实例方法

```javascript
// 静态
class StaticFunc {
  static sum(a, b) {
    console.log(a + b)
  }
}
// 调用方式
StaticFunc.sum(1, 2) // 3

// 原型
class PrototypeFunc {
  sum(a, b) {
    console.log(a + b)
  }
}
const protoFunc = new PrototypeFunc()
protoFunc.sum(1, 2) // 3

// 实例
class InstanceFunc {
  constructor() {
    this.sum = (a, b) => {
      console.log(a + b)
    }
  }
}
// 实例化时被调用，为实例化对象增加方法
const instanceFunc = new InstanceFunc()
instanceFunc.sum(1, 2) // 3
```

### 创建子类

```javascript
class human {
  constructor(weight, height) {
    this.weight = weight;
    this.height = height;
  }

  speck() {
  	console.log(this.weight);
  }
}

class man extends human {
  listen() {
  	console.log(this.height);
  }
}

var a = new man(100, 100);
console.log(a);
```

### super

```javascript
class Cat {
  constructor(name) {
  	this.name = name
  }

  speck() {
  	console.log(this.name)
  }
}

class Lion extends Cat {
  listen() {
  	super.speck()
  }
}
let l = new Lion('Mickey')
l.speck() // 'Mickey'
l.listen() // 'Mickey'
```











