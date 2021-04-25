<template>
<view class="content">
    <view class="daliy-miaosha" style="width:100%;height:50upx">
        <strong>今日秒杀</strong>
        <img src="hot">
    </view>

    <view class="hot-search2" style="height:100%;width:100%">
        <view class="block" style="position:relative;overflow:hidden;height:300px;width:95%;background-color:green;margin:5px;margin-bottom:10px;border-radius:20px;box-shadow:1px 2px 3px 4px #ccc ;">
            <img class="img" src="../../static/jingtai_test1.png" style="width:100%;height:100%;position:relative;border-radius:20px">
                    <view class="block-word" style="padding:20px;width:100%;position:absolute;left:-10px;top:0px;font-size:20px;color:white;width:106%;height:30px;background: linear-gradient(to right,#ff907e, #ff4b3c);  ">17:00 抢购中</view>

            </img>

            
        </view>
        
    </view>


    <view class="second-miaosha" style="display:flex;flex-direction:row;margin-bottom:20px">
        <view class="block" style="margin-right:50px;position:relative;height:150px;width:40%;background-color:green;margin:5px;margin-bottom:10px;border-radius:20px;box-shadow:1px 2px 3px 4px #ccc ;">
            <img class="img" src="../../static/jingtai_test2.png" style="width:100%;height:100%;position:relative;border-radius:20px">
                                <view class="block-word" style="position:absolute;left:20px;top:20px;font-size:20px;color:white">一元买走</view>

            </img>

            
        </view>

        <view class="block" style="position:relative;height:150px;width:40%;background-color:green;margin:5px;margin-bottom:10px;border-radius:20px;box-shadow:1px 2px 3px 4px #ccc ;">
            <img class="img" src="../../static/jingtai_test3.png" style="width:100%;height:100%;position:relative;border-radius:20px">
                                <view class="block-word" style="position:absolute;left:20px;top:20px;font-size:20px;color:white">养宠补贴</view>

            </img>

            
        </view>



    </view>


   

</view>



</template>

<script>
export default {
    

    onLoad(){
console.log("create");
    },
    methods:{

    }
}
</script>


<style lang="scss" scoped>

</style>