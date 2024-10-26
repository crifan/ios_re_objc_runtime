# objc_opt_class

* `objc_opt_class`
  * 概述：`iOS`的`ObjC`的（内置 内部）函数，`ObjC`中 `[somObj class]`的内部具体实现用`objc_opt_class`
  * 具体实现原理：其实就是获取类，如果参数是对象则返回类，如果是类就返回类
    * The compiler translates `[SomeClass class]` method calls into a call to that function (when targeting the new OS). That function has a fast path when +class isn't overridden, improving performance and code size. Other objc_opt_* functions are similar.
  * iOS版本：`iOS 13.0+`

## 定义

* [objc-internal.h](https://opensource.apple.com/source/objc4/objc4-781/runtime/objc-internal.h.auto.html)

```c
OBJC_EXPORT Class _Nullable
objc_opt_class(id _Nullable obj)
        OBJC_AVAILABLE(10.15, 13.0, 13.0, 6.0, 5.0);
```

## 具体实现

[RetVal/objc-runtime: A debuggable objc runtime (github.com)](https://github.com/RetVal/objc-runtime)

```c
// Calls [obj class]
Class
objc_opt_class(id obj)
{
#if __OBJC2__
    if (slowpath(!obj)) return nil;
    Class cls = obj->getIsa();
    if (fastpath(!cls->hasCustomCore())) {
        return cls->isMetaClass() ? obj : cls;
    }
#endif
    return ((Class(*)(id, SEL))objc_msgSend)(obj, @selector(class));
}
```

可以看出：

在 `__OBJC2__` 中主要是通过 `getIsa()` 获取对象所属的 class，然后根据所属 cls 是否是 `meta class` 返回不同的 class。 如果是元类，则返回类对象本身，否则返回该对象所属的类。

