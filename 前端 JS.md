# JavaScript 基础

## 循环

### for 循环
```JS
for (初始化变量; 条件表达式; 操作表达式) {
	循环体
}

for (var i = 1; i <= 100; i++) {
	console.log('你好吗');
}
```

### 双重 for 循环
```JS
for (外层的初始化变量; 外层的条件表达式; 外层的操作表达式) {
	for (里层的初始化变量; 里层的条件表达式; 里层的操作表达式) {
		执行语句;
	}
}

for (var i = 1; i <= 3; i++) {
	console.log('这是外层循环第' + i + '次');
	for (var j = 1; j <= 3; j++) {
		console.log('这是里层的循环第' + j + '次');
	}
}
```

### While 循环
```JS
while (条件表达式) {
	循环体
}

// 例子1
var num = 1;
	while (num <= 100) {
		console.log('好啊有');
		num++;
	}

// 例子2
var message = prompt('你爱我吗?');
	while (message !== '我爱你') {
		message = prompt('你爱我吗?');
	}
alert('我也爱你啊！');
```

### Do While 循环
```JS
// do while 先执行一次循环体 在判断条件 如果条件表达式结果为真，则继续执行循环体，否则退出循环
do {
	// 循环体
} while (条件表达式)

// 例子1
var i = 1;
do {
	console.log('how are you?');
	i++;
} while (i <= 100)

// 例子2
do {
	var message = prompt('你爱我吗?');
} while (message !== '我爱你')
alert('我也爱你啊');
```

### Continue 关键字
```JS
// 退出本次（当前次的循环）继续执行剩余次数循环

// 例子1
for (var i = 1; i <= 5; i++) {
	if (i == 3) {
		continue; // 只要遇见 continue就退出本次循环 直接跳到 i++
	}
	console.log('我正在吃第' + i + '个包子');
}

// 例子2
// 求1~100 之间， 除了能被7整除之外的整数和 
var sum = 0;
for (var i = 1; i <= 100; i++) {
	if (i % 7 == 0) {
		continue;
	}
	sum += i;
}
console.log(sum);
```

### Break 关键字
```JS
// break 退出整个循环
for (var i = 1; i <= 5; i++) {
	if (i == 3) {
		break;
	}
	console.log('我正在吃第' + i + '个包子');
}
```

## 数组
```JS
// 1. 数组(Array) ：就是一组数据的集合 存储在单个变量下
// 2. 利用new 创建数组
var arr = new Array(); // 创建了一个空的数组
// 3. 利用数组字面量创建数组 []
var arr = []; // 创建了一个空的数组
var arr1 = [1, 2, 'pink老师', true];
// 4. 我们数组里面的数据一定用逗号分隔
// 5. 数组里面的数据 比如1,2， 我们称为数组元素
// 6. 获取数组元素  格式 数组名[索引号]  索引号从 0开始
console.log(arr1);
console.log(arr1[2]); // pink老师
console.log(arr1[3]); // true
console.log(arr2[4]); // 因为没有这个数组元素 所以输出的结果是 undefined
```

### 遍历数组
```JS
var arr = ['red', 'green', 'blue'];
for (var i = 0; i < 3; i++) {
	console.log(arr[i]);
}
```

### 数组长度
```JS
// arr.length 动态监测数组元素的个数
var arr = ['关羽', '张飞', '马超', '赵云', '黄忠', '刘备', '姜维', 'pink'];
for (var i = 0; i < arr.length; i++) {
	console.log(arr[i]);
}

// 将数组 ['red', 'green', 'blue', 'pink'] 转换为字符串，并且用 | 或其他符号分割
var arr = ['red', 'green', 'blue', 'pink'];
var str = '';
var sep = '|';
for (var i = 0; i < arr.length; i++) {
	str += arr[i] + sep;
}
console.log(str);
```

### 新增数组元素
```JS
// 1. 新增数组元素 修改length长度 
var arr = ['red', 'green', 'blue'];
console.log(arr.length);
arr.length = 5; // 把我们数组的长度修改为了 5  里面应该有5个元素 
console.log(arr);
console.log(arr[3]); // undefined
console.log(arr[4]); // undefined

// 2. 新增数组元素 修改索引号 追加数组元素
var arr1 = ['red', 'green', 'blue'];
arr1[3] = 'pink';
arr1[4] = 'hotpink';
arr1[0] = 'yellow'; // 这里是替换原来的数组元素
console.log(arr1);
arr1 = '有点意思';
console.log(arr1); // 不要直接给 数组名赋值 否则里面的数组元素都没有了

// 新建一个数组，里面存放100个整数
var arr = [];
for (var i = 0; i < 100; i++) {
	// arr = i; 不要直接给数组名赋值 否则以前的元素都没了
	arr[i] = i + 1;
}
console.log(arr);
```

### 筛选数组元素
```JS
// 将数组 [2, 0, 6, 1, 77, 0, 52, 0, 25, 7] 中大于等于 10 的元素选出来，放入新数组。
// 方法1
var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
var newArr = [];
var j = 0;
for (var i = 0; i < arr.length; i++) {
	if (arr[i] >= 10) {
		// 新数组索引号应该从0开始 依次递增
		newArr[j] = arr[i];
		j++;
	}
}

// 方法2
var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
var newArr = [];
// 刚开始 newArr.length 就是 0
for (var i = 0; i < arr.length; i++) {
	if (arr[i] >= 10) {
		// 新数组索引号应该从0开始 依次递增
		newArr[newArr.length] = arr[i];
	}
}
```

## 函数
```JS
// 1. 声明函数
function 函数名(形参1,形参2，……) {
	函数体
}
// 2. 调用函数
函数名(实参1,实参2，……);
// 如果实参的个数多于形参的个数  多余的实参会省略
// 如果实参的个数小于形参的个数  多于的形参定义为undefined  最终的结果就是 NaN

// 例子 利用函数计算1-100之间的累加和 
// 1. 声明函数
function getSum() {
	var sum = 0;
	for (var i = 1; i <= 100; i++) {
		sum += i;
	}
	console.log(sum);
}
// 2. 调用函数
getSum();

// 例2：
// 利用函数翻转任意数组 reverse 翻转
function reverse(arr) {
	var newArr = [];
	for (var i = arr.length - 1; i >= 0; i--) {
		newArr[newArr.length] = arr[i];
	}
	return newArr;
}
var arr1 = reverse([1, 3, 4, 6, 9]);
console.log(arr1);
```

### 函数返回值
```JS
// 函数的返回值格式
function 函数名() {
	return 需要返回的结果;
}
函数名();

// 例1：
// 利用函数 求两个数的最大值
function getMax(num1, num2) {
	// if (num1 > num2) {
	//     return num1;
	// } else {
	//     return num2;
	// }
	return num1 > num2 ? num1 : num2;  // 三元运算
}
console.log(getMax(1, 3));

// 例2：
// 利用函数求数组 [5,2,99,101,67,77] 中的最大数值。
function getArrMax(arr) { // arr 接受一个数组  arr =  [5,2,99,101,67,77]
	var max = arr[0];
	for (var i = 1; i <= arr.length; i++) {
		if (arr[i] > max) {
			max = arr[i];
		}
	}
	return max;
}
// getArrMax([5, 2, 99, 101, 67, 77]); // 实参是一个数组送过去
// 在我们实际开发里面，我们经常用一个变量来接受 函数的返回结果 使用更简单
var re = getArrMax([5, 2, 99, 101, 67, 77]);
console.log(re);
```
返回值注意事项：
- return 终止函数
- return 只能返回一个值
```JS
function fn(num1, num2) {
	return num1, num2; // 返回的结果是最后一个值
}
console.log(fn(1, 2));
```
- 利用数组返回多个值
```JS
function getResult(num1, num2) {
	return [num1 + num2, num1 - num2, num1 * num2, num1 / num2];
}
var re = getResult(1, 2); // 返回的是一个数组
console.log(re);
```
- 如果函数没有 return 则返回undefined
```JS
function fun2() {

}
console.log(fun2()); // 函数返回的结果是 undefined
```

### arguments 参数
只有函数才有 arguments 对象  而且是每个函数都内置好了这个 arguments，arguments 返回的是伪数组，伪数组并不是真正意义上的数组，伪数组的特点：
	1. 具有数组的 length 属性
	2. 按照索引的方式进行存储的
	3. 它没有真正数组的一些方法 pop()  push() 等等
```JS
function fn() {
	// console.log(arguments); // 里面存储了所有传递过来的实参  arguments = [1,2,3]
	// 我们可以按照数组的方式遍历arguments
	for (var i = 0; i < arguments.length; i++) {
		console.log(arguments[i]);
	}
}
fn(1, 2, 3);

// 例1：
// 利用函数求任意个数的最大值
function getMax() { // arguments = [1,2,3]
	var max = arguments[0];
	for (var i = 1; i < arguments.length; i++) {
		if (arguments[i] > max) {
			max = arguments[i];
		}
	}
	return max;
}
console.log(getMax(1, 2, 3));
```

### 函数调用
```JS
function fn1() {
     console.log(11);
     fn2(); // 在fn1 函数里面调用了 fn2 函数
 }
 fn1();
 function fn2() {
     console.log(22);
 }

// 例
// 用户输入年份，输出当前年份2月份的天数
function backDay() {
	var year = prompt('请您输入年份:');
	if (isRunYear(year)) { // 调用函数需要加小括号
		alert('当前年份是闰年2月份有29天');
	} else {
		alert('当前年份是平年2月份有28天');
	}
}
backDay();

// 判断是否为闰年的函数
function isRunYear(year) {
	// 如果是闰年我们返回 true  否则 返回 false 
	var flag = false;
	if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
		flag = true;
	}
	return flag;
}
```

### 函数声明方式
```JS
// 1. 利用函数关键字自定义函数(命名函数)
function fn() {

}
fn();
// 2. 函数表达式(匿名函数) 
// var 变量名 = function() {};
var fun = function(aru) {
	console.log('我是函数表达式');
	console.log(aru);
}
fun('pink老师');
// (1) fun是变量名 不是函数名  
// (2) 函数表达式声明方式跟声明变量差不多，只不过变量里面存的是值,而函数表达式里面存的是函数
// (3) 函数表达式也可以进行传递参数
```

## 作用域
JavaScript作用域 ： 就是代码名字（变量）在某个范围内起作用和效果 目的是为了提高程序的可靠性更重要的是减少命名冲突
全局作用域： 整个script标签 或者是一个单独的js文件
```JS
var num = 10;
var num = 30;
console.log(num);
```
局部作用域（函数作用域）：在函数内部就是局部作用域 这个代码的名字只在函数内部起效果和作用
```JS
function fn() {
	// 局部作用域
	var num = 20;
	console.log(num);
}
fn();
```

