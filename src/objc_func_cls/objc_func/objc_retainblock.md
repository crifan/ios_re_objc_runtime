# objc_retainBlock

* `objc_retainBlock`
  * 概述
    * `objc_retainBlock`是和ObjC中的`Block`相关的函数
    * 和ARC中的引用计数中相关
  * 定义
    ```objc
    id objc_retainBlock(id value);
    ```
  * 常用逻辑=常用流程
    * Block初始化时，往往都是_NSConcreteStackBlock = Stack=栈 上的，然后被objc_retainBlock，从Stack上，copy拷贝到了 Heap堆上 NSConcreteMallocBlock
      * 即：在栈上创建block结构体对象，然后再通过Block_copy复制到堆上，然后把堆上的对象注册到自动释放池autoreleasepool中，同时返回这个堆上的对象

## 代码和实现

* 底层实现
  * 其实往往就是`Block_copy`
* 代码
  ```objc
  //
  // The -fobjc-arr flag causes the compiler to issue calls to objc_{retain/release/autorelease/retain_block}
  //

  id objc_retainBlock(id x) {
  #if ARR_LOGGING
      objc_arr_log("objc_retain_block", x);
      ++CompilerGenerated.blockCopies;
  #endif
      return (id)_Block_copy(x);
  }
  ```
* 相关源码
  * `runtime/objc-arr.mm`
    * 离线下载
      * https://opensource.apple.com/tarballs/objc4/objc4-493.9.tar.gz
    * 在线浏览
      * https://opensource.apple.com/source/objc4/objc4-493.9/runtime/objc-arr.mm.auto.html
