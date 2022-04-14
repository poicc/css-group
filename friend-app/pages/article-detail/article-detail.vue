<template>
	<view>
		<detail-info :item="detail"></detail-info>

		<view class="text-xl p-2 font-weight-bold">
			最新评论 {{comments.length}}
		</view>
		<view class="uni-comment px-2">
			<block v-for="(item,index) in comments" :key="index">
				<comments-item :item="item" :index="index"></comments-item>
			</block>
		</view>

		<!-- 分享弹框 -->
		<uni-popup ref="popup" type="bottom">
			<view class="text-center py-2 font-md border-bottom">分享到</view>
			<view class="flex align-center">
				<view class="icon-wrapper">
					<view class="iconfont icon-QQ icon" style="background-color: #4DB6AC;"></view>
						<text class="font-sm mt-1 text-muted">QQ</text>
				</view>
					<view class="icon-wrapper">
						<view class="iconfont icon-weixin icon" style="background-color: #4DB6AC;"></view>
						<text class="font-sm mt-1 text-muted">微信</text>
					</view>
					<view class="icon-wrapper">
						<view class="iconfont icon-xinlangweibo icon" style="background-color:#4DB6AC;"></view>
						<text class="font-sm mt-1 text-muted">微博</text>
					</view>
				</view>
				<view class="text-center py-2 font-md border-top" @tap="cancel()">取消</view>
		</uni-popup>
	</view>
</template>

<script>
	import detailInfo from "@/components/common/detail-info.vue";
	import commentsItem from "@/components/common/comments-item.vue";
	import uniPopup from "@/components/uni/uni-popup/uni-popup.vue";
	export default {
		components: {
			detailInfo,
			commentsItem,
			uniPopup
		},
		data() {
			return {
				detail: {},
				comments: [],
				shareShow: false
			}
		},
		onLoad(e) {

			const obj = JSON.parse(e.detailData);
			console.log(obj)
			this.initdata(obj)
			this.detail = obj;
			this.getcomments();
		},
		//监听导航右边按钮
		onNavigationBarButtonTap(e) {
			if (e.index === 0) {
				console.log("分享")
				this.$refs.popup.open()
			}
		},
		onBackPress() {
			this.$refs.popup.close()
		},
		methods: {
			//初始化数据，将窗口标题修改为文章标题
			initdata(obj) {
				uni.setNavigationBarTitle({
					title: obj.nickname
				});
			},
			cancel() {
				this.$refs.popup.close()
			},
			getcomments() {
				let arr = [{
						id: 1,
						fid: 0,
						avatarUrl: "/static/img/avatar4.jpg",
						nickname: "美绪",
						time: "2022-04-10 12:12:12",
						content: "我们所度过的每一个日常，也许就是接连发生的奇迹",
					},
					//子级评论
					{
						id: 2,
						fid: 1,
						avatarUrl: "/static/img/avatar1.jpg",
						nickname: "poicc",
						time: "2022-04-10 12:12:12",
						content: "珍惜这段缘",
					},
					{
						id: 3,
						fid: 1,
						avatarUrl: "/static/img/6.jpg",
						nickname: "凛",
						time: "2022-04-10 12:12:12",
						content: "yeah!!",
					},
					{
						id: 4,
						fid: 1,
						avatarUrl: "/static/img/avatar5.png",
						nickname: "阿强",
						time: "2022-04-10 12:12:12",
						content: "呀嘞呀嘞",
					}
				];
				this.comments = arr;
			},
		}
	}
</script>

<style scoped lang="less">
	@import (reference) '@/common/index.less';

	.u-comment {
		padding: 0 20rpx;
	}

	.u-comment-title {
		padding: 20rpx;
		font-size: 30rpx;
		font-weight: bold;
	}

	.icon-wrapper {
		.flex-1;
		.flex;
		.flex-col;
		.items-center;
		.justify-center;
		.py-2;
	}

	.icon {
		.text-white;
		.flex;
		.items-center;
		.justify-center;
		.text-xl;
		.rounded-full;
		.w-10;
		.h-10;
	}
</style>
