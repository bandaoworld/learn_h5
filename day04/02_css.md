# 1. CSS 的复合选择器
## 1.1 什么是复合选择器 
根据选择器的类型把选择器分为基础选择器和复合选择器
- 复合选择器可以更准确、更高效的选择目标元素（标签） 
- 复合选择器是由两个或多个基础选择器，通过不同的方式组合而成的 
- 常用的复合选择器包括：后代选择器、子选择器、并集选择器、伪类选择器等等 
## 1.2 后代选择器 (重要） 
后代选择器又称为包含选择器，可以选择父元素里面子元素。其写法就是把外层标签写在前面，内层标签写在后面，中间用空格分隔。当标签发生嵌套时，内层标签就成为外层标签的后代。
```css
ol li {
    /*  选择 ul 里面所有的 li标签元素  */
    color: pink;
}
```
- 元素1 和 元素2 中间用空格隔开 
- 元素1 是父级，元素2 是子级，最终选择的是元素2 
- 元素2 可以是儿子，也可以是孙子等，只要是元素1 的后代即可 
- 元素1 和 元素2 可以是任意基础选择器 
## 1.3 子选择器 (重要）
子元素选择器（子选择器）只能选择作为某元素的最近一级子元素。简单理解就是选亲儿子元素.
```css
.body > li {
    /*  选择 .body 里面所有最近一级 li 标签元素  */
    font-size: 20px;
}
```
- 元素1 和 元素2 中间用 大于号 隔开 
- 元素1 是父级，元素2 是子级，最终选择的是元素2 
- 元素2 必须是亲儿子，其孙子、重孙之类都不归他管. 你也可以叫他 亲儿子选择器
## 1.4 并集选择器 (重要）
并集选择器可以选择多组标签, 同时为他们定义相同的样式。通常用于集体声明.   
并集选择器是各选择器通过英文逗号（,）连接而成，任何形式的选择器都可以作为并集选择器的一部分。
```css
div, 
 p,
.pig {
    color: pink;
 }
```
- 并集选择器竖着写 
- 最后一个选择器 不需要加逗号
- 元素1 和 元素2 中间用逗号隔开 
- 逗号可以理解为和的意思 
- 并集选择器通常用于集体声明
## 1.5 伪类选择器
伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或选择第1个，第n个元素。 
伪类选择器书写最大的特点是用冒号（:）表示，比如 :hover 、:first-child 。 
因为伪类选择器很多，比如有链接伪类、结构伪类等，所以这里先给大家讲解常用的链接伪类选择器。
## 1.6 链接伪类选择器
```css
/* 1.未访问的链接 a:link  把没有点击过的(访问过的)链接选出来，受缓存影响 */
a:link {
    color: #333;
    text-decoration: none;
}
/*2. a:visited 选择点击过的(访问过的)链接 */
a:visited {
    color: orange;
}
/*3. a:hover 选择鼠标经过的那个链接 */
a:hover {
    color: skyblue;
}
/* 4. a:active 选择的是我们鼠标正在按下还没有弹起鼠标的那个链接 */
a:active {
    color: green;
}
```  
注意事项 
- 为了确保生效，请按照 LVHA 的循顺序声明 :link－:visited－:hover－:active。 
- 记忆法：love hate 或者 lv 包包 hao 。 
- 因为 a 链接在浏览器中具有默认样式，所以我们实际工作中都需要给链接单独指定样式
  
