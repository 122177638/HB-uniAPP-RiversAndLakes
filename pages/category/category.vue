<template>
	<view class="content">
		<view class="search_dom">
			<view class="search_l">
				<image src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=4264132728,3442146706&fm=27&gp=0.jpg" class="search_logo" mode=""></image>
				<view class="search_name">壹心理测评</view>
			</view>
			<view class="search_r">
				<image src="../../static/images/search.png" class="search_icon" mode=""></image>
				<input type="text" class="search_ipt" value="" placeholder="搜索"/>
			</view>
		</view>
		<view class="category_container">
			<view class="category">
				<view 
				:class="['category_type',onCategoryType == index?'on':'']" 
				v-for="(item,index) in categoryType" 
				:key="index"
				@click="switchTypeEvent(index)">
					{{item}}
				</view>
			</view>
			<view class="category_content">
				<view class="category_sort_wrap">
					<view>排序</view>
					<view 
					:class="['sort_type',{'on':sortTypeShow}]" 
					@click="switchSortTypeEvent()">
						{{sortType[selectSortType]}}
					</view>
					<view :class="['sort_type_wrap',{'on':sortTypeShow}]">
						<view class="sort_type_item" 
						v-for="(item,index) in sortType" 
						@click="selectSortTypeEvent(index)"
						:key="index"
						>
							<view :class="selectSortType == index?'on':''">{{item}}</view>
						</view>
					</view>
				</view>
				<scroll-view class="category_list_wrap" scroll-y scroll-with-animation enable-back-to-top 
				@scrolltolower="PulluploadEvent()" v-if="categoryData != ''">
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
					<view class="loadpromt" v-if="loadpromtShow">
						<view class="loadcover">
							<view class="cloud"></view>
						</view>
						<view>{{loadpromt}}</view> 
					</view>
				</scroll-view>
				<loading v-else></loading>
			</view>
		</view>
	</view>
</template>

