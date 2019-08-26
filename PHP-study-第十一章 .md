## PHP学习笔记—第十一章

#### 文件目录操作

1. 文件操作
2. 目录操作
3. 文件上传
4. 文件下载

#### 文件基础操作

```PHP
<?php
    /* 1. filetype() 测试文件类型 */
    	$file = 'uploads/img';
		echo filetype($file);
		/* 打印结果：dir */
    
    /* 2. is_dir() 判断目录 */
		$file = 'uploads/img';
		echo var_dump(is_dir($file));
		/* 打印结果：bool(true) */
    
    /* 3. is_file() 判断文件 */
		$file = 'uploads/img';
		echo var_dump(is_file($file));
		/* 打印结果：bool(false) */
    
    /* 4. file_exists() 判断目录或文件是否存在 */
		$file = 'uploads/img';
		echo var_dump(file_exists($file));
		/* 打印结果：bool(true) */
    
    /* 5. filesize() 文件大小 */
		$file = 'uploads/img/cs.jpg';
		echo var_dump(filesize($file));
		/* 打印结果：int(23575) 字节 */
?>
```

#### 文件操作

```PHP
<?php
    /* 0. 文件打开 fopen() */
    	$file = 'a.txt';
    	fopen($file,type);
		type: 'r' 'w' 'a';
		/* r代表读取，w代表创建，a代表追加式写入 */
    
    /* 1. 读取文件 fread() readfile() file_get_contents() */
    	$file = 'a.txt';
		$size = filesize($file);
		$fp = fopen($file,'r');
		$str = fread($fp,$size);
		echo $str;

		$file = 'a.txt';
		readfile($file);
		
		$sfile = 'https://www.baidu.com';
		$str = file_get_contents($sfile);
		$ptn = '/<title>(.+)<\/title>/';
		preg_match($ptn,$str,$arr);
		echo '<h1>采集网站的标题为：</h1>';
		echo "<p>{$arr[1]}</p>";

    /* 2. 文件复制 copy()*/
    	$afile = 'aaa.txt';
		$bfile = 'bbb.txt';
		copy($afile,$bfile);

    /* 3. 重命名 rename() */
    	$afile = 'a.txt';
		$bfile = 'b.txt';
		rename($afile,$bfile);

    /* 4. 关闭文件 fclose()*/
		$file = 'a.txt';
		$fp = fopen($file,'w');
    	fclose($fp);

    /* 5. 创建文件 */
		$fp = fopen('a.txt','w');
    
    /* 6. 写入文件 fwrite() file_put_contents() */
    	$file = 'a.txt';
		$fp = fopen($file,'w');
		$str = 'Turingbei';
		fwrite($fp,$str);
		file_put_contents($fp,$str);
		fclose($fp);

    /* 7. 删除文件 */
		$file = 'a.txt';
		unlink($file);
?>
```

#### 目录操作

```PHP
<?php
    /* 遍历目录 */
    	/* opendir() 打开目录资源*/
    	/* readdir() 目录读取 */
    	/* closedir() 关闭目录资源 */
    	/* scandir() 目录遍历 */
    	$dir = 'home';
		$rd = opendir($dir);
		while($file = readdir($rd)){
            if($file != '.' && $file != '..'){
                echo $file;
                echo '<br>';
            }
        }
		$files = scandir($dir);
		foreach($files as $file){
            if($file != '.' && $file != '..'){
                echo $file;
                echo '<br>';
            }
        }
		closedir($rd);
    
    /* 创建目录 mkdir() */
    	$dir = 'admin/shop';
		mkdir($dir);
    
    /* 删除空目录 rmdir() */
    	$dir = 'admin/shop';
		rmdir($dir);
            
    /* 删除非空目录 */
    	$dir = 'home';
		function deldir($dir){
            $files = scandir($dir);
            foreach($files as $file){
                if($file != '.' && $file != '..'){
                    $path = $dir.'/'.$file;
                    if(is_dir($path)){
                        deldir($path);
                    }else{
                        unlink($path);
                    }
                }
            }
           	rmdir($dir);
        }
    /* 复制目录 */
		$srcdir = 'home';
		$dstdir = 'admin';
		function copydir($srcdir,$dstdir){
            if(!file_exists($dstdir)){
                mkdir($dstdir);
            }
            $files = scandir($srcdir);
            foreach($files as $file){
                if($file != '.' && $file != '..'){
                    $srcpath = $srcdir.'/'.$file;
                    $dstpath = $dstdir.'/'.$file;
                    if(is_dir($srcpath)){
                        copydir($srcpath,$dstpath);
                    }else{
                        copy($srcpath,$dstpath);
                    }
                }
            }
        }
		copydir($srcdir,$dstdir);
?>
```

