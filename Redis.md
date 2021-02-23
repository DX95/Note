# Redis

## 一：简介

redis是一款高性能的NOSQL系列的非关系型数据库

![image-20201208142438934](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201208142438934.png)

![](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201208142655861.png)

![image-20201208142519521](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201208142519521.png)

## 二.Redis的数据结构

![image-20201208142151888](C:\Users\jl\AppData\Roaming\Typora\typora-user-images\image-20201208142151888.png)

## 三.命令操作

![image-20201208175111222](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201208175111222.png)

![image-20201208223347205](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201208223347205.png)

![image-20201208223425684](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201208223425684.png)

## 四.持久化

### RDB

![image-20201208223526417](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201208223526417.png)

### AOF

![image-20201208223550942](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201208223550942.png)

## 五.Jedis操作

![image-20201208223737238](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201208223737238.png)

### 字符串：string

set()    get()     setex()

![image-20201208223919608](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201208223919608.png)

### 哈希类型：hash

hset()	hget()	hgetAll()	遍历	值会覆盖

![image-20201209181220933](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201209181220933.png)

![image-20201209181330878](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201209181330878.png)

### 列表类型：list

lpush()/rpush()	lpop()/rpop()	lrange("name",star,end)		值允许重复

![image-20201209181722330](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201209181722330.png)

![image-20201209182802798](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201209182802798.png)

### 集合类型：set

sadd()	smembers()	不允许重复元素

![image-20201209183344282](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201209183344282.png)

### 有序集合类型：sortedset

zadd()	zrange()	不允许重复元素	可排序

![image-20201209184630297](D:\Users\jl\Desktop\Typora\Redis.assets\image-20201209184630297.png)

获取key及值：zrangeWithScores("Category", 0, -1);

删除： zremrangebyrank Category 0 -1 ；

## 六：案例

```java
public class CategoryServiceImp implements CategoryService {
    private CategoryDao dao=new CategoryDaoImp();
    @Override
    public List<Category> finAll() {
        Jedis jedis = JedisUtil.getJedis();
        Set<String> category = jedis.zrange("Category", 0, -1);
        List<Category> list=null;
        if (category==null||category.size()==0){
            System.out.println("从数据库查询");
            list=dao.findAll();
            for (int i = 0; i <list.size() ; i++) {
                jedis.zadd("Category",list.get(i).getCid(),list.get(i).getCname());
            }
        }else {
            System.out.println("从Radis查寻");
            list=new ArrayList<Category>();
            for (String name : category) {
                Category c=new Category();
                c.setCname(name);
                list.add(c);
            }
        }
        return list;
    }
}
```

