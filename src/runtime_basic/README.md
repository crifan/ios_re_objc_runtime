# Runtime基础知识

此处整理iOS的ObjC的Runtime的相关基础知识。

* ObjC Runtime
  * 官网文档
    * [Objective-C Runtime | Apple Developer Documentation](https://developer.apple.com/documentation/objectivec/objective-c_runtime?language=objc)
  * 概述
    * The Objective-C runtime is a runtime library that provides support for the dynamic properties of the Objective-C language, and as such is linked to by all Objective-C apps. Objective-C runtime library support functions are implemented in the shared library found at `/usr/lib/libobjc.A.dylib`.
    * You typically don't need to use the Objective-C runtime library directly when programming in Objective-C. This API is useful primarily for developing bridge layers between Objective-C and other languages, or for low-level debugging

TODO：

* 【整理】iOS运行时iOS Runtime基础知识
* 其他资料：
  * Swift & the Objective-C Runtime - NSHipster
    * [英文](https://nshipster.com/swift-objc-runtime/)
    * [中文](https://nshipster.cn/swift-objc-runtime/)

## load

TODO：

【未解决】iOS的ObjC基础知识：load方法

### __objc_classlist 和 __objc_nlcatlist

在`objc-file.mm`文件中存有以下定义

```c
// 类似于 C++ 的模板写法，通过宏来处理泛型操作
// 函数内容是从内存数据段的某个区下查询该位置的情况，并回传指针
#define GETSECT(name, type, sectname)                                   \
    type *name(const headerType *mhdr, size_t *outCount) {              \
        return getDataSection<type>(mhdr, sectname, nil, outCount);     \
    }                                                                   \
    type *name(const header_info *hi, size_t *outCount) {               \
        return getDataSection<type>(hi->mhdr(), sectname, nil, outCount); \
    }
// 根据 dyld 对 images 的解析来在特定区域查询内存
GETSECT(_getObjc2ClassList,           classref_t,      "__objc_classlist");
GETSECT(_getObjc2NonlazyCategoryList, category_t *,    "__objc_nlcatlist");
```

-> 才明白：

> `+ (void)load`
> 
> 对于每一个 Class 和 Category 来说，必定会调用此方法，而且仅调用一次。当包含 Class 和 Category 的程序库载入系统时，就会执行此方法，并且此过程通常是在程序启动的时候执行

->

* `__objc_classlist` ：`class`=`Class类`
* `__objc_nlcatlist`：`nlcat`=`Non Lazy Catetory`=`非懒加载的Category`

## iOS逆向技术：Method Swizzling

iOS逆向中的一种技术叫：`Method Swizzling`=`方法交换`，其底层就是利用了ObjC的Runtime的特性

TODO：

【记录】研究抖音越狱检测逻辑：iOS的ObjC的方法交换Method Swizzling

## 越狱检测和反越狱检测

TODO：

【已解决】iOS越狱检测和反越狱检测：iOS运行时iOS Runtime
