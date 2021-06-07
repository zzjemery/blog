---
    title: jquery中有时候attr不管用
---

## jquery中有时候attr不管用

> 在开发的时候遇到一个问题
````html
    <input type='checkbox' >
````
````javascript
    //如果我在页面渲染的时候初始化
    $('input').attr('checked','');
    // 然后给一个click事件来改变这个值
    function click(){
        $('input').attr('checked','checked');
    }
    
````

> 在webapp中如果进入下一个页面，再返回该页面，页面重新渲染之后并没有重置checked的属性值，还是checked状态，那就是有问题的，虽然不知道是什么原因，但是有解决的方法：

````javascript
    //如果我在页面渲染的时候初始化
    $('input').prop('checked','');
    // 然后给一个click事件来改变这个值
    function click(){
        $('input').prop('checked','checked');
    }
    
````

> 使用prop代替attr的话就可以避免该问题，页面返回之后，checked的属性值就为空了