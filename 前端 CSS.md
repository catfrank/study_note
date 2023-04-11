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

## 综合案例

### box 布局
```html
<head>
	<title>综合案例-产品模块</title>
    <style>
      * {
          margin: 0;
          padding: 0;
      }
      body {
          background-color: #f5f5f5;
      }
      a {
          color: #333;
          text-decoration: none;
      }
      .box {
          width: 298px;
          height: 415px;
          background-color:#fff;
          /* 让块级的盒子水平居中对齐 */
          margin: 100px auto;
      }
      .box img {
          /* 图片的宽度和父亲一样宽 */
          width: 100%;
      }
      .review {
          height: 70px;
          font-size: 14px;
          /* 因为这个段落没有 width属性 所有 padding不会撑开盒子的宽度 */
          padding: 0 28px;
          margin-top: 30px;
      }
      .appraise {
          font-size: 12px;
          color: #b0b0b0;
          margin-top: 20px;
          padding: 0 28px;
      }
      .info {
          font-size: 14px;
          margin-top: 15px;
          padding: 0 28px;
      }
      .info h4 {
          display: inline-block;
          font-weight: 400;
        
      }
      .info span {
          color: #ff6700;    
      }
      .info em {
          font-style: normal;
          color: #ebe4e0;
          margin: 0 6px 0 15px;
      }
    </style>
</head>
<body>
    <div class="box">
        <img src="images/img.jpg" alt="">
        <p class="review">快递牛，整体不错蓝牙可以说秒连。红米给力</p>
        <div class="appraise">来自于 117384232 的评价</div>
        <div class="info">
               <h4> <a href="#">Redmi AirDots真无线蓝...</a></h4>
               <em>|</em>
               <span> 99.9元</span>
        </div>
    </div>
</body>
```

## 圆角边框 border-radius
```css
div {
	width: 300px;
	height: 150px;
	background-color: pink;
	border-radius: 10px;
}
.yuanxing {
	width: 200px;
	height: 200px;
	background-color: pink;
	/* border-radius: 100px; */
	/* 50% 就是宽度和高度的一半  等价于 100px */
	border-radius: 50%;
}
.juxing {
	width: 300px;
	height: 100px;
	background-color: pink;
	/* 圆角矩形设置为高度的一半 */
	border-radius: 50px;
}
.radius {
	width: 200px;
	height: 200px;
	/* border-radius: 10px 20px 30px 40px; */
	/* border-radius: 10px 40px; */
	border-top-left-radius: 20px;
	background-color: pink;
}


<body>
    1. 圆形的做法:
    <div class="yuanxing"></div>
    2. 圆角矩形的做法:
    <div class="juxing"></div>
    3. 可以设置不同的圆角:
    <div class="radius"></div>
</body>
```

## 盒子阴影 box-shadow
```css
div {
	width: 200px;
	height: 200px;
	background-color: pink;
	margin: 100px auto;
	/* box-shadow: 10px 10px; */
}
/* 原先盒子没有影子,当我们鼠标经过盒子就添加阴影效果 */
div:hover {
	box-shadow: 10px 10px 10px -4px rgba(0, 0, 0, .3);
}
```

## 文字阴影 text-shadow
```css
div {
	font-size: 50px;
	color: orangered;
	font-weight: 700;
	text-shadow: 5px 5px 6px rgba(0, 0, 0, .3);
}
```

# CSS 浮动
float属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘
```css
div {
	float: left
}
```

## 浮动特性

### 脱标
脱离标准普通流的控制（浮）移动到指定位置（动），（俗称脱标）
浮动的盒子不再保留原先的位置

### 一行内显示
如果多个盒子都设置了浮动，则它们会按照属性值一行内显示井且顶端对奇排列。

### 行内块特征
任何元素都可以浮动。不管原先是什么模式的元素，添加浮动之后具有行内块元素相似的特性。
如果行内元素有了浮动,则不需要转换块级行内块元素就可以直接给高度和宽度

### 浮动元素与父级元素
```html
<style>
	.box {
		width: 1200px;
		height: 460px;
		background-color: pink;
		margin: 0 auto;
	}

	.left {
		float: left;
		width: 230px;
		height: 460px;
		background-color: purple;
	}

	.right {
		float: left;
		width: 970px;
		height: 460px;
		background-color: skyblue;
	}
</style>

<body>
    <div class="box">
        <div class="left">左侧</div>
        <div class="right">右侧</div>
    </div>
</body>
```