### 变量的作用域
变量的作用域：根据作用域的不同我们变量分为全局变量和局部变量
全局变量：在全局作用域下的变量 在全局下都可以使用
**注意 如果在函数内部 没有声明直接赋值的变量也属于全局变量**
```JS
function fun(aru) {
	var num1 = 10; // num1就是局部变量 只能在函数内部使用
	num2 = 20;  // num2是全局变量
}
fun();
console.log(num1);  // 不能打印
console.log(num2);  // 能打印
```

### 预解析
1. 我们js引擎运行js 分为两步：  预解析  代码执行
	(1) 预解析 js引擎会把js 里面所有的 var  还有 function 提升到当前作用域的最前面
	(2) 代码执行  按照代码书写的顺序从上往下执行
2. 预解析分为 变量预解析（变量提升） 和 函数预解析（函数提升）
	(1) 变量提升 就是把所有的变量声明提升到当前的作用域最前面  不提升赋值操作
	(2) 函数提升 就是把所有的函数声明提升到当前作用域的最前面  不调用函数
```JS
// 坑1
console.log(num); // undefined  
var num = 10;
// 相当于执行了以下代码
var num;
console.log(num);
num = 10;

// 坑2
fun(); // 报错  坑2 
var fun = function() {
	console.log(22);
}
// 函数表达式 调用必须写在函数表达式的下面
// 相当于执行了以下代码
var fun;
fun();
fun = function() {
	console.log(22)
}
```

```JS
// 案例1
var num = 10;
fun();
function fun() {
    console.log(num);
    var num = 20;
}
// 相当于执行了以下操作
var num;
function fun() {
    var num;
    console.log(num);
    num = 20;
}
num = 10;
fun();

// 案例2
f1();
console.log(c);
console.log(b);
console.log(a);
function f1() {
	var a = b = c = 9;
	console.log(a);
	console.log(b);
	console.log(c);
}
// 相当于执行了以下操作
function f1() {
    var a;
    a = b = c = 9;
    // 相当于 var  a  = 9; b = 9; c = 9; b 和 c 直接赋值 没有var 声明 当 全局变量看
    // 集体声明  var a = 9, b = 9, c = 9;
    console.log(a);
    console.log(b);
    console.log(c);
}
f1();
console.log(c);  // 9
console.log(b);  // 9
console.log(a);  // undefined
```

## 自定义对象
```JS
var obj = {};  // 创建了一个空的对象

// 例子
var obj = {
	uname: '张三疯',
	age: 18,
	sex: '男',
	sayHi: function() {
		console.log('hi~');
	}
}
console.log(obj.uname);
console.log(obj['age']);
obj.sayHi();
```
 
创建对象
	(1) 里面的属性或者方法我们采取键值对的形式  键 属性名 ： 值  属性值 
	(2) 多个属性或者方法中间用逗号隔开的
	(3) 方法冒号后面跟的是一个匿名函数
使用对象
	(1) 调用对象的属性 我们采取 对象名.属性名 . 我们理解为 的
	(2) 调用属性还有一种方法 对象名['属性名']
	(3) 调用对象的方法 sayHi   对象名.方法名() 千万别忘记添加小括号

### 创建对象
```JS
// 利用 new Object 创建对象
var obj = new Object(); // 创建了一个空的对象
obj.uname = '张三疯';
obj.age = 18;
obj.sex = '男';
obj.sayHi = function() {
		console.log('hi~');
	}
```
(1) 我们是利用 等号 = 赋值的方法 添加对象的属性和方法
(2) 每个属性和方法之间用 分号结束

### 构造函数创建对象
把对象里面一些相同的属性和方法抽象出来封装到函数里面
```JS
// 构造函数的语法格式
function 构造函数名() {
	this.属性 = 值;
    this.方法 = function() {}
}
new 构造函数名();

// 例子
function Star(uname, age, sex) {
	this.name = uname;
	this.age = age;
	this.sex = sex;
	this.sing = function(sang) {
		console.log(sang);
	}
}
var ldh = new Star('刘德华', 18, '男'); // 调用函数返回的是一个对象
console.log(ldh.name);
console.log(ldh['sex']);
ldh.sing('冰雨');
var zxy = new Star('张学友', 19, '男');
console.log(zxy.name);
console.log(zxy.age);
zxy.sing('李香兰')
```
1. 构造函数名字首字母要大写
2. 构造函数不需要return 就可以返回结果
3. 调用构造函数 必须使用 new
4. 属性和方法前面必须添加 this

### 封装对象
利用对象封装自己的数学对象  里面有 PI 最大值和最小值
```JS
var myMath = {
	PI: 3.141592653,
	max: function() {
		var max = arguments[0];
		for (var i = 1; i < arguments.length; i++) {
			if (arguments[i] > max) {
				max = arguments[i];
			}
		}
		return max;
	},
	min: function() {
		var min = arguments[0];
		for (var i = 1; i < arguments.length; i++) {
			if (arguments[i] < min) {
				min = arguments[i];
			}
		}
		return min;
	}
}
console.log(myMath.PI);
console.log(myMath.max(1, 5, 9));
console.log(myMath.min(1, 5, 9));
```

### 遍历属性
```JS
var obj = {
	name: 'pink老师',
	age: 18,
	sex: '男',
	fn: function() {}
}
// for in 遍历我们的对象
// 	for (变量 in 对象) {
// }
for (var k in obj) {
	console.log(k); // k 变量 输出  得到的是 属性名
	console.log(obj[k]); // obj[k] 得到是 属性值
}
```
for in 里面的变量 我们喜欢写 k  或者  key

## 内置对象
JS自带的一些对象，提供了常用的基本功能

### Math 对象
Math数学对象 不是一个构造函数 ，所以我们不需要new 来调用 而是直接使用里面的属性和方法即可
```JS
console.log(Math.PI); // 一个属性 圆周率
console.log(Math.max(1, 99, 3)); // 99
console.log(Math.max(-1, -10)); // -1
console.log(Math.max(1, 99, 'pink老师')); // NaN
console.log(Math.max()); // -Infinity
```

#### 绝对值方法
```JS
console.log(Math.abs(1)); // 1
console.log(Math.abs(-1)); // 1
console.log(Math.abs('-1')); // 隐式转换 会把字符串型 -1 转换为数字型
console.log(Math.abs('pink')); // NaN 
```

#### 取整方法
(1) Math.floor()   地板 向下取整  往最小了取值
```JS
console.log(Math.floor(1.1)); // 1
console.log(Math.floor(1.9)); // 1
```

(2) Math.ceil()   ceil 天花板 向上取整  往最大了取值
```JS
console.log(Math.ceil(1.1)); // 2
console.log(Math.ceil(1.9)); // 2
```

(3) Math.round()   四舍五入  其他数字都是四舍五入，但是 .5 特殊 它往大了取  
```JS
console.log(Math.round(1.1)); // 1
console.log(Math.round(1.5)); // 2
console.log(Math.round(1.9)); // 2
console.log(Math.round(-1.1)); // -1
console.log(Math.round(-1.5)); // 这个结果是 -1
```

#### 随机数方法
Math对象随机数方法   random() 返回一个随机的小数  0 =< x < 1，这个方法里面不跟参数
```JS
console.log(Math.random());

// 两个数之间的随机整数 并且 包含这2个整数
function getRandom(min, max) {
	return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log(getRandom(1, 10));

// 随机点名
var arr = ['张三', '张三丰', '张三疯子', '李四', '李思思', 'pink老师'];
console.log(arr[getRandom(0, arr.length - 1)]);
```

### Date 对象
Date() 日期对象 是一个构造函数，必须使用new 来调用创建我们的日期对象
```JS
// 1. 使用Date  如果没有参数 返回当前系统的当前时间
var date = new Date();
console.log(date);

// 2. 参数常用的写法  数字型  2019, 10, 01  或者是 字符串型 '2019-10-1 8:8:8'
var date1 = new Date(2019, 10, 1);
console.log(date1); // 返回的是 11月 不是 10月 
var date2 = new Date('2019-10-1 8:8:8');
console.log(date2);
```

#### 日期格式化
```JS
// 格式化日期 年月日 
var date = new Date();
console.log(date.getFullYear()); // 返回当前日期的年  2019
console.log(date.getMonth() + 1); // 月份 返回的月份小1个月   记得月份+1 
console.log(date.getDate()); // 返回的是 几号
console.log(date.getDay()); // 周一返回的是1 周六返回的是6 但是 周日返回的是0

// 我们写一个 2019年 5月 1日 星期三
var year = date.getFullYear();
var month = date.getMonth() + 1;
var dates = date.getDate();
var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
var day = date.getDay();
console.log('今天是：' + year + '年' + month + '月' + dates + '日 ' + arr[day]);


// 格式化日期 时分秒
console.log(date.getHours()); // 时
console.log(date.getMinutes()); // 分
console.log(date.getSeconds()); // 秒

// 要求封装一个函数返回当前的时分秒 格式 08:08:08
function getTimer() {
	var time = new Date();
	var h = time.getHours();
	h = h < 10 ? '0' + h : h;
	var m = time.getMinutes();
	m = m < 10 ? '0' + m : m;
	var s = time.getSeconds();
	s = s < 10 ? '0' + s : s;
	return h + ':' + m + ':' + s;
}
console.log(getTimer());
```

#### 毫秒
获得Date总的毫秒数(时间戳)  不是当前时间的毫秒数 而是距离1970年1月1号过了多少毫秒数
```JS
// 1. 通过 valueOf()  getTime()
var date = new Date();
console.log(date.valueOf()); // 就是 我们现在时间 距离1970.1.1 总的毫秒数
console.log(date.getTime());
// 2. 简单的写法 (最常用的写法)
var date1 = +new Date(); // +new Date()  返回的就是总的毫秒数
console.log(date1);
// 3. H5 新增的 获得总的毫秒数
console.log(Date.now());
```

