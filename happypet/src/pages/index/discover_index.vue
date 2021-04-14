<template>
<view class="content">
    <!--头部导航栏-->
    <view class="top-banner" style="background-color:#99CCFF;height:80px;width:100%;display:flex;flex-direction:row;margin-bottom:20px;box-shadow:1px 2px 30px 4px #aaf	;">
        <view class="top-banner-item" style="width:100px;height:40px;margin:20px">
            <view class="top-banner-item-title" >地区</view>
            <view class="top-banner-item-content" style="color:white">上海市</view>
        </view>
        <view class="top-banner-item" style="width:100px;height:40px;margin:20px">
            <view class="top-banner-item-title" >物种</view>
            <view class="top-banner-item-content" style="color:white">全部</view>
        </view>
        <view class="top-banner-item" style="width:100px;height:40px;margin:20px">
            <view class="top-banner-item-title" >话题类型</view>
            <view class="top-banner-item-content" style="color:white">全部</view>
        </view>

        

    </view>

<view>
		<view v-if="popMenu && (leftBottom||rightBottom||leftTop||rightTop)" :class="{
        'uni-fab--leftBottom': leftBottom,
        'uni-fab--rightBottom': rightBottom,
        'uni-fab--leftTop': leftTop,
        'uni-fab--rightTop': rightTop
      }" class="uni-fab">
			<view :class="{
          'uni-fab__content--left': horizontal === 'left',
          'uni-fab__content--right': horizontal === 'right',
          'uni-fab__content--flexDirection': direction === 'vertical',
          'uni-fab__content--flexDirectionStart': flexDirectionStart,
          'uni-fab__content--flexDirectionEnd': flexDirectionEnd,
		  'uni-fab__content--other-platform': !isAndroidNvue
        }" :style="{ width: boxWidth, height: boxHeight, backgroundColor: styles.backgroundColor }" class="uni-fab__content" elevation="5">
				<view v-if="flexDirectionStart || horizontalLeft" class="uni-fab__item uni-fab__item--first" />
				<view v-for="(item, index) in content" :key="index" :class="{ 'uni-fab__item--active': isShow }" class="uni-fab__item" @click="_onItemClick(index, item)">
					<image :src="item.active ? item.selectedIconPath : item.iconPath" class="uni-fab__item-image" mode="widthFix" />
					<text class="uni-fab__item-text" :style="{ color: item.active ? styles.selectedColor : styles.color }">{{ item.text }}</text>
				</view>
				<view v-if="flexDirectionEnd || horizontalRight" class="uni-fab__item uni-fab__item--first" />
			</view>
		</view>
		<view :class="{
		  'uni-fab__circle--leftBottom': leftBottom,
		  'uni-fab__circle--rightBottom': rightBottom,
		  'uni-fab__circle--leftTop': leftTop,
		  'uni-fab__circle--rightTop': rightTop,
		  'uni-fab__content--other-platform': !isAndroidNvue
		}" class="uni-fab__circle uni-fab__plus" :style="{ 'background-color': styles.buttonColor }" @click="_onClick">
			<view class="fab-circle-v" :class="{'uni-fab__plus--active': isShow}"></view>
			<view class="fab-circle-h" :class="{'uni-fab__plus--active': isShow}"></view>
		</view>
	</view>
	



	<view class="goto-my-discover">
		<button class="mini-btn" type="primary" size="mini">写写我的动态</button>
	</view>


	<view class="personal-interest" style="width:95%;height:100%;margin:10px;box-shadow:1px 2px 3px 4px #ccc ;" v-for="item in 3">
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

		<view class="thumb-container" style="height:100px;background-color:#FFFAFA">
			<view class="interest-comment" style="height:80px;display:flex
			;flex-direction:row">
				<view class="interest-head-icon" style="width:50%">

					<image src="../../static/shuijiao.jpg" style="width:60px;height:60px;margin:10px;border-radius:90px"></image>
				</view>
				<view class="interest-user-info"  style="width:100%;display:flex;
				flex-direction:column">
					<view class="interest-user-title" style="height:100%;"><text style="color:grey">评论：</text>好可爱呀！</view>
					<view class="interest-user-name" style="height:100%;">2020年9月20日</view>
				</view>

			</view>
		</view>
		<view style="margin:10px 0px;width:100%;height:5px;"></view>

		<view class="thumb-container" style="height:100%;background-color:#FFFAFA;">
			<view class="interest-comment" style="height:80px;display:flex
			;flex-direction:column">
				<view class="interest-head-icon" style="width:50%" v-if="0">

					<image src="../../static/shuijiao.jpg" style="width:60px;height:60px;margin:10px;border-radius:90px"></image>
				</view>
				<view class="interest-user-info"  style="width:100%;display:flex;flex-direction:row">
					<view class="interest-user-title" style="height:50%;"><text style="color:grey">请评论：</text><input class="comment-input" placeholder="文明发言" style="background-color:#eeeeee;border-radius:20px"></view>
					<button style="width:200upx;height:50%;margin:20px 20px"class="mini-btn" type="primary" size="mini" v-on="add_commit(e)">发送</button>
				</view>

			</view>
		</view>


	</view>











   


