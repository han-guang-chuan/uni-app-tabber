<template>
	<view class="content">
		<navigator url="../index_page/index_page">前往二级页面</navigator>
	</view>
</template>

<script>
	var bitmap = null;
	export default {
		data() {
			return {
				title: '首页'
			}
		},
		onShow() {
			var icon = plus.nativeObj.View.getViewById("icon");
			if (icon) {
				setTimeout(function(){
					icon.show();
				},100)
			}
		},
		onLoad() {
			bitmap = new plus.nativeObj.Bitmap('bmp1');
			bitmap.loadBase64Data('data:image/png;base64,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', function() {}, function(e) {});
			this.createtab();
		},
		methods: {
			createtab: function(){
				// 设置水平居中位置
				var leftPos = Math.ceil((plus.screen.resolutionWidth - 60) / 2);
				var view = new plus.nativeObj.View('icon', {
					bottom: '19px',
					left: leftPos + 'px',
					width: '60px',
					height: '60px'
				});
				view.drawBitmap(bitmap, {
					tag: 'font',
					id: 'icon',
					src: '/static/app-tabber/app-tabber.png',
					position: {
						top: '0px',
						left: '5px',
						width: '50px',
						height: '100%'
					}
				});
				view.addEventListener("click", function(e) {
					uni.switchTab({
						url: '/pages/app-tabber/index_2'
					})
				}, false);
				view.show();
			}
		}

	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}
	.logo{
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
	}
	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
