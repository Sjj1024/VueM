<template>
	<view class="item-box">
		<text class="nav-title">{{title}}</text>
		<slot name="content">
			<view class="nav-content">
				<view v-for="(link, index) in navLinks" :key="index" class="nav-link" hover-class="checkActive"
					hover-stay-time="100" @click="openBrowser(link.url)">
					<view class="link">{{ link.name }}</view>
				</view>
			</view>
		</slot>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		props: {
			title: {
				default: "坑人导航:",
				type: String
			},
			navLinks: {
				default () {
					return [{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
						{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
						{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
						{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
						{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
						{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
						{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
						{
							name: "百度一下",
							url: "https://www.baidu.com/"
						},
					]
				},
				type: Array
			}
		},
		methods: {
			openBrowser(url) {
				plus.runtime.openURL(url)
			},
		}
	}
</script>

<style lang="scss" scoped>
	.item-box {
		width: 100%;
		// margin-bottom: 10px;

		.nav-title {
			display: block;
			// width: 100%;
			height: 30px;
			padding: 0px 5px;
			line-height: 30px;
			font-size: 17px;
			font-weight: 700;
			border-bottom: 1px solid #ccc;
		}

		.nav-content {
			display: flex;
			flex-direction: row;
			flex-wrap: wrap;

			.checkActive {
				color: white;
				background-color: rgb(47, 137, 252);
				border-radius: 5px;
			}

			.nav-link {
				width: 25%;
				height: 40px;
				box-sizing: border-box;
				line-height: 40px;
				text-align: center;
				padding: 0px 10px;

				// &:hover {
				// 	color: white;
				// 	background-color: rgb(47, 137, 252);
				// }

				.link {
					display: block;
					// height: 30px;
					// line-height: 30px;
					// border-bottom: 1px solid rgb(47, 137, 252);
				}
			}
		}
	}
</style>
