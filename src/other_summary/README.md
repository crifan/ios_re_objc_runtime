# 其他心得

## iOS Runtime Header

可以查询和搜索iOS运行时的头文件的网站：

https://developer.limneos.net/

## ObjC Runtime源码

* objc4 = Objc = ObjC Runtime
  * 下载
    * https://opensource.apple.com/tarballs/objc4/
  * 在线浏览
    * https://opensource.apple.com/source/objc4/
      * 常用版本
        * https://opensource.apple.com/source/objc4/objc4-750/
        * https://opensource.apple.com/source/objc4/objc4-818.2/

具体例子：

* objc_retainAutoreleasedReturnValue + objc_autoreleaseReturnValue
  * https://opensource.apple.com/source/objc4/objc4-532.2/runtime/NSObject.mm
* objc_retainBlock
  * 相关源码：runtime/objc-arr.mm
    * 离线下载
      * https://opensource.apple.com/tarballs/objc4/objc4-493.9.tar.gz
    * 在线浏览
      * https://opensource.apple.com/source/objc4/objc4-493.9/runtime/objc-arr.mm.auto.html
* objc_alloc
  * https://opensource.apple.com/source/objc4/objc4-646/runtime/objc-internal.h
    ```c
    OBJC_EXPORT id objc_alloc(Class cls)
        __OSX_AVAILABLE_STARTING(__MAC_10_9, __IPHONE_7_0);

    OBJC_EXPORT id objc_allocWithZone(Class cls)
        __OSX_AVAILABLE_STARTING(__MAC_10_9, __IPHONE_7_0);
    ```
* objc_loadWeakRetained
  * https://opensource.apple.com/source/objc4/objc4-706/runtime/NSObject.mm.auto.html


## 可调试的objc runtime代码

看到一个经过别人整理，是可以运行和调试的objc runtime的代码：

[RetVal/objc-runtime: A debuggable objc runtime (github.com)](https://github.com/RetVal/objc-runtime)

如果以后需要，可以去尝试去编译和运行和调试

