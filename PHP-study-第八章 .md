## PHP学习笔记—第八章

### 字符串函数—第二节

#### 正则表达式

#### 正则表达式的作用

```PHP
<?php
    /* 1.检测手机号 */
    	$tel = "18012345678";
        $ptn = "/^(180\d{8})|(186\d{8})$/";
        $num = preg_match($ptn,$tel);
        if($num){
            echo '手机格式正确！';
        }else{
            echo '手机格式有误！';
        }
		/* 打印结果：手机格式正确！*/

    /* 2.检测邮箱 */
		$tel = '577390480@qq.com';
		$ptn = '/^\w+@\w+\.\w+$/';
		$num = preg_match($ptn,$tel);
		if($num){
            echo '邮箱格式正确！';
        }else{
            echo '邮箱格式有误！';
        }
		/* 打印结果：邮箱格式正确！*/
    
    /* 3.检测域名 */
		$tel = 'www.baidu.com';
		$ptn = '/^\w+\.\w+\.\w+$/';
		$num = preg_match($ptn,$tel);
		if($num){
            echo 'url格式正确！';
        }else{
            echo 'url格式有误！';
        }
		/* 打印结果：url格式正确！*/
    
    /* 4.高难度的替换 */
		$str = "2017-03-17";
		$ptn = "/(\d+)-(\d+)-(\d+)/";
		$rep = "$2/$3/$1";
		$str2 = preg_replace($ptn,$rep,$str);
		echo $str2;
		/* 打印结果：03/17/2017 */ 
?>
```

#### 原子

```PHP
<?php
    /* 1.任意一个字符 .是匹配任意一个字符*/
    	$str = "bei";
		$ptn = '/./';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
    	/* 打印结果：
    		Array
            (
                [0] => Array
                    (
                        [0] => b
                        [1] => e
                        [2] => i
                    )
            )
        */

    /* 2.字母，数字 []匹配一组或单个*/
		$str = "bei123";
		$ptn = '/[a-z][0-9]/';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => Array
                    (
                        [0] => b
                        [1] => e
                        [2] => i
                        [3] => 1
                        [4] => 2
                        [5] => 3
                    )
            )
        */
	
	/* 3.特殊字符 */
		$str = '/\d/'; // 匹配任意一个数字
		$str = '/\D/'; // 匹配任意一个非数字
		$str = '/\s/'; // 匹配空格
       	$str = '/\S/'; // 匹配非空格
        $str = '/\w/'; // 匹配任意一个字母，数字或下划线符号   
		$str = '/\W/'; // 匹配任意一个非字母，数字或下划线符号

	/* 4.向后引用 具体参考单元匹配 */
		$0-$n
            
	/* 5.转义符  \可以把特殊字符转义成普通字符 */
		$str = '/\./'    
?>
```

#### 元字符

```PHP
<?php
	/* 1. * 任意多个前面的原子  */
    	$str = "bei123";
    	$ptn = '/.*/';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => Array
                    (
                        [0] => bei123
                        [1] => 
                    )
            )
        */

    /* 2. + 一个或多个前面的原子 */
		$str = "bei123";
    	$ptn = '/.+/';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => Array
                    (
                        [0] => bei123
                    )
            )
        */
	
    /* 3. ? 一个或零个前面的原子 */
        $str = "bei123";
        $ptn = '/.?/';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
             Array
            (
                [0] => Array
                    (
                        [0] => b
                        [1] => e
                        [2] => i
                        [3] => 1
                        [4] => 2
                        [5] => 3
                        [6] => 
                    )
            )       
        */

    /* 4. | 或者的意思 */
		$str = "bei123";
        $ptn = '/bei|123/';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
           Array
            (
                [0] => Array
                    (
                        [0] => bei
                        [1] => 123
                    )
            )
        */

    /* 5. ^ 代表开头的原子 */
		$str = "bei1 bei2 bei3";
        $ptn = '/^bei./';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
           Array
            (
                [0] => Array
                    (
                        [0] => bei1
                    )
            )
        */

    /* 6. $ 代表结尾的原子 */
		$str = "bei1 bei2 bei3";
        $ptn = '/bei.$/';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
           Array
            (
                [0] => Array
                    (
                        [0] => bei3
                    )
            )	
        */

    /* 7. \b 单纯边界 */
		$str = "linux and php ispsplinux";
        $ptn = '/\bp.p\b/';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
           Array
            (
                [0] => Array
                    (
                        [0] => php
                    )
            )	
        */

    /* 8. \B 非单纯边界 */
		$str = "linux and php ispsplinux";
        $ptn = '/\Bp.p\B/';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
           Array
            (
                [0] => Array
                    (
                        [0] => psp
                    )
            )
        */

    /* 9. [^] 取非就是取反的意思 */
		$str = "123456ab";
        $ptn = '/[^1-5]/';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
           Array
            (
                [0] => Array
                    (
                        [0] => 6
                        [1] => a
                        [2] => b
                    )
            )
        */

    /* 10. {} 匹配多少个前面的原子 */
		$str = "123456789";
        $ptn = '/\d{4}/';
        preg_match_all($ptn,$str,$arr);
        echo '<pre>';
        print_r($arr);
        echo '</pre>';
        /* 打印结果：
           Array
            (
                [0] => Array
                    (
                        [0] => 1234
                        [1] => 5678
                    )
            )
        */

    /* 11. () 单元匹配 */
		$str = '2019-8-5';
		$ptn = '/^(\d+)-(\d+)-(\d+)$/';
		$rep = '$2/$3/$1';
		echo preg_replace($ptn,$rep,$str);
		/* 打印结果：8/5/2019 */
?>
```

