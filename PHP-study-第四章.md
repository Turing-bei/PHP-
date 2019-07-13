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

### PHP的全局变量和局部变量

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

