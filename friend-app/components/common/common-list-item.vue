<template>
	<view>
		<view class="info-wrapper">
			<image :src="item.avatarUrl" lazy-load class="avatar" @tap="openSpace"></image>
			<view class="flex-1">
				<view class="text-md">{{ item.nickname }}</view>
				<view class="publish-time">{{ item.publishTime }}</view>
			</view>
			<view v-if="!item.isFollow" class="follow-btn animated fast" hover-class="bounceOut" @tap="follow">关注</view>
			<view v-else class="unfollow-btn animated fast" hover-class="bounceOut" @tap="unFollow">已关注</view>
		</view>
		<view class="text-lg my-1 py-1" @tap="openDetail">{{ item.title }}</view>
		<!-- 图片 -->
		<image v-if="item.thumbnail" :src="item.thumbnail" style="height:350rpx;width:100%;border-radius: 5rpx;">
		</image>
		<!-- 图标 -->
		<view class=" flex-1 flex align-center justify-around">
			<!-- 顶 -->
			<view class="icon-wrapper animated fast" hover-class="jello" @tap="doSupport('support')"
				:class="item.support.type === 'support' ? 'support-active' : ''">
				<text class="iconfont icon-dianzan2 mr-2"></text>
				<text>{{ item.support.supportCount }}</text>
			</view>
			<!-- 踩-->
			<view class="icon-wrapper animated fast" hover-class="jello" @tap="doSupport('unSupport')"
				:class="item.support.type === 'unSupport' ? 'support-active' : ''">
				<text class="iconfont icon-cai mr-2"></text>
				<text>{{ item.support.unSupportCount }}</text>
			</view>
			<view class="icon-wrapper animated fast" hover-class="jello" @tap="openDetail()">
				<text class="iconfont icon-pinglun2 mr-2"></text>
				<text>{{ item.commentCount }}</text>
			</view>
			<view class="icon-wrapper animated fast" hover-class="jello" @tap="openDetail()">
				<text class="iconfont icon-fenxiang mr-2"></text>
				<text>{{ item.shareCount }}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item: Object,
			index: Number
		},
		methods: {
			// 打开个人空间
			openSpace() {
				console.log("打开个人空间")
			},
			// 关注
			follow() {
				// 通知父组件
				this.$emit("follow", this.index)
			},
			//取关
			unFollow() {
				// 通知父组件
				this.$emit('unFollow', this.index)
			},
			// 打开详情页
			openDetail() {
				console.log("打开详情页")
			},
			// 顶踩操作
			doSupport(type) {
				this.$emit('doSupport', {
					type,
					index: this.index
				})
		 },

		}
	};
</script>
<style lang="less" scoped>
	@import (reference) '@/common/index.less';

	.info-wrapper {
		.flex;
		.items-center;
		.justify-between;
	}

	.avatar {
		.w-10;
		.h-10;
		.rounded-full;
		.mr-2;
	}

	.publish-time {
		.text-sm;
		color: #9d9589;
	}

	.follow-btn {
		.w-9;
		.h-5;
		.flex;
		.items-center;
		.justify-center;
		.rounded-md;
		.text-white;
		.bg-primary;
	}

	.unfollow-btn {
		.w-9;
		.h-5;
		.flex;
		.items-center;
		.justify-center;
		.rounded-md;
		.text-white;
		.bg-primary;
		.px-1;
	}

	.icon-wrapper {
		.flex;
		.items-center;
		.justify-center;
	}

	.support-avtive {
		color: #769fcd;
	}
</style>
