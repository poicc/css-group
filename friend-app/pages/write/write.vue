<template>
	<view>
		<!-- 自定义导航 -->
		<uni-nav-bar leftIcon="back" leftText="返回" rightIcon="location" statusBar="true" backgroundColor="#4DB6AC"
			color="#fff" @click-left="back">
			<view class="flex align-center justify-center w-full">
				<text>
					所有人可见
				</text>
				<text class="iconfont icon-shezhi ml-2"></text>
			</view>
		</uni-nav-bar>

		<!-- 文本域 -->
		<textarea v-model="content" placeholder="说一句话吧" class="input-area" />
		<!-- 多图上传 -->
		<upload-image @change="changeImage" :list="imageList" ref="uploadImage" :show="show"></upload-image>

		<!-- 底部操作条 -->

		<view class="fixed-bottom flex align-center bg-white" style="height: 85rpx;">
			<view class="iconfont icon-caidan animated" hover-class="jello"></view>
			<view class="iconfont icon-huati animated" hover-class="jello"></view>
			<view class="iconfont icon-tupian animated" hover-class="jello" @tap="iconClickEvent('uploadImage')"></view>
			<view class="send animated" hover-class="bounceIn">发送</view>
		</view>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni/uni-nav-bar/uni-nav-bar.vue'
	import uploadImage from '@/components/common/upload-image.vue'
	export default {
		components: {
			uniNavBar,
			uploadImage
		},
		data() {
			return {
				content: '',
				imageList: [], //要上传到服务器的图片
				showBack: false //是否以及弹出提示框
			}
		},
		computed: {
			show() {
				return this.imageList.length > 0;
			}
		},
		onBackPress() {
			if ((this.content !== '' || this.imageList.length > 0) && !this.showBack) {
				uni.showModal({
					content: '是否保存为草稿',
					showCancel: true,
					cancelText: '不保存',
					confirmText: '保存',
					success: res => {
						//点击确认
						if (res.confirm) {
							this.store()
						} else {
							//点击取消
							uni.removeStorage({
								key: "write"
							})
						}
						//手动执行返回
						uni.navigateBack({
							delta: 1
						});
					},
				});
				this.showBack = true;
				return true
			}

		},
		//每次访问时候
		onShow() {
			if (!uni.getStorageSync("write")) {
				return
			}
			let result = JSON.parse(uni.getStorageSync("write"))
			console.log(result)
			this.content = result.content
			this.imageList = result.imageList
		},
		methods: {
			//选中的图片
			changeImage(e) {
				console.log(e)
				this.imageList = e
			},
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			//保存操作
			store() {
				uni.setStorage({
					//保存为本地存储
					key: "write",
					data: JSON.stringify({
						content: this.content,
						imageList: this.imageList
					})
				})
			},
			iconClickEvent(e) {
				switch (e) {
					case "uploadImage":
						this.$refs.uploadImage.chooseImage();
						break;
				}
			}
		}
	}
</script>

<style lang="less" scoped>
	@import (reference) '@/common/index.less';

	.input-area {
		.w-68;
		margin: auto;
		.h-30;
		background-color: #f6f6f6;
		.p-2;
		.mt-2;
		.text-md;
	}

	.fixed-bottom {
		.fixed;
		.bottom-0;
		.left-0;
		.right-0;
		.px-2;

		.iconfont {
			font-size: 50rpx;
			margin-right: 30rpx;
		}

		.send {
			.bg-primary;
			.text-white;
			.text-lg;
			.px-4;
			.rounded;
			.flex;
			.items-center;
			.justify-center;
			margin-left: auto;
			width: 120rpx;
			height: 80rpx;
		}
	}
</style>
