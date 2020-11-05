<template>
	<view class="content">
		<view>{{ msgText }}</view>
		<button type="primary" size="mini" @click="test">子传父</button>
		<button type="primary" size="mini" @click="testUni">uni子传父</button>
		<swiper indicator-dots="true" autoplay="true" interval="2000" duration="500" @change="testChange">
			<swiper-item v-for="(v, i) in arrayList" :key="i">{{ v }}</swiper-item>
		</swiper>
		<scroll-view :scroll-x="true" style="white-space: nowrap;">
			<view :class="['box','box1']">A</view>
			<view :class="['box','box2']">B</view>
			<view :class="['box','box3']">C</view>
		</scroll-view>
		
	</view>

	
</template>

<script>
export default {
	data() {
		return {
			arrayList: [1, 2, 3]
		};
	},
	props: ['msgText'],
	methods: {
		test() {
			this.$emit('testshow', { name: 'lucy' });
		},
		testUni() {
			uni.$emit('testEmit', { name: 'lily' });
		},
		testChange(e) {
			console.log(e.detail.current);
		}
	}
};
</script>

<style lang="scss">
	.box{
		border: 1px solid black;
		width: 400upx;
		height: 80upx;
		color: #ffd;
		display: inline-block;
	}
	.box1{
		background-color: red;
	}
	.box2{
		background-color: yellow;
	}
	.box3{
		background-color: blue;
	}
</style>
