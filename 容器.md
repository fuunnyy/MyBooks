####NSArray / NSSet / NSDictory 三者的异同点
- NSArray 是一个有序对象的一个集合。相当于一个队列存储，可以有重复的数进去。
- NSSet   比较典型的一个HASH表(集合)算法，是一个类似于集合的容器，利用散列算法去找特定的键值，效率比较高。
- NSDictory 是一个键值映射，key/value取值一一对应。

##Set的具体使用,整体上来看Set的用法与array的用法类似
####NSSet用法
 - [NSSet setWithSet:(NSSet *)set]; 用另外一个set对象构造
[NSSet setWithArray:(NSArray *)array];用数组构造
 - [NSSet setWithObjects:...]:创建集合对象，并且初始化集合中的数值，结尾必需使用nil标志。
 - [set count] ; 得到这个集合对象的长度。
 - [set containsObject:...]: 判断这个集合中是否存在传入的对象，返回Bool值。
 - [set objectEnumerator]: 将集合放入迭代器。
 - [enumerator nextObject]:得到迭代器中的下一个节点数据，使用while遍历这个迭代器，方可遍历集合对象中的对象。
 - [set isEqualToSet:objset]:判断两个集合是否完全相等,返回Bool值。
 - [set isSubsetOfSet:objset]:判断集合中的所有数据是否都相等与objeset集合中,返回Bool值。
 - [set allObjects];

####NSMutaleSet用法
 - [NSMutableSet setWithCapacity:6]:创建可变集合对象，并且初始化长度为6。
 - [set addObject: obj] : 向集合中动态的添加对象。
 - [set removeObject:obj]:删除集合中的一个对象。
 - [set removeAllObjects]:删除集合中的所有对象。
 - [set unionSet:obj]:向集合中添加一个obj集合的所有数据。
 - [set minusSet:obj]:向集合中删除一个obj集合的所有数据。
 - [set intersectSet]:向集合中删除一个不包含obj集合的所有数据。


