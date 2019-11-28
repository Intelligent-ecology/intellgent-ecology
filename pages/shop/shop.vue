<template>
	<view>
		<view class="shop">
			<view class="shop-box">
				<!-- 空购物车 -->
				<view class='shop-empty' v-if="!productList.length">
					<view>
						<image src='../../static/img/elephant.png'></image>
						<text class='empty'>购物车是空的~</text>
					</view>
					<button class='btn' @tap="goAround">去逛逛</button>
				</view>
				<!-- 商品列表 -->
				<view class="shop-Valued" v-if="productList.length">
					<view class='shop-item' v-for="(item,index) in productList" :key="index" :data-index="index">
						<!-- 是否选中 -->
						<text :class="item.check ? 'iconfont icon-xuanzhong-copy' : 'iconfont icon-xuanzhongyuandian'" @tap="check" :data-index="index"></text>
						<!-- 图片 -->
						<image :src='item.img' data-id="item.id"></image>
						<!-- 详细信息 -->
						<view class='item-content'>
						  <text class='goods_name'>{{item.title}}</text>
						  <text class='short_name'>{{item.info}}</text>
						  <text class='market_price'>￥{{item.allPrice}}</text>
						</view>
						<!-- 商品数量 -->
						<view class='Products' v-if="!item.check">
						  <view class='number'>
							<!-- 商品-1 -->
							<view class='remove' @tap="cutBack" :data-index="index">-</view>
							<input @input="bindKeyInput" :placeholder="item.count" disabled="true" />
							<!-- 商品+1 -->
							<view class='add' @tap="add" :data-index="index">+</view>
						  </view>
						</view>
						<!-- 删除商品 -->
						<view class='delete' v-if="item.check" @tap="remove" :data-index="index">
						  <text class="iconfont icon-shanchu"></text>
						  <text class='text'>删除</text>
						</view>
					</view>
					<!--底部-->
					<view class='shopping'>
						<view class='shoppingBottom'>
							<view class='shoppingLeft'>
							  <!-- 全选 -->
								<text class='selectAll' :class="!allChecked ? 'iconfont icon-xuanzhongyuandian' : 'iconfont icon-xuanzhong-copy'" @tap='allCheck' data-index="index"></text>
								<text class='text'>全选</text>
							</view>
							<view class='shoppingRight'>
								<text class='TotalCost'>￥{{totalPrice}}</text>
								<button class='Settlement' @tap="settlement">去结算</button>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				productList:[],
				totalPrice:0,
				allChecked:''
			}
		},
		methods: {
			// 去逛逛
			goAround(){
				console.log(1)
			},
			// 单选
			check(e){
				// console.log(e.currentTarget.dataset.index)
				var totalPrice=0;
				var checkLen=0;
				var arr=this.productList;
				arr[e.currentTarget.dataset.index].check=!arr[e.currentTarget.dataset.index].check
				for(var i=0;i<arr.length;i++){
					if(arr[i].check){
						checkLen++
						totalPrice += arr[i].allPrice
					}
				}
				this.totalPrice=totalPrice
				if(checkLen==arr.length){
					this.allChecked=true
				}else{
					this.allChecked=false
				}
				uni.setStorage({
					key:"cart",
					data:JSON.stringify(arr)
				})
			},
			// 全选按钮
			allCheck(){
				var totalPrice=0;
				this.allChecked=!this.allChecked
				var arr=this.productList
				if(this.allChecked){
					for(var i=0;i<arr.length;i++){
						totalPrice+=arr[i].allPrice
					}
					this.totalPrice=totalPrice
				}else{
					totalPrice=0
					this.totalPrice=totalPrice
				}
				for(var i=0;i<arr.length;i++){
					arr[i].check=this.allChecked
				}
				uni.setStorage({
					key:"cart",
					data:JSON.stringify(arr)
				})
			},
			// 加号按钮
			add(e){
				var arr=this.productList;
				arr[e.currentTarget.dataset.index].count++
				arr[e.currentTarget.dataset.index].allPrice=arr[e.currentTarget.dataset.index].count*arr[e.currentTarget.dataset.index].price
				uni.setStorage({
					key:"cart",
					data:JSON.stringify(arr)
				})
			},
			// 减号按钮
			cutBack(e){
				var arr=this.productList;
				arr[e.currentTarget.dataset.index].count--
				if(arr[e.currentTarget.dataset.index].count<=1){
					arr[e.currentTarget.dataset.index].count=1
				}
				arr[e.currentTarget.dataset.index].allPrice=arr[e.currentTarget.dataset.index].count*arr[e.currentTarget.dataset.index].price
				uni.setStorage({
					key:"cart",
					data:JSON.stringify(arr)
				})
			},
			// 删除商品
			remove(e){
				wx.showModal({
					title: '提示',
					content: "确定删除吗？",
					success: res => {
						if (res.confirm) {
							console.log(res.confirm)
						wx.showToast({
							title: '删除成功',
							icon: 'success',
							duration: 2000
						})
						  //删除逻辑
						var arr=this.productList;
						arr.splice(e.currentTarget.dataset.index,1)
						var totalPrice=0;
						for(var i=0;i<this.productList.length;i++){
							if(this.productList[i].check){
								totalPrice += this.productList[i].allPrice
							}
						}
						this.totalPrice=totalPrice
							uni.setStorage({
								key:"cart",
								data:JSON.stringify(arr)
							})
						} else if (res.cancel) {
							console.log("取消")
						}
					}
				})
			},
			// 去结算按钮
			settlement(){
				wx.navigateTo({
					url:'/pages/settlement/settlement'
				})
			}
		},
		onShow(){
			var that=this
			uni.getStorage({
				key:'cart',
				success(e){
					that.productList=JSON.parse(e.data)
					var checkLen=0;
					var totalPrice=0;
					for(var i=0;i<that.productList.length;i++){
						if(that.productList[i].check){
							checkLen++
							totalPrice += that.productList[i].allPrice
						}
					}
					if(checkLen==that.productList.length){
						that.allChecked=true
					}else{
						that.allChecked=false
					}
					that.totalPrice=totalPrice
				}
			})
			
		}
	}
</script>

<style>
	@import url("./shop.css");
</style>
