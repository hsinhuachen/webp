# WebP 圖片

## 轉換格式
### cwebp Encoder
Google 官方的 command line utility

	# 安裝
	$ brew install webp
	 
	# 轉檔
	$ cwebp -q 75 img_story_cuisine_3.jpg.jpg -o output.webp

### imagemin-webp

	npm install imagemin imagemin-webp

將 input 資料夾裡所有 .jpg 和 .png 圖片轉換成 .webp（影像品質設定為 75）

	const imagemin = require('imagemin');
	const webp = require('imagemin-webp');
	const convertImages = async () => {
	    const files = ['./input/*.{jpg,png}'];
	    const config = {
	        destination: './output',
	        plugins: [webp({ quality: 75 })],
	    };
		
	    console.log('開始轉換圖片⋯⋯');
	    await imagemin(files, config);
	    console.log('已將圖片轉成 WebP！');
	};
		
	convertImages();

	# 執行
	node webp.js

## 在 HTML 使用 WebP 圖片
	<picture>
	    <source srcset="aaa.webp" type="image/webp">
	    <img src="aaa.jpg" alt="">
	</picture>

## 在 CSS 使用 WebP 圖片
	 
	.webp .div-with-bg {
	    background-image: url("aaa.webp");
	}
	 
	.no-webp .div-with-bg {
	    background-image: url("aaa.jpg");
	}