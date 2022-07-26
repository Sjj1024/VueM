<template>
	<view class="my-box">
		<!-- 可用金币 -->
		<view class="my-money">
			<view class="last-money">
				<text class="money-title">我的金币(元)</text>
				<text class="money-rel">1888.88</text>
			</view>
			<view class="last-action">
				<view class="tixian">
					提现
				</view>
				<view class="chongzhi" @click="toChong">
					充值
				</view>
			</view>
		</view>
		<!-- 可操作项目 -->
		<view class="money-action">
			<view class="info-action">
				<image src="../../static/images/qianbao.png" mode="" class="info-img"></image>
				<text class="info-text">签到奖励</text>
			</view>
			<view class="info-action">
				<image src="../../static/images/commites.png" mode="" class="info-img"></image>
				<text class="info-text">每日赚钱</text>
			</view>
			<view class="info-action">
				<image src="../../static/images/downloader.png" mode="" class="info-img"></image>
				<text class="info-text">邀请返现</text>
			</view>
			<view class="info-action">
				<image src="../../static/images/times.png" mode="" class="info-img"></image>
				<text class="info-text">支出统计</text>
			</view>
			<view class="info-action">
				<image src="../../static/images/tuijian.png" mode="" class="info-img"></image>
				<text class="info-text">点点滴滴</text>
			</view>
		</view>
		<!-- 金币变动明细 -->
		<view class="money-detail">
			<ul class="detail-list">
				<li class="detail-header">
					<text class="detail-title">变动明细</text>
					<text>全部 ></text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							评论收入
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							支付宝充值
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							微信充值
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							云闪付充值
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							系统奖励
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							转账收入
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							评论收入
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
				</li>
				<li class="detail-item">
					<text class="detail-msg">
						<view class="detail-left">
							评论收入
						</view>
						<view class="detail-time">
							2222-07-25 01:12:32
						</view>
					</text>
					<text class="detail-right">
						<view class="right-money">
							+111.00
						</view>
						<view class="right-all">
							余额: 888.00
						</view>
					</text>
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
		methods: {
			toChong() {
				uni.navigateTo({
					url: "/subpkg/pay/pay"
				})
			}
		}
	}
</script>

<style lang="scss">
	.my-box {
		// height: 100vh;
		padding: 10px 5px 10px 5px;
		background-color: #eee;

		.my-money {
			height: 180px;
			background-color: #fff;
			border-radius: 5px;
			display: flex;
			flex-direction: column;
			align-items: center;
			padding: 50px 0px 20px 0px;
			margin-bottom: 10px;

			.last-money {
				flex: 3;
				display: flex;
				flex-direction: column;
				align-items: center;

				.money-title {
					font-size: 15px;
				}

				.money-rel {
					font-size: 30px;
					font-weight: 700;
				}
			}

			.last-action {
				flex: 1;
				display: flex;
				flex-direction: row;
				justify-content: space-evenly;
				width: 100%;

				.tixian,
				.chongzhi {
					display: block;
					width: 36%;
					height: 40px;
					line-height: 40px;
					text-align: center;
					border: 1px solid #ccc;
					border-radius: 5px;
					box-sizing: border-box;
				}

				.chongzhi {
					border: 0px;
					color: #fff;
					background-color: rgb(47, 137, 252);
				}
			}
		}

		.money-action {
			display: flex;
			flex-direction: row;
			justify-content: space-between;
			padding: 5px 20px;
			background-color: #fff;
			border-radius: 5px;
			margin-bottom: 10px;

			.info-action {
				display: flex;
				flex-direction: column;
				align-items: center;
				padding: 8px 0px;

				.info-img {
					width: 28px;
					height: 28px;
				}

				.info-text {
					font-size: 14px;
				}
			}
		}

		.money-detail {
			padding: 5px 20px;
			background-color: #fff;
			border-radius: 5px;

			.detail-list {
				padding: 0;
				margin: 0;

				li {
					list-style: none;
				}

				.detail-header {
					display: flex;
					flex-direction: row;
					justify-content: space-between;
					border-bottom: 1px solid #ccc;
					height: 30px;
					line-height: 30px;
					font-size: 18px;
				}

				.detail-item {
					display: flex;
					justify-content: space-between;
					font-size: 12px;
					color: #aaa;
					padding: 8px 0px;
					height: 40px;

					.detail-msg {
						display: flex;
						flex-direction: column;
						justify-content: space-evenly;

						.detail-left {
							color: black;
							font-size: 16px;
						}
					}

					.detail-right {
						display: flex;
						flex-direction: column;
						justify-content: space-evenly;
						text-align: right;

						.right-money {
							color: black;
							font-size: 16px;
						}
					}
				}
			}
		}
	}
</style>
