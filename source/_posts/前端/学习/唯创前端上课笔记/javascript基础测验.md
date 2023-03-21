---
title: '基础练习'
date: 2022-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: js
---

[javascript基础测验题目链接]([https://alidocs.dingtalk.com/i/team/O2RXDx4lJ6yRYXZj/docs/O2RXDQ0dD0o8ymZj# 「JavaScript基础测验」](https://alidocs.dingtalk.com/i/team/O2RXDx4lJ6yRYXZj/docs/O2RXDQ0dD0o8ymZj))

## 一，单项选择

1. C✔️对象遍历通过for...in
2. A✔️
3. A✔️
4. B✔️
5. B✔️//函数提升优先级比变量优先级高
6. D✔️

## 二，多项选择题

1. ABC✔️
2. ACD
3. ACD
4. ABCD
5. AC
6. ABC
7. ABCD

## 三，编程

1. ````javascript
   //第一种
   for (let i = 0; i < arr.length; i++) {
       var ran=Math.floor(Math.random()*arr.length);
       var temp=arr[ran];
       arr[ran]=arr[i];
       arr[i]=temp;
       console.log(arr[i]);
   }
   //第二种
   var arr=[1,2,3,4,5,6,7];
   var res=[],i=0;
   while(arr.length>0){
       var ran=Math.floor(Math.random()*arr.length);
       res.push(arr[ran]);
       arr.splice(ran,1);
       console.log(res[i++]);
   }
   //第三种
   var arr=[1,2,3,4,5,6,7];
   arr.sort(function (){
       return Math.random()-0.5;
   })
   console.log(arr);
   ````
2. ```javascript
   var x=10000000.111+"";
   var beg=x.indexOf(".")==-1?x.length:x.indexOf(".");
   var count=0;
   for(let i=beg-1;i>=0;i--){
       count++;
       if(count%3==0)x=x.substring(0,i)+","+x.substring(i,x.length);
   }
   console.log(x);
   ```
3. ```javascript
   var s="aba";
   var n=s.length;
   function judge(s){
       for(var i=0;i<=n/2;i++){
           if(s.charAt(i)!=s.charAt(n-i-1)){
               return false;
           }
       }
       return true;
   }
   console.log(judge(s));
   ```
4. ```javascript
   Array.prototype.newArr=function (arr2){
       var arr1=[];
       var res=[];
       for (let i = 0; i < arr2.length; i++) {
           if(arr1.indexOf(arr2[i])!=-1){

           }else{
               arr1.push(arr2[i]);
               res.push(arr2[i]);
           }
       }
       return res;
   }
   console.log(new Array().newArr([1,1,1,2,3,4]));
   ```
5. 不太理解原型
6. ```javascript
   var str1="asdasdsa1";
   function hasNum(str){
       for(let s of str){
           if(s>='0'&&s<='9')return true;
       }
       return false;
   }
   console.log(hasNum(str1));
   ```
7. ```javascript
   function multipli(a,b){
       return a*b;
   }
   ```
8. ```javascript
   function remove(arr,item){
       var res=[];
       for(let n of arr){
           if(n!=item)res.push(n);
       }
       return res;
   }
   console.log(remove([1,2,3],1));
   ```
9. ```javascript
   function toTwo(num){
       var res="";
       while(num){
           res=parseInt(num%2).toString()+res;
           num=parseInt(num/2);
       }
       if(res.length<8){
           var remain="";
           for(var i=0;i<8-res.length;i++){
               remain+="0";
           }
           res=remain+res;
       }
       return res;
   }
   console.log(toTwo(11));
   ```
10. ```javascript
    var a=["1","2","3","4","5"];
    var index=0;
    function after(){
        console.log(a[index++]);
    }
    setInterval(after, 2000);
    ```
11. ```javascript
    function mySort(arr){
        for(let i=0;i<arr.length-1;i++){
            for(let j=0;j<arr.length-i-1;j++){
                if(arr[j]>arr[j+1]){
                    var temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;
                }
            }
        }
        return arr;
    }
    console.log(mySort([1,3,2,4]));
    ```
12. ```javascript
    var s="20210107";
    var year=s.substring(0,4);
    var mon=s.substring(4,6);
    var day=s.substring(6,8);
    var res=year+"年"+mon+"月"+day;
    console.log(res);
    ```
13. ```javascript
    var user=prompt("请输入1,2,3 1:石头,2:剪刀,3:布");
    var result=['石头','剪刀','布'];
    var robot=parseInt(Math.random()*3)+1;
    if(robot-user==1||robot==1&&user==3){
        console.log("你赢了！你出的是："+result[user-1]+"机器人出的是："+result[robot-1]);
    }else if(robot==user){
        console.log("平局！你出的是"+result[user-1]+"机器人出的是"+result[robot-1]);
    }else{
        console.log("你输了你出的是"+result[user-1]+"机器人出的是"+result[robot-1])
    }
    ```
14. ```javascript
    function xyRandom(x,y){
        return Math.floor(Math.random()*(y-x+1))+x;
    }
    console.log(xyRandom(3,1003));
    ```
15. ```javascript
    var res=1,num=1;
    for(var i=0;i<64;i++){
        res*=2;
        num+=res;
    }
    console.log(0.00001*num+"kg");
    ```
16. ```javascript
    function seven(x){
        if(x%7==0)return false;
        while(x){
            if(x%10==7){
                return false;
            }
            x=parseInt(x/10);
        }
        return true;
    }
    for(let i=0;i<=100;i++){
        if(seven(i))console.log(i);
    }
    ```
17. ```javascript
    function sum(n){
        var res=1;
        if(n%2==0){
            for(let i=2;i<=n;i+=2){
                res+=1/i;
            }
            return res;
        }else{
            for(let i=3;i<=n;i+=2){
                res+=1/i;
            }
            return res;
        }
    }
    console.log(sum(11));
    ```
18. ```javascript
    function isDivid(m,n){
        var num=0;
        var res=0;
        for(let i=1;i<=n;i++){
            num=num*10+i;
            if(i>=m&&num%3==0)res++;
        }
        return res;
    }
    console.log(isDivid(1,7));
    ```
19. ```javascript
    不太会，自己瞎写的
    function getDataById(obj,target){
        if(typeof obj!="object")return ;
        for(let key in obj){
            if(key[id]==target)return key;
            return getDataById(key,target);
        }
    }
    ```
20. ```javascript
    function sum(n){
        var res=0;
        for(let i=1;i<=n;i++){
            var end=i;
            function huiwen(beg){
                if(beg==end)return beg;
                return ""+beg+huiwen(beg+1)+beg;
            }
            res+=parseInt(huiwen(1));
        }
        console.log(res);
    }
    sum(5);
    ```
21. ```javascript
    function toTuo(s){
        var arr=s.split('');
        var res=[];
        for(var i=0;i<arr.length;i++){
            if(arr[i]=='-'){
                res.push(String.fromCharCode(s.charCodeAt(i+1)-32));i++;//String.fromCharCode(arr[i+1].charCodeAt(i+1)-32)
            }else{
                res.push(arr[i]);
            }
        }
        return res.join('');
    }
    console.log(toTuo("asd-qwe-qwe"));
    ```
22. ```javascript
    function mySort(arr){
        var res=[];
        var num=[];
        for(let i=0;i<arr.length;i++){
            num.push(Object.keys(arr[i]).length);
        }
        for(var ii=0;ii<num.length-1;ii++){
            let max;
            max=0;
            var temp;
            var j;
            for(j=1;j<num.length-ii;j++){
                if(num[j]>num[max]){
                    max=j;
                }
            }
            temp=num[j-1];
            num[j-1]=num[max];
            num[max]=temp;
            temp=arr[j-1];
            arr[j-1]=arr[max];
            arr[max]=temp;
        }
        return arr;
    }
    var obj=[{a:1},{a:2,b:2,c:3},{a:3,b:2,c:4,d:5},{a:4,b:2}];
    console.log(mySort(obj));
    ```
23. 不太会
24. 不太会
25. ```javascript
    function centerPad(str,len,clo){
        if(len<=str.length)return str;
        var left=parseInt((len-str.length)/2);
        var right=len-str.length-left;
        var now=0,num=clo.length;
        var lstr="",rstr="";
        for(let i=0;i<left;i++){
            lstr+=clo[now%num];
            now++;
        }
        if(right!=left){
            rstr=lstr+clo[now%num];
        }else{
            rstr=lstr;
        }
        return lstr+str+rstr;
    }
    console.log(centerPad("hello",15,"abcasd"));
    ```
26.
27. ```javascript
    var a=[1,2,3,4];
    var res=[],one=0,two=0,thr=0,count=0;
    for(let i=0;i<a.length;i++){
        one=a[i];
        for(let j=0;j<a.length;j++){
            if(j==i)continue;
            two=one*10+a[j];
            for(let k=0;k<a.length;k++){
                if(k==j||k==i)continue;
                thr=two*10+a[k];
                if(res.indexOf(thr)==-1){
                    count++;
                    res.push(thr);
                }
            }
        }
    }
    console.log("数量为："+count+"，分别是：");
    console.log(res);


    ```
28. ```javascript
    function myMoney(x){
        var mine=0;
        if(x<=100000){
            return x*0.1;
        }else if(x>100000&&x<200000){
            return 100000*0.1+(x-100000)*0.075;
        }else if(x>=200000&&x<400000){
            return 100000*0.1+100000*0.075+(x-200000)*0.005;
        }else if(x>400000&&x<600000){
            return 100000*0.1+100000*0.075+200000*0.005+(x-400000)*0.003;
        }else if(x<1000000){
            return 100000*0.1+100000*0.075+200000*0.005+200000*0.003+(x-600000)*0.0015;
        }else{
            return 100000*0.1+100000*0.075+200000*0.005+200000*0.003+400000*0.0015+(x-1000000)*0.001;
        }
    }
    ```
29. ```javascript
    function remo(s){
        var res="";
        for (let c of s) {
            if(c!='a'&&
               c!='e'&&
               c!='i'&&
               c!='o'&&
               c!='u')res+=c;
        }
        return res;
    }
    console.log(remo("aeiosa"));
    ```
30. ```javascript
    function condition(x){
        var a,b,c;
        c=x%10;
        b=parseInt(x/10)%10;
        a=parseInt(x/100)%10;
        if(c*c*c+b*b*b+a*a*a===x)return true;
        return false;
    }
    for(let i=100;i<1000;i++){
        if(condition(i)){
            console.log(i);
        }
    }
    ```
31. ```javascript
    var res=1;
    for (let i = 0; i < 9; i++) {
        res=(res+1)*2;
    }
    console.log(res);
    ```
32. ```javascript
    function calcu(str){
        var num=0,letter=0,space=0,other=0;
        for (let s of str) {
            if(s>='0'&&s<='9')num++;
            else if(s>='a'&&s<='z'||s>='A'&&s<='Z')letter++;
            else if(s==' ')space++;
            else other++;
        }
        console.log(num,letter,space,other);
    }
    calcu('ad123  ???');
    ```
33. ```javascript
    console.log(
    "a->z,b->z,c->y"
    )
    ```

# 上课

```javascript
function fn(num){
    return num && num.toString().replace(/(\d)(?=(\d{3})+\.)/g,function (match){
    return match+',';
});
}
console.log(fn(1111111111.11));
```
