<template>
	<view class="content">
		<view class="mytest_top">
			<view class="top_content">
				<view class="head_wrap"><image src="https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=231878074,3728399985&fm=27&gp=0.jpg" class="head_img" mode="aspectFill"></image></view>
				<view class="place">欢迎回来，Anles!</view>
			</view>
		</view>
		<view class="test_history_container">
			<view class="test_history_tabbar">
				<view :class="['history_tabbar_item',{'on':tabbarCurrent == 0}]" @click="switchTabbarEvent(0)">未完成</view>
				<view :class="['history_tabbar_item',{'on':tabbarCurrent == 1}]" @click="switchTabbarEvent(1)">已完成</view>
				<view :class="['history_tabbar_item',{'on':tabbarCurrent == 2}]" @click="switchTabbarEvent(2)">全部测评</view>
			</view>
			<view class="test_history_content">
				<!-- <view class="test_history_list">
					<view class="test_history_item">
						
					</view>
				</view> -->
				<view class="null_container">
					<view class="null_toast">
						<image src="../../static/images/null.png" class="null_img" mode=""></image>
						<view class="null_promt">暂无测评</view>
					</view>
					<view class="null_btn" @click="navigateToCategory()">查看更多精彩测评</view>
					<view class="null_txt">壹心理@提供内容及技术支持</view>
				</view>
			</view>
		</view>
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
			},
			navigateToCategory(){
				uni.switchTab({
					url:'../category/category',
				})
			}
		},
	}
</script>

<style scoped lang="scss">
	.content{
		.mytest_top{
			position: relative;
			overflow: hidden;
			&:after{
				content: '';
				width:100%;
				height:100%;
				position: absolute;
				top:0;left:0;
				background:url('https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=231878074,3728399985&fm=27&gp=0.jpg') no-repeat;
				background-size:cover;
				filter: blur(40px);
			}
			.top_content{
				position: relative;
				z-index: 1;
				display: flex;
				align-items: center;
				height:200px;
				width:100%;
				padding:0 30px;
				box-sizing: border-box;
				.head_wrap{
					.head_img{
						width:100px;
						height:100px;
						border-radius: 50%;
						vertical-align: middle;
						border:2px solid #FFFFFF;
					}
				}
				.place{
					font-size:30px;
					color:#FFFFFF;
					margin-left:30px;
					text-shadow: 0 0 0 #999999;
				}
			}
		}
		.test_history_container{
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
						color: #F6C744;
					}
					&.on:after{
						content: '';
						width:120px;
						height:4px;
						background-color:#F6C744;
						position: absolute;
						bottom:0;
						left:50%;
						margin-left:-60px;
					}
				}
			}
			.test_history_content{
				.null_container{
					.null_toast{
						width:400px;
						height:400px;
						padding-top:50px;
						box-sizing: border-box;
						background-color:#FFFFFF;
						border-radius: 50%;
						display: flex;
						justify-content: center;
						align-items: center;
						flex-direction: column;
						margin:50px auto;
						.null_img{
							width:286px;
							height:180px;
						}
						.null_promt{
							font-size:30px;
							color:#333333;
							margin-top: 30px;
						}
					}
					.null_btn{
						width:350px;
						height:80px;
						line-height: 80px;
						font-size:30px;
						color:#333333;
						text-align: center;
						background-color:#F6C744;
						border-radius: 10px;
						margin:0 auto 20px;
					}
					.null_txt{
						font-size:28px;
						text-align: center;
						margin-bottom: 20px;
					}
				}
			}
		}
	}
</style>