链接伪类选择器实际工作开发中的写法： 
```css
/* a 是标签选择器  所有的链接 */  
a {        
    color: gray; 
    text-decoration: none;
} 
/* :hover 是链接伪类选择器 鼠标经过 */ 
a:hover {     
    color: red;  /* 鼠标经过的时候，由原来的 灰色 变成了红色 */ 
    text-decoration: underline;
}  
```
## 1.7 :focus 伪类选择器 
:focus 伪类选择器用于选取获得焦点的表单元素。 
焦点就是光标，一般情况 `<input>` 类表单元素才能获取，因此这个选择器也主要针对于表单元素来说。 
```css
input:focus {
    /* 有光标才会有效果 */
    /* 选中框的背景 */
    background-color: #cecece;
    /* 输入的文字效果 */
    color: rgb(0, 162, 255);
}
```
## 1.8 复合选择器总结 
|     选择器     |          作用          |       特征       | 使用情况 |           隔开符号及用法           |
| :------------: | :--------------------: | :--------------: | :------: | :--------------------------------: |
|   后代选择器   |    用来选择后代元素    |  可以是子孙后代  |   较多   |          符号是空格.nav a          |
|   子代选择器   |    选择最近一级元素    |    只选亲儿子    |   较少   |          符号是大于.nav>p          |
|   并集选择器   | 选择某些相同样式的元素 | 可以用于集体声明 |   较多   |      符号是逗号.nav, .header       |
| 链接伪类选择器 |   选择不同状态的链接   |    跟链接相关    |   较多   | 重点记住a{}和a:hover实际开发的写法 |
|  :focus选择器  |   选择获得光标的表单   |    跟表单相关    |   较少   |      input:focus记住这个写法       |
# 2. CSS 的元素显示模式 
## 2.1 什么是元素显示模式
作用：网页的标签非常多，在不同地方会用到不同类型的标签，了解他们的特点可以更好的布局我们的网页。 
元素显示模式就是元素（标签）以什么方式进行显示，比如`<div>`自己占一行，比如一行可以放多个`<span>`。
HTML 元素一般分为块元素和行内元素两种类型。 
## 2.2 块元素
常见的块元素有`<h1>`~`<h6>`、`<p>`、`<div>`、`<ul>`、`<ol>`、`<li>`等，其中 `<div>` 标签是最典型的块元素。 
块级元素的特点： 
1. 比较霸道，自己独占一行。 
2. 高度，宽度、外边距以及内边距都可以控制。 
3. 宽度默认是容器（父级宽度）的100%。 
4. 是一个容器及盒子，里面可以放行内或者块级元素。
## 2.2 行内元素 
常见的行内元素有 `<a>`、`<strong>`、`<b>`、`<em>`、`<i>`、`<del>`、`<s>`、`<ins>`、`<u>`、`<span>`等，其中`<span>` 标签是最典型的行内元素。有的地方也将行内元素称为内联元素
行内元素的特点： 
1. 相邻行内元素在一行上，一行可以显示多个。 
2. 高、宽直接设置是无效的。 
3. 默认宽度就是它本身内容的宽度。 
4. 行内元素只能容纳文本或其他行内元素。 
注意： 
- 链接里面不能再放链接 
- 特殊情况链接 `<a>` 里面可以放块级元素，但是给 `<a>` 转换一下块级模式最安全 
##  2.3 行内块元素 
在行内元素中有几个特殊的标签 —— `<img />`、`<input />`、`<td>`，它们同时具有块元素和行内元素的特点。有些资料称它们为行内块元素。 
行内块元素的特点： 
1. 和相邻行内元素（行内块）在一行上，但是他们之间会有空白缝隙。一行可以显示多个（行内元素特点）。 
2. 默认宽度就是它本身内容的宽度（行内元素特点）。 
3. 高度，行高、外边距以及内边距都可以控制（块级元素特点）
## 2.4 元素显示模式总结
|  元素模式  |        元素排列        |        设置样式        |     默认宽度     |           包含           |
| :--------: | :--------------------: | :--------------------: | :--------------: | :----------------------: |
|  块级元索  | 一行只能放一个块级元素 |    可以设置宽度高度    |    容器的100%    |  容器级可以包含任何标签  |
|  行内元素  | 一行可以放多个行内元素 | 不可以直接设置高度宽度 | 它本身内容的宽度 | 容纳文本或则其他行内元素 |
| 行内块元度 |  一行放多个行内块元素  |   可以设置宽度和高度   | 它本身内容的宽度 |                          |
## 2.5 元素显示模式转换
特殊情况下，我们需要元素模式的转换，简单理解: 一个模式的元素需要另外一种模式的特性，比如想要增加链接 `<a>` 的触发范围。    
- 转换为块元素：display:block; 
- 转换为行内元素：display:inline; 
- 转换为行内块：display: inline-block
## 2.6 一个小工具的使用 snipaste
略过
## 2.7 一个小技巧 单行文字垂直居中的代码 
让文字的行高等于盒子的高度  就可以让文字在当前盒子内垂直居中
## 2.8 单行文字垂直居中的原理
行高的上空隙和下空隙把文字挤到中间了.  是如果行高小于盒子高度,文字会偏上,如果行高大于盒子高度,则文字偏下 
# 3. CSS 的背景
背景属性可以设置背景颜色、背景图片、背景平铺、背景图片位置、背景图像固定等。 
## 3.1  背景颜色
background-color 属性定义了元素的背景颜色。 
```css
background-color:颜色值; 
```
一般情况下元素背景颜色默认值是 transparent（透明），我们也可以手动指定背景颜色为透明色。
```css
background-color:transparent;
```
## 3.2 背景图片
background-image 属性描述了元素的背景图像。实际开发常见于 logo 或者一些装饰性的小图片或者是超
大的背景图片, 优点是非常便于控制位置. (精灵图也是一种运用场景) 
```css
background-image : none | url (url) 
```
| 参数值 |              作用              |
| :----: | :----------------------------: |
|  none  |        无背景图(默认的)        |
|  url   | 使用绝对或相对地址指定背景图像 |

