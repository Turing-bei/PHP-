## PHP学习笔记—第六章

### PHP数组函数—第二章

9. 自定义数组函数

   ```PHP
   <?php
       $arr=array(
       	'item1'='php',
       	'item2'=>'js',
       	'item3'=>'html5'
   	);
   
       // 获取数组中的value
           function getval1($arr){
               foreach($arr as $key=>$val){
                   $row[]=$val;
               }
               return $row;
           }
           $row1 = getval1($arr);
           echo '<pre>';
           print_r($row1);
           echo '</pre>';
           /* 打印结果：
               Array
               (
                   [0] => php
                   [1] => js
                   [2] => html5
               )
           */
   
       // 获取数组中的key
           function getval2($arr){
               foreach($arr as $key=>$val){
                   $row[]=$key;
               }
               return $row;
           }
           $row2 = getval2($arr);
           echo '<pre>';
           print_r($row2);
           echo '</pre>';
           /* 打印结果：
               Array
               (
                   [0] => item1
                   [1] => item2
                   [2] => item3
               )
           */
       
       // 把数组中的key和value对调
           function getval3($arr){
               foreach($arr as $key=>$val){
                   $row[$val]=$key;
               }
               return $row;
           }
           $row3 = getval3($arr);
           echo '<pre>';
           print_r($row3);
           echo '</pre>';
           /* 打印结果：
               Array
               (
                   [php] => item1
                   [js] => item2
                   [html5] => item3
               )
           */
       
       // 求数组中所有值之和
           $brr = array(1,2,3,4,5);
           function getval4($brr){
               foreach($brr as $key=>$val){
                   $tot+=$val;
               }
               return $tot;
           }
           $row4 = getval4($brr);
           echo '<pre>';
           print_r($row4);
           echo '</pre>';
           /* 打印结果：15 */
       
       // 求数组中所有值的乘积
       	$crr = array(1,2,3,4,5);
           function getval5($crr){
               $tot = 1;
               foreach($crr as $key=>$val){
                   $tot*=$val;
               }
               return $tot;
           }
           $row5 = getval5($crr);
           echo '<pre>';
           print_r($row5);
           echo '</pre>';
           /* 打印结果：120 */
   
       // 判断一个值在不在数组中
       	function getval6($str,$arr){
               foreach($arr as $key=>$val){
                   if($val==$str){
                       return true;
                   }
               }
           }
           $row6 = getval6('php',$arr);
           echo '<pre>';
           var_dump($row6);
           echo '</pre>';
   		/* 打印结果：bool(true) */
   
       // 元素个数
       	function getval7($arr){
               foreach($arr as $key=>$val){
                  $tot++;
               }
               return $tot;
           }
           $row7 = getval7($arr);
           echo '<pre>';
           print_r($row7);
           echo '</pre>';
   		/* 打印结果：3 */
   
       // 数组值合并
       	$arr2 = array(
               'item4'=>'java',
               'item5'=>'flutter'
           );
   		function getval8($arr,$arr2){
               foreach($arr as $key=>$val){
                   $row[$key]=$val;
               }
               foreach($arr2 as $key2=>$val2){
                   $row[$key2]=$val2;
               }
               return $row;
           }
   		$row8 = getval8($arr,$arr2);
   		echo '<pre>';
   		print_r($row8);
   		echo '</pre>';
   		/* 打印结果：
               Array
               (
                   [item1] => php
                   [item2] => js
                   [item3] => html5
                   [item4] => java
                   [item5] => flutter
               )
   		*/
       // 数组过滤
   		$drr = array(0,1,2,3,4,5,6);
   		function getval9($drr){
               foreach($drr as $val){
                   if($val%2==1){
                       $row[]=$val;
                   }
               }
               return $row;
           }
   		$row9 = getval9($drr);
   		echo '<pre>';
   		print_r($row9);
   		echo '</pre>';
   		/* 打印结果：
               Array
               (
                   [0] => 1
                   [1] => 3
                   [2] => 5
               )
   		*/
       
       // 数组键值合并
   		$sss1 = array('js','php');
   		$sss2 = array('java','flutter');
   		function getval10($sss1,$sss2){
               for($i=0;$i<2;$i++){
                   $row[$sss1[$i]]=$sss2[$i];
               }
               return $row;
           }
   		$row10 = getval10($sss1,$sss2);
   		echo '<pre>';
   		print_r($row10);
   		echo '</pre>';
   		/* 打印结果：
               Array
               (
                   [js] => java
                   [php] => flutter
               )
   		*/
   ?>
   ```

