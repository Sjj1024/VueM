<template>
	<view class="pay-box">
		<!-- 充值方式 -->
		<view class="pay-way">
			<view class="way-title">
				充值方式:
			</view>
			<view class="way-list" @click="showWay">
				<view class="way-left">
					<image src="../../static/images/weixin.png" mode="" class="way-img"></image>
					<text class="way-info">
						<view>微信支付(9118)</view>
						<view class="info">每日最多可充值 ¥50000</view>
					</text>
				</view>
				<view class="way-right">
					>
				</view>
			</view>
		</view>
		<!-- 充值金额 -->
		<view class="pay-money" v-if="!payCode">
			<view class="pay-title">
				充值金额
			</view>
			<view class="pay-input">
				<!-- #ifndef APP-NVUE -->
				<u-input placeholder="" v-model="value" fontSize="20px" type="digit" :adjustPosition="false">
					<!-- #endif -->
					<!-- #ifdef APP-NVUE -->
					<u--input placeholder="" v-model="value" fontSize="20px" type="digit" :adjustPosition="false">
						<!-- #endif -->
						<u--text text="¥" slot="prefix" margin="0 3px 0 0" type="number" class="pre-text"></u--text>
						<!-- #ifndef APP-NVUE -->
				</u-input>
				<!-- #endif -->
				<!-- #ifdef APP-NVUE -->
				</u--input>
				<!-- #endif -->
			</view>
		</view>
		<!-- 立即充值 -->
		<view class="pay-submit" @click="showCode" v-if="!payCode">
			<u-button type="primary" text="立即充值" class="pay-btn"></u-button>
		</view>
		<!-- 展示二维码支付 -->
		<view class="pay-code" v-else :style="{height:screenHeight+'px'}">
			<view class="pay-tips">
				<view>
					请使用微信扫描二维码或长按识别
				</view>
				<view>
					您正在充值的金额是{{value}}元
				</view>
			</view>
			<view class="pay-mazi">
				<canvas id="qrcode" class="erweima" canvas-id="qrcode"
					:style="{ width: `${size}px`, height: `${size}px` }"></canvas>
			</view>
		</view>
		<!-- 选择方式弹出层 -->
		<u-popup :show="show" mode="bottom" @close="close" :round="10" @open="open" :closeable="true"
			closeIconPos="top-left">
			<view class="popup-title">
				请选择付款方式
			</view>
			<ul class="way-box">
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/zhifubao.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>支付宝支付(9118)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
					<view class="way-right">
						<image src="../../static/images/duihao.png" mode="" class="checked"></image>
					</view>
				</li>
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/weixin.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>微信支付(9118)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
					<!-- 					<view class="way-right">
						<image src="../../static/images/duihao.png" mode="" class="checked"></image>
					</view> -->
				</li>
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/jianshe.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>建设银行储蓄卡(9189)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
					<!-- 					<view class="way-right">
						<image src="../../static/images/duihao.png" mode="" class="checked"></image>
					</view> -->
				</li>
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/youzheng.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>邮政银行储蓄卡(4903)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
				</li>
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/zhonguo.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>中国银行储蓄卡(9189)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
				</li>
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/zhaoshang.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>招商银行储蓄卡(9189)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
				</li>
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/pufa.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>浦发银行储蓄卡(9189)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
				</li>
				<li class="way-item">
					<view class="way-left">
						<image src="../../static/images/gongshang.png" mode="" class="way-img"></image>
						<text class="way-info">
							<view>工商银行储蓄卡(9189)</view>
							<view class="info">每日最多可充值 ¥50000</view>
						</text>
					</view>
				</li>
			</ul>
		</u-popup>
	</view>
</template>

<script>
	import uQRCode from '../../uni_modules/Sansnn-uQRCode/js_sdk/u-qrcode';

	export default {
		data() {
			return {
				show: false,
				value: 1,
				text: 'https://payjs.cn/api/cashier?attach=1&body=%E7%A7%AF%E5%88%86%E5%85%85%E5%80%BC&hide=1&mchid=1593541201&notify_url=https%3A%2F%2F1024shen.com%2Fwp-content%2Fthemes%2FBreeze2%2Fmodules%2Fpush.php&out_trade_no=E2022072618092944611&total_fee=100&sign=EAF55DB13E3E247BC354A196E9C6ACAE',
				size: 256,
				payCode: false,
				screenHeight: 0,
			}
		},
		mounted() {
			uni.getSystemInfo({
				success: (res) => {
					console.log("首页获取到的页面高度:windowHeight", res.windowHeight);
					this.screenHeight = res.windowHeight;
				}
			});
		},
		methods: {
			open() {
				// console.log('open');
			},
			close() {
				this.show = false
				// console.log('close');
			},
			showWay() {
				this.show = true
			},
			showCode() {
				this.payCode = true
				const ctx = uni.createCanvasContext('qrcode');
				const uqrcode = new uQRCode({
						text: this.text,
						size: this.size
					},
					ctx
				);
				uqrcode.make();
				uqrcode.draw();
			}
		}
	}
</script>

<style lang="scss" scoped>
	.pay-box {
		padding: 10px 5px 10px 5px;
		background-color: #eee;

		.pay-submit {
			height: 30px;
			margin-top: 10px;

			.pay-btn {
				border: 0px;
			}
		}

		.pay-code {
			// height: 100%;
			padding: 20px 5px;
			background-color: #fff;
			margin-top: 10px;
			text-align: center;

			.pay-mazi {
				text-align: center;
				display: flex;
				justify-content: center;
				margin-top: 20px;
			}
		}

		.pay-money {
			padding: 20px 5px;
			background-color: #fff;
			margin-top: 10px;

			.pay-title {
				// font-size: 14px;
				margin-bottom: 10px;
			}

			.pay-input {
				font-size: 20px !important;

				.pre-text {
					font-size: 20px !important;
				}
			}
		}

		.pay-way {
			padding: 20px 5px;
			background-color: #fff;
			border-radius: 5px;
			// height: 80px;

			.way-list {
				display: flex;
				flex-direction: row;
				justify-content: space-between;
				align-items: center;
				margin-top: 10px;

				.way-left {
					display: flex;
					flex-direction: row;
					align-items: center;

					.way-img {
						width: 20px;
						height: 20px;
					}

					.way-info {
						display: flex;
						flex-direction: column;
						margin-left: 10px;

						.info {
							font-size: 14px;
							color: #bbb;
						}
					}
				}
			}
		}


		.popup-title {
			height: 40px;
			line-height: 40px;
			background-color: #eee;
			text-align: center;
		}

		.way-box {
			padding: 5px;

			.way-item {
				list-style: none;
				padding: 5px;
				border-bottom: 1px solid #eee;
				display: flex;
				justify-content: space-between;

				.way-left {
					display: flex;
					flex-direction: row;
					align-items: center;

					.way-img {
						width: 20px;
						height: 20px;
					}

					.way-info {
						display: flex;
						flex-direction: column;
						margin-left: 10px;

						.info {
							font-size: 14px;
							color: #bbb;
						}
					}
				}

				.way-right {
					display: flex;
					flex-direction: row;
					align-items: center;

					.checked {
						width: 15px;
						height: 15px;
					}
				}
			}
		}
	}
</style>
