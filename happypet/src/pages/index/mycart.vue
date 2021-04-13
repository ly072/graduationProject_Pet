<template>
<view class="content">


            <view class="ding">顶部实现</view>
        <view :class="{'st':true,'sticky-fixed':isF}">我是浮动栏</view>
        <view class="xiala">文章内容</view>




        <view class="uni-title" style="width:100%">
            <ul style="width:80%;height:50px;border-bottom:1px grey solid">
                <li><strong  style="font-size:22px">购物车</strong></li>
                <li><strong>我常买</strong></li>
                <li style="float:right"><strong>编辑</strong></li>
                
            </ul>
            
        </view>


   

</view>



</template>

<script>
  export default {
        data() {
            return {
                yuanH: uni.upx2px(300),
                isF: false,
            };
        },
        onPageScroll(e) {
            //#ifdef H5
            this.isF = true
            // #endif
            // #ifndef H5
            if (this.yuanH > e.scrollTop) {
                this.isF = false
            } else {
                this.isF = true
            }
            // #endif
        },
    };
</script>


<style lang="scss" scoped>
    .uni-title ul{
        list-style: none;
    }

    .uni-title li{
        float:left;
    }


        .ding {
        height: 300rpx;
        background-color: aquamarine;
    }

    .st {
        height: 100rpx;
        width: 750rpx;
        background-color: #fff;
        z-index: 999;
        /* top: 300upx; */
    }

    .sticky-fixed {
        /* #ifdef H5 */
        position: sticky;
        top: 44px;
        /* #endif */
        /* #ifndef H5 */
        position: fixed;
        top: 0;
        /* #endif */
        z-index: 999;
    }

    .xiala {
        height: 2500px;
        background-color: #eee;
        padding-top: 100rpx;
    }
</style>