# Hash_map
## 数据结构
    散列表（哈希表）：散列表是一个根据key来访问value的存储结构，HashMap中实现的散列表是一个链表类型的数组，数组+链表，用来存储key-value数据对。
    将key映射到数组的某个下标，存取的时候通过key获取到下标（index）然后通过下标直接存取。
    当数据发生碰撞时由链表解决
    ![哈希表]https://upload-images.jianshu.io/upload_images/16566539-672ab962ae6dc500.png?imageMogr2/auto-orient/strip|imageView2/2/format/webp
## 特点
    插入，查找都较为迅速
    空间换时间；建立较为费时，查找时间复杂度可视为常数

## unordered_map 类的定义
```c++
template<class Key,
         class Ty,
         class Hash = std::hash<Key>,
         class Pred = std::equal_to<Key>,
         class Alloc = std::allocator<std::pair<const Key,Ty>>
         >
class unorder_map;
```
|参数|描述|
|:-:|:-:|
| Key | 密钥值 |
| Ty | 映射类 |
| Hash | 哈希函数对象类 |
| Pred | 相等比较函数对象类 |
| Alloc | allocator类 |

## 相关函数使用（unordered_map）
### 头文件
```cpp
#include<unordered_map>
```
### 遍历访问key与Ty值(通过迭代器it)
```cpp
unordered_map<Key,T>::iterator it
(*it).first;    //the key value
(*it).second;        //the mapped value
for(unordered_map<Key,T>::iterator iter=mp.begin();iter!=mp.end;iter++)
```
### 成员函数
|迭代器| |
|-|-|
|begin| 返回指向容器起始位置(iterator) |
|end| 返回指向容器末尾位置 |
|cbegin|返回指向容器起始位置的常迭代器(const_iterator) |
|cend|返回指向容器末尾位置的常迭代器 |

|Capacity||
|-|-|
|size|有效元素个数|
|max_size|最大元素个数|
|empty|是否为空|

|操作||
|-|-|
|find|通过给定主键查找元素|
|count|返回与指定key值匹配的成员数量|
|equal_range|返回值匹配指定key值的成员|

|修改||
|-|-|
|insert|插入元素|
|erase|删除元素|
|emplace|构造并插入|
|clear|清空内容|