# PHP学习笔记—第三章

### PHP常量和运算符

1. PHP常量
2. PHP运算符

### 变量

```PHP
// 可变的量
// 变量的值会随着环境而改变
// 同名变量后面会覆盖前面
<?php
    $name =  'beibei';
    $name = 'bei';
    echo $name;
    // 打印结果：bei
?>
```

### 常量

```PHP
// 一常不变的量
// 常量的值不会随着环境而轻易的改变
// 同名常量不会发生覆盖
<?php
    //常量的定义和使用
    define('USER','bei');
    define('AGE','21');
    define('USER','beibei');
    echo USER."=".AGE;
    // 打印结果：bei=21
?>
// 常量定义: define('USER','bei');
// 常量输出: echon USER;
```

### 常量的使用环境

```php
// 1.脚本头部定义的变量后文不允许任何人修改
// 2.数据库连接和配置参数
<?php
    // 用常量写配置文件
    // 主机名
    define('HOST','localhost');
	// 用户名
	define('USER','root');
	// 密码
	define('PASS','12345678');
	// 数据库
	define('DBNAME','aiwanyou');

	mysql_connect(HOST,USER,PASS);
	mysql_query('set names utf8');
	mysql_select_db(DBNAME);
	$sql = 'select * from user';
	$rst = mysql_query($sql);
	
	while($row = nysql_fetch_assoc($rst)){
        echo '<pre>';
        print_r($row);
        echo '</pre>';
	}
	
	// 优化写法用常量写配置文件
	$arr = array(
        'HOST'=>'localhost',
        'USER'=>'root',
        'PASS'=>'12345678',
        'DBNAME'=>'aiwanyou'
	);
	foreach($arr as $key => $val){
        define($key,$val);
    }
	
	// 测试一个常量是否存在: defined();
	if(defined('BEI')){
		echo 'yes';
	}else{
		echo 'no';
	}
	// 打印结果: no
 ?> 
```

### 预定义常量

```PHP
 <?php
     // 圆周率常量
	echo M_PI;
	
	// 系统绝对路径
	echo __FILE__;
	
	// 当前行数
	echo __LINE__;

	// 当前所在函数名称
	function sum(){
		echo '函数名:'.__FUNCTION__;
		// 打印结果: sum
	}
	sum();
 ?>
```

### 运算符

1. 一元运算符

   ```PHP
<?php
		// 一元运算符
		$a = 10;
		$a = $a + 1;
		echo $a;
		// 打印结果: 11
   	
		$b = 10;
		$b++;
		echo $b;
		// 打印结果: 11
   	
		$c = 10;
		$d = $c++;
		echo $d.'<br>'.$c;
		// 执行操作步骤{ 1.$d=$c; 2.$c=$c+1; }
		// 先赋值,后运算
		// 打印结果: $d = 10 $c = 11;
   	
		$e = 10;
		$f = ++$e;
		echo $f.'<br>'.$e;
		// 执行操作步骤{ 1.$e=$e+1;  2.$e=$f; }
		// 先运算,后赋值
		// 打印结果: $e = 11 $f = 11;
   
		// 先赋值，后运算
		// $i++; $i--;
		// 先运算，后赋值
		// $++i; $--i;
?>
   ```

   

2. 二元运算符

   ```PHP
   <?php
       // 1.数学运算符
           // +,-,*,/,%
           $a = 1 + 2;
           echo $a;
           // 加号运算符 打印结果: 3
   
           $b = 2 - 1;
           echo $b;
           // 减号运算符 打印结果: 1
   
           $c = 2 * 1;
           echo $c;
           // 乘号运算符 打印结果: 2
   
           $d = 2 / 2;
           echo $d;
           // 除号运算符 打印结果: 1
   
           $e = 2 % 2;
           echo $e;
           // 余数运算符 打印结果: 0
     
       // 2.比较运算符
       	// >,<,==,>=,<=,!=,===,!==
   		$f = 0;
   		if($f == false){
               echo 'yes';
           }else{
               echo 'no';
           }
   		// 打印结果: yes  等于运算符
   	
   		if($f === false){
               echo 'yes';
           }else{
               echo 'no';
           }
   		// 打印结果: no  全等于运算符
   
       // 3.逻辑运算符
   		// &&，||，！
   		$user = 'admin';
   		$pass = '123';
   		if($user == 'admin' && $pass == '233'){
               echo 'yes';
           }else{
               echo 'no';
           }
   		// 打印结果：no &&与运算符 两边条件都为真，则为真。其余全为假
   		// 前面为真才会执行后面
   		
   		$aa = 3;
   		$bb = 5;
   		if($aa=3 && $bb=4){
               $aa++;
               $bb++;
           }
       	echo $aa.$bb;
   		// 打印结果：$aa=1; $bb=5; 
   		// 第一运算符优先级问题
   		// 第二与运算符前面为真才会执行后面的代码
   		// 第三表达式里面无论什么类型都会自动转换成布尔类型，true，false
   		
   		$user1 = 'admin';
   		$pass1 = '123';
   		if($user1 == 'admin' || $pass1 == '123'){
               echo 'yes';
           }else{
               echo 'no';
           }
   		// 打印结果：yes ||或运算符 两边条件都为假，则为假。其余全为真
   		// 前面为假才会执行后面
   
   		$namebei = false;
   		if(!$namebei){
               echo 'yes';
           }else{
               echo 'no';
           }
   		// 打印结果：yes ！非运算符 真则为假，假则为真
   		
   		
   		
       // 4.赋值运算符
   		// =, .=, +=, *=, /=, %=
   		$g+=2;
   		//$g = $g + 2;
   		echo $g;
      		
   		$str = '<h1>bei';
   		$str .= '</h1>';
   		//$str = $str.'</h1>';
   		echo $str;
   		// 打印结果: bei
   ?>
   ```

3. 三元运算符

   ```PHP
   <?php
       // 三元运算符
    	$a = true;
   	echo $a?'yes':'no';
   	// 打印结果: yes
   
   	$b = 'bei';
   	echo ($b == 'bei')?'yes':'no';
   	// 打印结果: yes
    ?>
   ```

