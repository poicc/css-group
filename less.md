# less开发指南

> 一切为了开发效率，有更多的时间做其他的事情。



## 特点 

### 原子的 

使用 原子css 会比 传统css 开发更快。 

当项目逐渐变大后，体积的增幅将会更小，因为所有的样式都是复用原先的样式，不需要重新定义。  

:point_down: 例如下边这个按钮，同样的效果，不一样的写法。

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331140210408.png" alt="1" style="zoom:57%;margin-left:0;" />

原子模式下

```vue
<template>
	<!-- 原子模式下开发快，但是模板乱，语义化弱 -->
	<div class="bg-success rounded text-white py-1">
		Success
	</div>
</template>
```
传统模式下

```vue
<template>
	<!-- 传统模式下清晰的模板和语义化，但开发较慢 -->
	<div class="btn"> Success </div>
</template>

<style scoped>
	/** 需要每次自行定义 class **/
	.btn {
		color: white;
		padding: 10rpx;
		border-radius: 0.25rem;
		background-color: #10b981;
	}
</style>
```



### Mixins

采用原子 css 会丢失掉模板结构的语义化，使得模板变得复杂与混乱。 

所以为了让模板语义化和结构更清晰，我们需要支持使用 [Mixins](https://lesscss.org/features/#mixins-feature) 去书写更具语义化的样式。

**App.vue引入动画库、图标库、通用less样式库**

```vue
<style lang="less">
	@import url("@/common/iconfont.css");
	@import url("@/common/animate.css");
	@import url("@/common/index.less");
</style>
```

**index.vue页面引入，使用Mixins来组合基础样式**

```vue
<template>
	<view class="content">
		<!-- 清晰的模板和语义化 -->
		<view class="card">
			<h2 class="text-secondary">卡片文字</h2>
		</view>

		<view class="btn animated fast" hover-class="fadeIn">
			我是有颜色的按钮
		</view>

		<view class="iconfont icon-dianhua icon-wrapper">
			{{title}}
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style scoped lang="less">
	/** 在style标签下重新引入基础less样式库 **/
  /**让 less 编译成 css 时按需生成混入的代码，减小项目体积**/
	@import (reference) '@/common/index.less';

	/** mixin样式库，使得设计更统一 **/
	.content {
		.p-2;
		.text-center;
	}

	.card {
		.p-5;
		.bg-primary;
		.bg-opacity-40;
		.my-5;
		.rounded-2xl;
		.shadow-lg;
	}

	.btn {
		.px-5;
		.py-3;
		.mb-5;
		.rounded-full;
		.text-white;
		.bg-warning;
		.font-bold;
		.text-2xl;
	}

	.icon-wrapper {
		.text-3xl;
		.text-success;
		.mx-2;
	}
</style>
```



## 参考

### 颜色

颜色分为三大部分:

- 背景色 bg
- 文字色 text
- 边框色 border

#### 背景色

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331140951112.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view class="text-white">
		<text class="bg-primary">主要</text>
		<text class="bg-secondary">次要</text>
		<text class="bg-accent">强调</text>
		<text class="bg-neutral">中和</text>
		<text class="bg-base">基础</text>
		<text class="bg-info">信息</text>
		<text class="bg-success">成功</text>
		<text class="bg-warning">警告</text>
		<text class="bg-error">错误</text>
	</view>
</template>
```



#### 文字色

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141012979.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="text-primary">主要</text>
		<text class="text-secondary">次要</text>
		<text class="text-accent">强调</text>
		<text class="text-neutral">中和</text>
		<text class="text-base">基础</text>
		<text class="text-info">信息</text>
		<text class="text-success">成功</text>
		<text class="text-warning">警告</text>
		<text class="text-error">错误</text>
	</view>
</template>
```



#### 边框色

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141035354.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="border border-primary">主要</text>
		<text class="border border-secondary">次要</text>
		<text class="border border-accent">强调</text>
		<text class="border border-neutral">中和</text>
		<text class="border border-base">基础</text>
		<text class="border border-info">信息</text>
		<text class="border border-success">成功</text>
		<text class="border border-warning">警告</text>
		<text class="border border-error">错误</text>
	</view>
</template>
```

当然你也可以给这些颜色加上后缀 `focus`，选择更深一点的颜色。  

例如 `bg-primary-focus` 比 `bg-primary` 颜色更深，`text-info-focus` 会比 `text-info` 颜色更深。



#### 颜色不透明度

可以分开调整各个颜色的不透明度。

- 背景色不透明度  `bg-opacity`
- 文字色不透明度  `text-opacity`
- 边框色不透明度  `border-opacity`

支持 0 到 100%的不透明度，默认为 100%。

##### 背景色不透明度

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141127255.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="bg-primary bg-opacity-0">0%</text>
		<text class="bg-primary bg-opacity-10">10%</text>
		<text class="bg-primary bg-opacity-20">20%</text>
		<text class="bg-primary bg-opacity-30">30%</text>
		<text class="bg-primary bg-opacity-40">40%</text>
		<text class="bg-primary bg-opacity-50">50%</text>
		<text class="bg-primary bg-opacity-60">60%</text>
		<text class="bg-primary bg-opacity-70">70%</text>
		<text class="bg-primary bg-opacity-80">80%</text>
		<text class="bg-primary bg-opacity-90">90%</text>
		<text class="bg-primary bg-opacity-100">100%</text>
	</view>
</template>
```



##### 文字色不透明度

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141147626.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="text-primary text-opacity-0">0%</text>
		<text class="text-primary text-opacity-10">10%</text>
		<text class="text-primary text-opacity-20">20%</text>
		<text class="text-primary text-opacity-30">30%</text>
		<text class="text-primary text-opacity-40">40%</text>
		<text class="text-primary text-opacity-50">50%</text>
		<text class="text-primary text-opacity-60">60%</text>
		<text class="text-primary text-opacity-70">70%</text>
		<text class="text-primary text-opacity-80">80%</text>
		<text class="text-primary text-opacity-90">90%</text>
		<text class="text-primary text-opacity-100">100%</text>
	</view>
</template>
```



##### 边框不透明度

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141209935.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="border border-primary border-opacity-0">0%</text>
		<text class="border border-primary border-opacity-10">10%</text>
		<text class="border border-primary border-opacity-20">20%</text>
		<text class="border border-primary border-opacity-30">30%</text>
		<text class="border border-primary border-opacity-40">40%</text>
		<text class="border border-primary border-opacity-50">50%</text>
		<text class="border border-primary border-opacity-60">60%</text>
		<text class="border border-primary border-opacity-70">70%</text>
		<text class="border border-primary border-opacity-80">80%</text>
		<text class="border border-primary border-opacity-90">90%</text>
		<text class="border border-primary border-opacity-100">100%</text>
	</view>
</template>
```

 **定位与不透明度**
 注意是不透明度，意味着你在使用一些定位的时候，它是会被透过去的，这时可以设置具体的颜色值来规避这种透过去的现象。

#### 最佳实践

好看的颜色搭配


##### 原色

深背景色，白色文字

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141318593.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="bg-primary text-white">主要</text>
		<text class="bg-secondary text-white">次要</text>
		<text class="bg-accent text-white">强调</text>
		<text class="bg-neutral text-white">中和</text>
		<text class="bg-base text-white">基础</text>
		<text class="bg-info text-white">信息</text>
		<text class="bg-success text-white">成功</text>
		<text class="bg-warning text-white">警告</text>
		<text class="bg-error text-white">错误</text>
	</view>
</template>
```



##### 高亮

深色文字，浅背景色 (10%的不透明度)

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141337180.png" alt="image-20220331141337180" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="bg-primary border-opacity-10 text-primary">主要</text>
		<text class="bg-secondary border-opacity-10 text-secondary">次要</text>
		<text class="bg-accent border-opacity-10 text-accent">强调</text>
		<text class="bg-neutral border-opacity-10 text-neutral">中和</text>
		<text class="bg-base border-opacity-10 text-base">基础</text>
		<text class="bg-info border-opacity-10 text-info">信息</text>
		<text class="bg-success border-opacity-10 text-success">成功</text>
		<text class="bg-warning border-opacity-10 text-warning">警告</text>
		<text class="bg-error border-opacity-10 text-error">错误</text>
	</view>
</template>
```



##### 轮廓

深色边框和深色文字，透明背景

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141355643.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="bg-transparent border border-primary text-primary"></text>主要</text>
		<text class="bg-transparent border border-secondary text-secondary">次要</text>
		<text class="bg-transparent border border-accent text-accent">强调</text>
		<text class="bg-transparent border border-neutral text-neutral">中和</text>
		<text class="bg-transparent border border-base text-base">基础</text>
		<text class="bg-transparent border border-info text-base">信息</text>
		<text class="bg-transparent border border-success text-success">成功</text>
		<text class="bg-transparent border border-warning text-warning">警告</text>
		<text class="bg-transparent border border-error text-error">错误</text>
	</view>
</template>
```



### 圆角

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141414099.png" alt="image-20220331141414099" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="border rounded-full">圆</text>
		<text class="border rounded-3xl">无敌大</text>
		<text class="border rounded-2xl">超级大</text>
		<text class="border rounded-xl">超大</text>
		<text class="border rounded-lg">大</text>
		<text class="border rounded-md">中</text>
		<text class="border rounded">基础</text>
		<text class="border rounded-sm">小</text>
		<text class="border rounded-none">无</text>
	</view>
</template>
```




### 阴影

<img src="https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/image-20220331141450656.png" alt="1" style="zoom:50%;" />

```vue
<template>
	<view>
		<text class="shadow-xl">超大</text>
		<text class="shadow-lg">大</text>
		<text class="shadow-md">中</text>
		<text class="shadow">基础</text>
		<text class="shadow-sm">小</text>
		<text class="shadow-none">无</text>
	</view>
</template>
```



### 尺寸

尺寸包含以下类型

- 宽度 w
- 高度 h
- 内边距 p
- 外边距 m

#### 范围

尺寸的范围是 0 到 750rpx，分为 75 份，每份 10rpx。  

例如 **w-9** 表示宽度 90rpx，**h-5** 表示高度 50rpx。

```vue
<template>
	<!-- 表示高50rpx，宽90rpx的块 -->
	<view class="bg-accent rounded h-5 w-9"></view>
</template>
```



#### full 和 screen

除此之外，宽和高还有  **full**  和  **screen**  两个尺寸。
full 表示 100%，而 screen 表示 100vh



#### 内外边距

由于边距有上下左右之分，所以除了用 **p-3** 这种表示上下左右内边距为 30rpx 之外，还可以加小前缀。小前缀可选值如下:

- l 左 👈
- r 右 👉
- t 上 👆
- b 下 👇

例如 pt-2 表示上内边距为 20rpx，mb-8 表示下外边距 80rpx。

```vue
<template>
	<!-- 表示高50rpx，宽90rpx的块，上内边距20rpx，左内边30rpx -->
	<view class="bg-accent rounded h-5 text-white pt-2 pl-3 w-9">1</view
	>
</template>
```



### 字重

<p>
  即 <t-tag>font-weight</t-tag>，可选值如下
</p>

- 100 font-thin
- 200 font-extralight
- 300 font-light
- 400 font-normal
- 500 font-medium
- 600 font-semibold
- 700 font-bold
- 800 font-extrabold
- 900 font-black


```vue
<template>
	<view>
		<text class="font-thin">thin</text>
		<text class="font-extralight">extralight</text>
		<text class="font-light">light</text>
		<text class="font-normal">normal</text>
		<text class="font-medium">medium</text>
		<text class="font-semibold">semibold</text>
		<text class="font-bold">bold</text>
		<text class="font-extrabold">extrabold</text>
		<text class="font-black">black</text>
	</view>
</template>
```



### 字体尺寸


```vue
<template>
	<view>
		<text class="text-xs">xs</text>
		<text class="text-sm">sm</text>
		<text class="text-md">md</text>
		<text class="text-lg">lg</text>
		<text class="text-xl">xl</text>
		<text class="text-2xl">2xl</text>
		<text class="text-3xl">3xl</text>
		<text class="text-4xl">4xl</text>
		<text class="text-5xl">5xl</text>
		<text class="text-6xl">6xl</text>
		<text class="text-7xl">7xl</text>
		<text class="text-8xl">8xl</text>
		<text class="text-9xl">9xl</text>
	</view>
</template>
```



### 文本方向

```vue
<template>
	<view>
		<view class="text-left">text-left</view>
		<view class="text-center">text-center</view>
		<view class="text-right">text-right</view>
	</view>
</template>
```




### 文本装饰

```vue
<template>
	<view>
		<text class="underline">underline</text>
		<text class="mx-5 line-through">line-through</text>
		<text class="no-underline">no-underline</text>
	</view>
</template>
```


### 文本大写

```vue
<template>
	<view>
		<text class="uppercase">Uppercase</text>
		<text class="mx-5 lowercase">LOWERCASE</text>
		<text class="mr-5 capitalize">Capitalize</text>
		<text class="normal-case">normal-case</text>
	</view>
</template>
```




### 不透明度


```vue
<template>
	<view class="flex">
		<text class="opacity-0 block-1">0%</text>
		<text class="opacity-10 block-1">10%</text>
		<text class="opacity-20 block-1">20%</text>
		<text class="opacity-30 block-1">30%</text>
		<text class="opacity-40 block-1">40%</text>
		<text class="opacity-50 block-1">50%</text>
		<text class="opacity-60 block-1">60%</text>
		<text class="opacity-70 block-1">70%</text>
		<text class="opacity-80 block-1">80%</text>
		<text class="opacity-90 block-1">90%</text>
		<text class="opacity-100 block-1">100%</text>
	</view>
</template>

<style scoped lang="less">
	@import (reference) '@/common/index.less';
	/** 块 **/
	.block-1 {
		.w-9;
		.h-6;
		.mr-3;
		.my-1;
		.rounded;
		.bg-accent;
		.bg-opacity-100;
	}
</style>
```



### Flex 布局

#### display

直接在容器上设置 `flex` 即可


```vue
<template>
	<view class="flex">
		<view class="block-1" />
		<view class="block-1" />
		<view class="block-1" />
		<view class="block-1" />
	</view>
</template>

<style scoped lang="less">
	@import (reference) '@/common/index.less';
	/** 块 **/
	.block-1 {
		.w-9;
		.h-6;
		.mr-3;
		.my-1;
		.rounded;
		.bg-accent;
		.bg-opacity-100;
	}
</style>
```



#### 主轴对齐

- justify-end 尾部
- justify-start 头部
- justify-evenly 等距
- justify-center 居中
- justify-around 等比
- justify-between 靠两头


```vue
<template>
	<view>
		<!-- 居中对齐 -->
		<view class="container flex justify-center">
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
		</view>

		<!-- 等距对齐 -->
		<view class="container flex justify-evenly">
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
		</view>

		<!-- 等比对齐 -->
		<view class="container flex justify-around">
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
		</view>

		<!-- 靠两头对齐 -->
		<view class="container flex justify-between">
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
		</view>

		<!-- 头部对齐 -->
		<view class="container flex justify-start">
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
		</view>

		<!-- 尾部对齐 -->
		<view class="container flex justify-end">
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
			<view class="block-1" />
		</view>
	</view>
</template>

<style scoped lang="less">
	@import (reference) '@/common/index.less';
	/** 块 **/
	.block-1 {
		.w-9;
		.h-6;
		.mr-3;
		.my-1;
		.rounded;
		.bg-accent;
		.bg-opacity-100;
	}
	/** 容器**/
	.container {
		.px-3;
		.py-2;
		.mt-4;
		.bg-accent;
		.rounded-lg;
		.bg-opacity-10;
	}
</style>
```



#### 交叉轴

- items-center 居中
- items-flex-end 头部
- items-flex-start 尾部
- items-baseline 文字基线对齐
- items-stretch 填充整个容器高度


```vue
<template>
	<view>
		<!-- 居中对齐 -->
		<view class="container flex items-center">
			<view class="h-3 block-common" />
			<view class="h-4 block-common" />
			<view class="h-5 block-common" />
			<view class="h-6 block-common" />
		</view>

		<!-- 填充整个容器高度，注意是容器高度 -->
		<view class="container flex items-stretch">
			<view class="h-6 block-common" />
			<view class="block-common" />
			<view class="block-common" />
			<view class="block-common" />
		</view>

		<!-- 文字基线对齐 -->
		<view class="container flex items-baseline">
			<view class="h-3 block-common" />
			<view class="h-4 block-common" />
			<view class="h-5 block-common" />
			<view class="h-6 block-common" />
		</view>

		<!-- 头部对齐 -->
		<view class="container flex items-flex-start">
			<view class="h-3 block-common" />
			<view class="h-4 block-common" />
			<view class="h-5 block-common" />
			<view class="h-6 block-common" />
		</view>

		<!-- 尾部对齐 -->
		<view class="container flex items-flex-end">
			<view class="h-3 block-common" />
			<view class="h-4 block-common" />
			<view class="h-5 block-common" />
			<view class="h-6 block-common" />
		</view>
	</view>
</template>

<style scoped lang="less">
	@import (reference) '@/common/index.less';

	/** 块 **/
	.block-common {
		.mr-3;
		.my-1;
		.flex-1;
		.rounded;
		.bg-accent;
		.bg-opacity-100;
	}

	/** 容器**/
	.container {
		.px-3;
		.py-2;
		.mt-4;
		.bg-accent;
		.rounded-lg;
		.bg-opacity-10;
	}
</style>
```



#### 方向

- flex-row 横排
- flex-col 竖排
- flex-row-reverse 反向横排
- flex-col-reverse 反向竖排


```vue
<template>
	<view>
		<!-- 横排 -->
		<view class="container flex flex-row">
			<view class="block-1">1</view>
			<view class="block-1">2</view>
			<view class="block-1">3</view>
			<view class="block-1">4</view>
		</view>

		<!-- 竖排 -->
		<view class="container flex flex-col">
			<view class="block-1">1</view>
			<view class="block-1">2</view>
			<view class="block-1">3</view>
			<view class="block-1">4</view>
		</view>

		<!-- 反向横排 -->
		<view class="container flex flex-row-reverse">
			<view class="block-1">1</view>
			<view class="block-1">2</view>
			<view class="block-1">3</view>
			<view class="block-1">4</view>
		</view>

		<!-- 反向竖排 -->
		<view class="container flex flex-col-reverse">
			<view class="block-1">1</view>
			<view class="block-1">2</view>
			<view class="block-1">3</view>
			<view class="block-1">4</view>
		</view>
	</view>
</template>

<style scoped lang="less">
	@import (reference) '@/common/index.less';
	/** 块 **/
	.block-1 {
		.w-9;
		.h-6;
		.mr-3;
		.my-1;
		.flex;
		.rounded;
		.bg-accent;
		.text-white;
		.items-center;
		.justify-center;
		.bg-opacity-100;
	}
	/** 容器**/
	.container {
		.px-3;
		.py-2;
		.mt-4;
		.bg-accent;
		.rounded-lg;
		.bg-opacity-10;
	}
</style>
```



### 自定义主题

#### 什么时候应该用?

- 需要强调产品的品牌色
- 内置的颜色不符合你的审美

#### 如何使用?

##### 全局主题

直接在 **App.vue** 下 Mixins 一个 **AppColors** 后按需修改颜色既可

```vue
<!-- App.vue -->
<style lang="less">
	@import '@/common/index.less';

	.AppColors({
		/* 品牌色 */
		primary: #570df8;   /* 主要 */
		secondary: #f000b8; /* 次要 */
		accent: #37cdbe;    /* 强调 */
		neutral: #3d4451;   /* 中和 */
		base: #7f899a;      /* 基础 */

		/* 通用色 */
		info: #3b82f6;    /* 信息 */
		success: #10b981; /* 成功 */
		warning: #f59e0b; /* 警告 */
		error: #ef4444;   /* 错误 */

		/* 点击时，品牌色 */
		primary-focus: #4406cb;    /* 主要 */
		secondary-focus: #bd0091;  /* 次要 */
		accent-focus: #2aa79b;     /* 强调 */
		neutral-focus: #2a2e37;    /* 中和 */
		base-focus: #656f7f;       /* 基础 */

		/* 点击时，通用色 */
		info-focus: #2563eb;     /* 信息 */
		success-focus: #059669;  /* 成功 */
		warning-focus: #d97706;  /* 警告 */
		error-focus: #dc2626;    /* 错误 */

		/* 白色 */
		white: #ffffff;
	});
</style>
```

**注意事项**
在  less 全局的 Mixins是一定要加分号的。

##### 局部主题

有时候 **App**需要加入第三方品牌的展示，而第三方品牌需要有属于自己的品牌色，这时就需要用到局部主题。

例如我们的品牌 A 用的是全局的蓝色，而第三方品牌 B 是红色。这时就需要有局部的主题配置。

```vue
<!-- App.vue -->
<style lang="less">
	@import '@/common/index.less';

	/* 我们的全局 A 品牌色 */
	.AppColors({
		primary: blue;   /* 主要 */
		/* ...此处省略其他配色 */
	});

	/* B品牌的配色 */
	.theme-B {
		/* 提供配色依赖 */
		.ProvideColors({ 
			primary: red; /* 主要 */
			/* ...此处省略其他配色，配色配置同全局一样 */
		});
	}
</style>
```

接着在需要展示第三方品牌的页面根节点上通过 class 注入即可

```vue
<!-- 展示第三方品牌 page -->
<template>
	<!-- 注入第三方品牌 B 的配色 -->
	<view class="theme-B">
		<!-- 此处省略各种第三方品牌的东西 -->
	</view>
</template>
```


