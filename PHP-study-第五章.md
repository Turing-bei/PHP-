## PHP学习笔记—第五章

### 数组函数—第一节

1. 数组作用

   ```PHP
   <?php
       $arr = array(1,'2',3.5,null);
   	/* 
   	数组的作用
   	一个数组变量可以存很多值。
   	可以是8种变量类型中的任意一种。
   	*/
   ?>
   ```

2. 数组定义

   ```PHP
   <?php
       // 第一种数组定义方法
       $arr = array(1,2,3);
   	
   	// 第二种数组定义方法
   	$brr = [1,2,3];	
   ?>
   ```

3. 数组输出

   ```php
   <?php
       $arr = array(1,2,3,4,5);
   	echo '<pre>';
   	print_r($arr);
   	echo '</pre>';
   	/* 打印结果：
   		Array
           (
               [0] => 1
               [1] => 2
               [2] => 3
               [3] => 4
               [4] => 5
           )
   	*/
   ?>
   ```

4. 数组组成

   ```PHP
   <?php
       $arr = array(1,2,3);
   	echo $arr[0];
   	// 打印结果：1
   	/*
   	数组是由元素组成的
   	元素是由：
   	1.下标 值
   	2.key value
   	3.键 值
   	*/
   ?>
   ```

5. 数组类型

   ```PHP
   <?php
   // 索引数组
   $arr = array(1,2,3);
   
   // 关联数组
   $brr = array(
       'item1'=>'linux',
       'item2'=>'php',
       'item3'=>'java'
   );
   
   // 混合数组
   $crr = array(
      	'linux',
       'item2'=>'php',
       'item3'=>'java'
   );
   ?> 
   ```

6. 数组赋值

   ```PHP
   <?php
       // 简单赋值
       $arr = array(1,2,3);
   	$arr[0] = 2;
   	echo '<pre>';
   	print_r($arr);
   	echo '</pre>';
   	/* 打印结果：
           Array
           (
               [0] => 2
               [1] => 2
               [2] => 3
           )
   	*/
       
       // 复杂赋值
   	$brr = array(
           'linux',
           'item2'=>'php',
           'item3'=>'java'
       );
   	$brr[] = 'html5';
   	$brr[100] = 'js';
   	$brr[] = 'web'; 
   	// web的下标是前面所以key中最大数字加1
   	echo '<pre>';
   	print_r($brr);
   	echo '</pre>';
   	/* 打印结果：
   		Array
           (
               [0] => linux
               [item2] => php
               [item3] => java
               [1] => html5
               [100] => js
               [101] => web
           )
   	*/
   	
   	// 赋值方法
   	for($i=0;$i<5;$i++){
           $crr[]=$i;
       }
   	echo '<pre>';
   	print_r($crr);
   	echo '</pre>';
   	/* 打印结果：
   		Array
           (
               [0] => 0
               [1] => 1
               [2] => 2
               [3] => 3
               [4] => 4
           )
   	*/
   ?>
   ```

7. 数组遍历

   ```PHP
   <?php
       // for遍历 索引数组遍历
       $arr = array('linux','java','php','js');
   	for($i=0;$i<4;$i++){
           echo $i.'-'.$arr[$i].'<br>';
       }
   	/* 打印结果：
           0-linux
           1-java
           2-php
           3-js
       */
   	
   	// while..list..each遍历数组
   	// list的作用 a，b是和数组下标相对于的
   	list($a,$b)=array('linux','php');
   	echo $a;
   	echo '<br>';
   	echo $b;
   	/* 打印结果：
   		linux
   		php
   	*/
   
   	//each的作用 each可以持续遍历数组
   	$brr = array(1,2,3);
   	$brr1 = each($brr);
   	print_r($brr1);
   	/* 打印结果：
   	Array ( [1] => 1 [value] => 1 [0] => 0 [key] => 0 )
   	*/
   	$brr2 = each($brr);
   	print_r($brr2);
   	/* 打印结果：
   	Array ( [1] => 2 [value] => 2 [0] => 1 [key] => 1 )
   	*/
   
   	// while..list..each的使用
   	$crr = array(
           'item1'=>'linux',
           'item2'=>'java',
           'item3'=>'php',
           'item4'=>'js'
       );
   	while(list($key,$val)=each($crr)){
           echo "<p>{$key}--{$val}</p>";
       }
   	/* 打印结果：
   		item1--linux
           item2--java
           item3--php
           item4--js
   	*/
   
   	// foreach遍历
   	$drr = array(
           'item1'=>'linux',
           'item2'=>'java',
           'item3'=>'php',
           'item4'=>'js'
       );
   	foreach($drr as $key=>$val){
           echo "<p>{$key}--{$val}</p>";
       }
   	/* 打印结果：
   		item1--linux
           item2--java
           item3--php
           item4--js
   	*/
   ?>
   ```

