<template>
	<view class="mine">
		<!-- 头部开始 -->
		<view class="header">
			<view class="icon">
				
			</view>
			<view class="buddha">
				<view class="headerImg">
					<open-data type="userAvatarUrl" class="imgHeadImg"></open-data>
				</view>
				<open-data type="userNickName" lang="zh_CN" class="name"></open-data>
			</view>
		</view>
		<!-- 头部结束 -->
		<!-- 我的订单开始 -->
		<view class="order">
			<view class="myOrder">
				我的订单
			</view>
			<view class="allOrder" @click="allOrder">
				查看全部订单
			</view>
		</view>
		<!-- 我的订单结束 -->
		<!-- 待收货、待发货，待评价开始 -->
		<view class="button">
			<view class="payment" @click="payment">代付款</view>
			<view class="share" @click="share">代分享</view>
			<view class="deliver" @click="deliver">代发货</view>
			<view class="receiving" @click="receiving">代收货</view>
			<view class="evaluate" @click="evaluate">代评价</view>
			
		</view>
		<!-- 待收货、待发货，待评价结束 -->
		<!-- 优惠券开始 -->
		<view class="coupon" @click="coupon">
			优惠券
		</view>
		<!-- 优惠券结束 -->
		<!-- 商品收藏开始 -->
		<view class="collect" @click="collect">
			商品收藏
		</view>
		<!-- 商品收藏结束 -->
		<!-- 历史浏览开始 -->
		<view class="browse" @click="browse">
			历史浏览
		</view>
		<!-- 历史浏览结束 -->
		<!-- 退款售后开始 -->
		<view class="refund" @click="refund">
			退款售后
		</view>
		<!-- 退款售后结束 -->	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			// 查看全部订单
			allOrder(){
				console.log('allOrder');
			},
			// 待付款
			payment(){
				console.log('payment');
			},
			// 待分享
			share(){
				console.log('share');
			},
			// 待发货
			deliver(){
				console.log('deliver');
			},
			// 待收货
			receiving(){
				console.log('receiving');
			},
			// 待评价
			evaluate(){
				console.log('evaluate');
			},
			// 优惠券
			coupon(){
				console.log('coupon');
				wx.navigateTo({
					url:"/pages/coupon/coupon"
				})
			},
			// 商品收藏
			collect(){
				console.log('collect');
				wx.navigateTo({
					url:"/pages/collect/collect"
				})
			},
			// 历史浏览
			browse(){
				console.log('browse');
				wx.navigateTo({
					url:"/pages/browse/browse"
				})
			},
			// 退款售后
			refund(){
				console.log('refund');
				wx.navigateTo({
					url:"/pages/refund/refund"
				})
			}
			
		}
	}
</script>

<style>
@import "./mine.css";
</style>
