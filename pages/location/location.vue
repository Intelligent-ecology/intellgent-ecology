<template>
	<view>
		<view class="location">
			<block v-for="(item,index) in userInfo" :key="index">
				<view class="content">
					<view class="location_top">
						<view class="t_left">
							<text class="name">{{item.name}}，{{item.phone}}</text>
							<text class="address">{{item.address}}</text>
						</view>
						<view class="t_right">
							<van-icon name="cross" class="cross" />
							<view>
								<van-icon name="success" v-if="curIndex1==index" />
								<van-button @tap="use" :data-index="index" size="mini" type="default" class="btn1" wx:else>使用</van-button>
							</view>
						</view>
					</view>
					<view class="location_bottom">
						<view class="b_left">
							<icon :class="item.def ? 'iconfont icon-xuanzhong-copy':'iconfont icon-xuanzhongyuandian'" @tap="ctrl"
							 :data-index="index"></icon>
							<text :class="item.def ?'red':''">{{item.def ?text:text1}}</text>
						</view>
						<view class="b_right">
							<view class="edit">编辑</view>
							<view class="topping" @tap="toTop" :data-index='index'>{{item.top?top:top1}}</view>
						</view>
					</view>
				</view>
			</block>
			<van-button size="large" type="danger" @tap="add" class="button">
				<image src="../../static/img/add.png"></image>
				<text>添加新收货地址</text>
			</van-button>
			<van-popup :show="show" @close="onClose">
				<view class="popup_content">
					<view class="popup_top">
						<text>添加新收货地址</text>
						<van-icon name="cross" class="cross1" size='20px' />
					</view>
					<view class="namePhone">
						<van-cell-group>
							<van-field value="{{ value }}" placeholder="收货姓名" border="{{ false }}" @change="onChange" />
						</van-cell-group>
						<van-cell-group>
							<van-field value="{{ value }}" placeholder="电话" border="{{ false }}" @change="onChange" />
						</van-cell-group>
					</view>
					<view class="choose">
						<text>选择地区</text>
						<van-icon name="arrow" class="arrow" size='16px' />
					</view>
					<view class="detailed">
						<van-cell-group>
							<van-field value="{{ value }}" placeholder="详细地址（如街道、小区、乡镇、村）" border="{{ false }}" @change="onChange" />
						</van-cell-group>
					</view>
					<van-button size="large" type="default" class="save">保存</van-button>
				</view>
			</van-popup>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo:[{
					name:"巫宇",
					phone:"15332952873",
					address:"北京市 北京市 西城区 南菜园街88号",
					top:false,
					def:false
				},{
					name:"张三",
					phone:"15332952873",
					address:"北京市 北京市 西城区 南菜园街88号",
					top:false,
					def:false
				},{
					name:"李四",
					phone:"15332952873",
					address:"北京市 北京市 西城区 南菜园街88号",
					top:false,
					def:false
				}],
				show:false,
				curIndex:0,
				curIndex1:0,
				text:"已设为默认",
				text1:"设为默认",
				top:"取消置顶",
				top1:"置顶"
			}
		},
		methods: {
			// 默认
			ctrl(e){
				for(var i=0;i<this.userInfo.length;i++){
					if(i==e.currentTarget.dataset.index){
						this.userInfo[i].def=true
					}else{
						this.userInfo[i].def=false
					}
				}
				
			},
			// 使用
			use(e){
				this.curIndex1=e.currentTarget.dataset.index
			},
			// 置顶
			toTop(e){
				var arr=this.userInfo
				for(var i=0;i<this.userInfo.length;i++){
					if(i==e.currentTarget.dataset.index){
						this.userInfo[i].top=!this.userInfo[i].top
						var obj=arr[i]
						if(this.userInfo[i].top){
							arr.splice(e.currentTarget.dataset.index,1)
							arr.unshift(obj)
						}else{
							arr.splice(e.currentTarget.dataset.index,1)
							arr.push(obj)
						}
					}
				}
				
			}
		}
	}
</script>

<style>
	@import url("./location.css");
</style>
