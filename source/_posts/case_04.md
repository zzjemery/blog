---
    title: 限制input输入框的字符或汉字
---


```html
    <input type="text"   name="explain"  id="explain" onkeyup="limitLength(value,20,'','explain')" >
```

```javascript
    function limitLength(value, byteLength, title, attribute) { 
            var newvalue = value.replace(/[^\x00-\xff]/g, "**"); //输入内容                   
            var length = newvalue.length;//获取内容长度               
        
            //当填写的字节数小于设置的字节数 
            if (length * 1 <=byteLength * 1){ 
                    return; 
            } 
            var limitDate = newvalue.substr(0, byteLength); 
            var count = 0; 
            var limitvalue = ""; 
            for (var i = 0; i < limitDate.length; i++) { 
                    console.log(i);
                    var flat = limitDate.substr(i, 1); 
                    if (flat == "*") { 
                        count++; 
                    } 
            } 
            var size = 0; 
            var istar = newvalue.substr(byteLength * 1 - 1, 1);//校验点是否为“×” 
        
            //if 基点是×; 判断在基点内有×为偶数还是奇数  
            if (count % 2 == 0) { 
                    //当为偶数时 
                    size = count / 2 + (byteLength * 1 - count); 
                    limitvalue = value.substr(0, size); 
            } else { 
                    //当为奇数时 
                    size = (count - 1) / 2 + (byteLength * 1 - count); 
                    limitvalue = value.substr(0, size); 
            } 
        // alert(title + "最大输入" + byteLength + "个字节（相当于"+byteLength /2+"个汉字）！"); 
        document.getElementById(attribute).value = limitvalue; 
        return; 
    }  
```

> 以上方法可以输入超过20个字符或10个汉字，但失去焦点时会只显示20个字符或10个汉字，多余的会被截掉。

> 若要实时监听则可采用下面的写法

```html
    <input type="text"   name="explain"  id="explain" oninput="limitLength(value,20,'','explain')" >
```

> oninput 可实时监听input框中的内容变化，但要注意它的使用方法