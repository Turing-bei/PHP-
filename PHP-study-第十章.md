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

#### 图片验证码实例

```php+HTML
<!-- html 的代码 -->
<! doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>用户注册</title>
        <style>
        img{
          cursor: pointer;
        }
        img:hover{
          box-shadow: 0 0 3px 3px #272822;
        }
        </style>
    </head>
    <body>
        <h2>用户注册</h2>
        <hr>
        <form action="./reg.php" method="post">
            <p>
                用户名
            </p>
            <p>
                <input type="text" value='user1' name='username'>
            </p>
            <p>
                密码
            </p>
            <p>
                <input type="passdword" value='123' name='password'>
            </p>
            <p>
                验证码
            </p>
            <p>
                <img src="verify.php" onclick="this.src='verify.php?rand=' + Math.random()">
            </p>
            <p>
                输入验证码
            </p>
            <p>
                <input type="text" name='fcode'>
            </p>
            <p>
                <input type="submit" value="注册">
            </p>
        </form>
    </body>
</html>

<!-- verify.php 的代码 -->
<?php
    /* session 是实现多个页面共享数据的 */
    /* 要使用session 需要先开启session */

    session_start();

    /* 1. 创建画布资源 */
        $img = imagecreatetruecolor(120,30);
    
    /* 2. 准备颜色 */
        $white = imagecolorallocate($img,255,255,255);
        $black = imagecolorallocate($img,0,0,0);
        $red = imagecolorallocate($img,255,0,0);
        $green = imagecolorallocate($img,0,255,0);
        $blue = imagecolorallocate($img,0,0,255);
        $gray = imagecolorallocate($img,200,200,200);
        $yellow = imagecolorallocate($img,255,255,0);
        imagefill($img,0,0,$white);

        $arr = array_merge(range(0,9),range('a','z'),range('A','Z'));
        shuffle($arr);
        $randStr = join('',array_slice($arr,0,5));
        
        /* 把随机字符串放到session数组中 */
        $_SESSION['vcode'] = $randStr;
        
        /* 显示文字 */
        imagettftext($img,20,0,20,22,$black,'./wryh.ttf',$randStr);

        /* 点干扰素 */
        for($i=0;$i<50;$i++){
            imagesetpixel($img,mt_rand(0,100),mt_rand(0,30),$blue);
        }

        /* 线干扰素 */
        for($j=0;$j<15;$j++){
            imageline($img,mt_rand(0,100),mt_rand(0,30),mt_rand(0,100),mt_rand(0,30),$blue);
        }

        /* 曲干扰素 */
        for($x=0;$x<10;$x++){
            imageellipse($img,mt_rand(0,100),mt_rand(0,30),mt_rand(1,100),mt_rand(0,100),$blue);
        }

		header('content-type: image/png');
    	imagepng($img);

        imagedestroy($img);
?>

<!-- reg.php 的代码 -->
<?php
    /* 开启session才可以取出其他页面放到session数组中的数据 */
    session_start();

    /* 获取表单中输入的验证码 */
    $fcode = strtolower($_POST['fcode']);

    /* 获取图片中的随机字符串 */
    $vcode =  strtolower($_SESSION['vcode']);

    /* 把验证码和随机字符串全部转成小写然后进行比较 */

    if($fcode == $vcode){
        echo "{$_POST['username']}注册成功！";
    }else{
        echo "验证码输入有误！";
    }

    echo "<script>alert('注册成功！');location='./index.php'</script>"
?>
```

#### 图片缩放

```PHP
<?php
    /* 大图资源 */
    $srcimg = imagecreatefromjpeg('a.jpg');

	/* 小图资源 */
	$dstimg = imagecreatetruecolor(381,251);

	/* 把大图缩放到小图上去 */
	imagecopyresampled($dstimg,$srcimg,0,0,0,0,381,251,910,600);

	/* 输出最终图像或保存最终图像 */
	header('content-type: image/jpg');
	imagejpeg($dstimg,'sm_a.jpg');
	
	/* 释放画布资源 */
	imagedestroy($img);
	
?>
```

#### 图片裁剪

```PHP
<?php
    /* 主图资源 */
    $srcimg = imagecreatefromjpeg('a.jpg');

	/* 裁剪资源 */
	$dstimg = imagecreatetruecolor(381,251);

	/* 把主图裁剪到裁剪图上去 */
	imagecopyresampled($dstimg,$srcimg,0,0,200,2000,381,251,300,200);

	/* 输出最终图像或保存最终图像 */
	header('content-type: image/jpg');
	imagejpeg($dstimg,'sm_a.jpg');
	
	/* 释放画布资源 */
	imagedestroy($img);
?>
```

#### 图片水印

```PHP
<?php
     /* 大图资源 */
    $srcimg = imagecreatefromjpeg('a.jpg');

	/* 小图资源 */
	$dstimg = imagecreatefromjpeg('b.jpg');

	/* 把大图缩放到小图上去 */
	imagecopy($dstimg,$srcimg,0,0,0,0,100,100);

	/* 输出最终图像或保存最终图像 */
	header('content-type: image/jpg');
	imagejpeg($dstimg,'logo.jpg');
	
	/* 释放画布资源 */
	imagedestroy($img);
?>
```

#### 图片缩放函数

```PHP
<?php
    $img = 'uploads/img/cs.jpg';

	function thumb($img,$dstx,$dsty,$pre){
        /* 得到图片信息 */
        $arr = getimagesize($img);
        $srcx = $arr[0];
        $srcy = $arr[1];
        $srctype = $arr[2];
        
        /* 图片类型 */
        /* 变量函数 */
        switch($srctype){
            case 1:
                $imgform = 'imagecreatefromgif';
                $imgout = 'imagegif';
                break;
            case 2:
                $imgfrom = 'imagecreatefromjpeg';
                $imgout = 'imagejpeg';
              	break;
            case 3:
                $imgfrom = 'imagecreatefrompng';
                $imgout = 'imagepng';
                break;
        }
        
        /* 原图资源 */
        $srcimg = $imgfrom($img);
        
        /* 等比例算法 */
        $scale = max($srcx/$dstx,$srcy/$dsty);
        $dstx = floor($srcx/$scale);
        $dsty = floor($srcy/$scale);
        
        /* 目标资源 */
        $dstimg = imagecreatetruecolor($dstx,$dsty);
        
        /* 图片缩放 */
        imagecopyresampled($dstimg,$srcimg,0,0,0,0,$dstx,$dsty,$srcx,$srcy);
        
        /* 保存路径 */
       	$dir = dirname($img);
        $file = basename($img);
        $dstfile = $dir."/".$pre.$file;
        
        /* 保存图片 */
        $imgout($dstimg,$dstfile);
        
        /* 关闭资源 */
        imagedestroy($srcimg);
        imagedestroy($dstimg);
         
    }
	thumb($img,500,500,'t_500_');
	thumb($img,200,200,'t_200_');
?>
```