子代选择器
```css
.right>div {
	float: left;
	width: 234px;
	height: 300px;
	background-color: pink;
	margin-left: 14px;
	margin-bottom: 14px;
}
```

一个盒子里面有多个子盒子，如果其中一个盒子浮动了，那么其他兄弟也应该浮动，以防止引起问题。
浮动的盒子只会影响浮动盒子后面的标准流不会影响前面的标准流

## 清除浮动

### 额外标签法
额外标签法会在浮动元素末尾添加一个空的标签。例如`<div style:=”clear:both”></div>`或渚其他标签(如`<br/>`等)。新增的盒子要求必须是块级元素不能是行内元素

### 给父级添加 overflow
`overflow: hidden;`可以给父级添加overflow属性，将其属性值设置为hidden、auto或scroll

### 给父级添加 :after 伪元素
```html
<style>
	.clearfix:after {
		content: "";
		display: block;
		height: 0;
		clear: both;
		visibility: hidden;
	}
	
	.clearfix {
		/* IE6、7 专有 */
		*zoom: 1;
	}
</style>

<div class="box clearfix">
	<div class="damao">大毛</div>
	<div class="ermao">二毛</div>
</div>
```

### 给父级添加双伪元素
```html
<style>
	.clearfix:before,
	.clearfix:after {
		content: "";
		display: table;
	}

	.clearfix:after {
		clear: both;
	}

	.clearfix {
		*zoom: 1;
	}
</style>

<div class="box clearfix">
	<div class="damao">大毛</div>
	<div class="ermao">二毛</div>
</div>
```

# 定位
浮动可以让多个块级盒子一行没有缝隙排列显示，经常用于横向排列盒子。
定位则是可以让盒子自由的在某个盒子内移动位置或者固定屏幕中某个位置，并且可以压住其他盒子。

## 静态定位
静态定位按照标准流特性摆放位置，它没有边偏移
静态定位在布局时很少用到

## 相对定位 relative
`position: relative;`

## 绝对定位 absolute
如果没有祖先元素或者祖先元素没有定位，则以浏览器为准定位(Document文档)。
如果祖先元素有定位(相对、绝对、固定定位)，则以最近一级的有定位祖先元素为参考点移动位置。
绝对定位不再占有原先的位置。（脱标-脱离标准流）
`position: absolute;`
加了绝对定位的盒子不能通过margir:0 auto水平居中，但是可以通过以下计算方法实现水平和垂直居中。
```html
<style>
	.box {
		position: absolute;
		/* 1. left 走 50%  父容器宽度的一半 */
		left: 50%;
		/* 2. margin 负值 往左边走 自己盒子宽度的一半 */
		margin-left: -100px;
		top: 50%;
		margin-top: -100px;
		width: 200px;
		height: 200px;
		background-color: pink;
		/* margin: auto; */
	}
</style>
```

## 子绝父相
子盒子用绝对定位，父盒子用相对定位

## 固定定位 fixed
`position: fixed;`
固定定位的特点：（务必记住）
1.以浏览器的可视窗口为参照点移动元素。
跟父元素没有任何关系
不随滚动条滚动。
2.固定定位不在占有原先的位置。
固定定位也是脱标的，其实固定定位也可以看做是一种特殊的绝对定位。
```html
<style>
	.w {
		width: 800px;
		height: 1400px;
		background-color: pink;
		margin: 0 auto;
	}
	.fixed {
		position: fixed;
		/* 1. 走浏览器宽度的一半 */
		left: 50%;
		/* 2. 利用margin 走版心盒子宽度的一半距离 */
		margin-left: 405px;
		width: 50px;
		height: 150px;
		background-color: skyblue;
	}
</style>
<body>
    <div class="fixed"></div>
    <div class="w">版心盒子 800像素</div>
  
</body>
```

## 粘性定位 sticky
以浏览器的可视窗口为参照点移动元素（固定定位特点）
粘性定位占有原先的位置（相对定位特点）
必须添加top、left、right、bottom其中一个才有效
```html
<style>
	body {
		height: 3000px;
	}
	.nav {
		/* 粘性定位 */
		position: sticky;
		top: 0;
		width: 800px;
		height: 50px;
		background-color: pink;
		margin: 100px auto;
	}
</style>
<body>
    <div class="nav">我是导航栏</div>
</body>
```

