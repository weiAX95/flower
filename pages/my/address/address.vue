<template>
	<view class="address">
		<view class='consignee'>
			<view class="name">
				收货人:
			</view>
			<view class="telephone">
				{{telephone}}
			</view>
		</view>
		<view class='detail_info'>
			这是详细地址
		</view>
		<view class="operation">
			<view class="default_address">
				默认地址
			</view>
			<view class="option">
				<view class="edit">编辑</view>
				<view class="delete">删除</view>
			</view>
		</view>
		<view class="add">
			<navigator url="./add_address/add_address">
			<button type="default">添加新地址</button>
			</navigator>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				telephone:'12345678'
			};
		}
	}
</script>

<style lang="scss">
	.address{
		padding: 20rpx;
		.consignee{
			display: flex;
			justify-content: space-between;
			height: 100rpx;
			line-height: 100rpx;
		}
		.detail_info{
			height: 150rpx;
		}
		.operation{
			display: flex;
			justify-content: space-between;
			border-top: 1px solid #CCCCCC;
			.option{
				display: flex;
				.delete{
					margin-left: 30rpx;
				}
			}
		}
		.add{
			margin: 50rpx;
			button{
			background-color: #00CE47;
			font: #fff;
			}
		}
	}
</style>
