## 利用std::map标记run number依赖的类

通常有一些修正是对不同的run number进行的，
这时候如果利用数组装入run number是非常不优雅的，尤其当某些run number的数据存在问题需要弃用时，这种方式甚至是不安全的。

利用 Stl 库中的 map/unordered_map 容器，可以直接产生从run number到该类的映射。这种映射以红黑树/哈希表实现，效率很高。

通常以run number作为key，而某一Histogram或者Profile作为value，例如：

```C++
   //定义：
   std::unordered_map mapRunClass = new std::unordered_map<int, SomeClass*>;
   mapRunClass -> insert(std::pair<int,TProfile*>(runNumList[i].Atoi(),someclass[i]));
   //访问时可：
   mapRunClass -> at(fRunNum) -> SomeClassFunc();
```
