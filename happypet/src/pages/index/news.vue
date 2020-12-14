<template>
	<view class="content">   
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in news" :key="index"
			 @tap="openinfo" :data-newsid="item.post_id">
				<view class="uni-media-list">
					<image class="uni-media-list-logo" :src="item.author_avatar"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top">{{item.title}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis">{{item.content}}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {			
				news:[]
			}
		},
		onLoad:function() {  //生命周期只执行一次
			uni.showLoading({
				title: '加载中...',  //数据加载转转圈圈操作
			});
           uni.request({   //数据请求
           	url: 'https://unidemo.dcloud.net.cn/api/news',
           	method: 'GET',
           	data: {},
           	success: res => {
				console.log(res);
				this.news=res.data;
				uni.hideLoading(); // 关闭转圈圈操作
			},
           	fail: () => {},
           	complete: () => {}
           });		   
		},
		methods: {   //方法
            openinfo(e){				
				var newsid = e.currentTarget.dataset.newsid;   //数据id
				console.log(newsid)
				uni.navigateTo({  //跳转页面
					url: '../info/info?newsid='+newsid,    //url加id
				});
			}
		}
		
	}
</script>

<style>
	.uni-media-list-body{
		height: auto;
	}
	.uni-media-list-text-top{
		line-height: 1.6em;
	}
</style>