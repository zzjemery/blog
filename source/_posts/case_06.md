---
    title: 关于MUI的时间选择器参数问题
---

##  关于MUI的时间选择器参数问题 

### 该文默认读者已看过官方文档，若没有则请<a href="http://dev.dcloud.net.cn/mui/ui/#picker">点击查看文档</a>

> 最近在用MUI做一个时间选择器，要求：①不可选择当前时间之前的时间；②具有记忆功能，即记住上一次选择的时间，在下一次点击进去选择的时候显示的是上一次选择的时间。此处我们以选择“年月日”为例。

1. 首先我们要引入css和js

````html
    <!-- 需改成的自己文件路径 -->
    <link rel="stylesheet" href=".css/mui.min.css">
    <link rel="stylesheet" type="text/css" href="css/app.css" />
    <link rel="stylesheet" href="css/mui.picker.min.css" />
    <script src="../../js/jquery-3.1.1.min.js"></script>
    <script src="../../js/mui.min.js"></script>
    <script src="../../js/mui.picker.min.js" type="text/javascript" charset="utf-8"></script>
````

2. dom结构分两种，一种是不想精确自定义起始时间和结束时间的，一种是精确自定义的
    2.1 第一种
> dom结构如下
````html
    <button id='demo2' data-options='{"type":"date","beginYear":2014,"endYear":2016}' class="btn mui-btn mui-btn-block">选择日期 ...</button>
    <div id='result' class="ui-alert"></div>
````
> js方法如下
````javascript
    (function($) {
        $.init();
        var result = $('#result')[0];
        var btns = $('.btn');
        btns.each(function(i, btn) {
            btn.addEventListener('tap', function() {
                var _self = this;
                if(_self.picker) {
                    _self.picker.show(function (rs) {
                        result.innerText = '选择结果: ' + rs.text;
                        _self.picker.dispose();
                        _self.picker = null;
                    });
                } else {
                    var optionsJson = this.getAttribute('data-options') || '{}';
                    var options = JSON.parse(optionsJson);
                    var id = this.getAttribute('id');
                    /*
                        * 首次显示时实例化组件
                        * 示例为了简洁，将 options 放在了按钮的 dom 上
                        * 也可以直接通过代码声明 optinos 用于实例化 DtPicker
                        */
                    _self.picker = new $.DtPicker(options);
                    _self.picker.show(function(rs) {
                        /*
                            * rs.value 拼合后的 value
                            * rs.text 拼合后的 text
                            * rs.y 年，可以通过 rs.y.vaue 和 rs.y.text 获取值和文本
                            * rs.m 月，用法同年
                            * rs.d 日，用法同年
                            * rs.h 时，用法同年
                            * rs.i 分（minutes 的第二个字母），用法同年
                            */
                        result.innerText = '选择结果: ' + rs.text;
                        /* 
                            * 返回 false 可以阻止选择框的关闭
                            * return false;
                            */
                        /*
                            * 释放组件资源，释放后将将不能再操作组件
                            * 通常情况下，不需要示放组件，new DtPicker(options) 后，可以一直使用。
                            * 当前示例，因为内容较多，如不进行资原释放，在某些设备上会较慢。
                            * 所以每次用完便立即调用 dispose 进行释放，下次用时再创建新实例。
                            */
                        _self.picker.dispose();
                        _self.picker = null;
                    });
                }
                
            }, false);
        });
    })(mui);
````

> 这种写法是最初始的写法，可以看官方案例即可    

2.2  第二种写法是完全自定义时间且可以具有记忆功能

> dom结构如下
````html
    <div class="ZZtime">
        <span class="ZZtimeName">转账时间：</span>
        <button id="ZZtime" class="btn mui-btn mui-btn-block card" type="button" >
            <span class="span">请选择</span>
            <img src="../../images/kangdaifu/icon_downarrow.png" alt="" style="width: 20px ;height: 10px; float: right;margin:15px 3% 0">
        </button>
    </div>
````
> js如下
````javascript
    (function($) {
        $.init();
        var btns = $('.btn');
        //此处写法是指需要取某一特定时间时间begin，即自定义时间，但begin的格式为yyyymmdd，即20181210这种。
        //当然只需要保证beginY=yyyy,beginM=mm,beginD=dd
        //注意，此处这三个值一定要是Number类型的
        var beginY = Number(begin.substring(0,4));
        var beginM = Number(begin.substring(4,6))-1;//这里 -1 的操作是因为在Date函数中的getmonth本身就是当前月份-1
        var beginD = Number(begin.substring(6,8));
        var flag = 0 ;//这是是否开启记忆功能的标志，为0则不记录，非0记录
        btns.each(function(i, btn) {
            btn.addEventListener('tap', function() {
                var id = this.getAttribute('id');
                var picker = new $.DtPicker({
                    type:'date',
                    beginDate: new Date(beginY,beginM,beginD),//此处设置开始时间，并无法选择该时间之前的时间
                    endDate: new Date(2028,11,31)//此处设置时间选择器结束时间，最大只能设置为11，理由和上面-1一样
                });
                picker.show(function(rs) {
                    var pickerModeBtn =document.getElementById('ZZtime');
                    pickerModeBtn.getElementsByTagName('span')[0].innerText=rs.text;//展示所选的时间
                    flag ++;
                    picker.dispose();
                });
                if(flag != '0'){
                    var value =document.getElementById('ZZtime').getElementsByTagName('span')[0].innerText;
                    //默认选中时间，value的格式为2018-12-10
                    picker.setSelectedValue(value);
                }
            }, false);
        });
    })(mui);
````