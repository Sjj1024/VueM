<template>
	<video :id="'myVideo'+ video.id" @click="click" @play="changePlay" class="video" :controls="false" :loop="false"
		:src="video.src">
	</video>
</template>

<script>
	export default {
		props: ['video'],
		name: "videoPlayer",
		data() {
			return {
				play: false
			};
		},
		onReady() {
			this.videoContext = uni.createVideoContext("myVideo" + this.video.id, this)
			console.log("视频组件onready:");
			// console.log(this.videoContext);
		},
		mounted() {
			this.videoContext = uni.createVideoContext("myVideo" + this.video.id, this)
		},
		methods: {
			click() {
				console.log("click", this.video.id, this.play);
				if (!this.play) {
					this.playthis()
				} else {
					this.pauseVideo()
				}
			},
			playVideo() {
				if (this.play === false) {
					console.log("playVideo", this.video.id);
					this.videoContext.seek(0)
					this.videoContext.play()
					this.play = true
				}
			},
			pauseVideo() {
				console.log("pauseVideo", this.video.id);
				if (this.play === true) {
					this.videoContext.pause()
					this.play = false
				}
			},
			playthis() {
				// console.log("playthis", this.video.id);
				if (this.play === false) {
					console.log("playthis", this.video.id);
					this.videoContext.play()
					this.play = true
				}
			},
			changePlay() {
				console.log("changePlay");
				this.play = true
			}
		}
	}
</script>

<style>
	.video {
		width: 100vw;
		height: 100vh;
		/* z-index: 1; */
	}

	/* 	.video {
		height: 100%;
		width: 100%;
		z-index: 1;
	} */
</style>
