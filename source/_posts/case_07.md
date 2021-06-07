---
    title: 如何对字符串进行隐藏处理
---

## 如何对字符串进行隐藏处理

````javascript
    function plusXing (str,frontLen,endLen) {
        var len = str.length-frontLen-endLen;
        var xing = '';
        for (var i=0;i<len;i++) {
            xing+='.';
        }
        return str.substring(0,frontLen)+xing+str.substring(str.length-endLen);
    }
````

> 结果如下：plusXing('jemery',1,1)  ==>  j....y
            plusXing('jemery',2,1)  ==>  je...y
            plusXing('jemery',1,0)  ==>  j.....

> 也可以这样操作：var str = 'jemery';
                plusXing(str,1,1)  ==>  j....y
                plusXing(str,2,1)  ==>  je...y
                plusXing(str,1,0)  ==>  j.....