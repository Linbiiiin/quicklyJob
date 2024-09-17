<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	:root {
		.wd-tag.is-default {
			padding: 3px 5px;
			color: rgba(0,0,0,0.65) !important;
			background: #ededed !important;
		}
		.wd-card {
			padding: 10px !important;
			margin: 10px !important;
			.wd-card__title-content,
			.wd-card__footer {
				padding: 0 !important;
			}
		}
	}
	/*每个页面公共css */
	/* #ifndef APP-NVUE */
	page {
		background-color: #f5f5f5;
	}

	/* #endif */
</style>
