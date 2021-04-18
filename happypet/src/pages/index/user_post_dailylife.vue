<template>
<view class="content">
    用户发布每日动态

<view style="display:flex;flex-direction:row;width:100%;margin-top:50px"><span style="width:20%;font-size:18px">标题:</span> <input :value="user" class="app-form-user" placeholder="请输入标题" @input="onInput_user" /></view>
   <view style="display:flex;flex-direction:row;width:100%;margin-top:50px"><span style="width:20%;font-size:18px">内容:</span> <textarea style="border-width:2px;border-style:solid" rows="3" cols="20"></textarea></view>
<button  style="margin-top:50px;width:100%;background: linear-gradient(to right,pink, #ff6666);color:white;border-style:none;border-radius:20px"  @click="submit()" plain>发布</button>

</view>



</template>

<script>
export default {
    

    onLoad(){
console.log("create");
    },
    methods:{
        submit(){


                        uni.navigateBack({

            success: () => {

     
                

                let page = getCurrentPages().pop();  //跳转页面成功之后

                if (!page) return;

                let options = {

                user_login:1  



                }

                                       uni.showToast({
								title: '发布成功',
								icon: 'none'
                            });


            }

            })

        }
    }
}
</script>


<style lang="scss" scoped>

</style>