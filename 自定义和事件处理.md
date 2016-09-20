# iOS应用的入口自定义和事件处理的自定义

````Objc
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    MWindow *window = [[MWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
    window.backgroundColor = [UIColor yellowColor];

    UIStoryboard *SB = [UIStoryboard storyboardWithName:@"Main" bundle:nil];
    UIViewController *vc = [SB instantiateInitialViewController];
    self.window = window;
    self.window.rootViewController = vc;
    [self.window makeKeyAndVisible];

    return YES;
}
  ````
这些方法的实现，可以实现事件处理者的自定义
````Objc
//找到事件的处理者  Application ---->window---->fitView
- (UIView *)hitTest:(CGPoint)point withEvent:(UIEvent *)event
{
// return [super hitTest:point withEvent:event];
    return self;
}
//判断点击点是不是在当前的响应者中
- (BOOL)pointInside:(CGPoint)point withEvent:(UIEvent *)event
{
 return YES;
}

- (void)touchesBegan:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event
{
    NSLog(@"%s",__func__);
}
  ````
