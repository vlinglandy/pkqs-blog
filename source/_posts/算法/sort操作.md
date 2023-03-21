---
title: 'sort操作'
date: 2022-05-20 10:06:51
tags: 
    - 数据结构
    - 算法
categories: 算法
---

## sort比较多维vector

```cpp
sort(intervals.begin(),intervals.end(),[](vector<int> &a,vector<int> &b){
    return a[1]<b[1];
});
```

```java
  Arrays.sort(ins, (a, b)->{
            return a[1] != b[1] ? a[1] - b[1] : b[0] - a[0];
        });
```
