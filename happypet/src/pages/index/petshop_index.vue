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

        <view style="height:600px;width:98%;display:flex;flex-direction:column;">
            <view style="width:95%;height:100%;border:1px solid #000;margin:5px">
                                <view class="miaosha-title">今日优惠</view>
                <view class="miaosha-content" style="display:flex;flex-direction:row;justify-content:center;align-items:center">
                    <view class="miaosha-item"  v-for="index of 3" style="margin:5px">
                        <view class="item-pic" style="width:100px;height:100px;"><img src="../../static/shop/1.jpeg" style="width:100%;height:100%"></view>
                        <view class="item-word">日本因阿宝</view>
                        <view class="item-price">￥998</view>
                    </view>


                </view>
            </view>
            <view style="width:95%;height:100%;border:1px solid #000;margin:5px">
                <view class="miaosha-title">秒杀区域</view>
                <view class="miaosha-content" style="display:flex;flex-direction:row;justify-content:center;align-items:center">
                    <view class="miaosha-item"  v-for="index of 3" style="margin:5px">
                        <view class="item-pic" style="width:100px;height:100px;"><img src="../../static/shop/1.jpeg" style="width:100%;height:100%"></view>
                        <view class="item-word">日本因阿宝</view>
                        <view class="item-price">￥998</view>
                    </view>


                </view>
            </view>
            <view style="width:95%;height:100%;border:1px solid #000;margin:5px">
                
                <view class="miaosha-content" style="display:flex;flex-direction:row;justify-content:center;align-items:center" v-for="index of 3">
                    <view class="miaosha-item"  v-for="index of 3" style="margin:5px">
                        <view class="item-pic" style="width:100px;height:100px;"><img src="../../static/shop/1.jpeg" style="width:100%;height:100%"></view>
                        <view class="item-word">日本因阿宝</view>
                        <view class="item-price">￥998</view>
                    </view>


                </view>
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