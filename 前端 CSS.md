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

## 边框 border
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

### 表格细线边框
```css
td, th {
	border: 1px solid pink;
	/* 合并相邻的边框 */
	border-collapse: collapse;
	font-size: 14px;
	text-align: center;
}
```

### 边框会影响盒子大小
```css
/* 我们需要一个200*200的盒子, 但是这个盒子有10像素的红色边框 */
div {
	width: 180px;
	height: 180px;
	background-color: pink;
	border: 10px solid red;
}
```

## 内边距 padding
```css
div {
	width: 200px;
	height: 200px;
	background-color: pink;
	padding-left: 20px;
	padding-top: 30px;
}
```

### 内边距复合写法
```css
div {
	width: 200px;
	height: 200px;
	background-color: pink;
	/* padding-left: 5px;
	padding-top: 5px;
	padding-bottom: 5px;
	padding-right: 5px; */
	/* 内边距复合写法(简写) */
	/* padding: 5px;  四周5px边距 */
	/* padding: 5px 10px;  上下5px边距 左右10px边距 */
	/* padding: 5px 10px 20px;  上5px边距 左右10px边距 下20px边距 */
	padding: 5px 10px 20px 30px; /* 顺时针 上5px 右10px 下20px 左30px */
}
```

### 边距会影响盒子大小
如果保证盒子跟效果图大小保持一致，则让width/height减去多出来的内边距大小即可。

#### 新浪导航案例
```html
<head>
	<style>
		.nav {
			height: 41px;
			border-top: 3px solid #ff8500;
			border-bottom: 1px solid #edeef0;
			background-color: #fcfcfc;
			line-height: 41px;
		}
		.nav a {
			/* a属于行内元素 此时必须要转换 行内块元素 */
			display: inline-block;
			height: 41px;
			padding: 0 20px;
			font-size: 12px;
			color: #4c4c4c;
			text-decoration: none;
		}
		.nav a:hover {
			background-color: #eee;
			color: #ff8500;
		}
	</style>
</head>
<body>
    <div class="nav">
        <a href="#">新浪导航</a>
        <a href="#">手机新浪网</a>
        <a href="#">移动客户端</a>
        <a href="#">微博</a>
        <a href="#">三个字</a>
    </div>
</body>
```

## 外边距 margin
```html
<head>
	<style>
      div {
          width: 200px;
          height: 200px;
          background-color: pink;
      }
      /* .one {
          margin-bottom: 20px;
      } */
      .two {
          /* margin-top: 20px; */
          /* margin: 30px; */
          margin: 30px 50px;
      }
    </style>
</head>
<body>
    <div class="one">1</div>
    <div class="two">2</div>
</body>
```

### 盒子水平居中
外边距可以让块级盒子水平居中，但是必须满足两个条件：
盒子必须指定了宽度(width).
盒子左右的外边距都设置为auto.
```html
<style>
  .header {
	  width: 900px;
	  height: 200px;
	  background-color: pink;
	  margin: 100px auto;
  }
</style>

<div class="header"></div>
```

### 行内/行内块元素水平居中
行内元素或者行内块元素水平居中给其父元素添加 text-align:center 即可
```html
<style>
	.header {
		width: 900px;
		height: 200px;
		background-color: pink;
		margin: 100px auto;
		text-align: center;
	}
  /* 行内元素或者行内块元素水平居中给其父元素添加 text-align:center 即可 */
</style>

<div class="header">
	<span>里面的文字</span>
</div>
	<div class="header">
	<img src="down.jpg" alt="">
</div>
```

### 外边距合并

#### 相邻块元素外边距合并
当上下相邻的两个块元素（兄弟关系）相遇时，如果上面的元素有下外边距margir-bottom,下面的元素有上外边距margin-top,则他们之间的垂直间距不是margin-bottom与margin-top之和。取两个值中的较大者这种现象被称为相邻块元素垂直外边距的合并。
```html
<style>
	.damao, .ermao {
		width: 200px;
		height: 200px;
		background-color: pink;
	}
	.damao {
		margin-bottom: 100px;
	}
	.ermao {
		margin-top: 200px;
	}
</style>

<body>
    <div class="damao">大毛</div>
    <div class="ermao">二毛</div>
</body>
```

#### 嵌套元素外边距合并
解决方案：
可以为父元素定义上边框。
可以为父元素定义上内边距。
可以为父元素添加overflow:hidden。
```html
<style>
	.father {
		width: 400px;
		height: 400px;
		background-color: purple;
		margin-top: 50px;
		/* border: 1px solid red; */
		/* border: 1px solid transparent; */
		/* padding: 1px; */
		overflow: hidden;
	}
	.son {
		width: 200px;
		height: 200px;
		background-color: pink;
		margin-top: 100px;
	}
</style>

<body>
    <div class="father">
        <div class="son"></div>
    </div>
</body>
```

### 清除内外边距
```html
<style>
	/* 这句话也是我们css 的第一行代码 */
   * {
	   margin: 0;
	   padding: 0;
   }
   span {
	   background-color: pink;
	   margin: 20px;
   }
</style>

<body>
   123
   <ul>
       <li>abcd</li>
   </ul>
   <span>行内元素尽量只设置左右的内外边距</span>
</body>
```