# UIView封装动画--iOS利用系统提供方法来做转场动画
````Objc
   UIViewAnimationOptions option;
    if (isNext) {
        option=UIViewAnimationOptionCurveLinear|UIViewAnimationOptionTransitionFlipFromRight;
    }else{
        option=UIViewAnimationOptionCurveLinear|UIViewAnimationOptionTransitionFlipFromLeft;
    }

    [UIView transitionWithView:_imageView duration:1.0 options:option animations:^{
        _imageView.image=[self getImage:isNext];
    } completion:nil];
````
关键方法：
````
(void)transitionFromView:(UIView *)fromView toView:(UIView *)toView duration:(NSTimeInterval)duration options:(UIViewAnimationOptions)options completion:(void (^)(BOOL finished))completion NS_AVAILABLE_IOS(4_0)
````
需要注意的是默认情况下转出的视图会从父视图移除，转入后重新添加，可以通过`UIViewAnimationOptionShowHideTransitionViews`参数设置，设置此参数后转出的视图会隐藏（不会移除）转入后再显示。并且这里不能再直接使用私有API了。
