# Java学习

## 6.22

今天是学习尚硅谷的day07的代码。记录自己在学习代码的时候，出现的知识难点。

有余力的话可以学习下cs收藏夹中的 [Java Arrays：专为数组而生的工具类](https://tobebetterjavaer.com/common-tool/arrays.html)学习下。这个Arrays的asList的方法是用来将数组转换为l集合的。视频课中应该有这个问题的学习思路，学习完了多用下。

### asList

这里贴一下`asList`的注释：

```java
Returns a fixed-size list backed by the specified array. (Changes to the returned list "write through" to the array.) This method acts as bridge between array-based and collection-based APIs, in combination with Collection.toArray. The returned list is serializable and implements RandomAccess.
This method also provides a convenient way to create a fixed-size list initialized to contain several elements:
      List<String> stooges = Arrays.asList("Larry", "Moe", "Curly");
  
Params:
a – the array by which the list will be backed
Returns:
a list view of the specified array
```

这个方法实现了将数组转换为固定大小的集合，是数组和集合转换的桥梁接口，和Collection.toArray是双向奔赴的。

### iterator

```java
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        Iterator iterator = coll.iterator();
        while (iterator.hasNext()){
            Object obj = iterator.next();
            if(new Person("Jerry",20).equals(obj)){
                iterator.remove();
                break;
            }
        
        iterator = coll.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }
```

为什么还要重新赋值后遍历：因为刚才的iterator指针指向了coll的末尾，此时的iteratr指向了null。 所以如果想重新遍历coll，必须让iterator指针指向coll的头部
。可以浅显地将迭代器理解为指针的功能。

### Comparator

TreeSet的Comparator实现功能。