<template>
<view class="content">
    <!--头部导航栏-->
    <view class="top-bar">
   
    </view>
    <view class="login-title">
        密码帐号登录
    </view>

    <!--表单-->
    <view class="app-form">
        <input class="app-form-user" placeholder="请输入帐号" @input="onInput" />
        <input class="app-form-password" placeholder="请输入密码" @input="onInput" />
        <button class="app-form-loginbtn" type="warn" @click="submit()" plain>登录</button>
    </view>
    
    <view class="login-way">
        <span>帐号密码登陆</span>
        <span>|</span>
        <span>登陆遇到问题？</span>
    </view>

    <view>
        <span>社交帐号登陆</span>
    </view>
     <view>
        <span>注册即代表您同意《xxx社区协议》</span>
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