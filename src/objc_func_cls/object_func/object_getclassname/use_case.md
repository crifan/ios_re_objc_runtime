# 应用举例

## MLOnesieRequestContext

* 用lldb调试时，想要查看第一个参数是什么类：

```c
(lldb) reg r x0
      x0 = 0x000000028195ccc0
(lldb) po 0x000000028195ccc0
10764012736

(lldb) po (char*)object_getClassName(0x000000028195ccc0)
"MLOnesieRequestContext"
```

## YTGLUILabel

```c
(lldb) reg r x9 x10
      x9 = 0x000000010a43a000  (void *)0x000000010a509788: YTGLUILabel
     x10 = 0x0000000109375578  @"partid"
(lldb) po 0x000000010a43a000
4467171328

(lldb) po (char*)0x000000010a43a000
"\x88\x97P\n\U00000001"

(lldb) po object_getClassName(0x000000010a43a000)
0x00000001086535b5

(lldb) po (char*)object_getClassName(0x000000010a43a000)
"YTGLUILabel"
```

## `MonkeyDev`的`LLDBTools.m`

```c
NSString* choose(const char* classname){
    NSMutableString* result = [NSMutableString new];
    NSArray* results = choose_inner(classname);
    [result appendFormat:@"Find %lu instance objects in memory!\n" , (unsigned long)results.count];
    for (id item in results) {
        [result appendFormat:@"<%s: 0x%llx>\n", object_getClassName(item), (long long)item];
    }
    return result;
}
```

## __NSDictionaryI

```bash
_objc_msgSend(<AWEOnlineABTestManager: 0x283244ce0>, "abTestData”)
```

查看返回值：

```bash
(lldb) reg r x0
      x0 = 0x0000000128900000

(lldb) po (char*)object_getClassName(0x0000000128900000)
"__NSDictionaryI"
```
