<template>
<view class="content">
   <view class="bottom-banner">
       <img src="../../static/img/logo.jpg" alt="" style="margin:10px 25px;widthd:50px;height:50px">
       <img src="../../static/img/logo.jpg" alt="" style="margin:10px 25px;widthd:50px;height:50px">
       <img src="../../static/img/logo.jpg" alt="" style="margin:10px 25px;widthd:50px;height:50px">
       <img src="../../static/img/logo.jpg" alt="" style="margin:10px 25px;widthd:50px;height:50px">
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
        submit(){
            console.log("hello");
            uni.navigateTo({
                url:"index"
            })
        }
    }
}
</script>


<style lang="scss" scoped>
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