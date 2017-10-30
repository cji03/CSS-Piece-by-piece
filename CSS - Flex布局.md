## Flex布局

![flex.png](https://i.loli.net/2017/10/30/59f745c4198ef.png)

设置了`display: flex`的容器是flex容器(flex container)，直接子元素叫做flex项(flex items)。  
`main axis`：主轴，flex项的延展方向。  
`cross axis`: 与主轴垂直的交叉轴，垂直方向上的延展。

`display: flex | inline-flex;`分别生成一个块级或者行内的flex容器。

**设置了flex布局之后，子元素的`float, clear, vertical-align`属性将会失效。** 

- **水平居中的示例：**

flex项目设置`margin: auto;`，或者flex容器设置水平垂直轴居中。

```html
<div class="parent">
  <div class="child"></div>
</div>
```
```css
.parent {
  display: flex;
  height: 300px; /* Or whatever */
  background-color: black;
  //align-items: center;
  //justify-content: center;
}
.child {
  width: 100px;  /* Or whatever */
  height: 100px; /* Or whatever */
  margin: auto;  /* Magic! */
  background-color: white;
}
```

### flex容器属性

- **`flex-direction`:** 决定了主轴的方向(flex项的排列方向)。

默认值：`row`

```css
.flex-container {
  flex-direction: row | row-reverse | column | column-reverse; 
}
```

- **`flex-wrap`:** 如果希望项目多行显示，可以使用这个属性。

默认值：`nowrap`，当flex容器宽度固定，flex项过多空间不足时会自动缩减项的大小，使其能单行显示。

```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

- **`flex-flow`:** `flex-direction`和`flex-wrap`的简写。

默认值为: `row nowrap`, 通常都会分开写比较清楚吧。

```css
.container {
  flex-flow: <flex-direction> || <flex-wrap>;
}
```

- **`justify-content`:** flex项目在flex容器沿着主轴在当前行的对齐方式。

默认值: `flex-start`， 左对齐

```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around;
  /*
  * space-between: Flex项目之间间距相对，第一个和最后一个flex项目向flex容器的边缘对齐。
  * space-around: 每个项目两侧的间隔相等。
  */
}
```

- **`align-items`:** 定义了项目在交叉轴上的对齐方式。

默认值: `stretch `, flex项未设置高度会占满整个容器高度。

```css
.container {
  align-items: flex-start | flex-end | center | baseline | stretch;
  /*
  * baseline: Flex项目按文本基线在flex容器侧轴中排列。
  */
}
```

- **`align-content`:** 定义了多行排列的对齐方式，如果项目只有一根轴线，那么该属性将不起作用。

默认值: `stretch `, flex项未设置高度会占满整个容器高度。

```css
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

### flex项目属性

- **`order`:** 用来控制flex容器中flex项目的排列顺序。

默认值: 0

```css
.flex-item {
  order: <integer>;
}
```

- **`flex-basis`:** 指定flex项目大小。与设置宽高相同效果。

默认值: `auto`, 即原大小，可以设置宽高

```css
.item {
  flex-basis: <length> | auto;
}
```

- **`flex-grow`:** 定义flex项的放大比例。

默认值: 0, 不放大。值都为 1 时，等分空间。

```css
.item {
  flex-grow: <number>;
}
```

- **`flex-shrink`:** 定义了flex项的缩小比例。

默认值: 1，即如果空间不足，该项将缩小，负值对该属性无效。  
数值越大，缩小比例越大，如果设置为 0 ，该项不缩小。

```css
.item {
  flex-shrink: <number>;
}
```

> 当flex容器有剩余空间可以分配的时候，`flex-grow`会起作用。没有多余空间时，`flex-shrink`可以起作用。

- **`align-self`:** 用来在单独的flex项上覆写默认的对齐方式。

```css
.item {
   align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

- **`flex`:** `flex-grow`, `flex-shrink`和`flex-basis`的简写。

```css
.item{
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
} 
```

默认值: `initial(0 1 auto)`, 其它可设置为`auto(1 1 auto)`和`non(0 0 auto)`。

*官方鼓励这种简写方式，而不使用单独的属性。*

---
[玩耍实例](https://codepen.io/justd/pen/yydezN)
