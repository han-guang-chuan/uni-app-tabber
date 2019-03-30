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
			bitmap.load('static/app-tabber/app-tabber.png', function() {}, function(e) {});
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
