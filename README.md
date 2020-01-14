# nginx-geo-module
## getting over nested if and multiple ifs using geo module in nginx


This snippet checks if the remote_addr matches any of the ips given below and sets the variable check_var's value to 1

```
geo $remote_addr $check_var{     
 default 0;
 192.168.12.11 1;
 192.168.12.15 1;
 }
 
```

Based on the requirement you can perform a specific operation with a condition in server block

```

if ($check_var != 1) {
    # redirect 
    return 302 http://www.redirect-here.com; 
    # set a variable value
    set $var value;
    # proxy pass
    proxy_pass http://upstream_server
}
 
```

Reference URLs : 

Nginx Geo Module : http://nginx.org/en/docs/http/ngx_http_geo_module.html

Nginx if : https://www.nginx.com/resources/wiki/start/topics/depth/ifisevil/