</view>



</template>

<script>

	let platform = 'other'
	// #ifdef APP-NVUE
	platform = uni.getSystemInfoSync().platform
	// #endif	
export default {
    		props: {
			pattern: {
				type: Object,
				default () {
					return {}
				}
			},
			horizontal: {
				type: String,
				default: 'left'
			},
			vertical: {
				type: String,
				default: 'bottom'
			},
			direction: {
				type: String,
				default: 'horizontal'
			},
			content: {
				type: Array,
				default () {
					return []
				}
			},
			show: {
				type: Boolean,
				default: false
			},
			popMenu: {
				type: Boolean,
				default: true
			}
		},
    
    data(){
        		return{
									fabShow: false,
				isShow: false,
				isAndroidNvue: platform === 'android',
				styles: {
					color: '#3c3e49',
					selectedColor: '#007AFF',
					backgroundColor: '#fff',
					buttonColor: '#3c3e49'
				},
			heartList:false,
			height:"",
			textarea:false,
			placeholder:'请输入内容',
			input:""
		}


    },
    onLoad(){
console.log("create");
    },computed: {
			contentWidth(e) {
				return (this.content.length + 1) * 55 + 10 + 'px'
			},
			contentWidthMin() {
				return 55 + 'px'
			},
			// 动态计算宽度
			boxWidth() {
				return this.getPosition(3, 'horizontal')
			},
			// 动态计算高度
			boxHeight() {
				return this.getPosition(3, 'vertical')
			},
			// 计算左下位置
			leftBottom() {
				return this.getPosition(0, 'left', 'bottom')
			},
			// 计算右下位置
			rightBottom() {
				return this.getPosition(0, 'right', 'bottom')
			},
			// 计算左上位置
			leftTop() {
				return this.getPosition(0, 'left', 'top')
			},
			rightTop() {
				return this.getPosition(0, 'right', 'top')
			},
			flexDirectionStart() {
				return this.getPosition(1, 'vertical', 'top')
			},
			flexDirectionEnd() {
				return this.getPosition(1, 'vertical', 'bottom')
			},
			horizontalLeft() {
				return this.getPosition(2, 'horizontal', 'left')
			},
			horizontalRight() {
				return this.getPosition(2, 'horizontal', 'right')
			}
		},
		watch: {
			pattern(newValue, oldValue) {
				//console.log(JSON.stringify(newValue))
				this.styles = Object.assign({}, this.styles, newValue)
			}
		},		
		created() {
			this.isShow = this.show
			if (this.top === 0) {
				this.fabShow = true
			}
			// 初始化样式
			this.styles = Object.assign({}, this.styles, this.pattern)
		},
    methods:{
		//在这写功能函数
		
					_onClick() {

				console.log("ccc")
								uni.navigateTo({  //跳转页面
					url: 'user_post_dailylife',    //url加id
				});
				// this.$emit('fabClick')
				// if (!this.popMenu) {
				// 	return
				// }
				// this.isShow = !this.isShow
			},
			open() {
				this.isShow = true
			},
			close() {
				this.isShow = false
			},
			/**
			 * 按钮点击事件
			 */
			_onItemClick(index, item) {
				this.$emit('trigger', {
					index,
					item
				})
			},
			/**
			 * 获取 位置信息
			 */
			getPosition(types, paramA, paramB) {
				if (types === 0) {
					return this.horizontal === paramA && this.vertical === paramB
				} else if (types === 1) {
					return this.direction === paramA && this.vertical === paramB
				} else if (types === 2) {
					return this.direction === paramA && this.horizontal === paramB
				} else {
					return this.isShow && this.direction === paramA ? this.contentWidth : this.contentWidthMin
				}
			},

        submit(){
            console.log("hello");
            uni.navigateTo({
                url:"searchword"
            })
        },

		add_commit(e)
		{


			
		},

        		// 键盘高度发生变化
		keyboardheightchange(e){
			this.height=e.detail.height-2;
			if(e.detail.height==0){
				this.inputShow(1);
			}
		},
		//回复
		nickName(item){
			this.textarea=true;
			this.placeholder='回复：'+item;
		},
		//关闭键盘
		inputShow(a){
			if(a==1){
				this.textarea=false;
			}else{
				this.textarea=true;
				this.placeholder="请输入内容"
			}
		},
		//笔芯
		showHeart(a){
			if(a==1){
				this.heartList=false
			}else{
				this.heartList=true
			}
		}

    }
}
</script>


