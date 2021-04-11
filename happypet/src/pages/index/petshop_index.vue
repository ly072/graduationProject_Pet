<template>
<view class="content">

        <view class="uni-title uni-common-mt" style="">
            <ul class="shop-title" style="width:100%">
                <li v-on:click="find_cut()">
                    <img src="../../static/petshop_pic/cut.svg">
                    今日优惠
                </li>
                <li  v-on:click="myorder()">
                    <img src="../../static/petshop_pic/order.svg">
                    我的订单
                </li>
                <li  v-on:click="mycart()">
                    <img src="../../static/petshop_pic/cart.svg">
                    我的购物车
                </li>
                <li  v-on:click="mycut()">
                    <img src="../../static/petshop_pic/mycut.svg">
                    我的优惠券
                </li>
            </ul>
        </view>

        <view style="height:600px;width:98%;display:flex;flex-direction:column;">
            <view style="width:95%;height:100%;border:1px solid #000;margin:5px;box-shadow:1px 2px 3px 4px #ccc ;">
                                <view class="miaosha-title">今日优惠</view>
                <view class="miaosha-content" style="display:flex;flex-direction:row;justify-content:center;align-items:center">
                    <view class="miaosha-item" v-on:click="shop_info()" v-for="index of 3" style="margin:5px">
                        <view class="item-pic" style="width:100px;height:100px;"><img src="../../static/shop/1.jpeg" style="width:100%;height:100%"></view>
                        <view class="item-word">日本因阿宝</view>
                        <view class="item-price">￥998</view>
                    </view>


                </view>
            </view>
            <view style="width:95%;height:100%;border:1px solid #000;margin:5px;box-shadow:1px 2px 3px 4px #ccc ;">
                <view class="miaosha-title">秒杀区域</view>
                <view class="miaosha-content" style="display:flex;flex-direction:row;justify-content:center;align-items:center">
                    <view class="miaosha-item" v-on:click="shop_info()" v-for="index of 3" style="margin:5px">
                        <view class="item-pic" style="width:100px;height:100px;"><img src="../../static/shop/1.jpeg" style="width:100%;height:100%"></view>
                        <view class="item-word">日本因阿宝</view>
                        <view class="item-price">￥998</view>
                    </view>


                </view>
            </view>
            <view style="width:95%;height:100%;border:1px solid #000;margin:5px;box-shadow:1px 2px 3px 4px #ccc ;">
                
                <view class="miaosha-content" style="display:flex;flex-direction:row;justify-content:center;align-items:center" v-for="index of 3">
                    <view class="miaosha-item" v-on:click="shop_info()" v-for="index of 3" style="margin:5px">
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
        shop_info(){
            
            uni.navigateTo({
                url:"shop_info"
            })
        },
        find_cut(){
            
            uni.navigateTo({
                url:"find_cut"
            })
        },
                myorder(){
            
            uni.navigateTo({
                url:"myorder"
            })
        },
                mycart(){
            
            uni.navigateTo({
                url:"mycart"
            })
        },
                mycut(){
            
            uni.navigateTo({
                url:"mycut"
            })
        }

    }
    
}
</script>


<style lang="scss" scoped>

.uni-title li{
    display: inline;
    font-size:10px;
    margin:5px;
}

.uni-title img{
    width:20px;
    height:20px;
    
}
</style>