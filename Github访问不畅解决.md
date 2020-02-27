# GitHub访问不畅解决

## 1.获取Github相关网站的ip

访问https://www.ipaddress.com，找到页面中下方的“IP Address Tools - Quick Links”，
分别输入github.global.ssl.fastly.net和github.com，查询ip地址。

## 2.修改本地host文件

以Mac为例，命令行下输入：sudo vi /etc/host，然后输入电脑的密码，打开host文件。

## 3.增加host映射(20200227更新)
199.232.5.194	github.global.ssl.fastly.net
140.82.113.4	github.com

## 4.更新DNS缓存

命令行输入：sudo dscacheutil -flushcache，使增加的映射生效。

## 5.大功告成

接下来就可以随意访问Github和clone代码了。