# MTProto Heroku

## 概述

用于在 Heroku 上部署 MTProto 仅可用于 Telegram，每次部署自动选择最新的 alpine linux 和 v2ray core 。  

## 镜像

经测试本镜像不会因为大量占用资源而被封号。

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/a132395/heroku-MTProto)


### 端口

`端口` 为 `443` 。

### secret

`secret` 默认为 `a0cbcef5a486d9636472ac27f8e11a9d` 可自行设置。

## 流量中转

可以使用cloudflare的workers来`中转流量`，配置为：  

addEventListener(  
    "fetch",event => {  
        let url=new URL(event.request.url);  
        url.hostname="xx.xxxx.xx";//你的heroku域名    
        let request=new Request(url,event.request);  
        event. respondWith(  
            fetch(request)  
        )  
    }  
)  
