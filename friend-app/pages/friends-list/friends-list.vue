<template>
	<view class="body">
		<!-- tab切换 -->
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollItemStyle="width:33%;"
			scrollStyle="border-bottom:0;">
		</swiper-tab-head>

		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(item,index) in newslist" :key="index">
					<scroll-view scroll-y="true" class="list" @scrolltolower="loadmore(index)">
						<template v-if="item.list.length>0">
							<!-- 图文列表 -->
							<block v-for="(item,index1) in item.list" :key="index1">
								<friend-list-item :item="item" :index="index1"></friend-list-item>
							</block>
						</template>
						<template v-else>
							<!-- 无内容默认 -->
							<nothing></nothing>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>

	</view>
</template>

<script>
	const demo = [{
			list: [{
					avatar: "/static/img/me.jpg",
					nickname: "陶然然",
					age: 18,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user2.jpg",
					nickname: "尚宇驰",
					age: 22,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user1.jpg",
					nickname: "杨阳",
					age: 22,
					gender: 0,
					isFollow: true
				},
				{
					avatar: "/static/img/user3.jpg",
					nickname: "何明明",
					age: 22,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user4.jpg",
					nickname: "王浩南",
					age: 22,
					gender: 0,
					isFollow: true
				},
			]
		},
		{
			list: [{
					avatar: "/static/img/me.jpg",
					nickname: "陶然然",
					age: 18,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user2.jpg",
					nickname: "尚宇驰",
					age: 22,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user1.jpg",
					nickname: "杨阳",
					age: 22,
					gender: 0,
					isFollow: true
				},
				{
					avatar: "/static/img/user3.jpg",
					nickname: "何明明",
					age: 22,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user4.jpg",
					nickname: "王浩南",
					age: 22,
					gender: 0,
					isFollow: true
				},
			]
		},
		{
			list: [{
					avatar: "/static/img/me.jpg",
					nickname: "陶然然",
					age: 18,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user2.jpg",
					nickname: "尚宇驰",
					age: 22,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user1.jpg",
					nickname: "杨阳",
					age: 22,
					gender: 0,
					isFollow: true
				},
				{
					avatar: "/static/img/user3.jpg",
					nickname: "何明明",
					age: 22,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/user4.jpg",
					nickname: "王浩南",
					age: 22,
					gender: 0,
					isFollow: true
				},
				{
					avatar: "/static/img/avatar4.jpg",
					nickname: "mob",
					age: 22,
					gender: 1,
					isFollow: true
				},
				{
					avatar: "/static/img/avatar5.png",
					nickname: "不知名jo厨",
					age: 22,
					gender: 0,
					isFollow: true
				},
				{
					avatar: "/static/img/6.jpg",
					nickname: "凛",
					age: 22,
					gender: 1,
					isFollow: true
				}
			]
		}
	]

	import swiperTabHead from "@/components/common/swiper-tab-header.vue"
	import friendListItem from "@/components/common/friend-list-item.vue"

	export default {
		components: {
			swiperTabHead,
			friendListItem
		},
		data() {
			return {
				swiperheight: 500,
				tabIndex: 0,
				tabBars: [{
						name: "互关",
						id: "huguan",
						num: demo[0].list.length
					},
					{
						name: "关注",
						id: "guanzhu",
						num: demo[1].list.length
					},
					{
						name: "粉丝",
						id: "fensi",
						num: demo[2].list.length
					},
				],
				newslist: demo
			};
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100)
					this.swiperheight = height;
				}
			});
		},
		//监听导航按钮时间
		onNavigationBarButtonTap(e) {
			if (e.index === 0) {
				uni.navigateBack({
					delta: 1
				});
			}
		},
		methods: {
			//tabbar点击事件
			tabtap(index) {
				this.tabIndex = index;
			},
			//滑动事件
			tabChange(e) {
				this.tabIndex = e.detail.current;
			}
		}
	}
</script>

<style>

</style>
