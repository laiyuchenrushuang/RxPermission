# RxPermission
### 背景
-----------------------------
   以前申请权限，很是累，先是去request，然后再去check，我觉得动态申请权限 这个好用，在这里两者合并了。代码不提供，这里直接显示怎么用。
### 开启的方式
-----------------------------
##### 1.看官网
 https://github.com/tbruyelle/RxPermissions#setup
##### 2.配环境

    （一）：build.gradle文件
    allprojects {
        repositories {
            ...
            maven { url 'https://jitpack.io' }
        }
    }

    dependencies {
        implementation 'com.github.tbruyelle:rxpermissions:0.10.2'
        implementation "io.reactivex.rxjava2:rxjava:2.2.1" // 必要rxjava2依赖
    }
  
    （二）：清单文件
  
    <uses-permission android:name="android.permission.CAMERA" />
    
 ##### 3.创建实例
    final RxPermissions rxPermissions = new RxPermissions(this); // where this is an Activity or Fragment instance
 ##### 4.开始使用
    rxPermissions
                .request(Manifest.permission.CAMERA)
                .subscribe(granted -> {
                    if (granted) { // Always true pre-M
                        Log.d("lylog", "Get permission");
                    } else {
                        finish();
                        Log.d("lylog", "No get permission");
                    }
                })
