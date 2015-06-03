##PullToRefreshListView：
### 简单实现下拉刷新
### 步骤
 1. 添加提示界面，即ListView的header头布局；
 2. 监听ListView滚动事件，即onScrollListener()事件：列表是否滑到最顶端firstVisibleItem
 3. 监听ListView的onTouch()事件：判断手势操作的Action
 4. 加载最新数据。

###隐藏header
* 如果不进行measureView()，则headerHeight = header.getMeasuredHeight()得到的高度为0；
* 测量 = 测量值 + 测量模式
* 测量模式：（3种）
     * **MeasureSpec.EXACTLY：精确尺寸，100dp，FILL_PARENT**
 	* **MeasureSpec.AT_MOST：最大尺寸，WRAP_CONTENT，控件大小一般随着控件的子空间或内容进行变化**
 	* **MeasureSpec.UNSPECIFIED：未指定尺寸，少见，一般都是父控件是AdapterView**


###自定义ViewGroup须覆写：
* onMeasure：测量子View的宽和高，设置自己的宽和高
* onLayout:设置子View的位置

###View的绘制流程：
* http://blog.csdn.net/qinjuning/article/details/7110211
* view.measure：这个方法是final类型的，也就是所有的子类都不能继承该方法，保证android初始化view的原理不变。
* view.onMeasure:真正的测量控件大小的方法，是由View的子类实现的，onMeasure是在measure方法中调用。

###onTouch()
* MotionEvent.ACTION_DOWN
* MotionEvent.ACTION_MOVE
* MotionEvent.ACTION_UP

###onMove() 
* state:NONE  PULL  RELESE  REFLASHING
