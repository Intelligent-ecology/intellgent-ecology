<template>
	<view class="content">
		<scroll-view scroll-y="true" style="height:92vh">
			<!-- 商品图片 -->
			<view class="topImg">
				<swiper circular="true"  interval="500" duration="1500" @change="changeImg">
					<swiper-item v-for="(item,index) in banner" :key="index">
						<image :src="item" mode=""></image>
					</swiper-item>
				</swiper>
				<text class="index">
					{{bannerIndex}}/{{banner.length}}
				</text>
				<view class='arrow' @tap='goBack'>
					<text class='iconfont icon-fanhui'></text>
				</view>
				<view class='cart'>
					<text class='iconfont icon-gouwuche'></text>
				</view>
				<!-- <view class='more'>
					<text class='iconfont icon-sangedian'></text>
				</view> -->
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
										<view class='time'>剩余 <text>23</text>:<text>23</text>:<text>34</text>结束</view>
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
				<view class="footer-list-lis" @tap="goIndex">
					<text class='iconfont icon-shouye'></text>
					<text>首页</text>
				</view>
				<view class="footer-list-lis" @tap="collect" :data-id="id">
					<text :class="collection?'iconfont icon-shoucang1':'iconfont icon-shoucang'"></text>
					<text>收藏</text>
				</view>
				<view class="footer-list-lis">
					<button open-type="contact" plain="true"></button>
					<text class='iconfont icon-kefu'></text>
					<text>客服</text>
				</view>
			</view>
			<view class="footer-list-1" @tap='isShow' data-index="0">发起拼单</view>
			<view class="footer-list-2" @tap='isShow' data-index="1">单独购买</view>
			<van-popup :show="show" position="bottom" :overlay="true" @close="onClose">
				<view class="footer-shop">
					<view class="contents">
						<image src="../../static/img/2.jpg"></image>
						<view class="footer-shop-right">
							<text>￥118-159</text>
							<text>库存2343件</text>
							<text>请选择 尺码</text>
							<text class="iconfont icon-guanbi1" @tap='onClose'></text>
						</view>
					</view>
					<scroll-view scroll-y="true" class="scrollBox">
						<view class="size">尺码</view>
						<view class='list'>
							<text v-for="(item,index) in size" :key="index" :data-size="index" :class="{'active':curSize===index}" @tap="selectSize">{{item}}</text>
						</view>
						<view class='size'>颜色</view>
						<view class="list">
							<text v-for="(item,index) in color" :key="index" :data-color="index" :class="{'active':curColor===index}" @tap="selectColor">{{item}}</text>
						</view>
						<view class="number">
							<text>数量</text>
							<view class='number1'>

								<view class='remove' @tap="cutBack">-</view>
								<input :value="count" :disabled="true" />
								<view class='add' @tap="add">+</view>
							</view>
						</view>
					</scroll-view>
					<view class="btn" @tap="goShop">确定</view>
				</view>
			</van-popup>
			<van-toast id="van-toast" />
		</view>
	</view>
</template>

<script>
	import Toast from 'wxcomponents/vant/dist/toast/toast';
	export default {
		data() {
			return {
				banner: ['../../static/img/2.jpg', '../../static/img/2.jpg', '../../static/img/2.jpg'],
				id: '',
				collection: '',
				product: '',
				detail: [],
				show: false,
				size: ["60*40cm", "58*36cm"],
				color: ["白色", "红色"],
				bannerIndex:1,
				curSize: null,
				curColor: null,
				curIndex: null,
				dataList: [],
				count: 1,
				Operations: '',
				newsList: [],
				productList: []
			}
		},
		methods: {
			goBack() {
				uni.navigateBack()
			},
			changeImg(e){
				this.bannerIndex=e.detail.current+1
			},
			isShow(e) {
				this.show = true
				// console.log(e.currentTarget.dataset.index)
				this.Operations = e.currentTarget.dataset.index
			},
			onClose() {
				this.show = false
			},
			// 尺码选择
			selectSize(e) {
				this.curSize = e.currentTarget.dataset.size
			},
			// 颜色选择
			selectColor(e) {
				this.curColor = e.currentTarget.dataset.color
			},
			// 加号按钮
			add() {
				this.count++
			},
			// 减号按钮
			cutBack() {
				this.count--
				if (this.count <= 1) {
					this.count = 1
				}
			},
			// 跳转首页
			goIndex() {
				uni.switchTab({
					url: '/pages/index/index'
				})
			},
			// 商品收藏  解决收藏问题
			collect(e) {
				this.collection = !this.collection
				var arr = this.newsList
				for (var i = 0; i < arr.length; i++) {
					if (arr[i].id == e.currentTarget.dataset.id) {
						arr[i].collect = this.collection
						uni.setStorage({
							key: 'collectList',
							data: JSON.stringify(arr)
						})
					}
				}
			},
			// 确定按钮(加入购物车功能)
			goShop() {
				if (this.size[this.curSize] && this.color[this.curColor]) {


					if (this.Operations == 0) {
						// 点击了发起拼单
						var product = {
							img: this.product.img,
							title: this.product.title,
							info: this.product.material,
							count: this.count,
							price: this.product.price,
							allPrice: this.count * this.product.price,
							size: this.size[this.curSize],
							color: this.color[this.curColor],
							check: true
						}
						uni.setStorage({
							key: 'groupcart',
							data: JSON.stringify([product])
						})
						wx.navigateTo({
							url: '/pages/settlement/settlement?operations=0'
						})
					} else {
						// 单独购买
						var product = {
							img: this.product.img,
							title: this.product.title,
							info: this.product.material,
							count: this.count,
							price: this.product.price,
							allPrice: this.count * this.product.price,
							size: this.size[this.curSize],
							color: this.color[this.curColor],
							check: false
						}
						this.productList.push(product)
						uni.setStorage({
							key: 'cart',
							data: JSON.stringify(this.productList)
						})
						wx.switchTab({
							url: '/pages/shop/shop'
						})
					}
				} else {
					Toast('请选择商品类型');
				}
			},
		},
		onLoad(options) {
			var _this = this
			this.product = JSON.parse(options.item)
			this.id = this.product.id
			// uni.getStorage({
			// 	key:'cart',
			// 	success(e) {
			// 		_this.productList=JSON.parse(e.detail)
			// 	}
			// })
		},
		onShow() {
			var that = this
			// 判断是否已收藏该id下的商品
			uni.getStorage({
				key: 'collectList',
				success(e) {
					// console.log(JSON.parse(e.data))
					that.newsList = JSON.parse(e.data) || []
					// console.log(that.newsList)
					for (var i = 0; i < that.newsList.length; i++) {
						if (that.newsList[i].id == that.id) {
							that.collection = that.newsList[i].collect
						}
					}
				}
			})
			uni.getStorage({
				key: 'cart',
				success(e) {
					that.productList = JSON.parse(e.data) || []
				}
			})
		}
	}
</script>

<style scoped>
	@import "./details.css";
</style>
