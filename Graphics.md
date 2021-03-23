# 绘制相关类

## Paint：画笔

### 常用方法：

```java
setColor(Color.BLUE);//设置颜色
setARGB(int a, int r, int g, int b);//设置ARGB值
setAlpha(255);//设置透明度
setStyle(Paint.Style.FILL);//设置样式，FILL、STROKE、FILE_AND_STROKE
setStrokeWidth(10);//设置画笔宽度
setStrokeCap(Paint.Cap.ROUND);//设置画笔端点的形状，ROUND(圆头)、BUTT(平头)、SQUARE(方头)
setStrokeJoin(Paint.Join.MITER);//设置拐角形状，MITER(尖角)、BEVEL(平角)、ROUND(圆角)
setAntiAlias(true);//打开抗锯齿，会损失一些性能
setLetterSpacing(10);//设置文字间距
setStrikeThruText(true);//设置删除线
setUnderlineText(true);//设置下划线
setTextSize(20);//设置文字大小
setTypeface(Typeface.BOLD);//设置字体类型,BOLD(粗体)、ITALIC(斜体)
setTextSkewX(-0.25f);//设置文字倾斜度
setTextAlign(Align.LEFT);//设置文字对齐方式,LEFT(左对齐)、CENTER(居中对齐)、RIGHT(右对齐)
breakText(String text, boolean measureForwards, float maxWidth, float[] measuredWidth);//测量文字宽度，text是要测量的文字；measureForwards表示文字的测量方向，true表示由左往右测量；maxWidth是给出的宽度上限；measuredWidth是用于接受数据赋值给measuredWidth[0]
getTextBounds(String text, int start, int end, Rect bounds);//获取文字的显示范围,text是要测量的文字，start和end分别是文字的起始和结束位置，bounds是存储文字显示范围的对象，测算完成会把结果写进 bounds
setColorFilter(ColorFilter filter);//设置颜色过滤，Matrix
setXfermode(Xfermode xfermode);//设置混合模式，PorterDuff.Mode
```

## Canvas：画布

### 常用方法：

```java
clipPath(Path path);//
clipPath(Path path, Region.Op op);//
clipRect(Rect rect);//
clipRect(Rect[F] rect, Region.Op op);//[]表示可选

save();//保存
restore();//恢复上一次保存前的状态

translate(float dx, float dy);//移动
scale(float sx, float sy);//缩放
scale (float sx, float sy, float px, float py);//缩放并平移
rotate(float degrees);//顺时针旋转
rotate(float degrees, float dx, float dy);//以某个点为基准顺时针旋转
skew(float sx, float sy);//画布倾斜，tan值

drawCircle(float cx, float cy, float radius, Paint paint);//画圆

drawArc(RectF oval, float startAngle, float sweepAngle, boolean useCenter,Paint paint);//画圆
drawArc(float left, float top, float right, float bottom, float startAngle, float sweepAngle, boolean useCenter, Paint paint);

drawBitmap(Bitmap bitmap, Matrix matrix, Paint paint);//画bitmap
drawBitmap(Bitmap bitmap, Rect src, RectF dst, Paint paint);
drawBitmap(Bitmap bitmap, float left, float top, Paint paint);
drawBitmapMesh(Bitmap bitmap, int meshWidth, int meshHeight, float[] verts, int vertOffset, int[] colors, int colorOffset, Paint paint);

drawColor(int color, PorterDuff.Mode mode);//画颜色
drawRGB(int r, int g, int b);

drawLine(float startX, float startY, float stopX, float stopY, Paint paint);//画线
drawLines(float[] pts,Paint paint);
drawLines(float[] pts, int offset, int count, Paint paint);

drawRect(float left, float top, float right, float bottom, Paint paint);//画矩形
drawRect(Rect r, Paint paint);
drawRect(RectF r, Paint paint);

drawRoundRect(RectF rect, float rx, float ry, Paint paint);//画圆角矩形
drawRoundRect(float left, float top, float right, float bottom, float rx, float ry, Paint paint);

drawOval(float left, float top, float right, float bottom, Paint paint);//画椭圆
drawOval(RectF oval, Paint paint);

drawPaint(Paint paint);//

drawPoint(float x, float y, Paint paint);
drawPoints(float[] pts, Paint paint);
drawPoints(float[] pts, int offset, int count, Paint paint);

drawText(String text, float x, float y, Paint paint);//画字符串
drawText(CharSequence text, int start, int end, float x, float y, Paint paint);
drawText(char[] text, int index, int count, float x, float y, Paint paint);
drawTextOnPath(String text, Path path, float hOffset, float vOffset, Paint paint);
drawTextOnPath(char[] text, int index, int count, Path path, float hOffset, float vOffset, Paint paint);
drawTextRun(CharSequence text, int start, int end, int contextStart, int contextEnd, float x, float y, boolean isRtl, Paint paint);
drawTextRun(char[] text, int index, int count, int contextIndex, int contextCount, float x, float y, boolean isRtl, Paint paint);
```



#### RenderNode：硬件加速节点

https://zhuanlan.zhihu.com/p/25477828

#### Matrix：矩阵

```java
//translate:平移
setTranslate(float dx, float dy)//dx表示x轴方向移动距离，dy表示y轴方向移动距离
preTranslate(float dx, float dy)
postTranslate(float dx, float dy)

//rotate:旋转
setRotate(float degrees)//degrees 旋转角度
setRotate(float degrees, float px, float py)//px py 旋转的支点（轴心点）
preRotate(float degrees)
preRotate(float degrees, float px, float py)
postRotate(float degrees)
postRotate(float degrees, float px, float py)

//scale:缩放
setScale(float sx, float sy)//sx、sy缩放倍数
setScale(float sx, float sy, float px, float py)//px py 旋转的支点（轴心点）
preScale(float sx, float sy)
preScale(float sx, float sy, float px, float py)
postScale(float sx, float sy)
postScale(float sx, float sy, float px, float py)

//skew:错切
setSkew(float kx, float ky)
setSkew(float kx, float ky, float px, float py)
preSkew(float kx, float ky)
preSkew(float kx, float ky, float px, float py)
postSkew(float kx, float ky)
postSkew(float kx, float ky, float px, float py)

//src 要缩放的源矩形
//dst 缩放后填充的目标矩形
//stf 填充的方式
setRectToRect(RectF src, RectF dst, ScaleToFit stf)

//矩形衔接
setConcat(Matrix a, Matrix b)
```



#### PixelFormat：像素格式

#### PorterDuff.Mode：是用来指定两个图像共同绘制时的颜色策略的

`PorterDuff.Mode` 一共有 17 个，可以分为两类：

1. Alpha 合成 (Alpha Compositing)
2. 混合 (Blending)

源图像和目标图像：

![img](https://wx3.sinaimg.cn/large/52eb2279ly1fig6ia1twgj20ds07tdgs.jpg)

第一类：Alpha 合成：

![img](https://wx3.sinaimg.cn/large/52eb2279ly1fig6im3hhcj20o50zt7bj.jpg)

第二类：混合:

![img](https://wx3.sinaimg.cn/large/52eb2279ly1fig6iw04v0j20ny0hzmzj.jpg)



#### Rect：矩形

#### Region：区域

#### Outline：