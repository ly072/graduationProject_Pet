<template>
	<view class="content" style="background:#ffffff">
		<view class="title">{{title}}</view>
		<view class="art-content">
			<rich-text class="richText" :nodes="strings"></rich-text>
		</view>

	<view class="comment" style="background:#ffffff;margin-top:100px">
		<view class="title">0条评论</view>
		<view class="art-content" style="display:flex;align-items:center;justify-content:center">
			<img class="comment-pic" src="../../static/nocomment.png" ></img>
		</view>



		
		
	</view>

		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'人用指甲钳可以给狗狗剪指甲吗？',
				strings:'可别拿一般的指甲钳就像帮狗狗剪指甲，网上或实体店都很容易找到狗狗专用的，另外可以准备指甲粉，流血时，可以立即止血。'
			}
		},
/*		onLoad:function(e){			
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+e.newsid,  //详情页数据请求
				method: 'GET',
				data: {},
				success: res => {
					console.log(res);
					this.title = res.data.title;
					this.strings = res.data.content;  //组件渲染
				},
				fail: () => {},
				complete: () => {}
			});
		},*/
		methods: {
			
		}
	}
</script>

<style>
.content{
	padding: 10upx 2%;
	width:96%;
	flex-wrap: wrap;
	
}
.title{
	line-height: 2em;
	font-weight: 700;
	font-size: 38upx;
}
.art-content{
	line-height: 2em;
}
</style>