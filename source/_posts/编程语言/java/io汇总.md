---
title: 'io汇总'
date: 2022-11-23 10:06:51
tags: 基础
categories: java
---

## 字节流输入

```java
FileInputStream fis = new FileInputStream("C:\\Personal\\Desktop\\自己做的游戏\\彩虹屁生成器\\1.txt");
int len=0;
while((len=fis.read())!=-1){
    System.out.println((char) len);
}
fis.close();
```

## 缓冲字符流输入

```java
FileInputStream fis = new FileInputStream("C:\\Personal\\Desktop\\自己做的游戏\\彩虹屁生成器\\1.txt");
BufferedInputStream bis = new BufferedInputStream(fis);
byte[] b=new byte[1024];
int len=0;
while((len=bis.read())!=-1){
    System.out.println((char) len);
}
fis.close();
```

## 缓冲字符流输入

```java
FileReader fr = new FileReader("C:\\Personal\\Desktop\\自己做的游戏\\彩虹屁生成器\\1.txt");
BufferedReader br = new BufferedReader(fr);
String s=null;
while((s=br.readLine())!=null){
    System.out.println(s);
}
br.close();
fr.close();
```

> reader是读取字符的父类
>
> stream是读取字节的父类
>
> inputstreamreader是沟通字节与字符的桥梁
