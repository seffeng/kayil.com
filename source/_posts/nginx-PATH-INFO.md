title: nginx PATH_INFO
date: 2015-01-08 13:52:24
tags: nginx
category: nginx
---

1.地址跳转
```bash
rewrite ^/.*/?$ http://www.qycn.com/host/ last;
rewrite ^/(.*)$ http://www.qycn.com/$1 last;
```
2.PATH_INFO 一
```bash
location ~ \.php {
    fastcgi_index index.php;
    fastcgi_pass 127.0.0.1:9000;
    include      fastcgi_params;
    set $path_info "";
    set $real_script_name $fastcgi_script_name;
    if ($fastcgi_script_name ~ "^(.+?\.php)(/.+)$") {
        set $real_script_name $1;
        set $path_info $2;
    }
    fastcgi_param SCRIPT_FILENAME /var/html/$real_script_name;
    fastcgi_param SCRIPT_NAME $real_script_name;
    fastcgi_param PATH_INFO $path_info;
}
```
3.PATH_INFO 二(thinkphp 将 URL_MODEL 改成 2)
```bash
if (!-e $request_filename) {
    rewrite  ^(.*)$  /index.php?s=$1  last;
    break;
}
location    ~ \.php {
    fastcgi_pass   127.0.0.1:9001;
    fastcgi_index  index.php;
    fastcgi_split_path_info ^(.+\.php)(.*)$;
    fastcgi_param PATH_INFO $fastcgi_path_info;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
}
```