# PHP学习笔记-第二章

### PHP变量的使用

PHP标签

```php
<?php
    //PHP代码
?>  
```

PHP脚本中允许混编

```php+HTML
<hr>
<?php
	echo "111";
?>
<hr>
```

### 变量的定义

```php
<?php
    $X = 10;
?> 
```

 ### 变量的输出

```PHP
<?php
    $X = 10;
	echo $X;
?> 
```

### 变量的命名

```PHP
<?php
    $NAME = 10;
	$name = 20
	echo $NAME;
	// 打印出来是10，变量的名称区分大小写。
?> 
```

### 变量作用

```PHP
<?php
    $name = "bei"
	echo '我是{$name}';
	// 可变的值
?>
```

### 变量用法

1. 普通变量

   ```PHP
   <?php
       $name = 'bei';
   ?> 
   ```

2. 可变变量

   ```PHP
   <?php
   	$name = "hello";
   	$hello = 'world';
   	echo $$name;
   	// 打印结果 world
   ?>
   ```

3. 引用变量

   ```PHP
   <?php
   	$a = 10;
   	$b = $a;
   	echo $b;
   	// 打印结果 10
   	$a = 10;
   	$b = &$a;
   	$a = 30
   	echo $b;
   	// 打印结果 30
   ?>
   ```

### 变量类型

1. 整型

   ```PHP
   <?php
       $a = 100;
   	echo $a;
   	// 打印结果 100 整数类型
   ?> 
   ```

2. 浮点型

   ```PHP
   <?php
       $a = 100.21;
   	echo $a + 20;
   	// 打印结果 120.21 浮点类型
   ?> 
   ```

3. 字符串

   ```PHP
   <?php
       $a = "PHP是世界上最好的语言。";
   	echo $a + "真的吗？";
   	// 打印结果 PHP是世界上最好的语言。真的吗？
   ?> 
   ```

4. 布尔型

   ```PHP
   <?php
       $a = true;
   	if($a){
           echo "是true";
       }else{
           echo "是false"
       }
   	// 打印结果 true
   ?> 
   ```

5. 数组

   ```PHP
   <?php
       $a = array(1,3,5,7,9);
   	print_r($a);
   	// 打印结果 Array ( [0] => 1 [1] => 3 [2] => 5 [3] => 7 [4] => 9 )
   	echo $a[2];
   	// 打印结果 5
   	// 数组需要用print_r()才能全部打印出来。
   	echo "<pre>";
   	print_r($a);
   	echo "</pre>";
   	// <per>按照原格式打印数组（就是显示网页原代码）
   ?> 
   ```

6. 对象

   ```PHP
   
   ```

7. 资源

8. NUll

   ```PHP
   <?php
       $a = null;
   	$b = $a + 10;
   	echo $b;
   	// 打印结果 10
   	// null 通常用来变量定义占位的，强力性语言变量必须要先定义才能使用，php则不需要。
   ?> 
   ```

   