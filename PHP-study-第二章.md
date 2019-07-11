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
   <?php
   	class Person {
      		// 特征
       	public $name = "bei";
      	 	public $age = "21";
       	public $sex = "男";
       	// 行为
       	public function say(){
           	echo "变成一个很厉害的人。<br>";
       	}
       	public function eat(){
           	echo "成为一个终身学习者。<br>";
       	}
   	}
   	$user1 = new Person();
   	echo $user1->name;
   	echo "<br>";
   	echo $user1->sex;
   	echo "<br>";
   	$user1->say();
   	$user1->eat();
   	// 类与对象。
   	//属性（特征），方法（行为）。
   ?>
   ```

7. 资源

   ```PHP
   <?php
       // 连接数据库
       $conn=mysql_connect('localhost','root','12345678');
   
       // 查看类型方法
       var_dump($conn);
   
       // 设置字符集
       mysql_query('set names utf8',$conn);
   
       // 选择aiwanyou数据库
       mysql_select_db('aiwanyou',$conn);
   
       // 准备查询语句
       $sql="select * from user";
   
       // 把语句发送到mysql服务器
       $rst=mysql_query($sql,$conn);
       
       //从mysql服务器返回的结果集中读取出每一行数据
       while($row=mysql_fetch_assoc($rst)){
           // 打印数组
           echo '<pre>';
           print_r($row);
           echo '</pre>';
       }
       // 数据库连接资源
   ?>
   ```

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


### PHP中8种变量类型

#### 1.标准类型

1. 整数型

2. 浮点型

3. 字符串

4. 布尔型

#### 2.复合类型

5. 数组

6. 对象

#### 3.特色类型

7. 资源

8. NULL

### 字符串连接符

```PHP
<?php
    $a = 'my name is';
    $b = 'bei';
    echo $a.$b;
    // 字符串连接符是 . 
?>
```

### 单双引号的区别

```PHP
<?php
    $b = 'bei';
    $a = 10;
    $c = 5;
    echo "my name is {$b}。";
    // 双引号中可以解析变量，变量前后加{}。
    echo 'my name is'.$b.'。';
    // 单引号中不能解析变量
    echo "$a+$c";
    // 打印结果：10+5 双引号中可以解析变量，但不能执行表达式
    echo "the num is".($a+$b)."!!!";
    // 双引号中如何执行表达式。要执行用.连接。
    echo "my 'nmae' is {$a} !!!";
    // 单双引号交叉包含使用。
    echo "my \"nmae\" is {$a} !!!";
    // 双引号中如何包含双引号。需要加\把特殊性取消掉。
?>
```

### 测试变量类型

1. var_dump();

   ```PHP
   <?php
       $a = 10;
       var_dump($a); 
   	// 打印结果：int(10)
   ?>
   ```

2. gettype();

   ```PHP
   <?php
       $a = '10';
       echo gettype($a); 
   	// 打印结果：string
   ?>
   ```

3. 精确判断某种类型

   ```PHP
   <?php
       // 精确判断是否是布尔型：is_bool();
       $a1 = true;
       $b1 = is_bool($a1);
   	var_dump($b1);
   	// 打印结果：bool(true)
   	
   	// 精确判断是否是字符串：is_string();
   	$a2 = 'bei';
   	$b2 = is_string($a2);
   	var_dump($b2);
   	// 打印结果：bool(true)
   
   	// 精确判断是否是浮点型：is_float();
   	$a3 = 11.11;
   	$b3 = is_float($a3);
   	var_dump($b3);
   	// 打印结果：bool(true)
   
   	// 精确判断是否是数组：is_array();
   	$a4 = array();
   	$b4 = is_array($a4);
   	var_dump($b4);
   	// 打印结果：bool(true)
   	
   	// 精确判断是否是对象：is_object();
   	class Person{};
   	$a5 = new Person();
   	$b5 = is_object($a5);
   	var_dump($b5);
   	// 打印结果：bool(true)
   
   	// 精确判断是否是资源：is_resource();
   	$a6 = mysql_connect('localhost','root','12345678');
   	$b6 = is_resource($a6);
   	var_dump($b6);
   	// 打印结果：bool(true)
   
   	// 精确判断是否是null：is_null();
   	$a7 =null;
   	$b7 = is_null($a7);
   	var_dump($b7);
   	// 打印结果：bool(true)
   	
   	// 精确判断是否是标准类型：is_scalar();
   	$a8 = 10;
   	$b8 = is_scalar($a8);
   	var_dump($b8);
   	// 打印结果：bool(true)
   	
   	// 精确判断是否是函数：is_callable();
   	function y(){}
   	$a9= is_callable('y');
   	var_dump($a9);
   	// 打印结果：bool(true)
   ?>
   ```

### 测试变量是否存在

1. isset();

   ```PHP
   <?php
   	// isset测试变量不存在的情况，有2种
   
   	//变量未定义
   	var_dump(isset($b));
   	// 打印结果：bool(false)
   
   	// 变量的值为null
   	$a = null;
   	var_dump(isset($a));
   	// 打印结果： bool(false)
   ?>
   ```

2. empty();

   ```PHP
   <?php
   	//empty测试变量为空的情况，有8种
   	// 1.变量未定义
   	// 2.$a = null;
   	// 3.$a = 0;
   	// 4.$a = '';
   	// 5.$a = '0';
   	// 6.$a = array();
   	// 7.$a = 0.0;
   	// 8.$a = false;
   	var_dump(empty($a));
   ?>
   ```

### 变量类型自动转换：

1. 自动类型转换

   ```PHP
   <?php
   	// 整型转字符串
   	$a1 = 10;
   	echo 'the num is '.$a1;
   	// 打印结果：the num is 10
   
   	//字符串转整型
   	$a2 = 10;
   	$b2 = '10abc3';
   	echo $a2 + 20;
   	// 打印结果：30
   
   	// 所有类型转布尔类型，为假的情况，其余全为真
   	// 1.变量未定义
   	// 2.$a = null;
   	// 3.$a = 0;
   	// 4.$a = '';
   	// 5.$a = '0';
   	// 6.$a = array();
   	// 7.$a = 0.0;
   	// 8.$a = false;
   ?>
   ```

2. 强制类型转换

   ```PHP
   <?php
       // 字符串强制转换成整型
   	$a1 = '10abc';
   	$b1 = (int)$a1;
   	var_dump($b1);
   	// 打印结果：int(10)
   
   	// 整形强制转换成字符串
   	$a2 = 10;
   	$b2 = (string)$a2;
   	var_dump($b2);
   	// 打印结果：string(2) "10"
   	
   	// 所有类型强制转换成布尔类型
   	$a3 = 10;
   	$b3 = (bool)$a3;
   	var_dump($b3);
   	// 打印结果：bool(true)
   	
   	// 字符串强制转换成浮点型
   	$a4 = '10.55abc';
   	$b4 = (float)$a4;
   	var_dump($b4);
   	// 打印结果：float(10.55)
   ?>
   ```