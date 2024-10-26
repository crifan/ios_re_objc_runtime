# NSObject

TODO：

【整理】iOS逆向心得：Runtime运行时NSObject对象

---

此处介绍iOS的ObjC中和Runtime有关的：`NSObject`类相关的内容。

* `NSObject`
  * 概述
    * NSObject是所有ObjC类的根类
  * 特点
    * NSObject有各个类的通用的属性和函数

## NSObject的protocol定义和类本身定义

* 【已解决】iOS逆向：NSObject的定义
  * 协议=Protocol
    * NSObject-Protocol.h
      * [iOS-Header/14.5/PrivateFrameworks/CloudDocsDaemon.framework/NSObject-Protocol.h at master · xybp888/iOS-Header · GitHub](https://github.com/xybp888/iOS-Header/blob/master/14.5/PrivateFrameworks/CloudDocsDaemon.framework/NSObject-Protocol.h)
  * 类=Class
    * NSObject.h
      * [iOS-Runtime-Headers/lib/libobjc.A.dylib/NSObject.h at fbb634c78269b0169efdead80955ba64eaaa2f21 · nst/iOS-Runtime-Headers · GitHub](https://github.com/nst/iOS-Runtime-Headers/blob/fbb634c78269b0169efdead80955ba64eaaa2f21/lib/libobjc.A.dylib/NSObject.h)

## 心得

### 调试时看到的类的名称和正向开发时所用的类名不一样

比如：

* 正向开发时写的类名是：`NSDictionary`
* 逆向调试时看到的类名是：`__NSDictionaryM`

具体解释，详见：

TODO：

【整理】iOS逆向心得：调试时看到的ObjC的底层数据类型和上层类型的对应关系
