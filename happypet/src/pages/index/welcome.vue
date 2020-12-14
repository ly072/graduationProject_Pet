<template>
    <view class="content">
    <view class="page">
        <swiper class="swiper" :circular="circular" :vertical="true" @change="onSwiperChange">
            <swiper-item v-for="item in videoList" :key="item.id">
                <video class="video" :id="item.id" :ref="item.id" :src="item.src" :controls="false" :loop="true"
                    :show-center-play-btn="false"></video>
            </swiper-item>
        </swiper>
    </view>
        <view class="uni-title uni-common-mt">
        欢迎您使用此软件<br>
        <text>快来尝试下面的功能吧～</text>
    </view>


    <uni-section title="基础图标" type="line">
			<view class="uni-right">
				<text class="uni-right-text">显示{{ checked?' unicode':'图标名' }}</text>
				<switch :checked="checked" class="switch" @change="change" />
			</view>
	</uni-section>
		<view class="example-body" v-show="0">
			<view v-for="(item,index) in iconClassList" :key="index" class="icon-item" @click="switchActive(index)">
				<uni-icons :type="item.name" :color="activeIndex === index?'#007aff':'#8f8f94'" size="25" />
				<text :style="{color:activeIndex === index?'#007aff':'#8f8f94'}" class="icon-item-text">{{ checked? item.unicode: item.name }}</text>
			</view>
		</view>

            <view style="width:100px;height:100px;background-color:#181818;color:white" v-on:click="hello">
                <text>新闻动态</text>
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
        data() {
            return {
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
		height: auto;
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
</style>
