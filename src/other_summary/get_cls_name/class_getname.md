# class_getName

## 应用举例

### lldb调试

lldb中给objc_alloc_init加上带条件判断的（之前用Xcode是可以正常去调试且能触发断点的）断点：

```bash
br s -n "objc_alloc_init" -c '(bool)[NSStringFromClass($x0) isEqualToString: @"AADeviceInfo"]'

br s -n "objc_alloc_init" -c '(int)strcmp((char *)class_getName($x0),"AADeviceInfo")==0'
```

### AWESearchUser

```bash
(lldb) po (char*)class_getName(0x000000010589f370)
"AWESearchUser"
```

### xyq_bundleAllClassesInfo

```objc
///获取当前工程下所有类（含系统类、cocoPods类）
+ (NSArray <NSString *> *)xyq_bundleAllClassesInfo {
...
        Class class = classes[index];
        NSString *className = [[NSString alloc] initWithUTF8String: class_getName(class)];
...
}
```
