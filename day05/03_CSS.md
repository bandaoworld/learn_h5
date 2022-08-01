# 1. CSS 的三大特性 
## 1.1 层叠性 
CSS 有三个非常重要的三个特性：
1. 层叠性
2. 继承性
3. 优先级
```css
div {
    font:16px "MiSans";
    color: red;
}
div {
    color: white;
}
```        
相同选择器给设置相同的样式，此时一个样式就会覆盖（层叠）另一个冲突的样式。层叠性主要解决样式冲突的问题
CSS 层叠性口诀：长江后浪推前浪，前浪死在沙滩上。 
层叠性原则： 
- 样式冲突，遵循的原则是就近原则，哪个样式离结构近，就执行哪个样式 
- 样式不冲突，不会层叠
## 1.2 继承性
CSS中的继承: 子标签会继承父标签的某些样式，如文本颜色和字号
- 恰当地使用继承可以简化代码，降低 CSS 样式的复杂性 
- 子元素可以继承父元素的样式（text-，font-，line-这些元素开头的可以继承，以及color属性） 
- 继承性口诀：龙生龙，凤生凤，老鼠生的孩子会打洞
行高的继承性
```css
body { 
    font:12px/1.5 Microsoft YaHei； 
}
```
- 行高可以跟单位也可以不跟单位 
- 如果子元素没有设置行高，则会继承父元素的行高为 1.5 
- 此时子元素的行高是：当前子元素的文字大小 * 1.5    
- body 行高 1.5  这样写法最大的优势就是里面子元素可以根据自己文字大小自动调整行高 
## 1.3 优先级 
当同一个元素指定多个选择器，就会有优先级的产生。 
- 选择器相同，则执行层叠性 
- 选择器不同，则根据选择器权重执行 

|选择器|选择器权重|
|:---:|:---:|
|继承或者*|0,0,0,0|
|元索选择器 (div{ })|0,0,0,1|
|类选择器，伪类选择器(class .test)|0,0,1,0|
|ID选择器(id #test)|0,1,0,0|
|行内样式 style=" "|1,0,0,0|
|!imporant重要的|∞无穷大|
权重叠加：如果是复合选择器，则会有权重叠加，需要计算权重。 
- div ul  li   ------>      0,0,0,3 
- .nav ul li   ------>      0,0,1,2 
- a:hover      -----—>      0,0,1,1 
- .nav a       ------>      0,0,1,1 
# 2. CSS 的注释
```css
/*  需要注释的内容  */ 
```











