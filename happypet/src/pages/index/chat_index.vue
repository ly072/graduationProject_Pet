<template>
  <view class="content">
    <view class="top-bar">
        <view class="top-bar-left">
        <image src="../../static/img/user_icon.jpg"></image>
        </view>

        <view class="top-bar-center">

        <image src="../../static/img/logo.jpg"></image>
        </view>

        <view class="top-bar-right">
        <image src="../../static/img/zoom_glasses.jpg" @click="searchword()"></image>
        </view>

    </view>
  

    <view class="friends">
    

      <view class="friend-list">

        <view class="friend-list-l">
            <text class="tip"></text>
              <view class="user-image">
              <image src="../../static/img/user_list_icon.jpg"></image>
              </view>
       
        </view>
        <view class="friend-list-r">
          <view class="friend-list-top">
            <view class="friend-list-top-left">好友请求</view>
            <view class="friend-list-top-right">11:34</view>
          </view>

          <view class="friend-list-bottom">在么？</view>
        </view>

        
      </view>




  </view>

  		<view class="status_bar bgc" style=""></view>
		<view class="header">
			<text>微信(77)</text>
			<view class="header_right">
				<view class="iconfont icon-sousuo"></view>
				<view class="iconfont icon-tianjia"></view>
			</view>
		</view>


    		<scroll-view class="chatList" scroll-y="true">
			<!-- <view class="chat_item" v-for="item in userArr" :key="item.nickname" @touchstart="navChatDetail(item.id , item.nickname)"> -->
        <view class="chat_item">
				<view class="useravatar">
					<image src="../../static/img/user_list_icon.jpg" mode="scaleToFill"></image>
					<view class="img_bage">
					</view>
				</view>
				<view class="userInfo">
					<view class="infocontent">
						<view class="userName">
							小王
						</view>
						<view class="userChat">哈哈哈</view>


					</view>
					<view class="userDate" >
						2018年
					</view>


				</view>

			</view>

              <view class="chat_item">
				<view class="useravatar">
					<image src="../../static/img/user_list_icon.jpg" mode="scaleToFill"></image>
					<view class="img_bage">
					</view>
				</view>
				<view class="userInfo">
					<view class="infocontent">
						<view class="userName">
							小王
						</view>
						<view class="userChat">哈哈哈</view>


					</view>
					<view class="userDate" >
						2018年
					</view>


				</view>

			</view>

              <view class="chat_item">
				<view class="useravatar">
					<image src="../../static/img/user_list_icon.jpg" mode="scaleToFill"></image>
					<view class="img_bage">
					</view>
				</view>
				<view class="userInfo">
					<view class="infocontent">
						<view class="userName">
							小li
						</view>
						<view class="userChat">哈哈哈</view>


					</view>
					<view class="userDate" >
						2018年
					</view>


				</view>

			</view>

		</scroll-view>
</view>
    
    
    
    

</template>

<script>
export default {
    data(){
        return{
            title:'Hello'
        }
    },
onLoad(){

},
methods:{
          searchword(){
            console.log("hello");
            uni.navigateTo({
                url:"searchword"
            })
        }
}
}

</script>

<style lang="scss" scope>

//new add

	.chatList {
		margin-top: 110upx;
		overflow: hidden;
		width: 100%;
		/*  #ifdef H5 || MP */
		height: calc(100vh - 110upx - var(--window-bottom));
		/* #endif*/
		/*  #ifdef APP-PLUS */
		height: calc(100vh - 110upx - var(--window-bottom) - var(--status-bar-height);
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
				.img_bage {
					position: absolute;
					width: 20rpx;
					height: 20rpx;
					background-color: red;
					border-radius: 50%;
					top: 10rpx;
					right: 10rpx;
				}
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
		top: var(--status-bar-height);
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
		z-index: 3;
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
			.icon-sousuo {
				// margin-top: 8upx;
				font-size:50upx;
				margin-right: 70upx;
			}
			.icon-tianjia {
				font-size:45upx;
			}
		}
		
	}

  .content{
    display:flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: #ccc;

  }

  .top-bar{
    height:90px;
    width: 100%;
    box-sizing: border-box;
    display:flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;

    background: white;
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
    background: #fff;

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