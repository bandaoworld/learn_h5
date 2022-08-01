# 1. 盒子模型
## 1.1 盒子模型（Box Model）组成
所谓盒子模型：就是把 HTML 页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器。 
CSS 盒子模型本质上是一个盒子，封装周围的 HTML 元素，它包括
1. border边框
2. margin外边距
3. padding内边距
4. 和content实际内容 
## 1.2 边框（border） 
border可以设置元素的边框。边框有三部分组成:边框宽度(粗细) 边框样式  边框颜色
```css
/* 没有顺序要求 */
border : border-width || border-style || border-color
```
|属性|作用|
|:---:|:---:|
|border-width|定义边框粗细，单位是px|
|border-style|边框的样式|
|border-color|边框颜色|
- none：没有边框即忽略所有边框的宽度（默认值） 
- solid：边框为单实线(最为常用的) 
- dashed：边框为虚线   
- dotted：边框为点线
边框分开写法：
```css
/* 只设定上边框， 其余同理 */ 
border-top: 1px solid red;     
```
## 1.3 表格的细线边框 
border-collapse 属性控制浏览器绘制表格边框的方式。它控制相邻单元格的边框。 
```css
border-collapse:collapse;  
```
- collapse 单词是合并的意思 
- border-collapse: collapse; 表示相邻边框合并在一起
## 1.4 边框会影响盒子实际大小 
边框会额外增加盒子的实际大小。因此我们有两种方案解决: 
1. 测量盒子大小的时候,不量边框. 
2. 如果测量的时候包含了边框,则需要 width/height 减去边框宽度（记得边框有左右边框）
## 1.5 内边距（padding） 
padding 属性用于设置内边距，即边框与内容之间的距离。
|属性|作用|
|:---:|:---:|
|padding-left|左内边距|
|padding-right|右内边距|
|padding-top|上内边距|
|padding-bottom|下内边距|
padding 属性（简写属性）可以有一到四个值
|值的个数|表达意思|
|:---:|:---:|
|padding: 5px;|1个值，代表上下左右都有5像索内边距;|
|padding: 5px 10px;|2个值，代表上下内边距是5像素左右内边距是10像索|
|padding: 5px 10px 20px;|3个值，代表上内边距5像素左右内边距10像索下内边距20像索|
|padding: 5px 10px 20px 30px;|4个值，上5像素 右10像素 下20像素 左是30像索，顺时针|
如果盒子已经有了宽度和高度，此时再指定内边框，会撑大盒子。   
若保证盒子跟效果图大小保持一致，则让 width/height 减去多出来的内边距大小即可。  

如果盒子本身没有指定width/height属性, 则此时padding不会撑开盒子大小。  
```css
div {
    width: 300px;
    height: 100px;
    background-color: purple;
}
div p {
    /* 这里不要写width */
    padding: 30px;
    background-color: skyblue;
}
```
## 1.6 外边距（margin）
margin 属性用于设置外边距，即控制盒子和盒子之间的距离。
|属性|作用|
|:---:|:---:|
|margin-left|左外边距|
|margin-right|右外边距|
|margin-top|上外边距|
|margin-bottom|下外边距|
(margin 简写方式代表的意义跟 padding 完全一致。)
### 外边距典型应用
让块级盒子水平居中，但是要两个条件： 
1. 盒子必须指定了宽度（width）。 
2. 盒子左右的外边距都设置为 auto 。  
   
`.header{ width:960px; margin:0 auto;}`
常见的写法，以下三种都可以：
``` css
margin-left: auto;   margin-right: auto; 
margin: auto; 
margin: 0 auto; 
```
行内元素或者行内块元素水平居中给其父元素添加 text-align:center 即可。
## 1.7 外边距合并
使用 margin 定义块元素的垂直外边距时，可能会出现外边距的合并。
### 1. 相邻块元素垂直外边距的合并

当上下相邻的两个块元素（兄弟关系）相遇时，
如果上面的元素有下外边距 margin-bottom，下面的元素有上外边距 margin-top ，
则他们之间的垂直间距不是 margin-bottom 与 margin-top 之和。
取两个值中的较大者这种现象被称为相邻块元素垂直外边距的合并。
#### 解决方案：尽量只给一个盒子添加 margin 值。
### 2. 嵌套块元素垂直外边距的塌陷 
对于两个嵌套关系（父子关系）的块元素，父元素有上外边距同时子元素也有上外边距，此时父元素会塌陷较大的外边距值。
#### 解决方案： 
1. 可以为父元素定义上边框。 `border: 1px solid transparent;`
2. 可以为父元素定义上内边距。 `padding: 1px;`
3. 可以为父元素添加 overflow:hidden。 
4. 还有其他方法，比如浮动、固定，绝对定位的盒子不会有塌陷问题
## 1.8 清除内外边距
网页元素很多都带有默认的内外边距，而且不同浏览器默认的也不一致。
```css
* { 
    padding:0;   /* 清除内边距 */ 
    margin:0;    /* 清除外边距 */ 
  }
```
#### 注意：行内元素为了照顾兼容性，尽量只设置左右内外边距，不要设置上下内外边距。但是转换为块级和行内块元素就可以了 
## 1.9 总结
1. 布局为啥用不同盒子,我只想用div？ 
标签都是有语义的, 合理的地方用合理的标签。比如产品标题 就用 h,  大量文字段落就用p 
2. 为啥用辣么多类名？ 
类名就是给每个盒子起了一个名字,可以更好的找到这个盒子, 选取盒子更容易,后期维护也方便。 
3. 到底用 margin 还是 padding？ 
大部分情况两个可以混用，两者各有优缺点，但是根据实际情况，总是有更简单的方法实现。 
4. 自己做没有思路？ 
布局有很多种实现方式，同学们可以开始先模仿我的写法，然后再做出自己的风格。 
最后同学们一定多运用辅助工具,比如屏幕画笔,ps等等

