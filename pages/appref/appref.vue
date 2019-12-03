<template>
	<view>
		<view class='applyRefund'>
			<!-- 物品  -->
			<view class='commodity'>
				<image :src='product.img' alt='...'></image>
				<view class='commodity-text'>
					<view class='text-top'>
						<text>{{product.title}}</text>
						<text>￥{{product.price}}</text>
					</view>
					<view class='text-bottom'>
						<text>{{product.material}}</text>
						<text>x{{product.num}}</text>
					</view>
				</view>
			</view>
			<!-- 退款原因 -->
			<view class='cause'>
				<text>退款原因</text>
				<text class='chooseReason' @tap='choose'>{{cause1?cause1:"请选择 >"}}</text>
			</view>
			<!-- 退款价格  -->
			<view class='refund-price'>
				<view class='price'>
					<text class='hint'>退款金额:</text>
					<text class='money'>￥{{product.price*product.num}}</text>
				</view>
				<view class='explain'>
					<text class='hint'>退款说明:</text>
					<input type='text' placeholder="选填" />
				</view>
			</view>
			<!--上传凭证  -->
			<view class='upload'>
				<view class='upload-hint'>上传凭证:</view>
				<view class='imgs' @tap="voucher"  v-if="tempFilePaths.length==0">
					<image src="../../static/img/photo.png" class="photo"></image>
					<text class='add-photo'>添加图片</text>
				</view>
				<view class="images"  v-if="tempFilePaths.length!==0">
					<image v-for="(item,index) in tempFilePaths" :src="item" :key="index" class="img"></image>
				</view>
			</view>
			<!--提交申请  -->
			<button class='btn'>提交申请</button>
			<van-popup :show="show" position="bottom" :overlay="true">
				<view class='cause-select'>
					<view class='cause-title'>退款原因</view>
					<view class='mores'>
						<radio-group class="radio-group">
							<label class="radio" @tap="radioChange" v-for="(item,index) in cause" :key="index" :data-index="index">
								<span>{{item.value}}</span>
								<radio :value="item.name" :checked="item.checked" />
							</label>
						</radio-group>
					</view>
				</view>
				<view class='close' @tap='onClose'>关闭</view>
			</van-popup>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show: false,
				product: {},
				cause: [{
						'value': '错拍/多拍/不想要',
						'checked': true
					},
					{
						'value': '协商一致退款',
						'checked': false
					},
					{
						'value': '未按约定时间发货',
						'checked': false
					},
					{
						'value': '其他',
						'checked': false
					}
				],
				cause1: 0,
				tempFilePaths:[]
			}
		},
		methods: {
			choose() {
				this.show = true
			},
			onClose() {
				this.show = false
			},
			// 原因选择
			radioChange(e) {
				this.cause1 = this.cause[e.currentTarget.dataset.index].value
				// console.log(this.cause1)
			},
			voucher() {
				var that=this
				wx.chooseImage({
					count: 3,
					sizeType: ['original', 'compressed'],
					sourceType: ['album', 'camera'],
					success(res) {
						// tempFilePath可以作为img标签的src属性显示图片
						that.tempFilePaths = res.tempFilePaths
						console.log(that.tempFilePaths)
					}
				})
			}
		},
		onLoad(options) {
			this.product = JSON.parse(options.item)
		}
	}
</script>

<style>
	@import url("./appref.css");
</style>
