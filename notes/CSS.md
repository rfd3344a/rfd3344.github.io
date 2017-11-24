---
layout: notes
published: true
---

# CSS Base
```
<link rel="stylesheet" type="test/css" href="./templates/CSS.css">
```
## Selector

### CSS_Selector
```
#red {color: red;}		ID 
.red {color: red;}		Class
div p{	}   	/* child and grandchild    	*/
div > p{	}  	/* child only    			*/
div ~ p {	}	/* div之后的同级p	*/
p: nth-of-type(2)  	  
选择属于其父元素第二个 <p> 元素的每个 <p> 元素
p:nth-child(2){	}	
    第二个子元素的所有<p> 元素 */
p: nth-last-child(3)   
    选择 倒数第三个p元素

p:nth-child(even) 
    选择偶数个
```
### Pseudo Class 
```
p: first-line { 	}
p: first-letter{	}
p: first-child{	}
p: last-child{	}
```
### Before After 
###### P 后插入图片
```
p: after {   
    content: url('./    pic1.jpg');
    display: block;
}
```
### :target
```
<style>
#news1:target  {
  background-color: skyblue;
}
#news2:target  {
  background-color: tomato;
}
</style>

<a href="#news1"> Title 1</a> 
<a href="#news2"> Title 2</a>

<p id="news1">New content 1...</p>
<p id="news2">New content 2...</p>
```

# Layout 
## Box
margin | border | padding | content 
### border
```
border: 2px solid black;
```
border-radius: 10px;
border-width: 5px;
border-style: dotted / dashed / solid /double / groove / ridge / inset
```
border-style:dotted double solid double;
```
border-color: red;
### Heigh/width
height:
width:
max-height:	
max-width:
min-height:	
min-width:

## Float
float: left/right
clear: left/right/both

## Position 
absolute: 相对于第一个父元素进行定位( static 定位以外)
fixed: 固定浏览器窗口
relative: 相对于其正常位置进行定位。
static: 默认值 
inherit: 规定应该从父元素继承 position 属性的值

z-index 
top, right, bottom, left
### Other
overflow: 	visible, hidden, scroll ;
overflow-x:	
overflow-y:

##Flexible Box

-----------
-----------
background, color

font, text,  decoration, writing mode

list, table 
Image, Transform 

content 
User Interface 
Multi-column


 
Animation, Transition
Printing  
Media Queries
webkit 

--------
---------

# Text
## font 
font-family: 		"Brush Script MT" | 
				    Edwardian Script ITC
font-style: 		oblique/ italic/ normal     
font-weight: 		bold/ bolder/ 100-900  
font-size: 		12px/ 12pt/ medium/ 50%
font-variant: 		small-caps/ normal
text-indent: 		10px/ 20% 				首行锁进
text-align: 		left/ right/ center／justify(双端)	对齐方式
text-decoration: 	none/ underline/ overline/ linethrough	
text-transform: 	capitalize/ uppercase/ lowercase
text-align:center	center	
line-height: 	16px/ 2em
word-wrap: break-word; 换行
white-space: nowrap;   不换行
## decoration

## writing mode
# Image Color 
.img-responsive 
.img-thumbnail
.img-circle
-webkit-filter: grayscale(100%);
## Transform
transform: rotate(20deg);
Transition 
-webkit-transition: width 2s, height 4s; /* Safari */
transition: width 2s, height 4s;

ease - specifies a transition effect with a slow start, then fast, then end slowly (this is default)
linear - specifies a transition effect with the same speed from start to end
ease-in - specifies a transition effect with a slow start
ease-out - specifies a transition effect with a slow end
ease-in-out - specifies a transition effect with a slow start and end
	cubic-bezier(n,n,n,n) - lets you define your own values in a cubic-bezier function
## background
background: url(“<location>”)
background-repeat: repeat/ repeat-x/ repeat-y/ no-repeat
background-attachment: scroll/ fixed/ inherit
background-position: <x> <y>| [top/ right/ left/ bottom] | center
background-attachment:	fix   		位置固定
background-blend-mode: normal|multiply|screen|overlay|darken|lighten|color-dodge|saturation|color|luminosity;

### Google Map 
Transfer  to Monochrome  黑白色

```
-webkit-filter: grayscale(100%);
-moz-filter: grayscale(100%);
-ms-filter: grayscale(100%);
-o-filter: grayscale(100%);
filter: grayscale(100%);
```
# Icon 
```
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
```
```
<i class="fa fa-cloud"></i>
<i class="fa fa-heart"></i>
<i class="fa fa-car"></i>
<i class="fa fa-file"></i>
<i class="fa fa-bars"></i>
```
```
:before{
	content: '\f041';
	font-family: fontawesome;
}
```
##### 100%宽 自适应高度
```
background-repeat: no-repeat;
background-size: contain;
width: 100%;
height: 0;
padding-bottom: 100%; //按比例选值
```

# List 
list-style: circle, square, 
            upper-roman(1234 order), 
            lower-alpha (abcd order)
list-style-image:		url('');
list-style-position	inside;     第二行左移	
list-style-type	

# Table 
border-collapse: 	collapse
width:
height:
text-align:	left, right, center
vertical-align: 	bottom;
tr:nth-child(even)	 {	}
overflow-x:		auto
# Action 
link/ visited/ hover/ active 正确顺序(链接访问过)
a: link {color: green;}
a: visited {color: grey;}
a: hover {color: blue;}    			鼠标滑过
a: active {color: yellow;}
## Animation
### animation-timing-function
```
#div1 {animation-timing-function: linear;}
#div2 {animation-timing-function: ease;}
#div3 {animation-timing-function: ease-in;}
#div4 {animation-timing-function: ease-out;}
#div5 {animation-timing-function: ease-in-out;}
```

