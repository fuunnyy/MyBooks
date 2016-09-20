##iOS反射机制：objc_property_t的使用

- 动态获取一个自定义类对象中的所有属性

````objc
- (NSDictionary *)allProperties
{
    NSMutableDictionary *props = [NSMutableDictionary dictionary];
    unsigned int outCount, i;
    objc_property_t *properties = class_copyPropertyList([self class], &outCount);
    for (i = 0; i<outCount; i++)
    {
        objc_property_t property = properties[i];
        const char *char_f =property_getName(property);
        NSString *propertyName = [NSString stringWithUTF8String:char_f];
        id propertyValue = [self valueForKey:(NSString *)propertyName];
        if (propertyValue)
            [props setObject:propertyValue forKey:propertyName];
    }
    free(properties);
    return props;
}
````

- 实现对象的自动赋值

````objc

- (BOOL)reflectDataFromOtherObject:(NSObject*)dataSource

{
    BOOL ret = NO;
    //propertyKeys 其实就是上面的方法的变形，上面方法回传一个可变字典，这里是得到一个可变数组的一个处理
    for (NSString *key in [self propertyKeys])
    {
    if ([dataSource isKindOfClass:[NSDictionary class]])
      {
    ret = ([dataSource valueForKey:key]==nil)?NO:YES;
      }
    else
      {
    ret = [dataSource  respondsToSelector:NSSelectorFromString(key)];
      }
    if (ret)
      {
    id propertyValue = [dataSource valueForKey:key];
    //该值不为NSNULL，并且也不为nil
    if (![propertyValue isKindOfClass:[NSNull class]] && propertyValue!=nil)
         {
    [self setValue:propertyValue forKey:key];
         }
       }
    }
return ret;
}

````
