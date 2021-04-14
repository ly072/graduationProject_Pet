<template>
<view class="content">
    <!--头部导航栏-->
    <view class="top-bar">
   
    </view>
    <view class="login-title">
        登录
    </view>

    <!--表单-->
    <view class="app-form" style="width:70%">
        <view style="display:flex;flex-direction:row;width:100%;margin-top:50px"><span style="width:20%;font-size:18px">帐号:</span> <input :value="user" class="app-form-user" placeholder="请输入帐号" @input="onInput_user" /></view>
        
        <view style="display:flex;flex-direction:row;width:100%;margin-top:50px"><span style="width:20%;font-size:18px">密码:</span> <input :value="password" class="app-form-password" placeholder="请输入密码" @input="onInput_pwd" /></view>
        <button  style="margin-top:50px;width:100%;background: linear-gradient(to right,pink, #ff6666);color:white;border-style:none;border-radius:20px"  @click="submit()" plain>登录</button>
    </view>
    
    <view class="login-way">
        <span style="font-size:20px;" @click="jump_register()">注册帐号</span>
        <span style="font-size:20px;margin:0px 20px">|</span>
        <span style="font-size:20px;">登陆遇到问题？</span>
    </view>

    <view style="margin-top:50px">
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
        return{one:1,
        user:'',
        password:''
        }

    },
    
    onLoad(){
console.log("create");
    },
    methods:{
        onInput_user(e){
            this.user=e.target.value;
            //console.log(this.user)   ok
        },
        onInput_pwd(e){
            this.password = e.target.value;
            //console.log(this.password) ok 
        },
        submit(){
            if((this.user === "user01") && (this.password === "123456"))
            {

                            
            uni.navigateBack({

            success: () => {

                            uni.showToast({
								title: '登录成功',
								icon: 'none'
                            });
                

                let page = getCurrentPages().pop();  //跳转页面成功之后

                if (!page) return;

                let options = {

                user_login:1  



                }
                console.log('hellohaha')


            }

            })
            }
            else if((this.user === "admin") && (this.password === "654321"))
            {
               uni.navigateTo({
                url:"admin_index"
            })



            }
            else{
                            uni.showToast({
								title: '登陆失败',
								icon: 'none'
                            });

            }

        },

        jump_register(){

               uni.navigateTo({
                url:"register"
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

      background: linear-gradient(to right,pink, #ff6666);
      border-bottom: grey;

  }
  .login-title{
      margin:50px;

  }
  .app-form{
      height:300px;
      width:90%;
    .app-form-user{

        border-bottom: thick double #aa0000;
        display:inline-block;
        width:90%;
        
        
    }
    .app-form-password{

        border-bottom: thick double #aa0000;
        display:inline-block;
        width:90%;
    }
    .app-form-loginbtn{
        margin: 50px;
    }
  }
  

</style>