背景图片后面的地址，千万不要忘记加 URL， 同时里面的路径不要加引号
## 3.3 背景平铺 
如果需要在 HTML 页面上对背景图像进行平铺，可以使用 background-repeat 属性。 
```css
background-repeat: repeat | no-repeat | repeat-x | repeat-y 
```
|  参数值   |                作用                |
| :-------: | :--------------------------------: |
|  repeat   | 背景图像在纵向和横向上平铺(默认的) |
| no-repeat |           背景图像不平铺           |
| repeat-x  |       背景图像在横向.上平铺        |
| repeat-y  |         背景图像在纵向平铺         |

页面元素既可以添加背景颜色也可以添加背景图片 只不过背景图片会压住背景颜色
## 3.4 背景图片位置
利用 background-position 属性可以改变图片在背景中的位置。 
```css
background-position: x  y; 
```
参数代表的意思是：x 坐标和 y 坐标。 可以使用 方位名词 或者 精确单位 
|  参数值  |                         说明                          |
| :------: | :---------------------------------------------------: |
|  length  |       百分数/由浮点数字和单位标识符组成的长度值       |
| position | top / center / bottom / left / center / right方位名词 |
具体情况
1. 参数是方位名词 
- 如果指定的两个值都是方位名词，则两个值前后顺序无关，比如 left  top 和 top  left 效果一致 
- 如果只指定了一个方位名词，另一个值省略，则第二个值默认居中对齐 
2. 参数是精确单位 
- 如果参数值是精确坐标，那么第一个肯定是 x 坐标，第二个一定是 y 坐标 
- 如果只指定一个数值，那该数值一定是 x 坐标，另一个默认垂直居中 
3. 参数是混合单位 
- 如果指定的两个值是精确单位和方位名词混合使用，则第一个值是 x 坐标，第二个值是 y 坐标 
## 3.5 背景图像固定（背景附着） 
background-attachment 属性设置背景图像是否固定或者随着页面的其余部分滚动。 
background-attachment 后期可以制作视差滚动的效果。
```css
background-attachment : scroll | fixed 
```
|  参数  |              作用               |
| :----: | :-----------------------------: |
| scroll | 背景图像是随对象内容滚动((默认) |
| fixed  |          背景图像固定           |
## 3.6 背景复合写法
background: 背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置; 
```css
background: transparent url(image.jpg) repeat-y  fixed  top ;
```
## 3.7 背景色半透明
```css
background: rgba(0, 0, 0, 0.3);
```
- 最后一个参数是 alpha 透明度，取值范围在 0~1之间 
- 我们习惯把 0.3 的 0 省略掉，写为 background: rgba(0, 0, 0, .3); 
- 注意：背景半透明是指盒子背景半透明，盒子里面的内容不受影响 
- CSS3 新增属性，是 IE9+ 版本浏览器才支持的，但是现在实际开发,我们不太关注兼容性写法了,可以放心使用 
## 3.8 背景总结 
|         属性          |      作用      |                        值                         |
| :-------------------: | :------------: | :-----------------------------------------------: |
|   background-color    |    背景颜色    |          预定义的颜色值/十六进制/RGB代码          |
|   background-image    |    背景图片    |                   url(图片路径)                   |
|   background-repeat   |    是否平铺    |        repeat/no-repeat/repeat-x/repeat-y         |
|  background-position  |    背景位置    |         length/position 分别是x 和y 坐标          |
| background-attachment |    背景附着    |        scroll (背最滚动) /fixed (背最固定)        |
|       背景简写        |   书写更简单   | 背景颜色 背景图片地址 背景平铺 背景滚动 背景位置; |
|     背景色半透明      | 背景颜色半透明 |    background: rgba(0,0,0,0.3);后面必须是4个值    |

实际开发常见于 logo 或者一些装饰性的小图片或者是超大的背景图片, 优点是非常便于控制位置. (精灵图也是一种运用场景) 
