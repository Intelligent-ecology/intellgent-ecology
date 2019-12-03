<template>
	<!--pages/After/After.wxml-->
	<view class="after">
	  <!-- 评价 -->
	  <view class="evaluate">
	    <image></image>
	    <view class="content">
	      <view class="active">
	        <van-icon name="flower-o"/>
	        <text>好评</text>
	      </view>
	      <view>
	        <van-icon name="flower-o" />
	        <text>中评</text>
	      </view>
	      <view>
	        <van-icon name="flower-o" />
	        <text>差评</text>
	      </view>
	    </view>
	  </view>
	  <!-- 评价内容 -->
	  <view class="eva-content">
	    <view class="content_top">
	      <textarea placeholder="宝贝满足你的期待吗？说说你的使用心得，分享给想买他们吧"></textarea>
	      <view class="add">
	      	<image src="../../static/logo.png" mode="" class="addImg"></image>
	      </view>
		  <view class="add">
		  	<image src="../../static/logo.png" mode="" class="addImg"></image>
		  </view>
		  <view class="add">
		  	<image src="../../static/logo.png" mode="" class="addImg"></image>
		  </view>
		
		  <view class="add" @click="chooseImg" >
	        <van-icon name="photo-o"/>
	        <text>添加照片</text>
	      </view>
		 
	    </view>
	    <view class="content_bottom">
	      <view>
	        <van-checkbox
	        value=" checked "
	        checked-color="#dc3025"
	        bind:change="onChange"
	        >
	        </van-checkbox>
	        <text>匿名</text>
	      </view>
	      <text>你的评价能帮助其他小伙伴呦</text>
	    </view>
	  </view>
	  <!-- 提交评价 -->
	  <view class="refer">
	    <view class="refer_top">
	      <view class="shop">
	        <van-icon name="shop-o" class="icon"/>
	        <text>店铺评分</text>
	      </view>
	      <view class="refer_con">
	        <view class="con1">
	          <text>描述相符</text>
	          <van-rate
	            value=" value "
	            size=" 25 "
	            color="#dc3025"
	            void-color="#eee"
	            void-icon="star"
	           @change="onChange"
	            class="star"
	          />
	          <text>非常好</text>
	        </view>
	        <view class="con1">
	          <text>物流服务</text>
	          <van-rate
	            value=" value "
	            size=" 25 "
	            color="#dc3025"
	            void-color="#eee"
	            void-icon="star"
	            @change="onChange"
	            class="star"
	          />
	          <text>非常好</text>
	        </view>
	        <view class="con1">
	          <text>服务态度</text>
	          <van-rate
	            value="value"
	            size=" 25 "
	            color="#dc3025"
	            void-color="#eee"
	            void-icon="star"
	            @change="onChange"
	            class="star"
	          />
	          <text>非常好</text>
	        </view>
	      </view>
	    </view>
	  </view>
	  <van-button size="large" type="danger" @click="submit">提交评价</van-button>
	</view>
	
</template>

<script>
	export default{
		data(){
			return {
				 value:3,
				 checked: true,
				 img:''
			}
		},
		methods:{
			remove: function(e) {
				if (this.extraLine.length > 0) {
					this.extraLine.pop();
					this.text = this.extraLine.join('\n');
					this.canAdd = this.extraLine.length < 12;
					this.canRemove = this.extraLine.length > 0;
				}
			},
			onChange(event) {
				this.value = event.detail
				
			},
			chooseWxImage: function(type) {
			    var that = this;
			    wx.chooseImage({
			      sizeType: ['original', 'compressed'],
			      sourceType: [type],
			      success: function(res) {
			        console.log(res.tempFilePaths);
					if(res.tempFilePaths.length>3){
						console.log("大于3");
						
					}
			        that.img = res.tempFilePaths
			      }
			    })
			  },
			chooseImg(){
				console.log("chooseImg");
				// 弹窗内容 
				    var that = this;
				    wx.showActionSheet({
				      itemList: ['从相册中选择', '拍照'],
				      itemColor: "#a3a2a2",
				      success: function(res) {
				        if (!res.cancel) {
				          if (res.tapIndex == 0) {
				            that.chooseWxImage('album')//从相册选择
				          } else if (res.tapIndex == 1) {
				            that.chooseWxImage('camera')//使用相机
				          }
				        }
				      }
				    })
			}  
		}
	}
</script>

<style>
	@import url("./evaluation.css");
</style>
