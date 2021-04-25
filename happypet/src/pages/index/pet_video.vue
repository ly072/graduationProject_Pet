<template>
<view class="content">
        <view v-for="index in 10">
        <view class="interest-banner" style="height:80px;display:flex;flex-direction:row">
			<view class="interest-head-icon" style="width:32%">

				<image src="../../static/img/user_icon.jpg" style="width:60px;height:60px;margin:10px;border-radius:90px"></image>
			</view>
			<view class="interest-user-info"  style="width:100%;display:flex;
			flex-direction:column">
				<view class="interest-user-title" style="height:100%;">是我呀</view>
				<view class="interest-user-name" style="height:100%;">2020年9月20日</view>
			</view>
		</view>
		<view class="interest-text">这个是我和狗狗的故事</view>
		<view class="interest-image-container">
            <swiper class="swiper" :circular="circular" :vertical="true" @change="onSwiperChange">
                <swiper-item v-for="item in videoList" :key="item.id">
                    <video class="video" :id="item.id" :ref="item.id" :src="item.src" :controls="true" :loop="true"
                        :show-center-play-btn="true"></video>
                </swiper-item>
            </swiper>
		</view>
					<view class="grey-divider" style="border:solid 1px #dddddd;width:90%;margin:5%"></view>


        </view>



   

</view>



</template>

<script>
    const videoData = [{
            src: 'https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/hellouniapp/hello-nvue-swiper-vertical-01.mp4'
        },
        {
            src: 'https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/hellouniapp/hello-nvue-swiper-vertical-02.mp4'
        },
        {
            src: 'https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/hellouniapp/hello-nvue-swiper-vertical-03.mp4'
        },
        {
            src: 'https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/hellouniapp/hello-nvue-swiper-vertical-01.mp4'
        },
        {
            src: 'https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/hellouniapp/hello-nvue-swiper-vertical-02.mp4'
        },
        {
            src: 'https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/hellouniapp/hello-nvue-swiper-vertical-03.mp4'
        }
    ];
export default {
    data(){
        return {
            videoDataList: [],
            
                            circular: true,
                videoList: [{
                        id: "video0",
                        src: "",
                        img: ""
                    },
                    {
                        id: "video1",
                        src: "",
                        img: ""
                    },
                    {
                        id: "video2",
                        src: "",
                        img: ""
                    }
                ]
        }
    },

    
    

    onLoad(){
console.log("create");


    },
            onReady() {
            this.init();
            this.getData();
        },
    methods:{
            init() {
                this._videoIndex = 0;
                this._videoContextList = [];
                for (var i = 0; i < this.videoList.length; i++) {
                    this._videoContextList.push(uni.createVideoContext('video' + i, this));
                }
                this._videoDataIndex = 0;
            },
            getData(e) {
                this.videoDataList = videoData;
                setTimeout(() => {
                    this.updateVideo(true);
                }, 200)
            },
            updateVideo(isNext) {
                this.$set(this.videoList[this._videoIndex], 'src', this.videoDataList[this._videoDataIndex].src);
                this.$set(this.videoList[this.getNextIndex(isNext)], 'src', this.videoDataList[this.getNextDataIndex(isNext)].src);
                setTimeout(() => {
                    this._videoContextList[this._videoIndex].play();
                }, 200);
                console.log("v:" + this._videoIndex + " d:" + this._videoDataIndex + "; next v:" + this.getNextIndex(
                    isNext) + " next d:" + this.getNextDataIndex(isNext));
            },
            topSwiperTab(e) {
            var that = this;
            this.topSwiperIndex = Number(e.target.current);
    }
    ,
            change(e) {
				// e.detail.value在安卓手机上可能是String类型，后续修复后要修改
				this.checked = e.detail.value === 'false' || !e.detail.value ? false : true
			},
			switchActive(index) {
				this.activeIndex = index
			}

    }
}
</script>


<style lang="scss" scoped>

</style>