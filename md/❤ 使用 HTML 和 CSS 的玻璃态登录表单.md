# ❤ 使用 HTML 和 CSS 的玻璃态登录表单

> Glassmorphism：玻璃拟态
>
> 人的兴趣总是捉摸不定，设计趋势因此也会如钟摆一样摇摆不定。
>
> 在Material Design为首的简约风格流行了几年之后，以苹果新的Mac OS Big Sur操作系统发布为标志，一种新的拟物风格正在悄悄回归。
>
> 这种把阴影、透明度以及模糊背景结合到一起的UI设计思路，因为给人以玻璃的质感，被称为Glassmorphism（玻璃拟态）



## 🥇 第 1 步：设计网页

使用了黑色作为网页的背景色。

```css
*,
*:before,
*:after{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
body{
    background-color: #080710;
}
```



## 🥈 第 2 步：在背景中创建两个彩色圆圈

圆的宽度和高度为 200 像素，并且使用了 50% 的边框半径使其完全圆形。位置绝对定位，使其保持在同一个位置。

```html
<body>
  <div class="background">
    <div class="shape"></div>
    <div class="shape"></div>
  </div>
</body>
```



```css
.background {
  width: 600px;
  height: 500px;
  position: absolute;
  transform: translate(-50%, -50%);
  left: 50%;
  top: 50%;
}

.background .shape {
  height: 200px;
  width: 200px;
  position: absolute;
  border-radius: 50%;
}
```

使用下面的 CSS 代码，在第一个圆圈背景中使用了蓝色绿色渐变，在第二个圆圈使用了红色黄色的渐变色。

```css
.shape:first-child {
  background: linear-gradient(#1845ad,
    #23a2f6);
  left: -90px;
  top: -80px;
}

.shape:last-child {
  background: linear-gradient(to right,
    #ff512f,
    #f09819);
  right: -90px;
  bottom: -80px;
}

```

## 📰 第 3 步：创建玻璃态登录表单的基本结构

使用以下 HTML 和 CSS 代码创建此登录表单的基本结构，玻璃态效果登录表单的宽为 `600px` 高为 `550px`.

使用了背景颜色半透明，圆角，模糊滤镜。

```html
<body>
  <div class="background">
    <div class="shape"></div>
    <div class="shape"></div>
  </div>
  
  <form>

  </form>
</body>
```



```css
form {
  width: 600px;
  height: 500px;
  background-color: rgba(255, 255, 255, 0.13);
  position: absolute;
  transform: translate(-50%, -50%);
  top: 50%;
  left: 50%;
  border-radius: 10px;
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 0 40px rgba(8, 7, 16, 0.6);
  padding: 50px 35px;
}

form * {
  font-family: 'Poppins', sans-serif;
  color: #ffffff;
  letter-spacing: 0.5px;
  outline: none;
  border: none;
}
```



## 📲 第 4 步：向表单添加标题

```html
<body>
  <div class="background">
    <div class="shape"></div>
    <div class="shape"></div>
  </div>
  
  <form>
 	   <h3>玻璃拟态 | 登录表单</h3>
  </form>
</body>
```

文字大小，居中

```css
form h3 {
  font-size: 24px;
  font-weight: 500;
  line-height: 42px;
  text-align: center;
}
```



## 🎯 第 5 步：创建表单输入框

表单输入框，使用了 50px 高度，并使用了半透明的背景色

```html
<body>
  <div class="background">
    <div class="shape"></div>
    <div class="shape"></div>
  </div>
  <form>
    <h3>玻璃拟态 | 登录表单</h3>
    
    <label for="username">账号</label>
    <input type="text" placeholder="Email or Phone" id="username">

    <label for="password">密码</label>
    <input type="password" placeholder="Password" id="password">
  </form>
</body>
```

```css
label {
  display: block;
  margin-top: 30px;
  font-size: 16px;
  font-weight: 500;
}

input {
  display: block;
  height: 50px;
  width: 100%;
  background-color: rgba(255, 255, 255, 0.07);
  border-radius: 3px;
  padding: 0 10px;
  margin-top: 8px;
  font-size: 14px;
  font-weight: 300;
}

::placeholder {
  color: #e5e5e5;
}
```



## 🏆 第 6 步：在玻璃态登录表单中添加登录按钮

创建登录按钮

```html
<body>
  <div class="background">
    <div class="shape"></div>
    <div class="shape"></div>
  </div>
  <form>
    <h3>漂亮的 | 登录表单</h3>
    <label for="username">账号</label>
    <input type="text" placeholder="Email or Phone" id="username">

    <label for="password">密码</label>
    <input type="password" placeholder="Password" id="password">
    <button>登录</button>
  </form>
</body>

```

设置基础的一些样式

```css
button {
  margin-top: 50px;
  width: 100%;
  background-color: rgba(255, 255, 255, 0.27);
  color: #eaf0fb;
  text-align: center;
  padding: 15px 0;
  font-size: 18px;
  font-weight: 600;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: rgba(255, 255, 255, 0.47);
}
```



至此，用 HTML 和 CSS 创建的玻璃态登录表单就已经完成了。

<img src="../Library/Application Support/typora-user-images/image-20220402190426529.png" alt="image-20220402190426529" style="zoom:50%;" />



