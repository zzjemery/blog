---
    title:  数组的常用方法
---

## 首尾操作

* push(): 在数组尾部添加元素，可以添加一个，也可以添加多个，返回新的长度。
* pop(): 删除数组的最后一项，只能删除最后一项，返回被删元素。
* shift(): 从头部删除一个元素，返回删除元素。
* unshift(): 在数组头部插入一个元素或多个元素，返回新的长度。

## 合并与拆分

* concat(): 合并两个或多个数组，返回一个新数组，不改变原来数组。
* slice(): 可以从已有的数组中返回选定的元素，返回的是一个新数组。
> eg：arr.slice(1,4);  <!-- 从下标为1的元素开始取，取到下标为4停止，包括1不包括4，也就是去下标为1，2，3的三个元素>

## 多功能方法

* splice():插入、删除、替换
> 一旦数组调用这个方法，数组会马上变化，不会返回新的数组。
```javascript
    //eg:
    var arr = [1,2,3,4,5,6,7,8];
    var arr1 = arr.splice(3,2,'x','y','z'); 
    //从数组下标为3开始，连续两项被替换为'x','y','z'  即arr1 = [x,y]
```

## 逆序

* reverse(): 让数组颠倒

## 排序

* sort()
    * 默认按照字符的顺序排，隐式转为字符串
    * 手动干预可以实现数字数组按大小排列，按个数排列

## 数组转为字符串

* join()
```javascript
    //eg:
    var arr = [1,2,3,4,5];
    var str = arr.join('*');
    console.log(str); //1*2*3*4*5
```