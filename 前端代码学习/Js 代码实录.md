# Js 代码实录





## JS 基础

### 简介

- **简称JS**
      	基本的作用：制作网页特效
      	移动端网页的制作   移动app
      	nodejs 能够进行服务器端运行

- **JS的特殊点**

  ​	从服务器取东西到前端所用的工具是：
  ​		ajax(仅针对JS)

  ​	JS在前端的地位：仅次一种通用语言 -->

-  **history:**
  	网景：natscape —— 开发了一个语言：
  	最初的目的 可以解决网络环境不好的情况下，用户对表达提交的问题进行验证

    ps：java和javascript完全没有关系

  ​	补充： 
  ​	javascript     网景
  ​	JSscript       微软

     两个语言，两个规范  需要进行统一：
  	ECMA一起制定了javascript的规范，成为ECMAScript

​	每个浏览器厂商在完善自己语言时，都必须按照ECMAScript的规范制作，但是每个厂商都有自己的特点，这就导致了兼容性的问题。 



- **当我们访问一个链接时，会发生什么事儿？**

​	 域名：区域的名字，地址，类似门牌号 www.baidu.com
​	 	
​	 	请求过程：我的计算机 输入域名 ____ 通过网络地址找到服务器
​	 	响应过程：服务器接收到用户请求，根于内容返回相应数据____用户进行接收-->



- **当浏览器读取到一个页面时，会做什么？**

  ​	浏览器的组成：
  ​		1、用户界面  你能看见的区域都是
  ​		2、浏览器引擎(核心作用，中控 类似cup进行资源分配)
  ​		3、渲染引擎：用户解析html和css文件  将文本语言翻译好在浏览器中呈现
  ​		4、JS解析器：用户解析js代码

  ​		上面四个组成必须背下来

  ​		5、网络模块

  ​			过程：
  ​			1、(渲染引擎)读取html文件，根据html中每个标签之间的相互关系生成一个树模型
  ​			2、(渲染引擎)读取css文件，根据css中每个样式，生成一个样式树模型
  ​			3、将html和css进行合并，生成渲染树(页面准备开始显示了)
  ​			4、根据渲染树设生成用户可以看到的页面：
  ​				4/1 显示每个标签显示到置顶位置，设置尺寸(排列)
  ​				4/2 显示标签内部的颜色、图片、文字(绘制)

  ​			现进排列，搭好结构，再进行内容渲染，最后进行显示。

- **JS引入方式**

  ```html
  <!DOCTYPE html>
  <html lang="en">
      <head>
          <meta charset="utf-8">
          <script src="111.js">  
          // <!-- 外联式：标签中间不能书写代码，因为会被src执向读取到的文件的内部代码尽心替代 -->
          </script>
      </head>
      <body>
      <!-- src属性  会将读取到的文件内部代码，替换掉当前标签内的所有内容 -->
      <!-- href属性 直接连接到相应文件进行执行 -->
      
  
  
  
  
  
      <!-- 行内式  不要使用 -->
      </body>
  </html>
  ```



- **JS 变量**

  1.变量的作用：存储数据，让数据可以重复利用
  2.数据的形式：固定数据和临时数据
      	   例：qq安装有200m  qq使用时间长了有缓存(在这里200m是固定数据 缓存是临时数据)

  ​	记住：	  JS在执行的时候都是临时数据  
  ​	  	  我们代码中书写的变量或数据都是临时的 

   3.固定数据和临沭数据保存：

  ​	  			固定数据保存在硬盘中             安装后的程序大小占地
  ​	  			临时数据常规情况下保存在内存中   程度进行操作的时候

   4.数据在栈中保存的方式：

  ​	  	栈：分了很多个区域  每个区域都有自己的地址
  ​	  		为了程序调用方便，我们将地址名替换成变量名
  ​	  		例：var num = 100;

  ​	  			本质：num实际保存所在的内部单元地址  根据地质再找具体数据

  ​	  			注意：但是为了表述方便，我们直接就称呼
  ​	  				  使用变量就是使用内部的数据

  ​    	  

- **变量的基本操作**

  ​	**1、变量的声明方式：**

  ​			关键字 变量名
  ​			var 变量名

  ​			1.1 命名规则：
  ​					开头可以为_$英文字母
  ​					内部可以有数字
  ​					不能使用js的关键字 保留字
  ​					注意：严格区分大小写
  ​						  变量名中不能出现空格

  ​				  	关键字 =(约等) 功能字

  ​				  	必须：命名有意义

  ​		**2、赋值：(变量使用过程中的重新赋值)**
  ​			     JS是一个动态语言
  ​			     例：
  ​			     var num;
  ​			     num = 100;
  ​			     num = "aaa"
  ​			     //能够进行数据类型的更改，但是  不推荐 

  ​		****3、语句：通过某一句代码无法得到一个结果，成为语句**
  ​		**4、表达式：通过某一句代码可以得到一个结果，成为表达式**
  ​		5、返回值：通过某一句代码可以得到这个结果，称为返回值**

  ​			语句没有返回值，返回值为undefined

  ​	 	**6、初始化：变量在声明的同时进行赋值**
  ​	 			   var num = 100;

  ​	 	**7、赋值和初始化的区别在于，一个又返回值，一个没有返回值**
  ​	 	   赋值是表达式，可以得到赋值的那个值
  ​	 	   初始化是语句，没有返回值

  ​	 	   检测方式直接找浏览器中的控制台

  ​	 	**8、声明 赋值 初始化**



