##UIVisualEffectView
  - UIBlurEffect
     - 只支持到iOS 8.0+。系统给予的一个自动生成滤镜的方法

````Objc

 UIVisualEffectView *effectView = [[UIVisualEffectView alloc] initWithEffect:[UIBlurEffect effectWithStyle:UIBlurEffectStyleDark]];
 effectView.frame = img.bounds;
[img addSubview:effectView];

````
