<template>
	<view>
		<!-- 订单 -->
		<view class='order'>
			<!-- 设置收货地址 -->
			<view class='order-header' @tap="location">
				<view class="oldLocation">
					<van-icon class='location' name="location-o" color='#248756' />
					<text>请选择收货地址</text>
					<van-icon class="arrow" name="arrow" />
				</view>
				<view class="newLocation"></view>
			</view>
			<!-- 彩条 -->
			<view class='Colorbar'>
				<image src='../../static/img/Colorbar.png' style="width: 100%; height: 4rpx;"></image>
			</view>
			<!-- 商品详情 -->
			<view class='order-content'>
				<view class='order-item' v-for="(item,index) in productList" :key="index" :data-index="index">
					<view class='ig'>
						<image :src='item.img'></image>
					</view>
					<view class='order-item-content'>
						<text class='goods_name'>{{item.title}}</text>
						<text class='short_name'>{{item.info}}</text>
						<view class='count'>
							<text class='Pirce'>共{{item.count}}件</text>
							<text class='unitPrice'>￥{{item.allPrice}}</text>
						</view>
					</view>
				</view>
				<!-- 优惠券 -->
				<view class='Coupon'>
					<view class='Coupon-text'>
						<view class='left'>
							<text>优惠</text>
						</view>
						<view class='right'>
							<text>0张可用</text>
							<van-icon class='arrow' name="arrow" size="24rpx" />
						</view>
					</view>
				</view>
				<view class='price-box'>
					<!-- 商品总额 -->
					<view class='price'>
						<text class='text'>商品总额</text>
						<text class='TotalCost'>￥{{totalPrice}}</text>
					</view>
					<!-- 运费 -->
					<view class='Freight'>
						<text class='text'>运费</text>
						<text class='FreightPrice'>￥0</text>
					</view>
				</view>
				<!-- 留言 -->
				<view class='leaveComments'>
					<text class='text'>留言</text>
					<text class='content'>给卖家留言</text>
				</view>
				<!-- 支付 -->
				<view class='Pay'>
					<van-radio-group :value="radio">
						<van-cell-group>
							<van-cell title="微信支付" value-class="value-class" clickable data-name="1" @click="onClick">
								<van-radio name="1" />
							</van-cell>
							<van-cell title="找微信好友支付" value-class="value-class" clickable data-name="2" @click="onClick">
								<van-radio name="2" />
							</van-cell>
						</van-cell-group>
					</van-radio-group>
				</view>
			</view>
			<!-- 结算 -->
			<view class='shopping'>
				<view class='shoppingBottom'>
					<view class='left'>
						<text class='TotalCost'>应付款：</text>
						<text class='red'>￥{{totalPrice}}</text>
					</view>
					<view class='right'>
						<button class='Settlement' @tap="popup" open-type="getUserInfo" lang="zh_CN" @getuserinfo="onGotUserInfo">提交订单</button>
					</view>
				</view>
			</view>
		</view>
		<!-- 模态框开始 -->
		<van-popup :show="show" :overlay="true" @close="onClose">
			<view class='top' style="display: flex; align-items: center; height: 102rpx; border-bottom: 2rpx solid #ddd;">
				<van-icon name="cross" style="margin-left: 31rpx; color: #ddd;" @tap="onClose" />
				<image :src='avatar' style="width: 55rpx; height: 55rpx; margin-left: 19rpx;"></image>
				<text style="margin-left: 11rpx; font-size: 34rpx;">确认支付密码</text>
			</view>
			<view class='bottom'>
				<text style="display: block; text-align: center; font-size: 26rpx; margin-top: 28rpx;">{{name}}</text>
				<view style="text-align: center;padding-bottom: 33rpx;">
					<text style="font-size: 34rpx; text-align: top;">￥</text>
					<text style="font-size: 54rpx;">{{totalPrice}}</text>
				</view>
				<view class='card' style="display: flex; align-items: center;padding-bottom: 55rpx;">
					<image src='../../static/img/card.png' style="width: 50rpx; height: 50rpx; margin-left: 60rpx;"></image>
					<text style="flex: 1; font-size: 24rpx; margin-left: 30rpx;">工商银行储蓄卡 （****）</text>
					<van-icon name="arrow" style="float: right; margin-right: 14rpx; font-szie: 24rpx; color: #ddd;" />
				</view>
				<button style="width: 300rpx; height: 90rpx; background: #e01616; border-radius: 10rpx; font-size: 34rpx; color: #fff; padding-bottom: 37rpx;">确认支付</button>
			</view>
		</van-popup>
		<!-- 模态框结束 -->
		<van-dialog id="van-dialog" class="dialog" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				productList: [],
				totalPrice: '',
				show: false,
				radio: '1',
				name: '',
				avatar: ''
			}
		},
		methods: {
			// 结算弹窗
			popup() {
				this.show = true;
			},
			onClose() {
				this.show = false;
			},
			onClick(e) {
				this.radio = e.currentTarget.dataset.name
			},
			onGotUserInfo: function() {
				var that = this
				// wx登录
				wx.login({
					success(res) {
						if (res.code) {
							//发起网络请求
							var code = res.code
							// 获取微信用户信息
							wx.getUserInfo({
								success: function(res) {
									that.name = res.userInfo.nickName
									that.avatar = res.userInfo.avatarUrl
								},
								fail: res => {
									// 获取失败的去引导用户授权 
								}
							})

						} else {
							
						}
					}
				})
			},
			location(){
				wx.navigateTo({
					url:"../location/location"
				})
			}
		},
		onShow() {
			var that = this;
			uni.getStorage({
				key: 'cart',
				success(e) {
					var arr = JSON.parse(e.data)
					var list = []
					var totalPrice = 0;
					for (var i = 0; i < arr.length; i++) {
						if (arr[i].check) {
							list.push(arr[i])
							totalPrice += arr[i].allPrice
						}
					}
					that.productList = list
					that.totalPrice = totalPrice
				}
			})
		}
	}
</script>

<style>
	@import url("./settlement.css");
</style>