- **不规则变量的使用**

  1.怪异的变量声明方式(单个变量)
      	   声明变量的时候不加var

  ```
  num  = 200;
  	   console.log(num);
  ```

  ​	

    2.多个声明(怪异)

  ```
  var a = b = c = 3
  ```

  以上所有的方法都不要用





- **基本数据类型**

  五大基本数据类型
      1.1 
      	 	检测方式：typeof 数据   typeof(数据)

  ​	 1.2 
  ​	 	 **string**字符串类型   JS中的字符串必须使用单引号或者双引号
  ​	 	 **number**数值类型     整数 
  ​	 	 					小数
  ​	 	 					NaN - 不是数字的一种数值
  ​	 	 					Infinity  无穷大
  ​	 	 					-Infinity  无穷小
  ​	 	 					Number.MAX_VALUE 正数的最大值
  ​	 	 					Number.MIN_VALUE 正数的最小值

  

  ​	 	 **boolean**布尔类型   //true false
  ​	 	 **undefined**		   //出现的场景
  ​	 	 					 (1).变量没有赋值
  ​	 	 					 (2).语句没有返回值，默认为undefined
  ​	 	 					 (3).变量没有赋值，和没有定义变量是有区别的
  ​	 	 					 		例：console.log(num) //这是没有声明变量
  ​	 	 					 		例：var num;
  ​	 	 					 			console.log(num) //这是声明了变量没有赋值
  ​	 	 
  ​	 	 **null** 				//使用typeof检测null的类型不准确，会显示boject
  ​			
  ​		 带字母的都是字符串类型

- 类型转换方式

  将其他数据类型转换为**字符串类型：**
  		1、强制转换方式
  			**数据.toString();**
  			String(数据);

  ​			这两者的区别：
  ​				undefined和null都没有 数据.toString() 转换类型方式
  ​				Cannot read property "toString" of undefined //意味undefined没有toString这个属性

  ​		2、隐式转换方式
  ​			使用任意数据类型**+**任意字符串，可以连接为一个新的字符串(+为连接符)-

  ​			为了不改变数据的原内容，我们使用空字符串来进行连接
  ​			var num = 100;
  ​			console.log(num + "");-->

  转换为**数值**的方式
  		1、强制转换

  ​			方式一：**Number();**

  ​			转换时，字符串中必须为纯数字字符串，否则转换失败 成NaN
  ​					console.log(Number("100"));
  ​					console.log(Number("100abc")); 

  ​			boolean:
  ​				console.log(Number(true));//1
  ​				console.log(Number(false));//0

  ​				null //0
  ​				undefined //NaN

  ​			方式二：**parseInt()**

  ​			可以去除一部分字符一部分数值的字符串内的数值部分
  ​			取值方式，从左往右取，取到不是数值为止
  ​				console.log(parseInt("100abc200")); //100
  ​				console.log(parseInt("abc200")); //NaN
  ​				console.log(parseInt("100.1123")); //100

  ​			方式三：parseFloat()
  ​				
  ​				console.log(parseFloat("100.112aaa")); //100.112

  ​			注意：使用parse系列转换null和undefined时，结果均为NaN
  ​			parseInt(null); //NaN
  ​			parseInt(undefined); //NaN
  ​		
  ​		2、隐式转换:隐式转换时，字符只能含数字字符，才能转换为纯数字
  ​			**-+*/%**
  ​			保证内容不变进行字符串转换
  ​			console.log("100" - 0);
  ​			console.log("100" * 1);
  ​			console.log("100" / 1);
  ​			console.log("100" % Infinity);


  ​    			

  ​			转换为bool类型
  ​			1、强制转换 Boolean(数据)
  ​			2、隐式转换 !!
  ​				console.log(!!数据);
  ​				//转换为false的数据有且只有6个：false "" 0 NaN undefined null（空指针）

  ​			数值（number）:安拉伯数字，NaN

  ​                NaN非常特殊，NaN不大于任何数字，同时NaN不等于自身NaN

  

  

  

- **操作符**

  **算数运算符：+-*/%**
      	 一元运算符：参与运算的操作数只有一个
      	 	一元+操作
      	 	++ -- ! typeof 

  ​	 自增 ++

  ​	 	无论++前置还是后置，只能决定当前位置的取值

  ​	 (1)、单独使用时，前置与后置没有区别
  ​	  var num = 100;
  ​	  num++;
  ​	  console.log(num); 

  ​	 (2)、与其他的运算结合使用时，前置和后置不同
  ​	 		前自增
  ​	 		后自增

  ​	 比较运算符 < > <= >=

  ​	 相等运算符 == === != !== 
  ​	 		相等比较内容
  ​	 		全等比较内容、类型

  ​	 注意：	NaN和任何类型进行比较包括自己返回都是false
  ​	 		NaN和任何类型进行计算，返回NaN 包括自己

  ​	 	可以使用isNaN()去检测一个数据是否为数字且类型为number
  ​	 			是，返回false

  ​	 逻辑运算符:
  ​	 	&& || !
  ​	 	逻辑与：两个操作数均为true，结果为true
  ​	 	逻辑或：两个操作数均为false，结果为false
  ​	 	逻辑非：取反

  ​	 	注意：当操作数不是bool值是：(短路操作)
  ​	 		console.log("100" && "abc");
  ​	 		
  ​	 		判定流程：
  ​	 				//从左往右看
  ​	 				//如果当前操作数不是bool值，隐式转换为bool值
  ​	 				//那个操作数可以决定式子的结果，就返回这个源操作数

  ​			&& 一假则假
  ​			|| 一真则真

  

  ​	 赋值运算符：= -= += *= /= %=
  ​	 	后面的其他赋值运算符，表示自身值进行操作
  ​	 	var num = 100;
  ​	 	num += 20; //num = num + 20;

  

