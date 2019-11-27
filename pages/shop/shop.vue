<template>
	<view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				productList:[]
			}
		},
		methods: {
			
		},
		onShow(){
			var that=this
			uni.getStorage({
				key:'cart',
				success(e){
					that.productList=JSON.parse(e.data)
				}
			})
			
		}
	}
</script>

<style>

</style>
