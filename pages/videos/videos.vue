<template>
	<swiper class="swiper" :vertical="true" @change="change" @touchstart="touchStart" @touchend="touchEnd">
		<block v-for="item of videoList" :key="item.id">
			<swiper-item ref="swiperItem" data-type="video" class="swiper-item" v-if="item.type === 'video'">
				<videoPlayer :video="item" ref="player"></videoPlayer>
			</swiper-item>
			<!-- 直播流/判断平台 -->
			<!-- #ifndef APP-PLUS -->
			<live-player v-else-if="item.type === 'live'" :style="{height:screenHeight+'px', width: windowWidth + 'px'}"
				:src="item.src" :object-fit="fillCrop"></live-player>
			<!-- #endif -->
			<!-- #ifdef APP-PLUS -->
			<video v-else-if="item.type === 'live'" :autoplay="false" :controls="true"
				:style="{height:screenHeight+'px', width: windowWidth + 'px'}" object-fit="fill"
				src="https://pull-flv-l11.douyincdn.com/third/stream-111331819072782812_hd.flv" preload="auto"></video>
			<!-- #endif -->
			<swiper-item ref="swiperItem" data-type="img" v-else>
				<swiper :style="{height:screenHeight+'px'}" class="img-boxs" circular :indicator-dots="true"
					:autoplay="true" :current="currentImgIndex" @change="changeswiper">
					<swiper-item v-for="(item, index) in item.imgList" :key="index">
						<image :src="item" mode="scaleToFill" class="swiper-img"></image>
					</swiper-item>
				</swiper>
			</swiper-item>
		</block>
	</swiper>
</template>

