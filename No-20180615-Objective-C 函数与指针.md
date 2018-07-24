### Object-C 函数

#### 函数定义

Object-C中方法定义的一般形式如下：

```
- (return_type) method_name:( argumentType1 )argumentName1 
joiningArgument2:( argumentType2 )argumentName2 ... 
joiningArgumentn:( argumentTypen )argumentNamen 
{
   body of the function
}
```

1.方法修饰符 
- 代表此方法是实体方法，必须先生成类实例，通过实例才能调用该方法。
+ 代表此方法是类的静态方法，可以直接调用，而不用生成类实例。

[Ubuntu下如何安装并使用Objective-C](https://www.linuxidc.com/Linux/2015-12/126211.htm)