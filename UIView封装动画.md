# UIView封装动画--iOS利用系统提供方法来做关键帧动画
ios7以后才有用。
````Objc
    /*关键帧动画
     options:UIViewKeyframeAnimationOptions类型
     */
    [UIView animateKeyframesWithDuration:5.0 delay:0 options: UIViewAnimationOptionCurveLinear| UIViewAnimationOptionCurveLinear animations:^{
        //第二个关键帧（准确的说第一个关键帧是开始位置）:从0秒开始持续50%的时间，也就是5.0*0.5=2.5秒
        [UIView addKeyframeWithRelativeStartTime:0.0 relativeDuration:0.5 animations:^{
            _imageView.center=CGPointMake(80.0, 220.0);
        }];
        //第三个关键帧，从0.5*5.0秒开始，持续5.0*0.25=1.25秒
        [UIView addKeyframeWithRelativeStartTime:0.5 relativeDuration:0.25 animations:^{
            _imageView.center=CGPointMake(45.0, 300.0);
        }];
        //第四个关键帧：从0.75*5.0秒开始，持所需5.0*0.25=1.25秒
        [UIView addKeyframeWithRelativeStartTime:0.75 relativeDuration:0.25 animations:^{
            _imageView.center=CGPointMake(55.0, 400.0);
        }];

    } completion:^(BOOL finished) {
        NSLog(@"Animation end.");
    }];

````
#####options可以分为两类
对于关键帧动画也有一些动画参数设置options，UIViewKeyframeAnimationOptions类型，和上面基本动画参数设置有些差别，关键帧动画设置参数分为两类，可以组合使用：
- 常规动画属性设置（可以同时选择多个进行设置）

   UIViewAnimationOptionLayoutSubviews：动画过程中保证子视图跟随运动。

   UIViewAnimationOptionAllowUserInteraction：动画过程中允许用户交互。

   UIViewAnimationOptionBeginFromCurrentState：所有视图从当前状态开始运行。

   UIViewAnimationOptionRepeat：重复运行动画。

   UIViewAnimationOptionAutoreverse ：动画运行到结束点后仍然以动画方式回到初始点。

   UIViewAnimationOptionOverrideInheritedDuration：忽略嵌套动画时间设置。

   UIViewAnimationOptionOverrideInheritedOptions ：不继承父动画设置或动画类型。

- 动画模式设置（同前面关键帧动画动画模式一一对应，可以从其中选择一个进行设置）

   UIViewKeyframeAnimationOptionCalculationModeLinear：连续运算模式。

   UIViewKeyframeAnimationOptionCalculationModeDiscrete ：离散运算模式。

   UIViewKeyframeAnimationOptionCalculationModePaced：均匀执行运算模式。

   UIViewKeyframeAnimationOptionCalculationModeCubic：平滑运算模式。

   UIViewKeyframeAnimationOptionCalculationModeCubicPaced：平滑均匀运算模式。

注意：关键帧动画有两种形式，属性值关键帧动画，路径关键帧动画目前UIView还不支持。
