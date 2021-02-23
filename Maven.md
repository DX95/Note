# 											Maven

mvn clean,把项目的编译信息干掉

mvn compile,把src里的main/Java文件编译，.class文件放在target目录中

mvn test，把src下的test和main测试代码编译成.class，放在target目录中

mvn package ，编译，测试并打包，war包

mvn install,安装。编译，测试，打包，安装到本地仓库

![image-20201210203409411](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201210203409411.png)

![image-20201210215803601](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210215803601.png)

修改本地仓库的地址：

![image-20201210222450186](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210222450186.png)

idea配置：

![image-20201210221822928](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210221822928.png)

![image-20201210221747001](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210221747001.png)

使用maven创建Java工程：（不使用更简单）

![image-20201210223136195](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210223136195.png)

使用maven创建Web工程:

![image-20201210224033389](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210224033389.png)

![image-20201210224318643](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210224318643.png)

避免本地tomcat中的servlet和jsp的jar与maven库中的包冲突，需加上属性

![image-20201210231924285](D:\Users\jl\Desktop\Typora\Maven.assets\image-20201210231924285.png)