<template>
	<view class="order">
		<view class="title" >
			<view class="all" :class="{'active':type=='all'}" @click="orderState('all')">全部</view>
			<view class="wait_pay" :class="{'active':type=='wait_pay'}"  @click="orderState('wait_pay')">待付款</view>
			<view class="send_goods" :class="{'active':type=='send_goods'}"  @click="orderState('send_goods')">待发货</view>
			<view class="take_goods" :class="{'active':type=='take_goods'}"  @click="orderState('take_goods')">待收货</view>
			<view class="comment" :class="{'active':type=='comment'}"  @click="orderState('comment')">评价</view>
		</view>
		<view class="main">
			<view class="main_item">
				<view class="time">
					<view>2020-06-24 14:48:04</view>
					<view class="">待收货</view>
				</view>
				<view class="info">
					<view class="img">
						<image src="../../static/images/company.png" mode="scaleToFill"></image>
					</view>
					<view class="info_main">
						<view class="name">非洲菊<span>10</span>枝</view>
						<view class="item_time">指定日期:12.1</view>
						<view>赠品:花瓶1</view>
						<view class="unit_price">￥120</view>
					</view>
				</view>
				<view class="price">
					<view class="total">共计1件</view>
					<view class="price">合计:￥120</view>
					<view class="option">
						<view>确认收货</view>
						<view>查看物流</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				type:"all"
			}
		},
		onLoad(option) {
			this.type = option.type
			console.log(this.type)
		},
		created() {
			let openId = uni.getStorageSync('openId');
			wx.request({
				"url":"https://xcx.zhangqihai.top/petal/api/orderList?openId="+openId+"&&offset=1&&pageSize=10"
				,
				"success":function(res) {
					console.log(res)
				}
			})
		},
		methods:{
			orderState(state){
				console.log(state)
			}
		}
	}
</script>

<style lang="scss">
	.order {
		.title{
			display: flex;
			height: 110rpx;
			line-height: 100rpx;
			view{
				flex: 1;
				text-align: center;
			}
		}
		.active{
			border-bottom: #07C160 1rpx solid;
		}
		.main{
			.main_item{
				padding: 10rpx;
				.time{
					display: flex;
					justify-content: space-around;
				}
				.info{
					display: flex;
					.img{
						flex: 1;
						image{
							display: inline;
						}
					}
					.info_main{
					 margin-left: 20rpx;
					 flex: 3;
					 
					}
				}
				.price{
					display: flex;
					justify-content: space-between;
					
					.option{
						display: flex;
						view{
							border-radius: 50rpx;
							padding: 5rpx;
							border: 1px solid #000;
							margin-right: 10rpx;
						}
						
					}
				}
			}
		}
	}
</style>
