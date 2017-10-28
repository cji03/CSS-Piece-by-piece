## Absolute 绝对定位

设置了`position: absolute;`的元素会脱离原来的文档流（浮了起来），通过指定元素相对于最近的非`static`定位祖先元素的偏移，来确定元素位置（如设置`top, left, right, bottom`）。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。

`absolute`和`float`具有类似的效果，会`block`化元素，唯一不同是`absolute`会脱离文档流。  
容器`absolute`后，容器会包裹子元素，子元素`absolute`后，容器的高度会塌陷，`absolute`后的子元素，不会受无定位父容器的`overflow`所影响。

- ### 无定位的绝对定位

不受`relative`的限制，不设置`top, left, right, bottom`的值。  
此状态的元素会依旧停留在原来的位置，只是浮了起来脱离了文档流，但是位置不变。此时如果配合`margin`可以进行一些比较精确的定位操作。

比如一些小图标的位置定位，可以用这样的方法，减少不必要的`relative`元素滥用。

- ### 有定位的绝对定位

设置`top, left, right, bottom`的值可使其上下左右移动。同时设置`top, left`或者`right, bottom`可对其进行拉伸。父元素设置`position: relative;`对其进行范围限定。

- ### 实例应用

1. **遮罩层：**

```css
.cover{
  position : absolute;
  /*容器拉伸*/
  left:0;top:0;right:0;bottom:0;
  background-color:#fff;
  opacity: .5; filter:alpha(opacity=50);
}
```

2. **图片左右翻页遮盖：**

```css
.prev,.next{
  /*覆盖容器的一半*/
  width:50%;
  /*上下拉伸*/
  position:absolute;top:0;bottom:0;
  background-image: ;
  outline:none;
}

.prev{cursor:url(),auto; left:0 }
.next{cursor:url(),auto; right:0}
```

3. **垂直水平居中：**

```css
.someDiv{
  position:absolute
  top:0;right:0;left:0;bottom:0;
  margin:atuo;
  width: 50%;
  height: 50%;
}
```
---
[Example](https://codepen.io/cjjason/pen/wPvmYv)