- 小结

  ​        1、请求和相应
  ​    	 2、浏览器的主要组成部分：用户界面，浏览引擎，渲染引擎(html和css) JS解析器
  ​		 3、浏览器读到页面后做什么：结构树-样式树-渲染树-哦案列大小-渲染

  ​	 变量：
  ​	 	作用：存储数据
  ​	 	存储方式：临时数据保存在内存中
  ​		简便来说，使用变量就是使用变量内保存的数据
  ​		变量声明：关键字 变量名
  ​		变量初始化：关键字 变量名：值
  ​		语句：没有返回值
  ​		表达式：又返回值
  ​		赋值：可以动态进行类型修改，可以进行数据类型的修改(不推荐，影响不可控)
  ​		基本数据类型：number string boolean null undefined
  ​		检测数据类型工具typof (但是对于null进行检测是不准确的)

  

  ​		转换方式：

  ​		变量.toString() //null和undefined是无法使用这个进行转换的
  ​		string()
  ​		XXX + ""//为了保持原意 一般加空字符串

  ​		Number()

  ​		//从左往右取，直到取不到数为止，进行数字转换
  ​		parseInt()
  ​		parseFloat()
  ​		-+*/%

  ​		Boolean() !! if(中的条件语句) 结果为false的：false 0 "" NaN undefined nill

  ​		运算符：
  ​		+-*/%
  ​		一元运算符：++ --
  ​		比较运算符： > < = < == === != !== 输出值必是bool值，两边类型不同，进行隐式
  ​		赋值运算符：+= —= *= /=  
  ​		逻辑运算符：&& || ！先进行&&后||进行运算

  ​		情况一：当操作数均为bool值
  ​			逻辑与：全真则真
  ​			逻辑或：全假则假
  ​			逻辑非：取反

  ​		情况二：当操作数为非bool
  ​			逻辑与：从左往右看，进行隐形转换，有false直接进行反馈，返回原操作数
  ​			逻辑或：。。。。，有true直接反馈，返回原操作数

  ​		优先级：
  ​			括号()
  ​		    一元：++ -- + ！(取反)
  ​		    算数：* / % + -
  ​		    比较运算符：> < >= <= == != === !=
  ​		    逻辑运算符：&& ||
  ​		    三元运算符：?:;
  ​		    赋值运算符：= += -= /= %=

  ​		    程序的执行顺序：
  ​		    顺序结构：按照书写顺序执行
  ​		    分支，选择，条件判断(if switch)
  ​		    循环结构(for while do....while)

  ​		    if语句的三种使用方式:
  ​		    	单if:
  ​		    		if(条件判断语句){

  ​		    		}

  ​		    	if...else

  ​		    	多种情况if....else...if....else...if...else

  ​				注意：
  ​					1、两种后面的东西必须进行 === 全等 来进行返回值
  ​					2、必须有break

  ​				进行范围比较，可以在条件书写true即可

  ​		    	switch(表达式，值){
  ​					case 表达式、值：
  ​		    	}


  ​					

  ​				while(){
  ​					使用场景：循环执行次数不定的重复执行代码
  ​				}

  ​				do..while();
  ​				//两者区别在于，无论条件是否成立，都会先执行一次do内的代码

  

  ​    	

- 

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title></title>
        <script>
        	//控制打印行数
		for (var j = 0;j < 10;j++) {
			//控制每行打印10个x
			for (var i = 0;i < 10;i++) {
				document.write(Math.floor(Math.random()*10));
			}
			//每次打印结束之后，要进行进行一个换行操作
			document.write("</br>");
		}




		/* 直角三角形 */
		//第一行：一个x
		//第二行：两个x
		//不难看出，我们每行的打印个数，和这个行数成正相关，而且行数有限，因此采用for循环，首先来书外循环
		
		for (var count = 1;count <= 10;count++) {
			//每行的打印个数，和行数成正相关，这样的话我们需要将内循环的控制数，和外循环进行一个关联，也就是判定条件min从1开始，max到10
			//所以：
			

			/* 思考+1：*/
			/* 在这里我们是不需要进行条件判定的，if是完全没有意义的，count增加1，必然i也会增加1，两者的数值永远相等，这个条件永远成立加if完全是一种浪费，所以不用加条件判定 */

			/* 思考+2 */ 
			/* 内循环：实际上在每次外循环执行一次的时候，内循环都需要进行重新声明，因此，建议将内循环的var i 声明，放在最外面定义 */ 
			// 注：避免重复声明对于内存的浪费，最好将var i 放在循环外面
			
			for (var i = 1;i <= count;i++) {
				document.write(Math.floor(Math.random()*10));
			}
			//在一行打印完毕之后我们需要进行换行操作
			document.write("<br/>")
		}
		
        </script>
    </head>
    <body>
    <!-- 什么时候需要使用循环嵌套 -->
    <!-- 通过题目进行分析
		打印10*10的星号

		打印10个星星实际上就是将一次打印星星重复10次

		for(var i = 0;i < 10;i++) {
			document.write("x");

		}
		一行打印完毕，需要进行换行，也就是写一个换行标签br
		但是需要打10行，也就是重复10次这个打印10次的操作

		我们发现，上面的两段代码表示一行星星所需要的代码，需要重复执行10次
		

		//控制打印行数
		for (var j = 0;j < 10;j++) {
			//控制每行打印10个x
			for (var i = 0;i < 10;i++) {
				document.write("x");
			}
			//每次打印结束之后，要进行进行一个换行操作
			document.write("</br>");
		}


		明白每个循环的含义，为什么要用，怎么进行功能块的分隔，如何进行的实现



     -->
    </body>
