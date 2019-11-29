<template>
	<view>
		<view class='order'>
			<!-- 订单内容 -->
			<view class='order-list'>
				<!--商品 -->
				<view class='lists' v-for="(item,index) in allOrder" :key="index">
					<!-- 订单编号 -->
					<view class='orderNumber' v-if="item.status=='finish'">
						<text>订单编号:{{item.orderNumber}}</text>
						<text class='over'>交易完成</text>
					</view>
					<view class='list-top'>
						<image :src='item.img'></image>
						<view class='listReight'>
							<view class='txt'>
								<view class='theme'>{{item.title}}</view>
								<view class='theme-bottom'>{{item.material}}</view>
							</view>
							<view class='pri'>
								<view class='pris'>￥{{item.price*item.num}}</view>
								<view class='nums'>X{{item.num}}</view>
							</view>
						</view>
					</view>
					<!-- 价格汇总 -->
					<view class='allPrice'>
						共计<text>1</text>件商品 合计:<text>￥228.0</text>(含运费￥0.00)
					</view>
					<!-- 评价 -->
					<view class='delAndre' v-if="item.status=='finish'">
						<text class='refund' @tap='gotoRefund' :data-index="index">申请退款</text>
						<text class='del' @tap="del" :data-index="index">删除</text>
						<text class='recommend'>评价</text>
					</view>
					<view class='delAndre' v-if="item.status=='unfinish'">
						<text class='removeList'>取消订单</text>
						<text class='goPay'>去支付</text>
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
				allOrder:[{
					status:"finish",
					orderNumber:'7564893587941546',
					img:'../../static/img/5.png',
					title:"泰国天然乳胶枕头一对",
					material:"天然乳胶",
					price:228,
					num:1,
				},{
					status:"unfinish",
					orderNumber:'7564893587941546',
					img:'../../static/img/5.png',
					title:"泰国天然乳胶枕头一对",
					material:"天然乳胶",
					price:228,
					num:1,
				},{
					status:"unfinish",
					orderNumber:'7564893587941546',
					img:'../../static/img/5.png',
					title:"泰国天然乳胶枕头一对",
					material:"天然乳胶",
					price:228,
					num:2,
				}]
			}
		},
		methods: {
			// 删除订单
			del(e){
				var that=this
				wx.showModal({
					title:'确定删除该订单吗？',
					success (res) {
					    if (res.confirm) {
							that.allOrder.splice(e.currentTarget.dataset.index,1)
					    } else if (res.cancel) {
							console.log('用户点击取消')
					    }
					 }
				})
			},
			// 申请退款
			gotoRefund(e){
				var obj=this.allOrder[e.currentTarget.dataset.index]
				wx.navigateTo({
					url:"/pages/appref/appref?item="+JSON.stringify(obj)
				})
			}
		}
	}
</script>

<style>
	@import url("./myOrder.css");
</style>
