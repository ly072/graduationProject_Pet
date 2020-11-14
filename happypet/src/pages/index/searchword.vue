<template>
<view class="content">


    <!--头部导航条-->
    <view class="top-banner" style="width:100%;height:100px;background-color:red">
        <!--返回箭头-->
        <view class="top-banner-back"></view>
        <!--搜索文字-->
        <view class="top-banner-text"></view>
    </view>

    <view class="search-banner" style="width:100%;height:100px">
        <input placeholder="请输入" @input="onInput" />
        <img src="" alt="" style="background-color:grey;width:100px;height:100px">
    </view>

    <!-- 热门搜索 -->
    <view class="hot-search" style="height:100px">
        <view class="hot-search-text" style="border-bottom:1px solid grey">热门搜索</view>

    </view>

        <!-- 历史搜索 -->
    <view class="history-search" style="height:100px">
        <view class="hot-search-text" style="border-bottom:1px solid grey">历史搜索</view>

    </view>
   

</view>



</template>

<script>
export default {
    

    onLoad(){
console.log("create");
    },
    methods:{
        submit(){
            console.log("hello");
            uni.navigateTo({
                url:"index"
            })
        },
        onInput(e) {
				console.log(e.detail)
				this.number = e.detail
			}
    }
}
</script>


<style lang="scss" scoped>

</style>