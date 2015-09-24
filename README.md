baguetteBox.js
==============

baguetteBox.js 是一个简单和易于使用lightbox纯JavaScript脚本。

[Demo页面](https://feimosi.github.io/baguetteBox.js/)

![Demo页面快照](http://i.imgur.com/uLSDpuW.png)

## 特点

* 纯JS编写，无任何依赖
* 支持多重画廊(Multiple-gallery)效果, 且允许自定义参数 
* 支持手势滑动(仅在支持多点触控设备上)
* 现代简约风格
* 图像字幕支持
* 响应式的图像
* CSS3转换
* SVG按钮,没有额外的文件下载
* 压缩后大约2.3KB

## 安装方法

### 使用npm安装

`npm install baguettebox.js`

### 使用Bower

`bower install baguettebox.js`

### 通用安装方法安装

下载baguetteBox.min.css和baguetteBox.min.js文件并添加到你的页面:

  ```html
<link rel="stylesheet" href="css/baguetteBox.min.css">
<script src="js/baguetteBox.min.js" async></script>
  ```

## 用法

### 初始化脚本运行:

```js
baguetteBox.run('.gallery', {
  // Custom options
});
```
其中第一个参数是一个选择器（或画廊）包含一个标签。HTML代码可能看起来像这样：
```html
<div class="gallery">
	<a href="img/2-1.jpg" data-caption="Image caption"><img src="img/thumbs/2-1.jpg"></a>
	<a href="img/2-2.jpg"><img src="img/thumbs/2-2.jpg"></a>
  ...
</div>
```

To use captions put `title` or `data-caption` attribute on `a` tag.

demo
```
<!DOCTYPE html>
<head>
    <meta charset="utf-8">
    <title>demo</title>
	<link rel="stylesheet" href="css/baguetteBox.css">
	<script src="js/baguetteBox.js"></script>
</head>

<body>
    <div class="gallery">
    <a href="img/image-1.jpg" data-caption="图片描述"><img src="img/thumb-1.jpg"></a>
</div>
</body>

<script>
	baguetteBox.run('.gallery', {
	  // Custom options
	});
</script>
```

### Additional public methods

* `showNext` - switch to the next image
* `showPrevious` - switch to the previous image
* `destroy` - remove the plugin with any event bindings

The first two methods return true on success or false if there's no more images to be loaded.

## Responsive images

To use this feature, simply put `data-at-{width}` attributes on `a` tags with value being a path to the desired image. `{width}` should be the maximum screen width the image can be displayed at. The script chooses the first image with `{width}` greater than or equal to the current screen width for best user experience.
That last `data-at-X` image is used also in the case of a screen larger than X.

Here's an example of what the HTML code can look like:
```html
<a href="img/2-1.jpg" 
  data-at-450="img/thumbs/2-1.jpg" 
  data-at-800="img/small/2-1.jpg" 
  data-at-1366="img/medium/2-1.jpg" 
  data-at-1920="img/big/2-1.jpg">
    <img src="img/thumbs/2-1.jpg">
</a>
```
If you have 1366x768 resolution baguetteBox.js will choose `"img/medium/2-1.jpg"`. If, however, it's 1440x900 it'll choose `"img/big/2-1.jpg"`. Keep `href` attribute as a fallback (link to a bigger image e.g. of HD size) for older browsers.

## Customization

You can pass an object with custom options as a second parameter. The following are available with their corresponding defaults:
```javascript
{
  captions: true,       // true|false|callback(element) - Display image captions
  buttons: 'auto',      // 'auto'|true|false - Display buttons
  async: false,         // true|false - Load files asynchronously
  preload: 2,           // [number] - How many files should be preloaded from current image
  animation: 'slideIn', // 'slideIn'|'fadeIn'|false - Animation type
  afterShow: null,      // callback - To be run after showing the overlay
  afterHide: null,      // callback - To be run after hiding the overlay
  onChange: null,       // callback(currentIndex, imagesElements.length) - When image changes
  filter: /.+\.(gif|jpe?g|png|webp)/i // RegExp object - pattern to match image files
}
```
* `captions: 'callback'` applies a caption returned by the callback. Invoked in the context of an array of gallery images.
* `buttons: 'auto'` hides buttons on touch-enabled devices or when only one image is displayed.

## Compatibility

* IE 8+
* Chrome
* Firefox 3.6+
* Opera 12+
* Safari 5+
* Sleipnir

## Notes

Feel free to report any bugs!

## Credits

Creation of `baguetteBox.js` was inspired by a great jQuery plugin [touchTouch](https://github.com/martinaglv/touchTouch).

## License

Copyright (c) 2015 [feimosi](https://github.com/feimosi/)

This content is released under the [MIT License](http://opensource.org/licenses/MIT).
