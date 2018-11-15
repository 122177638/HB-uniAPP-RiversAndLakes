<template>
	<view class="test_history_container">
		<view class="test_history_tabbar">
			<view :class="['history_tabbar_item',{'on':tabbarCurrent == 0}]" @click="switchTabbarEvent(0)">未完成</view>
			<view :class="['history_tabbar_item',{'on':tabbarCurrent == 1}]" @click="switchTabbarEvent(1)">已完成</view>
			<view :class="['history_tabbar_item',{'on':tabbarCurrent == 2}]" @click="switchTabbarEvent(2)">全部测评</view>
		</view>
		<swiper class="swiper_container" :current="tabbarCurrent" @change="changeTabbarEvent($event)">
			<swiper-item>
				<view class="swiper-item">
					<view class="null_container">
						<view class="null_toast">
							<image src="../static/images/null.png" width="100%"></image>
							<view class="null_promt">暂无测评</view>
						</view>
					</view>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">B</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">C</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				tabbarCurrent:0
			}
		},
		methods:{
			switchTabbarEvent(tabbarIndex){
				this.tabbarCurrent = tabbarIndex;
			},
			changeTabbarEvent(event){
				this.tabbarCurrent = event.detail.current;
			}
		},
	}
</script>

<style scoped lang="scss">
	.test_history_container{
		display: flex;
		flex-direction: column;
		
		.test_history_tabbar{
			display: flex;
			background-color:#FFFFFF;
			align-items: center;
			padding:0 30px;
			box-sizing: border-box;
			.history_tabbar_item{
				flex: 1;
				text-align: center;
				height:80px;
				line-height: 80px;
				position: relative;
				color: #333333;
				font-size:28px;
				transition: all .3s;
				&.on{
					color: #F3AC3C;
				}
				&.on:after{
					content: '';
					width:120px;
					height:4px;
					background-color:#F3AC3C;
					position: absolute;
					bottom:0;
					left:50%;
					margin-left:-60px;
				}
			}
		}
		.swiper_container{
			flex: 1;

			.swiper-item{

				.null_container{
					.null_toast{
						width:300px;
						height:300px;
						border-radius: 50%;
					}
				}
			}
		}
	}
</style>
