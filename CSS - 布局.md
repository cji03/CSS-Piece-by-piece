- ### 水平居中

**不限宽度：**

块级元素或者行内元素，在不限宽度的状态下可以使用`text-align: center;`来实现内容的水平居中。	

**设定宽度：**

在有设定宽度的情况下，元素都是块级元素。个人偏好使用`margin: 0 auto;`，简洁有效。  
当然也可以内层设置成`display: inline-block;`可以继承到外层的`text-align`属性，也可以使其水平居中。

还有一种比较通用的方法：使用`absolute`绝对定位，`top, left`50%的偏移量加上`margin`一半的偏移量使其定位在中心(CSS3的`transform: translate(-50%, -50%);`替代`margin`)。个人不是很喜欢这种方式，比较繁琐。

- ### 垂直居中

**单行行内元素：**

设置`height`与`line-height`高度相等，即可使内部文本垂直居中。

**多行行内元素：**

设置父元素`display: table-cell; vertical-align: middle;`可使内部多行元素垂直居中。上下`padding`相等。

**块级元素：**

使用`absolute`可以轻松实现。  
设置父元素`display: table-cell; vertical-align: middle;`，也可实现。  
具体情况具体实现不用死板。只要对单标签目标元素使用绝对定位就可以使其垂直居中，这一点非常方便，可以写成通用的样式。个人不是很喜欢用地位的方式写样式，像`relative`,`absolute`用多了会造成很混乱的层叠。

```css
  .center{
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  }
```

- 上述各种方式用`flex`布局都可以轻松达到。结合项目而定具体使用哪种方式合适。

- ### 单列布局

`header`, `body`, `footer`,三块区域。

```html
<div id="header">
  <div class="layout">头部</div>
</div>
<div id="content" class="layout">内容</div>
<div id="footer">
  <div class="layout">尾部</div>
</div>
```
```css
.layout{
  width: 100%;
  max-width: 960px;
  margin: 0 auto;
}
```

- ### 2&3列布局

1. **左侧固定，右侧自适应：**

左侧使用`absolute`浮起来，右侧设置边距空出左侧的距离。

```html
<div id="content">
  <div class="main">main</div>
  <div class="sub">left_side</div>
</div>
```
```css
.left_side {
  position: absolute;
  width: 200px;
}
.main {
  padding-left: 210px;
/*margin-left: 210px;*/
}
```

2. **圣杯／双飞翼布局：**

个人感觉非常复杂，css样式之间互相hack达到的一种布局方式。双飞翼是稍微优化了一些的样式：

```html
<div class="main-wrap">
  <div class="main">#main</div>
</div>
<div class="sub"></div>        
<div class="extra"></div>
```
```css
.main-wrap {        
  float: left;       
  width: 100%;   
 }  
 .sub {       
  float: left;        
  width: 190px;        
  margin-left: -100%;   
}   
.extra {        
  float: left;        
  width: 230px;        
  margin-left: -230px; 
 }
.main {
  margin: 0 230px 0 190px;
}
```

- ### flex布局

可以学习学习这种新式的布局方式，简单快捷花样多。

```html
<div class="layout">
  <aside class="aside">侧边栏宽度固定</aside>
  <div class="main">主内容栏宽度自适应</div>
</div>
<div class="layout">
  <div class="main">主内容栏宽度自适应</div>
  <aside class="aside">侧边栏宽度固定</aside>
</div>
<div class="layout">
  <aside class="aside">左侧边栏宽度固定</aside>
  <div class="main">主内容栏宽度自适应</div>
  <aside class="aside">右侧边栏宽度固定</aside>
</div>
<div class="layout">
  <aside class="aside">第1个侧边栏宽度固定</aside>
  <aside class="aside">第2个侧边栏宽度固定</aside>
  <div class="main">主内容栏宽度自适应</div>
</div>
<div class="layout">
  <div class="main">主内容栏宽度自适应</div>
  <aside class="aside">第1个侧边栏宽度固定</aside>
  <aside class="aside">第2个侧边栏宽度固定</aside>
</div>
```
```css
.layout {
  display: flex;
}
.main {
  flex: 1;
}
.aside {
  width: 200px;
}
```

---
[Example](https://codepen.io/cjjason/pen/gXOpxv)
