<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* 去除scroll滚动条 */
	/* #ifndef APP-NVUE */
	::-webkit-scrollbar {
		display: none;
		width: 0;
		height: 0;
		background-color: transparent;
	}

	/* #endif */

	.swiper-wrapper {
		transition-timing-function: linear; //匀速滚动
	}

	/* 	::-webkit-scrollbar {
		display: none;
		width: 0 !important;
		height: 0 !important;
		-webkit-appearance: none;
		background: transparent;
		color: transparent;
	} */

	/* 	wx wx-swiper .wx-swiper-wrapper {
		width: 100px;
		height: 100px;
	}

	wx-swiper .wx-swiper-wrapper-active {
		background-color: #000;
		width: 100px;
		border-radius: 5px;
	} */

	/* 注意要写在第一行，同时给style标签加入lang="scss"属性 */
	@import "@/uni_modules/uview-ui/index.scss";
</style>