倒计时案例
```JS
// 2.用时间戳来做。用户输入时间总的毫秒数减去现在时间的总的毫秒数，得到的就是剩余时间的毫秒数。
// 3.把剩余时间总的毫秒数转换为天、时、分、秒 （时间戳转换为时分秒）
// 转换公式如下： 
//  d = parseInt(总秒数/ 60/60 /24);    //  计算天数
//  h = parseInt(总秒数/ 60/60 %24)   //   计算小时
//  m = parseInt(总秒数 /60 %60 );     //   计算分数
//  s = parseInt(总秒数%60);            //   计算当前秒数
function countDown(time) {
	var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
	var inputTime = +new Date(time); // 返回的是用户输入时间总的毫秒数
	var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数
	d = d < 10 ? '0' + d : d;
	var h = parseInt(times / 60 / 60 % 24); //时
	h = h < 10 ? '0' + h : h;
	var m = parseInt(times / 60 % 60); // 分
	m = m < 10 ? '0' + m : m;
	var s = parseInt(times % 60); // 当前的秒
	s = s < 10 ? '0' + s : s;
	return d + '天' + h + '时' + m + '分' + s + '秒';
}
console.log(countDown('2019-5-1 18:00:00'));
var date = new Date();
console.log(date);
```

### 数组对象

#### 创建数组
创建数组的两种方式
```JS
// 1. 利用数组字面量
var arr = [1, 2, 3];
console.log(arr[0]);

// 2. 利用new Array()
// var arr1 = new Array();  // 创建了一个空的数组
// var arr1 = new Array(2);  // 这个2 表示 数组的长度为 2  里面有2个空的数组元素 
var arr1 = new Array(2, 3); // 等价于 [2,3]  这样写表示 里面有2个数组元素 是 2和3
console.log(arr1);
```

#### 检测是否为数组
1. instanceof  运算符 它可以用来检测是否为数组
```JS
var arr = [];
var obj = {};
console.log(arr instanceof Array);
console.log(obj instanceof Array);
```
2. Array.isArray(参数);  H5新增的方法  ie9以上版本支持
```JS
console.log(Array.isArray(arr));
console.log(Array.isArray(obj));
```

#### 添加/删除数组元素
- 添加元素
	- push() 在我们数组的末尾 添加一个或者多个数组元素
		- (1) push 是可以给数组追加新的元素
		- (2) push() 参数直接写 数组元素就可以了
		- (3) push完毕之后，返回的结果是 新数组的长度
		- (4) 原数组也会发生变化
	- unshift 在我们数组的开头 添加一个或者多个数组元素
		- (1) unshift是可以给数组前面追加新的元素
		- (2) unshift() 参数直接写 数组元素就可以了
		- (3) unshift完毕之后，返回的结果是 新数组的长度 
		- (4) 原数组也会发生变化
```JS
var arr = [1, 2, 3];
console.log(arr.push(4, 'pink'));
console.log(arr.unshift('red', 'purple'));
```
- 删除元素
	- pop() 它可以删除数组的最后一个元素
		- (1) pop是可以删除数组的最后一个元素 一次只能删除一个元素
		- (2) pop() 没有参数
		- (3) pop完毕之后，返回的结果是 删除的那个元素 
		- (4) 原数组也会发生变化
	- shift() 它可以删除数组的第一个元素
		- (1) shift是可以删除数组的第一个元素 一次只能删除一个元素
		- (2) shift() 没有参数
		- (3) shift完毕之后，返回的结果是 删除的那个元素 
		- (4) 原数组也会发生变化
```JS
console.log(arr.pop());
console.log(arr);
console.log(arr.shift());
console.log(arr);
```

案例
```JS
// 有一个包含工资的数组[1500, 1200, 2000, 2100, 1800]，要求把数组中工资超过2000的删除，剩余的放到新数组里面
var arr = [1500, 1200, 2000, 2100, 1800];
var newArr = [];
for (var i = 0; i < arr.length; i++) {
	if (arr[i] < 2000) {
		// newArr[newArr.length] = arr[i];
		newArr.push(arr[i]);
	}
}
console.log(newArr);
```

#### 数组排序
- 翻转数组 reverse
```JS
var arr = ['pink', 'red', 'blue'];
arr.reverse();
console.log(arr);
```
- 冒泡排序
```JS
var arr1 = [13, 4, 77, 1, 7];
arr1.sort(function(a, b) {
	//  return a - b; 升序的顺序排列
	return b - a; // 降序的顺序排列
});
console.log(arr1);
```

#### 数组索引方法
indexOf(数组元素)  返回数组元素索引号方法 作用就是返回该数组元素的索引号 从前面开始查找
- 只返回第一个满足条件的索引号
- 如果在该数组里面找不到元素，则返回的是 -1
```JS
var arr = ['red', 'green', 'pink'];
console.log(arr.indexOf('blue'));
```
lastIndexOf(数组元素)  作用就是返回该数组元素的索引号 从后面开始查找
```JS
var arr = ['red', 'green', 'blue', 'pink', 'blue'];
console.log(arr.lastIndexOf('blue')); // 4
```

#### 数组去重
数组去重 ['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b'] 要求去除数组中重复的元素。
1.目标： 把旧数组里面不重复的元素选取出来放到新数组中， 重复的元素只保留一个， 放到新数组中去重。
2.核心算法： 我们遍历旧数组， 然后拿着旧数组元素去查询新数组， 如果该元素在新数组里面没有出现过， 我们就添加， 否则不添加。
3.我们怎么知道该元素没有存在？ 利用 新数组.indexOf(数组元素) 如果返回时 - 1 就说明 新数组里面没有改元素
封装一个 去重的函数 unique
```JS
function unique(arr) {
	var newArr = [];
	for (var i = 0; i < arr.length; i++) {
		if (newArr.indexOf(arr[i]) === -1) {
			newArr.push(arr[i]);
		}
	}
	return newArr;
}
// var demo = unique(['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b'])
var demo = unique(['blue', 'green', 'blue'])
console.log(demo);
```

#### 数组转化为字符串
1. toString() 将我们的数组转换为字符串
```JS
var arr = [1, 2, 3];
console.log(arr.toString()); // 1,2,3
```
2. join(分隔符)
```JS
var arr1 = ['green', 'blue', 'pink'];
console.log(arr1.join()); // green,blue,pink
console.log(arr1.join('-')); // green-blue-pink
console.log(arr1.join('&')); // green&blue&pink
```

### 字符串对象
字符串的不可变所以不要大量的拼接字符串
```JS
// 字符串对象  根据字符返回位置  str.indexOf('要查找的字符', [起始的位置])
var str = '改革春风吹满地，春天来了';
console.log(str.indexOf('春'));
console.log(str.indexOf('春', 3)); // 从索引号是 3的位置开始往后查找
```

#### 查询某个字符
```JS
// 查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数
        // 核心算法：先查找第一个o出现的位置
        // 然后 只要indexOf 返回的结果不是 -1 就继续往后查找
        // 因为indexOf 只能查找到第一个，所以后面的查找，一定是当前索引加1，从而继续查找
var str = "oabcoefoxyozzopp";
var index = str.indexOf('o');
var num = 0;
// console.log(index);
while (index !== -1) {
	console.log(index);
	num++;
	index = str.indexOf('o', index + 1);
}
console.log('o出现的次数是: ' + num);
```

#### 根据位置返回字符
charAt(index) 根据位置返回字符
```JS
var str = 'andy';
console.log(str.charAt(3));
// 遍历所有的字符
for (var i = 0; i < str.length; i++) {
	console.log(str.charAt(i));
}
```

charCodeAt(index)  返回相应索引号的字符ASCII值 目的： 判断用户按下了那个键
```JS
console.log(str.charCodeAt(0)); // 97
```

str[index] H5 新增的
```JS
console.log(str[0]); // a
```

#### 统计出现最多的字符和次数
判断一个字符串 'abcoefoxyozzopp' 中出现次数最多的字符，并统计其次数。
```JS
// 核心算法：利用 charAt(） 遍历这个字符串
// 把每个字符都存储给对象， 如果对象没有该属性，就为1，如果存在了就 +1
// 遍历对象，得到最大值和该字符
var str = 'abcoefoxyozzopp';
var o = {};
for (var i = 0; i < str.length; i++) {
	var chars = str.charAt(i); // chars 是 字符串的每一个字符
	if (o[chars]) { // o[chars] 得到的是属性值
		o[chars]++;
	} else {
		o[chars] = 1;
	}
}
console.log(o);
var max = 0;
var ch = '';
for (var k in o) {
	// k 得到是 属性名
	// o[k] 得到的是属性值
	if (o[k] > max) {
		max = o[k];
		ch = k;
	}
}
console.log(max);  // 显示最多的次数
console.log('最多的字符是' + ch);  // 显示最多的字符
```

#### 字符串连接与截取
concat('字符串1','字符串2'....)
```JS
var str = 'andy';
console.log(str.concat('red'));
```
substr('截取的起始位置', '截取几个字符');
```JS
var str1 = '改革春风吹满地';
console.log(str1.substr(2, 2)); // 第一个2 是索引号的2 从第几个开始  第二个2 是取几个字符
```

#### 字符串替换与转换
replace('被替换的字符', '替换为的字符')  它只会替换第一个字符
```JS
var str = 'andyandy';
console.log(str.replace('a', 'b'));
// 有一个字符串 'abcoefoxyozzopp'  要求把里面所有的 o 替换为 *
var str1 = 'abcoefoxyozzopp';
while (str1.indexOf('o') !== -1) {
	str1 = str1.replace('o', '*');
}
console.log(str1);
```
字符转换为数组 split('分隔符')    前面我们学过 join 把数组转换为字符串
```JS
var str2 = 'red, pink, blue';
console.log(str2.split(','));
var str3 = 'red&pink&blue';
console.log(str3.split('&'));
```

## 简单/复杂数据类型
简单类型又叫做基本数据类型或者值类型，复杂类型又叫做引用类型
值类型：简单数据类型/基本数据类型，在存储时变量中存储的是值本身，因此叫做值类型  string number,boolean,undefined,null
引用类型：复杂数据类型，在存储时变量中存储的仅仅是地址（引用），因此叫做用数据类型
通过new关键字创建的对象(系统对象、自定义对象)，如Object、Array、Date等

### 基本包装类型
基本包装类型：  就是把简单数据类型 包装成为了 复杂数据类型
```JS
// (1) 把简单数据类型包装为复杂数据类型 
var temp = new String('andy');
// (2) 把临时变量的值 给 str
str = temp;
// (3) 销毁这个临时变量
temp = null;
```

### 内存分配
1. 简单数据类型 存放在栈里面 里面直接开辟一个空间存放的是值
2. 复杂数据类型 首先在栈里面存放地址 十六进制表示  然后这个地址指向堆里面的数据

# Web APIs

## DOM
DOM（Document Object Model——文档对象模型）是用来呈现以及与任意 HTML 或 XML 文档交互的 API。DOM 是载入到浏览器中的文档模型，以节点树的形式来表现文档，每个节点代表文档的构成部分（例如：页面元素、字符串或注释等等）。

## 获取元素

