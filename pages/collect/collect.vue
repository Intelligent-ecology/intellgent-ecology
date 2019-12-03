<template>
	<view class="collect">
		<view class="content"  >
			<view class="commodity"v-for="(item,index) in news" :key="index">
				<image :src="item.img" class="img"></image>
				<view class="content-text">
					<view class="title">
						{{item.title}}
					</view>
					<view class="depreciate">
						比收藏时降价20.00元
					</view>
					<view class="price">
						<view class="priceNum">
							￥<text>{{item.price}}</text>
						</view>
						
						<text class="collectPeople">已有10人收藏	</text>
					</view>
				</view>
			</view>
		</view>
		<!-- 没有收藏商品时开始 -->
		<view class="none" v-show=true>
			<view class="text">
				暂无商品收藏
			</view>
			<image src="../../static/img/empty.png" mode=""></image>
		</view>
		<!-- 没有收藏商品时开始 -->
	</view>
</template>

<script>
	export default{
		data(){
			return{
				news:[]
			}
		},
		methods:{
			
		},
		onLoad() {
			var that=this
			uni.getStorage({
				key:'collectList',
				success(e){
					that.news=JSON.parse(e.data)
					console.log(JSON.parse(e.data));
				}
			})
		}
	}
</script>

<style>
	@import "./collect.css"
</style>
