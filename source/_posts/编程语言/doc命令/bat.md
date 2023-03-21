---
title: '基本doc命令'
date: 2022-05-23 10:06:51
tags: doc
categories: doc
---

`\?`查看帮助

## echo

`echo on/of`

开启，取消回显

`echo 内容`

输出内容

## del

`del 路径`

可以删除文件

`\F`

强制删除

`\P`

删除前需要确认

`\S`

删除所有子目录下的文件

`\Q`

安静模式，不需要确认

**垃圾清理例子**

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md24309.6640686.png)

## REM命令和::

> 注释的作用

`@rem aaaaaaaaaa `

## call和set的使用

```shell
@echo off
set aa=123123
set str=echo %aa%
call %str%
pause
```

## start 命令

```shell
start explorer c:\
@rem 打开c盘
```

## goto命令

```shell
@echo off
:start
set /a var+=1
echo %var%
if %var% leq 3 goto start
pause
```

> leq是小于的意思

## @取消回显,dir列出文件目录

```shell
@echo off
dir c:\
pause
```

## >覆盖>>追加

## &与执行，前面的无效不影响后面

## cls清屏

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md27611.2343393.png)

```shell
tree c:\
md 123
rd 123
```

## path添加文件路径名

```shell
@echo off
path=C:\Personal\Desktop
1.txt
pause
```

## copy

> 拷贝文件
>
> copy [file1] [file2]

## move

> 移动文件
>
> move [file] [directory]
>
> 修改目录
>
> move [dir1] [dir2]

## ren

> 修改文件名字
>
> ren 1.txt 2.txt

## ping

```shell
ping 域名 /t     ...参数
```

## net

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md30465.8998462.png)

```shell
net share   ::查看共享命令
netstat -ano|findstr 3306

```

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md30833.0647414.png)

## type查看某个文件

## xcopy 复制

## taskkill

## tasklist

## reg

## if

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md33990.2925189.png)

## %date%  %time%

## if exist

## for

```shell
@echo off
for %%i in (1,2,3,4,5) do echo %%i
pause
```

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md34887.9539284.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md35092.5947733.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\bat.md35168.0603045.png)
