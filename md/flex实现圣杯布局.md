使用 flex 实现的圣杯布局。
## 需求
圣杯布局左中右三列布局，渲染顺序中间列书写在前保证提前渲染，左右两列定宽，中间列自适应剩余宽度。

圣杯布局与双飞翼布局的不同之处，圣杯布局的的左中右三列容器没有多余子容器存在，通过控制父元素的 padding 空出左右两列的宽度。
## 关键点

- 圣杯布局的关键点是通过 margin-left 与 left 属性将左右两列放置到准确的位置
- 圣杯布局的关键点父元素需要设置 padding
- 圣杯布局的关键点 margin-left 取值为百分比时，是以其父元素的宽度为基准的
## 实现
### HTML
```html
<div class="g-container">
  <div class="g-middle">middle</div>
  <div class="g-left">left</div>
  <div class="g-right">right</div>
</div>
```
### CSS
```css
.g-container {
  position: relative;
  height: 100vh;
  min-width: 400px;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
}
.g-container > div {
  height: 100vh;
  text-align: center;
  color: #fff;
  line-height: 100vh;
  font-size: 3vw;
}

.g-middle {
  order: 2;
  flex: auto 1 0;
  background: #cc6630;
}

.g-left {
  order: 1;
  flex: 200px 0 0;
  background: #ffcc00;
}

.g-right {
  order: 3;
  flex: 200px 0 0;
  background: pink;
}
```
### 效果
[点击查看【codepen】](https://codepen.io/mqxu/embed/XWVjoLY)
