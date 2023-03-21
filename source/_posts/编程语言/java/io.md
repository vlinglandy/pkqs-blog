---
title: 'java io操作'
date: 2022-11-23 10:06:51
tags: 基础
categories: java
---

# File类

## 创建文件，删除文件

```java
File file=new File("C:\\1.txt");
file.createNewFile();
file.delete();
```

## 创建文件夹

```java
file.mkdir();
```

## 常用方法

```java
.getNmae();
.length();//长度，汉字占两个字节，字母占一个字节
.idDirectory();
```

> file类能将字符串封装成一个文件，来代表一个文件，供流使用

# io流

![](file://C:\Personal\Documents\IkMarkdown\.assets\io.md112225.8044385.png)

```java
File file=new File("C:\\1.txt");
String str="你好";
FileOutputStream fos = new FileOutputStream(file);
fos.write(str.getBytes());//用append可以不用覆盖
fos.close();
```

## 乱码问题

![](file://C:\Personal\Documents\IkMarkdown\.assets\io.md113308.6995954.png)

## 复制文件

![](file://C:\Personal\Documents\IkMarkdown\.assets\io.md114167.4566158.png)

```java
String s1="c...";
String s2="d...";
FileInputStream fis = new FileInputStream(s1);
FileOutputStream fos = new FileOutputStream(s2);
int len=0;
while ((len=fis.read())!=-1){
    fos.write(len);
}
fis.close();
fos.close();
```

## 加速版本bufferinputstream

```java
String s1="c...";
String s2="d...";
FileInputStream fis = new FileInputStream(s1);
BufferedInputStream bis = new BufferedInputStream(fis);
FileOutputStream fos = new FileOutputStream(s2);
BufferedOutputStream bos = new BufferedOutputStream(fos);
byte[] bytes = new byte[1024];
int len=0;
while ((len=bis.read(bytes))!=-1){
    bos.write(bytes,0,len);
}
bis.close();
fis.close();
fos.close();
bos.close();
```

## 什么是序列化

> 就是将对象流化，就是将对象变成字节

## 读取文件内容

```java
FileReader fr = new FileReader("C:\\Personal\\Desktop\\自己做的游戏\\彩虹屁生成器\\1.txt");
char[] car=new char[1024];
int len=0;
while ((len=fr.read())!=-1){
    System.out.println(String.valueOf((char)len));
}
fr.close();
```

## 字符流读取

```java
FileReader fr = new FileReader("C:\\Personal\\Desktop\\自己做的游戏\\彩虹屁生成器\\1.txt");
BufferedReader br = new BufferedReader(fr,);
String line=null;
while ((line=br.readLine())!=null){
    System.out.println(line);
}
fr.close();
```

# 字符流能操作文本，字节流能操作几乎任意

```mindmap
- io
  - 字节
    - fileinputstream
    - 改乱码inputstreamreader
    - bufferinputstream
  - 字符
    - filereader
    - bufferedreader
  
```

## 最终的读入文件解决办法

```java
FileInputStream fis = new FileInputStream("C:\\Personal\\Desktop\\自己做的游戏\\彩虹屁生成器\\1.txt");
InputStreamReader isr = new InputStreamReader(fis, "UTF-8");
BufferedReader br = new BufferedReader(isr);
String s=null;
while ((s=br.readLine())!=null){
    System.out.println(s);
}
br.close();
isr.close();
fis.close();
```

> 走的时候用车，来的时候没有车