10. 系统数组函数

    1. 数组的键值操作函数

        ```PHP
        <?php
    		$arr = array(
                'item1'=>'php',
                'item2'=>'javascript',
                'item3'=>'html5'
            );
            /* 1.获取数组中的值 array_values() */
                $val = array_values($arr);
                echo '<pre>';
                print_r($val);
                echo '</pre>';
                /* 打印结果：
                    Array
                    (
                        [0] => php
                        [1] => javascript
                        [2] => html5
                    )
                */

    		/* 2.获取数组中的键 array_keys() */
                $key = array_keys($arr);
                echo '<pre>';
                print_r($key);
                echo '</pre>';
                /* 打印结果：
                    Array
                    (
                        [0] => item1
                        [1] => item2
                        [2] => item3
                    )
                */
        
    		/* 3.判断一个值是否在数组中 in_array() */
                $ina = in_array('php',$arr);
                echo '<pre>';
                var_dump($ina);
                echo '</pre>';
                /* 打印结果：bool(true) */
        
    		/* 4.判断一个键是否在数组中 array_key_exists() */
                $kee = array_key_exists('item1',$arr);
                echo '<pre>';
                var_dump($kee);
                echo '</pre>';
                /* 打印结果：bool(true) */
        
    		/* 5.数组中键值对调 array_flip() */
                $flip = array_flip($arr);
                echo '<pre>';
                print_r($flip);
                echo '</pre>';
                /* 打印结果：
                    Array
                    (
                        [php] => item1
                        [javascript] => item2
                        [html5] => item3
                    )
                */
            /* 6.数组反转 array_reverse() */
                $reve = array_reverse($arr);
                echo '<pre>';
                print_r($reve);
                echo '</pre>';
                /* 打印结果：
                    Array
                    (
                        [item3] => html5
                        [item2] => javascript
                        [item1] => php
                    )
                */
        ?>
        ```
    
    2. 统计数组的元素和唯一性
    
        ```php
        <?php
            $arr = array(
                'item1'=>'php',
                'item2'=>'javascript',
                'item3'=>'html5',
                'item4'=>'php'
            );
            /* 1.统计数组元素个数 count() */
                $rst1 = count($arr);
                echo $rst1;
                /* 打印结果：4 */

            /* 2.统计数组中所以值出现的次数 array_count_values() */
                $rst2 = array_count_values($arr);
                echo '<pre>';
                print_r($rst2);
                echo '</pre>';
                /* 打印结果：
                    Array
                    (
                        [php] => 2
                        [javascript] => 1
                        [html5] => 1
                    )
                */

            /* 3.统计数字中唯一值 array_unique() */
                $rst3 = array_unique($arr);
                echo '<pre>';
                print_r($rst3);
                echo '</pre>';
                /* 打印结果：
                    Array
                    (
                        [item1] => php
                        [item2] => javascript
                        [item3] => html5
                    )
                */
        ?>
        ```
    
     3. 使用回调函数处理数组的函数
    
        ```PHP
        <?php
            $arr = array(1,2,3,4,5,6,7,8,9,10);
            /* 1.过滤数组中为真的值 array_filter() */
            	$rst1 = array_filter($arr,'odd');
        		function even($val){
                    return $val%2==1;
                }
        		function odd($val){
                    return $val%2==0;
                }
        		echo '<pre>';
        		print_r($rst1);
        		echo '</pre>';
        		/* 打印结果：
                   Array
                    (
                        [1] => 2
                        [3] => 4
                        [5] => 6
                        [7] => 8
                        [9] => 10
                    )
        		*/
          
            /* 2.使用回调函数作用数组中的每个值 array_map() */
        		$rst2 = array_map('mod',$arr);
        		function mod($val){
                    return $val+2;
                }
        		echo '<pre>';
        		print_r($rst2);
        		echo '</pre>';
        		/* 打印结果：
                  	Array
                    (
                        [0] => 3
                        [1] => 4
                        [2] => 5
                        [3] => 6
                        [4] => 7
                        [5] => 8
                        [6] => 9
                        [7] => 10
                        [8] => 11
                        [9] => 12
                    )
        		*/
        ?>
        ```
    
     4. 数组的排序函数
    
        ```php
        <?php
            /* 1. sort() 不保留原数组key的升序排序 */
            	$arr = array(1000,10,3,7,200);
            	sort($arr);
                echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
        			Array
                    (
                        [0] => 3
                        [1] => 7
                        [2] => 10
                        [3] => 200
                        [4] => 1000
                    )
        		*/
        
            /* 2. rsort() 不保留原数组key的降序排序 */
        		$arr = array(1000,10,3,7,200);
        		rsort($arr);
                echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                    Array
                    (
                        [0] => 1000
                        [1] => 200
                        [2] => 10
                        [3] => 7
                        [4] => 3
                    )		
        		*/
            
            /* 3. asort() 保留key进行升序排序 */
        		$arr = array(1000,10,3,7,200);
        		asort($arr);
                echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                    Array
                    (
                        [2] => 3
                        [3] => 7
                        [1] => 10
                        [4] => 200
                        [0] => 1000
                    )
        		*/
            
            /* 4. arsort() 保留key进行降序排序 */
        		$arr = array(1000,10,3,7,200);
        		arsort($arr);
                echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                    Array
                    (
                        [0] => 1000
                        [4] => 200
                        [1] => 10
                        [3] => 7
                        [2] => 3
                    )
        		*/
            
            
            /* 5. ksort() 按key进行升序排序*/
        		$brr = array(
                    1000=>'php',
                    10=>'javascript',
                    7=>'html5',
                    3=>'css3'
            	);
            	ksort($brr);
                echo '<pre>';
        		print_r($brr);
        		echo '</pre>';
        		/* 打印结果：
                    Array
                    (
                        [3] => css3
                        [7] => html5
                        [10] => javascript
                        [1000] => php
                    )
        		*/
        
            /* 6. krsort() 按key进行降序排序*/
        		$brr = array(
                    1000=>'php',
                    10=>'javascript',
                    7=>'html5',
                    3=>'css3'
            	);
        		krsort($brr);
                echo '<pre>';
        		print_r($brr);
        		echo '</pre>';
        		/* 打印结果：
                   Array
                    (
                        [1000] => php
                        [10] => javascript
                        [7] => html5
                        [3] => css3
                    )
        		*/
            
        	
            /* 7. natsort() 按自然数排序*/
        		$crr = array('a','c','d','b','e');
            	natsort($crr);
                echo '<pre>';
        		print_r($crr);
        		echo '</pre>';
        		/* 打印结果：
                  	Array
                    (
                        [0] => a
                        [3] => b
                        [1] => c
                        [2] => d
                        [4] => e
                    )
        		*/
        	
        	
            /* 8. natcasesort() 忽略大小写排序*/
        		$drr = array('a','c','d','b','e','A');
        		natcasesort($drr);
                echo '<pre>';
        		print_r($drr);
        		echo '</pre>';
        		/* 打印结果：
                  	Array
                    (
                        [0] => a
                        [5] => A
                        [3] => b
                        [1] => c
                        [2] => d
                        [4] => e
                    )
        		*/
        
            /* 9. array_multisort() 多数组排序 默认参数不加SORT_DESC是降序排序*/
        	$err = array(
                'title1'=>'php',
                'title2'=>'js',
                'title3'=>'html5'
            );	
        	foreach($err as $val){
                $row[]=strlen($val);
            }
        	array_multisort($row,SORT_DESC,$err);
        	echo '<pre>';
        	print_r($err);
        	echo '</pre>';
        	/* 打印结果：
                Array
                (
                    [title3] => html5
                    [title1] => php
                    [title2] => js
                )
        	*/
        ?>
        ```
    
     5. 数组截取与合并函数
    
        ```PHP
        <?php
            /* 1. array_slice() 数组截取 */
                $arr = array(
                    'item1'=>'javascript',
                    'item2'=>'html5',
                    'item3'=>'css3',
                    'item4'=>'php'
                );
                $slice = array_slice($arr,2,3);
                echo '<pre>';
                print_r($slice);
                echo '</pre>';
                /*打印结果：
                    Array
                    (
                        [item3] => css3
                        [item4] => php
                    )
                */
        		$slice = array_slice($arr,-1);
        		echo '<pre>';
                print_r($slice);
                echo '</pre>';
                /*打印结果：
                   	Array
                    (
                        [item4] => php
                    )
                */
        
        	/* 2. array_splice() 数组截取,会改变原来的数组,
        		并且可在原截取数组的位置添加新数组 */
        		$arr = array(
                    'item1'=>'javascript',
                    'item2'=>'html5',
                    'item3'=>'css3',
                    'item4'=>'php'
                );
        		$splice = array_splice($arr,2,3,array('a','b'));
        		echo '<pre>';
        		print_r($splice);
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                    Array
                    (
                        [item3] => css3
                        [item4] => php
                    )
                    Array
                    (
                        [item1] => javascript
                        [item2] => html5
                        [0] => a
                        [1] => b
                    )
        		*/
        
        	/* 3. array_combine() 数组合并，键值合并 */
        		$arr = array('a','b','c');
        		$arr2 = array(1,2,3);
        		$arr3 = array_combine($arr,$arr2);
        		echo '<pre>';
        		print_r($arr3);
        		echo "</pre>";
        		/* 打印结果：
        			Array
                    (
                        [a] => 1
                        [b] => 2
                        [c] => 3
                    )
        		*/
        
        	/* 4. array_merge() 数组合并，值合并 */
        		$arr = array('a','b','c');
        		$arr2 = array(1,2,3);
        		$arr3 = array_merge($arr,$arr2);
        		echo '<pre>';
        		print_r($arr3);
        		echo "</pre>";
        		/* 打印结果：
        			Array
                    (
                        [0] => a
                        [1] => b
                        [2] => c
                        [3] => 1
                        [4] => 2
                        [5] => 3
                    )
        		*/
        ?>
        ```
    
     6. 数组拆分与连接函数
    
        ```PHP
        <?php
            /* 1. implode() 数组合并*/
            	$arr = array('2219','07','27');
        		$str = implode('-',$arr);
        		echo $str;
        		/* 打印结果：2219-07-27 */
            
            /* 2. explode() 数组分割*/
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
        
        	/* 3. join() 数组合并 */
        		$arr = array('2219','07','27');
        		$str = join('-',$arr);
        		echo $str;
        		/* 打印结果：2219-07-27 */
        ?>
        ```
    
     7. 数组与数据结构
    
        ```php
        <?php
            /* 1. array_pop() 删除数组中最后一个元素 */
            	$arr = array('php','js','html5','css3');
        		echo array_pop($arr);
        		echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                    css3
                    Array
                    (
                        [0] => php
                        [1] => js
                        [2] => html5
                    )
        		*/
        
        	/* 2. array_shift() 删除数组中第一个元素 */
        		$arr = array('php','js','html5','css3');
        		echo array_shift($arr);
        		echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                   	php
                    Array
                    (
                        [0] => js
                        [1] => html5
                        [2] => css3
                    )
        		*/
        
        	/* 3. array_push() 从数组最后插入一个元素 */
        		$arr = array('php','js','html5','css3');
        		echo array_push($arr,'java');
        		echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                   	5
                    Array
                    (
                        [0] => php
                        [1] => js
                        [2] => html5
                        [3] => css3
                        [4] => java
                    )
        		*/
        
        	/* 4. array_unshift() 从数组第一个插入一个元素 */
        		$arr = array('php','js','html5','css3');
        		echo array_unshift($arr,'java');
        		echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
                   	5
                    Array
                    (
                        [0] => java
                        [1] => php
                        [2] => js
                        [3] => html5
                        [4] => css3
                    )
        		*/
        ?>
        ```
    
     8. 其他有用的数组处理函数
    
        ```PHP
        <?php
        	/* 1. range() 生产有规律的数组*/
                // $arr = range('a','z');
                $arr = range(0,3);
                echo '<pre>';
                print_r($arr);
                echo '</pre>';
                /* 打印结果：
                	Array
                    (
                        [0] => 0
                        [1] => 1
                        [2] => 2
                        [3] => 3
                    )
                */
        
        	/* 2. array_sum() 计算数组值的和 */
                $arr = array(1,2,3,4,5);
                echo array_sum($arr);
                /* 打印结果：15 */
        	
        	/* 3.shuffle() 打乱原数组 */
        		$arr = array(1,2,3,4,5);
                shuffle($arr);
        		echo '<pre>';
        		print_r($arr);
        		echo '</pre>';
        		/* 打印结果：
        			Array
                    (
                        [0] => 1
                        [1] => 2
                        [2] => 4
                        [3] => 3
                        [4] => 5
                    )
        		*/
        
        	/* 4.array_rand() 随机下标 */
        		$arr = array(1,2,3,4,5);
                $key = array_rand($arr);
        		echo $arr[$key];
        		/* 打印结果：3  通过随机key取一个随机值*/
        
        	/* 小实例 五位随机验证码*/
        		$arr = array_merge(range(0,9),range('a','z'),range('A','Z'));
        		shuffle($arr);
        		$arr2 = array_slice($arr,0,5);
        		$str = join('',$arr2);
        		echo $str;
        		/* 打印结果：gD3NP */
        ?>
        ```
    