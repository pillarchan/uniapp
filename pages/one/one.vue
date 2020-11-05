<template>
	<view>
		<view class="">我是one</view>
		<button size="default" plain="true" type="primary" @click="topath">totwo</button>
		<button size="default" plain="true" type="primary" @click="toback">toback</button>
		<button size="default" plain="true" type="primary" @click="toswichbar">totarbar</button>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	onLoad(option) {
		console.log(option);
	},
	methods: {
		topath() {
			uni.navigateTo({
				url: '../two/two'
			});
		},
		toback() {
			uni.navigateBack({});
		},
		toswichbar() {
			uni.switchTab({
				url: '../demo1/demo1'
			});
		}
	}
};
</script>

<style lang="scss"></style>
