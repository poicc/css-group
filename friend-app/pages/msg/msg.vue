<template>
	<view class="px-2">
		<template v-if="list.length > 0">
			<block v-for="(item,index) in list" :key="index" >
				<msg-list-item :item="item" :index="index"></msg-list-item>
			</block>
		</template>
		<template v-else>
			<nothing></nothing>
		</template>

		<!-- 弹出层 -->
		<uni-popup ref="popup" type="top">
			<view class="menu-item" @tap="popupEvent('friend')">
				<text class="iconfont icon-sousuo mr-2"></text>
				<text>添加好友</text>
			</view>
			<view class="menu-item" @tap="popupEvent('clear')">
				<text class="iconfont icon-shanchu mr-2"></text>
				<text>删除列表</text>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	const demo = [{
			avatarUrl: "/static/img/me.jpg",
			nickname: "班班",
			time: "12:45",
			content: "今天也要元气满满喔",
			noReadNum: 1
		},
		{
			avatarUrl: "/static/img/user1.jpg",
			nickname: "杨阳",
			time: "10:45",
			content: "接口改好了",
			noReadNum: 1
		}, {
			avatarUrl: "/static/img/user2.jpg",
			nickname: "大哥",
			time: "10:45",
			content: "三食堂炸串真好吃！！",
			noReadNum: 2
		},
		{
			avatarUrl: "/static/img/avatar3.jpeg",
			nickname: "项目组",
			time: "10:45",
			content: "今天要部署一版",
			noReadNum: 2
		},
	]
	import uniPopup from "@/components/uni/uni-popup/uni-popup.vue";
	import msgListItem from "@/components/common/msg-list-item.vue";
	export default {
		components: {
			uniPopup,
			msgListItem
		},
		data() {
			return {
				list:[]
			};
		},
		//监听下拉刷新
		onPullDownRefresh() {
			this.getData();
		},
		//监听导航按钮点击事件
		onNavigationBarButtonTap(e) {
			switch (e.index) {
				case 0:
					uni.navigateTo({
						url: '../friends-list/friends-list'
					})
					//关闭弹出层
					this.$refs.popup.close();
					break;
				case 1:
					this.$refs.popup.open();
					break;
			}
		},
		/* onNavigationBarButtonTap() {
			console.log('跳转write')
			uni.navigateTo({
				url: '../friend-chat/friend-chat'
			})
		}, */
		
		methods: {

			//获取数据
			getData() {
				setTimeout(() => {
					//赋值
					this.list = demo;
					//关闭下拉刷新
					uni.stopPullDownRefresh();
				}, 1000);
			},
			//弹出层选型点击事件
			popupEvent(e) {
				switch (e) {
					case 'friend':
						console.log("添加好友");
						break;
					case 'clear':
						console.log("清除列表");
						break;
				}
				//关闭弹出层
				this.$refs.popup.close();
			}
		}
	}
</script>

<style scoped lang="less">
	@import (reference) '@/common/index.less';

	.msg-list {
		.py-2;
		.flex;

		image {
			.w-13;
			.h-13;
			.rounded-full;
			.mr-2;
			flex-shrink: 0;
		}

		view {
			flex: 1;
		}
	}

	.menu-item {
		.flex;
		.items-center;
		.justify-center;
		.h-10;
		.text-lg;
		.px-2;
		border-bottom: 1px solid #ccc;
	}
</style>
