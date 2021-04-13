<template>
  <view class="content" style="background:url('../../static/index_background.jpg')">

    	<view class="header">
			  <text>宠物社区兴趣平台</text>
		</view>
    <view class="top-bar" style="margin-top:130upx" v-if="0">
        <view class="top-bar-left">
        <image src="../../static/logo.png" style="margin:20px;width:40px;height:40px;border-radius: 50%;"></image> 
        </view>

        <view class="top-bar-center">

        <image src="../../static/img/logo.jpg" style="margin:0px 20px;width:30px;height:30px;border-radius: 50%;"></image>

		<view style="font-style:italic;font-weight:800"><text >一个不一样的宠物平台～</text></view>
		</image>
        </view>

        <view class="top-bar-right">
        <image src="../../static/img/zoom_glasses.jpg"  style="margin-right:20px;width:60px;height:60px;border-radius: 50%;" @click="searchword()"></image>
        </view>

    </view>
  

    <view class="friends">
    





  </view>

  		<view class="status_bar bgc" style=""></view>



    	<scroll-view class="chatList" scroll-y="true" style="margin-bottom:50px">
			<!-- <view class="chat_item" v-for="item in userArr" :key="item.nickname" @touchstart="navChatDetail(item.id , item.nickname)"> -->


			<view class="uni-list" style="background-color:transparent;">
					<view class="uni-list-cell" hover-class="uni-list-cell-hover" style="background-color:transparent;" v-for="(item,index) in news" :key="index"
					@tap="openinfo" :data-newsid="item.post_id">
						<view class="uni-media-list">
							<image class="uni-media-list-logo" :src="item.author_avatar">
									<view class="img_bage" style="position:absolute;z-index:2;left:0;margin-left:50px"></view>
							</image>

							<view class="uni-media-list-body" style="background-color:transparent;">
								<view class="uni-media-list-text-top">{{item.title}}</view>
								<view class="uni-media-list-text-bottom uni-ellipsis">{{item.content}}</view>
								<view class="uni-date" style="position:absolute;z-index:2;right:0;margin-right:50px">{{item.published_at}}</view>
							</view>
						</view>
					</view>
				</view>
		




					<!-- <view class="img_bage"> -->

		</scroll-view>
	</view>
    
    
    
    

</template>

<script>
export default {
    data(){
        return{
          img:'../../static/index_background.jpg',
				title:'',
				strings:'',
				news:[
  {
    "id": 121375,
    "from_id": "36kr",
    "title": "小白",
    "summary": "没有永远的敌人，只有永远的利益。",
    "column_id": "223",
    "column_name": "内容",
    "author_name": "未来汽车日报",
    "author_email": "",
    "author_avatar": "https://pic.36krcnd.com/avatar/201907/16100441/yd25e764o4bt93t9!120",
    "post_id": "5310910",
    "cover": "https://img.36krcdn.com/20200410/v2_9c3331af67e64994aa97a27fffb1a380_img_png?x-oss-process=image/resize,m_mfit,w_520,h_300/crop,w_520,h_300,g_center",
    "content": "在么？好久不见",
    "views_count": 0,
    "comments_count": 0,
    "published_at": "2020-04-11 17:07:48",
    "store_at": "0000-00-00 00:00:00",
    "type": "news",
    "created_at": "2020-04-11 17:11:09",
    "updated_at": "2020-04-11 17:11:09"
  },
    {
    "id": 121376,
    "from_id": "36kr",
    "title": "小黄",
    "summary": "没有永远的敌人，只有永远的利益。",
    "column_id": "223",
    "column_name": "内容",
    "author_name": "未来汽车日报",
    "author_email": "",
    "author_avatar": "https://pic.36krcnd.com/avatar/201907/16100441/yd25e764o4bt93t9!120",
    "post_id": "5310910",
    "cover": "https://img.36krcdn.com/20200410/v2_9c3331af67e64994aa97a27fffb1a380_img_png?x-oss-process=image/resize,m_mfit,w_520,h_300/crop,w_520,h_300,g_center",
    "content": "在么？好久不见",
    "views_count": 0,
    "comments_count": 0,
    "published_at": "2020-04-11 17:07:48",
    "store_at": "0000-00-00 00:00:00",
    "type": "news",
    "created_at": "2020-04-11 17:11:09",
    "updated_at": "2020-04-11 17:11:09"
  },
    {
    "id": 121377,
    "from_id": "36kr",
    "title": "小绿",
    "summary": "没有永远的敌人，只有永远的利益。",
    "column_id": "223",
    "column_name": "内容",
    "author_name": "未来汽车日报",
    "author_email": "",
    "author_avatar": "https://pic.36krcnd.com/avatar/201907/16100441/yd25e764o4bt93t9!120",
    "post_id": "5310910",
    "cover": "https://img.36krcdn.com/20200410/v2_9c3331af67e64994aa97a27fffb1a380_img_png?x-oss-process=image/resize,m_mfit,w_520,h_300/crop,w_520,h_300,g_center",
    "content": "在么？好久不见",
    "views_count": 0,
    "comments_count": 0,
    "published_at": "2020-04-11 17:07:48",
    "store_at": "0000-00-00 00:00:00",
    "type": "news",
    "created_at": "2020-04-11 17:11:09",
    "updated_at": "2020-04-11 17:11:09"
  }
]
        }
    },
	

	onLoad:function(e){		
		
		// 				uni.showLoading({
		// 		title: '加载中...',  //数据加载转转圈圈操作
		// 	});
        //    uni.request({   //数据请求
        //    	url: 'https://unidemo.dcloud.net.cn/api/news',
        //    	method: 'GET',
        //    	data: {},
        //    	success: res => {
		// 		console.log(res.data);
		// 		this.news=res.data;
		// 		uni.hideLoading(); // 关闭转圈圈操作
		// 	},
        //    	fail: () => {},
        //    	complete: () => {}
        //    });	

	},

methods:{
				searchword(){
					console.log("hello");
					uni.navigateTo({
						url:"searchword"
					})
				},
				openinfo: function(e){
						uni.navigateTo({  //跳转页面
							url: 'chat_personal'   //url加id
						});
					}
		}
}


