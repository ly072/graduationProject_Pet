<template>
<view class="content">
    <!--头部导航栏-->
    <view class="top-banner" style="background-color:grey;height:120px;width:100%;display:flex;flex-direction:row;">
        <view class="top-banner-item" style="background:red;width:100px;height:80px;margin:20px">
            <view class="top-banner-item-title" >地区</view>
            <view class="top-banner-item-content">上海市</view>
        </view>
        <view class="top-banner-item" style="background:red;width:100px;height:80px;margin:20px">
            <view class="top-banner-item-title" >物种</view>
            <view class="top-banner-item-content">全部</view>
        </view>
        <view class="top-banner-item" style="background:red;width:100px;height:80px;margin:20px">
            <view class="top-banner-item-title" >话题类型</view>
            <view class="top-banner-item-content">全部</view>
        </view>

        

    </view>

    <!--每个人的动态-->
        <view class="activate" style="width:100%;height:500px;background-color:green">
            <view class="activate-user">
                <view class="activate-user-icon"></view>
                <view class="activate-user-info">
                    <view class="activate-user-info-name"></view>
                    <view class="activate-user-info-time"></view>
                </view>

            </view>
            <view class="activate-content">

            </view>

    </view>




   <view class="bottom-banner">
       <view class="bottom-banner-item">
        <img src="../../static/img/logo.jpg" alt="" style="margin:5px 25px;widthd:40px;height:40px">
        <view style="text-align:center;"><span style="color:white;">宠物视频</span></view>
       </view>
        <view class="bottom-banner-item">
        <img src="../../static/img/logo.jpg" alt="" style="margin:5px 25px;widthd:40px;height:40px" @click="at_discover()">
        <view style="text-align:center;"><span style="color:white;">发现趣味</span></view>
       </view>
        <view class="bottom-banner-item">
        <img src="../../static/img/logo.jpg" alt="" style="margin:5px 25px;widthd:40px;height:40px" @click="submit()">
        <view style="text-align:center;"><span style="color:white;">我的消息</span></view>
       </view>
        <view class="bottom-banner-item">
        <img src="../../static/img/logo.jpg" alt="" style="margin:5px 25px;widthd:40px;height:40px" @click="submit()">
        <view style="text-align:center;"><span style="color:white;">我的空间</span></view>
       </view>
   </view>


   


</view>



</template>

<script>
export default {
    
    data(){

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
        }
    }
}
</script>


<style lang="scss" scoped>
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
  
  
  

