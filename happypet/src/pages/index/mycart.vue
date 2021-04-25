<template>
<view class="content">

<view>
		<view class="main">
			<view class="cartlist">
				<view class="cartitem" v-for="(item,index) of cartlist" :key="index" style="height:120px;width:100%">
					<checkbox-group @change="selected(item)">
						<checkbox class="xuanzhong" :checked="item.flag" />
					</checkbox-group>

					<image src='../../static/pet1.jpeg' mode=""></image>
					<view class="itemright" style="float:right;display:flex;flex-direction:row;" >
						<view class="proname" style="height:20px;line-hegiht:30px;margin-right:30px;margin:10px">
							狗钥匙
						</view>
						<view class="">
							￥577
							<view  style="height:20px;width:20px;line-height:15px;margin-right:30px;font-size:20px;background-color:#ff5555;margin:2px;text-align:center;"  @click="reduce(item)">-</view>
							{{item.num}}
							<view style="height:20px;width:20px;line-height:15px;margin-right:30px;font-size:20px;background-color:#ff5555;margin:2px;text-align:center;" @click="add(item)">+</view>
							<text class="del" @click="del(item,index)">删除</text>
						</view>
					</view>
				</view>
			</view>



			<view class="di">
				<view class="quanxuan">
					<checkbox-group @change="selectedall()">
						<checkbox class="quanxuananniu" :checked="allchecked" />全选
					</checkbox-group>
				</view>
				<view class="">
					总数:{{totalNum}}
				</view>
				<view class="">
					总价:{{totalPrice}}
				</view>
			</view>
		</view>

	</view>

	<view class="go_to_buy" style="width:100%;position:absolute;bottom:0;height:50px;display:flex;flex-direction:row;align-items:center;justify-content:center"><span style="width:65%">合计：59￥</span><button class=“buy” style="background-color:#f0c566;color:red;width:35%" @click="buy()">立即购买</button></view>


</view>



</template>

<script>
  //因为他们的功能我们不能全用上，所以自己封装个简单的（可以不封装）

	export default {
		data() {
			return {
				flag: true, // 用于判断用户购物车是否有商品，没有商品为true，有商品为false
				cartlist: ["大降价","998","娃哈哈"], // 购物车商品信息
				allchecked: true //默认全选为true，因为后台数据没有是否选中的信息
			}
		},

		computed: {
			// 计算选中商品数量
			totalNum() {
				let totalNum = 0;
				this.cartlist.map(item => {
					item.flag ? totalNum += item.num : totalNum += 0
				})
				return totalNum
			},
			//计算选中商品的总价
			totalPrice() {
				let totalPrice = 0;
				this.cartlist.map(item => {
					item.flag ? totalPrice += item.num * item.price : totalPrice += 0
				})
				return totalPrice
			}
		},
		onShow() {
			try {
				let userid = uni.getStorageSync('userid') // 提取缓存中的用户id
				let token = uni.getStorageSync('token') // 提取缓存中的token值
				if (userid && token) { // 两个值都在的时候才能访问购物车数据，否则跳到登录界面
					request({
						url: '/cart',
						data: {
							userid,
							token
						}
					}).then(res => {
						// console.log(res.data.data)
						if (res.data.code === '10019') {
							toast({
								title: '请先登录'
							})
							uni.navigateTo({
								url: '/pages/login/login'
							})
						} else if (res.data.code === '10012') {
							toast({
								title: '请选择商品'
							})
							this.flag = true
						} else {
							toast({
								title: '获取列表成功'
							})
							this.flag = false
							res.data.data.map(item => { //因为后端数据没有是否选中，所以自己加了一条
								item.flag = true
							})
							this.cartlist = res.data.data
						}
					})
				} else {
					toast({
						title: '请先登录'
					})
					uni.navigateTo({
						url: '/pages/login/login'
					})
				}
			} catch (e) {
				//TODO handle the exception
			}
		},
		methods: {
			buy(){
				uni.requestPayment({
					provider: 'alipay',
					orderInfo: orderInfo,
					success: function(res) {
						console.log('success:' + JSON.stringify(res));
						},
					fail: function(err) {
						console.log('fail:' + JSON.stringify(err));
						}
				});

			},
			// 减号操作
			reduce(item) {
				let num = item.num
				// 需要判断是否会减到0，我在这里是最小为1.
				if (num > 1) {
					num -= 1
				} else {
					num = 1
					return
				}
				let token = uni.getStorageSync('token')
				request({
					url: '/cart/update',
					data: {
						token,
						cartid: item.cartid,
						num
					}
				}).then(res => {
					if (res.data.code === '10019') {
						toast({
							title: '请先登录'
						})
						uni.navigateTo({
							url: '/pages/login/login'
						})
					} else {
						toast({
							title: '修改数量成功'
						})
						item.num = num
					}
				})
			},
			// 加号操作
			add(item) {
				let num = item.num
				num += 1
				let token = uni.getStorageSync('token')
				request({
					url: '/cart/update',
					data: {
						token,
						cartid: item.cartid,
						num
					}
				}).then(res => {
					if (res.data.code === '10019') {
						toast({
							title: '请先登录'
						})
						uni.navigateTo({
							url: '/pages/login/login'
						})
					} else {
						toast({
							title: '修改数量成功'
						})
						item.num += 1
					}
				})
			},
			// 删除单挑购物车商品
			del(item, index) {
				let token = uni.getStorageSync('token')
				request({
					url: '/cart/delete',
					data: {
						token,
						cartid: item.cartid,
					}
				}).then(res => {
					if (res.data.code === '10019') {
						toast({
							title: '请先登录'
						})
						uni.navigateTo({
							url: '/pages/login/login'
						})
					} else {
						toast({
							title: '删除成功'
						})
						this.cartlist.splice(index, 1)
						if (this.cartlist.length === 0) {
							this.flag = true
						}
					}
				})
			},
			// 单个商品前的勾选
			selected(item) {
				// console.log(item)
				item.flag = !item.flag
				if (!item.flag) {
					this.allchecked = false
				} else {
					const test = this.cartlist.every(item => {
						return item.flag === true
					})
					if (test) {
						this.allchecked = true
					} else {
						this.allchecked = false
					}
				}
			},
			// 全选按钮
			selectedall() {
				this.allchecked = !this.allchecked
				if (this.allchecked) {
					this.cartlist.map(item => {
						item.flag = true
					})
				} else {
					this.cartlist.map(item => {
						item.flag = false
					})
				}
			}

		}
	}

</script>


<style lang="scss" scoped>
   .cartlist {
		background-color: #f0c566;
		box-shadow:1px 2px 3px 4px #f0c566 ;
		padding: 10px;

		.cartitem {
			background-color: #eeeeee;
			box-shadow:1px 2px 3px 4px #f0c566 ;
			height: 50px;
			margin-bottom: 10px;

			.xuanzhong {
				float: left;
				line-height: 50px;
				padding-left: 5px;
			}

			image {
				display: inline-block;
				height: 40px;
				width: 40px;
				padding: 5px 0;
				float: left;
			}

			.itemright {
				display: inline-block;
				padding: 5px;

				.del {
					margin-left: 10px;
					background-color: red;
					color: #FFFFFF;
					border-radius: 3px;
					padding: 0 5px;
				}
			}
		}

	}

</style>