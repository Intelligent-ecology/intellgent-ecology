<template>
	<view>
		<view class="location">
			<block v-for="(item,index) in userInfo" :key="index">
				<view class="content">
					<view class="location_top">
						<view class="t_left">
							<text class="name">{{item.name}}，{{item.phone}}</text>
							<text class="address">{{item.address}}{{item.detail}}</text>
						</view>
						<view class="t_right">
							<van-icon name="cross" class="cross" @tap="del" :data-index="index"/>
							<view>
								<van-icon name="success" v-if="curIndex1==index" />
								<van-button @tap="use" :data-index="index" size="mini" type="default" class="btn1" v-if="curIndex1!==index">使用</van-button>
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
							<view class="edit" @tap="edit" :data-index="index" data-method="edit">编辑</view>
							<view class="topping" @tap="toTop" :data-index='index'>{{item.top?top:top1}}</view>
						</view>
					</view>
				</view>
			</block>
			<van-button size="large" type="danger" @tap="add" class="button" data-method="add">
				<image src="../../static/img/add.png"></image>
				<text>添加新收货地址</text>
			</van-button>
			<van-popup :show="show" @close="onClose">
				<view class="popup_content">
					<view class="popup_top">
						<text>添加新收货地址</text>
						<van-icon name="cross" class="cross1" size='20px' @tap="onClose"/>
					</view>
					<view class="namePhone">
						<van-cell-group>
							<van-field :value="username" placeholder="收货姓名" :border="false" @change="onChangeU" />
						</van-cell-group>
						<van-cell-group>
							<van-field :value="phone" placeholder="电话" :border="false" @change="onChangeP" />
						</van-cell-group>
					</view>
					<view class="choose">
						<!-- <text>选择地区</text>
						 -->
						<picker class="weui-btn" mode="region" @change="changeAdd">
						    <button type="default" :plain="true"><text class="chooseAdd">{{address?address:"选择地区"}}</text> <van-icon name="arrow" class="arrow" size='16px'/></button>
						</picker>
					</view>
					<view class="detailed">
						<van-cell-group>
							<van-field :value="detail" placeholder="详细地址（如街道、小区、乡镇、村）" :border="false" @change="onChangeA" />
						</van-cell-group>
					</view>
					<van-button size="large" type="default" class="save" @tap="save">保存</van-button>
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
					address:"北京市 北京市 西城区",
					detail:"",
					top:false,
					def:true
				},{
					name:"张三",
					phone:"15332952873",
					address:"北京市 北京市 西城区",
					detail:'',
					top:false,
					def:false
				},{
					name:"李四",
					phone:"15332952873",
					address:"北京市 北京市 西城区",
					detail:'',
					top:false,
					def:false
				}],
				show:false,
				curIndex:'',
				curIndex1:0,
				text:"已设为默认",
				text1:"设为默认",
				top:"取消置顶",
				top1:"置顶",
				username:"",
				phone:"",
				address:"",
				detail:"",
				method:"",
				editIndex:''
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
				console.log(this.curIndex1)
				wx.navigateBack()
				uni.setStorage({
					key:"userInfo",
					data:JSON.stringify(this.userInfo[e.currentTarget.dataset.index])
				})
				uni.setStorage({
					key:"useIndex",
					data:this.curIndex1
				})
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
				
			},
			// 删除收货款地址
			del(e){
				// console.log(e.currentTarget.dataset.index)
				this.userInfo.splice(e.currentTarget.dataset.index,1)
			},
			// 添加收货地址
			add(e){
				this.username=""
				this.phone=""
				this.address=""
				this.detail=""
				this.method=e.currentTarget.dataset.method
				this.show=true
			},
			onClose(){
				this.show=false
			},
			// 用户名
			onChangeU(e){
				this.username=e.detail
			},
			// 电话
			onChangeP(e){
				this.phone=e.detail
			},
			// 选择地址
			changeAdd(e){
				this.address=e.detail.value[0]+" "+e.detail.value[1]+" "+e.detail.value[2]
			},
			// 详细地址
			onChangeA(e){
				this.detail=e.detail
			},
			// 编辑地址
			edit(e){
				this.method=e.currentTarget.dataset.method
				this.show=true
				this.editIndex=e.currentTarget.dataset.index
				this.username=this.userInfo[e.currentTarget.dataset.index].name
				this.phone=this.userInfo[e.currentTarget.dataset.index].phone
				this.address=this.userInfo[e.currentTarget.dataset.index].address
				this.detail=this.userInfo[e.currentTarget.dataset.index].detail
			},
			// 保存
			save(e){
				// console.log(this.method)
				if(this.method=='add'){
					let obj={
						name:this.username,
						phone:this.phone,
						address:this.address + this.detail,
						top:false,
						def:false
					}
					this.userInfo.push(obj)
					this.show=false
				}else if(this.method=="edit"){
					// console.log(this.editIndex)
					var arr = this.userInfo
					arr[this.editIndex].name=this.username
					arr[this.editIndex].phone=this.phone
					arr[this.editIndex].address=this.address
					arr[this.editIndex].detail=this.detail
					this.show=false
				}
			}
		},
		onShow(){
			var that=this
			uni.getStorage({
				key:"useIndex",
				success(e){
					that.curIndex1=e.data
					console.log(that.curIndex1)
				}
			})
		}
	}
</script>

<style>
	@import url("./location.css");
</style>
