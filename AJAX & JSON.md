# 										AJAX

## 一：概念：

![image-20201128155203967](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201128155203967.png)

![image-20201128164240475](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201128164240475.png)

## js方式：

```jsp
<script>(了解)
function fn() {
            //发送异步请求
            //1.创建核心对象
            var xmlhttp;
            if (window.XMLHttpRequest)
            {//code for IE7+,Firefox,Chrome,Opera,Safari
                xmlhttp=new XMLHttpRequest();
            }else
            {//code for IE6,IE5
                xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
            }

            //2.建立连接
            /**
                参数：
                    1.请求方式:GET.POST
                        *get方式，请求参数在URL后面拼接。send方法为空参
                        *post方式，请求参数在send方法中定义
             *      2.请求的URL；
             *      3.同步或异步请求：true(异步)或false(同步)
             *  */
            xmlhttp.open("GET","servlet?username=tom",true);

            //3.发送请求
            xmlhttp.send();
            //4.接受并处理来自服务器的响应结果
			......
        }
    </script>
```

## jQuery方式：

### 1: $.ajax()

dataType可取值：

![image-20201203170717133](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203170717133.png)

![image-20201203170617232](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203170617232.png)

### 2.$.get()

![image-20201203171202980](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203171202980.png)

![image-20201203171125493](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203171125493.png)

### 3.$.post()

# JSON

## 一.概念：

![image-20201203171447325](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203171447325.png)

## 2.语法：

### 1.基本规则：

![image-20201203171808231](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203171808231.png)

### 2.获取数据

![image-20201203174957866](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203174957866.png)

#### 几种定义格式及值的获取：

![image-20201203174212451](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203174212451.png)

![image-20201203174122308](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203174122308.png)

![image-20201203174254562](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203174254562.png)

#### 遍历获取：

遍历获取基本格式：

![image-20201203174545274](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203174545274.png)

嵌套格式：{ }-->[ { } ]

![image-20201203175332781](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203175332781.png)

遍历获取数组格式：[ {},{},{}]

![image-20201203174721332](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203174721332.png)

## 3.java队象和json数据的相互转换：

### 1.json-->java(了解) 

![image-20201203193711919](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203193711919.png)

![image-20201203193552168](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203193552168.png)

### 2.java-->json

![image-20201203193428943](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203193428943.png)

![image-20201203191710801](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203191710801.png)

![image-20201203191824870](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203191824870.png)

![image-20201203192935012](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203192935012.png)

![image-20201203193227266](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203193227266.png)

![image-20201203193342809](D:\Users\jl\Desktop\Typora\AJAX.assets\image-20201203193342809.png)