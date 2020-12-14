<template>



<view>     
        <view class="mine-picture-text">我的头像</view>

        <view class="chooseImg" @tap="openChooseImg" style="width:40px;height:40px;border-radius: 50%;">
        <text v-if="!imgUrl">+</text>
        <image v-else :src="imgUrl" style="width:40px;height:40px;border-radius: 50%;"></image> 
        </view>

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

<view class="uni-tab-bar" style="height:300px">

<swiper :current="tabIndex" @change="tabChange" style="height:300px">

<swiper-item v-for="(content,index) in contentList" :key="index"  >

    <view  style="height:1000px;width:100%" v-if="tabIndex===2">
                <view class="uni-list">
                    系统设置
                    <view class="uni-list-cell" hover-class="uni-list-cell-hover" >
                        <view class="uni-list-cell-navigate uni-navigate-right">
                            {{listPersonalInfo[0]}}
                        </view>
                    </view>

                                        <view class="uni-list-cell" hover-class="uni-list-cell-hover" >
                        <view class="uni-list-cell-navigate uni-navigate-right">
                            {{listPersonalInfo[1]}}
                        </view>
                    </view>

                                        <view class="uni-list-cell" hover-class="uni-list-cell-hover" >
                        <view class="uni-list-cell-navigate uni-navigate-right">
                            {{listPersonalInfo[2]}}
                        </view>
                    </view>

                                        <view class="uni-list-cell" hover-class="uni-list-cell-hover" >
                        <view class="uni-list-cell-navigate uni-navigate-right">
                            {{listPersonalInfo[3]}}
                        </view>
                    </view>

                                                            <view class="uni-list-cell" hover-class="uni-list-cell-hover" >
                        <view class="uni-list-cell-navigate uni-navigate-right">
                            {{listPersonalInfo[4]}}
                        </view>
                    </view>
                </view>
                

                
    </view>

    <view  style="height:200px;width:200px;" v-if="tabIndex===1">
                <view class="uni-list">
                    我的消息
                    <view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item2,index2) in list" :key="index2">
                        <view class="uni-list-cell-navigate uni-navigate-right">
                            {{item2}}
                        </view>
                    </view>
                </view>
    </view>

    <view  style="height:100%;width:80%" v-if="tabIndex===0">
            <view class="uni-list" style="height:120%;width:100%" >
                个人信息
                <view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item3,index3) in listPersonalInfo" :key="index3">
                    <view class="uni-list-cell-navigate uni-navigate-right">
                        {{item3}}
                    </view>
                </view>
            </view>
    </view>



      

</swiper-item>


</swiper>




</view>

<view class="jifen" style="width:100%;height:200px;font-size:20px">
    我的积分：{{jifen}}
</view>


</view>

</template>

<script>



export default {



data() {






return {

    jifen:0,
     list:[1,2,3,4],
     listPersonalInfo: ['昵称','签名','地区','性别','退出登陆'],
    imgUrl:"",


    

tabIndex: 0, //选中标签栏的序列

contentList: [

"您当前暂未发布视频哦",

"积分：0",
"敬请期待",
"4"



],

tabBars:[

{

name: '个人信息',

id: 'publish'

},

{

name: '我的消息',

id: 'score'

},

{

name: '系统设置',

id: 'setting'

},
{

name: '4',

id: 'four'

}

],

swiperHeight: 0

}

},

components:{

},

onLoad() {

    this.getList();

},

methods: {


            getList() {
                uni.request({
                    url: 'http://localhost:3000/data3', 
                    success: (res) => {
                        console.log(res.data);
                         this.jifen =res.data;
                    }
                });
            },

    			openChooseImg(){
                console.log("open")
				uni.chooseImage({
				    count: 1, //默认9
				    sizeType: ['compressed'], //可以指定是原图还是压缩图，默认二者都有
				    sourceType: ['album','camera'], //从相册选择，和摄像头功能，默认二者都有
				    success: res=> {
						console.log(res)     
						/*res.tempFilePaths[0]是获取到的第一个数据的blob地址，将他赋值给数据区的imgUrl*/
						this.imgUrl=res.tempFilePaths[0]
						console.log(this.imgUrl)
				    }
				});
			},

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
