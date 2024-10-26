# ObjC获取Class类名

iOS的获取ObjC类名，有几种方法：

## 概述

* 获取Class名字=类名
  * 方式
    * 适用于=当输入类型是：**Class**
      * `NSStringFromClass`
        * 返回：`NSString*`
      * `class_getName`
        * 返回：`const char*`
    * 适用于=当输入类型是：**Instance**
      * `[someInstance className]`
        * 返回：`NSString*`
    * 适用于=当输入类型是：**id**(`Class`/`Instance`/...)
      * `object_getClassName`
        * 返回：`const char*`

## 详解

* 适用于：**Class**
  * `NSStringFromClass`
    * 定义
      ```objc
      NSString * NSStringFromClass(Class aClass);
      ```
    * 举例
      ```bash
      (lldb) po NSStringFromClass($x0)
      _NSXPCConnectionExportInfo
      ```
  * `class_getName`
    * 定义：
      ```objc
      const char * class_getName(Class cls);
      ```
* 适用于：**Instance**=**Object**
  * `className`
    * 定义：
      ```objc
      @property(readonly, copy) NSString *className;
      ```
    * 举例
      * 当输入参数类型错误时，无法使用
        * 当前参数是Class=类，不是实例Instance，所以调用报错
          ```bash
          (lldb) po $x0
          _NSXPCConnectionExportInfo
          
          (lldb) po [$x0 className]
          error: Execution was interrupted, reason: Attempted to dereference an invalid ObjC Object or send it an unrecognized selector.
          The process has been returned to the state before expression evaluation.
          ```
* 适用于：**id**（`Class`/`Instance`/...）
  * `object_getClassName`
    * 定义
      ```objc
      const char * object_getClassName(id obj);
      ```
    * 举例
      * 举例1
        ```bash
        (lldb) po (char*)object_getClassName(0x0000000286379c00)
        "AWESearchUser"
        ```
      * 举例2
        ```bash
        (lldb) po 0x00000001341cc0e0
        <AWEInviteSearchViewController: 0x1341cc0e0>
        
        (lldb) po (char*)object_getClassName(0x00000001341cc0e0)
        "AWEInviteSearchViewController_Hmd_Prefix_"
        ```
      * 举例3
        ```bash
        (lldb) po (char*)object_getClassName(0x00000002813e74e0)
        "__NSDictionaryM"
        ```
      * 举例4
        ```bash
        (lldb) po object_getClassName($x0)
        0x00000001874cf168
        
        (lldb) po (char*)0x00000001874cf168
        "_NSXPCConnectionExportInfo"
        ```

## 使用举例

### AADeviceInfo

* objc_alloc_init的条件判断的断点的写法
  * 判断是否是类AADeviceInfo
    * 输入参数类型：Class
      * NSStringFromClass
        ```bash
        (bool)[NSStringFromClass($x0) isEqualToString: @"AADeviceInfo"]
        ```
      * class_getName
        ```bash
        (int)strcmp((char *)class_getName($x0),"AADeviceInfo")==0
        ```
      * object_getClassName
        ```bash
        (int)strcmp((char *)object_getClassName($x0),"AADeviceInfo")==0
        ```
