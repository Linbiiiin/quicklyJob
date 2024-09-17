<template>
	<view class="my-container">
		<div class="my-header">
			<div class="my-setting">
				<wd-icon name="setting1" size="22px"></wd-icon>
			</div>
			<view class="my-card">
				<view class="my-avatar">
					<wd-img
					 :width="70"
					 :height="70"
					 round
					  :src="logoPng"
					/>
				</view>
				<view class="my-info">
					<view class="my-name">测试</view>
					<view class="my-tag">
						<wd-tag type="primary" plain round size="small">测试学校</wd-tag>
						<wd-tag type="primary" plain round size="small">27岁</wd-tag>
					</view>
				</view>
			</view>
		</div>
		<div class="my-content">
			<wd-card>
				<view class="my-task-stat">
					<view class="stat-item">
						<view class="stat-val">0</view>
						<view>全部报名</view>
					</view>
					<view class="stat-item">
						<view class="stat-val">0</view>
						<view>待录取</view>
					</view>
					<view class="stat-item">
						<view class="stat-val">0</view>
						<view>已录取</view>
					</view>
					<view class="stat-item">
						<view class="stat-val">0</view>
						<view>已结束</view>
					</view>
				</view>
			</wd-card>
			<wd-card>
				<view class="my-assets">
					<view class="card-title">我的资产</view>
					<view class="asstes-content">
						<view class="assets-stat">
							<wd-count-to class="assters-val" fontSize="20" :endVal="9999.99" :decimals="2" suffix="" color="#000"></wd-count-to>
							<view class="assets-desc">工资收入（元）</view>
						</view>
						<view class="assters-operator">
							<wd-button size="medium">提现</wd-button>
						</view>
					</view>
				</view>
			</wd-card>
			<wd-card>
				<view class="my-services">
					<view class="card-title">更多服务</view>
					<view class="my-services-list">
						<view class="service-item">
							<view class="service-icon">
								<wd-icon name="usergroup" color="#000" size="24px"></wd-icon>
							</view>
							<view class="service-name">切换至招聘者</view>
						</view>
						<view class="service-item">
							<view class="service-icon">
								<wd-icon name="attach" color="#000" size="24px"></wd-icon>
							</view>
							<view class="service-name">我的收藏</view>
						</view>
						<view class="service-item">
							<view class="service-icon">
								<wd-icon name="edit-1" color="#000" size="24px"></wd-icon>
							</view>
							<view class="service-name">用户协议</view>
						</view>
					</view>
				</view>
			</wd-card>
		</div>
	</view>
</template>

<script>
	import LogoPng from '@/static/logo.png';
	
	export default {
		data() {
			return {
				logoPng: LogoPng
			}
		}
	}
</script>

<style lang="scss">
	.my-container {
		.my-header {
			padding: 30px 10px;
			background: linear-gradient(to bottom, #c0dffb, transparent);
			.my-setting {
				padding: 0 20px;
				margin-bottom: 20px;
				text-align: right;
				.wd-icon {
					color: var(--UI-FG);
				}
			}
			.my-card {
				display: flex;
				align-items: center;
				.my-avatar {
					margin-right: 20px;
				}
				.my-info {
					.my-name {
						font-weight: 700;
						font-size: 20px;
						color: var(--UI-FG);
					}
					.my-tag {
						margin-top: 10px;
						.wd-tag {
							margin-right: 5px;
						}
					}
				}
			}
		}
		.my-content {
			.my-task-stat {
				display: flex;
				align-items: center;
				padding: 15px 0;
				.stat-item {
					flex: 1;
					text-align: center;
					font-size: 12px;
					color: var(--UI-FG-1);
					.stat-val {
						font-weight: 700;
						font-size: 20px;
						color: var(--UI-FG);
					}
				}
			}
		}
		.card-title {
			padding: 10px 0;
			font-weight: 700;
			font-size: 16px;
			color: var(--UI-FG);
		}
		.asstes-content {
			display: flex;
			align-items: flex-end;
			.assets-stat {
				flex: 1;
				display: flex;
				align-items: flex-end;
				overflow: hidden;
				.assters-val {
					margin-right: 4px;
					font-weight: 700;
				}
				.assets-desc {
					margin-bottom: 2px;
				}
			}
			.assters-operator {
				.wd-button {
					min-width: 80px;
					color: var(--primary-color);
					background: rgba(0, 122, 255, 0.1);
				}
			}
		}
		.my-services-list {
			display: flex;
			flex-wrap: wrap;
			margin: 10px 0;
			.service-item {
				width: 25%;
				text-align: center;
				.wd-icon {
					&::before {
						font-weight: 700;
					}
				}
				.service-name {
					font-size: 14px;
					color: var(--UI-FG-1);
				}
			}
		}
	}
</style>