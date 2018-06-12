### Android运行时权限
#### 权限分类：普通权限和危险权限

#### 如何动态申请权限
1. 判断是否拥有该权限
checkSelfPermission方法用于检测当前应用是否分配了所需的权限，使用代码如下：
```java
if (ContextCompat.checkSelfPermission(getActivity(), Manifest.permission.READ_PHONE_STATE)
                    != PackageManager.PERMISSION_GRANTED) {
    // 未分配该权限，则申请权限
    ...
} else {
    // 已分配，进行相应操作
    ...
}
```

1. 如何申请权限
```java
ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.READ_PHONE_STATE}, REQUEST_CODE);
```

1. 申请权限回调
当系统弹出的权限申请框消失后，系统会调用onRequestPermissionsResult方法，可在此方法中进行一些后续处理，代码如下
```java
@Override
public void onRequestPermissionsResult(int requestCode, String permissions[], int[] grantResults) {
    switch (requestCode) {
        case REQUEST_CODE:
            // If request is cancelled, the result arrays are empty.
            if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {

                // permission was granted, yay! Do the
                // contacts-related task you need to do.
                ...
            } else {

                // permission denied, boo! Disable the
                // functionality that depends on this permission.
                Toast.makeText(getActivity(), "请前往设置打开相机权限！", Toast.LENGTH_LONG).show();
            }
            break;
    }
}
```

1. 用户拒绝分配权限

Android原生系统中，如果第二次弹出权限申请的对话框，会出现“以后不再弹出”的提示框，如果用户勾选了，你再申请权限，则shouldShowRequestPermissionRationale返回true，意思是说要给用户一个解释，告诉用户为什么要这个权限。然而，在实际开发中，需要注意的是，很多手机对原生系统做了修改，比如小米，小米4的6.0的shouldShowRequestPermissionRationale 就一直返回false，而且在申请权限时，如果用户选择了拒绝，则不会再弹出对话框了。。。。 所以说这个地方有坑，可以在回调里面处理，如果用户拒绝了这个权限，则打开本应用信息界面，由用户自己手动开启这个权限。


#### 遇到的问题
Android 6.0 运行时在Fragment中申请权限无法回调 问题

#### 解决方案： 
在Fragment中申请权限，不要使用ActivityCompat.requestPermissions，直接使用Fragment的requestPermissions方法，否则在Fragment中无法回调onRequestPermissionsResult

https://blog.csdn.net/jimtrency/article/details/54012444