## 定位叠放次序 z-index
`z-index: 2;`
数值可以是正整数、负整数或0，默认是auto,数值越大，盒子越靠上
如果属性值相同，则按照书写顺序，后来居上
数字后面不能加单位
只有定位的盒子才有z-index属性

## 定位的特殊性
绝对定位和固定定位也和浮动类似。
1.行内元素添加绝对或者固定定位，可以直接设置高度和宽度。
2.块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小。
3.脱标的盒子不会触发外边距塌陷
浮动元素、绝对定位（固定定位）元素的都不会触发外边距合并的问题。

## 浮动元素的特殊性
```html
<style>
	.box {
		/* 1.浮动的元素不会压住下面标准流的文字 */
		/* float: left; */
		/* 2. 绝对定位（固定定位） 会压住下面标准流所有的内容。 */
		position: absolute;
		width: 150px;
		height: 150px;
		background-color: pink;
	}
</style>
</head>
<body>
    <div class="box"></div>
    <p>阁下何不同风起，扶摇直上九万里</p>
</body>
```

## 淘宝焦点图
```html
<style>
	* {
		margin: 0;
		padding: 0;
	}
	li {
		list-style: none;
	}

	.tb-promo {
		position: relative;
		width: 520px;
		height: 280px;
		background-color: pink;
		margin: 100px auto;
	}

	.tb-promo img {
		width: 520px;
		height: 280px;
	}

	/* 并集选择器可以集体声明相同的样式 */
	.prev,
	.next {
		position: absolute;
		/* 绝对定位的盒子垂直居中 */
		top: 50%;
		margin-top: -15px;
		/* 加了绝对定位的盒子可以直接设置高度和宽度 */
		width: 20px;
		height: 30px;
		background: rgba(0, 0, 0, .3);
		text-align: center;
		line-height: 30px;
		color: #fff;
		text-decoration: none;
	}

	.prev {
		left: 0;
		/* border-radius: 15px; */
		border-top-right-radius: 15px;
		border-bottom-right-radius: 15px;
	}

	.next {
		/* 如果一个盒子既有left属性也有right属性，则默认会执行 left属性 同理  top  bottom  会执行 top */
		right: 0;
		/* border-radius: 15px; */
		border-top-left-radius: 15px;
		border-bottom-left-radius: 15px;
	}
	.promo-nav {
		position: absolute;
		bottom: 15px;
		left: 50%;
		margin-left: -35px;
		width: 70px;
		height: 13px;
		/* background-color: pink; */
		background: rgba(255,255,255, .3);
		border-radius: 7px;
	}
	.promo-nav li {
		float: left;
		width: 8px;
		height: 8px;
		background-color: #fff;
		border-radius: 50%;
		margin: 3px;
	}
	/* 不要忘记选择器权重的问题 */
   .promo-nav .selected {
		background-color: #ff5000;
	}
</style>

<body>
    <div class="tb-promo">
        <img src="images/tb.jpg" alt="">
        <!-- 左侧按钮箭头 -->
        <a href="#" class="prev"> &lt; </a>
        <!-- 右侧按钮箭头 -->
        <a href="#" class="next"> &gt; </a>
        <!-- 小圆点 -->
        <ul class="promo-nav">
            <li class="selected"></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
</body>
```

# 布局总结
1.标准流
可以上盒子上下排列或者左右排列，垂直的块级盒子显示就用标准流布局。
2.浮动
可以让多个块级元素一行显示或者左右对齐盒子，多个块级盒子水平显示就用浮动布局。
3.定位
定位最大的特点是有层叠的概念，就是可以让多个盒子前后叠压来显示。如果元素自由在某个盒子内移动就用定位布局。

# 显示与隐藏元素

## display
display:none;隐藏对象
display:block;除了转换为块级元素之外，同时还有显示元素的意思
display隐藏元素后不再占有原来的位置。
```html
<style>
.peppa {
	display: none;
	/* display: block; */
	width: 200px;
	height: 200px;
	background-color: pink;
}
</style>
```