### 获取元素 getElementById 接口
```html
<div id="time">2019-9-9</div>
<script>
	// 1. 因为我们文档页面从上往下加载，所以先得有标签 所以我们script写到标签的下面
	// 2. get 获得 element 元素 by 通过 驼峰命名法 
	// 3. 参数 id是大小写敏感的字符串
	// 4. 返回的是一个元素对象
	var timer = document.getElementById('time');
	console.log(timer);
	console.log(typeof timer);
	// 5. console.dir 打印我们返回的元素对象 更好的查看里面的属性和方法
	console.dir(timer);
</script>
```

### 根据标签获取元素
```JS
// 获取过来元素对象的集合 以伪数组的形式存储的
var lis = document.getElementsByTagName('li');
console.log(lis);
console.log(lis[0]);

// 依次打印里面的元素对象我们可以采取遍历的方式
for (var i = 0; i < lis.length; i++) {
	console.log(lis[i]);
}
// 如果页面中只有一个li 返回的还是伪数组的形式 
// 如果页面中没有这个元素 返回的是空的伪数组的形式

// element.getElementsByTagName('标签名'); 父元素必须是指定的单个元素
var ol = document.getElementsByTagName('ol'); // [ol]
console.log(ol[0].getElementsByTagName('li'));

var ol = document.getElementById('ol');  // 通过ID获取
console.log(ol[0].getElementsByTagName('li'));
```

### 根据类名获取元素
```html
<div class="box">盒子1</div>
<div class="box">盒子2</div>
<div id="nav">
	<ul>
		<li>首页</li>
		<li>产品</li>
	</ul>
</div>
<script>
	// 1. getElementsByClassName 根据类名获得某些元素集合
	var boxs = document.getElementsByClassName('box');
	console.log(boxs);

	// 2. querySelector 返回指定选择器的第一个元素对象  切记 里面的选择器需要加符号 .box  #nav
	var firstBox = document.querySelector('.box');
	console.log(firstBox);
	var nav = document.querySelector('#nav');
	console.log(nav);
	var li = document.querySelector('li');
	console.log(li);

	// 3. querySelectorAll()返回指定选择器的所有元素对象集合
	var allBox = document.querySelectorAll('.box');
	console.log(allBox);
	var lis = document.querySelectorAll('li');
	console.log(lis);
</script>
```

### 获取 body 和 html 标签
```js
// 1.获取body 元素
var bodyEle = document.body;
console.log(bodyEle);
console.dir(bodyEle);

// 2.获取html 元素
var htmlEle = document.documentElement;
console.log(htmlEle);
```

## 事件
事件是有三部分组成  事件源  事件类型  事件处理程序   我们也称为事件三要素
- 事件源 事件被触发的对象
- 事件类型  如何触发 什么事件 比如鼠标点击(onclick) 还是鼠标经过 还是键盘按下
- 事件处理程序  通过一个函数赋值的方式 完成
```html
<button id="btn">唐伯虎</button>
    <script>
		var btn = document.getElementById('btn');  // 事件源:btn
		btn.onclick = function() {
            alert('点秋香');
        }
	</script>
```

### 执行事件步骤
1. 获取事件源
2. 绑定事件 注册事件
3. 添加事件处理程序
```js
var div = document.querySelector('div');
div.onclick
div.onclick = function() {
	console.log('我被选中了');
}
```

## 操作元素

### 改变元素内容
```html
<button>显示当前系统时间</button>
<div>某个时间</div>
<p>1123</p>
<script>
	// 当我们点击了按钮，  div里面的文字会发生变化
	// 1. 获取元素 
	var btn = document.querySelector('button');
	var div = document.querySelector('div');
	// 2.注册事件
	btn.onclick = function() {
		// div.innerText = '2019-6-6';
		div.innerHTML = getDate();  // getDate是自定义函数
	}
</script>
```

### 读写元素内容
```html
<p>
	我是文字
	<span>123</span>
</p>
<script>
	// innerText 和 innerHTML的区别 
	// 1. innerText 不识别html标签 非标准  去除空格和换行
	var div = document.querySelector('div');
	// div.innerText = '<strong>今天是：</strong> 2019';
	// 2. innerHTML 识别html标签 W3C标准 保留空格和换行的
	div.innerHTML = '<strong>今天是：</strong> 2019';
	// 这两个属性是可读写的  可以获取元素里面的内容
	var p = document.querySelector('p');
	console.log(p.innerText);
	console.log(p.innerHTML);
</script>
```

### 改变元素属性
```html
<button id="ldh">刘德华</button>
<button id="zxy">张学友</button> <br>
<img src="images/ldh.jpg" alt="" title="刘德华">

<script>
	// 修改元素属性  src
	// 1. 获取元素
	var ldh = document.getElementById('ldh');
	var zxy = document.getElementById('zxy');
	var img = document.querySelector('img');
	// 2. 注册事件  处理程序
	zxy.onclick = function() {
		img.src = 'images/zxy.jpg';
		img.title = '张学友思密达';
	}
	ldh.onclick = function() {
		img.src = 'images/ldh.jpg';
		img.title = '刘德华';
	}
</script>
```

#### 分时问候案例
```html
<img src="images/s.gif" alt="">
<div>上午好</div>
<script>
	// 根据系统不同时间来判断，所以需要用到日期内置对象
	// 利用多分支语句来设置不同的图片
	// 需要一个图片，并且根据时间修改图片，就需要用到操作元素src属性
	// 需要一个div元素，显示不同问候语，修改元素内容即可
	// 1.获取元素
	var img = document.querySelector('img');
	var div = document.querySelector('div');
	// 2. 得到当前的小时数
	var date = new Date();
	var h = date.getHours();
	// 3. 判断小时数改变图片和文字信息
	if (h < 12) {
		img.src = 'images/s.gif';
		div.innerHTML = '亲，上午好，好好写代码';
	} else if (h < 18) {
		img.src = 'images/x.gif';
		div.innerHTML = '亲，下午好，好好写代码';
	} else {
		img.src = 'images/w.gif';
		div.innerHTML = '亲，晚上好，好好写代码';
	}
</script>
```

### 操作表单元素
```html
<button>按钮</button>
<input type="text" value="输入内容">
<script>
	// 1. 获取元素
	var btn = document.querySelector('button');
	var input = document.querySelector('input');
	// 2. 注册事件 处理程序
	btn.onclick = function() {
		// input.innerHTML = '点击了';  这个是 普通盒子 比如 div 标签里面的内容
		// 表单里面的值 文字内容是通过 value 来修改的
		input.value = '被点击了';
		// 如果想要某个表单被禁用 不能再点击 disabled  我们想要这个按钮 button禁用
		// btn.disabled = true;
		this.disabled = true;
		// this 指向的是事件函数的调用者 btn
	}
</script>
```

### 表单元素属性操作

#### 密码明文案例
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            position: relative;
            width: 400px;
            border-bottom: 1px solid #ccc;
            margin: 100px auto;
        }
        
        .box input {
            width: 370px;
            height: 30px;
            border: 0;
            outline: none;
        }
        
        .box img {
            position: absolute;
            top: 2px;
            right: 2px;
            width: 24px;
        }
    </style>
</head>

<body>
	<div class="box">
		<label for="">
			<img src="images/close.png" alt="" id="eye">
		</label>
		<input type="password" name="" id="pwd">
	</div>
	<script>
		// 1. 获取元素
		var eye = document.getElementById('eye');
		var pwd = document.getElementById('pwd');
		// 2. 注册事件 处理程序
		var flag = 0;
		eye.onclick = function() {
			// 点击一次之后， flag 一定要变化
			if (flag == 0) {
				pwd.type = 'text';
				eye.src = 'images/open.png';
				flag = 1; // 赋值操作
			} else {
				pwd.type = 'password';
				eye.src = 'images/close.png';
				flag = 0;
			}
		}
	</script>
</body>
```

### 样式属性操作
```html
<head>
	<style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // 1. 获取元素
        var div = document.querySelector('div');
        // 2. 注册事件 处理程序
        div.onclick = function() {
            // div.style里面的属性 采取驼峰命名法 
            this.style.backgroundColor = 'purple';
            this.style.width = '250px';
        }
    </script>
</body>
```

#### 关闭淘宝二维码案例
```html
<div class="box">
	淘宝二维码
	<img src="images/tao.png" alt="">
	<i class="close-btn">×</i>
</div>
<script>
	// 1. 获取元素 
	var btn = document.querySelector('.close-btn');
	var box = document.querySelector('.box');
	// 2.注册事件 程序处理
	btn.onclick = function() {
		box.style.display = 'none';
	}
</script>
```

#### 循环精灵图
```html
<div class="box">
	<ul>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
	</ul>
</div>
<script>
	// 1. 获取元素 所有的小li 
	var lis = document.querySelectorAll('li');
	for (var i = 0; i < lis.length; i++) {
		// 让索引号 乘以 44 就是每个li 的背景y坐标  index就是我们的y坐标
		var index = i * 44;
		lis[i].style.backgroundPosition = '0 -' + index + 'px';
	}
</script>
```

#### 显示隐藏文本框内容
```html
<input type="text" value="手机">
<script>
	// 1.获取元素
	var text = document.querySelector('input');
	// 2.注册事件 获得焦点事件 onfocus 
	text.onfocus = function() {
			// console.log('得到了焦点');
			if (this.value === '手机') {
				this.value = '';
			}
			// 获得焦点需要把文本框里面的文字颜色变黑
			this.style.color = '#333';
		}
		// 3. 注册事件 失去焦点事件 onblur
	text.onblur = function() {
		// console.log('失去了焦点');
		if (this.value === '') {
			this.value = '手机';
		}
		// 失去焦点需要把文本框里面的文字颜色变浅色
		this.style.color = '#999';
	}
</script>
```

### 通过 className 修改元素样式
```html
<style>
	div {
		width: 100px;
		height: 100px;
		background-color: pink;
	}
	
	.change {
		background-color: purple;
		color: #fff;
		font-size: 25px;
		margin-top: 100px;
	}
</style>


<div class="first">文本</div>
<script>
	// 1. 使用 element.style 获得修改元素样式  如果样式比较少 或者 功能简单的情况下使用
	var test = document.querySelector('div');
	test.onclick = function() {
		// this.style.backgroundColor = 'purple';
		// this.style.color = '#fff';
		// this.style.fontSize = '25px';
		// this.style.marginTop = '100px';
		// 让我们当前元素的类名改为了 change
		// 2. 我们可以通过 修改元素的className更改元素的样式 适合于样式较多或者功能复杂的情况
		// 3. 如果想要保留原先的类名，我们可以这么做 多类名选择器
		// this.className = 'change';
		this.className = 'first change';
	}
