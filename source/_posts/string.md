---
    title:   字符串常见的方法和属性
---

## 属性

* length

## 方法

* charAt(): 返回在指定位置的字符

``'abcd'.charAt(0) == a``

* concat(): 链接字符串

* indexOf(): 检索字符串字符子串的位置

``'abcd'.indexOf('c') == 2``
``'abcd'.indexOf('e') == -1`` 注意：如果字符串中没有该子串，则返回'-1'！

* replace(): 替换字符串

``'abcd'.replace('ab','xy') == 'xybd'``

* slice(): 提取

``'abcd'.slice(-2,-1) == 'c'`` 注：从-2取到-1，包含-2不包含-1

* split(): 将字符串转为数组，切割字符串

* match(): 在父类字符串中匹配字符串，返回一个类数组

* substr(): 截取字符串

``'abcdefghijklmn'.substr(3,5) == 'defgh'`` 注：从下标为3的开始取，取5个字符，包括下标为3

* substring(): 截取子串

``'abcdefghijklmn'.substr(3,5) == 'de'`` 注：从下标为3的开始取，取到下标为5的字符，包括下标为3，不包括5

* toLowerCase()、toUpperCase(): 大小写转化

* search(): 获取字符在字符串中的位置

``'abcd'.search('c') == 2``
``'abcd'.search('e') == -1`` 注意：如果没有匹配到，则返回'-1'！


## 关于slice的问题

```javascript
    var arr = 'abcd'; 

    console.log(arr.slice(3,1)); // [] ==> 顺序错误，输出为空数组

    console.log(arr.slice(3,3)); // [] ==> 输出为空数组

    console.log(arr.slice(7,9)); // [] ==> 超出数组长度，输出为空数组 
```

## 字符串的返回值有三种

1. 返回字符串：substr,substring,charAt,slice,replace
2. 返回数字：indexOf,lastIndexOf,search,charCodeAt
3. 返回数组：split,match