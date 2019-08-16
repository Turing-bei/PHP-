## PHP学习笔记—第十章

#### 图片处理

#### PHP GD函数库

1. 处理图片
2. 画图

#### 处理图片

1. 验证码
2. 缩略图
3. 图片裁剪
4. 图片水印 

#### PHP中创建图像的步骤

```PHP
<?php
    /* 1. 创建画布资源 */
    	$img = imagecreatetruecolor(500,300);
    
    /* 2. 准备颜色 */
        $white = imagecolorallocate($img,255,255,255);
        $black = imagecolorallocate($img,0,0,0);
        $red = imagecolorallocate($img,255,0,0);
        $green = imagecolorallocate($img,0,255,0);
        $blue = imagecolorallocate($img,0,0,255);
        $gray = imagecolorallocate($img,200,200,200);
		$yellow = imagecolorallocate($img,255,255,0);

    /* 3. 在画布上画图像或文字 */
		imagefill($img,0,0,$black);

	/* 4. 在画布上画一个黄色的圆 */
		imagefilledellipse($img,250,150,200,200,$yellow);
    
    /* 5. 输出最终图像或保持最终图像 */
		imagejpeg($img,'a.jpg');
    
    /* 6. 释放画布资源 */
		imagedestroy($img);
    /* 7. 图片输出到浏览器上 */
		header('content-type: image/jpeg');
		header('content-type: image/png');
		header('content-type: image/gif');
?>
```

#### 绘制图像

```PHP
<?php
    $img = imagecreatetruecolor(500,300);
    $black = imagecolorallocate($img,0,0,0);
	$white = imagecolorallocate($img,255,255,255);
	imagefill($img,0,0,$white);

    /* 1. imagefill() 填充画布 */
		imagefill($img,0,0,$white);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 2. imagesetpixel() 画一个点像素  */
    	imagesetpixel($img,250,150,$black);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 3. imageline() 画线 */
    	imageline($img,0,0,500,300,$black);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 4. imagerectangle() 画一个矩形 */
		imagerectangle($img,10,10,490,290,$black);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 5. imagefilledrectangle() 画一个矩形并填充 */
    	imagefilledrectangle($img,10,10,490,290,$black);
		header('content-type: image/png');
    	imagepng($img);

    /* 6. imagepolygon() 画一个多边形 */
		$arr = array(
            250,50,
            50,250,
            450,150,
            450,50
        );
		imagepolygon($img,$arr,4,$balck);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 7. imagefilledpolygon() 画一个多边形并填充 */
		$arr = array(
            250,50,
            50,250,
            450,150,
            450,50
        );
		imagefilledpolygon($img,$arr,4,$balck);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 8. imageellipse() 画一个椭圆 */
		imageellipse($img,250,150,200,200,$balck);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 9. imagefilledellipse() 画一个椭圆并填充 */
		imagefilledellipse($img,250,150,200,200,$balck);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 10. imagearc() 画一个椭圆弧 */
		imagearc($img,250,150,200,200,0,180,$balck);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 11. imagefilledarc() 画一个椭圆弧并填充 */
		imagefilledarc($img,250,150,200,200,0,180,$balck,IMG_ARC_PIE);
		header('content-type: image/png');
    	imagepng($img);
    
    /* 12. imagettftext() 画字符串 需要引入字体*/
		$str = 'Turingbei'
		imagettftext($img,20,0,50,250,$balck,'./msyhbd.ttf',$str);
		header('content-type: image/png');
    	imagepng($img);
?>
```



