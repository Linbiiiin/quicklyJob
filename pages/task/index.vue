<template>
	<view class="mainContainer">
		<view class="headerContainer">
			<view class="spaceBar"></view>
			<view class="header">
				<view class="posName">厦门·软件园</view>
				<view class="searchContainer">
					<uni-search-bar radius="20" placeholder="输入框" bgColor="#fff" @confirm="search" />
				</view>
			</view>
			<!-- <view class="fastMenu"></view> -->
		</view>
		<view class="subHeader">
			<div class="title">
				<uni-title type="h4" title="精选兼职" color="#000"></uni-title>
			</div>
			<div class="fastFilter">
				<selector :options="fastFilter" size="normal" />
				<uni-tag class="filter" text="筛选" size="normal" @click="openFilterPopup" />
			</div>
		</view>
		<view class="listContainer">
			<uni-list :border="false">
				 <uni-list-item v-for="(item, index) in listData" class="uni-radius-lg task-item" direction="column">
					<template v-slot:header>
						<view class="card-desc">{{item.desc}}</view>
						<view class="card-header">
							<div class="shop-name uni-h4">{{item.title}}</div>
							<div class="commission uni-h4">{{item.commission}}{{item.unit}}</div>
						</view>
					</template>
					<template v-slot:body>
						<view class="card-body">
							<view class="card-tag">
								<uni-tag text="标签" size="mini" />
								<uni-tag text="标签" size="mini" />
								<uni-tag text="标签" size="mini" />
								<uni-tag text="标签" size="mini" />
							</view>
							<view class="shop-pos"></view>
						</view>
					</template>
					<template v-slot:footer>
						<view class="card-footer">
							<button size="mini">接单</button>
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
			console.log(i)
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
	
	export default {
		data() {
			return {
				listData: genData(100),
				fastFilter: [
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
				]
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
		}
	}
</script>

<style  lang="scss">
.spaceBar {
	width: 100%;
	height: var(--status-bar-height);
}
.mainContainer {
	width: 100%;
}
.headerContainer {
}
.listContainer {
	padding: 20rpx 20rpx 100rpx 20rpx;
	box-sizing: border-box;
	.uni-list {
		background-color: unset;
		.task-item {
			margin-bottom: 20rpx;
		}
	}
}
.card-footer {
	
}
.header {
	display: flex;
	align-items: center;
	padding: 0 20rpx;
}
.searchContainer {
	flex: 1;
}
.subHeader {
	position: sticky;
	left: 0;
	top: -1px;
	z-index: 99;
	display: flex;
	align-items: center;
	padding: 0 30rpx;
	border-radius: 40rpx 40rpx 0 0;
	background-color: #fff;
}
.title {
	margin-right: 60rpx;
}
.fastFilter {
	flex: 1;
	display: flex;
	justify-content: flex-end;
	.filter {
		
		color: $uni-primary;
		border: none;
		background-color: $uni-primary-light;
		&::after {
			content: '';
			display: inline-block;
			margin-left: 10rpx;
			margin-bottom: -2rpx;;
			width: 0;
			height: 0;
			border-style: solid;
			border-width: 3px;
			border-color: transparent $uni-primary $uni-primary transparent;
		}
	}
}
.card-desc {
	font-size: 24rpx;
	color: $uni-extra-color;
}
.card-header {
	display: flex;
	margin-top: 20rpx;
}
.card-header {
	.shop-name {
		flex: 1;
		margin-right: 30rpx;
		font-weight: 700;
		color: $uni-main-color;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}
	.commission {
		color: rgba(245, 54, 54, 1);
	}
}
.card-body {
	> .card-tag {
		margin: 20rpx 0;
		> * {
			margin-right: 20rpx;
		}
	}
}
.card-footer {
	display: flex;
	justify-content: flex-end;
	button {
		margin: 0;
		color: $uni-primary;
		background-color: $uni-primary-light;
		&::after {
			border: none;
		}
	}
}

</style>
