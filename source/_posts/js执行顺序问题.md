---
    title:  js执行顺序问题
---

## 半年前就困惑的问题

```javascript
    var a = 10;

    console.log(5<a<0); // false

    console.log(5<a<2); // true
```

> 由于js是按从上到下，从左到右的方式执行的，所以此处先执行 5 < a 这个比较，结果是true，又因为ture = 1，所以就有了 1 < 0 ==> false,1 < 2 ==> true.