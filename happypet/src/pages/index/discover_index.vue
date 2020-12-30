<template>
<view class="content">
    <!--头部导航栏-->
    <view class="top-banner" style="background-color:#99CCFF;height:80px;width:100%;display:flex;flex-direction:row;">
        <view class="top-banner-item" style="width:100px;height:40px;margin:20px">
            <view class="top-banner-item-title" >地区</view>
            <view class="top-banner-item-content" style="color:white">上海市</view>
        </view>
        <view class="top-banner-item" style="width:100px;height:40px;margin:20px">
            <view class="top-banner-item-title" >物种</view>
            <view class="top-banner-item-content" style="color:white">全部</view>
        </view>
        <view class="top-banner-item" style="width:100px;height:40px;margin:20px">
            <view class="top-banner-item-title" >话题类型</view>
            <view class="top-banner-item-content" style="color:white">全部</view>
        </view>

        

    </view>


	<view class="personal-interest" style="width:100%;height:100%;" v-for="item in 3">
		<view class="interest-banner" style="height:80px;display:flex
		;flex-direction:row">
			<view class="interest-head-icon" style="width:50%">

				<image src="../../static/img/user_icon.jpg" style="width:60px;height:60px;margin:10px;border-radius:90px"></image>
			</view>
			<view class="interest-user-info"  style="width:100%;display:flex;
			flex-direction:column">
				<view class="interest-user-title" style="height:100%;">是我呀</view>
				<view class="interest-user-name" style="height:100%;">2020年9月20日</view>
			</view>
		</view>
		<view class="interest-text">这个是我和狗狗的故事</view>
		<view class="interest-image-container">
			<image src="../../static/pet1.jpeg" style="width:100px;height:100px;margin:10px;"></image>
			<image src="../../static/pet2.jpeg" style="width:100px;height:100px;margin:10px;"></image>
		</view>

		<view class="thumb-container" style="height:100px;background-color:#FFFAFA">
			<view class="interest-comment" style="height:80px;display:flex
			;flex-direction:row">
				<view class="interest-head-icon" style="width:50%">

					<image src="../../static/shuijiao.jpg" style="width:60px;height:60px;margin:10px;border-radius:90px"></image>
				</view>
				<view class="interest-user-info"  style="width:100%;display:flex;
				flex-direction:column">
					<view class="interest-user-title" style="height:100%;"><text style="color:grey">评论：</text>好可爱呀！</view>
					<view class="interest-user-name" style="height:100%;">2020年9月20日</view>
				</view>

			</view>
		</view>
		<view style="margin:10px 0px;width:100%;height:5px;border-bottom:1px #FFFAFA solid"></view>

		<view class="thumb-container" style="height:200px;background-color:#FFFAFA">
			<view class="interest-comment" style="height:80px;display:flex
			;flex-direction:column">
				<view class="interest-head-icon" style="width:50%">

					<image src="../../static/shuijiao.jpg" style="width:60px;height:60px;margin:10px;border-radius:90px"></image>
				</view>
				<view class="interest-user-info"  style="width:100%;display:flex;
				flex-direction:row">
					<view class="interest-user-title" style="height:50%;"><text style="color:grey">请评论：</text><input class="comment-input" placeholder="文明发言"></view>
					<button style="width:200upx;height:50%;margin:20px 20px"class="mini-btn" type="primary" size="mini">发送</button>
				</view>

			</view>
		</view>


		<view style="margin:40px 0px;width:100%;height:10px;border-bottom:2px grey solid"></view>

	</view>











   


</view>



</template>

<script>
export default {
    props:['reviewList'],
    
    data(){
        		return{
			heartList:false,
			height:"",
			textarea:false,
			placeholder:'请输入内容',
			input:""
		}


    },
    onLoad(){
console.log("create");
    },
    methods:{
        //在这写功能函数

        submit(){
            console.log("hello");
            uni.navigateTo({
                url:"searchword"
            })
        },

        		// 键盘高度发生变化
		keyboardheightchange(e){
			this.height=e.detail.height-2;
			if(e.detail.height==0){
				this.inputShow(1);
			}
		},
		//回复
		nickName(item){
			this.textarea=true;
			this.placeholder='回复：'+item;
		},
		//关闭键盘
		inputShow(a){
			if(a==1){
				this.textarea=false;
			}else{
				this.textarea=true;
				this.placeholder="请输入内容"
			}
		},
		//笔芯
		showHeart(a){
			if(a==1){
				this.heartList=false
			}else{
				this.heartList=true
			}
		}

    }
}
</script>


