# NSObject.h

* `NSObject.h`
  * 源码
    * [iOS-Runtime-Headers/lib/libobjc.A.dylib/NSObject.h at fbb634c78269b0169efdead80955ba64eaaa2f21 · nst/iOS-Runtime-Headers · GitHub](https://github.com/nst/iOS-Runtime-Headers/blob/fbb634c78269b0169efdead80955ba64eaaa2f21/lib/libobjc.A.dylib/NSObject.h)

## `UIKitCore`

* `NSObject.h`（好像是）所属Framework是
  * `UIKitCore`
    * 概述：UIKitCore是iOS中的其中一个Private的Framework
      * 详见
        * [iOS逆向：Framework动态库](https://book.crifan.org/books/ios_re_framework_dylib/website/)
    * 具体位置：`/System/Library/PrivateFrameworks/UIKitCore.framework/UIKitCore`

## `NSObject.h`的内容

```c
// Image: /System/Library/PrivateFrameworks/UIKitCore.framework/UIKitCore


+ (long long)__accessibilityGuidedAccessRestrictionStateForIdentifier:(id)arg1;
+ (bool)__accessibilityGuidedAccessStateEnabled;
+ (void)__accessibilityRequestGuidedAccessSession:(bool)arg1 completion:(id /* block */)arg2;
+ (void)_installAppearanceSwizzlesForSetter:(id)arg1;


- (id)_NSItemProviderTypeCoercion_coercedUIImageValueFromNSDataValue:(id)arg1 error:(id*)arg2;
- (id)_NSItemProviderTypeCoercion_coercedUIImageValueFromNSURLValue:(id)arg1 error:(id*)arg2;
- (id)__autorotationSanityCheckObjectFromSource:(id)arg1 selector:(SEL)arg2;
- (id)__ivarDescriptionForClass:(Class)arg1;
- (id)__methodDescriptionForClass:(Class)arg1;
- (id)__propertyDescriptionForClass:(Class)arg1;
- (id)__ui_performAsyncSelector:(SEL)arg1 type:(long long)arg2 sender:(id)arg3 completionHandler:(id /* block */)arg4;
- (void)_accessibilityFinalize;
- (void)_applyTraitStorageRecordsForTraitCollection:(id)arg1;
- (void)_connectInterfaceBuilderEventConnection:(id)arg1;
- (id)_internalAccessibilityAttributedHint;
- (id)_internalAccessibilityAttributedLabel;
- (id)_internalAccessibilityAttributedValue;
- (void)_internalSetAccessibilityAttributedHint:(id)arg1;
- (void)_internalSetAccessibilityAttributedLabel:(id)arg1;
- (void)_internalSetAccessibilityAttributedValue:(id)arg1;
- (id)_ivarDescription;
- (id)_methodDescription;
- (id)_propertyDescription;
- (void)_setTraitStorageList:(id)arg1;
- (id)_shortMethodDescription;
- (id)_traitStorageList;
- (id)_ui_descriptionBuilder;
- (void)_uikit_applyValueFromTraitStorage:(id)arg1 forKeyPath:(id)arg2;
- (id)_uikit_valueForTraitCollection:(id)arg1;
- (bool)_uikit_variesByTraitCollections;
- (bool)accessibilityActivate;
- (struct CGPoint { double x1; double x2; })accessibilityActivationPoint;
- (id)accessibilityAssistiveTechnologyFocusedIdentifiers;
- (id)accessibilityAttributedHint;
- (id)accessibilityAttributedLabel;
- (id)accessibilityAttributedValue;
- (id)accessibilityContainer;
- (long long)accessibilityContainerType;
- (id)accessibilityCustomActions;
- (id)accessibilityCustomRotors;
- (void)accessibilityDecrement;
- (id)accessibilityDragSourceDescriptors;
- (id)accessibilityDropPointDescriptors;
- (id)accessibilityElementAtIndex:(long long)arg1;
- (long long)accessibilityElementCount;
- (void)accessibilityElementDidBecomeFocused;
- (void)accessibilityElementDidLoseFocus;
- (bool)accessibilityElementIsFocused;
- (id)accessibilityElements;
- (bool)accessibilityElementsHidden;
- (struct CGRect { struct CGPoint { double x_1_1_1; double x_1_1_2; } x1; struct CGSize { double x_2_1_1; double x_2_1_2; } x2; })accessibilityFrame;
- (id)accessibilityHeaderElements;
- (id)accessibilityHint;
- (id)accessibilityIdentification;
- (id)accessibilityIdentifier;
- (void)accessibilityIncrement;
- (id)accessibilityLabel;
- (id)accessibilityLanguage;
- (id)accessibilityLocalizedStringKey;
- (long long)accessibilityNavigationStyle;
- (id)accessibilityPath;
- (bool)accessibilityPerformEscape;
- (bool)accessibilityPerformMagicTap;
- (bool)accessibilityScroll:(long long)arg1;
- (void)accessibilitySetIdentification:(id)arg1;
- (unsigned long long)accessibilityTraits;
- (id)accessibilityValue;
- (bool)accessibilityViewIsModal;
- (void)awakeFromNib;
- (id)className;
- (unsigned long long)defaultAccessibilityTraits;
- (long long)indexOfAccessibilityElement:(id)arg1;
- (bool)isAccessibilityElement;
- (bool)isAccessibilityElementByDefault;
- (bool)isElementAccessibilityExposedToInterfaceBuilder;
- (void)prepareForInterfaceBuilder;
- (void)setAccessibilityActivationPoint:(struct CGPoint { double x1; double x2; })arg1;
- (void)setAccessibilityAttributedHint:(id)arg1;
- (void)setAccessibilityAttributedLabel:(id)arg1;
- (void)setAccessibilityAttributedValue:(id)arg1;
- (void)setAccessibilityContainer:(id)arg1;
- (void)setAccessibilityContainerType:(long long)arg1;
- (void)setAccessibilityCustomActions:(id)arg1;
- (void)setAccessibilityCustomRotors:(id)arg1;
- (void)setAccessibilityDragSourceDescriptors:(id)arg1;
- (void)setAccessibilityDropPointDescriptors:(id)arg1;
- (void)setAccessibilityElements:(id)arg1;
- (void)setAccessibilityElementsHidden:(bool)arg1;
- (void)setAccessibilityFrame:(struct CGRect { struct CGPoint { double x_1_1_1; double x_1_1_2; } x1; struct CGSize { double x_2_1_1; double x_2_1_2; } x2; })arg1;
- (void)setAccessibilityHeaderElements:(id)arg1;
- (void)setAccessibilityHint:(id)arg1;
- (void)setAccessibilityIdentifier:(id)arg1;
- (void)setAccessibilityLabel:(id)arg1;
- (void)setAccessibilityLanguage:(id)arg1;
- (void)setAccessibilityNavigationStyle:(long long)arg1;
- (void)setAccessibilityPath:(id)arg1;
- (void)setAccessibilityTraits:(unsigned long long)arg1;
- (void)setAccessibilityValue:(id)arg1;
- (void)setAccessibilityViewIsModal:(bool)arg1;
- (void)setIsAccessibilityElement:(bool)arg1;
- (void)setShouldGroupAccessibilityChildren:(bool)arg1;
- (bool)shouldGroupAccessibilityChildren;
- (id)storedAccessibilityActivationPoint;
- (id)storedAccessibilityContainerType;
- (id)storedAccessibilityElementsHidden;
- (id)storedAccessibilityFrame;
- (id)storedAccessibilityNavigationStyle;
- (id)storedAccessibilityTraits;
- (id)storedAccessibilityViewIsModal;
- (id)storedIsAccessibilityElement;
- (id)storedShouldGroupAccessibilityChildren;
```
