# Js 代码实录





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





