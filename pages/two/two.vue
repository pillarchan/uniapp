<template>
	<view>
		<view class="">我是two</view>
		<button size="default" plain="true" type="primary" @click="topath">toone</button>
	</view>
</template>

<script>
export default {
	data() {
		return {

		};
	},
	methods:{
		topath(){
			uni.redirectTo({
				url:"../one/one"
			})
		}
	}
}
</script>

<style lang="scss"></style>
