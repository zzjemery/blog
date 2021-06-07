---
    title: 如何快速获取到所点击的li是ul中的第几个
---

````html
    <ul class="list">
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
        <li>6</li>
        <li>7</li>
    </ul>
````

```js
    var oLi = $('.list li');
    for(var i = 0;i< oli.length;i++){
        oLi[i].index=i;
        oLi[i].onmouseover= function () {
            alert(this.index);
        };
    }

    //但是上述方法有他的弊端就是没办法保存有点像实时触发一样
    //因此有一种更为简便的获取方法
    
    $(".list li").click(function () {
    var index = $(".list li").index(this);
    alert(index);
    });

```