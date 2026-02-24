
电信 天翼网关 TEWA-600AGM 
==============================


获取LOID、宽带账号


使用useradmin 登录 http://192.168.1.1/ ，密码在路由器机身的标签上查看

访问 http://192.168.1.1/backupsettings.conf

从 backupsettings.conf 找到 telecomadmin 的密码

使用 telecomadmin 登录 http://192.168.1.1/

在状态 -> 状态总览 -> 网关注册信息 获取 逻辑ID （即LOID）


在网络 -> 网络设置 -> 网络连接 -> 连接名称 -> 找到internet的连接，封装类型为PPPOE，查看用户名、密码，注意密码要在浏览器网页里查看
