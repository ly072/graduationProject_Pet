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