</html>
```





- 表格

  ```html
  <!DOCTYPE html>
  <html lang="en">
      <head>
          <meta charset="utf-8">
  
  
  
  		<script>
  			//需求：创建十行，根据每行的编码，显示相应个数的数字
  			//创建表头和表身的上半部分
  			document.write("<table><thead></thead><tbody>");
  			//进行行创建
  			for (var i = 0;i <= 10;i ++) {
  				document.write("<tr>");
  				for (var j = 0;j <= i;j ++) {
  					document.write("<td>" + Math.floor(Math.random()*10) + "</td>");
  				}
  				document.write("</tr>");
  			}
  			document.write("</tbody></table>");
  		</script>
  
  
      </head>
      <body>
  	<!--<div class="box">-->
  
  	<!--</div>-->
  	<script>
  //		var box = document.getElementsByClassName("box")[0];
  //
  //
  //		var NewElement = document.createElement("p");
  //		NewElement.innerText = "今天天气不错！"
  //		box.innerText = "今天下雨";
  //		box.innerHTML = "雨停了";
  //		box.innerHTML = "准备下海起航";
  //		//进行节点内容的添加
  //		box.appendChild(NewElement);
  //		console.log(box);
  //		console.log(NewElement);
  	</script>
      </body>
  </html>
  ```

  



- break 和 continue

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <script>
        	// 1-100被7整除的整数的和(用continue)
        	// var sum = 0;


        	// //求200-300之间第一个能被7整除的数
        	// var result = 0;
        	// for (var count = 200;count <= 300;count++) {
        	// 	if (count %7 == 0) {
        	// 		document.write(result);
			//		break;
        	// 	}
        	// }
        	// 



        	//求1到100之间所有不能被3整除的整数的第一个大于2000的和（用continue和break）
        		var sum = 0;
        		for (var count = 0;count <= 100;count++) {
        			if (count%3 == 0) {
        				continue;
        			}else {
        				sum += count;
        				
        				}
        				if (sum > 2000) {
        					document.write(sum);
        					break;//结束循环语句，下载那个循环当中就结束哪个循环，因为if不是循环，她在for循环当中，所以直接结束for循环
        				}

        			}
        </script>
    </head>
    <body>
    <!-- break:跳出循环

    	 continue:结束本次循环，听从下一次循环的顶部开始

    	 break:遇见直接结束所在的循环

    	 continue可以结束 -->
    </body>
</html>
```





- 质数

  ```html
  
  <script>
          		
          	//方式三：计数法
          	var count = 0;//记录可以整除num的值的个数
          	var num = 16;
          	for (var i = 2;i < num;i++) {
          		if (num /i == 0) {
          			count++;
          		}
          	}
          	console.log(count);
          	if (count == 0) {
          		alert("是质数");
          	} else {
          		alert("不是质数");
          	}
  
  
  
          	//方式四：假设成立法
          	//使用场景：两种情况无法确定时，可以使用假设成立发
          	
          	//第一部分：进行假设条件的判定
          	//1、根据不确定的点，假设满足当前条件
          	var flag = true;//假设当前的值是一个质数
          	var num = 15;
  
          	//2、对假设进行失败的情况进行验证(找到假设失败的条件)
          	for (var i = 2;i <num; i++) {
          		// 找到可以被num整除的数
          		if(num%i == 0) {
          			flag = false;
          			//假设不成立，设置flag = flase
          			
          		}
          	}
          	
  
          	//第二部分：进行假设条件的验证
          	if (flag) {
          		alert("不是质数");
          	} else {
          		alert("是质数");
          	}
          </script>
  
  
  ```



- **数组**

  数组简介：
  		数组也是一种数据类型 

  1、为什么要有数组？

  ​	场景：使用js保存把你同学的考试成绩

  ​	一般方法：保存全班所有人的考试成绩
  ​	var sut1 = 100;
  ​	......
  ​	var stu70 = 100;
  ​	会声明七十多个变量
  ​	整体使用多个数据时，使用不便
  ​	数组可以解决这个问题，数组的作用，可以保存多个数据，降低操作的难度

  

  **2、数组的声明方式：**
  	

  ```
  2/1 
  		构造函数创建方式：
  		var arr = new Array();
  
  ​	2/2 数组字面量创建方式(推荐使用的方式 原因是短)
  ​		var arr = [];
  
  ​	3.数组可以同时保存多个数据
  ​		
  ​		3/1.多个数据使用逗号进行分隔
  ​			var arr = [6,7,8,9,10];
  
  ​		3/2.数组中的每个数据成为数组的元素
  
  ​		3/3.数组中的元素个数，可以使用数组的长度属性length
  ​			console.log(arr.length);
  
  ​		3/4.数组中元素的排列方式称为索引，索引从0开始
  
  ​		3/5.按照索引，获取和设置数组中的某个元素值
  ​			console.log(arr[3]);
  ​			或者
  ​			console.log(arr["2"]);
  
  ​		3/6修改数组arr中索引值为4的元素，修改为100
  ​			arr[4] = 100;
  ​			或者
  ​			arr[4] = "100";
  
  ​		3/7数组在控制台中打印时需要注意的问题
  ​			var arr = [1,2,3,4,5];
  ​			console.log(arr);
  ​			arr[2] = 100;
  ​			console.log(arr);
  ```

  ​			由于控制台具有展开查看的操作，展开时会读取数组当前的值。可能会导致第一次打印结果和展开打印结果不同

  

