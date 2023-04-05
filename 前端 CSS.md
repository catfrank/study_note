# 背景

## 背景图片
```css
body {
	background-image: url(images/bg.jpg);
	background-repeat: no-repeat;
	/* background-position: center top; */
	background-position: center 40px;
}
```

## 背景位置-精确位置
```css
div {
	width: 300px;
	height: 300px;
	background-color: pink;
	background-image: url(images/logo.png);
	background-repeat: no-repeat;
	/* 20px 50px; x轴一定是 20  y轴一定是 50 */
	/* background-position: 20px 50px; */
	/* background-position: 50px 20px; */
	background-position: 20px;
}
```

## 背景位置-混合位置
```css
div {
	width: 300px;
	height: 300px;
	background-color: pink;
	background-image: url(images/logo.png);
	background-repeat: no-repeat;
	/* 20px center  一定是x 为 20  y 是 center  等价于   background-position: 20px */
	/* background-position: 20px center; */
	/* 水平是居中对齐  垂直是 20 */
	background-position: center 20px;
}
```

## 背景固定
```css
div {
	...
	background-attachment: fixed;
	...
}
```

## 复合写法
当使用简写属性时，没有特定的书写顺序，一般习惯约定顺序为：
background:背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置；
```css
body {
	...
	background: black url(images/bg.jpg) no-repeat fixed center top;
	...
}
```

## 背景色半透明
```css
div {
	...
	background: rgba(0, 0, 0, .3);
	...
}
```

# 三大特性

## 层叠性
遵循的原则是就近原则，哪个样式离结构近，就执行哪个样式
样式不冲突，不会层叠
```css
div {
   color: red; 
   font-size: 12px;
}
div {
   color: pink; /*会覆盖red颜色*/
}
```

## 继承性
```css
div {
	color: pink;
	font-size: 14px;
}
/*div内的标签会继承div的样式,子标签只会继承颜色、字体样式*/
```

### 行高的继承
```css
body {
	color: pink;
	/* font: 12px/24px 'Microsoft YaHei'; */
	font: 12px/1.5 'Microsoft YaHei';
}
div {
	/* 子元素继承了父元素 body 的行高 1.5 */
	/* 这个1.5 就是当前元素文字大小 font-size 的1.5倍   所以当前div 的行高就是21像素 */
	font-size: 14px; 
}
p {
	/* 1.5 * 16 =  24 当前的行高 */
	font-size: 16px;
}
/* li 么有手动指定文字大小  则会继承父亲的 文字大小  body 12px 所以 li 的文字大小为 12px 
```

## 优先级
权重：！important>行内style="">ID选择器>类/伪类选择器>元素选择器>继承/*
（类选择器永远大于元素选择器，id选择器永远大于类选择器，以此类推。）
a链接浏览器默认制定了一个样式 蓝色的 有下划线  a {color: blue;}

### 权重叠加
复合选择器会有权重叠加的问题
```html
<style>
	/* ul li 权重  0,0,0,1 + 0,0,0,1  =  0,0,0,2     2 */
	ul li {
		color: green;
	}
	/* li 的权重是 0,0,0,1    1 */
	li {
		color: red;
	}
	/* .nav li  权重    0,0,1,0  +  0,0,0,1  =  0,0,1,1    11 */
	.nav li {
		color: pink;
	}
</style>
<body>
    <ul class="nav">
        <li>大猪蹄子</li>
    </ul>
</body>
```

# 盒子模型
所谓盒子模型：就是把HTML页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器。
CSS盒子模型本质上是一个盒子，封装周围的HTML元素，它包括：边框、外边距、内边距、和实际内容

## 边框
```css
div {
	/* border-width 边框的粗细  一般情况下都用 px */
	border-width: 5px;
	/* border-style 边框的样式  solid 实线边框   dashed 虚线边框  dotted 点线边框*/
	border-style: solid;
	/* border-style: dashed; */
	/* border-style: dotted; */
	/* border-color 边框的颜色  */
	border-color: pink;
}
```

### 边框的复合写法
```css
div {
	width: 300px;
	height: 200px;
	/* border-width: 5px;
	border-style: solid;
	border-color: pink; */
	/* 边框的复合写法 简写:  */
	/* border: 5px solid pink; */
	/* 上边框 */
	border-top: 5px solid pink;
	/* 下边框 */
	border-bottom: 10px dashed purple;
}

/* 请给一个 200*200 的盒子，设置上边框为红色，其余边框为蓝色 */
div {
	width: 200px;
	height: 200px;
	/* border-top: 1px solid red;
	border-bottom: 1px solid blue;
	border-left: 1px solid blue;
	border-right: 1px solid blue; */
	/* border包含四条边 */
	border: 1px solid blue;
	/* 层叠性 只是层叠了 上边框啊 */
	border-top: 1px solid red;
}
```