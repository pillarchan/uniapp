<template>
	<view class="content">
		<text>我是首页</text>
		{{ 'Leo' }}
		<view>{{ msg }}</view>
		<view>{{ msg + 'Jill' }}</view>
		<view>{{ msg.indexOf('na') === 0 ? '最靓的妞' : '最靓的仔' }}</view>
		<view>{{ '最靓的妞'.substring(0, 2) }}</view>
		<view>{{ false || '' || '前面都是假我就显示啦' }}</view>
		<image :src="imgUrl" mode=""></image>
		<view :class="'box' + 11"></view>
		<view :style="style1"></view>
		<view :style="[style1, sytle2]"></view>
		<view :class="['box', 'box1']"></view>
		<view :class="flag" @click="changeClass"></view>
		<view v-for="(item, index) in names" :key="index" :class="{ 'select-name': index === current }" @click="chooseName(index)">{{ item }}</view>
		<Demo :msgText="msg" @testshow="testEvent"></Demo>
		
		<button size="default" plain="true" type="primary" @click="topath">toone</button>
	</view>
</template>

<script>
import Demo from '../demo1/demo1';
export default {
	data() {
		return {
			msg: 'Anna',
			imgUrl: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/doc/github.svg',
			style1: { width: '100rpx', height: '100rpx', backgroundColor: 'orange' },
			sytle2: { border: '1px solid black' },
			names: ['Leo', 'Jill', 'Ken', 'Jerry'],
			current: 0,
			flag: { box: true }
		};
	},
	onLoad() {
		console.log("onLoad 进入页面只运行一次,页面加载时触发")
		uni.$on('testEmit', val => {
			console.log(val);
		});
	},
	onReady() {
		console.log("onReady 进入页面只运行一次,页面渲染完成后触发")
	},
	onShow() {
		console.log("onShow 进入页面多次运行,页面渲染完成后触发")
	},
	onHide(){
		console.log("onHide 离开页面时多次执行")
	},
	onPullDownRefresh() {
		console.log("下拉刷新")
	},
	onTabItemTap() {
		console.log("点击了底部导航栏")
	},
	methods: {
		changeClass() {
			let rand = Math.floor(Math.random() * 10);
			console.log(rand);
			if (rand <= 5) {
				this.flag = { box: true };
			} else {
				this.flag = { box11: true };
			}
		},
		chooseName(index) {
			this.current = index;
		},
		testEvent(val) {
			console.log(val);
		},
		topath(){
			uni.navigateTo({
				url:"../one/one?name='One'"
			})
		}
	},
	components: {
		Demo
	}
};
</script>

<style lang="scss">
.content {
	flex-flow: column nowrap;
}
.box11 {
	width: 200rpx;
	height: 200rpx;
	background-color: red;
}
.box {
	width: 200rpx;
	height: 200rpx;
	border: 1px solid black;
}
.box1 {
	background-color: blue;
}
.select-name {
	color: $uni-color-deapred;
}
</style>