<style lang="scss" scoped>


.friend{
	background-color: #FFFFFF;
    width:500px;
    
	 .input{
		width: 100%;
		display: flex;
		position: fixed;
		align-items: center;
		background-color: #F2F2F2;
		padding: 10rpx 0;
		left: 0;
		textarea{
			margin-left: 10rpx;
			min-height: 60rpx;
			height: auto;
			width: 80%;
			background-color: #FFFFFF;
			font-size: 26rpx;
			padding: 5rpx;
		}
		button{
			background-color: #07c160;
			border:none !important;
			font-size: 25rpx;
			padding: 0;
			width: 100rpx;
			height: 60rpx;
			color: #FFFFFF;
		}
	 }
	.buzan{
		display: flex;
		align-items: center;
	    image{
			width:40rpx;
			height:40rpx;
			margin-left: 20rpx;
		}
		view{
			width: 40rpx;height: 0;
		}
		padding-bottom: 10rpx;
		border-bottom: 1px solid #CCCCCC;
		.message{
			width: 45rpx;
			height: 45rpx;
		}
	}
	.discuss{
		background-color: #F2F2F2;
		border-radius: 10rpx;
		width: 530rpx;
		margin-top: 20rpx;
		.talk{
			font-size: 25rpx;
			padding: 0 10rpx 10rpx 10rpx;
			view{
				margin-top: 10rpx;
			}
			.talk-set{
				font-size: 23rpx;
				.title{
					color: #1296db;
					font-size: 25rpx;
				}
			}
		}
		.heart-people{
			display: flex;
			flex-wrap: wrap;
			padding:0 0 10rpx 10rpx;
		.heart{
			display: flex;
			align-items: center;
			justify-content: center;
			margin-right:10rpx;
			margin-top: 10rpx;
			image{
				width: 20rpx;
				height: 20rpx;
			}
			color: #1296db;
			text{
				font-size: 20rpx;
				margin-left: 5rpx;
			}
		}
	  }
	}
	  .show{
		 display: flex;
		.friend-right{
			width: 550rpx;
			.title{
				font-size:30rpx;
				font-weight: 700;
				margin-top: 15rpx;
			}
			.content{
				font-size: 25rpx;
				color: #323233;
				margin-top: 10rpx;
			}
		}
		.friend-left{
			$w:80rpx;
			width: $w;
			min-width: $w;
			min-height: $w;
			height: $w;
			border-radius: 50%;
			margin: 10rpx 10rpx 10rpx 0;
		}
		.image{
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			flex-direction: row;
			width: 488rpx;
			margin: 10rpx 0;
			image{
				margin-top: 5rpx;
				width: 160rpx;
				height: 160rpx;				
			}
		}
	  }
	}

span{
    font-size: 0.6em;
}
  .content{
      
      display:flex;
      flex-direction: column;
      align-items: center;
      
  }



.bottom-banner{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 100px;
    position: absolute;
    background:black;
    bottom:0;
    overflow: hidden;
}


span{
    font-size: 0.6em;
}
  .content{
      
      display:flex;
      flex-direction: column;
      align-items: center;
      
  }
  .top-bar{
      height:90rpx;
      width:100%;
      box-sizing: border-box;
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;

      background: #FF0000;
      border-bottom: grey;

  }
  .login-title{
      margin: 50px;
  }
  .app-form{
      height:300px;
      width:70%;
    .app-form-user{
        margin: 50px;
        border-bottom: thick double #aa0000;
        
    }
    .app-form-password{
        margin: 50px;
        border-bottom: thick double #aa0000
    }
    .app-form-loginbtn{
        margin: 50px;
    }
  }
  

</style>
  
  
  

