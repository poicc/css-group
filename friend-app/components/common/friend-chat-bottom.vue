<template>
	<view class="flex user-chat-bottom">
		<input type="text" placeholder="积极发言" v-model="text" />
		<view class="iconfont icon-fabu submit" @tap="submit">发送</view>
	</view>
</template>

<script>
export default{
	data(){
		return{
			text:""
		}
	},
	methods:{
		submit(){
			console.log(this.text)
			this.$emit('submit',this.text);
			this.text=""
		}
	}
}
</script>

<style lang="less" scoped>
@import (reference) '@/common/index.less';
.user-chat-bottom {
	.fixed;
	.bottom-0;
	.left-0;
	.right-0;
	.px-3;
	.py-2;
	background-color: #c8c8c8;

	input {
		.w-60;
		.mr-2;
		.py-2;
		.pl-2;
		.rounded;
		background: #f7f7f7;
	}

	.submit {
		.flex;
		.items-center ;
		.justify-center;
		.text-center;
		.w-15;
		font-size: 35rpx;
		.bg-primary;
		.rounded;
		.text-white;
	}
}
</style>
