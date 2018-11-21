# JavaKnowledge


## ArrayList与LinkedList异同

-  1.是否确保线程安全 ： ArrayList和LinkList都是不同步的，也就是不保证线程安全;
-  2.底层数据结构：  ArrayList底层使用的是Object组;LinkedList底层使用的是双向链表数据结构（注意双向链表和双向循环链表的区别）；
-  3.插入和删除是否收到元素位置的影响：  ArrayList采用数组存储，所以插入和删除的时间复杂度受元素位置影响。  比如：执行'add（E e）'方法的时候
，ArrayList会默认在指定的元素追加到此列表的末尾，这种情况复杂度就是O（1）。但是要在指定位置i插入和删除元素的话'add(int index,E element)'时间
复杂度就为O(n-i)。因为进行上述操作的时候集合中第i和第i个元素之后的（n-i）个元素都要执行向后/向前移一位的操作。<br>
**LinkedList 采用链表存储，所以插入，删除元素时间复杂度不受元素位置的影响，都近似O(1)而数组为近似O(n)。**
-**4.是否支持快速随机访问：** LinkedList不支持高效的随机元素访问，而ArrayList支持。快速随机访问就是通过元素的序号快速获取元素对象（对应于’
'get(int index)'方法）。

-  **5.内存空间占用：** ArrayList的控件浪费主要体现在List列表的结尾会预留一定的容量控件，而LinkedList的控件花费则体现在它的每一个元素都要
消耗比ArrayList更多的空间（因为要存放直接后继和直接前驱以及数据）。

**RandomAccess接口**
```java
public interface RandomAccess{
}
```
RandomAccess接口实际上什么都没有定义。所以RandomAccess接口只不过是一个标识。标识实现这个接口的类具有随机访问功能

在binarySearch（）方法中它要判断传入的List是否RamdomAccess的实例，如果是indexedBinarySearch（）方法，如果不是，那么调用
iteratorBinarySearch()方法
```java
  public static <T>
  int binarySearch(List<? extends Comparable<? super T>> list,T key){
    if(list instanceof RandomAccess || list.size()<BINARYSEARCH_THRESHOLD)
      return Collections.indexedBinarySearch(list,key);
    else
      return Collections.iteratorBinarySearch(list,key);
  }
  
```