#### 文件上传

```php+HTML
<!-- move_uploaded_file() 主要是这个方法 -->
<!doctype html>
<html lang='en'>
	<head>
    	<meta charset="UTF-8">
        <title>文件上传</title>
    </head>
    <body>
        <h3>
            文件上传
        </h3>
        <hr>
        <form action="up.php" method="post" enctype="multipart/form-data">
            <p>
                上传图片
            </p>
            <p>
                <input type="file" name="img">
            </p>
            <p>
                <input type="submit" value="上传">
            </p>
        </form>
    </body>
</html>
<!-- up.php -->
<?php
	if(!$_FILES){
        echo '文件上传大小超过了表单限制';
        exit();
    }
	/* 获取文件上传错误码 */
	$error = $_FILES['img']['error'];
	if($error == 0){
       	/* 只允许上传png或jpg图片文件 */
        $allow = array('jpg','png');

        /* 只允许上传500KB以内的图片 */
        $allowsize = 500*1024;
        $name = $_FILES['img']['name'];
        $ext = array_pop(explode('.',$name));
        $size = $_FILES['img']['size'];
        $tmp_name = $_FILES['img']['tmp_name'];
        $tfile = time().mt_rand().'.'.$ext;

        $target = 'uploads/'.$tfile;

        if($size<$allowsize){
            if(in_array($ext,$allow)){
                if(move_uploaded_file($tmp_name,$target)){
                    echo "文件{$name}上传成功！";
                }
            }else{
                echo '只允许上传jpg|png图片文件！';
            }
        }else{
            echo '只允许上传500KB以内的图片！';
        }
    }else if($error == 1){
       echo '文件上传大小超过20M';
    }else if($error == 4){
        echo '请你先选择图片';
    }

	/* php设置文件上传大小：该配置在php.ini
	1. upload_max_filesize = 20M
	文件上传框上传的文件最大大小。
	上传文件大小超过该值则报1错误码。
	2.post_max_size = 200M
	表单post传输允许的最大大小。
	上传文件大小超过该值则$_FILES为空数组。*/
?>
```

#### 文件下载

```php+HTML
<?php
	// 获取files中的文件
	$dir = 'files';
	$files = scandir($dir);
?>
<! doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>文件下载页面</title>
    </head>
    <body>
        <h2>
            页面下载页面
        </h2>
        <hr>
        <?php
        	foreach($files as $file){
                if($file != '.' && $file != '..'){
                    $filepath = $dir.'/'.$file;
                    echo "<p>{$file}<a href='down.php?filepath={$filepath}'>下载</a></p>";
                }
            }
        ?>
    </body>
</html>
<!-- down.php -->
<?php
    $file = $_GET['filepath'];
	$filepath = 'files/'.$file;
	$size = filesize($filepath);

	// 文件下载
    /* 1. 设置文件mime类型 */
    header("content-type:application/octet-stream"); 
    
    /* 2. 设置文件名和内容类型 */
    header("content-disposition:attachment;filename={$file}"); 
    
    /* 3. 设置文件大小 */
    header("content-length:{$size}"); 
    
    /* 4. 下载文件 */
    readfile($filepath);
    
?>
```

#### 多文件上传

```php+HTML
<!doctype html>
<html lang='en'>
	<head>
    	<meta charset="UTF-8">
        <title>文件上传</title>
    </head>
    <body>
        <h3>
            文件上传
        </h3>
        <hr>
        <form action="up.php" method="post" enctype="multipart/form-data">
            <p>
                上传图片
            </p>
            <p>
                <input type="file" name="img1">
            </p>
            <p>
                <input type="file" name="img2">
            </p>
            <p>
                <input type="file" name="img3">
            </p>
            <p>
                <input type="submit" value="上传">
            </p>
        </form>
    </body>
</html>
<!-- up.php -->
<?php
	echo '<pre>';
	print_r($_FILES);
	echo '</pre>';
	foreach($_FiLES as $file){
        $name = $file['name'];
        $ext = array_pop(explode('.',$name));
        $size = $file['size'];
        $tmp_name = $file['tmp_name'];
        $tfile = time().mt_rand().'.'.$ext;
        $target = 'uploads/'.$tfile;
        if(in_array($ext,$allow)){
            if(move_uploaded_file($tmp_name,$target)){
                echo "文件{$name}上传成功！";
            }
        }else{
            echo '只允许上传jpg|png图片文件！';
        }
    }  
?>
```

