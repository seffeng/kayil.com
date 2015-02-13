title: datepicker 日历插件
date: 2015-01-08 14:01:04
tags: javascript
category: javascript
---

```bash
$('#start_date').datepicker({
    dateFormat:'yy-mm-dd',
    maxDate:new Date(),
    onSelect:function(dateText, inst){
        var d = dateText.split('-');
        $('#end_date').datepicker('option', 'minDate', new Date(d[0], d[1]-1, d[2]));
        if($('#end_date').val() !='' && dateText > $('#end_date').val()){
            $('#end_date').datepicker('setDate', null);
        }
    }
});

$('#end_date').datepicker({
    dateFormat:'yy-mm-dd',
    maxDate:new Date(),
    onSelect:function(dateText, inst){
        var d = dateText.split('-');
        $('#start_date').datepicker('option', 'maxDate', new Date(d[0], d[1]-1, d[2]));
        if($('#start_date').val() !='' && dateText < $('#start_date').val()){
            $('#start_date').datepicker('setDate', null);
        }
    }
});
```