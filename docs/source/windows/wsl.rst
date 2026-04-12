安装WSL ubuntu虚拟机
-------------------------

开启WSL
###############

powershell 管理员

    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

或者通过开启windows功能: hyper-v，适用于linux的windows子系统

 
查看版本 
###############

    wsl -l -o 

安装 
###############

    wsl --install Ubuntu-20.04  

或者在windows store里安装

 
迁移到D盘
###############

    wsl --shutdown

    wsl --export Ubuntu-20.04 d:\ub.tar

    wsl --unregister Ubuntu-20.04 

    wsl --import Ubuntu-20.04 d:\software\vm\ubuntu\  d:\ub.tar   

压缩wsl镜像
###############

    wsl --shutdown

    diskpart

    DISKPART> select vdisk file = "xxxx\ext4.vhdx"

    DISKPART> compact vdisk
