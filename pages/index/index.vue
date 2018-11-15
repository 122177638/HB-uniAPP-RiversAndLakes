<template>
	<view class="content">
		<view class="banner_container">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" :circular="true">
				<swiper-item>
					<view class="swiper-item">
						<image src="https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=786563959,3210136610&fm=27&gp=0.jpg" mode=""></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=958305351,793168181&fm=27&gp=0.jpg" mode=""></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="http://img0.imgtn.bdimg.com/it/u=1690638720,3779370538&fm=27&gp=0.jpg" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
			<view class="search_dom">
				<view class="search_l">
					<image src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=4264132728,3442146706&fm=27&gp=0.jpg" class="search_logo" mode=""></image>
					<view class="search_name">壹心理测评</view>
				</view>
				<view class="search_r">
					<image src="../../static/images/search.png" class="search_icon" mode=""></image>
					<input type="text" class="search_ipt" @focus="navigatetoSearchEvent()" value="" placeholder="搜索"/>
				</view>
			</view>
		</view>
		<view class="list_wrap">
			<view class="list_top">
				<view class="list_title hot"><text>热卖</text>爆款</view>
				<view class="list_describe">不容错过的精彩测评</view>
			</view>
			<view class="list_content">
				<view class="list_item" v-for="item in hotData" :key="item.tid">
					<view class="item_top">
						<image :src="item.timg" class="item_img" mode=""></image>
						<view class="item_count">{{item.tcount}}人已测</view>
					</view>
					<view class="item_title">{{item.name}}</view>
					<view class="item_money">￥{{item.money}}</view>
				</view>
			</view>
		</view>
		<view class="list_wrap">
			<view class="list_top">
				<view class="list_title new"><text>新品</text>首发</view>
				<view class="list_describe">不容错过的精彩测评</view>
			</view>
			<view class="list_content">
				<view class="list_item" v-for="item in hotData" :key="item.tid">
					<view class="item_top">
						<image :src="item.timg" class="item_img" mode=""></image>
						<view class="item_count">{{item.tcount}}人已测</view>
					</view>
					<view class="item_title">{{item.name}}</view>
					<view class="item_money">￥{{item.money}}</view>
				</view>
			</view>
		</view>
		<view class="test_wrap">
			<view class="test_top">
				<view class="test_title">精选测评</view>
				<view class="test_more">更多</view>
			</view>
			<view class="test_content">
				<view class="category_list">
					<view class="category_item" v-for="item in categoryData" :key="item.cid">
						<view class="item_l">
							<view class="obox">
								<view class="item_title ellipsis">{{item.name}}</view>
								<view class="item_describe ellipsis">{{item.describe}}</view>
							</view>
							<view class="item_bz">
								<view><text class="Mcolor">￥{{item.money}}</text><text class="">￥{{item.oldmoney}}}</text></view>
								<view><text>{{item.count}}人已测</text></view>
							</view>
						</view>
						<view class="item_r">
							<image :src="item.headimg" class="item_img" mode="aspectFill"></image>
							<text class="itype">{{item.type}}</text>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="footer_container">
			<view class="navitoBtn" @click="navigateTocategory()">查看全部测评</view>
			<view class="footer_txt">壹心理@提供内容及技术支持</view>
		</view>
	</view>
</template>

