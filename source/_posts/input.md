---
    title: 关于input的那些事
---

## input的placeholder样式自定义

> 在input框中有时想将输入的字和placeholder设为不同的颜色或其它效果，这时就可以用以下代码来对placeholder进行样式设置了。
> ::-webkit-input-placeholder{}    /* 使用webkit内核的浏览器 */
:-moz-placeholder{}                  /* Firefox版本4-18 */
::-moz-placeholder{}                  /* Firefox版本19+ */
:-ms-input-placeholder{}           /* IE浏览器 */

```html
    <div id="container">
        <input id="input-test" type="text" placeholder="修改placeholder样式" />
    </div>
```
```css
     #input-test{
        color: #FFC0CB;
        font-size: 1.2em;
        width: 180px;
        height: 36px;
    }
    #input-test::-webkit-input-placeholder{
            color: #ADD8E6;
    }
    #input-text::-moz-placeholder{  
            color: #ADD8E6;        
    }
    #input-text:-ms-input-placeholder{  
            color: #ADD8E6;        
    }
```

## input单选框的样式问题

```html
    <input type="radio" name="jemery" checked="checked">Jemery
    <input type="radio" name="jemery" >Tom
```
```css
    input[type="radio"]:checked{
        background-color:#ff5505;
    }
```

### 下面的css可以去掉date中上下小三角，但是保留input类型为number的小三角

```css
    input[type="date"]::webkit-inner-spin-button{
        visibility: hidden;
    }
```