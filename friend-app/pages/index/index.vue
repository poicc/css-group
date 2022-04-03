<template>
	<view class="p-2">
		<view v-for="(item,index) in list" :key="index" class="mb-3">
			<view class="info-wrapper">
				<image :src="item.avatarUrl" lazy-load class="avatar"></image>
				<view class="flex-1">
					<view class="text-md">{{item.nickname}}</view>
					<view class="publish-time">{{item.publishTime}}</view>
				</view>
				<view class="follow-btn">
					关注
				</view>
			</view>

			<view class="text-lg my-1 py-1">
				{{item.title}}
			</view>

			<!-- 图片 -->
			<image :src="item.thumbnail" style="height:350rpx;width:100%;border-radius: 5rpx;"></image>

			<!-- 图标 -->
			<view class="flex align-center">
				<view class="icon-wrapper">
					<text class="iconfont icon-dianzan2 mr-2"></text>
					<text>{{item.support.supportCount}}</text>
				</view>
				<view class="icon-wrapper">
					<text class="iconfont icon-cai mr-2"></text>
					<text>{{item.support.unSupportCount}}</text>
				</view>
				<view class="icon-wrapper">
					<text class="iconfont icon-pinglun2 mr-2"></text>
					<text>{{item.commentCount}}</text>
				</view>
				<view class="icon-wrapper">
					<text class="iconfont icon-fenxiang mr-2"></text>
					<text>{{item.shareCount}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{
						nickname: '程序员鼓励师',
						avatarUrl: '/static/img/me.jpg',
						publishTime: '2022-04-03 19:20:12',
						isFollow: false,
						title: '',
						thumbnail: '/static/img/banner1.jpg',
						support: {
							type: "support",
							supportCount: 8,
							unSupportCount: 2
						},
						commentCount: 10,
						shareCount: 12
					},
					{
						nickname: 'poicc',
						avatarUrl: '/static/img/avatar1.jpg',
						publishTime: '2022-04-03 20:20:12',
						isFollow: false,
						title: '穿过鲜花 走过荆棘 只为自由之地',
						thumbnail: '/static/img/banner2.jpg',
						support: {
							type: "support",
							supportCount: 8,
							unSupportCount: 2
						},
						commentCount: 10,
						shareCount: 12
					},
					{
						nickname: 'mob',
						avatarUrl: '/static/img/avatar2.jpg',
						publishTime: '2022-04-03 21:20:12',
						isFollow: false,
						title: '我多想跑到海边 吹着海风',
						thumbnail: '/static/img/banner3.jpeg',
						support: {
							type: "support",
							supportCount: 8,
							unSupportCount: 2
						},
						commentCount: 10,
						shareCount: 12
					}
				]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
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
		color: #9D9589;
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

	.icon-wrapper {
		.flex;
		.items-center;
		.justify-center;
		.flex-1;
	}
</style>
