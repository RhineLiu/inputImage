# inputImage
为Mobile端JS上传照片或拍照提供接口：
- 自动创建input file并在使用后销毁
- 用户可以选择使用拍照或相册里的照片，接口可选择返回File、Image、Base64格式图片
- 解决手机拍照后在canvas中绘制会被旋转的问题(使用了EXIF信息插件)
- 可自定义尺寸等比例缩放图片，用于缩略图或者压缩上传图片

# Quick Start
```html
<button id="upload">Upload Image</button>
<img id="original_image">
<img id="resize_image">
<img id="adjust_image">
<script src='exif.js'></script>
<script src='inputImage.js'></script>
<script>
upload.addEventListener('click', function () {
    inputImage.input({
        camera: true, // use camera
        multiple: false, // take only one photo
        format: 'image',
        success: function (files) {
            original_image.src = files[0].src;
            // 尺寸不变的图片,可以用来绘制
            inputImage.adjust({
                image: files[0],
                success: function (base64) {
                    adjust_image.src = base64;
                }
            });
            // 尺寸变小的图片，可以用来做缩略图或压缩图片
            inputImage.resize({
                image: files[0],
                max: 120,
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
<img src="https://vmllab-js.github.io/inputImage/imgs/qrcode.png" width="30%"><br>
https://vmllab-js.github.io/inputImage