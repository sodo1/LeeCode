# Vector

## 概念：
    封装了动态大小数组的顺序容器（Sequence Container），可简单认为是是一个能够存放任意类型的动态数组

## 特性
    1.顺序性：容器中元素按线性顺序排列，可通过位置访问对应元素。
    2.动态性：支持随机访问；可在序列末尾快速增删元素。
    3.感知性：容器使用一个内存分配器对象来动态地处理它的存储需求。

## 基本实现：
### 1.构造函数
  * vector():创建新的vector
  * vector(int nSize):创建指定大小为nSize的Vector
  * vector(int nSize,const t& t):创建一个vector，元素个数为nSize,且值均为t
  * vector(const vector&):复制构造函数
  * vector(begin,end):复制[begin,end)区间内另一个数组的元素到vector中
### 2.增
  * void push_back(const T& x):向量尾部增加x
  * iterator insert(iterator it,const T& x):向量中迭代器指向元素前增加一元素
  * iterator insert(iterator it,const_iterator first,const_iterator last):向量中迭代器指向元素前插入另一同类型向量[first,last)间数据
### 3.删
  * iterator erase(iterator it):删除向量中迭代器指向元素
  * iterator erase(iterator first,iterator last):删除[first,last)间元素
  * void pop_back():删除最后一个元素
  * void clear():清空向量中元素
### 4.遍历
  * reference at(int pos):返回pos位置元素的引用
  * reference front():返回首元素的引用
  * reference back():返回尾元素的引用
  * iterator begin():返回向量头指针，指向第一个元素
  * iterator end():返回向量尾指针，指向向量最后一个元素的下一个位置
  * reverse_iterator rbegin():反向迭代器，指向最后一个元素
  * reverse_iterator rend():反向迭代器，指向第一个元素之前的位置 
### 5.判断
  * bool empty() cosnt:判空
### 6.大小函数
  * int size() const:返回向量中元素个数
  * int capacity() const:返回向量所能容纳最大元素值
  * int max_size() cosnt:返回最大可允许的vector元素数量
### 7.其他函数
  * void swap(vector&):交换两同类型向量的数据
  * void assign(int n,const T& x):设置第n个元素值为x
  * void assign(const_iterator first,const_iterator last):向量中[first,last)中元素设置成当前元素

## 基本用法
### 调用库
```
#include<vector>
using namespace std;
```
### 增删 push_back & pop_back() & clear()
```c++
#include<string.h>
#include<vector>
#include<iostream>
using namespace std;

int main()
{
    vector<int>obj;//int型向量存储容器obj
//将0~9依次插入至数组末尾    
    for(int i=0;i<10;i++){
        obj.push_back(i);
        cout<<obj[i]<<",";      // 0，1，2，3，4，5，6，7，8，9，
    }
//去掉后五个
    for(int i=0;i<5;i++){
        obj.pop_back();
    }
    for(int i=0;i<obj.size();i++){
        cout<<obj[i]<<","       //0，1，2，3，4，
    }

    obj.clear();
    for(int i=0;i<obj.size();i++){
        cout<<obj[i]<<","       //NULL
    }

    return 0;
}

```
### 排序 sort() & reverse()
```cpp
#include<string.h>
#include<vector>
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
    vector<int>obj;
    obj.push_back(1);
    obj.push_back(3);
    ovj.push_back(0);

    sort(obj.begin(),obj.end());        //从小到大排序
    reverse(obj.begin,obj.end());       //从大到小

    return 0;
}
```
### 访问 数组访问 & 迭代器访问
```cpp
#include<string.h>
#include<vector>
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
    vector<int>obj;
    for(int i=0;i<10;i++){
        obj.push_back(i);
    }
//利用数组访问
    for(int i=0;i<10;i++){     
        cout<<obj[i]<<",";
    }
//声明迭代器，访问iterator容器；作用：遍历或指向vector容器内元素
    vector<int>::iterator it;       
    for(it=obj.begin;it!=obj.end;it++){
        cout<<*it<<" ";
    }
}
```
### 二位数组定义
```cpp
#include<string.h>
#include<vector>
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
    int N=5,M=6;
    vector<vector<int>>obj(N);      //5行
    for(int i=0;i<obj.size();i++){
        obj[i].resize(M);       //6列
    }
    //输出
    for(int i=0;i<obj.size();i++){
        for(int j=0;j<obj[i].size;j++){
            cout<<obj[i][j]<<" "; 
        }
        cout<<"\n";
    }
}
```

```cpp
#include<string.h>
#include<vector>
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
    int N=5,M=6;
    vector<vector<int>>obj(N,vector<int>(M));      //5行6列二维动态数组
   
    //输出
    for(int i=0;i<obj.size();i++){
        for(int j=0;j<obj[i].size;j++){
            cout<<obj[i][j]<<" "; 
        }
        cout<<"\n";
    }
}
```