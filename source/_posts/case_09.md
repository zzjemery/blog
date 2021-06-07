---
    title: 未来元素绑定事件
---


> 最近在做jsp的项目，在发送ajax成功后返回数据并append到dom中，如果直接写点击事件的话是不会生效的，因此会有两种解决办法，一种是紧跟着append后面写点击事件，另一种就是在最外面绑定未来元素事件。


> 今天来说一下未来元素绑定事件

````html
    <ul class="existence">
        <li class="append">未来添加进来的li</li>
    <ul>
````

````js
    //给已知元素ul的未来儿子li绑定click事件
    $('.existence').on('click','.append',function(){
        alert('jemery');
    })
    //如果有多个未来元素也是一样
    $('.existence').on('click','.append',function(){
        console.log($(this).text())
    })
````


````html
    <ul class="existence">
        <li class="append">未来添加进来的li1</li>
        <li class="append">未来添加进来的li2</li>
        <li class="append">未来添加进来的li3</li>
        <li class="append">未来添加进来的li4</li>
        <li class="append">未来添加进来的li5</li>
        <li class="append">未来添加进来的li6</li>

    <ul>
````

````js
    
    //如果有多个未来元素也是一样
    $('.existence').on('click','.append',function(){
        console.log($(this).text())
    })
````