<style lang="scss" scoped>

	.uni-fab {
		position: fixed;
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		justify-content: center;
		align-items: center;
		z-index: 10;
	}

	.uni-fab--active {
		opacity: 1;
	}

	.uni-fab--leftBottom {
		left: 5px;
		bottom: 20px;
		/* #ifdef H5 */
		bottom: calc(20px + var(--window-bottom));
		/* #endif */
		padding: 10px;
	}

	.uni-fab--leftTop {
		left: 5px;
		top: 30px;
		/* #ifdef H5 */
		top: calc(30px + var(--window-top));
		/* #endif */
		padding: 10px;
	}

	.uni-fab--rightBottom {
		right: 5px;
		bottom: 20px;
		/* #ifdef H5 */
		bottom: calc(20px + var(--window-bottom));
		/* #endif */
		padding: 10px;
	}

	.uni-fab--rightTop {
		right: 5px;
		top: 30px;
		/* #ifdef H5 */
		top: calc(30px + var(--window-top));
		/* #endif */
		padding: 10px;
	}

	.uni-fab__circle {
		position: fixed;
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		justify-content: center;
		align-items: center;
		width: 55px;
		height: 55px;
		background-color: #3c3e49;
		border-radius: 55px;
		z-index: 11;
	}

	.uni-fab__circle--leftBottom {
		left: 15px;
		bottom: 30px;
		/* #ifdef H5 */
		bottom: calc(30px + var(--window-bottom));
		/* #endif */
	}

	.uni-fab__circle--leftTop {
		left: 15px;
		top: 40px;
		/* #ifdef H5 */
		top: calc(40px + var(--window-top));
		/* #endif */
	}

	.uni-fab__circle--rightBottom {
		right: 15px;
		bottom: 30px;
		/* #ifdef H5 */
		bottom: calc(30px + var(--window-bottom));
		/* #endif */
	}

	.uni-fab__circle--rightTop {
		right: 15px;
		top: 40px;
		/* #ifdef H5 */
		top: calc(40px + var(--window-top));
		/* #endif */
	}

	.uni-fab__circle--left {
		left: 0;
	}

	.uni-fab__circle--right {
		right: 0;
	}

	.uni-fab__circle--top {
		top: 0;
	}

	.uni-fab__circle--bottom {
		bottom: 0;
	}

	.uni-fab__plus {
		font-weight: bold;
	}

	.fab-circle-v {
		position: absolute;
		width: 3px;
		height: 31px;
		left: 26px;
		top: 12px;
		background-color: white;
		transform: rotate(0deg);
		transition: transform 0.3s;
	}

	.fab-circle-h {
		position: absolute;
		width: 31px;
		height: 3px;
		left: 12px;
		top: 26px;
		background-color: white;
		transform: rotate(0deg);
		transition: transform 0.3s;
	}

	.uni-fab__plus--active {
		transform: rotate(135deg);
	}

	.uni-fab__content {
		/* #ifndef APP-NVUE */
		box-sizing: border-box;
		display: flex;
		/* #endif */
		flex-direction: row;
		border-radius: 55px;
		overflow: hidden;
		transition-property: width, height;
		transition-duration: 0.2s;
		width: 55px;
		border-color: #DDDDDD;
		border-width: 1rpx;
		border-style: solid;
	}

	.uni-fab__content--other-platform {
		border-width: 0px;
		box-shadow: 0 0 5px 2px rgba(0, 0, 0, 0.2);
	}

	.uni-fab__content--left {
		justify-content: flex-start;
	}

	.uni-fab__content--right {
		justify-content: flex-end;
	}

	.uni-fab__content--flexDirection {
		flex-direction: column;
		justify-content: flex-end;
	}

	.uni-fab__content--flexDirectionStart {
		flex-direction: column;
		justify-content: flex-start;
	}

	.uni-fab__content--flexDirectionEnd {
		flex-direction: column;
		justify-content: flex-end;
	}

	.uni-fab__item {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 55px;
		height: 55px;
		opacity: 0;
		transition: opacity 0.2s;
	}

	.uni-fab__item--active {
		opacity: 1;
	}

	.uni-fab__item-image {
		width: 25px;
		height: 25px;
		margin-bottom: 3px;
	}

	.uni-fab__item-text {
		color: #FFFFFF;
		font-size: 12px;
	}

	.uni-fab__item--first {
		width: 55px;
	}


