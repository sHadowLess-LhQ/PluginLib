# PluginLib

#### 软件架构

升级满帮集团开源插件库框架插件库

### 缘由

原框架AGP版本低，不支持很多新特性（尤其是ViewBinding），升级到AGP 7.0.2

但原框架支持剔除公共库的AGP插件，升级后无法使用

（太菜了，不会写基于7.0.2的AGP插件）

支持compileOnly编译的库，还是可以和宿主共用

### 注意

测试安卓5.1以下不支持ViewBinding

### 安装教程

Step 1. 添加maven仓库地址和配置

```
     //旧AndroidStudio版本
     //build.gradle
     allprojects {
         repositories {
            ...
             maven { url 'https://jitpack.io' }
         }
     }
     
     //新AndroidStudio版本
     //settings.gradle
     dependencyResolutionManagement {
          repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
          repositories {
            ...
             maven { url 'https://jitpack.io' }
          }
      }
```

Step 2. 添加依赖

a、克隆引入

直接下载源码引入model

b、远程仓库引入

[![](https://jitpack.io/v/com.gitee.shadowless_lhq/host-lib.svg)](https://jitpack.io/#com.gitee.shadowless_lhq/plugin-lib)

```
     dependencies {
         implementation 'com.gitee.shadowless_lhq:plugin-lib:Tag'
         implementation 'com.gitee.shadowless_lhq:common-lib:1.0.0'
         implementation 'io.reactivex.rxjava2:rxjava:2.2.21'
         implementation 'io.reactivex.rxjava2:rxandroid:2.1.1'
         implementation 'com.github.liujingxing.rxlife:rxlife-rxjava2:2.2.2'
     }
```

#### 使用说明

### 使用方法

一定要继承以下类进行开发，不然宿主获取指定类型的类后，做构造代理类时强转会报错

- Activity需要继承PluginInterceptActivity
- Application需要继承PluginInterceptApplication
- IntentService需要继承PluginInterceptIntentService
- Service需要继承PluginInterceptService

需要快速开发Activity，可以继承BaseInterceptActivity

其他具体使用方法参照原项目使用方法：

[Phantom — 唯一零 Hook 稳定占坑类 Android 热更新插件化方案](https://github.com/ManbangGroup/Phantom)
