app mitm
==========

以 moto手机 + mitmproxy 为例

网络
---------

手机与PC连同一个wifi

手机解锁
----------------

开机，版本号按5次，打开开发者模式

在开发者模式下，开启oem解锁

重启，音量下键+电源键，进fastboot

fastboot oem get_unlock_data

获取unlock_data

在 https://motorola-global-portal.custhelp.com/app/standalone/bootloader/unlock-your-device-b 请求解锁

邮箱收到解锁码xxxx

fastboot oem unlock xxxx


手机刷magisk
-------------

下载moto官方firmware底包，提取boot.img

下载magisk的apk，安装到手机

在手机中打开magisk，对boot.img打补丁，获得 magisk_boot.img

进fastboot，刷入 magisk_boot.img

fastboot flash boot magisk_boot.img

重启


手机安装cert-fixer模块
-------------------------

下载cert-fixer.zip: https://github.com/pwnlogs/cert-fixer

在手机中打开magisk，切换到模块栏，安装cert-fixer.zip

重启


PC安装mitmproxy
------------------

https://github.com/mitmproxy/mitmproxy

假设PC的ip地址为 192.168.1.2

PC启动mitmproxy，假设mitmproxy的port为8080


手机侧安装mitmproxy root cert
----------------------------------

手机侧配置wifi的代理为 192.168.1.2:8080

手机侧使用浏览器（例如edge, firefox）访问 https://mitm.it ，根据提示下载 mitmproxy root cert文件，在系统中添加用户根证书

重启


app访问，pc侧mitm web页
-------------------------

pc侧使用浏览器打开 http://127.0.0.1:8081/ ，切换到 flow list 子页

手机使用app访问 https 内容

pc侧mitm查看内容


app访问，pc侧mitm用python解析指定内容
------------------------------------------


示例 example.py
######################

.. code-block:: python
   :linenos:

        from mitmproxy import http
        from datetime import datetime
        import json
        import os
        import hashlib

        OUTFILE = "example.txt"


        with open(OUTFILE, "w") as f:
            pass

        def response(flow: http.HTTPFlow):
            url = flow.request.pretty_url
            if "https://example.com/api/auth" in url:
                body = flow.response.content
                try:
                    data = json.loads(body)
                    token = data.get('data', {}).get('token')
                    if token:
                        ts = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
                        with open(OUTFILE, "a") as f:
                            f.write(f"[{ts}] : {token}\n\n")

                except Exception as e:
                    with open(OUTFILE, "a") as f:
                        f.write(f"Exception: {e}\n")



pc侧mitmproxy运行 example.py
###################################


mitmproxy -s example.py

手机使用app访问 https 内容

pc侧可查看解析出的 example.txt
