# 获取ObjC类的父类

对于一个ObjC的类（的实例）来说，想要获取其父类

* Xcode的lldb调试中
  * 方法1：`superclass`
    * 说明：推荐，更准确
    * 举例
      * 对于：
        ```bash
        (lldb) po 0x0000000281f086e0
        <__NSXPCInterfaceProxy_AKAppleIDAuthenticationDaemonProtocol: 0x281f086e0>
        ```
      * -》看不出具体是哪个类
      * -》去获取父类
        ```bash
        (lldb) po [0x281f086e0 superclass]
        _NSXPCDistantObject
        ```
  * 方法2：`class_getSuperclass`
    * 说明：不推荐，其是ObjC内部方法，不建议直接使用
    * 举例
      ```bash
      (lldb) po class_getSuperclass(0x281f086e0)
      <NSXPCConnection: 0x280d421c0> connection to service named com.apple.ak.auth.xpc
      ```
