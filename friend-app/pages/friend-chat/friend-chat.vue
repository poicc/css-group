<template>
	<view class="p-2" :style="{height:height + 'px'}">
		<!-- 聊天列表 -->
		<scroll-view scroll-y :scroll-with-animation="true" lower-threshold="100px" class="pb-10">
			<block v-for="(item,index) in list" :key="index">
				<chat-list-item :item="item" :index="index"></chat-list-item>
			</block>
		</scroll-view>
		<!-- 输入框 -->
		<friend-chat-bottom @submit="submit"></friend-chat-bottom>
	</view>
</template>

<script>
const arr = [
	{
		isMe: true,
		avatar: '/static/img/avatar1.jpg',
		type: 'text',
		content: '接口400了'
	},
	{
		isMe: false,
		avatar: '/static/img/user1.jpg',
		type: 'text',
		content: '收到'
	},
	{
		isMe: false,
		avatar: '/static/img/user1.jpg',
		type: 'text',
		content: '马上改'
	},
	{
		isMe: true,
		avatar: '/static/img/avatar1.jpg',
		type: 'text',
		content: '今天加班吗 老板'
	},
	{
		isMe: false,
		avatar: '/static/img/user1.jpg',
		type: 'text',
		content: '加班'
	},
	{
		isMe: true,
		avatar: '/static/img/avatar1.jpg',
		type: 'img',
		content: '/static/img/ku.jpg'
	}
];
import friendChatBottom from '@/components/common/friend-chat-bottom.vue';
import chatListItem from '@/components/common/chat-list-item.vue';
import time from '@/common/time.js';
export default {
	components: {
		friendChatBottom,
		chatListItem
	},
	data() {
		return {
			list: [],
			height:""
		};
	},
	onLoad() {
		this.height = uni.getSystemInfoSync().windowHeight
		this.getdata();
	},
	methods: {
		//获取聊天数据
		getdata() {
			//模拟从服务器获得数据
			this.list = arr;
		},
		submit(data) {
			if(!data){
				return
			}
			//发送逻辑
			let obj={
				isMe: true,
				avatar: '/static/img/avatar1.jpg',
				type: 'text',
				content: data ,
			};
			this.list.push(obj)
		}
	}
};
</script>

<style lang="less" scoped></style>
