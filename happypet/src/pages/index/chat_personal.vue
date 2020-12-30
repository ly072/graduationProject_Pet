<template>
    <view class="bgConston">
        <view class="userSession" style="1000px">
			<view v-for="(item,index) in chat_info">

            <view class="userH"  v-show="chat_info[index].user_chat == 0">
                <view class="userImg">
                    <image src="../../static/logo.png" mode="scaleToFill"></image>
                </view>
                <view class="userType">
                    <view class="userN">
                        <text>{{chat_info[index].nichen}}</text>
                        <text>{{chat_info[index].date}}</text>
                    </view>
                    <view class="textType">	
                        <text>{{chat_info[index].content}}</text>
                    </view>


                </view>
            </view>

			<view class="userH" v-show="chat_info[index].user_chat == 1" style="flex-direction:row-reverse;">
				<view class="userImg">
                    <image src="../../static/logo.png" mode="scaleToFill"></image>
                </view>
                <view class="userType">
                    <view class="userN">
                        <text>你</text>
                        <text>{{chat_info[index].date}}</text>
                    </view>
                    <view class="textType">
                        <text>{{chat_info[index].content}}</text>
                    </view>


                </view>
 </view>

            </view>


        </view>
		<view style="height:100px"></view>

        <view class="userInput">
            <input type="text" placeholder="文明发言" :value="input_value" @input="onKeyInput" >
            <view class="sumText" @click="submit(e)">发送</view>
        </view>
    </view>
</template>

<script>
	import {
		mapState
	} from 'vuex'
	export default {
		data() {
			return {
				abosultPaht: "../../",
				
				input_value:"哈哈哈",
				chat_info:[
					{
						"user_chat":"0",
						"nichen":"小红",
						"date":"2020-5-20",
						"content":"你好，欢迎订购最新的产品"

						
					},
										{
						"user_chat":"1",
						"nichen":"小黄",
						"date":"2020-5-20",
						"content":"你好，欢迎订购最新的产品"

						
					}
				]
				
			}
		},
		userContextItem:[{
			userId:1,
			meId:"",
			userName:"纵横天下",
			userImg:"../static/nan.png",
			type:"text",
			context:"你好，请问有什么可以帮助你的么？",
			time:new Date().getTime()
		}],
		onLoad(){
			uni.getSystemInfo({
				success:(res)=>{
					let height=res.windowHeight -uni.upx2px(100);
					//this.sHeight=height;
				}
			})
		},
		methods:{


			onKeyInput: function(event) {
                this.input_value= event.detail.value
            },
			
			submit: function(e){
				console.log('yellow')

				var arr  =
				{
									"user_chat":"1",
									"nichen":"你",
									"date":"2020-5-20",
									"content":this.input_value
				}

				this.chat_info.push(arr);
				this.input_value="";

				
				
				

			}
		},

		props: ['message', 'id'],
		computed: mapState(['user'])
	}
</script>

<style>

	.bgConston{
		width:100%;
		height:100%;
		background-color: #F8F8F8 ;
		margin:0;
		padding:0;
	}
	.userSession{
		width:100%;
		height:atuo;
		border-top: 1upx solid #EDEDED;
		overflow: auto;
	}

	.userH{
		width:80%;
		height:auto;
		display:flex;
		flex:1;
		flex-wrap:wrap;
		padding:20px;
	}
	.userMe{
		width:95%;
		height:auto;
		display:flex;
		flex:1;
		flex-wrap:wrap;
		padding:20px;
		justify-content:flex-start;
		flex-direction:row-reverse;
		text-align:right;

	}

	.userImg{
		width:70upx;
		height:70upx;
		display:flex;
		justify-content:center;
		align-items:center;


	}
	.userImg>image{
		width:65upx;
		height:65upx;
		border-radius:100%;
	}
	.userType{
		display:flex;
		justify-content: center;
		flex-direction: column;
		padding:10upx;

	}
	.userN{
		height:50upx;
		display:flex;
		justify-content: space-around;
	}
	.userN>text{
		height:50upx;
		min-height:100upx;
		color:#666;
	}
	.textType{
		max-width:400upx;
		background-color:#FFFFFF;
		border-radius:10upx;
		box-shadow: 3upx 3upx 3upx 3upx #E3E3E3;
	}
	.textType>text{
		font-size:28upx;
		color:#666;
	}
	.imgType{
		max-width: 300upx;
		max-height: 420upx;
		display: flex;
		justify-content: center;
		align-items: center;
		background-color:#ffffff;
		border-radius: 20upx;
		box-shadow: 3upx 3upx 3upx 3upx #E3E3E3;
		display:flex;
		align-items:center;
		justify-content:center;

	}

	.imgType>image{
		width:250upx;
		height:350upx;
		padding:20upx;

	}


	.videoType{
		width:300upx;
		height:400upx;
		display:flex;
		justify-content: center;
		align-items: center;
		background-color:#ffffff ;
		border-radius: 20upx;
		box-shadow: 3upx 3upx 3upx 3upx #e3e3e3;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.videoType>video{
		width:270upx;
		height:370upx;
	}

	.userInput{
		height:100upx;
		position:fixed;
		bottom:0;
		left:0;
		right:0;
		padding:0 10px;
		display: flex;
		justify-content: space-around;
		align-items: center;
		box-shadow: 0 0 5upx 0 #e3e3e3;
	}

	.userInput>input{
		height:50upx;
		background:#f4f5f6;
		border-radius:15upx;
		padding: 10upx 10upx;
		flex:1;
		margin-right: 20upx;
		font-size: 28upx;
	}
	.userInput>view{
		width:120upx;
		font-size:24upx;
		color:#ffffff;
		height:60upx;
		background-color:#e80080;
		border: radius 20upx;
		text-align: center;
		line-height:60upx;
	}



	.m-item {
		display: flex;
		flex-direction: row;
		padding-top: 40px;
	}
	.m-left {
		display: flex;
		width: 120px;
		justify-content: center;
		align-items: flex-start;
	}
	.m-content {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		word-break: break-all;
	}
	.m-right {
		display: flex;
		width: 120px;
		justify-content: center;
		align-items: flex-start;
	}
	.head_icon {
		width: 80px;
		height: 80px;
	}
	.m-content-head {
		position: relative;
	}
	.m-content-head-right {
		display: flex;
		justify-content: flex-end;
	}
	.m-content-head-home {
		text-align: left;
		background: #1482d1;
		border: 1px #1482d1 solid;
		border-radius: 20px;
		padding: 20px;
		color: white;
	}
	.m-content-head-home:before {
		border: 15px solid transparent;
		border-right: 15px solid #1482d1;
		left: -26px;
		width: 0;
		height: 0;
		position: absolute;
		content: ' '
	}
	.m-content-head-customer {
		border: 1px white solid;
		background: white;
		border-radius: 20px;
		padding: 20px;
	}
	.m-content-head-customer:after {
		border: 15px solid transparent;
		border-left: 15px solid white;
		top: 20px;
		right: -26px;
		width: 0;
		height: 0;
		position: absolute;
		content: ' '
	}
</style>