# objc_storeStrong

* 定义
  ```c
  void objc_storeStrong(id *object, id value);
  ```
* 说明
  * Precondition: object is a valid pointer to a __strong object which is adequately aligned for a pointer. value is null or a pointer to a valid object.
  * Performs the complete sequence for assigning to a __strong object of non-block type [*]. Equivalent to the following code:
* 代码实现
  ```c
  void objc_storeStrong(id *object, id value) {
    id oldValue = *object;
    value = [value retain];
    *object = value;
    [oldValue release];
  }
  ```

* > This does not imply that a __strong object of block type is an invalid argument to this function. Rather it implies that an objc_retain and not an objc_retainBlock operation will be emitted if the argument is a block.

相关理解：

* 在`Objective-C`中，对象的引用关系由引用修饰符来决定，如`__strong`、`__weak`、`__autorelease`等等，编译器会根据不同的修饰符生成不同逻辑的代码来管理内存。
  * 在`MRC`时代`Retain`修饰符将会使被引用的对象引用计数`+1`
  * 在`ARC`中`__strong`修饰符作为其替代者

在正向开发写代码，在给`__strong`变量赋值时

```c
obj = otherObj;
```

内部其实会调用对应的`runtime`的函数：

```c
// 会变成如下函数调用
objc_storeStrong(&obj, otherObj);
```
