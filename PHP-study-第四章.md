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
   2. for

3. 特殊流程控制

   1. break
   2. continue
   3. exit
   4. die