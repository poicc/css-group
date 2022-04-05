<template>
	<view>
		<scroll-view scroll-x class="scroll-row shadow" style="100rpx;">
			<view v-for="(item, index) in tabBars" class="scroll-row-item px-3 py-2 font-md" :key="index"
				:class="tabIndex === index ? 'text-primary  text-lg font-weight-bolder' : '' " @tap="changeTab(index)">
				{{ item.name }}
			</view>
		</scroll-view>

		<swiper :duration="150" :current="tabIndex" :style=" 'height:' + scrollH + 'px;' ">
			<swiper-item v-for="(item,index) in newsList" :key="index">
				<scroll-view scroll-y="true" :style=" 'height:' + scrollH + 'px;' " @scrolltolower="loadmore(index)">
					<template v-if="item.list.length > 0">
						<view class="p-2">
							<view v-for="(item2, index2) in item.list" :key="index2" class="mb-3">
								<common-list-item :item="item2" :index="index2" @follow="follow" @doSupport="doSupport"
									@unFollow="unFollow">
								</common-list-item>
								<divider v-if="index2 != item.list.length -1"></divider>
							</view>
							<!-- 上拉加载组件 -->
							<loadmore :loadmore="item.loadmore"></loadmore>
						</view>
					</template>
					<template v-else>
						<nothing></nothing>
					</template>
				</scroll-view>
			</swiper-item>
		</swiper>

	</view>
</template>

<script>
	import commonListItem from '@/components/common/common-list-item.vue';
	import loadmore from '@/components/common/loadmore.vue'
	export default {
		components: {
			commonListItem,
			loadmore
		},
		data() {
			return {
				scrollH: 600,
				tabIndex: 0,
				tabBars: [{
						name: '推荐',
					},
					{
						name: '二创',
					}, {
						name: '动画',
					}, {
						name: '游戏',
					}, {
						name: '音乐',
					}, {
						name: '国创',
					}, {
						name: '番剧',
					}
				],
				newsList: [],
			}
		},
		onLoad() {
			let res = uni.getSystemInfo({
				success: res => {
					console.log(res)
					this.scrollH = res.windowHeight + uni.upx2px(100)
				}
			})
			this.getData()
		},
		methods: {
			getData() {
				let arr = []
				for (let i = 0; i < this.tabBars.length - 1; i++) {
					let obj = {
						// 1.上拉加载更多 2.加载中 3.没有更多了
						loadmore: '上拉加载更多',
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
					}
					arr.push(obj)
				}
				//最后一个选项卡内容
				let emptyObj = {
					list: []
				}
				arr.push(emptyObj)
				this.newsList = arr
			},
			follow(e) {
				let list = this.newsList[this.tabIndex].list
				list[e].isFollow = true
				uni.showToast({
					title: "关注成功"
				})
			},

			unFollow(e) {
				let list = this.newsList[this.tabIndex].list
				list[e].isFollow = false
				uni.showToast({
					title: "取关成功"
				})
			},


			doSupport(e) {
				let list = this.newsList[this.tabIndex].list
				let item = list[e.index]
				if (item.support.type == '') {
					e.type === 'unSupport' ? item.support.unSupportCount++ : item.support.supportCount++
					item.support.type = e.type
					return
				}
				// 执行了"踩"操作
				if (item.support.type === 'support' && e.type === 'unSupport') {
					item.support.supportCount--;
					item.support.unSupportCount++;
					item.support.type = 'unSupport'
				} else if (item.support.type === 'unSupport' && e.type === 'support') {
					item.support.supportCount++;
					item.support.unSupportCount--;
					item.support.type = 'support'
				}
			},
			//切花选项卡
			changeTab(index) {
				if (this.tabIndex === index) {
					return
				}
				console.log(index)
				this.tabIndex = index
			},
			//监听滑动
			//上拉加载更多
			loadmore(index) {
				let item = this.newsList[index]
				//判断是否处于可加载状态
				if (item.loadmore !== '上拉加载更多') {
					return;
				}
				item.loadmore = "加载中..."
				//模拟数据请求
				setTimeout(() => {
					item.list = [...item.list, ...item.list]
					item.loadmore = '上拉加载更多'
				}, 1500)
			}
		}
	};
</script>

<style lang="less" scoped>
	@import (reference) '@/common/index.less';

	.scroll-row {
		width: 100%;
		white-space: nowrap;
	}

	.scroll-row-item {
		display: inline-block !important;
	}


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