- **数组的长度使用**

  ```
  			var arr = ["a","b","c","d","e"];
      	
      	1、数组的长度属性可以获取，也可以设置，获取表示数组当前元素个数
  
      	2、设置操作：
      		
  
  
      	情况一：设置length值大于了数组的真正元素个数
      		arr.length = 10;
      		console.log(arr);
      		//只会显示5个元素，其他的并没有，因为length是设置的
  			只会修改元素个数，不会进行真正的元素增加
  
  			console.log(arr[7]);
  			//如果访问后面多余的位置发现，值为undefined
  
  
  		情况二：设置的length值小当前数组真正的元素个数
  
              var arr = ["a","b","c","d","e"];
  			//会将多余的元素进行删除，并且无法进行恢复
  			arr.length = 2;
  			console.log(arr);
  			arr,length = 5;
  			console.log(arr);
  
  			//利用这个特性，我们可以从数组的最后进行数据的删除操作
  
  			//情况数组：arr.length = 0;
  
  ```

  



















## 基础知识

### JQuery



1. 显示和设置DIV内容

   ```html
     <script>
       //页面加载事件，等待文档全部加载之后才执行
      window.onload = function () {
        //不爽的地方
        //  1. 遍历不爽  有的时候还需要嵌套
        //  2. 获取元素的方法很少 而且代码很长
        //  3. 代码有兼容性问题
        //  4. 如果要实现动画，很麻烦 animate
        //  5. 事件的注册，多次注册后面的会覆盖前面的   addEventListener
        var btn1 = document.getElementById("btn1");
        var btn2 = document.getElementById("btn2");
        var divs = document.getElementsByTagName("div");
        btn1.onclick = function () {
          for (var i = 0; i < divs.length; i++) {
            divs[i].style.display = "block";
          }
        };
        btn2.onclick = function() {
          for (var i = 0; i < divs.length; i++) {
            // innerText火狐低版本的不兼容   textContent
            divs[i].innerText = "我是内容";
          }
        };
        console.log("小杨老师最帅");
      }
       //添加一个入口函数，html结构加载完成之后，就能进行script标签当中的内容加载
     </script>
   ```

```html
  <script>
    //不爽的地方
    //  1. 遍历不爽  有的时候还需要嵌套
    //  2. 获取元素的方法很少 而且代码很长
    //  3. 代码有兼容性问题
    //  4. 如果要实现动画，很麻烦 animate
    //  5. 事件的注册，多次注册后面的会覆盖前面的   addEventListener


    //注意：jQuery页面加载事件  标准写法
    $(document).ready(function () {
      // js里面是on   jq把on去掉
      $("#btn1").click(function () {
        // jQuery的设计   隐式迭代    偷偷地  遍历
        // 取出来的$("div")是个伪数组，在jq中可以直接进行方法添加，自动遍历
        $("div").fadeIn(3000);
      });
      $("#btn2").click(function () {
        $("div").text("我是内容");
      });
      $("#btn2").click(function () {
        console.log("呵呵");
      });
    });
      //$是个函数
      //同时需要需要页面加载函数
  </script>
```



### 入口函数

```html

<script>
    //1、ja的api：也就是jq的方法
    //2、JQ当中添加属性的方法：
    //css  css("属性名","属性值");

    //3、入口函数的三种写法：
    //js入口函数
    window.onload = function () {
        console.log("这是js的入口函数");
    }
    //jQuery入口函数的标准写法
    $(document).ready(function () {
        console.log("这是jQuery入口函数的第一种写法");
    });
    //jQuery第二种入口函数
    $(function () {
        console.log("第二种写法");
        $("#li1").css("backgroundColor", "red");
    });


    //注意js入口函数和jq入口函数两者的区别：
    //js入口函数：等待页面的结构+图片加载完毕才能够进行执行
    //jq入口函数：等待页面的结构加载完毕就能够进行执行
</script>

```



### JQuery对象和DOM对象(JS对象)的区别

```html
 <script>
    //入口函数：不管你的jq写在哪里，这个入口函数都要写
    $(function () {
      //1. 什么是DOM对象   就是js对象，就是使用js的方式获取的对象就是DOM对象
      var cloth = document.getElementById("cloth");

      //2. 什么是jQuery对象   用jQquery方式获取的对象就是jQuery对象
      var $lis = $("li");


      //3. jQuery对象和DOM对象有什么联系？  jQuery对象可以理解为一个DOM对象的伪数组   JQ是DOM对象的集合
      console.log(cloth);
      console.log($lis);

      //4. jQuery对象和DOM对象有什么区别
            // DOM对象不能调用jQuery对象的方法

            // jQuery对象不能使用DOM对象的属性     就是因为他们两个不是同一种对象


     //5、两种对象之间的转换：

        //JQ转成DOM对象的属性和方法，需要按照索引的方式，取出[0]DOM对象 .get(0)
        //等同于将JQ对象的集合打开，取出当中的一个DOM对象进行操作

        //DOM转换成jQuery对象  联想记忆  花钱 $()

    });

    /*  总结：
     * 1. 什么是DOM对象  使用js的方式获取的元素叫做DOM对象 也叫js对象
     * 2. 什么jQuery对象  使用jQuery的方式获取的元素叫做jQuery对象
     * 3. js对象和JQ对象有什么联系   jq对象可以理解为一个js对象的伪数组
     * 4. js对象和JQ对象的区别
     *    js对象不能使用JQ对象的方法
     *    JQ对象不能使用js对象的方法和属性
     *    js对象转换成JQ对象 花钱$()
     *    JQ对象转换成js对象   按照索引取出来其中的某一个 ：[index]          .get(index)
     */

    
  </script>
```



