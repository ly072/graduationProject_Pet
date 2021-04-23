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

        <view style="height:100%;width:98%;display:flex;flex-direction:column;">


            <view style="width:95%;height:100%;margin:5px;box-shadow:1px 2px 3px 4px #ccc ;">
                
                <view class="miaosha-content" style="display:flex;flex-direction:row;justify-content:center;align-items:center" v-for="(item,index) in shop_img">
                    <view class="miaosha-item" v-on:click="shop_info()" v-for="index2 of 3" style="margin:5px">
                        <view class="item-pic" style="width:100px;height:100px;"><img :src="shop_img[index].src" style="width:100%;height:100%"></view>
                        <view class="item-word">{{shop_item_word[index]}}</view>
                        <view class="item-price">￥998</view>
                    </view>


                </view>
            </view>

        </view>


   

</view>



</template>

<script>
export default {

        data(){
        return{
            shop_img:[
                {src:require('../../static/shopimg_1.png')},
                {src:require('../../static/shopimg_2.png')},
                {src:require('../../static/shopimg_3.png')},
                {src:require('../../static/shopimg_4.png')},
                {src:require('../../static/shopimg_5.png')},
                {src:require('../../static/shopimg_6.png')},
                {src:require('../../static/shopimg_7.png')},
                {src:require('../../static/shopimg_9.png')}
            ],
            shop_item_word:[
                "宠物托运上门服务全国空运猫猫狗狗航空运输铁路汽运随机手续运输",
                "不锈钢狗牌项链 钛钢宠物身份牌挂牌定做 广告促销小礼品定制logo",
                "出售家养可爱粘人其它宠物品种齐全149",
                "四季通用狗窝垫子夏天凉席睡垫泰迪柯基冰垫金毛凉窝夏季宠物用品",
                "客厅猫窝边几一体猫家具猫笼猫舍四季通用实木沙发边柜宠物狗窝",
                "狗狗牵引绳自动伸缩遛狗绳狗链子中型小型犬泰迪博美柯基宠物用品",
                "狗狗磨牙棒除口臭骨头幼犬补钙咬胶去泰迪耐咬玩具零食小狗洁齿棒",
                "狗狗牵引绳狗链狗绳泰迪狗链子狗绳子小型犬胸背带遛狗绳宠物用品"
            ]
        }

    },
    

    onLoad(){
console.log("create");

uni.setStorage({
                key:'swiper_info',
                data:21123123,
                success:()=>{
                    console.log('存入成功')
                }
            })
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