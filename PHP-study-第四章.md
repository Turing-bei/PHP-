## PHP学习笔记—第四章

### PHP流程控制

1. 分支流程控制

   1. if..else

      ```php
      <?php
      	$user = 'admin';
      	if($user == 'admin'){
              echo 'yes';
          }else{
              echo 'no';
          }
      	// 打印结果：yes
      ?>
      ```

   2. if..elseif..else

      ```PHP
      <?php
      	$score = 70;
      	if($score >= 80){
              echo 'A';
          }elseif($score >= 10){
              echo 'B';
        	}else{
              echo 'C';
      	}
      	// 打印结果：C
      ?>
      ```

   3. switch..case

      ```PHP
      <?php
          $w = 1;
      	switch($w){
              case 1:
                  echo '周一';
                  break;
              case 2:
                  echo '周二';
                  break;
              case 3:
                  echo '周三';
                  break;
              case 4:
                  echo '周四';
                  break;
              case 5:
                  echo '周五';
                  break;
              default:
                  echo '周末';
                  break;   
          }
      	// 打印结果：周一
      ?>
      ```

      

2. 循环流程控制

   1. while

      ```PHP
      <?php
          // while循环
          $i = 0;
      	while($i<3){
              echo "<h1>{$i}</h1>";
              $i++;
          }
      	// 打印结果：0 1 2
      ?>
      ```

   2. for

      ```PHP
      <?php
          // for循环
      	for($i = 0;$i<5;$i++){
              echo "<h1>{$i}</h1>";
          }
      	// 打印结果：0 1 2 3 4
      ?>
      ```

   3. 实例

      ```PHP
      <?php
          // 九九乘法表
          for($i=1;$i<=9;$i++){
              for($j=1;$j<=$i;$j++){
                  echo "{$j}x{$i}=".$j*$i.'&nbsp;&nbsp;&nbsp;';
              }
              echo '<br>';
          }
      
          // 隔行换色
          for($i=0;$i<5;$i++){
              if($i%2==1){
                  echo "<h1 style='background:#888;'>{$i}</h1>";
              }else{
                  echo "<h1>{$i}</h1>";
              }
          }
      ?>
      ```

3. 循环控制

   1. break
   
      ```PHP
      <?php
          for($i=0;$i<5;$i++){
              if($i==2){
                  break;
              }else{
                  echo "<h1>{$i}</h1>";
              }
          }
          // 打印结果：0 1
          // break 可以结束本层循环
      ?>
      ```
   
   2. continue
   
      ```PHP
      <?php
          for($i=0;$i<5;$i++){
              if($i==2){
                  continue;
              }else{
                  echo "<h1>{$i}</h1>";
              }
          }
          // 打印结果：0 1 3 4
          // continue 结束本次循环
      ?>
      ```
   
4. 脚本控制
   
   1. exit
   
      ```PHP
      <?php
          echo "1";
      	echo "2";
      	echo "3";
      	exit;
      	echo "4";
      	// 打印结果：1 2 3
      	// exit 结束脚本执行。
      ?>
      ```
   
   2. die
   
      ```php
      <?php
          echo "1";
      	echo "2";
      	echo "3";
      	die('本次程序结束，感谢使用');
      	echo "4";
      	// 打印结果：1 2 3 本次程序结束，感谢使用
      	// die 结束脚本执行之前打印结果等同于exit。
      ?>
      ```

### 语言结构

```php
<?php
    if();
	for();
	while();
	switch();
	array();
	echo();
	print();
	list();
	isset();
	unset();
	foreach();
	exit();
	die();
	include();
	require();
	empty();
?>
```

### 函数

1. 系统函数

   ```php
   <?php
       mysql_connect();
   ?>
   ```

2. 自定义函数

   ```PHP
   <?php
       function show(){
       	// 代码
   	}
   ?>
   ```

3. 函数的定义和调用

   ```php
   <?php
       // 函数的定义
       function show(){
       	echo "<h1>123</h1>";
   	}
   	
   	// 函数的调用
   	show();
   	show();
   	// 函数是一段代码被重复使用，提高代码的重用性，降低冗余度。
   ?>
   ```

### 判断是否是函数

```PHP
<?php
    $func='each';
	var_dump(function_exists($func));
	// 打印结果：bool(true) 是函数
?>
```

### 全局变量和局部变量

```php
<?php
	// 函数外面的变量是全局变量
	// 函数里面的变量是局部变量
    $a = 10;
	function sum(){
        $a++;
        echo $a.'<br>';
        // 打印结果：1
    }
	sum();
	echo $a;
	// 打印结果：10
?>
```

```php
<?php
    $a = 10;
	function show(){
        global $a;
        // global在函数内部可以直接使用函数外部的全局变量。
        $a++;
    }
	show();
	echo $a;
	// 打印结果：11
?>
```

 ### 静态变量

```PHP
<?php
    function show(){
    	static $a = 0;
  		// static同一个函数被多次调用时可以共享使用
    	$a++;
    	$func = __FUNCTION__;
    	echo "{$a}次调用{$func}函数！<br>";
	}
	show();
	show();
	// 打印结果：1次调用show函数！2次调用show函数！
?>
```

### 函数的返回值

```PHP
<?php
    $a = 10;
	$b = 20;
	function show($a,$b){
        return $a+$b;
    }
	echo show($a,$b);
	// 打印结果：30
?>
```

### 函数的参数

```PHP
<?php
    function show($i,$j){
    	return $i+$j;
	}
	echo show(10,20);
	// 打印结果：30 
	// 参数是函数外面的值进入函数内部的窗口,按值传递

	// 默认参数
	function show1($i,$j=2){
        return $i+$j;
    }
	echo show1(10);
	// $i必选参数，$j可选参数
	// 打印结果：12

	// 引用参数
	$a = 10;
	function show2(&$i){
        $i++;
    }
	show2($a);
	echo $a;
	// 打印结果：11
	
	// 可变个数参数的函数
	function show3(){
        $args = func_get_args();
        foreach($args as $val){
            $str.='-'.$val;
        }
        echo $str;
    }
	show3('a','b','c');
	// 打印结果：-a-b-c
	
?>
```

### 回调函数

```PHP
<?php
    function show($i,$j,$c){
    	return $c($i,$j);
	}
	echo show(10,20,'sum');
	// 打印结果：30
	function sum($a,$b){
        return $a + $b;
    }
	// 参数的值的类型可以是另一个函数的名字
	// 函数的代码是在语法检测的时候就已经被加载到内存的代码段中
?>
```

### 变量函数

```PHP
<?php
    function show(){
    	echo 'hello world'
	}
	$str = 'show';
	$str();
	// 打印结果：hello world
?>
```

### 递归函数

```PHP
<?php
    $a = 3;
	function sum($a){
        $tot+=$a;
        if($a>1){
            $tot+=sum(--$a);
        }
        return $tot;
    }
	echo sum($a);
	// 打印结果：6
	// 递归函数计算数字之和
 ?>
```

### 如何包含外部文件

1. include 'config.php';

2. require 'config.php';

3. include包含文件报错级别为warning，不会终止脚本

4. require包含文件报错级别为error，会终止脚本

5. 实例

   ```PHP
   <?php
       include 'config.php';
   	require 'config.php';
   	// 引入config.php文件，可以使用config.php文件里面的内容。
    ?>
   ```