title: ZeroClipboard 复制内容到剪贴板
date: 2014-12-15 16:24:44
tags: javascript
categories: javascript
---

1.引入文件
``` bash
<script type="text/javascript" src="/static/js/jquery.min.js"></script>
<script type="text/javascript" src="/static/js/ZeroClipboard.min.js"></script>
```

2.复制按键
``` bash
<!-- data-clipboard-target 复制此ID对应的内容 -->
<input type="text" id="fe_text" name="fe_text" value="copy_me" />
<span id="btn-copy_1" data-clipboard-target="fe_text" data-clipboard-text="test_1">复制</span>
<!-- data-clipboard-text 默认复制的内容 -->
<span id="btn-copy_2" data-clipboard-text="test_2">复制</span>
<span id="btn-copy_10" data-clipboard-text="test_10">复制</span>
```

3.javascript
``` bash
<script>
$(document).ready(function(){
    //1.x IE7+
    $('span[id^="btn-copy"]').each(function(){
        var _id = $(this).attr('id');
        var client = new ZeroClipboard(document.getElementById(_id), {moviePath: "/static/js/ZeroClipboard.swf"});
        client.on("load", function(client) {
            client.on("complete", function(client, args){
                alert("复制成功: " + args.text);
            });
        });
    });
    //2.x IE9+
    $('span[id^="btn-copy"]').each(function(){
        var _id = $(this).attr('id');
        var client = new ZeroClipboard(document.getElementById(_id));
        client.on("ready", function(readyEvent){
            client.on("aftercopy", function(event){
                alert("复制成功: " + event.data["text/plain"]);
            });
        });
    });
});
</script>
```