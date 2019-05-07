jq中的顶级对象：
 jQuery ----- $

 ```js
$("button").eq(0).click(function () {
  $("#div").css({
    width: "100px",
    height: "100px",
    background: "pink",
    borderRadius: "50%"
  })
})
 ```



jq对象和dom对象互转问题：

 dom转jq

$(dom元素)就成为你jq对象了

```js
var div = document.getElementsByTagName("div")[0];
$(div).click(function(){
    alert("哈哈")
});
```



jq转dom

```js
var div = $("div").eq(0);
div[0].onclick = function () {  
  alert(1);
}
```

$(dom元素)jq对象

$(dom元素)jsdom对象



判断标签是否引用了类样式：
 hasClass("类名")

删除类名：

removeClass("类名")

添加类名：

addClass("类名")

```js
$("button").eq(0).click(function () {
  if ($("body").hasClass("cls")) {
    $("body").removeClass("cls")
  } else {
    $("body").addClass("cls")
  }
})
```



val()  设置属性值



jquery中第一种页面加载的事件：

dom版本变成jq版本

 ```js
$(window).load(function(){
  console.log("页面加载事件1");
})
 ```

jquery中第二种页面加载事件(比load的方式快):

页面中基本的元素加载后就触发

```js
$(document).ready(function(){
  console.log("页面加载事件2")
})
```

jquery中第三种页面加载事件：

 ```js
$(function(){
  console.log("页面加载事件3");
})
 ```



$("p"); //给所有的p标签设置内容

获取值很多都是直接写方法



本身代码没有循环操作，jq中内部帮助我们循环操作的---->隐式迭代



选择器：
 并集选择器：

 ```js
$("div,p,li"); //使用逗号分隔，只要符合条件之一就可以
 ```



交集选择器：

 ```js
$("div.className")
 ```

子代选择器：

 ```js
$("ul>li")  不会获取孙子元素
 ```

后代选择器：

 ```js
$("ul li")  使用空格，代表后代选择器，获取ul下的所有li元素，包括孙子等
 ```



html(); //设置标签内容，==>innerHTML

css(); //设置css样式



层次选择器：

  ```js
$("#div~span").css()
//获取的是div这个父级元素后面的所有的兄弟元素span
$("#div+span").css()
//获取的是div后面直接的兄弟元素，也就是说选择div后面的span，只选择一个，直接兄弟元素
  ```



隔行变色：
 odd:奇数

even:偶数



下拉菜单：

先停止动画再显示隐藏：

 ```js
$(function () {  
  $(".wrap>ul>li").mouseenter(function(){
    //找到子元素ul
    $(this).children("ul").stop().show(600)
  });
  $(".wrap>ul>li").mouseleave(function(){
    $(this).children("ul").stop().hide(300)
  });
})
 ```



高亮显示，链式编程：

```js
$("ul li").mouseenter(function(){
  $(this).css({
    "background":"pink"
  })
}).mouseleave(function(){
  $(this).css({
    "background":""
  })
})
```



:eq(index)--->选择器，选择对应的selector



jquery中几乎把dom中的事件都封装成了一个方法，在jquery中几乎是吧on去掉，然后变成了方法

jquery对象调用dom对象的属性和方法，

jquery对象[0]-----Dom对象

```js
//dom对象转成jq对象
var div = document.getElementsByTagName("div")[0];
$(div).click(function () {
  alert(1);
})

//jq对象转成dom对象
var div = $('div');
div[0].onclick = function () {
  alert(1);
}
```



```js
$('button').click(function () {
  if($(this).text() == '关灯'){
    $('body').css('background','#000');
    $(this).text('开灯');
  }else{
    $('body').css('background','');
    $(this).text('关灯');
  }
});
```



页面加载的不同事件：

```js
$(fucntion(){
})

$(window).load(function(){
  console.log(111);
})

//页面中的基本的元素加载后就触发
$(document).ready(function(){
  console.log(111);
})

```



本身代码没有循环操作，jquery中内部帮助我们循环操作的---->隐式迭代



交集选择器：

```js
<div class="cls">你好</div>
$('div.cls').text('世界');
```



层次选择器：
 $("#div li")



隔行变色：





ul>li  只拿到第一层的li 再往里面的层就拿不到了

ul li 可以拿到子代，子代的子代

```js
$(".wrap>ul>li").mouseenter(function () {
  var ul = $(this).children("ul").stop().show(700);
});

$(".wrap>ul>li").mouseleave(function () {
  var ul = $(this).children("ul").stop().hide(700);
});


children获取子代元素
```

