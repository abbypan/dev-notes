电信 天翼网关 TEWA-780V 
============================

设置LOID、宽带账号

准备一个FAT32的U盘，插入路由器的USB接口。

使用useradmin 登录 http://192.168.1.1:8080/ ，密码在路由器机身的标签上查看。

F12 查看网页源码，查看 set3_sessionKey 的数字，例如7524351841943326816。注意这个数字会变化。

访问 http://192.168.1.1:8080/usbbackup.cmd?action=backupeble&set3_sessionKey=7524351841943326816

禁用快速恢复。

再访问 http://192.168.1.1:8080/usbbackup.cmd?action=backupeble&set3_sessionKey=7524351841943326816 。

如果数字过期，则重新F12查看，再访问新URL。

点击备份配置，导出e8_Config_Backup的文件夹。

有的说要在网页console贴js执行语句：

usbsubarea = {selectedIndex: 0, value: "never_mind", options: [{value: "usb1_1"}]}; btnApply();

访问 https://jonirrings.github.io/xor/ ，配置文件选中U盘中的 e8_Config_Backup/ctce8_TEWA-780V.cfg ，点击转换。

从 转换后的内容中 找到 telecomadmin 的密码。

使用 telecomadmin 登录 http://192.168.1.1/ 

网络-> 远程管理 -> 宽带识别码认证 -> 填入 逻辑ID（即LOID），逻辑密码与逻辑ID相同。

在网络 -> 网络设置 -> 网络连接 -> 连接名称 -> 找到internet的连接，封装类型为PPPOE，设置宽带拨号的用户名、密码

重启路由器
