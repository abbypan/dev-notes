wiiu
=======

aroma
-----

按网页教程处理：https://wiiu.hacks.guide/aroma/getting-started.html

格式化sd卡为fat32: https://github.com/usbtool/formatusb/releases

sd卡根目录下放wiiu文件夹

主机插入sd卡，开机，连gamepad，连wifi

浏览器访问 https://wiiuexploit.xyz，点击run exploit，同时长按B键

…

浏览器访问 https://wiiuexploit.xyz，点击run exploit，同时长按X键

…

wup installer
-------------

访问 https://www.gamebrew.org/wiki/WUP_Installer_GX2_Wii_U ,
下载wup_installer_gx2.wuhb 放到 wiiu/apps

访问 https://www.gamebrew.org/wiki/SigpatchesModuleWiiU ， 下载
01_sigpatches.rpx 放到 wiiu/environments/aroma/modules/setup

wiiu游戏安装文件夹，放到 sd卡根目录下的 install文件夹下

Region changing the Gamepad
---------------------------

wiiu主机与gamepad锁区，两者必须同区域才能配对。

-  假设有jpn gamepad，wiiu jpn主机, wiiu usa主机
-  使用 jpn gamepad，与 wiiu jpn主机 配对，破解 wiiu jpn主机
-  将 gamepad 改区

   -  访问 https://github.com/GaryOderNichts/DRXUtil/releases ，下载
      DRXUtil.rpx 放到 wiiu/apps
   -  按 https://wiki.hacks.guide/wiki/Wii_U:Region_Changing
      教程，可以将gamepad改到目标区域，例如usa

-  使用改刷的 usa gamepad，与 wiiu usa主机 配对，破解 wiiu usa主机
-  这样可直接使用英文界面的usa gamepad & wiiu
   usa主机，也不用改wiiu主机的区域

汉化界面
--------

使用sdcafiine外挂汉化: https://www.bilibili.com/opus/1001822313202581513

vwii 破解
------------


wiiu 已 aroma 破解。

参考 https://wii.hacks.guide/vwii-homebrew-channel 。

wiiu下安装  Compat Title Installer Wii U ： https://www.gamebrew.org/wiki/Compat_Title_Installer_Wii_U 。

点击compat installer，安装vwii下的hbc。

下载 YAWM ModMii Edition ：https://wii.hacks.guide/yawmme

下载usbloadergx：https://github.com/wiidev/usbloadergx/releases

下载  Patched IOS80 Installer for vWii ：https://oscwii.org/library/app/Patched_IOS80_Installer_for_vWii

下载 d2x cIOS installer vWii ：https://oscwii.org/library/app/d2x-cios-installer-vwii

在vwii下的hbc中安装YAWM ModMii Edition。

参考 https://www.bilibili.com/opus/747290053046173704


马里奥银河2 绿屏 
---------------------------

进入 vwii。

用  YAWM ModMii Edition  安装  usbloadergx 的 wad 。

用  usbloadergx 载入 马里奥银河2 的wbfs，点击该游戏，在setting中设置game lang为 japanese 。
