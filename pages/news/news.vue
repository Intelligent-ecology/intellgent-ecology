<template>
	<view class="content">
		<!-- 推荐商品图片 -->
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
		<!-- 新品列表 -->
		<view class="newsList">
			<view class="newsItem" v-for="(item,index) in newsList" :key="index">
				<view class="collect">
					<text @tap="collect" :class="item.collect?'iconfont icon-shoucang1':'iconfont icon-shoucang'" :data-id="index"></text>
				</view>
				<view class="product" @tap="goDetail" :data-id="item.id" :data-index="index">
					<image :src="item.img" mode=""></image>
				</view>
				<view class="productInfo">
					<view class="title">{{item.title}}</view>
					<view class="material">{{item.material}}</view>
					<view class="price">￥{{item.price}}</view>
				</view>
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
					price:"228.0",
					collect:false
				},{
					id:2,
					img:"../../static/img/4.png",
					title:"泰国平面波浪枕",
					material:"泰国天然乳胶原料",
					price:"228.0",
					collect:false
				},{
					id:3,
					img:"../../static/img/4.png",
					title:"泰国平面波浪枕",
					material:"泰国天然乳胶原料",
					price:"228.0",
					collect:false
				}],
				collectList:[]
			}
		},
		methods: {
			collect(e){
				// this.collectList=[]
				this.newsList[e.currentTarget.dataset.id].collect=!this.newsList[e.currentTarget.dataset.id].collect
				// for(var i=0;i<this.newsList.length;i++){
				// 	if(this.newsList[i].collect){
				// 		this.collectList.push(this.newsList[i])
				// 		uni.setStorage({
				// 			key:'collectList',
				// 			data:JSON.stringify(this.collectList)
				// 		})
				// 	}
				// }
				// uni.getStorage({
				// 	key:'collectList',
				// 	success(e){
				// 		console.log(JSON.parse(e.data))
				// 	}
				// })
				uni.setStorage({
					key:'collectList',
					data:JSON.stringify(this.newsList)
				})
			},
			goDetail(e){
				// console.log(e.currentTarget.dataset.id)
				wx.navigateTo({
					url:"../details/details?item="+JSON.stringify(this.newsList[e.currentTarget.dataset.index])
				})
			}
		},
		onLoad(){
			uni.setStorage({
				key:'collectList',
				data:JSON.stringify(this.newsList)
			})
		},
		onShow(){
			var that=this
			uni.getStorage({
				key:'collectList',
				success(e){
					that.newsList=JSON.parse(e.data)
				}
			})
		}
	}
</script>

<style scoped>
	@import "./news.css";
</style>
