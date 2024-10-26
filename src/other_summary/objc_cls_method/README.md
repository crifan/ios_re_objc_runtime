# ObjC类的常用方法

* ObjC类的常用方法
  * 获取Class名字=类名
    * 概述
      * `NSStringFromClass(someClass)` => `NSString*`
      * `class_getName(someClass)` => `const char*`
      * `[someInstance className]` => `NSString*`
      * `object_getClassName(someId)` => `const char*`
    * 详解
      * [ObjC获取Class类名](../../other_summary/get_cls_name/README.md)
  * 获取父类
    * 概述
      * `[xxx superclass]`
      * `class_getSuperclass(xxx)`
    * 详解
      * [获取ObjC类的父类](../../other_summary/get_parent_cls.md)
  * 获取Class
    * 适用于=输入是：`char *`
      * `objc_getClass`
        * 定义：
          ```objc
          id objc_getClass(const char *name);
          ```
        * 含义
          * 传入参数：字符串=类名
          * 返回值：`Class`
        * 举例
          * 举例1
            ```bash
            (lldb) po object_getClass("YTNetworkRequestTrackerImpl")
            0x00000004654e5458
            ```
          * 举例2
            ```bash
            (lldb) expr id $protoClass = (id)objc_getClass("GPBMessage")
            (lldb) po $protoClass
            GPBMessage
            ```
          * 举例3
            ```bash
            (lldb) po [objc_getClass("GPBMessage") parseFromData: newHttpBodyData]
            <GPBMessage 0x287b4f4d0>: {
              # --- Unknown fields ---
              1: "\n\233\022\n\005zh-CN\022\002CNR\002CNb\005Applej\tiPhone9,1\200\001\005\212\001\007
              ...
            ```
          * 举例4
            ```bash
            Class LSApplicationProxy_class = object_getClass(@"LSApplicationProxy");
            ```
    * 适用于=输入是：id
      * `object_getClass`
        * 定义：
          ```objc
          Class object_getClass(id obj);
          ```
        * 含义
          * 传入参数：obj可能是instance对象、class对象、meta-class对象
          * 返回值
            * 如果是instance对象，返回class对象
            * 如果是class对象，返回meta-class对象
            * 如果是meta-class对象，返回NSObject（基类）的meta-class对象
    * 适用于=输入是：Instance=Object
      * class属性
        * 用法：
          ```objc
          [obj class]
          ```
        * 返回：`Class`
  * 判断是否是某个类
    * 适用于=输入是：`Instance`=`Object`
      * `isKindOfClass`
        * 定义
          * 针对`NSObject`的：
            ```objc
            - (BOOL)isKindOfClass:(Class)aClass;
            ```
        * 用法
          ```objc
          BOOL isSameClass = [someObjcInstance isKindOfClass: SomeClass]
          ```
