# ObjC运行时概览

[iOS逆向](http://book.crifan.org/books/ios_reverse_dev/website)时，常会涉及到一些[iOS底层机制](https://book.crifan.org/books/ios_re_ios_internal/website/)，其中就包括，`ObjC`的`运行时`=`Runtime`。

iOS逆向期间涉及到的很多内容，都和Runtime有关：

* 逆向技术
  * Method Swizzling
    * 底层就依赖于Objc的Runtime机制
  * 导出头文件
    * 据说底层机制就依赖于ObjC的Runtime
      * 据说，如果代码换成Swift，就无法导出头文件
* 动态调试
  * 可以输出类的属性和函数
    * 底层就涉及到，Runtime中的`NSObject`、`isa`等内容
