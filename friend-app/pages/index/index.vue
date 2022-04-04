<template>
	<view class="p-2">
		<view v-for="(item, index) in list" :key="index" class="mb-3">
			<common-list-item :item="item" :index="index" @follow="follow" @doSupport="doSupport" @unFollow="unFollow">
			</common-list-item>
			<divider v-if="index != list.length -1"></divider>
		</view>
	</view>
</template>

<script>
	import commonListItem from '@/components/common/common-list-item.vue';
	export default {
		components: {
			commonListItem
		},
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
			follow(e) {
				console.log("关注")
				this.list[e].isFollow = true
				uni.showToast({
					title: "关注成功"
				})
			},

			unFollow(e) {
				this.list[e].isFollow = false
				uni.showToast({
					title: "取关成功"
				})
			},


			doSupport(e) {
				let item = this.list[e.index]
				// 执行了"踩"操作
				if (item.support.type === 'support' && e.type === 'unSupport') {
					item.support.supportCount--;
					item.support.unSupportCount++;
				} else if (item.support.type === 'unSupport' && e.type === 'support') {
					item.support.supportCount++;
					item.support.unSupportCount--;
				}
			}
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
		.bg-pink;
	}

	.icon-wrapper {
		.flex;
		.items-center;
		.justify-center;
		.flex-1;
	}
</style>