```表单正则验证
$("#btn").click(function () {
var flag = /^[\u4e00-\u9fa5]{2,4}$/.test($("#txt").val());
if(flag){
$("#txt").css("background",'green');
}else{
$("#txt").css("background",'red');
}
})
```



```js
$("#left li").mouseenter(function () {
  //索引值
  var index = $(this).index();
  $("#center li").hide();
  $("#center li").eq(index).show();
});

$("#right li").mouseenter(function () {
  var index = $(this).index()+9;
  $("#center li").hide();
  $("#center li").eq(index).show();
});
```



淘宝精品展示：

```js
$("#left li").mouseenter(function () {
  //索引值
  var index = $(this).index();
  $("#center li").hide();
  $("#center li").eq(index).show();
});
$("#right li").mouseenter(function () {
  var index = $(this).index()+9;
  $("#center li").hide();
  $("#center li").eq(index).show();
});
```



css的几种用法：
 css("键","值");

css({"width":"200px","height":"200px...});

```js
$("#btn").click(function () {
  $("#div").css({ "width": "200px", "height": "200px", "border": "1px solid red", "background": "orange" })
})
```





如何写链式编程：
 链式编程：对象不停的调用方法

对象.方法().方法().方法().方法();

对象调用方法，如果返回值还是当前这个对象，那么就可以继续的调用方法

经验：在jquery中，一般情况，对象调用的方法，这个方法的意思是设置的意思，那么返回的几乎都是当前对象，就可以继续链式编程

 添加样式的方式：
 addClass("cls1 cls2") 可以有两个类样式也可以有多个

移除类样式：

 removeClass("cls cls2") 可以有两个类样式也可以有多个

hasClass("类名") ； 判断有没有这个类样式

```js
//开关灯的实现
$("#btn").click(function () {
  if ($("body").hasClass("cls")) {
    $("body").removeClass("cls")
    $("#btn").val("关灯");
  } else {
    $("body").addClass("cls")
    $("#btn").val("开灯");
  }
})
```



toggleClass("cls"); //类样式的切换



jquery筛选选择器：

 children(selector) //子类选择器相当于$("ul>li")

find(selector)  //相当于$("ul li") , 后代选择器

siblings(selector) //查找兄弟节点，不包括自己本身

parent() // 查找父亲

eq(index) //index从0开始

next()  找下一个兄弟

prev()  找上一个兄弟

```js
$("#btn").click(function(){
  //获取上一个兄弟元素
  var res = $("#three").prev().text();
  console.log(res)
  //获取下一个兄弟元素
  var res = $("#three").next().text();
  console.log(res);
})
```



nextAll(select); //获取后面的所有兄弟节点

prevAll(select); //获取前面的所有兄弟节点



断链解决：

 .end() //修复断链，恢复断链之前的状态

```js
$("ul>li").mouseenter(function () {
  $(this).css("background", "pink").siblings().css("backgroung", "");
}).mouseleave(function () {
  $(this).parent().children("li").css("background", "");
}).click(function () {
  //断链之后.end()重新恢复
  $(this).prevAll().css("background","green").end().nextAll().css("background","blue");
})
```



tab栏的切换：

 ```js
$(".tab>li").mouseenter(function () {
$(this).addClass("active").siblings().removeClass("active");
var index  = $(this).index();
$(".products>div").removeClass("selected").eq(index).addClass("selected")
})
 ```



动画相关：

 show(time,callback)

 hide(time,callback)

callback : 动画结束之后执行callback





动画相关方法：
 slideDown(); //向下滑   滑出

slideUp();  //向上滑   滑入

```js
$("#show").click(function(){
  $("#div").slideUp(1000);
})
$("#hide").click(function(){
  $("#div").slideDown(1000);
})
$("#toggle").click(function () {  
  $("#div").slideToggle(1000);
})
```

slideToggle(time); //切换动画（切换滑入滑出）



fadeIn(1000)

fadeOut(1000)

fadetoggle(1000) //淡入淡出切换 

```js
$("#fadeIn").click(function () {  
  $("#div").fadeIn(1000); //淡入
})
$("#fadeOut").click(function () {  
  $("#div").fadeOut(1000); //淡出
})
```



fadeTo(time,透明度的值);

```js
$("#fadeTo").click(function () {  
  $("#div").fadeTo(1000,0.2);
})
```



slow：慢

fast : 快

nomal : 正常的



动画效果的实现：

.last(); //最后一个

递归：

  ```js
$("div img").last().hide(1000,function f1(){
  $(this).prev().hide(1000,f1)
})
  ```

arguments.callee  少用,不推荐使用

```js

$("#btn1").click(function () {  
  //递归思想
  // 第一个按钮隐藏
  $("div img").last().hide(1000,function f1(){
    $(this).prev().hide(1000,f1)
  })
})
$("#btn2").click(function () {  
  //递归思想
  // 第一个按钮显示
  //第二个按钮显示
  $("div img").first().show(1000,function f2() { 
    $(this).next().show(1000,f2);
  })
  //第二个按钮显示
})
```



animate方法：

 ```js
$("img").animate({"left":"300px"},1000,function () {  
  $(this).animate({"top":"500px"},1000)
})
 ```



元素的创建及添加：

```js
$(select).append($("<a></a>"));


$("button").click(function(){
  $("#div").html("");
  $("#div").append("<a href='#'>你好</a>")
})
```



创建一个子元素直接加到父级元素 ：

```js
//主动添加
$("button").click(function () {  
  $("<a href='#' style='text-decoration: none;'>你好</a>").appendTo($("#div"))
})
```



点击按钮创建多个p标签：

 for循环操作



动态创建列表 ： 

内置对象：js内置的对象(Array,Object,Date,Regexp)

浏览器对象：window

自定义对象:自己定义的构造函数创建的对象

DOM对象：通过DOM方式获取的对象

jq对象：通过jq方式获取的对象

```js
var arr = ['1','2','3','4','5'];
$("button").click(function () {  
  var obj = $("<ul></ul>").appendTo($("#div"));
  //创建li
  for(var i = 0; i<arr.length; i++){
    $("<li>"+arr[i]+"</li>").appendTo(obj);
  }
})
```



剪切的效果：

```js
$("button").click(function () {
  $("#div").append($("#divp>p"));
})
```



 克隆效果：

 ```js
$("button").click(function(){
  $("#div").append($("#divp>p").clone());
})
 ```



元素创建的不同的方式 :

被动：

prepend($("dom元素")) ; //将元素插入到最前面

主动：

prependTo($(select))

```js
$("button").click(function () {  
       $("#div").prepend("<p>你好世界！</p>")
  $("<p>哈哈哈</p>").prependTo($("#div"));
   $("#div").after($("<p>下一个兄弟元素</p>"))
    $("#div").before($("<p>上一个兄弟元素</p>"))
  
})
```



 after("dom"); //把元素添加到div的后面的位置，是div的下一个的兄弟元素

before("dom"); //把元素添加到div的前面的位置，是div的上一个兄弟元素



元素移除：
 从父级元素中移除子元素：

 ```js
$("button").click(function () {  
  $("#div").html("");
}) 
 ```



清空div

$("div").empty() ;// 清空

移除元素：

 $("div").remove(); //自杀，想要干掉谁，直接找到这个元素，调用这个方法就ok了。

```js
$("button").click(function () {  
  //清空父元素中的子元素方法
  // $("#div").html("");
  // $("#div").empty();
  
  //清空自己元素
  //自杀
  $("#div").remove();
})
```



selected : 

```js
$("#toAllRight").click(function () {  
  $("#se1>option").appendTo($("#se2"));
})
$("#toAllLeft").click(function () {  
  $("#se2>option").appendTo($("#se1"));
})
$("#toRight").click(function () {  
  $("#se1>option:selected").appendTo($("#se2"));
})
$("#toLeft").click(function () {  
  $("#se2>option:selected").appendTo($("#se1"));
})
```

 

元素的value属性设置 ：

选中select下面的option为5的option

$("select option").val(5);

checked = true; 选中input的radio

自定义属性：

 attr("键","值");//设置值

attr("键"); //获取值

checked-----> attr("checked")---->结果:checked

attr对单选框或者是复选框是否选中问题，是有问题的，主要是针对自定义属性的

操作选中是有prop这个方法



attr('k','v'); //设置属性

prop("k","v");

```js
//点击按钮
$("#btn").click(function () {
  $("#ck8").prop("checked", true);
});
```

prop();一个值的时候是获取



选中/不选中：

```js
$("button").click(function () {  
  console.log($("#check").prop("checked"));
  if($("#check").prop("checked")){
    $("#check").prop("checked",false);
  }else{
    $("#check").prop("checked",true);
  }
})
```



获取css的宽和高：
 $("width"); //获取css的宽和高

 ```js
$("button").click(function () {  
  //获取css的宽
  var width = $("#div").css("width");
  //获取css的高
  var height = $("#div").css("height");
  $("#div").css("width",parseInt(width)*2);
  $("#div").css("height",parseInt(height)*2);
})
 ```



jq中css方法没有px自己会加上px



//这两个方法可以设置元素的宽和高

width();

height();



操作元素的left和top : 

offset(); //返回的是一个对象，margin-top,top 合在一起的值，直接.就等获取到值

可以获取，可以设置：

 ```js
$("#btn").click(function () {
  //获取的是一个对象：
  //{top: 100, left: 100}
  var t = $("#div").offset().top;
  var l = $("#div").offset().left;
  // $("#div").css("top",$("#div").offset().top*2);
  // $("#div").css("left",$("#div").offset().left*2);
  //设置
  $("#div").offset({"left":l*2,"top":t*2});
})
 ```



//可以设置也可以设置

 .width()是元素的宽

.height()元素的高

.offset() --->获取的是对象，可以设置，也可以获取



元素卷曲的设置：

scroll系列 ： 卷曲的距离

```js
$("button").click(function () {
  //向左卷曲的距离,数字类型
  var offset = $("#div").scrollLeft();
  //向上卷曲的距离，数字类型
  var offsetT = $("#div").scrollTop();
  console.log(offset);
  console.log(offsetT);
})
```



onscorll事件：

 ```js
$("#div").scroll(function(){
  console.log($("#div").scrollLeft());
  console.log($("#div").scrollTop());
})
 ```



position默认就是： $(".nav").css("position","static");



 jq绑定事件的方式：

 bind绑定事件的方式：

 ```js
$("button").bind("click",function () {  
  alert("点击");
})
$("button").bind("mouseenter",function () {  
  $(this).css("background","pink");
})
$("button").bind("mouseleave",function () {  
  $(this).css("background","green");
})
 ```



注意问题：

 多个相同事件：

 ```js
$("button").click(function () {
  alert(1)
}).click(function () {
  alert(2)
}).click(function () {
  alert(3);
})
 ```

方式2：

 ```js
$("button").bind("click",function () {  
  alert(1);
}).bind("click",function () {  
  alert(2);
})
 ```



键值对的方式写bind:
 bind这个方法绑定多个相同事件的时候，如果使用的是键值对的方法，只能执行最后一个

 ```js
$("button").bind({
  "click": function () {
    console.log(1)
  }, "click": function () {
    console.log('2');
  }
})
 ```

bind方法内部是调用的另一个方法绑定的事件



dalegate方式绑定事件：

dalegate : 代理 ， 委托

 子级元素委托父级元素绑定事件

 ```js
$("button").click(function () {  
  $("div").delegate("p","click",function () {
    alert('点击了');
  })
})
 ```



绑定事件的三种形式：
对象.on

对象.bind

对象.delegate("子级元素","事件名字",函数)---->

事件委托：

```js
$("button").click(function () {  
  $("div").delegate("p","click",function () {
    alert('点击了');
  })
})
```



click只能为页面存在的元素绑定事件

事件委托解决

on方式绑定事件：

 为子元素绑定事件：

 $("#btn").on("click","p",callback);

on和delegate作用是一样的，参数的顺序是不一样的



事件的总结：

对象.事件名

对象.bind("事件名",callback)

上面两种只能有页面存在的绑定事件



下面的两种方式可以未存在的绑定事件，后添加的元素也有事件

对象.delegate(select,"事件名字",callback)

对象.on("事件名字",select,callback) 

以后直接使用on，dalegate中使用的就是on



解绑事件：

 bind("click",callback)

unbind("click")

click的方式也可以使用unbind方式解绑事件

 unbind();没有参数的时候，元素所有的事件解绑

 同时解绑多个事件，中间用空格隔开即可：
unbind("mouseenter mouseleave")



delegate绑定事件对应的方式解绑方式：

 

undelegate : 解绑delegate

移除了p的所有的事件 

jq中阻止事件冒泡：

 return false;即可

 

trigger : 

$("selelctor").trigger("focus"); //触发了事件

 



$.fn.ChangeColor

$.fn 必须以这个开头

ChangeColor表示方法名字

 



























































 

 














































































































































































































































































