# objc_getClass

TODO：

* 【无法解决】iOS越狱检测和反越狱检测：objc_getClass
*【整理】iOS运行时Runtime：objc_getClass相关函数

---

## hook代码

iOS逆向的动态调试时，底层写hook代码，往往会涉及到这个`objc_getClass`

```c
Class NSErrorClass = objc_getClass("NSError");
Class NSDictionaryClass = objc_getClass("NSDictionary");

// 写代码解析传入的变量，是什么类型，然后决定取出对应属性，即request url
//NSURL* getHamErrReqUrl(NSError* curError){
NSURL* getHamErrReqUrl(id erroOrDict){
    NSURL* curUrl = NULL;
//    if (curError) {
    if (erroOrDict) {
        NSDictionary* curUserInfo = NULL;
        if ([erroOrDict isKindOfClass: NSErrorClass]){
            curUserInfo = [erroOrDict userInfo];
        } else if ([erroOrDict isKindOfClass: NSDictionaryClass]) {
            curUserInfo = (NSDictionary*)erroOrDict;
        }

        if (curUserInfo) {
            id hamErrUrlReq = curUserInfo[@"HAMErrorURLRequest"];
            if (hamErrUrlReq != NULL) {
                BOOL isUrlReq = [hamErrUrlReq isKindOfClass: NSMutableURLRequestClass];
                if (isUrlReq) {
                    curUrl = [hamErrUrlReq URL];
                }
            }
        }
    }

    return curUrl;
}
```

## 心得

### Xcode的lldb中用objc_getClass如何获取到类名带括号的类

对于iOS的ObjC的定义：

```objc
#import <UIKit/UIImage.h>

@interface UIImage (AWEUserRecommend)
+ (id)awe_userRecommendImageNamed:(id)arg1 compatibleWithTraitCollection:(id)arg2;
+ (id)awe_userRecommendImageNamed:(id)arg1;
@end
```

想要查看类`UIImage(AWEUserRecommend)`的描述（属性、函数等）

不能用：

```bash
po [objc_getClass("UIImage(AWEUserRecommend)") _shortMethodDescription]
```

而是改用：

```
po [objc_getClass("UIImage") _shortMethodDescription]
```

因为

类名不是叫：`UIImage(AWEUserRecommend)` 或 `UIImage (AWEUserRecommend)`

而是：

此处是 继承自 UIImage的，和AWEUserRecommend相关的类

其真正的类名，还是叫：`UIImage`

所以直接用：

```bash
po [objc_getClass("UIImage") _shortMethodDescription]
```

即可。
