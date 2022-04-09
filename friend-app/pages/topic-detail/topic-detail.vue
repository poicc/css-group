<template>
	<view>
		<!-- <uni-nav-bar statusBar rightIcon="more" leftIcon="back"></uni-nav-bar> -->
		<!-- 话题介绍组件 -->
		<topic-info :item="topicInfo"></topic-info>
		
		<!-- 消息区 -->
		<divider></divider>
		<block v-for="count in 2">
			<view class="top">
				<text class="iconfont icon-xiaoxi1 text-orange text-lg font-weight-bolder pl-2 mx-2"></text>
				<text>【新人必读】uni-app实战 社区交友</text>
			</view>
			<divider></divider>
		</block>
		
		<!-- 列表 -->
		<view class="p-2">
			<block v-for="(item,index) in list" :key="index">
				<common-list-item :item="item" :index="index"></common-list-item>
				<divider></divider>
			</block>
		</view>
	</view>
</template>

<script>
	import topicInfo from "@/components/common/topic-info.vue";
	import commonListItem from "@/components/common/common-list-item.vue";
	const demo = [
		{
			nickname: '夏目',
			avatarUrl: '/static/img/banner6.jpg',
			publishTime: '2022-04-09 20:14:01',
			isFollow: true,
			title: '我必须承认生命中大部分时光是属于孤独的，努力成长是在孤独里可以进行的最好的游戏。',
			thumbnail: '/static/img/banner6.jpeg',
			support: {
				type: "support",
				supportCount: 6,
				unSupportCount: 6
			},
			commentCount: 66,
			shareCount: 66
		},
		{
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
		},
	]
	
	export default {
		components:{
			topicInfo,
			commonListItem
		},
		
		data() {
			return {
				topicInfo: {
					id: 0,
					titlePic: '',
					title: '',
					desc: '',
					totalNum: 0,
					todayNum: 0
				},
				list: demo
			};
		},
		onLoad(option) {
			console.log(option)
			this.topicInfo = JSON.parse(option.item)
			console.log(this.topicInfo)
		},
		methods: {
			
		}
	}
</script>

<style scoped lang="less">
	@import (reference) '@/common/index.less';
	
	.top {
		.h-10;
		line-height: 100rpx;
		.text-lg;
	}

</style>
