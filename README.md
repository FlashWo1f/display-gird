## display: grid

总所周知 flex 布局 很强大。
Flex 布局是轴线布局，只能指定"项目"针对轴线的位置，可以看作是一维布局。
Grid 布局则是将容器划分成"行"和"列"，产生单元格，然后指定"项目所在"的单元格，可以看作是二维布局。
Grid 布局远比 Flex 布局强大。

兼容性可能稍微差点, 但是暂时还没查到各浏览器厂商的支持情况

### 容器和项目

Grid 布局只对项目生效。
最外层 div => container => display: grid
子div => item => 生效

```html
<div>
  <div><p>1</p></div>
  <div><p>2</p></div>
  <div><p>3</p></div>
</div>
```

### 网格线

grid-template-columns 属性和 grid-template-rows 属性里面，还可以使用方括号，指定每一根网格线的名字，方便以后的引用。
网格布局允许同一根线有多个名字，比如[fifth-line row-5]。
```css
.container {
  display: grid;
  grid-template-columns: [c1] 100px [c2] 100px [c3] auto [c4];
  grid-template-rows: [r1] 100px [r2] 100px [r3] auto [r4];
}
```

### place-items

justify-items属性设置单元格内容的水平位置（左中右），align-items属性设置单元格内容的垂直位置（上中下）。

```css
.container {
  justify-items: start | end | center | stretch;
  align-items: start | end | center | stretch;
}
```
start：对齐单元格的起始边缘。
end：对齐单元格的结束边缘。
center：单元格内部居中。
stretch：拉伸，占满单元格的整个宽度（默认值）。

而  place-items === justify-items + align-items

place-items: <align-items> <justify-items>;


### place-contents

justify-content属性是整个内容区域在容器里面的水平位置（左中右），align-content属性是整个内容区域的垂直位置（上中下）。

```css
.container {
  justify-content: start | end | center | stretch | space-around | space-between | space-evenly;
  align-content: start | end | center | stretch | space-around | space-between | space-evenly;  
}
```

### grid-column  grid-row 属性

grid-column-start属性：左边框所在的垂直网格线
grid-column-end属性：右边框所在的垂直网格线
grid-row-start属性：上边框所在的水平网格线
grid-row-end属性：下边框所在的水平网格线

```css
.container {
  grid-row: 1 / 3;
  /* 相同 */
  grid-row-start: 1;
  grid-row-end: 3;
  /* 相同 */
  grid-row: 1 / span 2;
}
```

### grid-area
单元格项目中有重叠覆盖的话 可以设置 z-index
```css
#container {
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
  grid-template-areas: 'a b c'
    'd e f'
    'g h i';
}
.item-1 {
  grid-area: e;
}
.item-2 {
  /* grid-area: <row-start> / <column-start> / <row-end> / <column-end>; */
  /* 还可以这样子 */
  grid-area: 3 / 1 / 4 / 4;
  background-color: #f68f26;
}
```

### justify-self align-self place-self 

同理
```css
.item {
  justify-self: start | end | center | stretch;
  align-self: start | end | center | stretch;
  place-self: <align-self> <justify-self>;
}
```