# CALayer的使用

在我的理解中CALayer就是iOS中利用图层精简非交互式绘图。那么那些核心动画类。也就是变化图层的非交互式绘制规则而已。其中的本质就是将CALayer中的内容转化为map图。从而能够获取到硬件的操作。CALayer是**QuartzCore**框架下的。

 - 隐式动画属性 `CALayer`很多属性的改变都能形成动画效果，隐式动画属性。

#####属性:说明(是否支持隐式动画)
- anchorPoint是和中心点position重合的一个点，称为“锚点”，锚点的描述是相对于x、y位置比例而言的默认在图像中心点(0.5,0.5)的位置	            是
- backgroundColor	图层背景颜色	是
- borderColor	边框颜色	是
- borderWidth	边框宽度	是
- bounds	图层大小	是
- contents	图层显示内容，例如可以将图片作为图层内容显示	是
- contentsRect	图层显示内容的大小和位置	是
- cornerRadius	圆角半径	是
- doubleSided	图层背面是否显示，默认为YES	否
- frame	图层大小和位置，不支持隐式动画，所以CALayer中很少使用frame，通常使用bounds和position代替	否
- hidden	是否隐藏	是
- mask	    图层蒙版	是
- maskToBounds	子图层是否剪切图层边界，默认为NO	是
- opacity	透明度 ，类似于UIView的alpha	是
- position	图层中心点位置，类似于UIView的center	是
- shadowColor	阴影颜色	是
- shadowOffset	阴影偏移量	是
- shadowOpacity	阴影透明度，注意默认为0，如果设置阴影必须设置此属性	是
- shadowPath	阴影的形状	是
- shadowRadius	阴影模糊半径	是
- sublayers	子图层	是
- sublayerTransform	子图层形变	是
- transform	图层形变