</script>
```

#### 密码框验证信息
```html
<style>
        div {
            width: 600px;
            margin: 100px auto;
        }
        .message {
            display: inline-block;
            font-size: 12px;
            color: #999;
            background: url(images/mess.png) no-repeat left center;
            padding-left: 20px;
        }
        .wrong {
            color: red;
            background-image: url(images/wrong.png);
        }
        .right {
            color: green;
            background-image: url(images/right.png);
        }
    </style>
</head>

<body>
    <div class="register">
        <input type="password" class="ipt">
        <p class="message">请输入6~16位密码</p>
    </div>
    <script>
        // 首先判断的事件是表单失去焦点 onblur
        // 如果输入正确则提示正确的信息颜色为绿色小图标变化
        // 如果输入不是6到16位，则提示错误信息颜色为红色 小图标变化
        // 因为里面变化样式较多，我们采取className修改样式
        // 1.获取元素
        var ipt = document.querySelector('.ipt');
        var message = document.querySelector('.message');
        //2. 注册事件 失去焦点
        ipt.onblur = function() {
            // 根据表单里面值的长度 ipt.value.length
            if (this.value.length < 6 || this.value.length > 16) {
                // console.log('错误');
                message.className = 'message wrong';
                message.innerHTML = '您输入的位数不对要求6~16位';
            } else {
                message.className = 'message right';
                message.innerHTML = '您输入的正确';
            }
        }
    </script>
</body>
```

### 排他思想
如果有同一组元素，我们想要某一个元素实现某种样式，需要用到循环的排他思想算法
```html
<body>
    <button>按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>
    <button>按钮4</button>
    <button>按钮5</button>
    <script>
        // 1. 获取所有按钮元素
        var btns = document.getElementsByTagName('button');
        // btns得到的是伪数组  里面的每一个元素 btns[i]
        for (var i = 0; i < btns.length; i++) {
            btns[i].onclick = function() {
                // (1) 我们先把所有的按钮背景颜色去掉  干掉所有人
                for (var i = 0; i < btns.length; i++) {
                    btns[i].style.backgroundColor = '';
                }
                // (2) 然后才让当前的元素背景颜色为pink 留下我自己
                this.style.backgroundColor = 'pink';
            }
        }
        //2. 首先先排除其他人，然后才设置自己的样式 这种排除其他人的思想我们成为排他思想
    </script>
</body>
```

#### 更换背景图片效果
```html
<head>
	<style>
		* {
            margin: 0;
            padding: 0;
        }
        
        body {
            background: url(images/1.jpg) no-repeat center top;
        }
        
        li {
            list-style: none;
        }
        
        .baidu {
            overflow: hidden;
            margin: 100px auto;
            background-color: #fff;
            width: 410px;
            padding-top: 3px;
        }
        
        .baidu li {
            float: left;
            margin: 0 1px;
            cursor: pointer;
        }
        
        .baidu img {
            width: 100px;
        }
    </style>
</head>

<body>
    <ul class="baidu">
        <li><img src="images/1.jpg"></li>
        <li><img src="images/2.jpg"></li>
        <li><img src="images/3.jpg"></li>
        <li><img src="images/4.jpg"></li>
    </ul>
    <script>
        // 1. 获取元素 
        var imgs = document.querySelector('.baidu').querySelectorAll('img');
        // console.log(imgs);
        // 2. 循环注册事件 
        for (var i = 0; i < imgs.length; i++) {
            imgs[i].onclick = function() {
                // this.src 就是我们点击图片的路径   images/2.jpg
                // console.log(this.src);
                // 把这个路径 this.src 给body 就可以了
                document.body.style.backgroundImage = 'url(' + this.src + ')';
            }
        }
    </script>
</body>
```

#### 鼠标经过更换背景色
```html
<style>
        table {
            width: 800px;
            margin: 100px auto;
            text-align: center;
            border-collapse: collapse;
            font-size: 14px;
        }
        
        thead tr {
            height: 30px;
            background-color: skyblue;
        }
        
        tbody tr {
            height: 30px;
        }
        
        tbody td {
            border-bottom: 1px solid #d7d7d7;
            font-size: 12px;
            color: blue;
        }
        
        .bg {
            background-color: pink;
        }
    </style>
</head>

<body>
    <table>
        <thead>
            <tr>
                <th>代码</th>
                <th>名称</th>
                <th>最新公布净值</th>
                <th>累计净值</th>
                <th>前单位净值</th>
                <th>净值增长率</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
        </tbody>
    </table>
    <script>
        // 1.获取元素 获取的是 tbody 里面所有的行
        var trs = document.querySelector('tbody').querySelectorAll('tr');
        // 2. 利用循环绑定注册事件
        for (var i = 0; i < trs.length; i++) {
            // 3. 鼠标经过事件 onmouseover
            trs[i].onmouseover = function() {
                    // console.log(11);
                    this.className = 'bg';
                }
                // 4. 鼠标离开事件 onmouseout
            trs[i].onmouseout = function() {
                this.className = '';
            }
        }
    </script>
</body>
```

#### 表单全选/反选
```html
<body>
    <div class="wrap">
        <table>
            <thead>
                <tr>
                    <th>
                        <input type="checkbox" id="j_cbAll" />
                    </th>
                    <th>商品</th>
                    <th>价钱</th>
                </tr>
            </thead>
            <tbody id="j_tb">
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPhone8</td>
                    <td>8000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPad Pro</td>
                    <td>5000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPad Air</td>
                    <td>2000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>Apple Watch</td>
                    <td>2000</td>
                </tr>

            </tbody>
        </table>
    </div>
    <script>
        // 1. 全选和取消全选做法：  让下面所有复选框的checked属性（选中状态） 跟随 全选按钮即可
        // 获取元素
        var j_cbAll = document.getElementById('j_cbAll'); // 全选按钮
        var j_tbs = document.getElementById('j_tb').getElementsByTagName('input'); // 下面所有的复选框
        // 注册事件
        j_cbAll.onclick = function() {
                // this.checked 它可以得到当前复选框的选中状态如果是true 就是选中，如果是false 就是未选中
                console.log(this.checked);
                for (var i = 0; i < j_tbs.length; i++) {
                    j_tbs[i].checked = this.checked;
                }
            }
            // 2. 下面复选框需要全部选中， 上面全选才能选中做法： 给下面所有复选框绑定点击事件，每次点击，都要循环查看下面所有的复选框是否有没选中的，如果有一个没选中的， 上面全选就不选中。
        for (var i = 0; i < j_tbs.length; i++) {
            j_tbs[i].onclick = function() {
                // flag 控制全选按钮是否选中
                var flag = true;
                // 每次点击下面的复选框都要循环检查者4个小按钮是否全被选中
                for (var i = 0; i < j_tbs.length; i++) {
                    if (!j_tbs[i].checked) {
                        flag = false;
                        break; // 退出for循环 这样可以提高执行效率 因为只要有一个没有选中，剩下的就无需循环判断了
                    }
                }
                j_cbAll.checked = flag;
            }
        }
    </script>
</body>
```

### 自定义属性值
element.属性获取内置属性值（元素本身自带的属性）
element.getAttribute('属性')；主要获得自定义的属性（标准）我们程序员自定义的属性
```html
<div id="demo" index="1" class="nav"></div>
<script>
	var div = document.querySelector('div');
	// 1. 获取元素的属性值
	// (1) element.属性
	console.log(div.id);
	//(2) element.getAttribute('属性')  get得到获取 attribute 属性的意思 我们程序员自己添加的属性我们称为自定义属性 index
	console.log(div.getAttribute('id'));
	console.log(div.getAttribute('index'));
</script>
```

#### 设置自定义属性值
```html
<script>
// 2. 设置元素属性值
	// (1) element.属性= '值'
	div.id = 'test';
	div.className = 'navs';
	// (2) element.setAttribute('属性', '值');  主要针对于自定义属性
	div.setAttribute('index', 2);
	div.setAttribute('class', 'footer'); // class 特殊  这里面写的就是class 不是className
	// 3 移除属性 removeAttribute(属性)    
	div.removeAttribute('index');
</script>
```

#### Tab 栏切换
```html
<script>
	// 获取元素
	var tab_list = document.querySelector('.tab_list');
	var lis = tab_list.querySelectorAll('li');
	var items = document.querySelectorAll('.item');
	// for循环绑定点击事件
	for (var i = 0; i < lis.length; i++) {
		// 开始给5个小li 设置索引号 
		lis[i].setAttribute('index', i);
		lis[i].onclick = function() {
			// 1. 上的模块选项卡，点击某一个，当前这一个底色会是红色，其余不变（排他思想） 修改类名的方式
			// 干掉所有人 其余的li清除 class 这个类
			for (var i = 0; i < lis.length; i++) {
				lis[i].className = '';
			}
			// 留下我自己 
			this.className = 'current';
			// 2. 下面的显示内容模块
			var index = this.getAttribute('index');
			console.log(index);
			// 干掉所有人 让其余的item 这些div 隐藏
			for (var i = 0; i < items.length; i++) {
				items[i].style.display = 'none';
			}
			// 留下我自己 让对应的item 显示出来
			items[index].style.display = 'block';
		}
	}
</script>
```

#### H5 获取自定义属性
H5规定自定义属性data开头做为属性名并且赋值。
比如`<div data-index=""><div>`
```html
<div getTime="20" data-index="2" data-list-name="andy"></div>
    <script>
        var div = document.querySelector('div');
        // console.log(div.getTime);
        console.log(div.getAttribute('getTime'));
        div.setAttribute('data-time', 20);
        console.log(div.getAttribute('data-index'));
        console.log(div.getAttribute('data-list-name'));
        // h5新增的获取自定义属性的方法 它只能获取data-开头的
        // dataset 是一个集合里面存放了所有以data开头的自定义属性
        console.log(div.dataset);
        console.log(div.dataset.index);
        console.log(div.dataset['index']);
        // 如果自定义属性里面有多个-链接的单词，我们获取的时候采取 驼峰命名法
        console.log(div.dataset.listName);
        console.log(div.dataset['listName']);
    </script>
</div>
```

### 节点操作
一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个基本属性。
元素节点nodeType为1
属性节点nodeType为2
文本节点nodeType为3(文本节点包含文字、空格、换行等)

#### 节点层级

##### 父节点
```html
<div class="demo">
	<div class="box">
		<span class="erweima">×</span>
	</div>
</div>

