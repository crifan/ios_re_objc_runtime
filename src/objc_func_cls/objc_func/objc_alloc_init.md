# objc_alloc_init

* `objc_alloc_init`
  * 函数定义
    ```objc
    id objc_alloc_init(Class cls)
    ```
  * 底层实现过程
    * 先`alloc`再`init`
      ```objc
      [[xxx alloc] init]
      ```
    * `iOS 15`中，调试出的内部主要实现逻辑
      * 先：`_objc_rootAllocWithZone`
      * 再：`[xxx init]`
      * 最后再去：`[NSMutableArray alloc]`

## 反汇编代码

`iOS 15`中`objc_alloc_init`的反汇编代码实现：

```asm
libobjc.A.dylib`objc_alloc_init:
->  0x19cbd3c3c <+0>:  stp    x29, x30, [sp, #-0x10]!
    0x19cbd3c40 <+4>:  mov    x29, sp
    0x19cbd3c44 <+8>:  cbz    x0, 0x19cbd3c5c          ; <+32>
    0x19cbd3c48 <+12>: ldr    x8, [x0]
    0x19cbd3c4c <+16>: and    x8, x8, #0xffffffff8
    0x19cbd3c50 <+20>: ldrb   w8, [x8, #0x1d]
    0x19cbd3c54 <+24>: tbz    w8, #0x6, 0x19cbd3c6c     ; <+48>
    0x19cbd3c58 <+28>: bl     0x19cbd0134              ; _objc_rootAllocWithZone
    0x19cbd3c5c <+32>: adrp   x8, 368761
    0x19cbd3c60 <+36>: ldr    x1, [x8, #0x188]
    0x19cbd3c64 <+40>: ldp    x29, x30, [sp], #0x10
    0x19cbd3c68 <+44>: b      0x19cbcd000              ; objc_msgSend
    0x19cbd3c6c <+48>: adrp   x8, 14396
    0x19cbd3c70 <+52>: add    x1, x8, #0xeda
    0x19cbd3c74 <+56>: bl     0x19cbcd000              ; objc_msgSend
    0x19cbd3c78 <+60>: b      0x19cbd3c5c              ; <+32>
```
