<template>
	<view>
		<view class="slideShow">
			<image src="../../../static/images/slideshow1.png" mode="aspectFill"></image>
		</view>
		 <uni-calendar 
		    :insert="true"
		    :lunar="true" 
		    @change="change"
			:selected='select'
		     />
		<view class="cale_info">
			<view class="info_item">
				<div class="item_header">
					
					<div class='info_data'>
						<view class="month">2020/07</view>
					<div class='week'>星期一</div>
					</div>
					<div class="number">配送数量 1</div>
				</div>
				<div class="item_main">
					<view class="goods_img">
					<image src="../../../static/logo.png" mode=""></image>
					</view>
					<view>
						<view><view>普通混合型</view><view>代配送</view></view>
						<view class="addr">北京 .............................</view>
					</view>
				</div>
			</view>
		</view>
	</view>
</template>

<script>
	import uniCalendar from '../../../components/uni-calendar/uni-calendar.vue'
	export default {
		data() {
			return {
				select:[
					{date: '2020-07-28', info: '签到', data: { custom: '自定义信息', name: '自定义消息头'}}
				]
			};
		},
		methods:{
			 change(e) {
			            console.log(e);
			       }
		},
		components: {
			uniCalendar
		},
	}
</script>

<style lang="scss">
	page{
		background-color: #CCCCCC;
	}
	.slideShow{
		height: 300rpx;
		image{
		height: 300rpx;
		}
	}
	.cale_info{
		margin-top: 20rpx;
		.info_item{
			background: #fff;
			padding: 0 20rpx;
			.item_header{
				display: flex;
				justify-content: space-between;
				.info_data{
					display: flex;
					justify-content: space-between;
					.week{
						margin-left: 20rpx;
					}
				}
			}
			.item_main{
				border: 1px sold #EEEEEE;
				display: flex;
				.goods_img{
					image{
						width: 100rpx;
						height: 100rpx;
					}
					
				}
			}
		}
	}
</style>
