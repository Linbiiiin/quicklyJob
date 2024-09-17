<template>
	<view class="mainContainer">
		<view class="headerContainer">
			<view class="spaceBar"></view>
			<view class="header">
				<view class="posName">厦门·软件园</view>
				<view class="searchContainer">
					<wd-search hide-cancel />
				</view>
			</view>
			<!-- <view class="fastMenu"></view> -->
		</view>
		<wd-sticky :offset-top="-50">
			<view class="subHeader">
				<text class="title">
					精选推荐
				</text>
				<view class="fastFilter">
					<wd-tag v-for="tag in fastFilterOptions" :custom-class="activeFastFilter !== tag.value ? 'fast-tag': 'fast-tag-active'" text="筛选" size="normal" @click="onChangeFastFilter(tag)">{{tag.label}}</wd-tag>
					<wd-tag custom-class="filter-tag" text="筛选" size="normal" @click="openFilterPopup">
						筛选
					</wd-tag>
				</view>
			</view>
		</wd-sticky>
		<view class="listContainer">
			<uni-list :border="false">
				<uni-list-item v-for="(item, index) in listData" class="uni-radius-lg task-item" direction="column">
					<template v-slot:header>
						<view class="card-desc">{{item.desc}}</view>
						<view class="card-header">
							<div class="shop-name">{{item.title}}</div>
							<div class="commission">{{item.commission}}{{item.unit}}</div>
						</view>
					</template>
					<template v-slot:body>
						<view class="card-body">
							<view class="card-tag">
								<wd-tag custom-class="task-tag" size="small">标签</wd-tag>
								<wd-tag custom-class="task-tag" size="small">标签</wd-tag>
								<wd-tag custom-class="task-tag" size="small">标签</wd-tag>
								<wd-tag custom-class="task-tag" size="small">标签</wd-tag>
							</view>
							<view class="shop-pos"></view>
						</view>
					</template>
					<template v-slot:footer>
						<view class="card-footer">
							<wd-button size="small" plain @click="onClickTask(item)">接单</wd-button>
						</view>
					</template>
				</uni-list-item>
			</uni-list>
		</view>
		<uni-popup :is-mask-click="false" ref="filterPopup" background-color="#fff" @change="">
			<view class="popup-content">
				<text class="text">popup 内容</text>
			</view>
		</uni-popup>
	</view>
</template>

<script steup>
	function genData(num) {
		const result = [];

		for (let i = 0; i < num; i++) {
			result.push({
				id: i + 1,
				desc: '测试小标题',
				title: '测试内容描述测试内容描述测试内容描述测试内容描述测试内容描述',
				tag: ['标签', '标签', '标签', '标签'],
				commission: parseInt(Math.random() * 100),
				unit: '元/小时'
			});
		}

		return result;
	}
	const FAST_FILTER_OPTIONS = [
		{
			label: '推荐',
			value: '0'
		},
		{
			label: '附近',
			value: '1'
		},
		{
			label: '最新',
				value: '2'
		}
	];

	export default {
		data() {
			return {
				listData: genData(100),
				fastFilterOptions: FAST_FILTER_OPTIONS,
				activeFastFilter: FAST_FILTER_OPTIONS[0].value,
			}
		},
		methods: {
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			openFilterPopup() {
				// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
				this.$refs.filterPopup.open('bottom')
			},
			onChangeFastFilter(e) {
				this.activeFastFilter = e.value;
			},
			onClickTask(e) {
				console.log(e);
				uni.navigateTo({
					url: '/pages/taskDetail/index',
					animationType: 'pop-in',
				})
			}
		}
	}
</script>

<style lang="scss">
	.spaceBar {
		width: 100%;
		height: var(--status-bar-height);
	}

	.mainContainer {
		width: 100%;
	}

	.headerContainer {}

	.listContainer {
		padding: 10px 10px 50px 10px;
		box-sizing: border-box;

		.uni-list {
			background-color: unset;

			.task-item {
				margin-bottom: 10px;
			}
		}
	}

	.card-footer {}

	.header {
		display: flex;
		align-items: center;
		height: 50px;
		padding: 0 10px;
		background-color: #fff;

		.searchContainer {
			flex: 1;

			.wd-search {
				background: unset !important;
			}
		}
	}

	.subHeader {
		// position: sticky;
		// left: 0;
		// top: -1px;
		// z-index: 99;
		width: 100vw;
		display: flex;
		align-items: center;
		padding: 10px 15px;
		overflow: hidden;
		box-sizing: border-box;
		background-color: #fff;		
		.title {
			margin-right: 30px;
		}
		
		.fastFilter {
			flex: 1;
			display: flex;
			justify-content: flex-end;
			.fast-tag {
				margin-right: 10px;
			}
			.fast-tag-active {
				margin-right: 10px;
				color: var(--primary-color) !important;
				background: #d1e3f7 !important;
			}
			.filter-tag {
				padding: 3px 5px;
				color: var(--primary-color) !important;
				background: #d1e3f7 !important;
				&::after {
					content: '';
					display: inline-block;
					margin-left: 5px;
					margin-bottom: -1px;
					;
					width: 0;
					height: 0;
					border-style: solid;
					border-width: 3px;
					border-color: transparent var(--primary-color) var(--primary-color) transparent;
				}
			}
		}
	}
	
	.task-tag {
		padding: 3px 5px !important;
		color: rgba(0,0,0,0.65) !important;
		background: #ededed !important;
	}

	.card-desc {
		font-size: 12px;
		// color: $uni-extra-color;
	}

	.card-header {
		display: flex;
		margin-top: 10px;
	}

	.card-header {
		.shop-name {
			flex: 1;
			margin-right: 15px;
			font-weight: 700;
			font-size: 18px;
			// color: $uni-main-color;
			overflow: hidden;
			text-overflow: ellipsis;
			white-space: nowrap;
		}

		.commission {
			font-size: 18px;
			color: rgba(245, 54, 54, 1);
		}
	}

	.card-body {
		.card-tag {
			margin: 10px 0;

			.wd-tag {
				margin-right: 10px;
			}
		}
	}

	.card-footer {
		display: flex;
		justify-content: flex-end;

		button {
			margin: 0;

			// color: $uni-primary;
			// background-color: $uni-primary-light;
			&::after {
				border: none;
			}
		}
	}
</style>