## visibility
visibility属性用于指定一个元素应可见还是隐藏。
visibility:visible;元素可视
visibility:hidden;元素隐藏
visibility隐藏元素后，继续占有原来的位置
如果隐藏元素想要原来位置，就用visibility:hidden
如果隐藏元素不想要原来位置，就用display:none(用处更多）
```html
<style>
.baba {
	visibility: hidden;
	width: 200px;
	height: 200px;
	background-color: pink;
}
</style>
```

## overflow
```html
<style>
	.peppa {
		/* overflow: visible; */
		/* overflow: hidden; */
		/* scroll 溢出的部分显示滚动条  不溢出也显示滚动条 */
		/* overflow: scroll; */
		/* auto 溢出的时候才显示滚动条 不溢出不显示滚动条 */
		/* overflow: auto; */
		width: 200px;
		height: 200px;
		border: 3px solid pink;
		margin: 100px auto;
	}
</style>
```
一般情况下，我们都不想让溢出的内容显示出来，因为溢出的部分会影响布局。
但是如果有定位的盒子，请慎用overflow:hidden因为它会隐藏多余的部分。

# CSS 高级技巧

## 精灵图
一个网页中往往会应用很多小的背景图像作为修师，当网页中的图像过多时，服务器就会颜繁接收和发送请求图片，造成服务然请求压力过大，这将大大降低网页的加载速度。

精灵技术目的：
为了有效地减少服务器接收和发送请求的次数，提高页面的加载速度

使用精灵图核心：
1.精灵技术主要针对于背景图片使用。就是把多个小背景图片整合到张大图片中。
2.这个大图片也称为sprites精灵图或者雪碧图
3.移动背景图片位置，此时可以使用background-position.
4.移动的距离就是这个目标图片的×和y坐标。注意网页中的坐标有所不同
5.因为一般情况下都是往上往左移动，所以数值是负值。
6.使用精灵图的时候需要精确测量，每个小背景图片的大小和位置。

使用精灵图核心总结：
1.精灵图主要针对于小的背景图片使用。
2.主要借助于背景位置来实现--background-position.
3.一般情况下精灵图都是负值。(千万注意网页中的坐标：轴右边走是正值，左边走是负值，y轴同理。)

```html
<style>
	.box1 {
		width: 60px;
		height: 60px;   
		margin: 100px auto;
		background: url(images/sprites.png) no-repeat   -182px 0;
	  
	}
	.box2 {
		width: 27px;
		height: 25px;
		/* background-color: pink; */
		margin: 200px;
		background: url(images/sprites.png) no-repeat  -155px -106px;

	}
</style>

<body>
    <div class="box1"></div>
    <div class="box2"></div>
</body>
```

## 字体图标
字体图标使用场景：主要用于显示网页中通用、常用的一些小图标
精灵图是有诸多优点的，但是缺点很明显。
1.图片文件还是比较大的。
2.图片本身放大和缩小会失真。
3.一旦图片制作完毕想要更换非常复杂。
此时，有一种技术的出现很好的解决了以上问题，就是字体图标iconfont.
字体图标可以为前端工程师提供一种方便高效的图标使用方式，展示的是图标，本质属于字体。

字体优点：
轻量级：一个图标字体要比一系列的图像要小。一旦字体加载了，图标就会马上渲染出来，减少了服务器请求
灵活性：本质其实是文字，可以很随意的改变颜色、产生阴影、透明效果、旋转等
兼容性：几乎支持所有的浏览器，请放心使用

## 字体图标
如果工作中，原来的字体图标不够用了，我们需要添加新的字体图标到原来的字体文件中。
把压缩包里面的selection.json从新上传，然后选中自己想要新的图标，从新下载压缩包，并替换原来的文件即可。

## CSS 三角
```html
<style>
	.box1 {
		width: 0;
		height: 0;
		/* border: 10px solid pink; */
		border-top: 10px solid pink;
		border-right: 10px solid red;
		border-bottom: 10px solid blue;
		border-left: 10px solid green;
	}
	.box2 {
		width: 0;
		height: 0;
		border: 50px solid transparent;
		border-left-color: pink;
		margin: 100px auto;
	}
	.jd {
		position: relative;
		width: 120px;
		height: 249px;
		background-color: pink;
	}
	.jd span {
		position: absolute;
		right: 15px;
		top: -10px;
		width: 0;
		height: 0;
		/* 为了照顾兼容性 */
		line-height: 0;  
		font-size: 0;
		border: 5px solid transparent;
		border-bottom-color: pink;
	}
</style>

<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="jd">
        <span></span>
    </div>
</body>
```

## 界面样式

### 鼠标样式
```html
<li style="cursor: default;">我是默认的小白鼠标样式</li>
<li style="cursor: pointer;">我是鼠标小手样式</li>
<li style="cursor: move;">我是鼠标移动样式</li>
<li style="cursor: text;">我是鼠标文本样式</li>
<li style="cursor: not-allowed;">我是鼠标禁止样式</li>
```

### 轮廓线
```html
<style>
	input, textarea {
		/* 取消表单轮廓 */
		outline: none;
	}
	textarea {
		/* 防止拖拽文本域 */
		resize: none;
	}
</style>
<body>
    <!-- 1. 取消表单轮廓 -->
    <input type="text">
    <!-- 2. 防止拖拽文本域 -->
    <textarea name="" id="" cols="30" rows="10"></textarea>
</body>
```

### vertical-align 属性
```html
<style>
	img {
		/* vertical-align: bottom; */
		/* 让图片和文字垂直居中 */
		vertical-align: middle;
		/* vertical-align: top; */
	}
	textarea {
		vertical-align: middle;
	}
</style>

<body>
    <img src="images/ldh.jpg" alt="">  pink老师是刘德华
    <br>
    <textarea name="" id="" cols="30" rows="10"></textarea> 请您留言
</body>
```

### 解决图片底部空白
```html
<style>
	div {
		border: 2px solid red;
	}
	img {
		/* vertical-align: middle; */
		display: block;
	}
</style>

<body>
    <div>
        <img src="images/ldh.jpg" alt="">
    </div> 
</body>
```

### 单行溢出文字省略号显示
```html
<style>
	div {
		width: 150px;
		height: 80px;
		background-color: pink;
		margin: 100px auto;
		/* 这个单词的意思是如果文字显示不开自动换行 */
		/* white-space: normal; */
		/* 1.这个单词的意思是如果文字显示不开也必须强制一行内显示 */
		white-space: nowrap;
		/* 2.溢出的部分隐藏起来 */
		overflow: hidden;
		/* 3. 文字溢出的时候用省略号来显示 */
		text-overflow: ellipsis;
	}
</style>

<body>
    <div>
        啥也不说，此处省略一万字
    </div>
</body>
```

### 多行溢出文字省略号显示
适合移动端，否则容易出现兼容性问题
```html
<style>
	div {
		width: 150px;
		height: 65px;
		background-color: pink;
		margin: 100px auto;
		overflow: hidden;
		text-overflow: ellipsis;
		/* 弹性伸缩盒子模型显示 */
		display: -webkit-box;
		/* 限制在一个块元素显示的文本的行数 */
		-webkit-line-clamp: 3;
		/* 设置或检索伸缩盒对象的子元素的排列方式 */
		-webkit-box-orient: vertical;
	}
</style>


<body>
    <div>
        啥也不说，此处省略一万字,啥也不说，此处省略一万字此处省略一万字
    </div>
</body>
```

### 布局技巧
#### margin负值
```html
<style>
	ul li {
		position: relative;
		float: left;
		list-style: none;
		width: 150px;
		height: 200px;
		border: 1px solid red;
		margin-left: -1px;
	}

	/* ul li:hover {
	   1. 如果盒子没有定位，则鼠标经过添加相对定位即可
	position: relative;
	border: 1px solid blue;
   } */
	ul li:hover {
		/* 2.如果li都有定位，则利用 z-index提高层级 */
		z-index: 1;
		border: 1px solid blue;
	}
</style>

<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul>
</body>
```

#### 文字围绕
浮动
```html
<style>
	* {
		margin: 0;
		padding: 0;
	}
	.box {
		width: 300px;
		height: 70px;
		background-color: pink;
		margin: 0 auto;
		padding: 5px;
	}
	.pic {
		float: left;
		width: 120px;
		height: 60px;
		margin-right: 5px;
	}
	.pic img {
		width: 100%;
	}
</style>

<body>
    <div class="box">
        <div class="pic">
            <img src="images/img.png" alt="">
        </div>
        <p>【集锦】热身赛-巴西0-1秘鲁 内马尔替补两人血染赛场</p>
    </div>
</body>
```

# HTML5 新特性

## 语义化标签
```html
<header>头部标签</header>
<nav>导航栏标签</nav>
<section>某个区域</section>
```
