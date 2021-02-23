# spring

## 一：IOC的概念和作用：

![image-20210118165133429](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210118165133429.png)

### 使用xml文件配置bean：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="Factorytest" class="zbvc.factory.Factorytest"></bean>
    <!-- collaborators and configuration for this bean go here -->
    <!-- 纯注解时这里就相当于@Configuration  -->
</beans>
```

```xml
<!-- springIOC所需依赖  -->
<dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>5.0.2.RELEASE</version>
        </dependency>
```

```java
public static void main(String[] args) {
        //获取核心容器对象
        ApplicationContext a=new ClassPathXmlApplicationContext("bean.xml");
        //获取bean对象
        Factorytest test= (Factorytest) a.getBean("Factorytest");
        System.out.println(test);
        test.connection();
    }
```

![image-20210118173019359](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210118173019359.png)

![image-20210118174819924](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210118174819924.png)

### 使用工厂创建对象的多种方式：

类中的方法。类中的静态方法

![image-20210118200347620](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210118200347620.png)

### bean的作用范围调整：

![image-20210119104010730](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119104010730.png)

#### global-session:

![image-20210119104524954](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119104524954.png)

### bean的生命周期：

#### 单例对象：

![image-20210119105007794](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119105007794.png)

![image-20210119104925954](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119104925954.png)

#### 多例对象：

![image-20210119105326506](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119105326506.png)

## spring中的依赖注入：

![image-20210119111510950](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119111510950.png)

#### 构造函数注入：

![image-20210119113534257](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119113534257.png)

![image-20210119113444699](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119113444699.png)

#### set方式注入：

![image-20210119121608568](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119121608568.png)

#### 注入集合数据：

![image-20210119122638566](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119122638566.png)

![image-20210120204046307](spring/image-20210120204046307.png)

拓展的注入方式：

![image-20210120205510589](spring/image-20210120205510589.png)

## 二：使用注解方式实现IOC:

### 用于创建对象的：

Component:普通的

Controller：表现层

Service：业务层

Repository：持久层

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
    <!--使用xml配置的方式-->
    <!--<bean id="Factorytest" class="zbvc.factory.Factorytest"></bean>-->
    <!--使用注解配置-->
    <context:component-scan base-package="zbvc"></context:component-scan>
    <!-- collaborators and configuration for this bean go here -->
    <!-- 纯注解时这里就相当于@Configuration  -->
</beans>
```

```java
@Component(value="name")//或者省略value
```

![image-20210119134559663](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119134559663.png)

### 用于注入数据的：

Autowired:自动按照类型注入

Qualifier:按照类的基础上再按照名称注入，不可单独使用

Resource:直接按照bean的id注入，可以独立使用

以上三种只能注入其他bean类型

value;用于注入基本类型和string类型

![image-20210119153701070](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119153701070.png)

![image-20210119154314108](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119154314108.png)

![image-20210119154213532](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119154213532.png)

![image-20210120145247401](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120145247401.png)

### 该变作用范围和声明周期：

![image-20210119162056967](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210119162056967.png)

### 使用注解代替xml：

Configuration:指定当前类是一个配置类

componentScan:指定创建容器时要扫描的包

Bean:把当前方法的返回值作为bean对象存入spring的ioc容器中

Import:导入其他的配置类

使用xml的方式:

![image-20210120144436074](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120144436074.png)

![image-20210120123540632](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120123540632.png)

![image-20210120125238445](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120125238445.png)

![image-20210120134934585](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120134934585.png)

![image-20210120135015866](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120135015866.png)

三：spring整合junit

为什么整合？

![image-20210120154651294](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120154651294.png)

![image-20210120154421008](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120154421008.png)

![image-20210120154516083](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120154516083.png)

![image-20210120154536226](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120154536226.png)

![image-20210120154613547](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20210120154613547.png)