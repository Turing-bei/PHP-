## PHP学习笔记—第七章

### PHP字符串函数—第一节

#### 字符串的输出

```PHP
<?php
    /* 1.echo 可以输出字符串*/
    	$str = 'Turingbei';
		echo $str;
		/* 打印结果：Turingbei */
    
    /* 2.var_dump() 输出值 长度 类型*/
		$str = 'Turingbei';
		var_dump($str);
		/* 打印结果：string(9) "Turingbei" */
    
    /* 3.print 可以输出字符串*/
		$str = 'Turingbei';
		print $str;
		/* 打印结果：Turingbei */
    
    /* 4.print_r() 可以输出字符串*/
		$str = 'Turingbei';
		print_r($str);
    	/* 打印结果：Turingbei */

    /* 5.printf() 字符串格式化输出*/
		/* 
			%s 转字符串
			%d 转数字
			%f 转小数
		*/	
		$a = 'php';
		$b = 'js';
		$c = 'html5';
		printf('--%s--%s--%s--',$a,$b,$c);
		/* 打印结果： --php--js--html5-- */
           
    /* 6.sprintf() 返回字符串格式化的函数，并不输出*/
		/* 
			%s 转字符串
			%d 转数字
			%f 转小数
		*/	
		$a = 'php';
		$b = 'js';
		$c = 'html5';
		$d = sprintf('--%s--%s--%s--',$a,$b,$c);
		echo $d;
		/* 打印结果： --php--js--html5-- */
    
    /* 7.die() 可以输出字符串后文不在执行*/
		$str = 'Turingbei';
		die($str);
		echo 'go go go';
    	/* 打印结果：Turingbei */
    
    /* 8.exit() 可以输出字符串后文不在执行*/
		$str = 'Turingbei';
		exit($str);
		echo 'go go go';
		/* 打印结果：Turingbei */
?>
```

#### 去除空格和字符串填补函数

```PHP
<?php
    /* 1. ltrim() 去除字符串左侧空格*/
    	$str = ' php ';
		echo strlen(ltrim($str));
		/* 打印结果：4 */
		
    /* 2. rtrim() 去除字符串右侧空格*/
		$str = ' php ';
		echo strlen(rtrim($str));
		/* 打印结果：4 */
    
    /* 3. trim() 去除任意左右字符，默认是空格*/
    	$str = ' php ';
		/* trim($str,'-'); */
		echo strlen(trim($str));
		/* 打印结果：3 */

    /* 4. str_pad() 把字符串补充到一定长度*/
		$str = 'php';
		/* str_pad($str,2,'-',STR_PAD_RIGHT) 右侧*/
		/* str_pad($str,2,'-',STR_PAD_LEET) 左侧*/
		echo str_pad($str,2,'-',STR_PAD_BOTH);
		/* 打印结果：-php- */
    
    /* 5. str_repeat() 字符串重复出现多少次*/
		$str = 'abc';
		echo str_repeat($str,2);
		/* 打印结果：abcabc */

	/* 6. strlen() 字符串长度*/ 
		$str = ' php ';
		echo strlen($str);
		/* 打印结果：5 */
    
?>
```

#### 字符串大小写转换函数

```PHP
<?php
    /* 1. strtolower() 字符串转小写 */ 
        $str = 'TURINGBEI';
        echo strtolower($str);
		/* 打印结果：turingbei */

	/* 2. strtoupper() 字符串转大写*/ 
		$str = 'turingbei';
		echo strtoupper($str);
		/* 打印结果：TURINGBEI */

	/* 3. ucfirst() 字符串首字符转大写*/
		$str = 'turingbei';
		echo ucfirst($str);
		/* 打印结果：Turingbei */

	/* 4. ucwords() 字符串每个单词的首字母转大写*/ 
		$str = 'turing bei';
		echo ucwords($str);
		/* 打印结果：Turing Bei */
?>
```

#### 与HTML标签相关联的字符串函数

