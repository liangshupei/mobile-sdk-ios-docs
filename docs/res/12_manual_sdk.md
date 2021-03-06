# 手动 导入 SDK

## 1、使用时的工程设置

* Podfile

```
Demo 工程中提供了 Podfile，里面已经写好了依赖的工程
```

* 工程设置

```
在工程的 Embed Library 中加上我们的 framework
在 Framework Search Path 中把 framework 所在路径设置好
```

* 注意目前只有 Debug 版本，且运行时注意是模拟器或真机环境 

## 2、SDK依赖的第三方开源库

```
source 'https://github.com/aliyun/aliyun-specs.git'

...

pod 'AliyunOSSiOS', '2.10.7'
pod 'CocoaAsyncSocket', '7.6.0'
pod 'ReachabilitySwift', '4.1.0'
pod 'AFNetworking', '2.6.3'
pod 'MQTTClient', '0.14.0'
pod 'Alamofire', '4.7.3'
```

## 3、导入 SDK

1. 新建工程

2. 选择工程文件 -> 选择target -> General

3. 在 Embedded Binaries 中点击 +，选择 RokidSDK.framework，点击确定。

4. 使用第3部的方法将依赖的第三方库依次加入。
![](media/manual_import_1.jpg)

5. 检查 setting 中的 framework search path 是否将添加的 framework 路径都包含了，缺少的加上。如果不确定，则在3、4步中添加framework时，选中 Copy item if needed，将 framework 添加到工程根目录下。
![](media/manual_import_2.jpg)

6. 在 setting 中打开 swift 标准库（Always Embed Swift Standard Libraries）
![](media/manual_import_3.jpg)

7. 如果 pod install 之后打开项目编译报如图的错误。
![](media/build_error_swift_version.png)

    需要选中 Pods 工程， 找到对应的 target，例如 `Alamofire`，然后选中 **Build Settings**，设置一个明确的 **Swift Language Version**，推荐设置 `Swift 4`。操作如图所示。

    ![](media/build_error_correct.png)