<script>
	// 1. 父节点 parentNode
	var erweima = document.querySelector('.erweima');
	// var box = document.querySelector('.box');
	// 得到的是离元素最近的父级节点(亲爸爸) 如果找不到父节点就返回为 null
	console.log(erweima.parentNode);
</script>
```

##### 子节点
注意：childNodes 返回值里面包含了所有的子节点，包括元素节点，文本节点等。
如果只想要获得里面的元素节点，则需要专门处理。所以我们一般不提倡使用child Nodes
```html
<script>
	// DOM 提供的方法（API）获取
	var ul = document.querySelector('ul');
	var lis = ul.querySelectorAll('li');
	// 1. 子节点  childNodes 所有的子节点 包含 元素节点 文本节点等等
	console.log(ul.childNodes);
	console.log(ul.childNodes[0].nodeType);
	console.log(ul.childNodes[1].nodeType);
	// 2. children 获取所有的子元素节点 也是我们实际开发常用的
	console.log(ul.children);
</script>
```

##### 子节点第一个/最后一个节点
```html
<script>
	var ol = document.querySelector('ol');
	// 1. firstChild 第一个子节点 不管是文本节点还是元素节点
	console.log(ol.firstChild);
	console.log(ol.lastChild);
	// 2. firstElementChild 返回第一个子元素节点 ie9才支持
	console.log(ol.firstElementChild);
	console.log(ol.lastElementChild);
	// 3. 实际开发的写法  既没有兼容性问题又返回第一个子元素
	console.log(ol.children[0]);
	console.log(ol.children[ol.children.length - 1]);
</script>
```

##### 下拉菜单案例
```html
<body>
    <ul class="nav">
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
    </ul>
    <script>
        // 1. 获取元素
        var nav = document.querySelector('.nav');
        var lis = nav.children; // 得到4个小li
        // 2.循环注册事件
        for (var i = 0; i < lis.length; i++) {
            lis[i].onmouseover = function() {
                this.children[1].style.display = 'block';
            }
            lis[i].onmouseout = function() {
                this.children[1].style.display = 'none';
            }
        }
    </script>
</body>
```

##### 兄弟节点
```html
<div>我是div</div>
<span>我是span</span>
<script>
	var div = document.querySelector('div');
	// 1.nextSibling 下一个兄弟节点 包含元素节点或者 文本节点等等
	console.log(div.nextSibling);
	console.log(div.previousSibling);
	// 2. nextElementSibling 得到下一个兄弟元素节点
	console.log(div.nextElementSibling);
	console.log(div.previousElementSibling);
</script>
```

#### 创建/添加节点
document.createElement（）方法创建由tagName指定的HTML元素。因为这些元素原先不存在，是根据我们的需求动态生成的，所以我们也称为动态创建元素节点。
```html
<ul>
	<li>123</li>
</ul>
<script>
	// 1. 创建节点元素节点
	var li = document.createElement('li');
	// 2. 添加节点 node.appendChild(child)  node 父级  child 是子级 后面追加元素  类似于数组中的push
	var ul = document.querySelector('ul');
	ul.appendChild(li);
	// 3. 添加节点 node.insertBefore(child, 指定元素);
	var lili = document.createElement('li');
	ul.insertBefore(lili, ul.children[0]);
	// 4. 我们想要页面添加一个新的元素 ： 1. 创建元素 2. 添加元素
</script>
```

##### 简单留言板
```html
<textarea name="" id=""></textarea>
<button>发布</button>
<ul>

</ul>
<script>
	// 1. 获取元素
	var btn = document.querySelector('button');
	var text = document.querySelector('textarea');
	var ul = document.querySelector('ul');
	// 2. 注册事件
	btn.onclick = function() {
		if (text.value == '') {
			alert('您没有输入内容');
			return false;
		} else {
			// console.log(text.value);
			// (1) 创建元素
			var li = document.createElement('li');
			// 先有li 才能赋值
			li.innerHTML = text.value;
			// (2) 添加元素
			// ul.appendChild(li);
			ul.insertBefore(li, ul.children[0]);
		}
	}
</script>
```

#### 删除节点
```html
<button>删除</button>
<ul>
	<li>熊大</li>
	<li>熊二</li>
	<li>光头强</li>
</ul>
<script>
	// 1.获取元素
	var ul = document.querySelector('ul');
	var btn = document.querySelector('button');
	// 2. 删除元素  node.removeChild(child)
	// ul.removeChild(ul.children[0]);
	// 3. 点击按钮依次删除里面的孩子
	btn.onclick = function() {
		if (ul.children.length == 0) {
			this.disabled = true;
		} else {
			ul.removeChild(ul.children[0]);
		}
	}
</script>
```

##### 删除留言案例
```html
<textarea name="" id=""></textarea>
<button>发布</button>
<ul>

</ul>
<script>
	// 1. 获取元素
	var btn = document.querySelector('button');
	var text = document.querySelector('textarea');
	var ul = document.querySelector('ul');
	// 2. 注册事件
	btn.onclick = function() {
		if (text.value == '') {
			alert('您没有输入内容');
			return false;
		} else {
			// console.log(text.value);
			// (1) 创建元素
			var li = document.createElement('li');
			// 先有li 才能赋值
			li.innerHTML = text.value + "<a href='javascript:;'>删除</a>";
			// (2) 添加元素
			// ul.appendChild(li);
			ul.insertBefore(li, ul.children[0]);
			// (3) 删除元素 删除的是当前链接的li  它的父亲
			var as = document.querySelectorAll('a');
			for (var i = 0; i < as.length; i++) {
				as[i].onclick = function() {
					// node.removeChild(child); 删除的是 li 当前a所在的li  this.parentNode;
					ul.removeChild(this.parentNode);
				}
			}
		}
	}
</script>
```

#### 克隆节点
node.cloneNode（）方法返回调用该方法的节点的一个副本。也称为克隆节点/拷贝节点
注意：
1. 如果括号参数为空或者为fa1se,则是浅拷贝，即只克隆复制节点本身，不克隆里面的子节点。
2. node.cloneNode(true); 括号为true 深拷贝 复制标签复制里面的内容
```html
<ul>
	<li>1111</li>
	<li>2</li>
	<li>3</li>
</ul>
<script>
	var ul = document.querySelector('ul');
	// 1. node.cloneNode(); 括号为空或者里面是false 浅拷贝 只复制标签不复制里面的内容
	// 2. node.cloneNode(true); 括号为true 深拷贝 复制标签复制里面的内容
	var lili = ul.children[0].cloneNode(true);
	ul.appendChild(lili);
</script>
```

#### 动态调整表格
```html
<table cellspacing="0">
	<thead>
		<tr>
			<th>姓名</th>
			<th>科目</th>
			<th>成绩</th>
			<th>操作</th>
		</tr>
	</thead>
	<tbody>

	</tbody>
</table>
<script>
	// 1.先去准备好学生的数据 可以从后端获取
	var datas = [
		{
			name: '魏璎珞',
			subject: 'JavaScript',
			score: 100
		}, {
			name: '弘历',
			subject: 'JavaScript',
			score: 98
		}, {
			name: '傅恒',
			subject: 'JavaScript',
			score: 99
		}, {
			name: '明玉',
			subject: 'JavaScript',
			score: 88
		}, {
			name: '大猪蹄子',
			subject: 'JavaScript',
			score: 0
		}
	];
	// 2. 往tbody 里面创建行： 有几个人（通过数组的长度）我们就创建几行
	var tbody = document.querySelector('tbody');
	for (var i = 0; i < datas.length; i++) { // 外面的for循环管行 tr
		// 1. 创建 tr行
		var tr = document.createElement('tr');
		tbody.appendChild(tr);
		// 2. 行里面创建单元格(跟数据有关系的3个单元格) td 单元格的数量取决于每个对象里面的属性个数  for循环遍历对象 datas[i]
		for (var k in datas[i]) { // 里面的for循环管列 td
			// 创建单元格 
			var td = document.createElement('td');
			// 把对象里面的属性值 datas[i][k] 给 td  
			// console.log(datas[i][k]);
			td.innerHTML = datas[i][k];
			tr.appendChild(td);
		}
		// 3. 创建有删除2个字的单元格 
		var td = document.createElement('td');
		td.innerHTML = '<a href="javascript:;">删除 </a>';
		tr.appendChild(td);
	}
	// 4. 删除操作 开始 
	var as = document.querySelectorAll('a');
	for (var i = 0; i < as.length; i++) {
		as[i].onclick = function() {
			// 点击a 删除 当前a 所在的行(链接的爸爸的爸爸)  node.removeChild(child)  
			tbody.removeChild(this.parentNode.parentNode)
		}
	}
	// for(var k in obj) {
	//     k 得到的是属性名
	//     obj[k] 得到是属性值
	// }
</script>
```

### 三种创建元素的区别
1. document.write() 创建元素  如果页面文档流加载完毕，再调用这句话会导致页面重绘
```html
<script>
	var btn = document.querySelector('button');
	btn.onclick = function() {
		document.write('<div>123</div>');
	}
</script>
```
2. innerHTML 创建元素
```html
<script>
	// 追加多个元素（效率低）
	var inner = document.querySelector('.inner');
	for (var i = 0; i <= 100; i++) {
		inner.innerHTML += '<a href="#">百度</a>'
	}
	// 数组（效率高）
	var arr = [];
	for (var i = 0; i <= 100; i++) {
		arr.push('<a href="#">百度</a>');
	}
</script>
```
3. document.createElement() 创建元素（效率比数组低，比追加高）
```html
<script>
	var create = document.querySelector('.create');
	for (var i = 0; i <= 100; i++) {
		var a = document.createElement('a');
		create.appendChild(a);
	}
</script>
```

## DOM 重点核心
关于dom操作，我们主要针对于元素的操作。主要有创健、增、删、改、查、属性操作、事件操作。

### 事件

### 注册事件
```html
<script>
	var btns = document.querySelectorAll('button');
	// 1. 传统方式注册事件
	btns[0].onclick = function() {
		alert('hi');
	}
	btns[0].onclick = function() {
			alert('hao a u');
		}
		// 2. 事件侦听注册事件 addEventListener 
		// (1) 里面的事件类型是字符串 必定加引号 而且不带on
		// (2) 同一个元素 同一个事件可以添加多个侦听器（事件处理程序）
	btns[1].addEventListener('click', function() {
		alert(22);
	})
	btns[1].addEventListener('click', function() {
			alert(33);
		})
		// 3. attachEvent ie9以前的版本支持
	btns[2].attachEvent('onclick', function() {
		alert(11);
	})
