# objc_getClass

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