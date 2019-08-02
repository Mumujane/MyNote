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



























## 函数, 功能代码段





