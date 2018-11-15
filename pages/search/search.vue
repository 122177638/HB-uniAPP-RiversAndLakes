<template>
	<view class="content">
		<view class="search_container">
			<view class="search_wrap">
				<view class="search_import">
					<image src="../../static/images/search.png" class="search_icon" mode=""></image>
					<input type="text" class="search_ipt" placeholder="输入标题或内容" v-model="keyword"/>
				</view>
				<view 
					:class="['search_btn',{'on':searchShow}]" 
					@click="searchShow?startSearch():gobackEvent()">
					{{searchShow?'搜索':'取消'}}
				</view>
			</view>
			<scroll-view class="search_content" scroll-y @scrolltolower="PulluploadEvent()">
				<view class="search_ruselt" v-if="resultShow">
					<!-- 有数据 -->
					<view class="search_success" v-if="categoryData !=''">
						<view class="search_text">为您找到以下跟 "<text class="keyword">{{keyword}}</text>" 有关的内容</view>
						<view class="search_success_content">
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
							<view class="loadpromt">没有更多了</view>
						</view>
					</view>
					<!-- 无数据 -->
					<view class="search_fail" v-else>
						<view class="search_img">
							<image src="../../static/images/null.png" class="search_icon" mode=""></image>
						</view>
						<view class="search_text">抱歉，没有找到 "<text class="keyword">{{keyword}}</text>" 相关内容</view>
					</view>
				</view>
				<!-- 推荐搜索 -->
				<view class="recom_wrap" v-show="categoryData ==''">
					<view class="recom_title">推荐搜索</view>
					<view class="recom_list">
						<view class="recom_item">情商</view>
						<view class="recom_item">心里健康</view>
						<view class="recom_item">抑郁</view>
						<view class="recom_item">性</view>
						<view class="recom_item">童年阴影</view>
						<view class="recom_item">内向</view>
						<view class="recom_item">自卑</view>
					</view>
				</view>
				<!-- 热门推荐 -->
				<view class="hot_wrap" v-show="categoryData ==''">
					<view class="hot_title">热门推荐</view>
					<view class="hot_content">
						<view class="category_list">
							<view class="category_item" v-for="item in HotData" :key="item.cid">
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
						<view class="loadpromt">没有更多了</view>
					</view>
				</view>
				<!-- 搜索提示 -->
				<view class="search_promt_wrap" v-show="searchShow && categoryData!='' && !resultShow">
					<view class="search_promt_list">
						<view class="search_promt_item" v-for="item in categoryData" @click="importSearchEvent(item)" :key="item.cid">{{item.name}}</view>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
	
</template>

<script>
	import { throttle } from '../../utils/utils.js';
	export default {
		data(){
			return{
				HotData:[
					{cid:1,name:'甜蜜',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
					{cid:2,name:'大帝',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
					{cid:3,name:'无敌',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
					{cid:4,name:'至尊',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
					{cid:5,name:'中和',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
					{cid:6,name:'无极',describe:'测测你的自尊水平?',oldmoney:'99',money:'9.9',count:'23255',type:'性格',headimg:'http://pic.qiantucdn.com/58pic/15/42/47/79h58PICG4y_1024.png!qtwebp324'},
				],
				categoryData:[],
				keyword:'',
				searchShow:false,
				resultShow:false,
			}
		},
		watch: {
			keyword:throttle(function(newValue, oldValue) {
				let searcharr = new Array();
				if(newValue == ""){
					this.searchShow = false;
					this.categoryData = [];
					this.resultShow = false;
					console.log('请输入关键字')
				}else{
					this.searchShow = true;
					this.HotData.map((item)=>{
						if(item.name.indexOf(newValue) != -1){
							searcharr.push(item)
							this.categoryData = searcharr;
							console.log(123)
						}
					})
					if(this.resultShow && newValue!=oldValue){
						this.resultShow = false;
					}
				}
			},100,500)
			
		},
		mounted(){

		},
		methods:{
			startSearch(){
				this.searchEvent();
			},
			importSearchEvent(item){
				this.keyword = item.name;
				this.searchEvent()
			},
			searchEvent(){	
				uni.showLoading({title:'加载中...'})
				setTimeout(()=>{
					this.resultShow = true;
					uni.hideLoading()
				},1000)
			},
			
			gobackEvent(){
				console.log('返回')
			},
			PulluploadEvent(){
				
			}
		}
	}
</script>

<style scoped lang="scss">
	.search_container{
		display: flex;
		flex-direction: column;
		height:100vh;
		.search_wrap{
			flex-shrink: 0;
			align-items: center;
			display:flex;
			padding:20px;
			box-sizing: border-box;
			background-color:#FFFFFF;
			position: relative;
			.search_import{
				flex: 1;
				height:60px;
				position: relative;
				.search_ipt{
					width: 100%;
					height:100%;
					padding-left:75px;
					padding-right:20px;
					box-sizing: border-box;
					border-radius: 35px;
					background-color:#f0f0f0;
					font-size:28px;
				}
				.search_icon{
					position: absolute;
					width:32px;
					height:32px;
					left:30px;
					top:50%;
					margin-top:-16px;
				}
			}
			.search_btn{
				width:100px;
				height:60px;
				line-height: 60px;
				text-align: center;
				font-size:28px;
				color:#333333;
				border:1px solid #f0f0f0;
				border-radius: 10px;
				margin-left:20px;
				box-sizing: border-box;
				&.on{
					background-color:#FFDD2B;
					border:none;
				}
			}
		}
		.search_content{
			flex: 1;
			overflow: auto;
			-webkit-overflow-scrolling:touch;
			.recom_wrap{
				.recom_title{
					font-size:28px;
					color:#989898;
					padding:0 24px;
					line-height: 4;
				}
				.recom_list{
					display: flex;
					flex-wrap: wrap;
					padding:0 40px 20px;
					box-sizing: border-box;
					.recom_item{
						padding:10px 20px;
						border-radius: 10px;
						background-color:#FFFFFF;
						margin-right:20px;
						margin-bottom:20px;
					}
				}
			}
			.hot_wrap{
				background-color:#FFFFFF;
				.hot_title{
					font-size:28px;
					color:#989898;
					padding:30px 24px 0;
				}
				.hot_content{
					
				}
			}
			.search_promt_wrap{
				width:100%;
				height:100%;
				background-color:#FFFFFF;
				.search_promt_list{
					border-top: 1px solid #f6f6f6;
					.search_promt_item{
						padding:20px;
						font-size:28px;
						color:#333333;
						border-bottom: 1px solid #f6f6f6;
					}
				}
			}
			.search_ruselt{
				.search_fail{
					display: flex;
					flex-direction: column;
					align-items: center;
					margin:50px 0 0;
					.search_img{
						width:140px;
						height:140px;
						display: flex;
						justify-content: center;
						align-items: center;
						background-color:#FFFFFF;
						border-radius: 50%;
						margin-bottom:30px;
						.search_icon{
							width:98px;
							height:64px;
						}
					}
				}
				.search_success{
					.search_text{
						padding:20px 0;
						text-align: center;
					}
					.search_success_content{
						background-color:#FFFFFF;
					}
				}
				.search_text{
					color:#999999;
					font-size:28px;
					.keyword{
						color:#333333;
					}
				}
			}
		}	
		.category_list{
			.category_item{
				padding:30px 0;
				margin:0 24px;
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
			font-size:28px;
			color:#333333;
			line-height: 3;
			text-align: center;
			background-color: #F6F6F6;
		}
	}
</style>
