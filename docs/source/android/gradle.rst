gradle
========


gradle-wrapper.properties 
-----------------------------

仅当前 project，在gradle/wrapper/gradle-wrapper.properties 文件中修改

.. note::

        distributionUrl=https\://mirrors.cloud.tencent.com/gradle/gradle-8.13-bin.zip


全局project，新建文件 ~/.gradle/init.d/gradle-mirror.gradle ，内容例如

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



settings.gradle
-----------------

.. note::

        pluginManagement {
            repositories {
                maven { url 'https://maven.aliyun.com/repository/google' }
                maven { url 'https://maven.aliyun.com/repository/central' }
                maven { url 'https://maven.aliyun.com/repository/gradle-plugin' }
                google()
                mavenCentral()
                gradlePluginPortal()
            }
        }

        dependencyResolutionManagement {
            repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
            repositories {
                maven { url 'https://maven.aliyun.com/repository/google' }
                maven { url 'https://maven.aliyun.com/repository/central' }
                maven { url 'https://maven.aliyun.com/repository/public' }
                google()
                mavenCentral()
            }
        }
        rootProject.name = "myappname"
        include(":app")


build.gradle
--------------

.. note::

        plugins  {
            id "com.android.application" version "8.13.0" apply false
            id "org.jetbrains.kotlin.android" version "2.2.0" apply false
        }



app/build.gradle
--------------------

.. note::

        plugins {
            id 'com.android.application'
            id 'org.jetbrains.kotlin.android'
        }

        android {
            namespace 'com.example.jwtapp'
            compileSdk = 34

            defaultConfig {
                applicationId = "com.example.jwtapp"
                minSdk = 26
                targetSdk = 34
                versionCode = 1
                versionName = "1.0"
            }

            buildTypes {
                release {
                    minifyEnabled = false
                    proguardFiles(
                            getDefaultProguardFile('proguard-android-optimize.txt'),
                            'proguard-rules.pro'
                    )
                }
                debug {
                    minifyEnabled = false
                }
            }

            buildFeatures {
                viewBinding = true
            }

            compileOptions {
                sourceCompatibility = JavaVersion.VERSION_17
                targetCompatibility = JavaVersion.VERSION_17
            }

            kotlinOptions {
                jvmTarget = "17"
            }
        }

        dependencies {
            implementation "org.jetbrains.kotlin:kotlin-stdlib:2.2.0"
            implementation 'androidx.core:core-ktx:1.12.0'
            implementation 'androidx.appcompat:appcompat:1.7.0'
            implementation 'com.google.android.material:material:1.12.0'

            // OkHttp for HTTPS
            implementation 'com.squareup.okhttp3:okhttp:4.11.0'
            implementation 'com.squareup.okhttp3:logging-interceptor:4.11.0'

            // JWT ES256
            implementation 'io.jsonwebtoken:jjwt-api:0.11.5'
            runtimeOnly 'io.jsonwebtoken:jjwt-impl:0.11.5'
            runtimeOnly 'io.jsonwebtoken:jjwt-jackson:0.11.5'
        }

        androidComponents {
            onVariants(selector().withBuildType("debug")) { variant ->
                def runtimeConfig = variant.runtimeConfiguration
                def copyName = variant.name + "RuntimeClasspathCopy"

                if (!configurations.findByName(copyName)) {
                    configurations.create(copyName) { conf ->
                        conf.extendsFrom(runtimeConfig)
                        conf.canBeResolved = true
                        conf.canBeConsumed = false
                    }
                }
            }
        }