```PHP
<?php
    /* 1. nl2br() 	\n转成<br/>标签*/ 
    	$str = "php\n is \nvery \nmuch!";
    	echo nl2br($str);
		/* 打印结果：
			php
            is 
            very 
            much!
		*/
    
    /* 2. addslashes() 单双引号前自动加反斜线*/ 
    	$str = "'worde',delete 'from mess' ";
    	echo addslashes($str);
		/* 打印结果：\'worde\',delete \'from mess\' */

    /* 3. stripslashes() 去除反斜线*/ 
		$str = "php\n is \nvery \nmuch!";
		echo stripslashes($str);
		/* 打印结果：php is very much! */
    
    /* 4. strip_tags() 去除html标签*/ 
		$str = "<h1 style='color: red;'>Turing bei</h1>";
    	echo strip_tags($str);
		/* 打印结果：Turing bei */
    
    /* 5. htmlspecialchars() 把HTML标签转换成实体显示出来。*/ 
		$str = "<h1 style='color: red;'>Turing bei</h1>'worde',> 'from";
		echo htmlspecialchars($str);
		/* 打印结果：<h1 style='color: red;'>Turing bei</h1>'worde',> 'from */
	
	/* 6.htmlspecialchars_decode() 把实体解析成HTML标签 */
		$str = "<h1 style='color: red;'>Turing bei</h1>'worde',> 'from";
		echo htmlspecialchars_decode($str);
		/* 打印结果： 
            Turing bei 
            'worde',> 'from 
		*/
?>
```

#### 其他字符串格式化函数

```PHP
<?php
    /* 1. strrev() 字符串反转*/ 
    	$str = 'Turing bei';
		echo strrev($str);
		/* 打印结果：ieb gniruT */
    		
    /* 2. strlen() 字符长度*/ 
    	$str = 'Turingbei';
		echo strlen($str);
		/* 打印结果：9 */

    /* 3. number_format() 货币格式化*/ 
		$str = 1800000;
		echo number_format($str);
		/* 打印结果：1,800,000 */
    
    /* 4. md5() md5单向不可逆加密*/ 
    	$str = 123;
		echo md5($str);
		/* 打印结果：202cb962ac59075b964b07152d234b70*/

    /* 5. str_shuffle() 打乱字符串*/ 
		$str = 12345678;
		echo str_shuffle($str);
		/* 打印结果: 67813245*/
?>
```

#### 字符串的分割与拼接

```PHP
<?php
    /* 1. explode() 字符串分割*/
    	$str = '2050-07-27';
		$arr = explode('-',$str);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => 2050
                [1] => 07
                [2] => 27
            )
		*/

    /* 2. implode() 字符串合并*/
		$arr = array('2219','07','27');
		$str = implode('-',$arr);
		echo $str;
		/* 打印结果：2219-07-27 */

    /* 3. join() 字符串合并*/
		$arr = array('2219','07','27');
		$str = join('-',$arr);
		echo $str;
		/* 打印结果：2219-07-27 */
?>
```

#### 字符串的截取

```PHP
<?php
    /* 1. substr() 字符串截取*/
    	$str = '123456';
		echo substr($str,0,3);
		/* 打印结果：123 */
?>
```

#### 字符串的查找

```PHP
<?php
    /* 1. strpos() 查询一个字符在字符串第一出现的位置*/
    	$str = '/web/home/index.php';
    	echo strpos($str,'/');
		/* 打印结果：0 */
    
    /* 2. strrpos() 查询一个字符在一个字符串最后出的位置*/
		$str = '/web/home/index.php';
    	echo strrpos($str,'/');
		/* 打印结果：9 */
?>
```

#### 字符串的替换

```PHP
<?php
    /* 1. str_replace() 字符串替换*/
    	$str = '/web/home/index.php';
		echo str_replace('home','admin',$str);
		/* 打印结果：/web/admin/index.php */
?>
```

#### 支持多字节文字

```PHP
<?php
    /* 1. mb_substr() 可以支持中文的正常截取 */
        $str = '我爱自由，我爱自己。';
        echo mb_substr($str,0,2).'...';
        /* 打印结果：我爱... */
?>
```

#### 其他常用的字符串函数

```PHP
<?php
    /* 1. pathinfo() 解析地址字符串*/
    	$str = '/web/home/index.php';
		$arr = pathinfo($str);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [dirname] => /web/home
                [basename] => index.php
                [extension] => php
                [filename] => index
            )		
		*/
    
    /* 2. basename() 获取路径文件名部分*/
		$str = '/web/home/index.php';
		$arr = basename($str);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：index.php */

    /* 3. dirname() 获取路径目录部分*/
		$str = '/web/home/index.php';
		$arr = dirname($str);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：/web/home */

    /* 4. parse_url() 解析url地址 */
		$str = 'https://www.baidu.com?id=10&name=bei';
		$arr = parse_url($str);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [scheme] => https
                [host] => www.baidu.com
                [query] => id=10&name=bei
            )
        */

    /* 5. parse_str() 解析地址栏的参数*/
		$str = 'https://www.baidu.com?id=10&name=bei';
		$arr = parse_url($str);
		$query = $arr['query'];
		parse_str($query,$arr2);
		echo '<pre>';
		print_r($arr2);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [id] => 10
                [name] => bei
            )
        */
?>
```

