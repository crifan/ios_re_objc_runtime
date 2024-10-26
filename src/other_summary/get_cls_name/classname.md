# className

## 应用举例

### ACAccount

```asm
AppleMediaServices`+[AMSBagNetworkTask bagStorefrontForAccountMediaType:]:
    0x1864b051c <+0>:   pacibsp 
...
    0x1864b0580 <+100>: mov    x20, x0
    0x1864b0584 <+104>: adrp   x8, 289692
    0x1864b0588 <+108>: add    x1, x8, #0x7be            ; =0x7be 
    0x1864b058c <+112>: bl     0x182011dc8              ; symbol stub for: objc_msgSend
```

->

```bash
(lldb) reg r x0
      x0 = 0x000000028314d960
(lldb) po 0x000000028314d960
xxx@yyy.com (1xxxxFF-9xxE-4xxE-Axx2-02xxxxx57)

(lldb) po object_getClassName(0x000000028314d960)
0x0000000183ae4efc

(lldb) po (char*)object_getClassName(0x000000028314d960)
"ACAccount"

(lldb) po [0x000000028314d960 className]
ACAccount
```

### AADeviceInfo

```bash
(lldb) po (bool)[[$x0 className] isEqualToString: @"AADeviceInfo"]
true
```
