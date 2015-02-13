title: nginx wordpress伪静态
date: 2015-01-08 13:47:18
tags: nginx
category: nginx
---

修改 nginx 配置文件，修改 location / {} 部分，增加 if 部分。
```bash
location    / {
    index       index.html index.htm index.php index.asp default.asp default.htm default.html default.aspx;
    if (-f $request_filename/index.html){
        rewrite (.*) $1/index.html break;
    }
    if (-f $request_filename/index.php){
        rewrite (.*) $1/index.php;
    }
    if (!-f $request_filename){
        rewrite (.*) /index.php;
    }
}
```