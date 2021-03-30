<template>
<view class="content">

        <view class="uni-title uni-common-mt" style="">
            <ul style="width:100%">
                <li>今日优惠</li>
                <li>我的订单</li>
                <li>我的购物车</li>
                <li>我的优惠券</li>
                <li>立即下单</li>
                <li>物流状态</li>
            </ul>
        </view>

        <view style="height:600px;width:100%;display:flex;flex-direction:column">
            <view style="width：100%;height:200px;background:grey">
                今日优惠
            </view>
            <view style="width：100%;height:200px;background:pink">
                限时秒杀
            </view>
            <view style="width：100%;height:200px;background:green">
                商品列表
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

.uni-title li{
    display: inline;
    font-size:10px;
    margin:5px;
}

</style>