### 隔行变色

```html
<script>
// //方法一：
// //    利用jq进行入口函数的书写
// //      $("名称")，可以进行id或者类名，或者对象的直接提取
//     $(function () {
//         //利用jq进行元素的获取
//         var $lis = $("li");       //取出的是jq对象，是个伪类数组
//         //进行遍历添加背景也拿色
//         for (var i = 0; i < $lis.length; i++) {
//             //进行条件的判定
//             if (i % 2 == 0) {
//                 //lis[i]取出的是DOM对象，如果希望利用jq的方法，那么就要进行转换
//                 $($lis[i]).css("backgroundColor", "yellow");
//             } else {
//                 $($lis[i]).css("backgroundColor", "skyblue");
//             }
//         }
//     })

//方法二：
    //利用筛选元素进行背景颜色的添加
    $(function () {
        //进行奇数元素的获取
        //$("对象：odd")
         $("li:odd").css("backgroundColor","yellow");
        //进行偶数元素的获取
        //$("对象:even")
        $("li:even").css("backgroundColor","skyblue");
    })


</script>
<ul>
    <li>欢迎来到新世界</li>
    <li>欢迎来到新世界</li>
    <li>欢迎来到新世界</li>
    <li>欢迎来到新世界</li>
    <li>欢迎来到新世界</li>
    <li>欢迎来到新世界</li>
    <li>欢迎来到新世界</li>
    <li>欢迎来到新世界</li>
</ul>
</body>

```





### $的实质

```html
<script>
  // $是一个函数，在使用的时候千万记得加()
  //入口函数
  $(function () {

  });
  //1、JQ进行对象的获取
  // 获取对象
  $("#li")


  //2、DOM对象转jq对象
  // DOM对象转换jQuery对象
  $(DOM对象)
</script>
```



### JQuery的选择器

```html
<ul id="ul1">
  <li>
    <ul>
      <li id="li1">我是第一个li</li>
      <li class="li2">我是第二个li</li>
      <li>
        <ul>
          <li></li>
          <li></li>
        </ul>
      </li>
    </ul>
  </li>
  <li><span class="li2">我是span</span></li>
  <li class="li2"></li>
</ul>
</body>
<script src="jquery-1.12.4.js"></script>
<script>
  $(function () {
//    // id选择器
////    $("#li1").css("backgroundColor","pink");
//    // 标签选择器
//    $("li").css("fontSize","32px");
//    // 类选择器
//    $(".li2").text("大力出奇迹");
//    // 并集选择器
////    $("span,li").css("backgroundColor","red");
//    // 交集选择器
//    $("li.li2").css("backgroundColor","yellow");



    // 子代选择器 >   后代选择器  空格
//    $("#ul1>li").css("backgroundColor","red");

    $("ul li ul").html("aa");

    /**
     * jQuery 什么是？ 是js的一个库

     * 什么是jq对象  使用jq方式获取的对象
     * 什么是DOM对象  使用js的方式获取的对象就是DOM对象
     * jq对象就是DOM对象的伪数组
     * jq对象和DOM对象不能混用方法和属性
     * jq对象需要取出DOM对象  [0]  .get(0)
     * DOM对象转换成jq对象  花钱  $()
     *
     * $();  $(function(){})入口函数  $("#id") 找对象    $(DOM对象);
     *
     * id   标签   类选择器      并集             交集            子代选择器             后代
     * #id   div    .className   div,.classname   div.classname   > (儿子辈不能跨级)      空格(能够进行后代跨级)

     *    JQ取出来的都是伪数组
     */
  });
</script>
```







### 隔行变色

```html
<ul>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>
  <li>欢迎来到新世界</li>

</ul>
</body>
<script src="jquery-1.12.4.min.js"></script>
<script>
    //$("对象：even")  取出偶数对象
    //$("对象：add")   取出奇数对象

    //增添入口函数
    $(function (){
        //根据奇偶性的不同，利用jq进行对象的取出
        $("li:even").mouseenter(function (){
            $(this).css("backgroundColor","yellow");
        });
        $("li:even").mouseleave(function (){
            $(this).css("backgroundColor","");
        });

        $("li:odd").mouseenter(function (){
            $(this).css("backgroundColor","orange");
        });
        $("li:odd").mouseleave(function (){
            $(this).css("backgroundColor","");
        });
    })
</script>
```





### 筛选 选择器

```html

		//筛选选择器：
    //寻找儿子：.children()   寻找所有的子对象，是个伪数组   或者可以是指定的子对象  .children("各种名称")
    //寻找父亲：.parent()     寻找父元素
    //兄弟节点：.sibling()    寻找除了本节点以外的兄弟节点
    //寻找某个节点：.find("各种名称")  寻找特定的那个节点
    //寻找下一个兄弟：.next()   寻找下一个兄弟节点   .prev()  寻找上一个兄弟节点
    //对象.eq(index):伪数组当中，eq(index)特指的哪项，index是伪数组(对象)当中要取出元素的索引值   等价$("li:eq(1)")

    //由于取出的所有都是JQ对象，是个伪数组，想要提取其中的某一个，可以在后面添加[index]或者get(index)成为DOM对象
    //提取完毕后还可以加$转换回去，继续使用JQ当中的方法。
```







