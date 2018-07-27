IOS NSString 与 NSData 互转

1. NSString 转 NSData
```Objective-C
NSData *data =[str dataUsingEncoding:NSUTF8StringEncoding];
```

2. NSData 转 NSString
```Objective-C
NSString * str  =[[NSString alloc] initWithData:data encoding:NSUTF8StringEncoding];
```