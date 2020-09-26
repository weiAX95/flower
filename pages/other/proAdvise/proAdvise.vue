<template>
	<view>
		<view class="adv">
			<image src="../../../static/images/slideshow1.png" mode=""></image>
		</view>
		<view class="content">
			<textarea v-model="feedback" placeholder="您反馈的产品建议,我们会认真阅读并进行改进,谢谢" />
			<view class="">
				<input type="text" v-model="email" placeholder="您的邮箱"/>
				<input type="text" v-model="telephone"  placeholder="收花人手机号" />
			</view>
			<button type="default" @click="submit">提交建议</button>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				feedback:"",
				email:"",
				telephone:""
			}
		},
		methods: {
			submit(){
				console.log('123')
				let nData = {
					email:this.email,
					adviceContent:this.feedback,
					contact:this.telephone,
					openId: ''
				}
				wx.request({
					url:"https://xcx.zhangqihai.top/petal/api/addAdvice?email="+this.email+"&adviceContent="+this.feedback+"&contact="+this.telephone+"&openId="+uni.getStorageSync('openId'),
					method:"GET",
					success:function(res){
						console.log(res)
					}
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.adv{
	image{
		height: 400rpx;
	}
}

.content{
	padding: 0 30rpx;
	textarea{
		border: 1px solid #ccc;
	}
	input{
		margin-top: 30rpx;
		border: 1rpx solid #CCCCCC;
		height: 80rpx;
		line-height: 80rpx;
		width: 100%;
	}
	button{
		border-radius: 50rpx;
		background-color: #DC7004;
		margin-top: 50rpx;
	}
}
</style>
