# 										JQuery

## 1.概念：

![image-20201124132307403](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201124132307403.png)

## 2.快速入门：

![image-20201124132714207](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201124132714207.png)

```jsp
<script>
        //使用js方式获取名称为div的所有html的元素对象
        var div1 = document.getElementsByTagName("div");
        alert(div1);//可以将其当作数组使用
        //对div中所有的div，让其标签体中的内容都变为"bbb"
        for (var i = 0; i <div1.length ; i++) {
            div1[i].innerHTML="bbb";
            //js-->jq:  $(div[i]).html("bbb");
        }

        //使用jq方式获取名称为div的所有html的元素对象
        var $div2=$("div");
        alert($div2);
        ////对div中所有的div，让其标签体中的内容都变为"ccc"
        $div2.html("ccc");
    	//jq-->js:	$div2[0].innerHTML="ccc";
    
    	 /**
         *	1.JQuery对象在操作时，更加方便
         *  2.JQuery对象方法和js对象方法不通用
         *  3.两者可以相互转化：jq-->js: jq对象[索引] 或 jq对象.get(索引)
         *                     js-->jq: $(js对象)
         */
    </script>
```



## 3.JQuery对象和js对象的相互转化：题二



## 4.选择器：筛选具有相似特征的元素(标签)

### 一：基本语法学习：

1. 事件绑定

2. 入口函数

3. 样式控制

4. ```jsp
   <script>
           //入口函数(dom文档加载完成后执行该函数中的代码)
           $(function () {
               //事件绑定
               $("#div1").click(function () {
                   alert("abc");
               });
           });
           window.onload=function () {
               
           }
       
       	//样式控制
       	$(function(){
               $("#div").css("backgroundColor","red");
           })
           /**
            *  window.onload 和 $(function ())的区别：
            *      1.window.onload：只能定义一次，如果定义多次，后面的会将前面的覆盖掉
            *      2.$(function ())：可以定义多次，且值不覆盖
            */
       </script>
   ```

### 二：分类：

#### 1.基本选择器：

![image-20201124141612493](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201124141612493.png)

例：1.  $("div")		2.  $("#div")		3.  $(".min")

​		4:改变所有<span>元素和id为 two的元素的背景色为红色：$("span，#two").css("backgroundColor","red")；

#### 2.层级选择器：

![image-20201125135340418](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125135340418.png)

解释说明：$("A B")，A下的所有B                                                 $("A>B")，A下的子B

#### 3.属性选择器：

![image-20201125135944874](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125135944874.png)

例：含有属性 title 的 div 元素背景色为红色：$("div [ title ]").css(....)

含有属性 title 值等于 test 的 div 元素背景色为红色:  $("div [ title =' test ' ] ")

含有属性 title 值不等于 test 的 div 元素背景色为红色:  $("div [ title ! =' test ' ] ")

![image-20201125140839956](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125140839956.png)

![image-20201125140808929](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125140808929.png)

#### 4.过滤选择器：

![image-20201125141053200](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125141053200.png)

![image-20201125141612829](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125141612829.png)

![image-20201125141640255](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125141640255.png)

![image-20201125141506841](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125141506841.png)

#### 5.表单过滤选择器：

![image-20201125142044439](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125142044439.png)

![image-20201125143640071](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125143640071.png)

多选下拉框：

![image-20201125143740956](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125143740956.png)

### 三：DOM操作：

#### 1.内容操作

![image-20201125191653387](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125191653387.png)

![image-20201125184157361](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125184157361.png)

#### 2.属性操作：

##### 	1.通用属性操作

![image-20201125191750104](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125191750104.png)

![image-20201125185414067](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125185414067.png)

checked 等属性，必须使用prop，其他可酌情选择

##### 	2.对class属性操作

![image-20201125191826128](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125191826128.png)

![](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125191358335.png)

#### 3.CRUD操作：

![image-20201125192147806](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125192147806.png)

![image-20201125192200662](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125192200662.png)

![image-20201125192246390](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125192246390.png)

```jsp
<script>
    //在“城市”模块后添加“反恐”
	$(function(){
        $("#city").append($("#fk"))
    })
    //在“城市”模块前添加“反恐”
    $(function(){
        $("#city").prepend($("#fk"))
    })
    //在“天津”后插入“反恐”
     $(function(){
        $("#tj").after($("#fk"))
    })
     //在“天津”前插入“反恐”
     $(function(){
        $("#tj").before($("#fk"))
    })
</script>
```

![image-20201125193451297](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125193451297.png)  

#### 案例：

![image-20201125211220633](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125211220633.png)

![image-20201125222726641](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125222726641.png)

![image-20201125223316687](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125223316687.png)

![image-20201125223043134](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201125223043134.png)

# 										JQuery高级

## 1.动画：

![image-20201126132149911](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126132149911.png)

```jsp
<script>
    //默认显示和隐藏方式
    $(function(){
        $("#div").show("[speed]","swing(默认的可不写)/linear(匀速)",[fn]);
})
      $(function(){
        $("#div").hide("[speed]","swing(默认的可不写)/linear(匀速)",[fn]);
})
      $(function(){
        $("#div").toggle("[speed]","swing(默认的可不写)/linear(匀速)",[fn]);
})
    //滑动显示和隐藏方式
     $(function(){
        $("#div").slideDown();
})
      $(function(){
        $("#div").slideUP();
})
      $(function(){
        $("#div").slideToggle();
})
    //淡入淡出显示和隐藏方式
         $(function(){
        $("#div").fadeIn();
})
      $(function(){
        $("#div").fadeOut();
})
      $(function(){
        $("#div").fadeToggle();
})
</script>


```

## 2.遍历：

### js遍历的方式：

![image-20201126140601902](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126140601902.png)

### jq遍历的方式：

#### jq对象.each(callback)

![image-20201126140751769](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126140751769.png)

#### $.each(object,[callback]):

#### for...of :3.0之后

![image-20201126184004182](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126184004182.png)

## 3.事件绑定：

#### 1.jQuery标准的绑定方式：

​		jq对象.事件方法(回调函数)；

![image-20201126201953863](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126201953863.png)

#### 2.on/绑定事件/off解除绑定

​	jq对象.on("事件名称",回调函数)

​	jq对象.off(“事件名称”)，如果off方法不传递任何参数，则将组件上的所有事件全部解绑

![image-20201126204242779](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126204242779.png)

#### 3.事件切换：toggle

![image-20201126205345656](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126205345656.png)

![image-20201126205238363](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201126205238363.png)

# 案例：

### 1.广告的显示和隐藏：

![image-20201127104724992](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201127104724992.png)

### 2.照片的切换和显示：

![image-20201127111142390](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201127111142390.png)

![image-20201127111212310](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201127111212310.png)

![image-20201127111025412](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201127111025412.png)

![image-20201127111054576](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201127111054576.png)

# JQuery插件机制

![image-20201128132603401](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201128132603401.png)

### $.fn.extend(object)

![image-20201128132527133](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201128132527133.png)

![image-20201128132738307](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201128132738307.png)

### $.extend(object)

![image-20201128132952971](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201128132952971.png)

![image-20201128133056089](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201128133056089.png)

# w3school案例：

![image-20201129182929348](D:\Users\jl\Desktop\Typora\JQuery.assets\image-20201129182929348.png)

