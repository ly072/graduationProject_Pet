<template>

<view>

<!--顶部导航栏-->

<view class="uni-tab-bar">

<scroll-view scroll-x class="uni-swiper-tab">

<block v-for="(tabBar,index) in tabBars" :key="index">

<view class="swiper-tab-list" :class="{'active': tabIndex==index}" @tap="toggleTab(index)">

{{tabBar.name}}

<view class="swiper-tab-line">

</view>

</view>

</block>

</scroll-view>

</view>

<!--内容区-->

<view class="uni-tab-bar">

<swiper :current="tabIndex" @change="tabChange">

<swiper-item v-for="(content,index) in contentList" :key="index" >

<view class="swiper-item">{{content}}</view>

</swiper-item>

</swiper>

</view>

</view>

</template>

<script>

export default {

data() {

return {

tabIndex: 0, //选中标签栏的序列

contentList: [

"您当前暂未发布视频哦",

"积分：0",
"敬请期待"



],

tabBars:[

{

name: '发布',

id: 'publish'

},

{

name: '积分',

id: 'score'

},

{

name: '设置',

id: 'setting'

}

],

swiperHeight: 0

}

},

components:{

},

onLoad() {

},

methods: {

toggleTab(index){

console.log(index)

this.tabIndex = index

},

//滑动切换swiper

tabChange(e){

console.log(e.detail)

const tabIndex = e.detail.current

this.tabIndex = tabIndex

}

}

}

</script>

<style>

.swiper-tab-list{

color: #969696;

font-weight: bold;

}

.uni-tab-bar .active{

color: #343434;

}

.active .swiper-tab-line{

border-bottom: 6upx solid #FEDE33;

width: 70upx;

margin: auto;

border-top: 6upx solid #FEDE33;

border-radius: 20upx;

}

.uni-swiper-tab{

border-bottom: 1upx solid #eeeeee;

}

</style>
