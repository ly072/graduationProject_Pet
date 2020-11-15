<template>
<view class="content">


    <!--头部导航条-->
		<view class="example-body">
			
			<uni-search-bar radius="100" placeholder="自定义圆角" @confirm="search" />
		</view>

    <!-- 热门搜索 -->
    <view class="hot-search" style="height:50px">
        <view class="hot-search-text" style="border-bottom:1px solid grey">热门搜索</view>

    </view>

        <!-- 历史搜索 -->
    <view class="history-search" style="height:50px">
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