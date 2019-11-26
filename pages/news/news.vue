<template>
	<view>
		<view class="topImg">
			<image src="../../static/img/banner.png" mode=""></image>
			<view class="recommend">
				<view class="txt1">
					<text>RECOMMENDED</text>
					<text>每日推荐</text>
				</view>
				<view class="txt2">
					每日推荐
				</view>
			</view>
		</view>
		<view class="newsList">
			<view class="newsItem">
				<!-- <view class="iconfont icon-shoucang"></view> -->
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				newsList:[{
					id:1,
					img:"../../static/img/4.png",
					title:"泰国平面波浪枕",
					material:"泰国天然乳胶原料",
					price:"228.0"
				},{
					id:2,
					img:"../../static/img/4.png",
					title:"泰国平面波浪枕",
					material:"泰国天然乳胶原料",
					price:"228.0"
				},{
					id:3,
					img:"../../static/img/4.png",
					title:"泰国平面波浪枕",
					material:"泰国天然乳胶原料",
					price:"228.0"
				},{
					id:4,
					img:"../../static/img/4.png",
					title:"泰国平面波浪枕",
					material:"泰国天然乳胶原料",
					price:"228.0"
				}]
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
