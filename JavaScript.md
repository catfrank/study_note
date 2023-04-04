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

## 预解析
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

## 对象
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