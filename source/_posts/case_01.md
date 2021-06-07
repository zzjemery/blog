---
    title:  获取验证码
---

## 获取验证码

```html
    <input  type='number' placeholder="请输入验证码" class='jemery' maxlength="6" />
    <i id="jemery">获取验证码</i>
```

```javascript
    var t = 60;
    var flag = false;//是否在倒计时
    var timer = null;
    var jemery = document.getElementById('jemery');
    $('#jemery').on('click',function(){
        if(flag){
            return false;
        }else{
            flag = true;
            $('.vcode').val('').attr("placeholder",'短信序列号为：' + msg ).focus();//msg 是后台返回的数据
            countDown();
        }
    })
    function countDown(){
        timer = setInterval(function(){
            if(t > 1){
                t-- ;
                jemery.innerText = t + 'S';
            }else{
                t = 60;
                flag = false;
                jemery.innerText = '重新获取';
                clearInterval(timer)
            }
        },1000)
    }
```