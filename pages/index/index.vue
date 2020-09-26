<template>
	<view class="content">
		<view>
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" :circular="true">
			<swiper-item v-for="(item,index) in swiperList" :key="index">
				<view class="swiper-item">
					<image :src="item" mode="scaleToFill"></image>
				</view>
			</swiper-item>
		</swiper>
		</view>
		<view class="month_service">
			<view class="month_left">
				<image src="../../static/images/flatRate.png" mode=""></image>
			</view>
			<view class="month_right">
				<view class="top">
					<image src="../../static/images/company.png" mode=""></image>
				</view>
				<view class="bottom">
					<image src="../../static/images/rim.png" mode=""></image>
				</view>
			</view>
		</view>
	
		<!-- 热卖 -->
		<view class="hot_sell">
			<view class="title">
				<view>
					<text>热卖专区</text>
				</view>
				<view>
					<text>HOT SALE</text>
				</view>
			</view>
			<view class="sell_container">
				<view class="sell_item">
					<image src="../../static/images/slideshow3.png" mode=""></image>
					<view class="name">
						
					</view>
				</view>
				<view class="sell_item">
					<image src="../../static/images/slideshow3.png" mode=""></image>
					<view class="name">
						
					</view>
				</view><view class="sell_item">
					<image src="../../static/images/slideshow3.png" mode=""></image>
					<view class="name">
						
					</view>
				</view><view class="sell_item">
					<image src="../../static/images/slideshow3.png" mode=""></image>
					<view class="name">
						
					</view>
				</view>
				<view class="sell_item">
					<image src="../../static/images/slideshow1.png" mode=""></image>
				</view>
				<view class="sell_item">
					<image src="../../static/images/slideshow1.png" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swiperList:['/static/images/slideshow1.png','/static/images/slideshow2.png','/static/images/slideshow3.png']
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.swiper-item{
		height: 300rpx;
		image{
			width: 100%;
			height: 100%;
		}
	}
	.content .month_service{
		display: flex;
		height: 300rpx;
		overflow: auto;
		.month_left{
			flex: 3;
			image{
				width: 100%;
				height: 100%;
			}
		}
		.month_right{
			flex:2;
			display: flex;
			flex-direction: column;
			view{
			flex: 1;
			image{
				width: 100%;
				height: 100%;
			}
			}
		}
		
	}
	.hot_sell{
		box-sizing: border-box;
		padding: 0 30rpx;
		.sell_container{
			margin: 0 10rpx;
			display: flex;
			flex-wrap: wrap;
			.sell_item{
				flex: 0 1 300rpx;
				height: 300rpx;
				margin: 15rpx;
				image{
					width: 100%;
					height: 100%	;
				}
			}
		}
		
	}
	
</style>
