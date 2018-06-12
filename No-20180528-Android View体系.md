### Android View体系

#### View类的继承结构

View类是所有控件类的基类，View和ViewGroup类都继承自View，布局类继承自ViewGroup类，一般控件继承自View类。

#### View坐标系

Android中有两种坐标系，Android坐标系和视图坐标系。

##### Android坐标系

Android坐标系以设备屏幕左上角为原点，原点以右为X轴，以下为Y轴。
常用API：
`getRawX()`:
`getRawY()`:

##### 视图坐标系

视图坐标系以父控件的左上角为原点。
常用API：

#### View的滑动

基本思想：当触摸事件传到View时，系统记下触摸点的坐标，手指移动时系统记下移动后的触摸的坐标并算出偏移量，并通过偏移量来修改View的坐标。

##### 六种滑动方式

1. 调用`layout()`方法重新放置控件的位置。
2. 和方法1类似，调用offsetLeftAndRight()与offsetTopAndBottom()
3. LayoutParams（改变布局参数）

```java
LinearLayout.LayoutParams layoutParams= (LinearLayout.LayoutParams) getLayoutParams();
layoutParams.leftMargin = getLeft() + offsetX;
layoutParams.topMargin = getTop() + offsetY;
setLayoutParams(layoutParams);
```

1. 动画
2. scollTo与scollBy
3. Scroller

#### View的事件分发机制

`dispatchTouchEvent(MotionEvent ev)`：用来进行事件的分发
`onInterceptTouchEvent(MotionEvent ev)`：用来进行事件的拦截，在dispatchTouchEvent()中调用，需要注意的是View没有提供该方法
`onTouchEvent(MotionEvent ev)`：用来处理点击事件，在dispatchTouchEvent()方法中进行调用

#### 参考文献：

[刘望舒的博客](http://liuwangshu.cn/tags/View%E4%BD%93%E7%B3%BB/)