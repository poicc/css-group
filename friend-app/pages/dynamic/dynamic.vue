<template>
	<view>
		<uni-nav-bar statusBar backgroundColor="#4DB6AC" color="#ffffff" title="动态"></uni-nav-bar>

		<scroll-view scroll-y class="mt-1">
			<!-- 轮播图 -->
			<swiper class="px-2" indicator-active-color="#4DB6AC" indicator-color="#fff3e0" :indicator-dots="true"
				:autoplay="true" :interval="3000" :duration="1000">
				<block v-for="(item,index) in topic.swiper" :key="index">
					<swiper-item>
						<image class="w-full rounded" :src="item.src" mode="aspectFill" lazy-load></image>
					</swiper-item>
				</block>
			</swiper>

			<!-- 热门分类 -->
			<hot-topic :nav="topic.nav"></hot-topic>

			<!-- 最近更新 -->
			<view class="px-2">
				<view class="text-lg mb-1">最近更新</view>
				<block v-for="(item,index) in topic.list" :key="index">
					<topic-list-item :item="item" :index="index"></topic-list-item>
				</block>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import uniNavBar from "@/components/uni/uni-nav-bar/uni-nav-bar.vue";
	import hotTopic from "@/components/common/hot-topic.vue";
	import topicListItem from "@/components/common/topic-list-item.vue";

	export default {
		components: {
			uniNavBar,
			hotTopic,
			topicListItem
		},
		data() {
			return {
				swiperheight: 600,
				topic: {
					swiper: [{
							src: "/static/img/banner1.jpg"
						},
						{
							src: "/static/img/banner2.jpg"
						},
						{
							src: "/static/img/banner3.jpeg"
						}
					],
					nav: [{
							name: "二创"
						},
						{
							name: "动画"
						},
						{
							name: "游戏"
						},
						{
							name: "音乐"
						},
						{
							name: "国创"
						},
						{
							name: "番剧"
						},
					],
					list: [{
							id: 1,
							titlePic: "/static/img/1.jpeg",
							title: "明日香",
							desc: "我想不起来任何你我共度的时光，但那无关紧要.",
							totalNum: 50,
							todayNum: 10
						},
						{
							id: 2,
							titlePic: "/static/img/2.jpg",
							title: "樱满集",
							desc: "就算是对我抱有敌意的人，也是被某个人深爱着而降生在这个世界上的。",
							totalNum: 50,
							todayNum: 10
						},
						{
							id: 3,
							titlePic: "/static/img/3.jpg",
							title: "玛奇玛",
							desc: "尸体在说话",
							totalNum: 50,
							todayNum: 10
						},
						{
							id: 4,
							titlePic: "/static/img/4.jpeg",
							title: "鼠苑",
							desc: "对自己老实，对他人亲切，这是我最近的座右铭",
							totalNum: 50,
							todayNum: 10
						},
						{
							id: 5,
							titlePic: "/static/img/5.jpg",
							title: "乔鲁诺",
							desc: "所谓觉悟，就是在漆黑的荒野上开辟出一条理当前进的光明大道。",
							totalNum: 50,
							todayNum: 10
						},
						{
							id: 6,
							titlePic: "/static/img/6.jpg",
							title: "松冈凛",
							desc: "没有什么才能比努力更重要～",
							totalNum: 50,
							todayNum: 10
						},
					]
				}
			};
		},
		onLoad() {},
		methods: {
			gotoDetail(index) {
				uni.navigateTo({
					url: "../topic-detail/topic-detail"
				})
			}
		}
	}
</script>

<style scoped>
	.topic-swiper {
		padding: 0 20upx 20upx 20upx;
	}

	.topic-swiper image {
		width: 100%;
		border-radius: 10upx;
	}

	.topic-new {
		padding: 20upx;
	}

	.topic-new>view:first-child {
		padding-bottom: 5upx;
		font-size: 32upx;
	}
</style>
