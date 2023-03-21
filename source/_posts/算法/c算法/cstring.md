---
title: 'cstring'
date: 2022-05-23 10:06:51
tags: 
    - c
categories: 算法
---

[c语言字符串操作](https://blog.csdn.net/yunmao2882/article/details/88962329)

[string类全解](http://c.biancheng.net/view/400.html)

```c
#include<stdio.h>
#include<string.h>
int main(){
	char a[]={'a','b','\0','c'};
	char b[10];
	printf("%s\n",a);
	strcpy(b,a);
	int i=0;
	printf("%s\n",b);

	strcat(a,b);
	printf("%s\n",a);

	printf("%d\n",strcmp(a,b));

	printf("%d",strchr(a,'a'));
	return 0;
}
```

## substr

> substr有2种用法：
> 假设：string s = "0123456789";

> string sub1 = s.substr(5); //只有一个数字5表示从下标为5开始一直到结尾：sub1 = "56789"

> string sub2 = s.substr(5, 3); //从下标为5开始截取长度为3位：sub2 = "567"
