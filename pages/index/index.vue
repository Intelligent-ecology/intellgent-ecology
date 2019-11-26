<template>
	<view class="content">
		<image class="backgroundimg" src="../../static/img/bg.jpg"/>
		<!-- 轮播图开始 -->
		<view class="swiper">
			<!-- 左边框 -->
			<view class="left"></view>
			<!-- 轮播图图片 -->
			<view class="home_list">
				<swiper indicator-dots="true" autoplay="true" interval="2000" circular="true">
				  <block v-for="(item, index) in banner" :key="index">
				    <swiper-item>
				      <image :src="item"></image>
				    </swiper-item>
				  </block>
				</swiper>
			</view>
			<!-- 右边框 -->
			<view class="right"></view>
		</view>
		<!-- 轮播图结束 -->
		<!-- 拼团开始 -->
		<view class="pinker">
			<view class="top">
				<view class="name">快来和我拼团吧</view>
				<image src="../../static/img/bg_11.png"></image>
			</view>
			<!-- 推荐商品 -->
			<view class="ranking-shop">
				<view class="content-shop">
					<image src='../../static/img/bg1.jpg'></image>
					<!-- 主推内容开始 -->
					<view class='assembleCon'>
					  <!-- 描述 -->
					  <view class='text1'>双面头颈椎设计呵护</view>
					  <view class='text1'>泰国乳胶枕芯</view>
					  <!-- 价格 -->
					  <view class='price'>
					    <!-- 新价格 -->
					    <text class='num'>￥</text><text class='newPrice'>150</text>
					    <!-- 旧价格 -->
					    <view class='oldPrice'>￥120</view>
					  </view>
					  <!-- 限时抢购 -->
					  <view class='buying'>
					    <text>限时抢购</text>
					  </view>
					</view>
				</view>
				
			</view>
			
			<view class="avatar">
				<view class='avatar_item'>
				  <view>?</view>
				  <view>?</view>
				  <view>?</view>
				  <view>?</view>
				  <view>?</view>
				</view>
			</view>
			<view class="countDown">
				<view class="countDownPeople">
					仅剩3人，快呼唤小伙伴来参加吧！
				</view>
				<view class="timeBox">
					<view class="line left"></view>
					<view class="">剩余</view>
					<view class="timeNum">23</view>
					<view class="">:</view>
					<view class="timeNum">23</view>
					<view class="">:</view>
					<view class="timeNum">23</view>
					<view class="">结束</view>
					<view class="line right"></view>
				</view>
			</view>
		</view>
		<!-- 拼团结束 -->
		<!-- 优惠券开始 -->
		<view class="coupon">
			<view class="coupon-text">
				<image src="../../static/img/logo1.gif" ></image>
				<view class="coupon-title">玩趣加购  分享有礼</view>
				<view class="coupon-name">先领券  再购物</view>
			</view>
			<view class="coupon-img">
				<view class="coupon-card">
					<view class="coupon-cardTitle">RMB</view>
					<view class="">
						
					</view>
				</view>
			</view>
		</view>
		<!-- 优惠券结束 -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				banner:["../../static/img/1.jpg","../../static/img/bg.jpg"]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	@import "./index.css";
	
</style>
