---
layout: post
title:  "nginx基本操作"
date:   2018-08-07 22:18:00 +0800
tags: Nginx
---

#### 安装
{% highlight shell %}
# MacOS
brew install nginx
# ubuntu
apt-get install nginx
{% endhighlight %}

#### 操作
{% highlight shell %}
# 检查配置
nginx -t
# 选择配置文件
nginx -c /path/to/config
# MacOS
brew services start nginx || nginx
brew services stop nginx || nginx -s stop
brew services restart nginx || nginx -s reload
# ubuntu
service nginx start
service nginx stop
service nginx restart

{% endhighlight %}


{% highlight shell %}
upstream node_test {
    server 47.91.240.218:3000;
}
server {
    listen       8000;
    server_name localhost;

    location / {
        proxy_pass http://localhost:8084;
        # proxy_redirect default;
    }
    location /api {
        rewrite  ^/api/(.*)$ /$1 break;
        proxy_pass   http://node_test;
    }
}
{% endhighlight %}
