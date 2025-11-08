Audio
=======


重装windows系统后，oed驱动故障，导致无声音
----------------------------------------------

intel 11代cpu

参考 https://www.bilibili.com/opus/497993911719182966?spm_id_from=333.1387.0.0

下载 Realtek 驱动: `DRV202102190003, Audio-n32a123w.exe <https://think.lenovo.com.cn/support/driver/driverdetail.aspx?DEditid=89528&driverID=undefined&treeid=3124500>`_

下载 Intel SST 驱动: `Intel Smart Sound Technology (SST) Driver for Windows 10 (64-bit) - 720S-13IKB (Type 81BV) <https://support.lenovo.com/us/en/downloads/ds503776>`_

设备管理器，选择 intel 智音技术音频总线(bus)/控制器(controller)，

更新驱动程序，浏览电脑查找，从计算机可用驱动程序列表选取，

取消显示兼容硬件，找到intel相关栏目，选择上面安装的控制器驱动版本。
