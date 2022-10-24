# objc_msgSend

TODO：

* 【整理】iOS逆向开发心得：如何判断ObjC的objc_msgSend的参数个数
* 【已解决】Xcode的lldb调试iOS的ObjC或Swift时如何打印出objc_msgSend第一个参数是什么类的实例
* 【整理】ObjC底层函数：objc_msgSendSuper2、objc_msgSendSuper
* 【未解决】iOS逆向：如何找到objc_msgSendSuper2的第一个参数调用的是什么类
* 【基本解决】Xcode的lldb中动态调试objc_msgSend第一个参数self是哪个类
* 
* 【未解决】研究YouTube逻辑：谁调用了_dispatch_call_block_and_release以及_pthread_wqthread
* 【整理】iOS逆向调试心得：如何找到Block的_pthread_wqthread和_dispatch_call_block_and_release的函数调用最初来源
* 【整理】iOS逆向心得：ObjC函数调用时参数顺序和汇编代码中寄存器传递的参数顺序不一致

---

iOS逆向中，肯定会涉及到底层的ObjC的Runtime中，最重要的一个函数：`objc_msgSend`
