<template>
	<view class="main">
		<!-- 最新文章 -->
		<view class="news">
			<u-list class="new-list" @scrolltolower="scrolltolower" lowerThreshold="150">
				<u-list-item>
					<!-- 轮播图 -->
					<u-swiper :autoplay="autoplay" height="150" :list="swiperList" keyName="url" indicator
						@change="change" @click="click" circular>
					</u-swiper>
					<!-- 热门文章 -->
					<view class="hot">
						<text class="hot-title">热门文章：</text>
						<ul class="hot-list">
							<li class="hot-item" v-for="(item, index) in hotList" :key="index">
								<img :src="item.imgUrl" alt="你好" class="img">
								<text>{{item.title}}</text>
							</li>
						</ul>
					</view>
				</u-list-item>
				<u-list-item>
					<text class="title">最新文章：</text>
				</u-list-item>
				<u-list-item class="new-item" v-for="(item, index) in articleList" :key="index">
					<view :class="{'new-content': item.imgList.length === 1}">
						<view class="new-title" :class="{'title-three':item.imgList.length === 1}">
							{{item.title}}
						</view>
						<view class="new-imgs" v-if="item.imgList.length > 0">
							<image :src="imgUrl" mode="scaleToFill" v-for="(imgUrl, index) in item.imgList" :key="index"
								class="pre-img" :class="{'one-img':item.imgList.length === 1}">
							</image>
						</view>
					</view>
					<view class="new-info">
						<text class="info">{{item.author}}</text>
						<text class="info">{{item.commites}}评论</text>
						<text class="info">{{item.timer}}小时前</text>
					</view>
				</u-list-item>
			</u-list>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				autoplay: true,
				swiperList: [{
						url: 'https://cdn.uviewui.com/uview/swiper/swiper1.png',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东',
						poster: 'https://cdn.uviewui.com/uview/swiper/swiper1.png',
						type: 'image'
					},
					{
						url: 'https://cdn.uviewui.com/uview/swiper/swiper2.png',
						title: '身无彩凤双飞翼，心有灵犀一点通',
						type: 'image'
					},
					{
						url: 'https://cdn.uviewui.com/uview/swiper/swiper3.png',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳',
						type: 'image'
					}
				],
				hotList: [{
					title: "没什么特别要做的。车子开到了停车场，就去地下餐厅吃饭了...",
					imgUrl: 'https://cdn.uviewui.com/uview/album/2.jpg'
				}, {
					title: "自己应该停在哪里。这个过程比预想中简单很多...",
					imgUrl: 'https://cdn.uviewui.com/uview/album/3.jpg'
				}, {
					title: "周围毫无可逛一逛的风景，人们慵懒地敞开胸膛躺在草地上...",
					imgUrl: 'https://cdn.uviewui.com/uview/album/4.jpg'
				}, {
					title: "坐在车子里玩儿着手机，或者呼呼大睡。我拿着相机到处拍...",
					imgUrl: 'https://cdn.uviewui.com/uview/album/5.jpg'
				}, {
					title: "只是围着自己的汽车转悠。轮船比预定时间晚到了2小时...",
					imgUrl: 'https://cdn.uviewui.com/uview/album/6.jpg'
				}],
				articleList: [{
						title: "当然这时候还有力气和心思欣赏，应接不暇的辽阔与无暇的蓝",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/7d12420bd3666d1b8b457858efbf69e3.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/4eccdc4270a2ba8d139907733b032705.gif",
							"https://img-blog.csdnimg.cn/img_convert/d441d4c59a0f5541841986c74d0a97b7.gif"
						],
						author: "1024小神",
						commites: "36",
						timer: "9"
					},
					{
						title: "这样一座城市，面积不大，主要的街道似乎只有一条，早餐过后我们散步过去，却发现没有一间开始营业的店铺。不知道它们会一直这样紧闭大门，还是只是我们的到访太早而已",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/c89509758ce09b1357921c929604ed54.jpeg"
						],
						author: "光明网",
						commites: "66",
						timer: "1"
					},
					{
						title: "稍远处有一处建在 灯塔 下的房车营地，倒是显得热闹一些。营地前的海滩上长满了荒草，海风吹来，一股萧瑟的咸腥味道",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/132432af7aef388263ab33d45516596e.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/d794e0b76460ea037fc707b01bb1d703.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/f90cd009d24e58857a135cfcd44fe993.jpeg"
						],
						author: "摄影基地",
						commites: "23",
						timer: "2"
					},
					{
						title: "这种切换不管是在app端仍是小程序或者H5页面都是很常见的功能",
						imgList: [],
						author: "光明网",
						commites: "16",
						timer: "8"
					},
					{
						title: "当然这时候还有力气和心思欣赏，应接不暇的辽阔与无暇的蓝",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/7d12420bd3666d1b8b457858efbf69e3.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/4eccdc4270a2ba8d139907733b032705.gif",
							"https://img-blog.csdnimg.cn/img_convert/d441d4c59a0f5541841986c74d0a97b7.gif"
						],
						author: "1024小神",
						commites: "36",
						timer: "9"
					},
					{
						title: "这样一座城市，面积不大，主要的街道似乎只有一条，早餐过后我们散步过去，却发现没有一间开始营业的店铺。不知道它们会一直这样紧闭大门，还是只是我们的到访太早而已",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/c89509758ce09b1357921c929604ed54.jpeg"
						],
						author: "光明网",
						commites: "66",
						timer: "1"
					},
					{
						title: "稍远处有一处建在 灯塔 下的房车营地，倒是显得热闹一些。营地前的海滩上长满了荒草，海风吹来，一股萧瑟的咸腥味道",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/132432af7aef388263ab33d45516596e.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/d794e0b76460ea037fc707b01bb1d703.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/f90cd009d24e58857a135cfcd44fe993.jpeg"
						],
						author: "摄影基地",
						commites: "23",
						timer: "2"
					},
					{
						title: "这种切换不管是在app端仍是小程序或者H5页面都是很常见的功能",
						imgList: [],
						author: "光明网",
						commites: "16",
						timer: "8"
					},
					{
						title: "当然这时候还有力气和心思欣赏，应接不暇的辽阔与无暇的蓝",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/7d12420bd3666d1b8b457858efbf69e3.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/4eccdc4270a2ba8d139907733b032705.gif",
							"https://img-blog.csdnimg.cn/img_convert/d441d4c59a0f5541841986c74d0a97b7.gif"
						],
						author: "1024小神",
						commites: "36",
						timer: "9"
					},
					{
						title: "这样一座城市，面积不大，主要的街道似乎只有一条，早餐过后我们散步过去，却发现没有一间开始营业的店铺。不知道它们会一直这样紧闭大门，还是只是我们的到访太早而已",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/c89509758ce09b1357921c929604ed54.jpeg"
						],
						author: "光明网",
						commites: "66",
						timer: "1"
					},
					{
						title: "稍远处有一处建在 灯塔 下的房车营地，倒是显得热闹一些。营地前的海滩上长满了荒草，海风吹来，一股萧瑟的咸腥味道",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/132432af7aef388263ab33d45516596e.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/d794e0b76460ea037fc707b01bb1d703.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/f90cd009d24e58857a135cfcd44fe993.jpeg"
						],
						author: "摄影基地",
						commites: "23",
						timer: "2"
					},
					{
						title: "这种切换不管是在app端仍是小程序或者H5页面都是很常见的功能",
						imgList: [],
						author: "光明网",
						commites: "16",
						timer: "8"
					},
					{
						title: "当然这时候还有力气和心思欣赏，应接不暇的辽阔与无暇的蓝",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/7d12420bd3666d1b8b457858efbf69e3.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/4eccdc4270a2ba8d139907733b032705.gif",
							"https://img-blog.csdnimg.cn/img_convert/d441d4c59a0f5541841986c74d0a97b7.gif"
						],
						author: "1024小神",
						commites: "36",
						timer: "9"
					},
					{
						title: "这样一座城市，面积不大，主要的街道似乎只有一条，早餐过后我们散步过去，却发现没有一间开始营业的店铺。不知道它们会一直这样紧闭大门，还是只是我们的到访太早而已",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/c89509758ce09b1357921c929604ed54.jpeg"
						],
						author: "光明网",
						commites: "66",
						timer: "1"
					},
					{
						title: "稍远处有一处建在 灯塔 下的房车营地，倒是显得热闹一些。营地前的海滩上长满了荒草，海风吹来，一股萧瑟的咸腥味道",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/132432af7aef388263ab33d45516596e.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/d794e0b76460ea037fc707b01bb1d703.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/f90cd009d24e58857a135cfcd44fe993.jpeg"
						],
						author: "摄影基地",
						commites: "23",
						timer: "2"
					}
				]
			}
		},
		onLoad() {
			this.loadmore()
		},
		onPullDownRefresh() {
			console.log("下拉刷新");
			this.timer = setInterval(() => {
				uni.stopPullDownRefresh()
				clearInterval(this.timer)
			}, 1000)
			uni.showToast({
				title: '数据已更新....',
				duration: 2000
			});
		},
		// onReachBottom() {
		// 	uni.showToast({
		// 		title: '数据已更新....',
		// 		duration: 2000
		// 	});
		// },
		methods: {
			change() {
				// console.log("改变了");
			},
			click() {
				// console.log("点击了");
				this.autoplay = false
			},
			scrolltolower() {
				console.log("滚动到底部了");
				uni.showToast({
					title: '数据已更新....',
					duration: 2000
				});
			},
			loadmore() {
				uni.showToast({
					title: '数据已更新....',
					duration: 2000
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	.main {
		height: auto !important;

		.hot {
			padding: 5rpx 10rpx;
			height: auto !important;
			margin-bottom: 10px;

			.hot-list {
				padding: 0;

				.hot-item {
					display: flex;
					flex-direction: row;
					padding: 5px 0px;
					border-bottom: 1px solid #eee;
					font-size: 30rpx;

					.img {
						width: 50px;
						height: 50px;
						margin-right: 10px;
					}
				}
			}

			.hot-title {
				display: inline-block;
				width: 97%;
				padding: 10rpx;
				font-size: 35rpx;
				font-weight: 700;
				border-bottom: 1px solid #ccc;
			}
		}

		.new-list {
			// height: auto !important;
			height: 100vh;
			overflow-y: auto;

			.new-item {
				::v-deep .u-cell__body {
					padding: 10px 0px 10px 5px;
				}
			}
		}

		.news {
			padding: 5rpx 20rpx;
			// height: 100vh;
			overflow-y: auto;

			.title {
				display: inline-block;
				width: 97%;
				padding: 10rpx;
				font-size: 35rpx;
				font-weight: 700;
				border-bottom: 1px solid #ccc;
			}

			.new-item {
				padding: 10rpx;
				margin-bottom: 20rpx;
				border-bottom: 1px solid #eee;

				.new-content {
					display: flex;
					flex-direction: row;
					justify-content: space-between;

				}

				.new-title {
					flex: 2;
					font-size: 35rpx;
					margin-bottom: 10rpx;
					overflow: hidden;
					display: -webkit-box;
					-webkit-line-clamp: 2;
					line-clamp: 2;
					-webkit-box-orient: vertical;
					text-overflow: ellipsis;
				}

				.title-three {
					height: 70px;
					overflow: hidden;
					display: -webkit-box;
					-webkit-line-clamp: 3;
					line-clamp: 3;
					-webkit-box-orient: vertical;
					text-overflow: ellipsis;
				}

				.new-imgs {
					flex: 1;
					display: flex;
					flex-direction: row;
					justify-content: space-between;

					.pre-img {
						width: 33%;
						height: 180rpx;
					}

					.one-img {
						width: 100%;
					}
				}

				.new-info {
					margin-top: 10rpx;

					.info {
						font-size: 30rpx;
						color: gray;
						margin-right: 20rpx;
					}
				}
			}
		}


	}
</style>