<script>
	import loading from '../../components/loading.vue'
	export default {
		data: {
			sortTypeShow:false,
			selectSortType:0,
			sortType:['按热度','按时间','按价格'],
			onCategoryType:0,
			categoryType:['全部','性格','情感','职场','健康','人际','亲子','能力','趣味H5'],
			categoryData:[
				{cid:1,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
				{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
			],
			loadpromtShow:false,
			loadpromt:'加载中...',
			isthrottle:false,
		},
		components:{
			loading
		},
		mounted:function(){
			console.log(this.$store)
		},
		methods:{ 
			switchTypeEvent(index){
				// 防止重复触发 
				if(this.onCategoryType != index){
					this.onCategoryType = index;
					this.categoryData = []; //清空数据，显示loading
					setTimeout(()=>{this.categoryData.push(
						{cid:2,name:'自尊类型测试',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
					)}, 1000);	
				}
			},
			switchSortTypeEvent(){
				this.sortTypeShow = !this.sortTypeShow;
			},
			selectSortTypeEvent(index){
				this.selectSortType = index;
				this.sortTypeShow = !this.sortTypeShow;
			},
			PulluploadEvent(){
				this.loadpromtShow = true;
				if(!this.isthrottle){
					this.isthrottle = true;
					setTimeout(() => {
						this.isthrottle = false;
						this.loadpromtShow = false;
					}, 200);
				}else{
					return
				}
			},
		}
	}
</script>

<style scoped lang="scss">
	.content{
		display: flex;
		height: 100vh;
		flex-direction: column;
		.search_dom{
			display: flex;
			height: 0.8rem;
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
		.category_container{
			display: flex;
			flex: 1;
			.category{
				display: flex;
				flex-direction: column;
				background-color:#F6F6F6;
				border-right: 2px solid #dddddd;
				overflow-y: auto;
				-webkit-overflow-scrolling:touch;
				.category_type{
					display: flex;
					width:148px;
					height: 100px;
					justify-content: center;
					line-height: 100px;
					position: relative;
					color:#333333;
					font-size:30px;
					flex-shrink: 0;
					&.on{
						background-color:#ffffff;
						border-top:2px solid #dddddd;
						border-bottom: 2px solid #dddddd;
						box-sizing: border-box;
						&::before{
							content: '';
							width:10px;
							height: 34px;
							display: inline-block;
							background-color:#F6C744;
							position: absolute;
							left:0;
							top:50%;
							margin-top:-17px;
						}
					}
					
				}
			}
			.category_content{
				display: flex;
				flex: 1;
				flex-direction: column;
				.category_sort_wrap{
					display: flex;
					justify-content: space-between;
					height:100px;
					line-height: 100px;
					padding:0 30px;
					border-top:2px solid #dddddd;
					font-size:26px;
					color:#686868;
					box-sizing: border-box;
					position: relative;
					.sort_type{
						color:#333333;
						position: relative;
						padding-right:40px;
						&::after{
							content: '';
							width:15px;
							height:15px;
							border-top:2px solid #999999;
							border-left:2px solid #999999;
							display: inline-block;;
							position: absolute;
							right:0;
							top:50%;
							margin-top:-12px;
							transform:rotate(225deg);
							transition: all 0.3s;
							border-radius: 1px;
						}
						&.on::after{
							margin-top:-2px;
							transform:rotate(45deg);
						}
					}
					.sort_type_wrap{
						width: 100%;
						max-height:0;
						overflow: hidden;
						display: block;
						position: absolute;
						top:100%;
						left:0;
						z-index: 2;
						background-color:#ffffff;
						border-bottom: 2px solid #dddddd;
						box-sizing: border-box;
						transition: all .3s;
						&.on{
							max-height:100vh;
						}
						.sort_type_item{
							display: flex;
							padding:0 30px;
							justify-content: flex-end;
							align-items: center;
							view{
								padding-right:40px;
								position: relative;
							}
							view.on::after{
								content: '';
								width: 10px;
								height:20px;
								border-top:2px solid #999999;
								border-left:2px solid #999999;
								display: inline-block;
								position: absolute;
								top:50%;
								margin-top:-15px;
								right:0;
								transform: rotate(225deg);
								border-radius: 1px;
							}
						}
					}
				}
				.category_list_wrap{
					flex: 1;
					display: flex;
					flex-direction: column;
					overflow: auto;
					-webkit-overflow-scrolling:touch;
					.category_list{
						border-top:2px solid #dddddd;
						display: block;
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
					.loadpromt{
						padding:10px;
						font-size:24px;
						color:#989898;
						display: flex;
						justify-content: center;
						align-items: center;
						.loadcover{
								background-color: rgba(0,0,0, 0.3);
								border-radius: 1px;
								width: 40px;
								height:20px;
								margin-right:10px;
								font-size: 0;
							.cloud{
								width: 4px;
								height: 20px;
								opacity: 0.5;
								position: relative;
								display: inline-block;
								box-shadow: 6px 0px 0px 0px rgba(255,255,255,1),
											12px 0px 0px 0px rgba(255,255,255,1),
											18px 0px 0px 0px rgba(255,255,255,1),
											24px 0px 0px 0px rgba(255,255,255,1),
											30px 0px 0px 0px rgba(255,255,255,1),
											36px 0px 0px 0px rgba(255,255,255,1);
								animation: rain 1s linear infinite alternate;
								&:after{
									width: 40px;
									height: 20px;
									position: absolute;
									display: inline-block;
									content: "";
									background-color: rgba(255,255,255,1);
									top: 0px;
									opacity: 1;
									animation: line_flow 2s linear infinite reverse;
								}	
							}
						}	
					}
				}
			}
		}
	}
	@keyframes line_flow{
		0%{ width: 0px;}
		100%{width: 40px;}
	}
	@keyframes rain{
		0%{
		box-shadow: 6px 0px 0px 0px rgba(255,255,255,1),
					12px 0px 0px 0px rgba(255,255,255,0.9),
					18px 0px 0px 0px rgba(255,255,255,0.7),
					24px 0px 0px 0px rgba(255,255,255,0.6),
					30px 0px 0px 0px rgba(255,255,255,0.3),
					36px 0px 0px 0px rgba(255,255,255,0.2);
		}
		100%{
		box-shadow: 6px 0px 0px 0px rgba(255,255,255,0.2),
					12px 0px 0px 0px rgba(255,255,255,0.3),
					18px 0px 0px 0px rgba(255,255,255,0.6),
					24px 0px 0px 0px rgba(255,255,255,0.7),
					30px 0px 0px 0px rgba(255,255,255,0.9),
					36px 0px 0px 0px rgba(255,255,255,1);
			opacity: 1;
		}
	}
</style>
