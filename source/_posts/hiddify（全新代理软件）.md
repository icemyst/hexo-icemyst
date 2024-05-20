---
title: hiddify（全新代理软件）
tags:
  - 科学上网
categories: 实用工具
description: 无需复杂的配置，直接可以访问流媒体，chatgpt等限制平台。
cover: >-
  https://npm.elemecdn.com/ushio-api-img-moe@5.0.34/img_343_1869x1168_96_null_normal.jpg
background: >-
  https://npm.elemecdn.com/ushio-api-img-moe@5.0.47/img_471_2560x1440_72_null_normal.jpg
abbrlink: '3472'
date: 2024-04-13 00:28:34
---

{% folding open, 个人观念 %}

这里推荐这款软件，主要是适合小白配置，基于 [Sing-box](https://github.com/SagerNet/sing-box) 制作的，直接解锁chatgpt、流媒体，奈飞等，但还是有很多的 BUG，使用情况还是有点不理想，这里在使用的时候出现鼠标问题，开启后在移动鼠标的时候出现了很大的延迟，分流情况也很不理想，开启后，点击关闭，会出现软件退出情况，这里使用的是[hiddify V1.1.1](https://github.com/hiddify/hiddify-next/releases/tag/v1.1.1)版本出现的各种问题，等后面稳定了，就可以考虑使用这款软件了。

{% endfolding %}

{% hideToggle 点击预览,bg,blue %}
![hiddify](http://storage.live.com/items/7244E5F19F8EB8ED!524:/20240414183016.png?authkey=!AGBDz9Rfavu1WSE)
{% endhideToggle %}

## 介绍

一款基于 [Sing-box](https://github.com/SagerNet/sing-box) 通用代理工具的跨平台代理客户端。Hiddify 提供了较全面的代理功能，例如自动选择节点、TUN 模式、使用远程配置文件等。Hiddify 无广告，并且代码开源。它为大家自由访问互联网提供了一个支持多种协议的、安全且私密的工具。

## 使用

Hiddify 下载：【[点击前往](https://github.com/hiddify/hiddify-next/releases)】

备用下载区：

Android 端：【[点击跳转](https://www.123pan.com/s/mHNvjv-OwIfd.html)】
PC 端：【[点击跳转](https://www.123pan.com/s/mHNvjv-RwIfd.html)】

优选 IP 工具：【[点击下载](https://gitlab.com/Misaka-blog/warp-script/-/raw/main/files/warp-yxip/warp-yxip-win.7z)】

优选 IP 工具（蓝奏云）：【[点击跳转](https://bingmeng.lanzoub.com/ir1Ys1v4h4ha)】

配置文件：

{% note warning flat %}使用IP优选工具获取延迟低的IP，然后把**优选 IP** 和**优选端口**切换为你获取的 **IP** 和**端口**。{% endnote %}

```json
{  
"route": {
    "geoip": {
      "path": "geo-assets\\sagernet-sing-geoip-geoip.db"
    },
    "geosite": {
      "path": "geo-assets\\sagernet-sing-geosite-geosite.db"
    },
    "rules": [
      {
        "inbound": "dns-in",
        "outbound": "dns-out"
      },
      {
        "port": 53,
        "outbound": "dns-out"
      },
      {
        "clash_mode": "Direct",
        "outbound": "direct"
      },
      {
        "clash_mode": "Global",
        "outbound": "select"
      }
    ],
    "auto_detect_interface": true,
    "override_android_vpn": true
  },
  "outbounds": [
    {
      "type": "selector",
      "tag": "select",
      "outbounds": [
        "auto",
        "IP->Iran, Yotube:MisaHiro",
        "IP->Main, Yotube:MisaHiro"
      ],
      "default": "auto"
    },
    {
      "type": "urltest",
      "tag": "auto",
      "outbounds": [
        "IP->Iran, Yotube:MisaHiro",
        "IP->Main, Yotube:MisaHiro"
      ],
      "url": "http://cp.cloudflare.com/",
      "interval": "10m0s"
    },
    {
      "type": "wireguard",
      "tag": "IP->Iran, Yotube:MisaHiro",
      "local_address": [
        "172.16.0.2/32",
        "2606:4700:110:8c91:4063:21d0:7dd5:f218/128"
      ],
      "private_key": "CBVIIWvXdLr4PbSrnm11ZJJ300IiPudRD4R62/IxV1g=",
      "server": "162.159.195.93",
      "server_port": 2506,
      "peer_public_key": "bmXOC+F1FxEMF9dyiK2H5/1SUtzH0JuVo51h2wPfgyo=",
      "reserved": "AAAA",
      "mtu": 1280,
      "fake_packets": "5-10"
    },
    {
      "type": "wireguard",
      "tag": "IP->Main, Yotube:MisaHiro",
      "detour": "IP->Iran, Yotube:MisaHiro",
      "local_address": [
        "172.16.0.2/32",
        "2606:4700:110:8c15:3f90:ad2d:8810:77f3/128"
      ],
      "private_key": "CCC/TQTc82ub9i8f37Rpix2v425Sv/mxTzvE/iKRMkw=",
      "server": "优选ip",
      "server_port": 优选端口,
      "peer_public_key": "bmXOC+F1FxEMF9dyiK2H5/1SUtzH0JuVo51h2wPfgyo=",
      "reserved": "AAAA",
      "mtu": 1280,
      "fake_packets": "5-10"
    },
    {
      "type": "dns",
      "tag": "dns-out"
    },
    {
      "type": "direct",
      "tag": "direct"
    },
    {
      "type": "direct",
      "tag": "bypass"
    },
    {
      "type": "block",
      "tag": "block"
    }
  ]
}
```

## 扩展

这里可以改一下dns选项，也可以不改，默认为cloudflare的服务器地址，这里可以使用以下服务器地址。

直连DNS：

```
中国移动 DNS：211.138.180.2
备用 DNS 服务器：211.138.180.3

中国联通 DNS：221.131.143.69
备用 DNS 服务器：221.131.143.69

中国电信 DNS：223.5.5.5
备用 DNS 服务器：223.6.6.6
```

远程DNS：

```
Google Public DNS：tls://8.8.8.8和tls://8.8.4.4
```