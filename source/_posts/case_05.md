---
    title: 类似input focus和blur事件的替代
---

> 在webapp的日常开发中会出现这样一种情形，由于顶部的“返回键”、标题、“首页”是属于app端的控件，若有一个input的在失去焦点时要触发某个函数，此时用户若输入完成后直接点击“返回键”，则还是会执行该函数，此时blur()事件并没有那么好用，但可以用其他的办法解决。

```html 
    <input id="jemery"  />
```

```javascript
    //这种情况下点击当前app除了该input框的任何地方都会弹出1，而我们要实现的效果是点击“返回”可返回到上一页面且不会有弹框
    $("#jemery").blur(function(){
        alert(1);
    })
```

> 此时可有另一种方法来代替blur事件

```javascript
    //这种方法可以避免之前那种尴尬的情况，因为顶部的控件是app的，并不属于网页，也不存在document这个说法
    $(document).on("click",function(e){
        if((window.event.srcElement.id) != "jemery"){
             alert(1);
        }
    })
```