</script>

<style lang="scss" scope>

	.uni-media-list-body{
		height: auto;
	}
	.uni-media-list-text-top{
		line-height: 1.6em;
	}

	.img_bage {
	position: absolute;
	width: 20rpx;
	height: 20rpx;
	background-color: red;
	border-radius: 50%;
	top: 10rpx;
	right: 10rpx;
}

//new add

	.chatList {
		overflow: hidden;
		width: 100%;
		/*  #ifdef H5 || MP */
		height: calc(100vh - 110upx - var(--window-bottom));
		/* #endif*/
		/*  #ifdef APP-PLUS */
		height: calc(100vh - 110upx - var(--window-bottom) - var(--status-bar-height));
		/* #endif*/
		.chat_item {
      margin:50px;
			width: 100%;
			height: 180upx;
			display: inline-block;
			padding-left: 35upx;
			.useravatar{
				width: 20%;
				height: 100%;
				float: left;
				position: relative;

				image {
					width: 128upx;
					height: 128upx;
					border-radius: 10upx;
					position: absolute;
					left: 50%;
					top: 50%;
					margin-left: -50%;
					margin-top: -50%;
				}
			}
			.userInfo {
				display: flex;
				float: left;
				align-items: center;
				width: 80%;
				height: 100%;
				color: rgb(211, 211, 211);
				font-size: 28upx;
				border-bottom: 1upx solid #ccc;
				padding-right: 35upx;
				
				.infocontent {
					flex: 9;
					height: 128upx;
					display: flex;
					flex-direction: column;
					justify-content:space-around;
					.userName {
						font-size: 32upx;
						font-weight: 520;
						color: #000000;
					}
					
				}
				.userDate {
					width: auto;
				}
			}
		}
	}
.header {
		position: fixed;
		/* #ifdef H5 || MP */
		top: 0;
		/* #endif */
		/* #ifdef APP-PLUS */
		/* #endif */
		left: 0;
		width: 100%;
		height: 110upx;
		display: flex;
		justify-content: space-between;
		align-items: center;
		background-color: #ededed;
		color: #000000;
		padding: 0 10upx;
		z-index: 999;
		text {
			font-size: 36upx;
			font-weight: 520;
		}
		.header_right {
			height: 100%;
			display: flex;
			justify-content: center;
			align-items: center;
			font-weight: 500;
		}
		
	}

  .content{
    display:flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

  }

  .top-bar{
    height:90px;
    width: 100%;
    box-sizing: border-box;
    display:flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    border-bottom:gray;
     .top-bar-left{
   
        text-align: left;
       height: 90px;/*元素高度*/
       width: 33%;
      float:left;
      image{
  
        width:68px;
        height:68px;
        border-radius:16rpx;
 
      }
    }
    .top-bar-center{

      height: 88px;/*元素高度*/
       width: 33%;
      text-align: center;
      float:center;
      image{
        
        width:68px;
        height:68px;
        border-radius:16rpx;
        
      }
    }
    .top-bar-right{
      height: 88px;
      width: 33%;
      float:right;

       image{
        width:68px;
        height:68px;
        float:right;

        top:50%;
        height:68px;
        margin-top:-34px;
        border-radius:16px;
         
        
      }
      
    }
  }
  .main{

  }
  .friends{
    width: 100%;

    

     .friend-list{
    margin: 2px;
    box-sizing: border-box;
    text-align:center;
    width: 100%;
    float:left;
    .friend-list-l{
      width: 20%;
      height:140rpx;
      float:left; 
         top:50%;
        height:70px;
        margin-top:70px;


      image{
        height: 78rpx;
        width: 78rpx;
        border-radius: 18px;
      }
    }
    .friend-list-r{
      flex-direction: column;
      width: 80%;
      height:140rpx;
      float:right;

      .friend-list-top{
        width: 100%;
        .friend-list-top-left{
          float:left;
          margin: 20rpx;
          font-size: 20px;
          color: grey;
          width:35%;
          

          
        }
        .friend-list-top-right{
          float:right;
          margin: 20rpx;
           font-size: 20px;
          color: grey;
          width:35%;


        }
      }

      .friend-list-bottom{
        
      }

    }
  }
    
  }
 
  
 
 
</style>