<script>
	export default {
		onLaunch: function () {
			console.log('App Launch')
		},
		onShow: function () {
			console.log('App Show')
		},
		onHide: function () {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	page {
		min-height: 100%;
		display: flex;
	}
	.content{
		flex: 1;
		width: 100%;
		font-size:28px;
		color:#333333;
		font-family: -apple-system, BlinkMacSystemFont, "PingFang SC","Helvetica Neue",STHeiti,"Microsoft Yahei",Tahoma,Simsun,sans-serif;
		background-color:#F6F6F6;
	}
	.ellipsis{
		white-space: nowrap;
		text-overflow: ellipsis;
		overflow: hidden;
	}
</style>
