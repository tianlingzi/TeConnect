# TeConnect
typecho第三方登录插件
# 前言
该插件的最初始的版本为[jiangmuzi/TeConnect][1]，最后维护时间为2016年。

由大卫二次开发并修复：[ledccn/TeConnect][1]，最后维护时间为2020年。

后由白雾林开发并修复：[baiwulin/ThirdLogin][3]，最后维护时间为2023年。

本人于2024年年底，在使用过程中，结合上面三位作者的修改进行融合修复，修改了部分设置和功能融合，在此特别说明并向三位作者的贡献表示感谢。

## 一、功能介绍
**Typecho互联登录插件，目前已支持15种第三方登录：QQ/腾讯微博/新浪微博/网易微博/人人网/360/豆瓣/Github/Google/Msn/点点/淘宝网/百度/开心网/搜狐。**

----------

## 二、插件下载
https://github.com/tianlingzi/TeConnect/releases

----------

## 三、安装步骤
 1. 解压插件到`Plugins`目录；
 2. 将文件名改为“TeConnect”；
 3. 把TeConnect插件目录下的callback.php文件拷贝到当前使用的主题跟目录下面；
 4. 在后台启用插件，并配置插件参数（方法见：参数配置 - 配置示例）；
 5. 在当前使用主题的适当位置添加`TeConnect_Plugin::show()`方法，代码：
   ```php
<?php TeConnect_Plugin::show(); ?>
   ```
 6. 在第三方平台设置网站回调域，注意区分http、https（方法见：参数配置 - 配置示例）。
 7. 如果您的主题开启了全站PJAX，需要把以下代码放入PJAX回调函数内：

```
/*PJAX时：来源页写入cookie*/
var exdate = new Date();
exdate.setDate(exdate.getDate() + 1);
document.cookie = "TeConnect_Referer=" + encodeURI(window.location.href) + "; expires=" + exdate.toGMTString() + "; path=/";
```

----------

## 三、参数配置
### 配置示例

名称 | 类型 | 配置示例 | 网站回调域
-|-|-|-
腾讯QQ | qq | qq:APP_KEY,APP_SECRET,腾讯QQ | https://127.0.0.1/oauth_callback?type=qq
腾讯微博 | tencent | tencent:APP_KEY,APP_SECRET,腾讯微博 | https://127.0.0.1/oauth_callback?type=tencent
新浪微博 | sina | sina:APP_KEY,APP_SECRET,新浪微博 | https://127.0.0.1/oauth_callback?type=sina
网易微博 | t163 | t163:APP_KEY,APP_SECRET,网易微博 | https://127.0.0.1/oauth_callback?type=t163
人人网 | renren | renren:APP_KEY,APP_SECRET,人人网 | https://127.0.0.1/oauth_callback?type=renren
360 | x360 | x360:APP_KEY,APP_SECRET,360 | https://127.0.0.1/oauth_callback?type=x360
豆瓣 | douban | douban:APP_KEY,APP_SECRET,豆瓣 | https://127.0.0.1/oauth_callback?type=douban
Github | github | github:APP_KEY,APP_SECRET,Github | https://127.0.0.1/oauth_callback?type=github
Google | google | google:APP_KEY,APP_SECRET,Google | https://127.0.0.1/oauth_callback?type=google
MSN | msn | msn:APP_KEY,APP_SECRET,MSN | https://127.0.0.1/oauth_callback?type=msn
点点 | diandian | diandian:APP_KEY,APP_SECRET,点点 | https://127.0.0.1/oauth_callback?type=diandian
淘宝网 | taobao | taobao:APP_KEY,APP_SECRET,淘宝网 | https://127.0.0.1/oauth_callback?type=taobao
百度 | baidu | baidu:APP_KEY,APP_SECRET,百度 | https://127.0.0.1/oauth_callback?type=baidu
开心网 | kaixin | kaixin:APP_KEY,APP_SECRET,开心网 | https://127.0.0.1/oauth_callback?type=kaixin
搜狐微博 | sohu | sohu:APP_KEY,APP_SECRET,搜狐微博 | https://127.0.0.1/oauth_callback?type=sohu

### 1：后台互联配置
具体格式为：`type:appid,appkey,title`，注释：
 - type：第三方登录帐号类型
 - appid：第三方开放平台申请的应用id
 - appkey：第三方开放平台申请的应用key
 - title：登录按钮的标题
在后台互联配置中，直接以文本形式填写，一行为一个帐号系统的参数；
为减少错误发生，您可以复制对应的`配置示例`，把`APP_KEY`和`APP_SECRET`改成您自己的参数就可以了！
例如：`qq:APP_KEY,APP_SECRET,腾讯QQ`
改成：`qq:101015836,547s87f8s7df7sd877ji75s78sdfd,腾讯QQ`
粘贴到后台`互联配置`，即完成了腾讯QQ登录的配置，其他类型同理！

### 2：网站回调域配置
您可以复制对应的`配置示例`，把`127.0.0.1`改成您的域名，填写到第三方开发平台的网站回调域设置中，即可完成配置！

以本博客`www.tianlingzi.top`,设置QQ登录，为例：
复制插件中给出的回调地址：`https://www.tianlingzi.top/oauth_callback?type=qq`

[1]: https://github.com/jiangmuzi/TeConnect
[2]: https://github.com/ledccn/TeConnect
[3]: https://github.com/baiwulin/ThirdLogin
