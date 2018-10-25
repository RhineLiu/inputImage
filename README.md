# inputImage
为Mobile端JS上传照片或拍照提供接口：
- 自动创建input file并在使用后销毁
- 用户可以选择使用拍照或相册里的照片，接口可选择返回File、Image、Base64格式图片
- 解决手机拍照后在canvas中绘制会被旋转的问题
- 可自定义尺寸等比例缩放图片，用于缩略图或者压缩上传图片

# Quick Start
```html
<button id="upload">上传图片</button>
<script src='exif.js'></script>
<script src='inputImage.js'></script>
<script>
upload.addEventListener('click', function () {
	inputImage.input({
		format: 'image',
		success: function (files) {
			preview_image.src = files[0].src;
			// 尺寸不变的图片,可以用来绘制
			inputImage.adjust({
				image: files[0],
				success: function (base64) {
					adjust_image.src = base64;
				}
			});
			// 尺寸变小的图片,可以用来检测脸
			inputImage.resize({
				image: files[0],
				min: 480,
				success: function (base64) {
					resize_image.src = base64;
				}
			});
		}
	});
});
</script>
```

# Examples
https://vmllab-js.github.io/inputImage