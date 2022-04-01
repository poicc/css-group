<template>
	<view class="content">
		<!-- <view class="iconfont icon-alipay" style="font-size: 32px;"></view> -->
		<!-- 清晰的模板和语义化 -->
		<view class="card">
			<h2 class="text-neutral">透明主色背景，阴影</h2>
		</view>

		<view class="btn bg-warning animated fast" hover-class="rotateInUpLeft">warning颜色的按钮</view>
		<view class="btn bg-success animated fast" hover-class="slideInLeft">success颜色的按钮</view>
		<view class="btn bg-info animated fast" hover-class="fadeIn">info颜色的按钮</view>
		<view class="btn bg-error animated fast" hover-class="rollOut">error颜色的按钮</view>
		<view class="iconfont icon-icon-test15 icon-wrapper" hover-class="bounceIn">{{ title }}</view>

		<view class="flex">
			<view class="block-1" v-for="count in 3">{{ count }}</view>
		</view>

		<h2 class="text-neutra">背景色</h2>
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

		<h2 class="text-neutra">文字色</h2>
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

		<h2 class="text-neutra">边框色</h2>
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

		<h2 class="text-neutra">颜色不透明度</h2>
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

		<h2 class="text-neutra">文字色不透明度</h2>
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

		<h2 class="text-neutra">边框色不透明度</h2>
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

		<h2 class="text-neutra">高亮</h2>
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

		<h2 class="text-neutra">轮廓</h2>
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



		<h2 class="text-neutra">圆角</h2>
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

		<h2 class="text-neutra">阴影</h2>
		<view>
			<text class="shadow-xl">超大</text>
			<text class="shadow-lg">大</text>
			<text class="shadow-md">中</text>
			<text class="shadow">基础</text>
			<text class="shadow-sm">小</text>
			<text class="shadow-none">无</text>
		</view>


		<h2 class="text-neutra">字重</h2>
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

		<h2 class="text-neutra">字体尺寸</h2>
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

		<h2 class="text-neutra">文本装饰</h2>
		<view>
			<text class="underline">underline</text>
			<text class="mx-5 line-through">line-through</text>
			<text class="no-underline">no-underline</text>
		</view>

		<h2 class="text-neutra">文本大写</h2>
		<view>
			<text class="uppercase">Uppercase</text>
			<text class="mx-5 lowercase">LOWERCASE</text>
			<text class="mr-5 capitalize">Capitalize</text>
			<text class="normal-case">normal-case</text>
		</view>

		<h2 class="text-neutra">不透明度</h2>
		<view class="flex">
			<text class="opacity-0 block-2">0%</text>
			<text class="opacity-10 block-2">10%</text>
			<text class="opacity-20 block-2">20%</text>
			<text class="opacity-30 block-2">30%</text>
			<text class="opacity-40 block-2">40%</text>
			<text class="opacity-50 block-2">50%</text>
			<text class="opacity-60 block-2">60%</text>
			<text class="opacity-70 block-2">70%</text>
			<text class="opacity-80 block-2">80%</text>
			<text class="opacity-90 block-2">90%</text>
			<text class="opacity-100 block-2">100%</text>
		</view>

		<h2 class="text-neutra">主轴对齐</h2>
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



		<h2 class="text-neutra">交叉轴</h2>
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


		<h2 class="text-neutra">方向</h2>
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

<script>
	export default {
		data() {
			return {
				title: "Hello"
			};
		},
		onLoad() {},
		methods: {}
	};
</script>

<style scoped lang="less">
	/** 在style标签下重新引入基础less样式库 **/
	/**让 less 编译成 css 时按需生成混入的代码，减小项目体积**/
	@import (reference) "@/common/index.less";

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
		.font-bold;
		.text-2xl;
	}

	.icon-wrapper {
		.text-3xl;
		.text-success;
		.m-5;
		.p-3;
		.border;
		.border-accent;
	}

	.block-1 {
		.w-25;
		.h-20;
		.mr-1;
		.my-1;
		.rounded;
		.bg-accent;
		.bg-opacity-100;
	}

	.block-2 {
		.w-9;
		.h-6;
		.mr-3;
		.my-1;
		.rounded;
		.bg-accent;
		.bg-opacity-100;
	}


	.container {
		.px-3;
		.py-2;
		.mt-4;
		.bg-accent;
		.rounded-lg;
		.bg-opacity-10;
	}
</style>
