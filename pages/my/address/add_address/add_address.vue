<template>
	<view>
		<view class="detail_info">
			<view class="name item">
				<span>收件人</span>
				<input type="text" v-model="name" placeholder="小明"/>
			</view>
			<view class="contact item">
				<span>联系方式</span>
				<input type="text" v-model="telephone" placeholder="12345678900"/>
			</view>
			<view class="region item">
				<span>省市区</span>
				<input type="text" placeholder="北京市" v-model="rregion">
			</view>
			<view class="detail_address item">
				<span>详细地址</span>
				<input type="text" placeholder="奥北科技园" v-model="detail_address">
			</view>
			<view class="default item">
				<span>设为默认</span>
				
			</view>
			<view class="submit">
				<button @click="submit">保存并使用</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:"",
				telephone:"",
				region:"",
				detail_address:""
			}
		},
		methods: {
			submit(){
				let openId = uni.getStorageSync('openId');
				if(!openId){
					wx.showToast({
						title:'用户未登录',
						duration:1500
					})
					return
				}
				let data = {
					address:this.region,
					detailedAddress:this.detail_address,
					userName:this.name,
					userPhone:this.telephone,
					isShow:1,
					opendId:openId
				}
				wx.request({
					url:"https://xcx.zhangqihai.top/petal/api/address",
					method:"POST",
					data:data,
					success:function(res){
						console.log(res)
					}
				})
			}
		}
	}
</script>

<style lang="scss">
	.detail_info{
	}
	.item{
		height: 80rpx;
		line-height: 80rpx;
		input{
			display: inline-block;
			height: 80rpx;
			vertical-align:top;
			margin-left:50rpx;
			width: 60%;
		}
		border: 1px solid #EEEEEE;
	}
	.default{
		margin-top: 50rpx;
	}
	.submit{
		margin-top: 150rpx;
		button{
			width: 80%;
			background-color: #00CE47;
			margin:0 auto;
			font: #fff;
		}
	}
</style>