<script>
	import coverLoading from '../../components/coverLoading.vue'
	export default {
		data: {
			hotData:[
				{name:'专业爱情测评',tid:0,money:6.6,timg:'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2249893882,1165836821&fm=27&gp=0.jpg',tcount:'32.8W',},
				{name:'专业爱情测评',tid:0,money:6.6,timg:'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2249893882,1165836821&fm=27&gp=0.jpg',tcount:'32.8W',},
				{name:'专业爱情测评',tid:0,money:6.6,timg:'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2249893882,1165836821&fm=27&gp=0.jpg',tcount:'32.8W',},
				{name:'专业爱情测评',tid:0,money:6.6,timg:'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2249893882,1165836821&fm=27&gp=0.jpg',tcount:'32.8W',},
				{name:'专业爱情测评',tid:0,money:6.6,timg:'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2249893882,1165836821&fm=27&gp=0.jpg',tcount:'32.8W',},
				{name:'专业爱情测评',tid:0,money:6.6,timg:'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2249893882,1165836821&fm=27&gp=0.jpg',tcount:'32.8W',},
			],
			categoryData:[
 				{cid:1,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
 				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
 				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
 				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
 				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
			],
		},
		components:{
			coverLoading
		},
		methods:{
			navigateTocategory(){
				uni.switchTab({
					url:'../category/category',
				})
			},
			navigatetoSearchEvent(){
				uni.navigateTo({
					url:'../search/search',
				})
			}
		},
	}
</script>

<style scoped lang="scss">
	.content {
		.banner_container{
			position: relative;
			swiper{
				height:450px;
				.swiper-item image{width: 100%;height:450px;vertical-align: middle;}
			}
			.search_dom{
				position: absolute;
				top:0;
				left:0;
				right:0;
				display: flex;
				height: 80px;
				width: 100%;
				align-items: center;
				justify-content: space-between;
				padding:0 30px;
				box-sizing:border-box;
				background-color:rgba(0,0,0,0.7);
				.search_l{
					display: flex;
					align-items:center;
					.search_logo{width:48px;height:48px;border-radius: 50%;}
					.search_name{font-size:28px;color:#ffffff;font-weight: 700;margin-left:20px;}
				}
				.search_r{
					width:200px;
					height:56px;
					display: flex;
					background-color:#ffffff;
					border-radius: 35px;
					align-items: center;
					position: relative;
					.search_ipt{
						flex: 1;
						height:100%;
						font-size:26px;
						color:#dddddd;
						padding-left: 80px;
					}
					.search_icon{
						width:32px;
						height:32px;
						position: absolute;
						left:30px;
						top:50%;
						margin-top:-16px;
					}
				}
			}
		}
		.list_wrap{
			background-color: #ffffff;
			padding:40px 0 20px 20px;
			margin-bottom: 20px;
			box-sizing: border-box;
			.list_top{
				margin-bottom:20px;
				.list_title{
					font-size:36px;
					color:#333333;
					font-weight: 700;
					&.hot text{
						color:#DB2F00;
					}
					&.new text{
						color:#F6C744;
					}
					&.hot::after{
						content: 'HOT';
						vertical-align: top;
						font-size:24px;
						color:#FFA489;
						margin-left:10px;
					}
					&.new::after{
						content: 'NEW';
						vertical-align: top;
						font-size:24px;
						color:#F3AC3C;
						margin-left:10px;
					}
				}
				.list_describe{
					font-size:20px;
					color:#989898;
				}
			}
			.list_content{
				display: flex;
				overflow: auto;
				-webkit-overflow-scrolling:touch;
				.list_item{
					display: flex;
					flex-direction: column;
					flex-shrink: 0;
					padding-right:10px;
					.item_top{
						position: relative;
						.item_img{
							width:225px;
							height:225px;
							vertical-align: middle;
						}
						.item_count{
							position: absolute;
							font-size:20px;
							color:#FFFFFF;
							bottom: 0;
							margin:10px;
						}
					}
					.item_title{
						font-size:28px;
						color:#333333;
						font-weight: 700;
						line-height: 2;
					}
					.item_money{
						font-size:24px;
						color:#f3ac3c;
					}
				}
			}
		}
		.test_wrap{
			padding:40px 0px 20px;
			box-sizing: border-box;
			background-color: #FFFFFF;
			.test_top{
				display: flex;;
				justify-content: space-between;
				align-items: center;
				padding:0 20px;
				box-sizing:border-box;
				.test_title{
					font-size:36px;
					font-weight: 700;
					color:#333333;
				}
				.test_more{
					font-size:28px;
					color:#333333;
					&:after{
						content: '';
						width:14px;
						height:14px;
						vertical-align: middle;
						display: inline-block;
						border-top:2px solid #999999;
						border-left: 2px solid #999999;
						transform: rotate(135deg);
					}
				}
			}
			.category_list{
				.category_item{
					padding:30px 0;
					margin:0 30px;
					border-bottom:2px solid #f0f0f0;
					box-sizing: border-box;
					display: flex;
					&:nth-last-child(1){border-bottom:none;}
					.item_l{
						display: flex;
						flex-direction: column;
						justify-content: space-between;
						flex: 1;
						overflow: hidden;
						width:0;
						.item_title{
							font-size:30px;
							color:#333333;
							font-weight: 700;
						}
						.item_describe{
							margin-top:10px;
							font-size:22px;
							color:#999999;
						}
						.item_bz{
							display: flex;
							justify-content: space-between;
							view:nth-child(1){
								align-items: center;
								text{
									&:nth-child(1){
										font-size:22px;
										color:#f3ac3c;
									}
									&:nth-child(2){
										margin-left:10px;
										font-size:16px;
										color:#999999;
										text-decoration: line-through;
									}
								}
							}
							view:nth-child(2){
								align-items: center;
								text{
									font-size:22px;
									color:#999999;
								}
							}
							
							
						}
					}
					.item_r{
						position: relative;
						margin-left:20px;
						.item_img{
							width:160px;
							height:160px;
							vertical-align: middle;
						}
						.itype{
							position: absolute;
							padding:5px 10px;
							display: inline-block;
							border:2px solid #87a6f2;
							border-radius: 5px;
							font-size:18px;
							color:#87a6f2;
							bottom:10px;
							right:-10px;
							background-color:#FFFFFF;
						}
					}
				}
			}
		}
		.footer_container{
			.navitoBtn{
				width:300px;
				height:60px;
				font-size:28px;
				color:#989898;
				background-color:#FFFFFF;
				line-height: 60px;
				text-align: center;
				margin:30px auto 40px;
				border:1px solid #f0f0f0;
				&:after{
					content:'';
					width:12px;
					height:12px;
					display: inline-block;
					border-top: 2px solid #989898;
					border-left: 2px solid #989898;
					transform: rotate(135deg);
					vertical-align: middle;
					margin-left:10px;
				}
			}
			.footer_txt{
				font-size:24px;
				color:#333333;
				text-align: center;
				margin-bottom: 20px;
			}
		}
	}	
</style>
