<template>
	<view class='browsing'>
		<!-- 有数据开始 -->
		<view class="" v-if=showVal>
			<view class='content'>
				<!-- 内容 -->
				<view class='list'>
					<!-- 图片 -->
					<image src='../../static/img/3.png' />
					<!-- 描述 -->
					<view class='text'>
						<!-- 标题 -->
						<text class='title'>泰国天然乳胶枕头一对单人家用橡胶护颈椎护颈记忆枕芯双人枕套护颈椎护颈</text>
						<!-- 价格 -->
						<text class='price'>￥<text class='nPrice'>299.00</text></text>
						<!-- 购买人数 -->
						<view class='already'>
							<text>已有5673人购买</text>
							<text>上海</text>
						</view>
					</view>
				</view>
			</view>
			<!-- 底部 -->
			<view class='footer'>
				<text>没有更多了</text>
				<image src='../../static/img/empty.png'></image>
			</view>
		</view>
		<!-- 有数据结束 -->
		<!-- 没有数据开始 -->
		<view class="none" v-else>
			<view class="text">
				暂无商品收藏
			</view>
			<image src="../../static/img/empty.png" mode=""></image>
		</view>
		<!-- 没有数据结束 -->
	</view>

</template>

<script>
	export default{
		data(){
			return {
				showVal:true
			}
		}
	}
</script>

<style>
	@import "./browse.css";
</style>
