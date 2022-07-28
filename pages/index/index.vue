<template>
	<view class="content">
		<!-- 头部菜单导航 -->
		<view class="navigate">
			<scroll-view class="menus" scroll-x :show-scrollbar="false">
				<view class="item" :class="{active:activeNum === index}" v-for="(item, index) in menuList" :key="index"
					@click="toMenu(index, item)">
					{{item}}
				</view>
			</scroll-view>
		</view>
		<!-- 首页/菜单页 -->
		<Dashboard v-show="activeNum === 0"></Dashboard>
		<!-- 分类菜单展示：不同的菜单有不同的列表 -->
		<MenuList v-for="(item, index) in menuNumList" :key="index" v-show="activeNum === item" :menuName="menuName">
		</MenuList>
	</view>
</template>

<script>
	import Dashboard from "./components/Dashboard.vue"
	import MenuList from "./components/MenuList.vue"
	export default {
		data() {
			return {
				title: 'Hello',
				activeNum: 0,
				menuName: "",
				timer: null,
				menuList: ["首页", "生活", "编程", "前端", "数据", "爬虫", "软件", "技术", "美图", "旅游"]
			}
		},
		onLoad() {},
		computed: {
			menuNumList() {
				var arr = new Array();
				for (var i = 1; i < this.menuList.length; i++) {
					arr.push(i)
				}
				return arr
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
		components: {
			Dashboard,
			MenuList
		},
		methods: {
			toMenu(index, menuName) {
				this.activeNum = index;
				this.menuName = menuName
				console.log("当前激活index为", index);
			},
			isMenu(index) {
				console.log("index", index);
				if (this.activeNum === 0) {
					return false
				} else {
					console.log("activeNum", this.activeNum === index);
					return this.activeNum === index
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		padding-top: 42px;

		.navigate {
			position: fixed;
			top: 44px;
			// #ifdef APP-PLUS
			top: 0px;
			// #endif
			background-color: #fff;
			z-index: 999;
			width: 100%;
			height: 70rpx;
			line-height: 70rpx;
			color: black;
			border-bottom: 1px solid #eee;

			.menus {
				width: 100%;
				height: 70rpx;
				line-height: 70rpx;
				white-space: nowrap;

				.item {
					text-align: center;
					display: inline-block;
					width: 100rpx;
					box-sizing: border-box;
					margin-left: 20rpx;
					// margin-top: 3px;
				}

				.active {
					color: #f85959;
				}
			}
		}
	}
</style>