<script>
	import videoPlayer from "./components/videoPlayer.vue"
	var time = null
	export default {
		props: ["myList"],
		components: {
			videoPlayer,
		},
		name: "video-list",
		data() {
			return {
				videoList: [{
						id: 7,
						type: "image",
						imgList: [
							'https://img-blog.csdnimg.cn/img_convert/4ce460a31366926464acc88c991721d9.jpeg',
							'https://img-blog.csdnimg.cn/img_convert/a8d701d5adc9008ca018905f43c34145.jpeg',
							'https://img-blog.csdnimg.cn/img_convert/3090b46bd91e5c7ee5d78d988fbae0bd.jpeg',
							"https://img-blog.csdnimg.cn/img_convert/08acb513a12e1d7d654cc43cf4e2ee48.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/eebf7eefba5849ef9788e32c148061c8.jpeg"
						],
					}, {
						id: 1,
						type: "video",
						preImg: "http://p1-q.mafengwo.net/s16/M00/8D/4D/CoUBUmFZOWKAA8mQAA8Oww0vs7k240.jpg",
						src: "https://txmov2.a.yximgs.com/upic/2020/03/14/16/BMjAyMDAzMTQxNjIwMDlfMTI0OTQzNzMzOV8yNDk0OTExNDY1NF8xXzM=_b_B8cf5a4391531e161385a32cdadfef87c.mp4"
					},
					{
						id: 8,
						type: "image",
						imgList: [
							'https://img-blog.csdnimg.cn/img_convert/4ce460a31366926464acc88c991721d9.jpeg',
							'https://img-blog.csdnimg.cn/img_convert/a8d701d5adc9008ca018905f43c34145.jpeg',
							'https://img-blog.csdnimg.cn/img_convert/3090b46bd91e5c7ee5d78d988fbae0bd.jpeg',
							"https://img-blog.csdnimg.cn/img_convert/08acb513a12e1d7d654cc43cf4e2ee48.jpeg",
							"https://img-blog.csdnimg.cn/img_convert/eebf7eefba5849ef9788e32c148061c8.jpeg"
						],
					},
					{
						id: 9,
						type: "live",
						preImg: "http://p1-q.mafengwo.net/s16/M00/8D/4D/CoUBUmFZOWKAA8mQAA8Oww0vs7k240.jpg",
						src: "https://pull-flv-l11.douyincdn.com/third/stream-111331250459378140_hd.flv"
					}, {
						id: 2,
						type: "video",
						preImg: "http://b1-q.mafengwo.net/s16/M00/23/F3/CoUBUmFbN5OAGqEkAA4O0V-U1uo031.jpg",
						src: "https://txmov2.a.yximgs.com/upic/2020/10/02/09/BMjAyMDEwMDIwOTAwMDlfMTIyMjc0NTk0Ml8zNjk3Mjg0NjcxOF8xXzM=_b_B28a4518e86e2cf6155a6c1fc9cf79c6d.mp4"
					},
					{
						id: 3,
						type: "video",
						preImg: "http://p1-q.mafengwo.net/s16/M00/23/F4/CoUBUmFbN5WAbMikAA5cYlWno5U709.jpg",
						src: "https://txmov6.a.yximgs.com/upic/2020/08/23/00/BMjAyMDA4MjMwMDMyNDRfMTYzMzY5MDA0XzM0ODI4MDcyMzQ5XzFfMw==_b_B9a1c9d4e3a090bb2815994d7f33a906a.mp4"
					},
					{
						id: 4,
						type: "video",
						preImg: "http://p1-q.mafengwo.net/s18/M00/E6/C0/CoUBYGFceTyAOSBqABFXcMPFJ1w112.jpg",
						src: "https://alimov2.a.yximgs.com/upic/2020/03/04/15/BMjAyMDAzMDQxNTU3MTdfMzE3MDM5OTAzXzI0NDUwNjQ1MzgxXzFfMw==_b_B53c20819cb9a2103b9805b0144f545cf.mp4"
					},
					{
						id: 5,
						type: "video",
						preImg: "http://p1-q.mafengwo.net/s18/M00/E6/C0/CoUBYGFceTyAOSBqABFXcMPFJ1w112.jpg",
						src: "https://txmov2.a.yximgs.com/upic/2020/07/14/16/BMjAyMDA3MTQxNjEyNDBfMTU3MDQyNjA0XzMyMzUyOTQ4NzM0XzJfMw==_b_Bd53949260b17aaa7b712526aa61e590a.mp4"
					},
					{
						id: 6,
						type: "video",
						preImg: "http://p1-q.mafengwo.net/s18/M00/E6/C0/CoUBYGFceTyAOSBqABFXcMPFJ1w112.jpg",
						src: "https://txmov2.a.yximgs.com/upic/2020/09/28/15/BMjAyMDA5MjgxNTAwMTlfNjk3OTM4NjUzXzM2NzQyNzU5MzA2XzFfMw==_b_B6e8aca57e704ac40b34856eb663b8d57.mp4"
					},
				],
				screenHeight: 0,
				currentImgIndex: 0
			};
		},
		mounted() {
			uni.getSystemInfo({
				success: (res) => {
					// console.log("首页获取到的页面高度:windowHeight", res.windowHeight);
					this.screenHeight = res.windowHeight;
				}
			});
		},
		methods: {
			change(res) {
				clearTimeout(time)
				this.page = res.detail.current
				let swiperPre = this.$refs.swiperItem[this.page - 1]
				let swiperItem = this.$refs.swiperItem[this.page]
				let swiperNext = this.$refs.swiperItem[this.page + 1]
				let currentType = swiperItem.$attrs["data-type"]
				time = setTimeout(() => {
					if (this.pageStartY > this.pageEndY) {
						// console.log("向上滑动当前页:" + this.page);
						// console.log("改变当前显示图片索引:", this.currentImgIndex);
						if (currentType === "video") {
							swiperItem.$children[0].playVideo()
							this.pageStartY = 0
							this.pageEndY = 0
						} else {
							// console.log("改变当前显示图片索引:", this.currentImgIndex);
							this.$nextTick(() => {
								this.currentImgIndex = 0
							})
						}
						if (swiperPre.$attrs["data-type"] === "video") {
							swiperPre.$children[0].pauseVideo()
						}
					} else {
						// console.log("向下滑动" + this.page);
						// console.log("改变当前显示图片索引:", this.currentImgIndex);
						if (currentType === "video") {
							swiperItem.$children[0].playVideo()
							this.pageStartY = 0
							this.pageEndY = 0
						} else {
							this.$nextTick(() => {
								this.currentImgIndex = 0
							})
						}
						if (swiperNext.$attrs["data-type"] === "video") {
							swiperNext.$children[0].pauseVideo()
						}
					}
				}, 1)
			},
			touchStart(res) {
				this.pageStartY = res.changedTouches[0].pageY;
				console.log(this.pageStartY);
			},
			touchEnd(res) {
				this.pageEndY = res.changedTouches[0].pageY;
				console.log(this.pageEndY);
			},
			changeswiper(e) {
				this.currentImgIndex = e.detail.current
			}
		},
		watch: {
			myList() {
				this.list = this.myList;
			}
		}
	}
</script>

<style>
	.swiper {
		width: 100vw;
		height: 100vh;
	}

	.swiper-item {
		width: 100vw;
		height: 100vh;
		z-index: 9;
	}

	.swiper-img {
		width: 100%;
		height: 100%;
	}


	/* 	.left-box {
		z-index: 20;
		position: absolute;
		bottom: 50px;
		left: 10px;
	}

	.right-box {
		z-index: 20;
		position: absolute;
		bottom: 50px;
		right: 10px;
	} */
</style>
