<template>
    <scroll-view class="content" style="width:100%;height:5000px;background:url('../../static/index_background.jpg')">
    <view class="page">
        <!-- <swiper class="swiper" :circular="circular" :vertical="true" @change="onSwiperChange">
            <swiper-item v-for="item in videoList" :key="item.id">
                <video class="video" :id="item.id" :ref="item.id" :src="item.src" :controls="false" :loop="true"
                    :show-center-play-btn="false"></video>
            </swiper-item>
        </swiper> -->
    </view>
        <view class="uni-title uni-common-mt" style="display:inline-block">
            <ul style="width:100%">
                <li><strong  style="font-size:22px">推荐</strong></li>
                <li>最新</li>
                <li>视频</li>
                <li>同城</li>
                
            </ul>
            
        </view>

        <view><uni-search-bar radius="100" placeholder="快来搜搜吧～" @confirm="search" /></view>

<view class="swiper" style="background:white">
        <swiper :interval="1000" :duration="1000" :indicator-dots="true"
     :current="topSwiperIndex" @change="topSwiperTab">
        <swiper-item v-for="(item,index) in topSwiper" :key="index">
            <view class="swiper-item">
                <image :src="item.src" mode="aspectFill" style="margin:20px"></image>
            </view>
        </swiper-item>
    </swiper>

        <!-- 自定义指示点dots -->
    <view class="dots">
        <text>{{topSwiperIndex+1}}/{{topSwiper.length}}</text>
    </view>
</view>

