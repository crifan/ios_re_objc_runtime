# 自己组装出objc_msgSend

如果了解`objc_msgSend`底层的机制的话，普通的`objc_msgSend`的函数调用，也可以自己组装=生成出来，比如：

* [low-level objc runtime apis (github.com)](https://gist.github.com/TooTallNate/1073294/5d0cd61744358ae53660fbba6e7b301d20a52e3a)

```c
...
// Set up a NSString with the contents "Hello World" from a C string
Class nsstring = objc_getClass("NSString");
SEL stringUTF8sel = sel_registerName("stringWithUTF8String:"); 
id hello = objc_msgSend(nsstring, stringUTF8sel, "Hello World\n"); 
...
```