## Transition
```
<div> </div>
<style> 
div {
    width: 100px;
    height: 100px;
    background: red;
    -webkit-transition: all 2s; /* For Safari 3.1 to 6.0 */
    transition: all 2s;
}

div:hover {
    width: 200px;
    background: green;
}
</style>
```
### 延迟
-webkit-transition-delay: 1s; /* Safari */
transition-delay: 1s;
transition-duration：
transition-property
transition-timing-function
## Video
autoplay 
control 
loop 

```
<video id= "video2" height="700"autoplay control loop src="./../statistic/Video2.mp4"></video>
```
## Others
content: ‘hello’;
linear-gradient(to bottom/ blue/ white);
background: radial-gradient
z-index:
height: calc(100vh - 103px); 
100vh  屏幕高度100%

color:blue !important;  
```
@media
/*  orientation: portrait / landscape  */
@media (max-width:1023px) {    }

/* Tablet  768x1024 */
@media (min-width:768px) and (max-width:1024px) {   }
/*   Iphone5       320x568 
     Iphone6Plus   414x736    */
@media (min-width:300px) and (max-width:767px) {   }
```


## content 
## User Interface 
## Multi-column
## Printing  
## Media Queries
## webkit 

# LESS
```
<script src="//cdnjs.cloudflare.com/ajax/libs/less.js/2.7.2/less.min.js"></script>
```
### Create Variables @:
```
@the-border: 1px;        
h2{
   border-right: @the-border * 3;
}
```
### 类Class
```
.rounded-corners (@radius: 5px 10px 8px 2px) {
  -webkit-border-radius: @radius;
  -moz-border-radius: @radius;
  border-radius: @radius;
}
#header {
  .rounded-corners;
}
#footer {
  .rounded-corners(10px 25px 35px 0px);
}
```
### 子类中直接写CSS
``` 
#header {
  h1 {
    font-size: 26px;
    font-weight: bold;
  }
  p {
    font-size: 16px;
    a {
      text-decoration: none;
      color: red;
      &:hover {
        border-width: 1px;
        color: #fff;
      }
    }
  }
}
```
# HTML
## Link   JS_CSS

### Special Characters 特殊字符
```
 &lt;		<
<!-- comments  -->
<marquee id=a onmouseover-a.stop() onmouseout=a.start()> TEST </marquee>
        滚动
```
## Scalable Vector Graphics (SVG)
```
<hr> 		水平线
Example Scalable Vector Graphics (SVG)
<svg width="100" height="100"> 		
	<circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
</svg>
```
## Head
```
<head>	
<title>	
<base>	default address or target 
<link> 	relationship between document, external resource
<meta>	Defines metadata about an HTML document
<script>
<style>	
```
## Text
``` 
<b>			bold 
<em>		 	emphasized  
<i>			italic 
<small>		smaller 
<strong>	 	important 
<sub>		 	subscripted 
<sup>		 	superscripted 
<ins>		 	inserted 
<del>		 	deleted 
<mark>		marked/highlighted 
```
## Quote
```
<abbr>	 		abbreviation_acronym
<address>	
<bdo>			text_direction
<blockquote>	quoted
<cite>			title
<q>				inline_quotation
```
## Code
```
<code>&lt; body &gt; </code>	
<kbd>ctrl</kbd>
<samp>	 		computer_output
<var>	 		variable
<pre>	 		preformatted text
```
## Link
```
<a href="url">text</a>		Hyperlink
<a href="http://www.google.com" target="_blank">
_blank		Opens the linked document in a new window or tab
_self			Opens the linked document in the same frame as it was clicked (this is default)
_parent		Opens the linked document in the parent frame
_top			Opens the linked document in the full body of the window
framename		Opens the linked document in a named frame
```
## Image
```
<img>			image
<alt>			图像无法显示时, 替代文本
<map>			image-map
<area>		clickable area inside an image-map
```
###### Example:
```
<img src="planets.gif" width="145" height="126" alt="Planets" usemap="#planetmap">
<map name="planetmap">
	<area shape="rect" coords="0,0,82,126" alt="Sun" href="sun.htm">
	<area shape="circle" coords="90,58,30" alt="Mercury" href="mercur.htm">
	<area shape="circle" coords="124,58,80" alt="Venus" href="venus.htm">
</map>
```
## List
```
<ul>	unordered list
<ol>	ordered list
<li>	list item
<dl>	Description list
<dt>	description list
<dd>	description in a description list
```
## Blocks
```
<div>	 	block-level
<span>		inline
<iframe>		inline frame
```
## Form
```
<form>
<input type="text">		one-line input field for text input
<input type="radio"> 	Radio button
<input> <datalist> <option>
<select> <option>		selection list
<textarea>
<button>
<input type="submit">   button for submitting 
<form action="action_page.php">		action when submit
<form method="get">	 when submit GET or POST (when submit)

<fieldset>	Groups related elements in a form
<legend>	Defines a caption for a <fieldset> element
<keygen>	Defines a key-pair generator field (for forms)
<output>	Defines the result of a calculation
```

## Iframe
##### 添加 IframeClass 到iframe 
```
$(document).ready(function() {  
$('iframe').on("load", function() { 
$( "iframe" ).contents().find("body").html( "1111" );
$( "iframe" ).contents().find("body").addClass("IframeClass");
	});
});
```


#  Sass 
## Variables
```
$primary-color: #333;
```
## Nesting
```
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
}
```
## Mixins
```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```
## Extend
```
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}
.success {
  @extend .message;
  border-color: green;
}
```
## Operators
```
width: 300px / 960px * 100%;
```








