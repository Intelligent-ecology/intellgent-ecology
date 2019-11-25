<template>
	<view class="content">
		<scroll-view scroll-y="true" style="height:92vh">
			<!-- 商品图片 -->
			<view class="topImg">
				<image src="../../static/img/2.jpg" mode=""></image>
				<view class='arrow' @tap='goBack'>
					<text class='iconfont icon-fanhui'></text>
				</view>
				<view class='cart'>
					<text class='iconfont icon-gouwuche'></text>
				</view>
				<view class='more'>
					<text class='iconfont icon-sangedian'></text>
				</view>
			</view>
			<!-- 商品信息 -->
			<view class='product'>
			  <view class='norms'>
			    <text>新款正品万泰林</text>
				<view class="shareBox">
					<view class="share">
						<text class='iconfont icon-fenxiang'></text>
						<text>分享</text>
					</view>
					<button open-type="share" plain="true" class="shareBtn"></button>
				</view>
			    
			</view>
			<!-- 价格范围 -->
			<view class='priceBox'>
			    ￥<text>118-159</text>
			</view>
			<view class='express'>
				<text>快递：免运费</text>
				<text class='saleNum'>已拼3.8万件</text>
			  </view>
			</view>
			<!-- 优惠券 -->
			<view class='coupon'>
				<view class='couponBox'> 
					<view>
						<image src="../../static/img/icon-1.png"></image>
						<text>10元店铺优惠券</text>
					</view>
					<view>
						<image src="../../static/img/icon-1.png"></image>
						<text>20元店铺优惠券</text>
					</view>
				</view>
				<text class='iconfont icon-icon'></text>
			</view>
			<!-- 退款 -->
			<view class='serviceBox'>
				<view>
					<text class='service'>极速退款</text>
					·
					<text class='service'>全场包邮</text>
					·
					<text class='service'>7天退换</text>
					·
					<text class='service'>48小时发货</text>
				</view>
				<text class='iconfont icon-icon jaintou'></text>
			</view>
			<!-- 拼团 -->
			<view class='assemble'>
				<view class='collageTitle'>
					<text>4人在拼单，可直接参与</text>
				</view>
			  <!-- 滚动内容 -->
				<view class='collageBox'>
					<swiper autoplay='true' circular='true' class='collageBoxItem' vertical='true' display-multiple-items='1'>
					  <block v-for="(item,index) in 4" :key="index">
						<swiper-item class='scrollitem'>
							<view class='user'>
								<view class='image'>
									<image src="../../static/img/1.jpg"></image>
								</view>
								<view class='name'>名字</view>
							</view>
							<view class='settlement'>
								<view class='discrepancy'>
									<view class='peopleNum'>差3人拼成</view>
									<view class='time'>剩余     <text>23</text>:<text>23</text>:<text>34</text>结束</view>
								</view>
								<button>去拼单</button>
							</view>
						</swiper-item>
					  </block>
					</swiper>
				</view>
			</view>
			
			<view class='empty'></view>
			<!-- 评价部分 -->
			<view class='appraise'>
			  <!-- 评价标题 -->
				<view class='appraiseTitle'>
					<text>商品评价（8823）</text>
					<view>
						<text class='more1'>查看更多</text>
						<text class='iconfont icon-icon'></text>
					</view>
				</view>
				  <!-- 评价内容 -->
				<view class='appraiseNav'>
					<text class='nav'>便宜<text class='num'>(126)</text></text>
					<text class='nav'>质量好<text class='num'>(111)</text></text> 
					<text class='nav'>软硬度好<text class='num'>(52)</text></text>
					<text class='nav'>服务态度好<text class='num'>(46)</text></text>
					<text class='nav'>枕着很舒服<text class='num'>(46)</text></text>
				</view>
				  <!-- 用户评价 -->
				<view class='appraiseItem'>
					<view class='appraiseUser'>
						<view class='image'>头像</view>
						<view class='name'>名字</view>
					</view>
					<!-- 用户评价内容 -->
					<view class='appriaseContent'>
						<view class='appriaseText'>
							商品质量特别的好晚上睡觉用它-夜到天亮，睡得很踏
							实没有异味收到货，柔软度还是不错的，枕头本身的
							味道是很自然的味道。
						</view>
						<view class='appriaseImage'>
							<block v-for="(item,index) in 4" :key="index">
								<image src="../../static/img/2.png"></image>
							</block>
						</view>
					</view>
				</view>
				<!-- 商品推荐 -->
				<view class='goodsRecommend'>
				  <view class='recommendTitle'>商品推荐</view>
				  <!-- 详情内容 -->
				  <view class='goodsList'>
				    <block v-for="(item,index) in 7" :key="index">
				       <view class='goodsItem'>
				        <view class='goodsImg'>
				          <image src="../../static/img/4.png"></image>
				        </view>
				        <view class='goodsMsg'>
				          <view class='goodsTitle'>乳胶波浪枕</view>
				          <view class='goodsShop'>
				            <image src="../../static/img/logo2.gif" class='goodsIcon'></image>
				            <text class='goodsPrice'>￥<text class='num'>228</text>.00</text>
				            <button>立即购买</button>
				          </view> 
				        </view>
				      </view>
				    </block>
				  </view>
				</view>
				<!-- 商品推荐结束 -->
				<view class='person'>
				  <image src='../../static/img/person1.png'></image>
				  <image src='../../static/img/person2.png'></image>
				  <image src='../../static/img/person3.png'></image>
				  <image src='../../static/img/person4.png'></image>
				  <image src='../../static/img/person5.png'></image>
				  <image src='../../static/img/person6.png'></image>
				  <image src='../../static/img/person6.png'></image>
				  <image src='../../static/img/person6.png'></image>
				  <image src='../../static/img/person6.png'></image>
				  <image src='../../static/img/person6.png'></image>
				  <image src='../../static/img/person6.png'></image>
				  <image src='../../static/img/person7.png'></image>
				</view>
			</view>
		</scroll-view>
		<view class="footer">
			<view class="footer-list">
				<view class="footer-list-lis">
					<text class='iconfont icon-shouye'></text>
					<text>首页</text>
				</view>
				<view class="footer-list-lis">
					<text class='iconfont icon-shoucang'></text>
					<text>收藏</text>
				</view>
				<view class="footer-list-lis">
					<text class='iconfont icon-kefu'></text>
					<text>客服</text>
				</view>
		  </view>
		  <view class="footer-list-1" @tap='isShow' data-index="0">发起拼单</view>
		  <view class="footer-list-2" @tap='isShow' data-index="1">单独购买</view>
		  
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				product:{
					id:1,
					img:"../../static/img/4.png",
					title:"泰国平面波浪枕",
					material:"泰国天然乳胶原料",
					price:"228.0",
					collect:false
				}
			}
		},
		methods: {
			goBack(){
				uni.navigateBack()
			}
		},
		onLoad(options){
			console.log(options.id)
		}
	}
</script>

<style scoped>
	@import "./details.css";
</style>