<!-- 推荐条 -->
<view class="advance-banner"><strong style="font-size:30px;color:#555555">最新发现</strong><span style="font-size:16px;margin:20px">惠州超可爱小猫咪   前往</span></view>



		<!-- <view class="example-body" v-show="0">
			<view v-for="(item,index) in iconClassList" :key="index" class="icon-item" @click="switchActive(index)">
				<uni-icons :type="item.name" :color="activeIndex === index?'#007aff':'#8f8f94'" size="25" />
				<text :style="{color:activeIndex === index?'#007aff':'#8f8f94'}" class="icon-item-text">{{ checked? item.unicode: item.name }}</text>
			</view>
		</view> -->
        <view class="top-list" style="display:flex;flex-direction:row;margin-top:100upx">

            <view style="margin:10px 10px;width:70px;height:70px;background-color:#227799;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello">
                <text>新闻动态</text>
            </view>

            <view style="width:70px;margin:10px 10px;height:70px;background-color:#992277;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello_video">
                <text>宠物视频</text>
            </view>

            <view style="width:70px;margin:10px 10px;height:70px;background-color:green;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello_shop">
                <text>宠物商城</text>
            </view>

            <view style="width:70px;margin:10px 10px;height:70px;background-color:blue;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello_mission">
                <text>每日任务</text>
            </view>
        </view>

                <view class="bottom-list" style="display:flex;flex-direction:row">

            <view style="margin:10px 10px;width:70px;height:70px;background-color:#22AA99;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello_knowledge">
                <text>宠物知识</text>
            </view>

            <view style="width:70px;margin:10px 10px;height:70px;background-color:#CC2277;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello_shareus">
                <text>分享我们</text>
            </view>

            <view style="width:70px;margin:10px 10px;height:70px;background-color:red;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello_cut">
                <text>寻找优惠</text>
            </view>

            <view style="width:70px;margin:10px 10px;height:70px;background-color:#992211;color:white;border-radius:20px;display:flex;align-items:center;justify-content:center" v-on:click="hello_play">
                <text>轻松一下</text>
            </view>
        </view>


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
			<image src="../../static/pet1.jpeg" style="width:100px;height:100px;margin:10px;"></image>
			<image src="../../static/pet2.jpeg" style="width:100px;height:100px;margin:10px;"></image>
		</view>
					<view class="grey-divider" style="border:solid 1px #dddddd;width:90%;margin:5%"></view>


        </view>


        <!-- 页面底部高度控制 -->
        <view style="height:200px"></view>

    </scroll-view>

    
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
        data() {
            return {

                   topSwiperIndex: 0,
        topSwiper: [
            {
                src: require('../../static/pet1.jpeg')
            },
            {
                src: require('../../static/pet2.jpeg')
            },
            {
                src: require('../../static/pet3.jpeg')
            },
            {
                src: require('../../static/pet2.jpeg')
            },
            {
                src: require('../../static/pet1.jpeg')
            }
        ] ,
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
                ],
                videoDataList: [],
                iconClassList: [{
					"name": "arrowdown",
					"unicode": "e581"
				}, {
					"name": "arrowleft",
					"unicode": "e582"
				}, {
					"name": "arrowright",
					"unicode": "e583"
				}, {
					"name": "arrowup",
					"unicode": "e580"
				}, {
					"name": "arrowthindown",
					"unicode": "e585"
				}, {
					"name": "arrowthinleft",
					"unicode": "e586"
				}, {
					"name": "arrowthinright",
					"unicode": "e587"
				}, {
					"name": "arrowthinup",
					"unicode": "e584"
				}]
            }
        },
        onLoad(e) {},
        onReady() {
            this.init();
            this.getData();
        },
        methods: {

               topSwiperTab(e) {
        var that = this;
        this.topSwiperIndex = Number(e.target.current);
    },
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
            hello: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"news"
            })
            },

            hello_video: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"swiper-vertical"
            })
            },
            hello_shop: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"petshop_index"
            })
            },
            hello_mission: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"daily_mission"
            })
            },
            hello_knowledge: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"pet_knowledge"
            })
            },
            hello_shareus: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"shareus"
            })
            },
            hello_cut: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"find_cut"
            })
            },
            hello_play: function(){
                console.log("hello")
                            uni.navigateTo({
                url:"play_index"
            })
            },
            onSwiperChange(e) {
                let currentIndex = e.detail.current;
                if (currentIndex === this._videoIndex) {
                    return;
                }

                let isNext = false;
                if (currentIndex === 0 && this._videoIndex === this.videoList.length - 1) {
                    isNext = true;
                } else if (currentIndex === this.videoList.length - 1 && this._videoIndex === 0) {
                    isNext = false;
                } else if (currentIndex > this._videoIndex) {
                    isNext = true;
                }

                if (isNext) {
                    this._videoDataIndex++;
                } else {
                    this._videoDataIndex--;
                }

                if (this._videoDataIndex < 0) {
                    this._videoDataIndex = this.videoDataList.length - 1;
                } else if (this._videoDataIndex >= this.videoDataList.length) {
                    this._videoDataIndex = 0;
                }

                this.circular = (this._videoDataIndex != 0);

                if (this._videoIndex >= 0) {
                    this._videoContextList[this._videoIndex].pause();
                    this._videoContextList[this._videoIndex].seek(0);
                }

                this._videoIndex = currentIndex;

                setTimeout(() => {
                    this.updateVideo(isNext);
                }, 200);
            },
            getNextIndex(isNext) {
                let index = this._videoIndex + (isNext ? 1 : -1);
                if (index < 0) {
                    return this.videoList.length - 1;
                } else if (index >= this.videoList.length) {
                    return 0;
                }
                return index;
            },
            getNextDataIndex(isNext) {
                let index = this._videoDataIndex + (isNext ? 1 : -1);
                if (index < 0) {
                    return this.videoDataList.length - 1;
                } else if (index >= this.videoDataList.length) {
                    return 0;
                }
                return index;
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

<style>
    /* #ifndef APP-PLUS */
    page {
        width: 100%;
        min-height: 100%;
        display: flex;
    }
    /* #endif */

    .page {
        flex: 1;
        width: 750rpx;
    }

    .swiper {
        flex: 1;
        background-color: #007AFF;
    }

    .swiper-item {
        flex: 1;
    }

    .video {
        flex: 1;
        /* #ifndef APP-PLUS */
        width: 100%;
        /* #endif */
    }

    /* 头条小程序组件内不能引入字体 */
	/* #ifdef MP-TOUTIAO */
	@font-face {
		font-family: uniicons;
		font-weight: normal;
		font-style: normal;
		src: url('~@/static/uni.ttf') format('truetype');
	}

	/* #endif */

	/* #ifndef APP-NVUE */
	page {
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		background-color: #efeff4;
		min-height: 100%;
		height: 200rpx;
	}

	view {
		font-size: 14px;
		line-height: inherit;
	}

	.example {
		padding: 0 15px 15px;
	}

	.example-info {
		padding: 15px;
		color: #3b4144;
		background: #ffffff;
	}

	.example-body {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 0;
		font-size: 14px;
		background-color: #ffffff;
	}

	/* #endif */
	.example {
		padding: 0 15px;
	}

	.example-info {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 15px;
		color: #3b4144;
		background-color: #ffffff;
		font-size: 14px;
		line-height: 20px;
	}

	.example-info-text {
		font-size: 14px;
		line-height: 20px;
		color: #3b4144;
	}


	.example-body {
		flex-direction: column;
		padding: 15px;
		background-color: #ffffff;
	}

	.word-btn-white {
		font-size: 18px;
		color: #FFFFFF;
	}

	.word-btn {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		align-items: center;
		justify-content: center;
		border-radius: 6px;
		height: 48px;
		margin: 15px;
		background-color: #007AFF;
	}

	.word-btn--hover {
		background-color: #4ca2ff;
	}


	.example-body {
		padding: 0;
		flex-direction: row;
		flex-wrap: wrap;
		/* align-items: center;
 */
		/* justify-content: center;
 */
	}

	.uni-right {
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		color: #666;
	}

	.uni-right-text {
		font-size: 28rpx;
	}

	.switch {
		transform: scale(0.8);
		margin-left: 5px;
	}

	.icon-item {
		/* #ifndef APP-NVUE */
		display: flex;
		box-sizing: border-box;
		/* #endif */
		width: 180rpx;
		padding: 30rpx 10rpx;
		text-align: center;
		flex-direction: column;
	}

	.icon-item-text {
		font-size: 24rpx;
		text-align: center;
	}

    .uni-title ul{
        list-style: none;
    }

    .uni-title li{
        float:left;
        margin-left:20px;
    }

    .top-list view,.bottom-list view{
        box-shadow:1px 2px 3px 4px #ccc ;
    }


</style>
