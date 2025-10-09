gradle
========


mirror
----------

project目录下的 gradle/wrapper/gradle-wrapper.properties 文件中修改路径

例如

.. note::

        distributionUrl=https\://mirrors.cloud.tencent.com/gradle/gradle-8.13-bin.zip


global mirror
---------------------

~/.gradle/init.d/gradle-mirror.gradle

.. note::

        allprojects {
            gradle.beforeSettings { settings ->
                def wrapper = settings.gradle.startParameter.gradleUserHomeDir.toPath()
                def wrapperProps = settings.settingsDir.toPath().resolve("gradle/wrapper/gradle-wrapper.properties").toFile()
                if (wrapperProps.exists()) {
                    def text = wrapperProps.text
                    def aliyunUrl = "https://mirrors.cloud.tencent.com/gradle/"
                    if (text.contains("https://services.gradle.org/distributions/")) {
                        text = text.replace("https://services.gradle.org/distributions/", aliyunUrl)
                        wrapperProps.text = text
                        println "[init.d] use Aliyun mirror for: ${settings.rootProject.name}"
                    }
                }
            }
        }