</script>
```

### 删除事件
```html
<body>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <script>
        var divs = document.querySelectorAll('div');
        divs[0].onclick = function() {
                alert(11);
                // 1. 传统方式删除事件
                divs[0].onclick = null;
            }
            // 2. removeEventListener 删除事件
        divs[1].addEventListener('click', fn) // 里面的fn 不需要调用加小括号
        function fn() {
            alert(22);
            divs[1].removeEventListener('click', fn);
        }
        // 3. detachEvent
        divs[2].attachEvent('onclick', fn1);
        function fn1() {
            alert(33);
            divs[2].detachEvent('onclick', fn1);
        }
    </script>
</body>
```

### DOM 事件流
DOM事件流分为3个阶段：
1.捕获阶段
2.当前目标阶段
3.冒泡阶段
事件冒泡：IE最早提出，事件开始时由最具体的元素接收，然后逐级向上传播到倒到DOM最顶层节点的过程
事件捕获：网景最早提出，由DOM最顶层节点开始，然后逐级向下传播到到最具体的元素接收的过程。
```html
<style>
	.father {
		overflow: hidden;
		width: 300px;
		height: 300px;
		margin: 100px auto;
		background-color: pink;
		text-align: center;
	}
	
	.son {
		width: 200px;
		height: 200px;
		margin: 50px;
		background-color: purple;
		line-height: 200px;
		color: #fff;
	}
</style>

<body>
    <div class="father">
        <div class="son">son盒子</div>
    </div>
    <script>
        // dom 事件流 三个阶段
        // 1. JS 代码中只能执行捕获或者冒泡其中的一个阶段。
        // 2. onclick 和 attachEvent（ie） 只能得到冒泡阶段。
        // 3. 捕获阶段 如果addEventListener 第三个参数是 true 那么则处于捕获阶段  document -> html -> body -> father -> son
        // var son = document.querySelector('.son');
        // son.addEventListener('click', function() {
        //     alert('son');
        // }, true);
        // var father = document.querySelector('.father');
        // father.addEventListener('click', function() {
        //     alert('father');
        // }, true);
        // 4. 冒泡阶段 如果addEventListener 第三个参数是 false 或者 省略 那么则处于冒泡阶段  son -> father ->body -> html -> document
        var son = document.querySelector('.son');
        son.addEventListener('click', function() {
            alert('son');
        }, false);
        var father = document.querySelector('.father');
        father.addEventListener('click', function() {
            alert('father');
        }, false);
        document.addEventListener('click', function() {
            alert('document');
        })
    </script>
</body>
```
1.JS代码中只能执行捕获或者冒泡其中的一个阶段。
2.onclick和attachEvent只能得到冒泡阶段。
3.addEventListener(type,listener[,useCapture])第三个参数如果是true,表示在事件捕获阶段调用事件处理程序：如果是fa1se(不写默认就是fa1se),表示在事件冒泡阶段调用事件牧处理程序。
4.实际开发中我们很少使用事件捕获，我们更关注事件冒泡。
5.有些事件是没有冒泡的，比如onblur、onfocus、onmouseenter、onmouseleave
6.事件冒泡有时候会带来麻烦，有时候又会帮助很巧妙的做某些事件，我们后面讲解。

### 事件对象
1. event 就是一个事件对象 写到我们侦听函数的 小括号里面 当形参来看
2. 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数
3. 事件对象 是 我们事件的一系列相关数据的集合 跟事件相关的 比如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标啊，如果是键盘事件里面就包含的键盘事件的信息 比如 判断用户按下了那个键
4. 这个事件对象我们可以自己命名 比如 event 、 evt、 e
5. 事件对象也有兼容性问题 ie678 通过 window.event 兼容性的写法  e = e || window.event;
```html
<div>123</div>
<script>
	// 事件对象
	var div = document.querySelector('div');
	div.onclick = function(e) {
			// console.log(e);
			// console.log(window.event);
			// e = e || window.event;
			console.log(e);
		}
</script>
```

### 事件对象的属性 e.target/this
```js
// 1. e.target 返回的是触发事件的对象（元素）  this 返回的是绑定事件的对象（元素）
// 区别 ： e.target 点击了那个元素，就返回那个元素 this 那个元素绑定了这个点击事件，那么就返回谁
var div = document.querySelector('div');
div.addEventListener('click', function(e) {
	console.log(e.target);
	console.log(this);
})
var ul = document.querySelector('ul');
ul.addEventListener('click', function(e) {
		// 我们给ul 绑定了事件  那么this 就指向ul  
		console.log(this);
		console.log(e.currentTarget);
		// e.target 指向我们点击的那个对象 谁触发了这个事件 我们点击的是li e.target 指向的就是li
		console.log(e.target);
	})
	// 了解兼容性
	// div.onclick = function(e) {
	//     e = e || window.event;
	//     var target = e.target || e.srcElement;
	//     console.log(target);
// }
// 2. 了解 跟 this 有个非常相似的属性 currentTarget  ie678不认识
```

### 阻止事件默认行为
```html
<body>
    <div>123</div>
    <a href="http://www.baidu.com">百度</a>
    <form action="http://www.baidu.com">
        <input type="submit" value="提交" name="sub">
    </form>
    <script>
        // 常见事件对象的属性和方法
        // 1. 返回事件类型
        var div = document.querySelector('div');
        div.addEventListener('click', fn);
        div.addEventListener('mouseover', fn);
        div.addEventListener('mouseout', fn);
        
        function fn(e) {
            console.log(e.type);
        }
        // 2. 阻止默认行为（事件） 让链接不跳转 或者让提交按钮不提交
        var a = document.querySelector('a');
        a.addEventListener('click', function(e) {
                e.preventDefault(); //  dom 标准写法
            })
            // 3. 传统的注册方式
        a.onclick = function(e) {
            // 普通浏览器 e.preventDefault();  方法
            // e.preventDefault();
            // 低版本浏览器 ie678  returnValue  属性
            // e.returnValue;
            // 我们可以利用return false 也能阻止默认行为 没有兼容性问题 特点： return 后面的代码不执行了， 而且只限于传统的注册方式
            return false;
            alert(11);
        }
    </script>
</body>
```

### 阻止事件冒泡
```html
<body>
    <div class="father">
        <div class="son">son儿子</div>
    </div>
    <script>
        // 常见事件对象的属性和方法
        // 阻止冒泡  dom 推荐的标准 stopPropagation() 
        var son = document.querySelector('.son');
        son.addEventListener('click', function(e) {
            alert('son');
            e.stopPropagation(); // stop 停止  Propagation 传播
            e.cancelBubble = true; // 非标准 cancel 取消 bubble 泡泡
        }, false);

        var father = document.querySelector('.father');
        father.addEventListener('click', function() {
            alert('father');
        }, false);
        document.addEventListener('click', function() {
            alert('document');
        })
    </script>
</body>
```

### 事件委托
不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点。
```html
<body>
    <ul>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
    </ul>
    <script>
        // 事件委托的核心原理：给父节点添加侦听器， 利用事件冒泡影响每一个子节点
        var ul = document.querySelector('ul');
        ul.addEventListener('click', function(e) {
            // alert('知否知否，点我应有弹框在手！');
            // e.target 这个可以得到我们点击的对象
            e.target.style.backgroundColor = 'pink';
        })
    </script>
</body>
```

### 禁止右键和选中
```html
<body>
    我是一段不愿意分享的文字
    <script>
        // 1. contextmenu 我们可以禁用右键菜单
        document.addEventListener('contextmenu', function(e) {
                e.preventDefault();
            })
            // 2. 禁止选中文字 selectstart
        document.addEventListener('selectstart', function(e) {
            e.preventDefault();

        })
    </script>
</body>
```

### 鼠标坐标
```html
<body>
    <script>
        // 鼠标事件对象 MouseEvent
        document.addEventListener('click', function(e) {
            // 1. client 鼠标在可视区的x和y坐标
            console.log(e.clientX);
            console.log(e.clientY);
            console.log('---------------------');

            // 2. page 鼠标在页面文档的x和y坐标
            console.log(e.pageX);
            console.log(e.pageY);
            console.log('---------------------');

            // 3. screen 鼠标在电脑屏幕的x和y坐标
            console.log(e.screenX);
            console.log(e.screenY);

        })
    </script>
</body>
```

#### 图片跟随鼠标移动
```html
<style>
	img {
		position: absolute;
		top: 2px;
	}
</style>

<body>
    <img src="images/angel.gif" alt="">
    <script>
        var pic = document.querySelector('img');
        document.addEventListener('mousemove', function(e) {
            // 1. mousemove只要我们鼠标移动1px 就会触发这个事件
            // console.log(1);
            // 2.核心原理： 每次鼠标移动，我们都会获得最新的鼠标坐标， 把这个x和y坐标做为图片的top和left 值就可以移动图片
            var x = e.pageX;
            var y = e.pageY;
            console.log('x坐标是' + x, 'y坐标是' + y);
            //3 . 千万不要忘记给left 和top 添加px 单位
            pic.style.left = x - 50 + 'px';
            pic.style.top = y - 40 + 'px';
        });
    </script>
</body>
```

### 键盘事件
```html
<script>
	// 常用的键盘事件
	//1. keyup 按键弹起的时候触发 
	// document.onkeyup = function() {
	//         console.log('我弹起了');
	//     }
	document.addEventListener('keyup', function() {
		console.log('我弹起了');
	})
	//3. keypress 按键按下的时候触发  不能识别功能键 比如 ctrl shift 左右箭头
	document.addEventListener('keypress', function() {
			console.log('我按下了press');
		})
		//2. keydown 按键按下的时候触发  能识别功能键 比如 ctrl shift 左右箭头
	document.addEventListener('keydown', function() {
			console.log('我按下了down');
		})
		// 4. 三个事件的执行顺序  keydown -- keypress -- keyup
</script>
```

### 键盘 keyCode 属性
```html
<script>
	// 键盘事件对象中的keyCode属性可以得到相应键的ASCII码值
	// 1. 我们的keyup 和keydown事件不区分字母大小写  a 和 A 得到的都是65
	// 2. 我们的keypress 事件 区分字母大小写  a  97 和 A 得到的是65
	document.addEventListener('keyup', function(e) {
		// console.log(e);
		console.log('up:' + e.keyCode);
		// 我们可以利用keycode返回的ASCII码值来判断用户按下了那个键
		if (e.keyCode === 65) {
			alert('您按下的a键');
		} else {
			alert('您没有按下a键')
		}
	})
	document.addEventListener('keypress', function(e) {
		// console.log(e);
		console.log('press:' + e.keyCode);
	})