### 奇偶选择器

```html
<script>
    	//奇行变黄
    	$(function () {
    		$("li:even").css("backgroundColor","yellow");//代表进行偶数行的元素取出并且修饰
    		$("li:odd").css("backgroundColor","green");//代表奇数行的元素取出并且修饰
            $("li:eq(1)").css("backgroundColor","skyblue")//$("对象：eq(index)")取出的是jq伪数组当中指定的项外面得$添加将取出元素变成jq对象，index为元素在伪数组当中的索引
    	})
    	console.dir($);
 </script>
```



### index

```html
...
<ul>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
  <li><a href="#">aaa</a></li>
</ul>
...

<script>
  // index()是在同级所有兄弟元素当中的索引值，例：在这里a标签的同级兄弟只有自己，那么索引就是0
  // 另外as取出来就是一个数组，直接进行click()事件的添加，自动进行所有元素事件添加，这就是jq的特别之处，别自己再写循环了
  $(function () {
    var as = $("a");
    as.click(function () {
      var index = $(this).index();
      console.log(index);
    })
  });
</script>

```







### JS对CSS 操作

```html

<ul>
  <li>柳岩</li>
  <li>赵丽颖</li>
  <li>迪丽热巴</li>
  <li>凤姐</li>
</ul>
</body>
<script src="jquery-1.12.4.js"></script>
<script>
  $(function () {
    //1、JQ进行css样式修改，修改的是行内样式属性：

    // css方法 修改的是style  行内样式
    // 方式一：css(属性名,属性值)      多个属性只能进行逐一添加修改，不能在同一个括号内进行连写修改，但是能够进行链式编程
    // 方式二：css（{属性名:属性值}）
//    $("li").css({
//      backgroundColor:"hotpink",
//          fontSize:"32px"
//    });
    console.log($("li").eq(0).css("fontSize", "20px"));
    $("li").eq(1).css("fontSize","25px");
    $("li").eq(2).css("fontSize","30px");
    $("li").eq(3).css("fontSize","35px");
    
    //2、JQ进行css样式获取，获取的是伪数组，获取的是伪数组第一个元素当中的属性值
    // 对象.css（属性名）    进行样式值的获取   返回值是个字符串类型
    // 隐式迭代
    console.log($("li").css("fontSize"));

    //隐式迭代：
      //进行样式设置：对所有元素设置同样的属性值
      //进行样式获取：只获取伪数组的第一个值
  });
</script>

```





### Class操作

```html
<ul>
    <input type="button" value="添加basic类"/>
    <input type="button" value="添加bigger类"/>
    <input type="button" value="移除bigger类"/>
    <input type="button" value="判断bigger类"/>
    <input type="button" value="切换类"/>
    <li id="li1" class="aa bb cc dd ee">柳岩</li>
    <li>赵丽颖</li>
    <li>迪丽热巴</li>
    <li>凤姐</li>
</ul>
</body>
<script src="jquery-1.12.4.js"></script>
<script>
    //1、添加class类名：只进行类名的添加，不会进行覆盖，同时如果是同一个class名称，权重由class在style当中先后顺序决定的，
    //   和script当中书写的jq先后添加顺序是没有任何关系的，也就是说，写在后面的同名class即便最后一个进行添加，也会比前面
    //    添加的同名class权重高，应为他是写在style当中的最后面
        //方法：对象.addClass("类名");
    $(function () {
        $("input").eq(0).click(function () {
            //点击按钮给所有li标签添加basic类
            $("li").addClass("basic");
        });
        $("input").eq(1).click(function () {
            //点击按钮给所有li标签添加bigger类
            $("li").addClass("bigger");
        });

    //2、移出类名：进行制定类名的移除
        //方法：对象.removeClass("类名");
        $("input").eq(2).click(function () {
            //点击按钮给所有li标签添加bigger类
            $("li").removeClass("bigger");
        });

    //3、判断是否含有类名：
        //方法：对象.hasClass("类名");
        //用来进行条件判断
        $("input").eq(3).click(function () {
            //判断是否有bigger类
            // hasClass（）判断当前标签是否有某个类
            console.log($("li").hasClass("bigger"));
        });

    //4、类名切换：
        //方法：如果有就进行移除，没有就进行添加
        //对象.toggleClass()进行类名的切换  有就进行移除，没有进行添加
        $("input").eq(4).click(function () {
            //切换类
            // hasClass（）判断当前标签是否有某个类
//      if($("li").hasClass("basic")){
//        $("li").removeClass("basic");
//      }else{
//        $("li").addClass("basic");
//      }   本方法太麻烦

            $("li").toggleClass("basic");
        });

    });
</script>
```





### 链式编程

```
 //链式变成能够一直.下去因为修改后返回的是一个jq对象，如果说返回的不是jq对象，而是例如$("选择器 也就是单选框")prop("checked")或者attr("标签属性名")或者css("行内样式属性名")
    
  //返回的就不是一个对象，就无法继续进行链式编程了
```







### attr 操作



