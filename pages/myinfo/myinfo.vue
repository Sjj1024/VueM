<template>
	<view class="my-box">
		<view class="my-header">
			<image src="/static/images/mylogo.jpg" mode="" class="my-logo"></image>
			<text class="nick-name">1024小神</text>
		</view>
		<!-- 我的消息 -->
		<view class="my-info">
			<view class="info-action">
				<image src="../../static/images/collector.png" mode="" class="info-img"></image>
				<text>我的收藏</text>
			</view>
			<view class="info-action">
				<image src="../../static/images/commites.png" mode="" class="info-img"></image>
				<text>我的消息</text>
			</view>
			<view class="info-action">
				<image src="../../static/images/downloader.png" mode="" class="info-img"></image>
				<text>下载管理</text>
			</view>
			<view class="info-action">
				<image src="../../static/images/times.png" mode="" class="info-img"></image>
				<text>浏览历史</text>
			</view>
		</view>
		<!-- 软件设置 -->
		<view class="more-action">
			<text class="action-title">更多服务</text>
			<ul class="my-setting">
				<li class="action-set">
					<image src="../../static/images/kefu.png" mode="" class="set-img"></image>
					<text>客服中心</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/qianbao.png" mode="" class="set-img"></image>
					<text>我的钱包</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/guanggao.png" mode="" class="set-img"></image>
					<text>广告推广</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/anquan.png" mode="" class="set-img"></image>
					<text>安全中心</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/yinsi.png" mode="" class="set-img"></image>
					<text>隐私设置</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/pinglun.png" mode="" class="set-img"></image>
					<text>评论管理</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/gouwuche.png" mode="" class="set-img"></image>
					<text>购物车</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/yonghuxieyi.png" mode="" class="set-img"></image>
					<text>用户协议</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/ruanjiangengxin.png" mode="" class="set-img"></image>
					<text>软件更新</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/guanyuwomen.png" mode="" class="set-img"></image>
					<text>关于我们</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/chongzhi.png" mode="" class="set-img"></image>
					<text>金币充值</text>
				</li>
				<li class="action-set">
					<image src="../../static/images/tuijian.png" mode="" class="set-img"></image>
					<text>推荐有奖</text>
				</li>
			</ul>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
	}
</script>

<style lang="scss" scoped>
	.my-box {
		width: 100%;
		height: 100vh;
		// background-color: #eee;
		padding: 100px 5px 0px 5px;
		box-sizing: border-box;
		background: url("https://img-blog.csdnimg.cn/img_convert/a6e32639e756aee2c15d92aaaf99430c.jpeg") no-repeat fixed center;

		.my-header {
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			height: 150px;

			.my-logo {
				width: 60px;
				height: 60px;
				border-radius: 30px;
				margin-bottom: 10px;
			}

			.nick-name {
				font-size: 20px;
			}
		}

		.my-info {
			display: flex;
			flex-direction: row;
			justify-content: space-between;
			padding: 5px 20px;
			background-color: #fff;
			border-radius: 5px;

			.info-action {
				display: flex;
				flex-direction: column;
				align-items: center;

				.info-img {
					width: 40px;
					height: 40px;
				}
			}
		}

		.more-action {
			margin: 10px 0px 0px 0px;
			background-color: #fff;
			border-radius: 5px;

			.action-title {
				display: block;
				height: 40px;
				line-height: 40px;
				font-weight: 700;
				padding: 0px 20px;
			}

			.my-setting {
				display: flex;
				flex-direction: row;
				flex-wrap: wrap;
				padding: 0;

				.action-set {
					display: flex;
					flex-direction: column;
					align-items: center;
					justify-content: center;
					width: 25%;
					height: 80px;
					// line-height: 80px;
					list-style: none;

					.set-img {
						width: 40px;
						height: 40px;
					}
				}
			}
		}


	}
</style>
