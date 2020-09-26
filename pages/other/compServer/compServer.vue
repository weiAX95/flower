<template>
	<view>
		<view class="adv">
			<image src="../../../static/images/slideshow1.png" mode="aspectFill"></image>
		</view>
		<view class="main">
			<view class="need">
				<p>简述您的需求</p>
				<textarea v-model="need" placeholder="在此输入您的需求" maxlength="200" />
			</view>
			<view class="requier_info">
				<view class="name item">
					<span>*</span>
					<label for="name">姓名</label>
					<input type="text" id='name' requier_info v-model="name">
				</view>
				<view class="telephone item">
					<span>*</span>
					<label for="telephone">手机号码</label>
					<input type="text" id='telephone' v-model="telephone">
				</view>
				<view class="email item">
					<span>*</span>
					<label for="email">电子邮箱</label>
					<input type="text" id='email' v-model="email">
				</view>
				<view class="city item">
					<span>*</span>
					<label for="city">城市</label>
					<input type="text" id='city' v-model="city">
				</view>
				<view class="company item">
					<span>*</span>
					<label for="company">企业名称</label>
					<input type="text" id='company' v-model="company">
				</view>
				<view class="guild item">
					<span>*</span>
					<label for="guild">所属行业</label>
					<input type="text" id='guild' v-model="guild">
				</view>
				<view class="cooperation_type item">
					<span>*</span>
					<label for="cooperation_type">合作类型</label>
					<input type="text" id='cooperation_type' v-model="cooperation_type">
				</view>
				<view class="button">
					<button type="primary" @click="submit">提交</button>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				need:"",
				name:"",
				telephone:"",
				email:"",
				city:"",
				company:"",
				guild:"",
				cooperation_type:""
			}
		},
		methods: {
			submit(){
				let info = {
					name:this.name,
					telephone:this.telephone,
					email:this.email,
					city:this.city,
					company:this.company,
					guild:this.guild,
					cooperation_type:this.cooperation_type
				}
				let openId = uni.getStorageSync('openId')
				console.log(openId)
				if(!openId) return;	
				wx.request({
						url:"https://xcx.zhangqihai.top/petal/api/addEnterprise?enterpriseName="+ info.name +"&enterpriseContact="+ info.telephone +"&enterpriseEmail="+info.email+"&city="+info.city+"&userName="+info.company+"&industry="+info.guild+"&type="+info.cooperation_type+"&openId="+openId +"&remark=123123",
						method:"GET",
						success: (res) => {
							console.log(res)
						}
				})
			}
		}
	}
</script>

<style lang='scss' scoped>
.adv{
	height: 400rpx;
	image{
		height: 400rpx;
	}
}
.main{
	padding: 0 30rpx;
	margin-top: 20rpx;
	.need{
		textarea{
			max-height: 120rpx;
			overflow: auto;
		}
	}
	.requier_info{
		.item{
			height: 100rpx;
			line-height: 100rpx;
			border-bottom: 1px solid #CCCCCC;
		}
		label{
			margin-right: 20rpx;
			 vertical-align: middle;
		}
		input{
			display: inline-block;
			 vertical-align: middle;
		}
		.button{
			margin-top: 100rpx;
		}
	}
}

</style>
