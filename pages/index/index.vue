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
					<view class="coupon-price">100</view>
					<view class="coupon-receive">x</view>
					<view class="coupon-collect">收藏+关注</view>
					<image src="../../static/img/empty.png"></image>
				</view>
				<view class="coupon-card">
					<view class="coupon-cardTitle">RMB</view>
					<view class="coupon-price">100</view>
					<view class="coupon-receive">x</view>
					<view class="coupon-collect">收藏+关注</view>
					<image src="../../static/img/empty.png"></image>
				</view>
				<view class="coupon-card">
					<view class="coupon-cardTitle">RMB</view>
					<view class="coupon-price">100</view>
					<view class="coupon-receive">x</view>
					<view class="coupon-collect">收藏+关注</view>
					<image src="../../static/img/empty.png"></image>
				</view>
				<view class="coupon-card">
					<view class="coupon-cardTitle">RMB</view>
					<view class="coupon-price">100</view>
					<view class="coupon-receive">x</view>
					<view class="coupon-collect">收藏+关注</view>
					<image src="../../static/img/empty.png"></image>
				</view>
			</view>
		</view>
		<!-- 优惠券结束 -->
		
		
		
		
		<!-- 店家推荐开始 -->
		<view class="dotey">
		  <view class='jewel' style="background:url('../../static/img/bg_11.png')">
		    <image src='../../static/img/logo3.gif'></image>
		  </view>
		  <view class='common'>
		    <image src='../../static/img/logo1.gif'></image>
		    <view>泰国平面波浪枕</view>
		  </view>
		</view>
		<!-- 店家推荐结束 -->
		<!-- 产品1 -->
		<view class="body1">
		  <image class='bgImage' src='../../static/img/pillow_1.gif'></image>
		  <view class='con'>
		    <image src='../../static/img/logo2.gif' class='iconImg'></image>
		    <text>￥</text><text class='price'>228.00</text>
		    <view class='button'>
		      <text>立即购买</text>
		      <icon class='iconfont icon-youjiantou'></icon>
		    </view>
		  </view>
		</view>
		<!-- 产品1 -->
		<!-- 城市 -->
		<view class="city">
		  <image src="../../static/img/bg_1.gif"></image>
		</view>
		<!-- 产品2开始 -->
		<view class="body2">
		  <image src='../../static/img/pillow_2.gif' class='img1'></image>
		  <view class='bodyCon2'>
		    <image src='../../static/img/pillow_3.gif' class='img2'></image>
		    <view class='bodyPrice'>
		      <text>￥</text><text class='price'>228.00</text>
		    </view>
		    <view class='button'>
		      <text>立即购买</text>
		      <icon class='iconfont icon-youjiantou'></icon>
		    </view>
		  </view>
		</view>
		<!-- 产品2结束 -->
		<!-- 产品3开始 -->
		<view class='common'>
		  <image src='../../static/img/logo1.gif'></image>
		  <view>泰国平面波浪枕</view>
		</view>
		<!-- 产品3内容 -->
		<view class="body3">
		  <!-- 产品3内容图片 -->
		  <view class='person'>
		    <image src='../../static/img/pillow_4.gif'></image>
		  </view>
		  <view class='commodity'>
		    <view class='center1'>
		      <text class='title'>波浪按摩枕</text>
		      <image src="../../static/img/pillow_2.gif" class='img3'></image>
		      <view class='bottom'>
		        <image src='../../static/img/logo2.gif' class='iconimg'></image>
		        <text>￥</text><text class="price">238.00</text>
		        <view class='button'>
		          <text>立即购买</text>
		          <icon class='iconfont icon-youjiantou'></icon>
		        </view>
		      </view>
		    </view>
		    <view class='center1'>
		      <text class='title'>狼牙按摩枕</text>
		      <image src="../../static/img/pillow_2.gif" class='img3'></image>
		      <view class='bottom'>
		        <image src='../../static/img/logo2.gif' class='iconimg'></image>
		        <text>￥</text><text class="price">228.00</text>
		        <view class='button'>
		          <text>立即购买</text>
		          <icon class='iconfont icon-youjiantou'></icon>
		        </view>
		      </view>
		    </view>
		  </view>
		</view>
		<!-- 产品3结束 -->
		<!-- 产品4开始 -->
		<view class="dotey">
		  <view class='jewel' style="background:url('../../static/img/bg_11.png')">
		    <image src='../../static/img/logo3.gif'></image>
		  </view>
		  <view class='common'>
		    <image src='../../static/img/logo1.gif'></image>
		    <view>泰国平面波浪枕</view>
		  </view>
		</view>
		<view class="body4">
		  <view class='commodity'>
		    <view class='center1'>
		      <text class='title'>波浪按摩枕</text>
		      <image src="../../static/img/pillow_2.gif" class='img3'></image>
		      <view class='bottom'>
		        <image src='../../static/img/logo2.gif' class='iconimg'></image>
		        <text>￥</text><text class="price">238.00</text>
		        <view class='button'>
		          <text>立即购买</text>
		          <icon class='iconfont icon-youjiantou'></icon>
		        </view>
		      </view>
		    </view>
		    <view class='center1'>
		      <text class='title'>狼牙按摩枕</text>
		      <image src="../../static/img/pillow_2.gif" class='img3'></image>
		      <view class='bottom'>
		        <image src='../../static/img/logo2.gif' class='iconimg'></image>
		        <text>￥</text><text class="price">228.00</text>
		        <view class='button'>
		          <text>立即购买</text>
		          <icon class='iconfont icon-youjiantou'></icon>
		        </view>
		      </view>
		    </view>
		  </view>
		</view>
		<!-- 产品4结束 -->
		<view class="girl">
		  <image src="../../static/img/pillow_5.gif"></image>
		</view>
		<!-- 排行榜开始 -->
		<view class="row">
		  <!-- 排行榜头部 -->
		  <view class="header">
		    <text class='ranking'>排行榜</text>
		    <view class='volume'>
		      <text class='active'>销量排行</text>
		    </view>
		  </view>
		  <!-- 排行内容 -->
		  <view class="rowList">
		      <!-- 商品 -->
			<block v-for="(item,index) in 3" :key="index">
		      <view class='center'>
		        <!-- 图片 -->
		        <image src="../../static/img/pillow_2.gif" ></image>
		        <!-- 序号 -->
		        <view class='circle'>
		          <text>1</text>
		        </view>
		        <!-- 描述 -->
		        <view class='text'>
		          <text>泰国乳胶狼牙按摩枕</text>
		          <text class='person1'>199人付款</text>
		        </view>
		      </view>
		    </block>
		  </view>
		</view>
		<!-- 排行榜结束 -->
		
		
		
		<!-- 猜你喜欢开始 -->
		<view class="like">
		  <view class='title'>猜你喜欢</view>
		  <view class="likeList">
		    <block v-for="(item,index) in 4" :key="index">
		      <view class="like-item" bindtap='goDetail'>
		        <image src="../../static/img/pillow_2.gif"></image>
		        <view class="new_text1">泰国波浪平面枕</view>
		        <view class="new_text2">泰国天然乳胶原料</view>
		        <view class="new_text3">￥238.00</view>
		      </view>
		    </block>
		  </view>
		  <!-- 查看全部宝贝开始 -->
		  <view class='seeMore'>
		    <text>查看全部宝贝</text>
		  </view>
		  <!-- 查看全部宝贝结束 -->
		</view>
		<!-- 猜你喜欢结束 -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
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
	@import url("./index.css");
</style>
  
