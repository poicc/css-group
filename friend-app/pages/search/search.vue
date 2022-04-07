<template>
	<view class="p-2">
		<template v-if="searchList.length === 0">
			<!-- 搜索历史 -->
			<view class="py-2 text-md">
				搜索历史
			</view>
			<view class="flex flex-wrap">
				<view class="history-item" v-for="(item,index) in list" :key="index" @tap="tapSearchHistory(item)">
					{{item}}
				</view>
			</view>
		</template>
		
		<template>
			<view v-for="(item,index) in searchList" :key="index">
				<common-list-item :item="item" :index="index"></common-list-item>
			</view>
		</template>
	</view>
</template>

<script>
	const demo = [{
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
		},
		{
			nickname: 'mob',
			avatarUrl: '/static/img/avatar3.jpeg',
			publishTime: '2022-04-03 21:20:12',
			isFollow: false,
			title: '种子',
			thumbnail: '/static/img/banner4.jpeg',
			support: {
				type: "",
				supportCount: 0,
				unSupportCount: 0
			},
			commentCount: 0,
			shareCount: 0
		},
		{
			nickname: 'poicc',
			avatarUrl: '/static/img/avatar4.jpg',
			publishTime: '2022-04-03 21:20:12',
			isFollow: false,
			title: '日子老师yyds',
			thumbnail: '/static/img/banner5.jpg',
			support: {
				type: "support",
				supportCount: 8,
				unSupportCount: 2
			},
			commentCount: 10,
			shareCount: 12
		}, {
			nickname: 'jo太郎',
			avatarUrl: '/static/img/avatar5.png',
			publishTime: '2022-04-03 21:20:12',
			isFollow: false,
			title: '呀嘞呀嘞daze',
			thumbnail: '/static/img/banner6.png',
			support: {
				type: "support",
				supportCount: 8,
				unSupportCount: 2
			},
			commentCount: 10,
			shareCount: 12
		},
	]
	import commonListItem from '@/components/common/common-list-item.vue';
	export default {
		components:{
			commonListItem
		},
		data() {
			return {
				searchTxt: '',
				list:[
					'自由之地',
					'jojo的奇妙冒险',
					'泛式',
					'明日方舟海蒂'
				],
				searchList: []
			}
		},
		onNavigationBarSearchInputChanged(e) {
			this.searchTxt = e.text
		},
		onNavigationBarButtonTap() {
			this.searchEvent()
		},
		methods: {
			//点击搜索历史
			tapSearchHistory(txt) {
				this.searchTxt = txt
				this.searchEvent()
			},
			searchEvent() {
				//收起软键盘
				uni.hideKeyboard()
				uni.showLoading({
					title:"加载中",
					mask:false
				})
				//请求搜索
				setTimeout(() => {
					this.searchList = demo
					uni.hideLoading()
				})
			}
		}
	}
</script>

<style lang="less" scoped>
	@import (reference) '@/common/index.less';
	
	.history-item {
		.border;
		.border-primary;
		.rounded;
		.text-sm;
		.text-base;
		.mr-2;
		.my-1;
		.px-2;
		.text-primary;
	}

</style>
