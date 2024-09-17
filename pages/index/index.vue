<template>
	<view class="container">
		<view class="viewContent">
			<Task v-if="tabs[0].path === activeTabPath"></Task>
			<Order v-if="tabs[1].path === activeTabPath"></Order>
			<My v-if="tabs[2].path === activeTabPath"></My>
		</view>
		<view class="tabContainer">
			<tabBar :tabs="tabs" @change="onChangeTabar" />
		</view>
	</view>
</template>

<script>
	import Task from '@/pages/task';
	import Order from '@/pages/order';
	import My from '@/pages/my';
	
	export default {
		components: {
			Task,
			My,
			Order
		},
		data() {
			return {
				tabs: [
					{
						title: '兼职广场',
						icon: 'navigate',
						path: 'pages/task/index'
					},
					{
						title: '订单',
						icon: 'list',
						path: 'pages/order/index'
					},
					{
						title: '我的',
						icon: 'person-filled',
						path: 'pages/my/index'
					}
				],
				activeTabPath: 'pages/task/index',
			}
		},
		methods: {
			onChangeTabar(tab) {
				this.activeTabPath = tab?.path;
			}
		}
	}
</script>
<style scoped lang="scss">
	.container {
		display: flex;
		flex-direction: column;
		width: 100%;
		height: 100%;
		.viewContent {
			flex: 1;
			overflow: auto;
		}
		.tabContainer {
			
		}
	}
</style>