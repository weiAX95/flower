<template>
	<view class="myPage">
		<view class="login">
			<button type="default" @click="login">login</button>
		</view>
		<view class="order">
			<view class="title">
				<view class="order_title">我的订单</view>
				<navigator url="../order/index?type=all">
				<view class="all">
					查看全部<span>></span>
				</view>
				</navigator>
			</view>
			<view class="order_state">
				<view class="obligation">
					<navigator url="../order/index?type=wait_pay">
					<image src="../../static/images/待发货.png" mode="aspectFit"></image>
					<view>待付款	</view>
					</navigator>
				</view>
				<view class="wait_send_goods">
					<navigator url="../order/index?type=send_goods">
					<image src="../../static/images/待发货.png" mode="aspectFit"></image>
					<view class="">
						待发货
					</view>
					</navigator>
				</view>
				<view class="wait_receive_goods">
					<navigator url="../order/index?type=take_goods">
					<image src="../../static/images/待收货.png" mode="aspectFit"></image>
					<view class="">
						待收货
					</view>	
					</navigator>
				</view>
				<view class="wait_evaluate">
					<navigator url="../order/index?type=comment">
					<image src="../../static/images/待评价.png" mode="aspectFit"></image>
					<view>待评价</view>	
					</navigator>
				</view>
			</view>
		</view>
		<view class="calendar select">
			<navigator url="./calendar/calendar">
				收花日历
			</navigator>
		</view>
		<view class="shipping_addr select">
			<navigator url="./address/address">
			收货地址
			</navigator>
		</view>
		<view class="person_info select">个人信息</view>
		<view class="other">
			<view class="title">其他帮助</view>
			<view class="other_container">
				<view>
					<navigator url="../other/compServer/compServer">
					<image src="../../static/images/赞.png" mode="aspectFit"></image>
					<view>企业服务</view>	
					</navigator>
					
				</view>
				<view>
					<navigator url="../other/proAdvise/proAdvise">
					<image src="../../static/images/建议.png" mode="aspectFit"></image>
					<view>产品建议</view>
					</navigator>
				</view>
				<view>
					<navigator url="../other/preSales/preSales">
					<image src="../../static/images/客服.png" mode="aspectFit"></image>
					<view>售前客服</view>
					</navigator>
				</view>
				<view>
					<navigator url="../other/coupon/coupon">
					<image src="../../static/images/建议.png" mode="aspectFit"></image>
					<view>优惠券</view>
					</navigator>	
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			login(){
				wx.login({
				  success: function (loginRes) {
					console.log(loginRes)
					uni.request({
						url:"https://xcx.zhangqihai.top/petal/api/login",
						data:{
							code:loginRes.code
						},
						success(res) {
							console.log(res)
							 uni.setStorageSync('openId', res.data.data);
						}
					})
				  }
				});
			}
		}
	}
</script>

<style lang="scss">
	.myPage{
		background: rgb(245,245,245);
		height: 100%;
		.login{
			width: 100%;
			height: 340rpx;
		}
		.order{
			margin-top: 10rpx;
			background-color: #FFFFFF;
			width: 100%;
			.title{
				display: flex;
				justify-content: space-between;
				padding: 0 15rpx;
			}
			.order_state{
				display: flex;
				justify-content:space-around;
				// .obligation .wait_send_goods .wait_receive_goods .wait_evaluate{
					margin-top: 10rpx;
					image{
						width: 100%;
						max-height: 80rpx;
					}
				// }
			}
		}
		.select{
			margin-top: 10rpx;
			height: 90rpx;
			line-height: 90rpx;
			background: #ffff;
		}
		.other{
			background-color: #FFFFFF;
			margin-top: 10rpx;
			.title{
				border-bottom: 1px solid #EEEEEE;
			}
			.other_container{
				display: flex;
				justify-content: space-around;
				margin-top: 10rpx;
				view{
					text-align: center;
				}
				image{
					width: 50%;
					max-height: 100rpx;
				}
			}
		}
	}
	
</style>