#### 模式修正符

```PHP
<?php
    /* 1. i  忽略大小写 */
    	$str = 'lincx and php and LINBX';
		$ptn = '/lin.x/i';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => Array
                    (
                        [0] => lincx
                        [1] => LINBX
                    )
            )
        */
    
    /* 2. m  视为多行 */
		$str = "lincx and \n and LINBX";
		$ptn = '/lin.x/im';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => Array
                    (
                        [0] => lincx
                        [1] => LINBX
                    )
            )
        */
    
    /* 3. s  视为单行 */
		$str = "a\nbc";
		$ptn = '/./s';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => Array
                    (
                        [0] => a
                        [1] => 

                        [2] => b
                        [3] => c
                    )
            )
        */
    
    /* 4. U  贪婪模式 */
		$str = 'bei';
		$ptn = '/.*/U';
		preg_match_all($ptn,$str,$arr);
		echo '<pre>';
		print_r($arr);
		echo '</pre>';
		/* 打印结果：
			Array
            (
                [0] => Array
                    (
                        [0] => 
                        [1] => b
                        [2] => 
                        [3] => e
                        [4] => 
                        [5] => i
                        [6] => 
                    )
            )
        */
    
    /* 5. e  向后引用(函数加工) */
		$str = 'php-javascript-html5';
		$ptn = '/(\w+)-(\w+)-(\w+)/e';
		$rep = '$1."-".strtoupper($2)."-".$3';
		echo preg_replace($ptn,$rep,$str);
		/* 打印结果：php-JAVASCIPT-html5 */
?>
```

#### 正则函数

```PHP
<?php
    /* 1.字符串的匹配与查找 */
    	/* 1.1 preg_match() 匹配一次 */
            $str = 'Turing bei';
            $ptn = '/bei/';
            preg_match($ptn,$str,$arr);
            echo '<pre>';
            print_r($arr);
            echo '</pre>';
            /* 打印结果： 
                Array
                (
                    [0] => bei
                )
            */
		
		/* 1.2 preg_match_all() 逐行匹配 */
            $str = 'Turing bei bei';
            $ptn = '/bei/';
            preg_match_all($ptn,$str,$arr);
            echo '<pre>';
            print_r($arr);
            echo '</pre>';
            /* 打印结果： 
               Array
                (
                    [0] => Array
                        (
                            [0] => bei
                            [1] => bei
                        )
                )
            */

		
		/* 1.3 preg_grep() 数组匹配 */
            $arr = array(
                'title1'=>'php is very much!',
                'title2'=>'javascript and php',
                'title3'=>'javascript and html5'
            );
            $ptn = '/php/';
            $arr2 = preg_grep($ptn,$arr);
            echo '<pre>';
            print_r($arr2);
            echo '</pre>';
            /* 打印结果： 
               Array
                (
                    [title1] => php is very much!
                    [title2] => javascript and php
                )
            */

    /* 2.字符串的替换 */
    	/* 1.1 preg_replace() 字符串替换 */
			$str = 'javascript and php';
			$ptn = '/php/';
			$rep = 'python';
			echo preg_replace($ptn,$rep,$str);
			/* 打印结果：javascript and python */

    /* 3.字符串的分割与连接 */
    	/* 1.1 preg_split() 字符串替换 */
			$str = 'javascript-and+php.and,python';
			$ptn = '/-|\+|,|\./';
			$arr = preg_split($ptn,$str);
			echo '<pre>';
			print_r($arr);
			echo '</pre>';
			/* 打印结果：
				Array
                (
                    [0] => javascript
                    [1] => and
                    [2] => php
                    [3] => and
                    [4] => python
                )
            */
 ?>
```

#### 货币格式化

```PHP
<?php
    $str = '12345678';
	function format($str){
        $arr = str_split($str,3);
        $str2 = join(',',$arr);
        echo $str2;
    }
	format($str);
	/* 打印结果： 123,456,78 */
?>
```