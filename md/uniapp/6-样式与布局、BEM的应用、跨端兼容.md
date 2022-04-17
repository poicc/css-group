# 样式与布局、BEM的应用、跨端兼容

主要学习 CSS 命名规范与 HTML 结构相结合的关系，并使用条件编译对应不同平台。

先看一下 CSS 命名弊端。

## CSS 命名弊端

你是否有见过这样的代码？

```css
.top--left .left1-block_nav-liItem > li a{
	
}
.gy-theme .bar-header .hy-nav .order-search .pull-down.active .select-drop {
    display: block
}
```

上面的代码风格各异的使用了 `-` , `_`，驼峰等风格而且嵌套深，CSS 引擎查找样式从右到左进行匹配，遍历页面上每个 li a 元素并确定其父元素。

每个人的代码都有自己的风格在，对于本人也会对自己写的代码会比较熟悉，但是放在多人开发上就显得另类了。协同开发的小伙伴可能根本不知道你写的是什么，甚至跟你写的代码冲突覆盖。或者会反感你写的代码。

我们先了解一下 CSS 中命名规范中的 BEM。

## 什么叫BEM？

**BEM 是 BlockElementModifier 的简称**，其实是块（block）、元素（element）、修饰符（modifier）的简称，是 CSS 中的一种命名规范。这种巧妙的命名方法让你的 CSS 类对其他开发者来说更加透明而且更有意义。BEM命名约定更加严格，而且包含更多的信息，它们用于一个团队开发一个耗时的大项目。

BEM 的关键是光凭名字就可以告诉其他开发者某个标记是用来干什么的。通过浏览HTML代码中的class属性，你就能够明白模块之间是如何关联的：有一些仅仅是组件，有一些则是这些组件的子孙或者是元素，还有一些是组件的其他形态或者是修饰符。

看一下这个大家比较熟悉的哆啦A梦吧，看看这之间有什么相似之处。

![img](https://img.kancloud.cn/21/19/21190fe4e68f708901ba3ece593d9b23_694x430.png)

上面的哆啦A梦如果用进行分块，可以分为头部（脸部），手部，脚部这三大块。其中我们把脸部拿出来细分：眼睛、嘴巴、鼻子，用关系图表示：

![img](https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/c3bc59229c844fef487faf2c05256b64_709x421.png)

## 页面布局 + BEM + scss

我们用 BEM 规范来表达一下哆啦A梦的结构：

```vue
<template>
	<view>
		<view class="doraemon">
			<view class="doraemon--face">
				<view class="doraemon--face-eye doraemon--face-eye_active"></view>
				<view class="doraemon--face-mouth"></view>
				<view class="doraemon--face-nose"></view>
			</view>
			<view class="doraemon--hand">
				<view class="doraemon--hand-finger"></view>
			</view>
			<view class="doraemon--footer">
				<view class="doraemon--footer-toe"></view>
			</view>
		</view>
	</view>
</template>	
<style lang="scss">
	.doraemon{
		.doraemon--face{
			.doraemon--face-eye{}
			.doraemon--face-mouth{}
			.doraemon--face-nose{}
		}
		.doraemon--hand{
			.doraemon--hand-finger{}
		}
		.doraemon--footer{
			.doraemon--footer-toe{}
		}
	}
</style>	
```

上面使用 BEM 规范：**块和元素之间用 -- 连接**，**元素和修饰符之间用 _ 连接** （示例：b--e_m），来命名 CSS（用代码组织哆啦A梦），组织 HTML 元素结构，一一对应 CSS 代码，使得代码结构更清晰。

使用 BEM 的方式，还是混淆使用 `-`，`_`，而且命名方式长，就命名这一个会让你举手投降。

利用 BEM 的规范思想，我们可以有自己的一套命名规范。

比如上面的示例中最里层的代码顶层元素，代表颗粒度最小的元素组成部分了，以此为准则，最底层元素不加任何前缀修饰符和块表示，并且以全小写用 - 连接（kebab-case），因此我们可以这么去做：

```vue
<template>
	<view>
		<view class="doraemon">
			<view class="doraemon-face">
				<view class="eye"></view>
				<view class="mouth"></view>
				<view class="nose"></view>
			</view>
			<view class="doraemon-hand">
				<view class="finger"></view>
			</view>
			<view class="doraemon-footer">
				<view class="toe"></view>
			</view>
		</view>
	</view>
</template>	
<style lang="scss">
	.doraemon{
		.doraemon-face{
			.eye{}
			.mouth{}
			.nose{}
		}
		.doraemon-hand{
			.finger{}
		}
		.doraemon-footer{
			.toe{}
		}
	}
</style>	
```

当然每个团队的规范不一样，为了更容易阅读和理解，更容易协作，更容易控制，需要服从团队的意识再去以开发效率去考虑，让团队甚至是你个人都能够更加容易地维护代码，如果你做到了，那么你自己也有了规范。

当我们自己将不同的规范糅合在一起以形成自己的行为准则时，需要考虑：

1. 修改元素 class 的时候会不会干扰到其他地方的样式，导致其他引用这个样式的地方错乱；
2. class 名称是否足够简洁，不会让人烧脑；
3. 样式的引用在哪里存放，是否会以 class 命名存放，然后修改 style 能快捷定位；
4. H5 中 class 命名的元素有没有绑定事件，修改会不会导致事件失效。

## 全局样式与局部样式

定义在 App.vue 中的样式为全局样式，作用于每一个页面。在 pages 目录下 的 vue 文件中定义的样式为局部样式，只作用在对应的页面，并会覆盖 App.vue 中相同的选择器。

注意：

1. nvue页面暂不支持全局样式；
2. App.vue 中通过 `@import` 语句可以导入外联样式，一样作用于每一个页面。

这样我们可以在 common 的文件夹添加一个 common.scss 引入到app.vue中作为基础样式

```scss
<!-- App.vue -->
<style lang="scss">
    @import './common/css/common.scss';
</style>
```

## 样式的条件编译

> 如果有个需求是 元素在 H5 的情况下渲染红色，在小程序下渲染绿色，怎么做？

判断平台，判断设备？用 UniApp 就不用考虑那么复杂了，UniApp 直接做了条件编译。

条件编译是用特殊的注释作为标记，在编译时根据这些特殊的注释，将注释里面的代码编译到不同平台。

条件编译写法：**以 #ifdef 或 #ifndef 加 “平台名称” 开头，以 #endif 结尾**。

- \#ifdef：if defined 仅在某平台存在
- \#ifndef：if not defined 除了某平台均存在
- %PLATFORM%：平台名称

平台名称参数对应：

![img](https://cdn.jsdelivr.net/gh/mqxu/wiki-image@master/uPic/8434808e10ce563062ae2d8b276cbdbd_815x592.png)

条件编译是利用注释实现的，在不同语法里注释写法不一样，**JS 使用 // 注释、CSS 使用 /* 注释 */**

可以这么实现:

```css
/* #ifdef MP-WEIXIN */
.wx-clor{
    color: green;
}
/* #endif */
```

## 小结

1. 使用良好的命名规范更容易阅读和理解，更容易协作，更容易控制，能让你的团队开发效率提升一大截；
2. 局部样式就是每个 vue 页面的样式，它的权重比全局样式要高；
3. UniApp 的条件编译是开发者编写一套代码发布多端项目的利器。