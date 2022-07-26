<template>
	<view class="nav-box">
		<navItem v-for="(link, index) in linkList" :key="index" :title="link.title" :navLinks="link.links"></navItem>
	</view>
</template>

<script>
	import navItem from "./components/navItem.vue"

	export default {
		data() {
			return {
				linkList: [{
						title: "坑人搜索",
						links: [{
								name: "百度一下",
								url: "https://www.baidu.com/"
							},
							{
								name: "百度一下",
								url: "https://www.baidu.com/"
							}, {
								name: "百度一下",
								url: "https://www.baidu.com/"
							}, {
								name: "百度一下",
								url: "https://www.baidu.com/"
							}, {
								name: "百度一下",
								url: "https://www.baidu.com/"
							}, {
								name: "百度一下",
								url: "https://www.baidu.com/"
							}, {
								name: "百度一下",
								url: "https://www.baidu.com/"
							}, {
								name: "百度一下",
								url: "https://www.baidu.com/"
							},
						]
					},
					{
						title: "生活服务",
						links: [{
								name: "天气预报",
								url: "https://www.baidu.com/"
							},
							{
								name: "快递查询",
								url: "https://www.baidu.com/"
							},
							{
								name: "违章查询",
								url: "https://www.baidu.com/"
							},
							{
								name: "手机充值",
								url: "https://www.baidu.com/"
							},
							{
								name: "股票基金",
								url: "https://www.baidu.com/"
							},
							{
								name: "银行理财",
								url: "https://www.baidu.com/"
							},
							{
								name: "房产查询",
								url: "https://www.baidu.com/"
							},
							{
								name: "汽车飞机",
								url: "https://www.baidu.com/"
							},
							{
								name: "购物团购",
								url: "https://www.baidu.com/"
							},
						]
					},
					{
						title: "在线影视",
						links: [{
								name: "爱奇艺",
								url: "https://www.baidu.com/"
							},
							{
								name: "腾讯视频",
								url: "https://www.baidu.com/"
							},
							{
								name: "优酷视频",
								url: "https://www.baidu.com/"
							},
							{
								name: "YouTube",
								url: "https://www.baidu.com/"
							},
							{
								name: "努努影视",
								url: "https://www.baidu.com/"
							},
						]
					},
					{
						title: "技术学习",
						links: [{
								name: "Bilibili",
								url: "https://www.baidu.com/"
							},
							{
								name: "幕客视频",
								url: "https://www.baidu.com/"
							},
							{
								name: "黑客教程",
								url: "https://www.baidu.com/"
							},
							{
								name: "破解教程",
								url: "https://www.baidu.com/"
							},
							{
								name: "安全网络",
								url: "https://www.baidu.com/"
							},
						]
					},
					{
						title: "电脑网络",
						links: [{
								name: "软件仓库",
								url: "https://www.baidu.com/"
							},
							{
								name: "病毒查杀",
								url: "https://www.baidu.com/"
							},
							{
								name: "硬件",
								url: "https://www.baidu.com/"
							},
							{
								name: "网页编程",
								url: "https://www.baidu.com/"
							},
							{
								name: "主机域名",
								url: "https://www.baidu.com/"
							},
						]
					},
					{
						title: "娱乐休闲",
						links: [{
								name: "今日头条",
								url: "https://www.baidu.com/"
							},
							{
								name: "视频电影",
								url: "https://www.baidu.com/"
							},
							{
								name: "电视游戏",
								url: "https://www.baidu.com/"
							},
							{
								name: "新闻小说",
								url: "https://www.baidu.com/"
							},
							{
								name: "动漫体育",
								url: "https://www.baidu.com/"
							},
						]
					},
				]
			};
		},
		components: {
			navItem
		}
	}
</script>

<style lang="scss" scoped>
	.nav-box {
		width: 100%;
		padding: 5px 0px 0px 0px;
	}
</style>
