## CSS Table布局

HTML的Table布局现阶段应该很少有人会在使用了，毕竟是当年对table标签的取巧的不正当使用。
但是`display: table;`这个css属性的出现和普及(全线浏览器的支持)，可以让我们用div+css实现一些table布局的效果。

css的一些display属性：
```css
display: table 指定对象作为块元素级的表格。类同于html标签<table>（CSS2）
display: inline-table 指定对象作为内联元素级的表格。类同于html标签<table>（CSS2）
display: table-caption 指定对象作为表格标题。类同于html标签<caption>（CSS2）
display: table-cell 指定对象作为表格单元格。类同于html标签<td>（CSS2）
display: table-row 指定对象作为表格行。类同于html标签<tr>（CSS2）
display: table-row-group 指定对象作为表格行组。类同于html标签<tbody>（CSS2）
display: table-column 指定对象作为表格列。类同于html标签<col>（CSS2）
display: table-column-group 指定对象作为表格列组显示。类同于html标签<colgroup>（CSS2）
display: table-header-group 指定对象作为表格标题组。类同于html标签<thead>（CSS2）
display: table-footer-group 指定对象作为表格脚注组。类同于html标签<tfoot>（CSS2
```

- ### 动态垂直，水平居中 [例子](https://codepen.io/cjjason/pen/BmBWGm)

```html
<div class="wrap">
  <div class="parent">
    <div class="child">
      <p>自适应宽高的垂直、水平居中</p>
      <p>支持 IE8+</p>
    </div>
  </div>
</div>
<style>
  html, body {
    height: 100%;
  }
  .parent {
    width: 100%;
    height: 100%;
    background: #ddd;
  }
  .child {
    background: #f18c16;
    color: #fff;
    padding: 20px;
  }
  /* 核心代码 */
  /* 给 wrap 设置 display: table; */
  /* 这样就可以给 wrap 设置百分比宽高了 */
  .wrap {
    display: table;
    width: 100%;
    height: 100%;
  }
  /* parent元素可以设置百分比宽高 */
  .parent {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
  }
  /* inline-block可以继承外层text-align，从而居中 */
  .child {
    display: inline-block;
    /* 另一种写法，不用text-align达到水平居中
    * display: table;
    * margin: auto
    */
  }
</style>
```

- ### 多列等高，响应布局 [例子](https://codepen.io/cjjason/pen/WXejeg)

父元素display: table;, 子元素display: table-cell;
```html
<div class="boxes">
   <div class="box box1">Box 1</div>
   <div class="box box2">Box 2</div>
   <div class="box box3">Box 3</div>
</div>
<style>
  html, body{
    margin: 0;
    padding: 0;
    height: 100%;
  }
  .boxes {
    display:table;
    width: 100%;
    height: 100%;
  }
  .box {
    display: table-cell;
    text-align: center;
    vertical-align:middle;
  }
  .box1 {
    background-color: orange;
  }
  .box2 {
    background-color: green;
  }
  .box3 {
    background-color: blue;
  }
  @media (max-width: 600px) {
    /* 将元素的display属性从table-cell 切换到 block，我们就能够将元素堆叠起来 */
    .box {
      display: block;
      width: 100%;
    }
}
</style>
```

- ### 动态高度的页脚贴在页面底部 [例子](动态高度的页脚贴在页面底部)

父元素`display: table;`， 页脚元素`display: table-row;`
```html
<div class="main">这里是主体区域
  <div>内容区域</div>
</div>
<div class="footer">这里是底部</div>
<style>
  html, body{
    margin: 0;
    padding: 0;
    height: 100%;
  }
  body {
    background: @beige;
    color: @orange;
    display: table;
    width: 100%;
  }
  .main {
    height: 100%;
  }
  .footer {
    display: table-row;
    height:1px;
    background: @green;
    color: @beige;
  }
  @orange: #BD4932;
  @yellow: #FFD34E;
  @green: #105B63;
  @beige: #FFFAD5;
</style>
```

- ### 圣杯布局 [例子](https://codepen.io/cjjason/pen/NwKjeV)

唯一有个问题是：主题内容不会出现在第一个节点位置。
```html
<div class="wrapper">
  <div class="header">头部</div>
  <div class="main">
    <div class="box sidebar">左侧栏</div>
    <div class="box content">主体内容</div>
    <div class="box sidebar">有侧栏</div>
  </div>
  <div class="footer">页脚底部</div>
</div>
<style>
  body {
    background: @beige;
    color: black;
  }
  .wrapper {
    height: 100%;
    display: table;
    width: 100%;
    text-align: center;
  }
  .header {
    display: table-row;
    height: 1px;
    background: @yellow;
  }
  .main {
    height: 100%;
    display: table;
    width: 100%;
  }
  .box {
    display: table-cell;
  }
  .sidebar {
    width: 100px;
    background: @orange;
  }
  .footer {
    display: table-row;
    height:1px;
    background: @green;
    color: @beige;
  }
@orange: #BD4932;
@yellow: #FFD34E;
@green: #105B63;
@beige: #FFFAD5;
</style>
```
