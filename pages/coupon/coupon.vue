<template>
	<view class="coupon">
		<view class="offer">
			<!-- 可用红包 -->
			<view class='packetTop'>
				<view class="line"></view>
				<view class="redPacket">可用红包<text>4</text>个</view>
			</view>
			<!-- 可用红包结束 -->
			<!-- 内容开始 -->
			<view class="content">
				<view class="coupon-btn">
					<view class="left">
						<view class="top">
							<text class="price">￥</text><text class="priceNum">5</text>
							<text class="shopping-voucher">购物券</text>
						</view>
						<view class="bottom">
							收藏+关注
						</view>
					</view>
					<view class="right">
						<view @click="employ">立即使用</view>
					</view>
				</view>
				<view class="coupon-btn">
					<view class="left">
						<view class="top1">
							<view class="moneyOff">满199立减</view>
						</view>
						<view class="bottom1">
							<text class="price">￥</text><text class="priceNum">20</text>
							<text class="shopping-voucher">购物券</text>
						</view>
					</view>
					<view class="right">
						<view @click="employ">立即使用</view>
					</view>
				</view>
				
			</view>
			<!-- 内容结束 -->
			<view class="footer">
				<view class="footer-text">
					没有更多了
				</view>
				<image src="../../static/img/empty.png"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		methods: {
			employ() {
				console.log(11);
			}
		}
	}
</script>

<style>
	@import "./coupon.css"
</style>
