---
title: 'c++读写文件与容器操作'
date: 2022-05-23 10:06:51
tags: 
    - c
categories: 算法
---

## 读写文件

```c_cpp
#include<stdio.h>
#include<time.h>
#include<stdlib.h>
int main(){
	srand(time(0));
	freopen("1.in","r",stdin);
	int a[5];
	for(int i=0;i<5;i++){
		scanf("%d",&a[i]);
	}
	freopen("1.out","w",stdout);
	for(int i=0;i<5;i++){
		printf("%d\n",a[i]);
	}
	return 0;
} 
```

## algorithm头文件

```c_cpp
#include<iostream>
#include<algorithm>
using namespace std;
int main(){
	int a=2,b=4;
	cout<<max(2,3)<<endl;
	cout<<min(2,3)<<endl;
	cout<<a<<b<<endl;
	swap(a,b);
	cout<<a<<b<<endl;
	return 0;
} 
```

## 引用

```c_cpp
#include<iostream>
#include<algorithm>
using namespace std;
int main(){
	int a=10;
	int &b=a;
	cout<<b;
	return 0;
} 
```

![](file://C:\Personal\Desktop\c++读写文件，容器操作\57566894e9a8d95f5e8a57fd2b31e4f5.png)

## 引用的使用（交换变量）

```c_cpp

#include<iostream>
#include<algorithm>
using namespace std;

void my_swap(int &a,int &b){
	int temp=a;
	a=b;
	b=temp;
}

int main(){
	int a=10;
	int b=12;
	cout<<a<<b<<endl;
	my_swap(a,b);
	cout<<a<<b<<endl;
	return 0;
} 
```

## 异或运算

```c_cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main(){
	//异或就是先取反后或运算 
	int one=1;
	int zero=0;
	int res1=one^one;
	int res2=one^zero;
	int res3=zero^one;
	int res4=zero^zero;
	cout<<res1<<" "<<res2<<" "<<res3<<" "<<res4;
	return 0;
} 
```

## c++中的string基本运算

```c_cpp
#include<iostream>
#include<algorithm>
#include<string>
using namespace std;

int main(){
	string s="asdsad";
	s.insert(1,"super boy");
	cout<<s<<endl;
	s.erase(1,9);
	cout<<s<<endl;
	string s2=s.substr(1,10);
	cout<<s2.size()<<endl;
	//找到返回索引，找不到返回-1 
	int pos=s.find("sadasd");
	cout<<pos<<endl;
	string s3="11231231";
	cout<<s3.find('1',3);//输出4 
	cout<<s3.find('1',6);//输出7 
	return 0;
} 
```

## c++容器

#### vector

动态更新数组内存，底层实现是数组，可以按索引顺序访问，如果是插入和删除则需要内存区的拷贝

**int初始化方式**


| 代码                   | 解释                                   |
| ------------------------ | ---------------------------------------- |
| vector<int> a;         | 初始化一个名为a装有int值的vector容器   |
| vector<int> b(a);      | 用a定义b(地址不一样，完全是两个vector) |
| vector<int> a(100);    | 定义一个a，有100个数字0                |
| vector<int> a(100,12); | 定义一个a，有100个数字6                |

**string初始化方式**


| vector<string> s;                    | 初始化一个名为s装有string值的vector容器 |
| -------------------------------------- | ----------------------------------------- |
| vector<string> s(s.begin(),s.end()); | 用s1定义s(地址不一样，完全是两个vector) |
| vector<string> s(s1);                | 同上                                    |
| vector<string> s(100,"null")；       | 初始化100个null                         |

**妙用**


| struct  point{int x,y;}			vector<point> p; | p用来存放坐标 |
| -------------------------------------------- | --------------- |
| vector<int> a[MAXN]                        | 定义多维数组  |

```c_cpp
#include<bits/stdc++.h>
using namespace std;
struct point{
	int x,y;
};

int main(){
	vector<int> a;
	vector<int> b(a);
	cout<<&a<<" "<<&b<<endl; 
	vector<string> s1;
	vector<string> s(s1);
	vector<string> s2(s1.begin(),s1.end());
	cout<<&s<<" "<<&s1<<" "<<&s2<<endl; 
	vector<point> p();
	cout<<"vector的各种操作"<<endl;
	return 0;
}
```

![](file://C:\Personal\Desktop\c++读写文件，容器操作\1a530934271b2c6784a1a0115a7cf661.png)

**练习**

初始化数值方式1：先定义空间大小，后循环访问

```c_cpp
#include<bits/stdc++.h>
using namespace std;

int main(){
	vector<int> a(100);
	cout<<"vector的各种操作"<<endl;

	for(int i=0;i<10;i++){
		a[i]=i;
		cout<<a[i]<<endl;
	}

	return 0;
}
```

初始化数值方式2：直接初始化，不定义空间，然后push_back();

```c_cpp
#include<bits/stdc++.h>
using namespace std;

int main(){
	vector<int> a;
	for(int i=0;i<10;i++){
		a.push_back(i);
		cout<<a[i]<<endl;
	}
	return 0;
}
```

**汇总：**

```c_cpp
#include<bits/stdc++.h>
using namespace std;
void print(vector<int>& a){
	if(!a.empty()){
		for(int i=0;i<a.size();i++){
			cout<<a[i]<<" ";
		}
		cout<<endl;
	}else{
		cout<<"您的vector为空!!\n"; 
	}
}

int main(){
	vector<int> a;
	cout<<a.empty()<<endl; 
	for(int i=0;i<10;i++){
		a.push_back(i);
	}
	print(a);
	a.insert(a.begin(),123);
	print(a);
	a.insert(a.end(),123);
	print(a);
	a.resize(10);
	print(a);
	a.insert(a.end(),10,0);
	print(a);
	a.insert(a.begin()+3,521);
	print(a);
	                 
	a.erase(a.begin());
	print(a);
	int i=0,j=1;
	a.erase(a.begin()+i,a.begin()+j);
	print(a);
	reverse(a.begin(),a.end());
	print(a);
	sort(a.begin(),a.end());
	print(a); 
	/*
	用迭代器的，一般是区间，如vector的erase 
	用数字的，一般是开头的个数，如string的substr 
	预备知识
	a.begin()指向第一个元素，a.end()指向末尾，不是最后一个元素 
	1.判断是否为空a.empty(); 
	2.插入元素a.insert(a.begin(),3);
			  a.insert(a.end(),10);
			  a.insert(a.begin()+i,12);//在索引为i的位置插入 
			  a.insert(a.begin(),10,0);//在a的末尾插入10个0 
	3.删除元素 a.erase(a.begin());//删除开头元素
			   a.erase(a.begin(),a.end());//删除所有元素 
			   a.erase(a.begin(),a.begin()+a.size());//删除所有元素 
	  pop_back()
	4.清空clear()
	5.翻转reverse(a.begin(),a.end()); 
	*/
	return 0;
}
```

#### list

**STL中的list是双向链表，在内存中地址不连续，通过指针来实现数据的访问，插入和删除的的时间复杂度是常数级**

#### map

**底层是平衡二叉搜索树，效率高**

```c_cpp
#include <iostream>
#include <map>
#include <string.h>
using namespace std;

void translate(map<int,int> temp_map);//map直接作为参数传递
void translate(map<int,int> *pMap);//传递map指针
int main()
{
	 map<int,int> map1;
	 map1.insert(map<int,int>::value_type(1,22));
	 
	 translate(map1);
	 
	 map<int,int> *pmap1;
	 pmap1 = &map1;
	 
	 translate(pmap1);
	 
	 map<int,int> map2;
	 map2 = map1;//直接赋值
	 map<int,int>::iterator iter;
	 iter = map2.begin();
	 cout<<iter->second<<endl;
	 return 0;   
}

void translate(map<int,int> temp_map)
{
	 map<int,int> map2;
	 map2 = temp_map;
	 map<int,int>::iterator iter;
	 iter = map2.begin();
	 cout<<iter->second<<endl;
}
void translate(map<int,int> *pMap)
{
	 map<int,int> map2;
	 map2 = *pMap;
	 map<int,int>::iterator iter;
	 iter = map2.begin();
	 cout<<iter->second<<endl; 
}
```

```c_cpp
#include<bits/stdc++.h>
using namespace std;
void print(map<int,string> m){
	map<int,string>::iterator it;
	for(it=m.begin();it!=m.end();it++){
		cout<<it->first<<" "<<it->second<<endl;
	}
}
int main()
{
	pair<int,string> p;
	p.first=1;
	p.second="123";
	map<int,string> m;
	m.insert(p);
	cout<<p.first<<" "<<p.second<<endl;
	map<int,string>::iterator it;

	m[3]="234";
	for(it=m.begin();it!=m.end();it++){
		cout<<it->first<<" "<<it->second<<endl;
	}
	m.insert(make_pair(6,"你好"));
	cout<<m[0]<<endl;
	pair<int,string> p2;
	p2.first=12;
	p2.second="123123";
	m.empty();
	print(m);
	m.clear();
	print(m);
	m.empty();
	/*
	m[i]可用于输出元素，还可用于创建元素 
	1.初始化 map<type,type> name;
	2.添加元素 m[key]=value;
			   pair<type,type> p;m.insert(p);//insert返回该元素的迭代器 
	3.输出元素 cout<<m[i] ;
	4.清空元素clear();
	5.判断是否为空empty(); 
	*/
	return 0;
}
```

#### set

**底层实现是二叉搜索树，在竞赛中很常见访问每个元素的时间复杂度是O(logn)**


| 代码              | 解释                      |
| ------------------- | --------------------------- |
| set<int> s;       | 初始化一个set的集合       |
| s.insert(item);   | 将item插入s中             |
| s.erase();        | 将item删除,成功则1反之0   |
| s.find(k);        | 查找k返回一个迭代器       |
| s.count(k);       | 查找k存在返回1，不存在则0 |
| s.clear();        | 清除s中的数据             |
| s.empty();        | 判断s是否为空             |
| s.lower_bound(k); | 返回不小于k的迭代器       |
| s.upper_bound(k); | 返回不大于k的迭代器       |

```c_cpp
#include<bits/stdc++.h>
using namespace std;

void p(set<int>& s){
	set<int>::iterator it;
	for(it=s.begin();it!=s.end();it++){
		cout<<*it<<" ";
	}
	cout<<endl;
}
int main()
{
	vector<int> v;
	set<int> s;
	for(int i=0;i<10;i++){
		s.insert(i);
	}
	set<int>::iterator it;
	p(s);
	s.count(10);
	p(s);
	s.erase(1);
	p(s);
	it=s.begin();
	it++;
	it++;
	s.erase(it,s.end());
	p(s);
	return 0;
}
```

#### dequeue

#### queue

**队列，先进先出，后进后出**


| 代码          | 解释              |
| --------------- | ------------------- |
| queue<int> q; | 初始化一个q的队列 |
| q.front();    | 返回队首元素      |
| q.back();     | 返回队尾元素      |
| q.pop();      | 队首元素出队      |
| q.push(num);  | 把num放入队尾部   |
| q.size();     | 返回队列的大小    |
| q.empty();    | 判断队列是否为空  |

#### priority_queue优先队列

**底层实现是二叉堆，队里有自己的排序方式，每次入队都会将优先级最高的放在队首**

```c_cpp
#include<bits/stdc++.h>
using namespace std;

int main(){
	priority_queue<int> q;
	for(int i=0;i<10;i++){
		q.push(i);
	}
	while(!q.empty()){
		cout<<q.front()<<endl;
		q.pop();
	}
	return 0;
}
```

上述结果是9,8,7----0，说明每次push,优先队列都会把最大的数字放到前面

less会让队列从队首到队尾是高到低排列，也就是数字大的优先级越高（默认）

greater会让队列从队首到队尾是低到高排列，也就是数字小的优先级越高

```c_cpp
#include<cstdio>
#include<queue>
using namespace std;
priority_queue <int,vector<int>,less<int> > p;
priority_queue <int,vector<int>,greater<int> > q;
int a[5]={10,12,14,6,8};
int main()
{
	for(int i=0;i<5;i++)
		p.push(a[i]),q.push(a[i]);

	printf("less<int>:");
	while(!p.empty())
		printf("%d ",p.top()),p.pop();

	printf("\ngreater<int>:");
	while(!q.empty())
		printf("%d ",q.top()),q.pop();
}
```

#### stack

**先进后出的数据结构**


| 代码            | 解释               |
| ----------------- | -------------------- |
| stack<int> sta; | 初始化一个sta的栈  |
| sta.push(num);  | 把数字num放入sta中 |
| sta.pop();      | 队首元素出栈       |
| sta.top();      | 查看队首元素       |
| sta.size();     | 返回栈的长度       |
| sta.empty();    | 判断栈是否为空     |

## 迭代器iterator

```c_cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
	vector<int> v;
	set<int> s;
	for(int i=0;i<10;i++){
		s.insert(i);
	}
	set<int>::iterator it;
	for(it=s.begin();it!=s.end();it++){
		cout<<*it;
	}
	return 0;
}
```

## pair

参考链接：[pair的使用](https://blog.csdn.net/sevenjoin/article/details/81937695)

```c_cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
	pair<int,string> p;
	p.first=1;
	p.second="123";
	cout<<p.first<<" "<<p.second;
	return 0;
}
```
