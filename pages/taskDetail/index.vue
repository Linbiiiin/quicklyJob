<template>
	<view class="part-job">
		<wd-card>
			<template #default>
					<view class="card-tooltip">求职保障</view>
					<view class="job-title">兼职标题</view>
					<view class="job-salary">17元/小时</view>
					<view class="job-tags">
						<wd-tag>标签名称</wd-tag>
						<wd-tag>标签名称</wd-tag>
						<wd-tag>标签名称</wd-tag>
						<wd-tag>标签名称</wd-tag>
					</view>
					<view class="job-process">
						<wd-img
						 :width="20"
						 :height="20"
						  :src="logoPng"
						  round
						/>
						<view class="job-report-num">已有1人报名</view>
					</view>
			</template>
		</wd-card>
		<wd-card>
			<template #default>
				<view class="job-info" v-for="item in workerContentOptions">
					<view class="job-info-header">
						<wd-icon :name="item.icon" :color="item.color" size="18px"></wd-icon>
					</view>
					<view class="job-info-content">
						<view class="job-info-name">{{item.name}}</view>
						<view class="job-info-desc">{{item.content}}</view>
					</view>
				</view>
			</template>
		</wd-card>
		<view class="card-title">职位详情</view>
		<wd-card>
			<template #default>
				<view class="pos-detail">
					年龄调整到16周岁就可以<br />
					湖州水上乐园<br />
					16周岁以上暑假工<br />
					
					工作内容：主要负责景区安全工作，不用干活，在游乐场做安全员～检票的工作<br />
					
					上班时间：7：00-18：00<br />
					
					工资待遇：一个小时15元，要求工资保密，自己招聘的只有12元一个小时，综合工资4500左右，每个月20日发放上个月工资
					
					<br />工资工期：6月20号-8月20号左右<br />
					
					吃住条件：吃住都在景区，每天饭补22元，够吃三餐，入职卡里充值500元，吃完再充值，不用自己花钱，住景区酒店公寓，四个人一间，水电费全免，独立卫生间～空调～热水器～电视～阳台
					
				</view>
			</template>
		</wd-card>
		
		<view class="card-title">发布者</view>
		<wd-card>
			<template #default>
				<view class="recruiter">
					<view class="recruiter-picture">
						<wd-img
						 :width="40"
						 :height="40"
						 round
						  :src="logoPng"
						/>
					</view>
					<view class="recruiter-info">
						<view class="recruiter-name">发布者</view>
						<view class="recruiter-auth">
							<wd-icon name="check-outline" color="orange" size="12px"></wd-icon>
							个人认证
						</view>
					</view>
				</view>
			</template>
		</wd-card>
		
		<view class="card-title">发布企业</view>
		<wd-card>
			<template #default>
				<view class="recruiter">
					<view class="recruiter-picture">
						<wd-img
							 :width="40"
							 :height="40"
							 round
							  :src="logoPng"
						/>
					</view>
					<view class="recruiter-info">
						<view class="recruiter-name">发布企业发布企业发布企业发布企业发布企业发布企业发布企业发布企业
						</view>
						<view class="recruiter-auth">
							<wd-icon name="check-outline" color="orange" size="12px"></wd-icon>
							个人认证
						</view>
					</view>
				</view>
			</template>
		</wd-card>
		<wd-card>
			<template #default>
				<view class="task-tip">
					<view class="task-tip-title">
						<wd-icon name="notification-filled" color="#34d19d" size="16px"></wd-icon>
						小贴士
					</view>
					<view class="task-tip-content">
						兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中兼职过程中
					</view>
				</view>
			</template>
		</wd-card>
		<view class="task-operator">
			<wd-button type="info" size="large">立即沟通</wd-button>
			<wd-button size="large">我要兼职</wd-button>
		</view>
		<wd-gap bg-color="transparent" height="60px"></wd-gap>
	</view>
</template>

<script>
	import LogoPng from '@/static/logo.png';
	const WORKER_CONTENT_OPTIONS = [
		{
			name: '工作日期',
			icon: 'calendar',
			color: '#8268de',
			content: '每周工作天数3~4天'
		},
		{
			name: '工作时段',
			icon: 'time',
			color: '#fa4350',
			content: '每周工作天数3~4天'
		},
		{
			name: '具体位置',
			icon: 'location',
			color: '#f0883a',
			content: '每周工作天数3~4天'
		},
		{
			name: '职位要求',
			icon: 'app',
			color: '#f0cf1d',
			content: '每周工作天数3~4天'
		},
	]
	
	export default {
		data() {
			return {
				logoPng: LogoPng,
				workerContentOptions: WORKER_CONTENT_OPTIONS,
			}
		}
	}
</script>

<style lang="scss">
	$baseMarginBottom: 14px;
	
	.part-job {
		overflow: hidden;
		.wd-card {
			.wd-card__content {
				padding: 10px 0 !important;
			}
			.card-tooltip {
				margin-bottom: $baseMarginBottom;
				font-size: 12px;
				color: var(--UI-FG-1);
			}
			.job-title {
				margin-bottom: $baseMarginBottom;
				font-weight: 700;
				font-size: 20px;
				color: var(--UI-FG);
			}
			.job-salary {
				margin-bottom: $baseMarginBottom;
				font-size: 18px;
				color: red;
			}
			.job-tags {
				margin-bottom: $baseMarginBottom;
				.wd-tag {
					margin-right: 10px;
				}
			}
			.job-process {
				display: flex;
				align-items: center;
				font-size: 14px;
				color: var(--UI-FG-1);
				.job-report-num {
					margin-left: 10px;
				}
			}
			
			.job-info {
				display: flex;
				margin-bottom: 10px;
				.wd-icon {
					margin-right: 10px;
				}
				.job-info-content {
					padding-top: 4px;
					.job-info-name {
						display: flex;
						align-items: center;
						font-size: 12px;
						color: var(--UI-FG-1);
					}
					.job-info-desc {
						margin-top: 6px;
						font-size: 14px;
						color: var(--UI-FG);
					}
				}
			}
		}
		.card-title {
			padding: 10px 10px 0 10px;
			font-weight: 700;
			font-size: 18px;
			color: var(--UI-FG);
		}
		.pos-detail {
			font-size: 14px;
			color: var(--UI-FG);
		}
		.recruiter {
			display: flex;
			align-items: center;
			.recruiter-picture {
				margin-right: 10px
			}
			.recruiter-info {
				flex: 1;
				overflow: hidden;
				.recruiter-name {
					width: 100%;
					font-weight: 700;
					font-size: 16px;
					color: var(--UI-FG);
					white-space: nowrap;
					overflow: hidden;
					text-overflow: ellipsis;
				}
				.recruiter-auth {
					display: flex;
					align-items: center;
					font-size: 12px;
					color: var(--UI-FG-1);
					.wd-icon {
						margin-right: 4px;
					}
				}
			}
		}
		.task-tip {
			.task-tip-title {
				margin-bottom: 4px;
				font-size: 16px;
				color: var(--UI-FG);
			}
			.task-tip-content {
				font-size: 12px;
				color: var(--UI-FG-1);
			}
		}
		.task-operator {
			display: flex;
			align-items: center;
			position: fixed;
			left: 0;
			bottom: 0px;
			width: 100%;
			height: 60px;
			padding: 0 15px;
			box-sizing: border-box;
			background-color: #fff;
			.wd-button {
				flex: 1;
				&:first-child {
					margin-right: 15px;
				}
			}
		}
	}
</style>