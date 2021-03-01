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











