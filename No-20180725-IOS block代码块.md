IOS block代码块

1. 声明block变量的语法格式
>返回值类型 (^block变量名称)(参数列表);

```Objective-C
// 声明了1个叫做myBlock1的block类型的变量 该变量中只能存储没有返回值和参数的代码段
void (^myBlock1)();

// 声明myBlock2变量 只能存储没有参数且返回值类型为int的代码
int (^myBlock2)();

// 声明myBlock2变量 只能存储没有参数且返回值类型为int的代码
int (^myBlock3)(int num1, int num2);
```

2. block代码块语法格式
>^返回值类型(){
>    代码段;
>}

```Objective-C
^void(){
    NSLog(@"无参无返回值的代码块");
};

//代码块声明和赋值
void (^myBlock1)(void);
myBlock1 = ^void(){
    NSLog(@"无参无返回值代码块");
};

int (^myBlock2)(void);
myBlock2 = ^int(){
    int num = 3;
    return num;
};

int (^myBlock3)(int num1, int num2);
myBlock3 = ^int(int num1, int num2){
    int sum = num1 + num2;
    return sum;
};
```

3. 代码块调用格式
>block变量名();

```Objective-C
myBlock1();

int num = myBlock2();
NSLog(@"num=%d", num);

int sum = myBlock3(2, 3);
NSLog(@"sum=%d", sum);
```
