使用 background-attachment，filter: blur() 实现毛玻璃效果。

毛玻璃效果的重点在于，需要虚化的底图部分是会随页面 resize 变换而变换的。

`background-attachment:fixed` 则可以完美契合这一需求。

## 关键点

`background-attachment` 是一个比较生僻的属性，但是它本身很有意思。

`background-attachment`：如果指定了 `background-image` ，那么 `background-attachment` 决定背景是在视口中固定的还是随着包含它的区块滚动的。

### background-attachment: fixed

**fixed** 此关键字表示背景相对于视口固定。即使一个元素拥有滚动机制，背景也不会随着元素的内容滚动。

## 实现
### HTML
```html
<div>
  <p>使用 </p>
  <p>background-attachment: fixed </p>
  <p>filter: bulr()</p>
  <p>实现毛玻璃效果</p>
</div>
```
### CSS
```css
html,
body {
  width: 100%;
  height: 100%;
  background-image: url("https://images.unsplash.com/photo-1440688807730-73e4e2169fb8?dpr=1&auto=format&fit=crop&w=1500&h=1001&q=80&cs=tinysrgb&crop=");
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  background-position: top;
  overflow: hidden;
}

div {
  position: relative;
  width: 30vw;
  height: 40vh;
  background: inherit;
  margin: 50px auto;
  padding: 5vmin;
  border-radius: 5px;
  border: 2px solid rgba(255, 255, 255, 0.5);
}
div p {
  position: relative;
  color: #000;
  z-index: 10;
  font-size: 24px;
  line-height: 1.5;
}
div::after {
  position: absolute;
  content: "";
  background: inherit;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  filter: blur(10px);
  z-index: 0;
}
```
### 效果
[点击查看【codepen】](https://codepen.io/mqxu/embed/dyJOdEY)