</script>
```

#### 京东搜索框
```html
<body>
    <input type="text">
    <script>
        // 核心思路： 检测用户是否按下了s 键，如果按下s 键，就把光标定位到搜索框里面
        // 使用键盘事件对象里面的keyCode 判断用户按下的是否是s键
        // 搜索框获得焦点： 使用 js 里面的 focus() 方法
        var search = document.querySelector('input');
        document.addEventListener('keyup', function(e) {
            // console.log(e.keyCode);
            if (e.keyCode === 83) {
                search.focus();
            }
        })
    </script>
</body>
```

#### 查询快递单框
```html
<body>
    <div class="search">
        <div class="con">123</div>
        <input type="text" placeholder="请输入您的快递单号" class="jd">
    </div>
    <script>
        // 快递单号输入内容时， 上面的大号字体盒子（con）显示(这里面的字号更大）
        // 表单检测用户输入： 给表单添加键盘事件
        // 同时把快递单号里面的值（value）获取过来赋值给 con盒子（innerText）做为内容
        // 如果快递单号里面内容为空，则隐藏大号字体盒子(con)盒子
        var con = document.querySelector('.con');
        var jd_input = document.querySelector('.jd');
        jd_input.addEventListener('keyup', function() {
                // console.log('输入内容啦');
                if (this.value == '') {
                    con.style.display = 'none';
                } else {
                    con.style.display = 'block';
                    con.innerText = this.value;
                }
            })
            // 当我们失去焦点，就隐藏这个con盒子
        jd_input.addEventListener('blur', function() {
                con.style.display = 'none';
            })
            // 当我们获得焦点，就显示这个con盒子
        jd_input.addEventListener('focus', function() {
            if (this.value !== '') {
                con.style.display = 'block';
            }
        })
    </script>
</body>
```

## BOM
BOM(Browser Object Model)即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对像，其核心对象是window.
BOM由一系列相关的对象构成，并目每个对像都提供了很多方法与属性。

### 窗口加载事件 onload
window.onload是窗口页面）加载事件，当文档内容完全加载完成会发该事件（包括图像、脚本文件、CSS文件等），就调用的处理函数。
1.有了window.onload就可以把JS代码写到页面元素的上方，因为onload是等页面内容全部加载完毕再去执行处理函数。
2.window.onload传统注册事件方式只能写一次，如果有多个，会以最后一个window.onload为准。
3.如果使用addEventListener则没有限制
```html
<script>
	// window.onload = function() {
	//     var btn = document.querySelector('button');
	//     btn.addEventListener('click', function() {
	//         alert('点击我');
	//     })
	// }
	// window.onload = function() {
	//     alert(22);
	// }
	window.addEventListener('load', function() {
		var btn = document.querySelector('button');
		btn.addEventListener('click', function() {
			alert('点击我');
		})
	})
	window.addEventListener('load', function() {

		alert(22);
	})
	document.addEventListener('DOMContentLoaded', function() {
			alert(33);
		})
	// load 等页面内容全部加载完毕，包含页面dom元素 图片 flash  css 等等
	// DOMContentLoaded 是DOM 加载完毕，不包含图片 falsh css 等就可以执行 加载速度比 load更快一些
</script>

<body>
    <button>点击</button>
</body>
```

### 调整窗口大小事件 resize
```html
<style>
	div {
		width: 200px;
		height: 200px;
		background-color: pink;
	}
</style>

<body>
    <script>
        window.addEventListener('load', function() {
            var div = document.querySelector('div');
            window.addEventListener('resize', function() {
                console.log(window.innerWidth);
                console.log('变化了');
                if (window.innerWidth <= 800) {
                    div.style.display = 'none';
                } else {
                    div.style.display = 'block';
                }
            })
        })
    </script>
    <div></div>
</body>
```

### 定时器 setTimeout
```html
<script>
	// 1. setTimeout 
	// 语法规范：  window.setTimeout(调用函数, 延时时间);
	// 1. 这个window在调用的时候可以省略
	// 2. 这个延时时间单位是毫秒 但是可以省略，如果省略默认的是0
	// 3. 这个调用函数可以直接写函数 还可以写 函数名 还有一个写法 '函数名()'
	// 4. 页面中可能有很多的定时器，我们经常给定时器加标识符 （名字)
	// setTimeout(function() {
	//     console.log('时间到了');
	// }, 2000);
	function callback() {
		console.log('爆炸了');
	}
	var timer1 = setTimeout(callback, 3000);
	var timer2 = setTimeout(callback, 5000);
	// setTimeout('callback()', 3000); // 我们不提倡这个写法
</script>
```
注意：
1.window可以省略。
2.这个调用函数可以直接写函数，或者写函数名或者采取字符串‘函数名()'三种形式。第三种不推荐
3.延迟的毫秒数省略默认是0，如果写，必须是毫秒。

### 回调函数
5秒后自动关闭广告
```html
<body>
    <img src="images/ad.jpg" alt="" class="ad">
    <script>
        var ad = document.querySelector('.ad');
        setTimeout(function() {
            ad.style.display = 'none';
        }, 5000);
    </script>
</body>
```

### 停止定时器 clearTimeout
```html
<body>
    <button>点击停止定时器</button>
    <script>
        var btn = document.querySelector('button');
        var timer = setTimeout(function() {
            console.log('爆炸了');
        }, 5000);
        btn.addEventListener('click', function() {
            clearTimeout(timer);
        })
    </script>
</body>
```

### 定时器 setInterval
setlnterval()方法重复调用一个函数，每隔这个时间，就去调用一次回调函数。
```html
<script>
	// 1. setInterval 
	// 语法规范：  window.setInterval(调用函数, 延时时间);
	setInterval(function() {
		console.log('继续输出');
	}, 1000);
	// 2. setTimeout  延时时间到了，就去调用这个回调函数，只调用一次 就结束了这个定时器
	// 3. setInterval  每隔这个延时时间，就去调用这个回调函数，会调用很多次，重复调用这个函数
</script>
```

#### 倒计时效果
```html
<body>
    <div>
        <span class="hour">1</span>
        <span class="minute">2</span>
        <span class="second">3</span>
    </div>
    <script>
        // 1. 获取元素 
        var hour = document.querySelector('.hour'); // 小时的黑色盒子
        var minute = document.querySelector('.minute'); // 分钟的黑色盒子
        var second = document.querySelector('.second'); // 秒数的黑色盒子
        var inputTime = +new Date('2019-5-1 18:00:00'); // 返回的是用户输入时间总的毫秒数
        countDown(); // 我们先调用一次这个函数，防止第一次刷新页面有空白 
        // 2. 开启定时器
        setInterval(countDown, 1000);
        function countDown() {
            var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
            var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数 
            var h = parseInt(times / 60 / 60 % 24); //时
            h = h < 10 ? '0' + h : h;
            hour.innerHTML = h; // 把剩余的小时给 小时黑色盒子
            var m = parseInt(times / 60 % 60); // 分
            m = m < 10 ? '0' + m : m;
            minute.innerHTML = m;
            var s = parseInt(times % 60); // 当前的秒
            s = s < 10 ? '0' + s : s;
            second.innerHTML = s;
        }
    </script>
</body>
```

### 清除定时器 clearInteaval
```html
<body>
    <button class="begin">开启定时器</button>
    <button class="stop">停止定时器</button>
    <script>
        var begin = document.querySelector('.begin');
        var stop = document.querySelector('.stop');
        var timer = null; // 全局变量  null是一个空对象
        begin.addEventListener('click', function() {
            timer = setInterval(function() {
                console.log('ni hao ma');
            }, 1000);
        })
        stop.addEventListener('click', function() {
            clearInterval(timer);
        })
    </script>
</body>
```

#### 发送短信
```html
<body>
    手机号码： <input type="number"> <button>发送</button>
    <script>
        // 按钮点击之后，会禁用 disabled 为true 
        // 同时按钮里面的内容会变化， 注意 button 里面的内容通过 innerHTML修改
        // 里面秒数是有变化的，因此需要用到定时器
        // 定义一个变量，在定时器里面，不断递减
        // 如果变量为0 说明到了时间，我们需要停止定时器，并且复原按钮初始状态
        var btn = document.querySelector('button');
        var time = 3; // 定义剩下的秒数
        btn.addEventListener('click', function() {
            btn.disabled = true;
            var timer = setInterval(function() {
                if (time == 0) {
                    // 清除定时器和复原按钮
                    clearInterval(timer);
                    btn.disabled = false;
                    btn.innerHTML = '发送';
                } else {
                    btn.innerHTML = '还剩下' + time + '秒';
                    time--;
                }
            }, 1000);
        })
    </script>
</body>
```

### this 指向问题
```html
<body>
    <button>点击</button>
    <script>
        // this 指向问题 一般情况下this的最终指向的是那个调用它的对象
        // 1. 全局作用域或者普通函数中this指向全局对象window（ 注意定时器里面的this指向window）
        console.log(this);
        function fn() {
            console.log(this);
        }
        window.fn();
        window.setTimeout(function() {
            console.log(this);
        }, 1000);
        // 2. 方法调用中谁调用this指向谁
        var o = {
            sayHi: function() {
                console.log(this); // this指向的是 o 这个对象
            }
        }
        o.sayHi();
        var btn = document.querySelector('button');
        // btn.onclick = function() {
        //     console.log(this); // this指向的是btn这个按钮对象
        // }
        btn.addEventListener('click', function() {
                console.log(this); // this指向的是btn这个按钮对象
            })
            // 3. 构造函数中this指向构造函数的实例
        function Fun() {
            console.log(this); // this 指向的是fun 实例对象
        }
        var fun = new Fun();
    </script>
</body>
```

## JS 执行机制

### JS 执行队列（同步/异步）
同步任务：同步任务都在主线程上执行，形成一个执行栈。
异步任务：JS的异步是通过回调函数实现的。一般而言，异步任务有以下三种类型
1、普通事件，如click、resize等
2、资源加载，如load、error等
3、定时器，包括setlnterval、setTimeout等

执行过程
1.先执行执行栈中的同步任务。
2.异步任务（回调函数）放入任务队列中。
3.一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行。
```html
<body>
    <script>
        // 第一个问题
        // console.log(1);
        // setTimeout(function() {
        //     console.log(3);
        // }, 1000);
        // console.log(2);
        // 2. 第二个问题
        // console.log(1);
        // setTimeout(function() {
        //     console.log(3);
        // }, 0);
        // console.log(2);
        // 3. 第三个问题
        console.log(1);
        document.onclick = function() {
            console.log('click');
        }
        console.log(2);
        setTimeout(function() {
            console.log(3)
        }, 3000)
    </script>
</body>
```
