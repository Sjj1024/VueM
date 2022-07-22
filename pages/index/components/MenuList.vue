<template>
	<view class="news">
		<u-list class="new-list" @scrolltolower="scrolltolower" lowerThreshold="150">
			<u-list-item>
				<text class="title">菜单新闻列表---{{menuName}}</text>
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
</template>

<script>
	export default {
		data() {
			return {
				articleList: [{
						title: "使用uni-app提供的scroll-view组件",
						imgList: [
							"https://img-blog.csdnimg.cn/img_convert/539ee665a9a7bfc58303467aa27421fe.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/083a2793a43d8d5e464cdaf84920f44f.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/31e1bedc46adf2d5448f18dfd60e0b70.gif"
						],
						author: "人民日报",
						commites: "100",
						timer: "10"
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
		props: {
			menuName: {
				default: "默认",
				type: String
			}
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
		methods: {
			scrolltolower() {
				console.log("滚动到底部了");
				uni.showToast({
					title: '数据已更新....',
					duration: 2000
				});
			}
		}
	}
</script>

<style scoped lang="scss">
	// .menu-list {
	// 	height: 100vh;
	// 	overflow-y: auto;
	// }

	.new-list {
		// 要设置一个高度，否则无效
		height: 95vh;
		overflow-y: auto;

		.new-item {
			::v-deep .u-cell__body {
				padding: 10px 0px 10px 5px;
			}
		}
	}

	.news {
		padding: 5rpx 20rpx;
		height: 95vh;
		overflow-y: auto;

		.title {
			display: inline-block;
			width: 97%;
			padding: 10rpx;
			font-size: 35rpx;
			font-weight: 600;
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
</style>