```html
<body>
  <!-- alt 是标签的属性    background   样式的属性 -->
  <img src="04.gif" alt="图破了" title="对对对">
</body>
<script src="jquery-1.12.4.js"></script>
<script>
  $(function () {
    //1、区分属性和样式属性还有css属性
    //属性：指的是标签自带的属性：例如id，alt，title等等，同样也包含了行内样式style属性   来自标签的属性
    //行内样式属性：指的是行内style，用来进行对象的修饰  可以利用css操作进行修改  例如：background
    //css属性：单独写在css外面，可以利用class操作进行修改


     //注意：属性包含了行内样式属性
     //意味着：attr()能够进行完成css()的部分添加属性操作


    //2、标签属性的操作：对象.attr   用来操作标签自带属性的

      //2.1进行属性的添加或者修改
    //操作方式一： $("img").attr("alt","土坯了");
            // 对象.attr("标签自带属性名称","标签修改属性值")
    //操作方式二：利用键值对
    $("img").attr({
      alt:"土坯了",
      title:"错错错",
      style:"height:1000px",//能够代替css()完成一部分操作
      aa:"bb",//能够进行自定义属性的添加
    });

      //2.2进行标签属性的取出：
        // 注意：取出的是style属性，显示的是里面的字符串
    console.log($("img").attr("style"));



    //3、移除一个属性
    $("img").removeAttr("alt");
    console.log($("img").attr("alt"));

  });
</script>

```





### prop 操作

```html


<body>
<input type="button" value="选中"/>
<input type="button" value="取消"/>
<input type="checkbox">

</body>
<script src="jquery-1.12.4.js"></script>
<script>
  // 进行checkbox单选框的手动修改
  // 修改方法：修改checkbox中，checked属性    对象.prop("checked",boolean);进行checkbox属性的手动修改，这个单选框，本身被点击就是true 再次点击就是false
  // 获取方法：获取checkbox中，checked属性    对象.prop("checked")返回当前的boolen值
  $(function () {
    $("input").eq(0).click(function () {
        console.log($("input").eq(2).prop("checked"));
      $("input").eq(2).prop("checked",true);
    });
    $("input").eq(1).click(function () {
      $("input").eq(2).prop("checked",false);
    });
  });
  
  //表单元素默认有checked属性，只是没有显示出来，可以直接获取
  //仅在表单元素当中prop和attr的用法是相通的，但我们都用attr,来修饰标签属性，prop仅进行boolean修饰的时候进行使用
</script>
</html>

```



### 表单属性

```
		//针对带有checked属性的input   也就是单选框
    //$("选择器").length     获取取出的伪数组长度
    //$("选择器":checked).length  获取被选中的单选框所组成的伪数组的长度
```



### 表格全选



```html

<div class="wrap">
  <table>
    <thead>
    <tr>
      <th>
        <input type="checkbox" id="j_cbAll"/>
      </th>
      <th>菜名</th>
      <th>饭店</th>
    </tr>
    </thead>
    <tbody id="j_tb">
    <tr>
      <td>
        <input type="checkbox"/>
      </td>
      <td>红烧肉</td>
      <td>田老师</td>
    </tr>
    <tr>
      <td>
        <input type="checkbox"/>
      </td>
      <td>西红柿鸡蛋</td>
      <td>田老师</td>
    </tr>
    <tr>
      <td>
        <input type="checkbox"/>
      </td>
      <td>红烧狮子头</td>
      <td>田老师</td>
    </tr>
    <tr>
      <td>
        <input type="checkbox"/>
      </td>
      <td>日式肥牛</td>
      <td>田老师</td>
    </tr>
    
    </tbody>
  </table>
</div>

<script src="jquery-1.12.4.js"></script>
<script>
  $(function () {
    // 先设置全选checkbox的点击事件
    $("#j_cbAll").click(function () {
      	//当上面的cb点击的时候，下面的所有cb要跟上面的cb状态一致
        //this.checked直接调取input标签当中的自带属性
      //但是如果用prop()方法，其中只能传字符串"checked"才能取出当中的值
      $("#j_tb input").prop("checked",this.checked);
      
      //获取的是DOM对象
      console.log(this);
      
      //获取的是JQ对象
      console.log($(this));
      console.log(this.checked);
    });
    
    $("#j_tb input").click(function () {
      // 当下面cb被选中的数量等于全部cb的数量的时候，上面的cb被选中
      console.log($("#j_tb input").length);
      console.log($("#j_tb input:checked").length);
      if($("#j_tb input").length == $("#j_tb input:checked").length){
        $("#j_cbAll").prop("checked",true);
      }else{
        $("#j_cbAll").prop("checked",false);
      }
    });
    
  });
</script>


```





### fadein, fadeout

```html
<head lang="zh-CN">
  <meta charset="UTF-8">
  <title></title>
  <style>
    div{
      width: 200px;
      height: 200px;
      background-color: mediumaquamarine;
      display: none;
      position:absolute;
      left:0px;
      border-radius:200px;
    }
  </style>
</head>
<body>
<input type="button" value="显示"/>
<input type="button" value="切换"/>
<div></div>
</body>
<script src="jquery-1.12.4.js"></script>
<script>
  $(function () {
    // fadein 和 fadeout 和show和hide语法基本一致
    
    //区别：
    //1、$("div").fadeToggle();
    //能够在同一个标签进行反复的设置，show系列方法没有此特效
    
    //2、里面参数为空，还是有动画效果
    $("input").eq(0).click(function () {
      $("div").fadeIn("normal", function () {
        console.log("hehe");
      });
    });


    //动效bug
    $("input").eq(1).click(function () {
      $("div").stop(true,false).fadeToggle("slow", function() {
        clearInterval(timer);
        var timer = setInterval(function(){
                    console.log(1)
                    console.log($("div").css("left"));
                    if($("div").css("left") == "0px") {
                    $("div").animate({left:100})
                    } else {
                    $("div").animate({left:0})
                  }
        },1000);
      })
    });

  });
</script>
```





















































## 函数, 功能代码段





