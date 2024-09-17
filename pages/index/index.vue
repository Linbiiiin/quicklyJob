<template>
	<view class="container">
		<view class="viewContent">
			<Task v-if="tabs[0].path === tabbar"></Task>
			<!-- <Order v-if="tabs[1].path === tabbar"></Order> -->
			<My v-if="tabs[1].path === tabbar"></My>
		</view>
		<wd-tabbar fixed v-model="tabbar" @change="onTabarChange" bordered safeAreaInsetBottom placeholder>
		  <wd-tabbar-item v-for="tab in tabs" :name="tab.path" :title="tab.title" :icon="tab.icon"></wd-tabbar-item>
		</wd-tabbar>
	</view>
</template>

<script>
	import { ref } from 'vue'
	import Task from '@/pages/task';
	import Order from '@/pages/order';
	import My from '@/pages/my';
	
	const tabbar = ref(null);

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
						icon: 'chart-bubble',
						path: 'pages/task/index'
					},
					// {
					// 	title: '订单',
					// 	icon: 'list',
					// 	path: 'pages/order/index'
					// },
					{
						title: '我的',
						icon: 'user',
						path: 'pages/my/index'
					}
				],
				tabbar: 'pages/task/index'
			}
		},
		methods: {
			onTabarChange(e) {
				tabbar.value = e.value;
			}
		},
		mounted() {
		}
	}
</script>
<style scoped lang="scss">
	.container {
	}
</style>