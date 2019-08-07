## PHP学习笔记—第九章

### PHP数字日期和错误处理

#### 数学函数

```PHP
<?php
    /* 1.max() 获取最大值 */
    	$arr = array(29,20,99,78,66);
		echo max($arr);
		/* 打印结果：99 */
    
    /* 2.min() 获取最小值 */
		$arr = array(29,20,99,78,66);
		echo min($arr);
		/* 打印结果：20 */

    /* 3.mt_rand() 随机数*/
		echo mt_rand(1,10);
    	/* 打印结果：6 */
		/* 时间戳实例 */
		echo time().'_'.mt_rand().'.jpg';

    /* 4.round() 四舍五入 */
    	$num = 10.57;
		echo round($num);
		/* 打印结果：11 */
    
    /* 5.floor() 下一个整数 */
		$num = 10.57;
		echo floor($num);
		/* 打印结果：10 */
    
    /* 6.ceil() 上一个整数 */
		$num = 10.57;
		echo ceil($num);
		/* 打印结果：11 */
?>
```

#### 错误处理

```PHP
<?php
    /* 1. 错误级别 */
    	/* 1.1 提示错误 不会阻止脚本 */
    		E_NOTICE
    	/* 1.2 警告错误 不会阻止脚本 */
    		E_WARNING
    	/* 1.3 致命错误 会阻止脚本 */
    		E_ERROR
    	/* 1.4 语法错误 不执行脚本 */
    		E_PARSE
    	/* 1.5 所有错误 会阻止脚本 */
    		E_ALL
    	/* 1.6 丢弃错误 不会阻止脚本*/
    		E_DEPRECATED
    
    /* 2. 控制错误 */
    	error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED;
		/* 输出所以错误，但是除了提示，严格和丢弃错误。 */
?>		
```

#### 日期函数

```PHP
<?php
    /* 修改时区：php.ini (在php解析器里面) */
    	date.timezone = PRC;
    
    /* 1. time() 获取时间戳 */
    	echo time();
		/* 打印结果：1565162190 */
    
    /* 2. date() 时间戳转日期 */
		echo date('Y-m-d H:i:s',time());
		/* 打印结果：2019-08-07 15:31:48 */
		/* 
			Y year 年
			m month 01-12月
            d date 0-31日
            h hour 12小时
            H 21小时
            i minute 00-59分
            s second 00-59秒
            w 0-6 周几
            t 本月几天
            A AM上午或PM下午
            a am上午或pm下午	
            L 是否是闰年 闰年的定义：能被4整除 同时如果能被100整除的话，则必须被400整除
         */
    
    /* 3. strtotime() 日期转时间戳 */
		$str = '2019-8-7';
		echo strtotime($str);
		/* 打印结果：1565107200 */
    
    /* 4. microtime() 获取微妙数 */
		/* 1秒 = 1000毫米 = 1000000微妙 */
        $start = microtime(true);
		for($i=0;$i<10000000;$i++){
            // 1000 万行代码
        }
		$end = microtime(true);
		$diff = $end - $start;
		echo "php中执行1000万次循环总计用时：{$diff}";
		/* 打印结果： php中执行1000万次循环总计用时：0.42620897293091 */
?>
```

#### 万年历实例

```php+HTML
<?php
    // 年
    $year =  $_GET['y']?$_GET['y']:date('Y',time());

    // 月
    $month = $_GET['m']?$_GET['m']:date('n',time());

    // 本月总天数
    $days = date('t',strtotime("{$year}-{$month}-1"));

    // 本月1号是周几
    $week = date('w',strtotime("{$year}-{$month}-1"));

    // 真正的第一天
    $first = 1 - $week;

    // 月数大于12月年加1，月变成1月
    if($month>=12){
        // 下一年
        $nextYear = $year + 1;
        $nextMonth = 1;
    }else{
        // 下一月
        $nextYear = $year;
        $nextMonth = $month + 1;
    }

     // 月数小1月年减1，月变成12月
     if($month<=1){
        // 下一年
        $prevYear = $year - 1;
        $prevMonth = 12;
    }else{
        // 下一月
        $prevYear = $year;
        $prevMonth = $month - 1;
    }
   

?>
<!doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>万年历</title>
        <style>
            h1,h2{
                text-align: center;
            }
            a{
                color: #99f;
            }
            table{
                margin: 0 auto;
                border: 2px solid #272822;
                width: 1000px;
            }
            td,th{
                border: 1px solid #272822;
            }
        </style>
    </head>
    <body>
        <h1>万年历-<?php echo $year.'-'.$month; ?></h1>
        <table>
            <tr>
                <th>周日</th>
                <th>周一</th>
                <th>周二</th>
                <th>周三</th>
                <th>周四</th>
                <th>周五</th>
                <th>周六</th>
            </tr>
           <?php
                for($i=$first;$i<=$days;){
                    echo '<tr>';
                    for($j=0;$j<7;$j++){
                        if($i<=$days && $i>=1){
                            echo "<td>{$i}</td>";
                        }else{
                            echo "<td>&nbsp;</td>";
                        }
                        $i++;
                    }
                    echo '</tr>';
                }
           ?>
        </table>
        <h2>
            <a href="index.php?y=<?php echo $prevYear; ?>&m=<?php echo $prevMonth; ?>">上一月</a>
            <a href="index.php?y=<?php echo $nextYear; ?>&m=<?php echo $nextMonth; ?>">下一月</a>
        </h2>
</html>
```