8. 超全局数组

   1. $_SERVER

      ```PHP
      <?php
          echo '<pre>';
      	print_r($_SERVER);
      	echo '</pre>';
      	
      	print_r($_SERVER[SERVER_NAME]);
      	// 1.域名
      	
      	print_r($_SERVER[SERVER_ADDR]);
      	// 2.服务器ip地址
      	
      	print_r($_SERVER[SERVER_PORT]);
      	// 3.服务器端口
      	
      	print_r($_SERVER[REMOTE_ADDR]);
      	// 4.客户端ip
      	
      	print_r($_SERVER[DOCUMENT_ROOT]);
      	// 5.网站根目录
      	
      	print_r($_SERVER[REQUEST_SCHEME]);
      	// 6.请求的协议
      
      	print_r($_SERVER[SCRIPT_FILENAME]);
      	// 7.当前脚本的系统绝对路径
      	
      	print_r($_SERVER[QUERY_STRING]);
      	// 8.给当前脚本传递的参数
      	
      	print_r($_SERVER[REQUEST_URI]);
      	// 9.网站绝对地址加参数
      	
      	print_r($_SERVER[SCRIPT_NAME]);
      	// 10.网站绝对地址
      	
      	print_r($_SERVER[PHP_SELF]);
      	// 11.网站绝对地址
      ?>
      ```

   2. $_GET

      ```php+HTML
      <!-- 获取form表单GET传递数据 -->
      <form action="reg.php">
          <p>用户名:</p>
          <P>
              <input type='text' name='username'>
          </P>
          <p>密码:</p>
          <P>
              <input type='text' name='password'>
          </P>
          <p>
              <input type='submit' value='ok'>
          </p>
      </form>
      <?php
      	// 本php文件被命名为reg.php
          echo '<pre>';
      	print_r($_GET);
      	echo '</pre>';
      	// 获取给当前脚本所传递的地址栏的参数
      ?>
      ```

   3. $_POST

      ```php+HTML
      <!-- 获取form表单POST传递数据 -->
      <form action="reg.php" method='post'>
          <p>用户名:</p>
          <P>
              <input type='text' name='username'>
          </P>
          <p>密码:</p>
          <P>
              <input type='text' name='password'>
          </P>
          <p>
              <input type='submit' value='ok'>
          </p>
      </form>
      <?php
      	// 本php文件被命名为reg.php
          echo '<pre>';
      	print_r($_POST);
      	echo '</pre>';
      	// 获取表单给当前脚本所传递的POST数据
      ?>
      ```

   4. $_REQUEST

      ```php+HTML
      <!-- 获取form表单传递数据 -->
      <form action="reg.php" method='post'>
          <p>用户名:</p>
          <P>
              <input type='text' name='username'>
          </P>
          <p>密码:</p>
          <P>
              <input type='text' name='password'>
          </P>
          <p>
              <input type='submit' value='ok'>
          </p>
      </form>
      <form action="reg.php" method='get'>
          <p>用户名:</p>
          <P>
              <input type='text' name='username'>
          </P>
          <p>密码:</p>
          <P>
              <input type='text' name='password'>
          </P>
          <p>
              <input type='submit' value='ok'>
          </p>
      </form>
      <?php
      	// 本php文件被命名为reg.php
          echo '<pre>';
      	print_r($_REQUEST);
      	echo '</pre>';
      	// 获取表单给当前脚本所传递的GET或POST数据
      	// 不建议使用，是什么数据传值用什么速度更快。
      ?>
      ```

   5. $GLOBALS

      ```PHP
      <?php
          // 包含所以其他超全局数组
          // 不建议使用
      ?>
      ```

   6. $_COOKIE

   7. $_SESSION

   8. $_FILES

   超全局作用：

   1. 预定义
      1. php中提前已经定义好了。

   2. 超全局
      	1. 函数外面可以用。
       	2. 函数里面也可以用。

   超全局数组的使用：

   ```php+HTML
   <!-- 超链接 -->
   <a href='list.php?id=10&name=bei&age=20'>
       列表页面
   </a>
   <?php
   	// 本页面是list.php
   	echo '<pre>';
   	print_r($_GET);
   	echo '</pre>';
   	/* 打印结果：Array
       (
           [id] => 10
           [name] => bei
           [age] => 20
       )
       超链接GET传值
       */
   ?>
   <!-- 表单 -->
   <form action="reg.php" method='post'>
       <p>用户名:</p>
       <P>
           <input type='text' name='username'>
       </P>
       <p>密码:</p>
       <P>
           <input type='text' name='password'>
       </P>
       <p>
           <input type='submit' value='ok'>
       </p>
   </form>
   <?php
   	// 本页面是reg.php
   	echo '<pre>';
   	print_r($_POST);
   	echo '</pre>';
   	/* 打印结果：Array
       (
           [username] => bei
           [password] => 123
       )
      表单GET传值可GET也可POST，POST传值不会在地址栏出现，
      建议POST。
       */
   ?>
   <!-- 表单POST传输数据 -->
   <!-- 1.文本框 -->
   <form action="reg.php" method='post'>
       <P>
           <input type='text' name='username'>
       </P>
       <p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 2.密码框 -->
   <form action="reg.php" method='post'>
       <P>
           <input type='password' name='password'>
       </P>
       <p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 3.单选框 -->
   <form action="reg.php" method='post'>
       <label>
           <input type='radio' name='love' value='php'>php
       </label>
       <label>
           <input type='radio' name='love' value='js'>js
       </label>
       <p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 4.多选框 -->
   <form action="reg.php" method='post'>
       <label>
           <input type='checkbox' name='love[]' value='php'>php
       </label>
       <label>
           <input type='checkbox' name='love[]' value='js'>js
       </label>
       <label>
           <input type='checkbox' name='love[]'value='html5'>html5
       </label>
       <p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 5.下拉菜单 -->
   <form action="reg.php" method='post'>
       <p>
           <select name='love'>
               <option value='php'>php</option>
               <option value='js'>js</option>
               <option value='html5'>html5</option>
           </select>
       </p>
      	<p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 6.多选下拉菜单 -->
   <form action="reg.php" method='post'>
       <p>
           <select name='love[]' multiple>
               <option value='php'>php</option>
               <option value='js'>js</option>
               <option value='html5'>html5</option>
           </select>
       </p>
      	<p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 7.文本域 -->
   <form action="reg.php" method='post'>
       <p>
          <textarea name='mess'></textarea>
       </p>
      	<p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 8.隐藏框 -->
   <form action="reg.php" method='post'>
       <p>
          <input type='hidden' name='id' value='100'>
       </p>
      	<p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   <!-- 8.文件  php文件接收需要用$_FILES-->
   <form action="reg.php" method='post' enctype='multipart/form-data'>
       <p>
          <input type='file' name='img'>
       </p>
      	<p>
           <input type='submit' value='提交'>
           <input type='reset' value='取消'>
       </p>
   </form>
   ```
   