.friend{
	background-color: #FFFFFF;
    width:500px;
    
	 .input{
		width: 100%;
		display: flex;
		position: fixed;
		align-items: center;
		background-color: #F2F2F2;
		padding: 10rpx 0;
		left: 0;
		textarea{
			margin-left: 10rpx;
			min-height: 60rpx;
			height: auto;
			width: 80%;
			background-color: #FFFFFF;
			font-size: 26rpx;
			padding: 5rpx;
		}
		button{
			background-color: #07c160;
			border:none !important;
			font-size: 25rpx;
			padding: 0;
			width: 100rpx;
			height: 60rpx;
			color: #FFFFFF;
		}
	 }
	.buzan{
		display: flex;
		align-items: center;
	    image{
			width:40rpx;
			height:40rpx;
			margin-left: 20rpx;
		}
		view{
			width: 40rpx;height: 0;
		}
		padding-bottom: 10rpx;
		border-bottom: 1px solid #CCCCCC;
		.message{
			width: 45rpx;
			height: 45rpx;
		}
	}
	.discuss{
		background-color: #F2F2F2;
		border-radius: 10rpx;
		width: 530rpx;
		margin-top: 20rpx;
		.talk{
			font-size: 25rpx;
			padding: 0 10rpx 10rpx 10rpx;
			view{
				margin-top: 10rpx;
			}
			.talk-set{
				font-size: 23rpx;
				.title{
					color: #1296db;
					font-size: 25rpx;
				}
			}
		}
		.heart-people{
			display: flex;
			flex-wrap: wrap;
			padding:0 0 10rpx 10rpx;
		.heart{
			display: flex;
			align-items: center;
			justify-content: center;
			margin-right:10rpx;
			margin-top: 10rpx;
			image{
				width: 20rpx;
				height: 20rpx;
			}
			color: #1296db;
			text{
				font-size: 20rpx;
				margin-left: 5rpx;
			}
		}
	  }
	}
	  .show{
		 display: flex;
		.friend-right{
			width: 550rpx;
			.title{
				font-size:30rpx;
				font-weight: 700;
				margin-top: 15rpx;
			}
			.content{
				font-size: 25rpx;
				color: #323233;
				margin-top: 10rpx;
			}
		}
		.friend-left{
			$w:80rpx;
			width: $w;
			min-width: $w;
			min-height: $w;
			height: $w;
			border-radius: 50%;
			margin: 10rpx 10rpx 10rpx 0;
		}
		.image{
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			flex-direction: row;
			width: 488rpx;
			margin: 10rpx 0;
			image{
				margin-top: 5rpx;
				width: 160rpx;
				height: 160rpx;				
			}
		}
	  }
	}

span{
    font-size: 0.6em;
}
  .content{
      
      display:flex;
      flex-direction: column;
      align-items: center;
      
  }



.bottom-banner{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 100px;
    position: absolute;
    background:black;
    bottom:0;
    overflow: hidden;
}


span{
    font-size: 0.6em;
}
  .content{
      
      display:flex;
      flex-direction: column;
      align-items: center;
      
  }
  .top-bar{
      height:90rpx;
      width:100%;
      box-sizing: border-box;
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;

      background: #FF0000;
      border-bottom: grey;

  }
  .login-title{
      margin: 50px;
  }
  .app-form{
      height:300px;
      width:70%;
    .app-form-user{
        margin: 50px;
        border-bottom: thick double #aa0000;
        
    }
    .app-form-password{
        margin: 50px;
        border-bottom: thick double #aa0000
    }
    .app-form-loginbtn{
        margin: 50px;
    }
  }
  

</style>
  
  
  

