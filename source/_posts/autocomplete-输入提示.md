title: autocomplete 输入提示
date: 2014-12-15 16:23:51
tags: javascript
categories: javascript
---

1.引入文件
``` bash
<script type="text/javascript" src="/static/plugins/jquery-ui/jquery-ui.min.js"></script>
<link rel="stylesheet" href="/static/plugins/jquery-ui/jquery-ui.min.css">
<style type="text/css">
    /*显示滚动条，默认高度300px*/
    .ui-autocomplete{max-height: 300px; overflow-y: auto; overflow-x: hidden;}
</style>
```

2.输入文本框
``` bash
<input id="input_key" name="input_key" type="text" value="">
```

3.javascript
``` bash
<script>
    var _data = ['abc', 'bcd'];    //提示数据；Object or Array
    $('#input_key').autocomplete({
        source: _data,
        minLength: 0,  //无输入也提示，1-输入1个字时提示......
        scroll: true,
        scrollHeight: 10,
        create: function(e, ui){
            $(this).bind('click', function(){  //文件框获取焦点即时提示，
                $(this).autocomplete('search', '');
            });
        },
    });
</script>
```