---
    title: 手机点击input框不显示键盘的方法
---


## 开发过程中有时候有自己的安全键盘，此时若还有系统自带的键盘出现时就会同时又两个键盘，体验非常差，因此需要将系统键盘给去掉，具体的做法有：

1. 使用css样式
```css
    input { 
        pointer-events: none; 
    }
```

2. 使用事件阻止
```javascript
    input.onmousedown = function (e) { 
        e.preventDefault(); 
    } 
    //这样不仅会阻止键盘，同时 input 会失去光标跟随。 
    //如果你的需求不受这点因素影响，可以采用这种方式，否则还是自定义实现吧。
```

3. 使用其他非焦点获取的标签来代替input，比如div；

4. `<input onfocus='this.blur();'>`