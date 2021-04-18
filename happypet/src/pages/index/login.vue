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
           timeProcessing(){


let Time = new Date();


var year = Time.getFullYear()
var month = Time.getMonth() + 1
var day = Time.getDate()
var hour = Time.getHours() 
var minute = Time.getMinutes() 
var second = Time.getSeconds() 
if(month >= 1 && month <= 9){
month = "0" + month;}
if(day >= 0 && day <= 9){
day = "0" + day
}
if(hour >= 0 && hour <= 9){
hour = "0" + hour
}
if(minute >= 0 && minute <= 9){
minute = "0" + minute
}
if(second >= 0 && second <= 9){
second = "0" + second
}
var timestemp = year + month + day  + hour + minute  + second
console.log(timestemp)//Mon Jun 24 2019 11:08:48 GMT+0800 (中国标准时间)

//1561345728000
return timestemp;

} ,
        onInput_user(e){
            this.user=e.target.value;
            //console.log(this.user)   ok
        },
        onInput_pwd(e){
            this.password = e.target.value;
            //console.log(this.password) ok 
        },
        submit(){


            if((this.password === '') || (this.user === '')){
                uni.showToast({
                    title: '请完善填写',
                    icon: 'none'
                });

            }

            else{

                uni.request({
                    url: 'http://localhost:3000/func/login', 
                     data:{user:this.user,password:this.password,r_time:this.timeProcessing()},
                      method: 'GET',
                       header: {},
                    success: (res) => {
                        console.log(res.data); 
                        if(res.data != "-1"){



                        //添加类似cookie保存用户信息
                        // const store = new Vuex.Store({  
                        //     state: {  
                        //         uerInfo: {},  
                        //         hasLogin: false  
                        //     },  
                        //     mutations: {  
                        //         login(state, provider) {//改变登录状态  
                        //             state.hasLogin = true  
                        //             state.uerInfo.token = provider.token  
                        //             state.uerInfo.userName = provider.user_name  
                        //             uni.setStorage({//将用户信息保存在本地  
                        //                 key: 'uerInfo',  
                        //                 data: provider  
                        //             })  
                        //         },  
                        //         logout(state) {//退出登录  
                        //             state.hasLogin = false  
                        //             state.uerInfo = {}  
                        //             uni.removeStorage({  
                        //                 key: 'uerInfo'  
                        //             })  
                        //         }  
                        //     }  
                        // })

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
                    },
                    fail:(res) =>{
                    //失败时候回调
                    uni.showToast({
                    title: '网络请求出错',
                    icon: 'none'
                });
                }
                });


            }






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