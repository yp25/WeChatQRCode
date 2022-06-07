# WeChatQRCode

[![Download](https://img.shields.io/badge/download-App-blue.svg)](https://raw.githubusercontent.com/jenly1314/WeChatQRCode/master/app/release/app-release.apk)
[![MavenCentral](https://img.shields.io/maven-central/v/com.github.jenly1314.WeChatQRCode/wechat-qrcode)](https://repo1.maven.org/maven2/com/github/jenly1314/WeChatQRCode)
[![JitPack](https://jitpack.io/v/jenly1314/WeChatQRCode.svg)](https://jitpack.io/#jenly1314/WeChatQRCode)
[![CI](https://travis-ci.com/jenly1314/WeChatQRCode.svg?branch=master)](https://travis-ci.com/jenly1314/WeChatQRCode)
[![CircleCI](https://circleci.com/gh/jenly1314/WeChatQRCode.svg?style=svg)](https://circleci.com/gh/jenly1314/WeChatQRCode)
[![API](https://img.shields.io/badge/API-21%2B-blue.svg?style=flat)](https://android-arsenal.com/api?level=21)
[![License](https://img.shields.io/badge/license-Apche%202.0-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![Blog](https://img.shields.io/badge/blog-Jenly-9933CC.svg)](https://jenly1314.github.io/)
[![QQGroup](https://img.shields.io/badge/QQGroup-20867961-blue.svg)](http://shang.qq.com/wpa/qunwpa?idkey=8fcc6a2f88552ea44b1.1.982c94fd124f7bb3ec227e2a400dbbfaad3dc2f5ad)

基于OpenCV开源的微信二维码引擎移植的封装库。又一个扫码相关的轮子，之所以说又，是因为这样的轮子已经开源三个了；几个轮子之间的优缺点，各有千秋，请自寻选择（小孩子才做选择，我全都要）。
Based on OpenCV open source WeChat QR code engine porting package library. Another wheel related to scanning code, the reason why I say it again is because three such wheels have been open sourced; the advantages and disadvantages of several wheels have their own advantages and disadvantages, please find your own choice (children only make choices, I want them all) .

> 基于ZXing的扫码轮子 | Scanning wheel based on ZXing [ZXingLite](https://github.com/jenly1314/ZXingLite)
 
> 基于MLKit的扫码轮子 | Code scanning wheel based on MLKit [MLKit](https://github.com/jenly1314/MLKit)
 
> 基于OpenCV的扫码轮子| Code scanning wheel based on OpenCV [WeChatQRCode](https://github.com/jenly1314/WeChatQRCode)

## GIF 展示

暂时没有录制GIF。

> 你可以直接下载 | you can directly download [演示App](https://raw.githubusercontent.com/jenly1314/WeChatQRCode/master/app/release/app-release.apk) 体验效果

## 各Module相关说明 | Description of each Module

### [app](app)

示例App：主要用于提供WeChatQRCode的演示效果 | Mainly used to provide the demonstration effect of WeChatQRCode

### [opencv](opencv)

OpenCV：编译好的OpenCV | Compiled OpenCV

### [opencv-armv7a](opencv-armv7a)

OpenCV：**armeabi-v7a** 的libopencv_java4.so

### [opencv-armv64](opencv-armv64)

OpenCV：**arm64-v8a** 的libopencv_java4.so

### [opencv-x86](opencv-x86)

OpenCV：**x86** 的libopencv_java4.so
### [opencv-x86_64](opencv-x86_64)

OpenCV：**x86_64** 的libopencv_java4.so

### [wechat-qrcode](wechat-qrcode)

微信二维码识别：封装好的API，通过 **WeChatQRCodeDetector** 你可以很轻松的拥有OpenCV中开源的微信二维码识别功能
WeChat QR code recognition: The packaged API, through **WeChatQRCodeDetector**, you can easily have the open source WeChat QR code recognition function in OpenCV

### [wechat-qrcode-scanning](wechat-qrcode-scanning)

微信二维码扫码：有了上面的微信二维码识别功能，基本的扫码相关界面还是需要有个的，扫码加识别完美搭配，依赖[MLKit](https://github.com/jenly1314/MLKit)中的 **mlkit-camera-core**；
WeChat QR code scanning: With the above WeChat QR code recognition function, the basic scanning related interface still needs to have one, and scanning code and recognition are perfect combination, relying on [MLKit]
**wechat-qrcode-scanning** 相当于[MLKit](https://github.com/jenly1314/MLKit)中的 **mlkit-camera-core**的衍生库。


### [Java版本（点击查看java分支）]Java version (click to view the java branch) (https://github.com/jenly1314/WeChatQrCode/tree/java) 


## 引入

### Gradle:

1. 在Project的 **build.gradle** 里面添加远程仓库  |Add the remote repository in the **build.gradle** of the Project
          
```gradle
allprojects {
    repositories {
        //...
        mavenCentral()
    }
}
```

2. 在Module的 **build.gradle** 里面添加引入依赖项 | Add import dependencies in **build.gradle** of Module

```gradle
// OpenCV基础库（*必须）| // OpenCV base library (*required)
implementation 'com.github.jenly1314.WeChatQRCode:opencv:1.1.1'
implementation 'com.github.jenly1314.WeChatQRCode:opencv-armv7a:1.1.1'

// OpenCV的其他ABI（可选），根据你的需求选择想要的so支持 | // Other ABIs of OpenCV (optional), choose the so support you want according to your needs
implementation 'com.github.jenly1314.WeChatQRCode:opencv-armv64:1.1.1'
implementation 'com.github.jenly1314.WeChatQRCode:opencv-x86:1.1.1'
implementation 'com.github.jenly1314.WeChatQRCode:opencv-x86_64:1.1.1'

// 微信二维码识别功能（可选）| // WeChat QR code recognition function (optional)
implementation 'com.github.jenly1314.WeChatQRCode:wechat-qrcode:1.1.1'

// 微信二维码扫码功能（可选）| // WeChat QR code scanning function (optional)
implementation 'com.github.jenly1314.WeChatQRCode:wechat-qrcode-scanning:1.1.1'
//MLKit的Camera核心库：如果您使用了wechat-qrcode-scanning，则必须依赖mlkit-camera-core库 | 
//Camera core library for MLKit: If you use wechat-qrcode-scanning, you must rely on mlkit-camera-core library
implementation 'com.github.jenly1314.MLKit:mlkit-camera-core:1.0.3'

```

## 示例 | Example

初始化 **OpenCV** 和 **WeChatQRCodeDetector** （建议在 **MainActivity** 的 **onCreate** 方法中初始化）
| Initialize **OpenCV** and **WeChatQRCodeDetector** (recommended to be initialized in the **onCreate** method of **MainActivity**)
```kotlin
        //初始化OpenCV | Initialize OpenCV
        OpenCV.initAsync(context)

        //初始化WeChatQRCodeDetector | Initialize WeChatQRCodeDetector
        WeChatQRCodeDetector.init(context)
```   

识别二维码 （**wechat-qrcode**中的WeChatQRCodeDetector）| Recognize QR code (WeChatQRCodeDetector in **wechat-qrcode**)
```kotlin
    //识别二维码；results是一个List<String>集合，可能会有多个结果，如果只识别一个码，可以取List中第0个就可以
    //Recognize QR code; results is a List<String> collection, there may be multiple results, if only one code is recognized, you can take the 0th one in the List.
    val results = WeChatQRCodeDetector.detectAndDecode(bitmap)

``` 

识别二维码并返回二维码位置信息 （**wechat-qrcode**中的WeChatQRCodeDetector）
Identify QR codes and return QR code location information (WeChatQRCodeDetector in **wechat-qrcode**)
```kotlin
    // 扫码结果二维码的位置信息 | Scanning result QR code location information
    val points = ArrayList<Mat>()
    //通过WeChatQRCodeDetector识别图片中的二维码并返回二维码的位置信息 | Identify the QR code in the picture through WeChatQRCodeDetector and return the location information of the QR code
    val result = WeChatQRCodeDetector.detectAndDecode(bitmap, points)
    points.forEach { mat ->
        // 扫码结果二维码的四个点 | The four dots of the QR code in the scan result
        Log.d(TAG, "point0: ${mat[0, 0][0]}, ${mat[0, 1][0]}")
        Log.d(TAG, "point1: ${mat[1, 0][0]}, ${mat[1, 1][0]}")
        Log.d(TAG, "point2: ${mat[2, 0][0]}, ${mat[2, 1][0]}")
        Log.d(TAG, "point3: ${mat[3, 0][0]}, ${mat[3, 1][0]}")
    }

``` 



通过继承 **wechat-qrcode-scanning** 中的 WeChatCameraScanActivity或者WeChatCameraScanFragment可以很轻松的实现扫码功能
The scanning function can be easily implemented by inheriting WeChatCameraScanActivity or WeChatCameraScanFragment in **wechat-qrcode-scanning**
```kotlin
class WeChatQRCodeActivity : WeChatCameraScanActivity() {

    companion object{
        const val TAG = "WeChatQRCodeActivity"
    }

    override fun onScanResultCallback(result: AnalyzeResult<List<String>>) {
        if(result.result.isNotEmpty()){
            //停止分析 stop analysis
            cameraScan.setAnalyzeImage(false)
            Log.d(TAG,result.result.toString())
            // 当初始化 WeChatScanningAnalyzer 时，如果是需要二维码的位置信息，则会返回 WeChatScanningAnalyzer.QRCodeAnalyzeResult
            //When initializing WeChatScanningAnalyzer, if the location information of the QR code is required, WeChatScanningAnalyzer.QRCodeAnalyzeResult will be returned
            if(result is WeChatScanningAnalyzer.QRCodeAnalyzeResult){ // 如果需要处理结果二维码的位置信息 | If you need to process the location information of the resulting QR code

                val buffer = StringBuilder()
                val bitmap = result.bitmap.drawRect {canvas,paint ->
                    // 扫码结果可能有多个 | There may be multiple scan results
                    for ((index,data) in result.result.withIndex()) {
                        buffer.append("[$index] ").append(data).append("\n")
                        result.points?.forEach { mat ->
                            // 扫码结果二维码的四个点 | The four dots of the QR code in the scan result
                            Log.d(TAG, "point0: ${mat[0, 0][0]}, ${mat[0, 1][0]}")
                            Log.d(TAG, "point1: ${mat[1, 0][0]}, ${mat[1, 1][0]}")
                            Log.d(TAG, "point2: ${mat[2, 0][0]}, ${mat[2, 1][0]}")
                            Log.d(TAG, "point3: ${mat[3, 0][0]}, ${mat[3, 1][0]}")

                            val path = Path()
                            path.moveTo(mat[0, 0][0].toFloat(), mat[0, 1][0].toFloat())
                            path.lineTo(mat[1, 0][0].toFloat(), mat[1, 1][0].toFloat())
                            path.lineTo(mat[2, 0][0].toFloat(), mat[2, 1][0].toFloat())
                            path.lineTo(mat[3, 0][0].toFloat(), mat[3, 1][0].toFloat())
                            path.lineTo(mat[0, 0][0].toFloat(), mat[0, 1][0].toFloat())
                            // 将二维码位置在图片上框出来 | Frame the position of the QR code on the picture
                            canvas.drawPath(path, paint)
                        }
                    }
                }

                val config = AppDialogConfig(this, R.layout.qrcode_result_dialog).apply {
                    content = buffer
                    onClickConfirm = View.OnClickListener {
                        AppDialog.INSTANCE.dismissDialog()
                        // 继续扫码分析 | Continue to scan code analysis
                        cameraScan.setAnalyzeImage(true)
                    }
                    onClickCancel = View.OnClickListener {
                        AppDialog.INSTANCE.dismissDialog()
                        finish()
                    }
                    val imageView = getView<ImageView>(R.id.ivDialogContent)
                    imageView.setImageBitmap(bitmap)
                }
                AppDialog.INSTANCE.showDialog(config,false)

            } else {

                //一般需求都是识别一个码，所以这里取第0个就可以；有识别多个码的需求，可以取全部 | The general requirement is to identify one code, so the 0th one can be taken here; if there is a need to identify multiple codes, all of them can be taken.
                val text = result.result[0]
                val intent = Intent()
                intent.putExtra(MainActivity.SCAN_RESULT,text)
                setResult(RESULT_OK,intent)
                finish()
            }

        }
    }

    override fun createAnalyzer(): Analyzer<MutableList<String>>? {
        // 分析器默认不会返回结果二维码的位置信息 | The analyzer does not return the location information of the result QR code by default
//        return WeChatScanningAnalyzer()
        // 如果需要返回结果二维码位置信息，则初始化分析器时，参数传 true 即可
        //If you need to return the result QR code location information, when initializing the analyzer, you can pass true as the parameter
        return WeChatScanningAnalyzer(true)
    }

}
```
   
### 特别说明 Special Note

因为 **wechat-qrcode-scanning** 依赖了 [MLKit](https://github.com/jenly1314/MLKit) 中的 **mlkit-camera-core**，所以布局在使用上完全遵循 **mlkit-camera-core** 的使用方式。    Because **wechat-qrcode-scanning** relies on **mlkit-camera-core** in [MLKit](https://github.com/jenly1314/MLKit), the layout completely follows **mlkit in use How -camera-core** is used.
        
#### 布局示例 （这里贴出部分 **[MLKit](https://github.com/jenly1314/MLKit)** 中的部分示例）
#### Layout example (post here some examples from **[MLKit](https://github.com/jenly1314/MLKit)**)
>  可自定义布局（覆写getLayoutId方法），布局内至少要保证有PreviewView，然后自己可根据需要添加的控件。
>  You can customize the layout (override the getLayoutId method), at least ensure that there is a PreviewView in the layout, and then you can add controls as needed.

> PreviewView 用来预览，布局内至少要保证有PreviewView，如果是继承BaseCameraScanActivity或BaseCameraScanFragment，控件id可覆写getPreviewViewId方法自定义
> PreviewView is used for preview. At least PreviewView must be in the layout. If it inherits BaseCameraScanActivity or BaseCameraScanFragment, the control id can override the getPreviewViewId method to customize

> 关于扫码框动画，你可以直接拷贝[MLKit](https://github.com/jenly1314/MLKit)中的[ViewfinderView](https://github.com/jenly1314/MLKit/blob/master/mlkit-barcode-scanning/src/main/java/com/king/mlkit/vision/barcode/ViewfinderView.java)来使用，也可以自定义实现。
> Regarding the scan code box animation, you can directly copy the [ViewfinderView](https://github.com/jenly1314/MLKit/blob/master/mlkit) in [MLKit](https://github.com/jenly1314/MLKit) -barcode-scanning/src/main/java/com/king/mlkit/vision/barcode/ViewfinderView.java) to use, or you can customize the implementation.

```Xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <androidx.camera.view.PreviewView
        android:id="@+id/previewView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>
    <!-- 只需保证有布局内有PreviewView即可，然后自己可根据需要添加的控件 -->
    <!-- Just make sure that there is a PreviewView in the layout, and then you can add controls as needed -->
</FrameLayout>
```

更多使用详情，请查看[app](app)中的源码使用示例或直接查看 [API帮助文档](https://jitpack.io/com/github/jenly1314/WeChatQRCode/latest/javadoc/)
For more usage details, please see the source code usage example in [app](app) or directly view the [API help documentation](https://jitpack.io/com/github/jenly1314/WeChatQRCode/latest/javadoc/)

### 相关推荐 related suggestion

#### [MLKit](https://github.com/jenly1314/MLKit) 一个强大易用的工具包。通过ML Kit您可以很轻松的实现文字识别、条码识别、图像标记、人脸检测、对象检测等功能。     A powerful and easy-to-use toolkit. With ML Kit, you can easily implement text recognition, barcode recognition, image marking, face detection, object detection and other functions.
#### [ZXingLite](https://github.com/jenly1314/ZXingLite) 基于ZXing库优化扫码和生成二维码/条形码功能，扫码界面完全支持自定义。Based on the ZXing library, the function of scanning code and generating QR code/barcode is optimized, and the scanning interface fully supports customization.


## 版本记录 Version record

#### v1.1.1：2021-11-2
* 优化细节 Optimization details
* 更新mlkit-camera-core至v1.0.3 Update mlkit-camera-core to v1.0.3

#### v1.1.0：2021-8-6
* 编译多种ABI支持 Compile with multiple ABI support
* 更新mlkit-camera-core至v1.0.2 Update mlkit-camera-core to v1.0.2

#### v1.0.0：2021-7-24
* WeChatQRCode初始版本 Initial version of WeChatQRCode

## 赞赏 appreciate
如果您喜欢WeChatQRCode，或感觉WeChatQRCode帮助到了您，可以点右上角“Star”支持一下，您的支持就是我的动力，谢谢 :smiley:<p>
 If you like WeChatQRCode, or feel that WeChatQRCode has helped you, you can click "Star" in the upper right corner to support, your support is my motivation, thank you :smiley:<p>
您也可以扫描下面的二维码，请作者喝杯咖啡 :coffee:
  You can also scan the QR code below to invite the author to have a cup of coffee :coffee:
    <div>
        <img src="https://jenly1314.github.io/image/pay/wxpay.png" width="280" heght="350">
        <img src="https://jenly1314.github.io/image/pay/alipay.png" width="280" heght="350">
        <img src="https://jenly1314.github.io/image/pay/qqpay.png" width="280" heght="350">
        <img src="https://jenly1314.github.io/image/alipay_red_envelopes.jpg" width="233" heght="350">
    </div>

## 关于我 about me
   Name: <a title="关于作者" href="https://about.me/jenly1314" target="_blank">Jenly</a>

   Email: <a title="欢迎邮件与我交流" href="mailto:jenly1314@gmail.com" target="_blank">jenly1314#gmail.com</a> / <a title="给我发邮件" href="mailto:jenly1314@vip.qq.com" target="_blank">jenly1314#vip.qq.com</a>

   CSDN: <a title="CSDN博客" href="http://blog.csdn.net/jenly121" target="_blank">jenly121</a>

   CNBlogs: <a title="博客园" href="https://www.cnblogs.com/jenly" target="_blank">jenly</a>

   GitHub: <a title="GitHub开源项目" href="https://github.com/jenly1314" target="_blank">jenly1314</a>

   Gitee: <a title="Gitee开源项目" href="https://gitee.com/jenly1314" target="_blank">jenly1314</a>

   加入QQ群: <a title="点击加入QQ群" href="http://shang.qq.com/wpa/qunwpa?idkey=8fcc6a2f88552ea44b1411582c94fd124f7bb3ec227e2a400dbbfaad3dc2f5ad" target="_blank">20867961</a>
   <div>
       <img src="https://jenly1314.github.io/image/jenly666.png">
       <img src="https://jenly1314.github.io/image/qqgourp.png">
   </div>

