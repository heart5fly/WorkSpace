# 绘制相关类

## Paint：画笔

### 常用方法：

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawCircle(170, 1500, 150, mPaint);
    mPaint.setColor(Color.RED);
    canvas.drawCircle(520, 1500, 150, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置透明度

setAlpha(int alpha);

alpha取值范围：0~255

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.RED);
    canvas.drawCircle(170, 1500, 150, mPaint);
    mPaint.setAlpha(30);
    canvas.drawCircle(520, 1500, 150, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置ARGB值

setARGB(int a, int r, int g, int b);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawCircle(170, 1500, 150, mPaint);
    mPaint.setARGB(30, 255, 0, 0);
    canvas.drawCircle(520, 1500, 150, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>



#### 设置画笔宽度

setStrokeWidth(int width);

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.GREEN);
    canvas.drawLine(20, 1900, 1060, 1900, mPaint);
    mPaint.setStrokeWidth(20);
    canvas.drawLine(20, 2030, 1060, 2030, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置样式

setStyle(Paint.Style style);

共三种样式：FILL、STROKE、FILE_AND_STROKE

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.RED);
    mPaint.setStrokeWidth(50);
    mPaint.setStyle(Paint.Style.FILL);
    canvas.drawCircle(170, 1880, 150, mPaint);
    mPaint.setStyle(Paint.Style.STROKE);
    canvas.drawCircle(520, 1880, 150, mPaint);
    mPaint.setStyle(Paint.Style.FILL_AND_STROKE);
    canvas.drawCircle(880, 1880, 150, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置画笔端点的形状

setStrokeCap(Paint.Cap cap);

共三种形状：ROUND(圆头)、BUTT(平头)、SQUARE(方头)

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.GREEN);
    mPaint.setStrokeWidth(50);
    canvas.drawLine(50, 900, 760, 900, mPaint);
    mPaint.setStrokeCap(Paint.Cap.ROUND);
    canvas.drawLine(50, 1030, 760, 1030, mPaint);
    mPaint.setStrokeCap(Paint.Cap.BUTT);
    canvas.drawLine(50, 1160, 760, 1160, mPaint);
    mPaint.setStrokeCap(Paint.Cap.SQUARE);
    canvas.drawLine(50, 1290, 760, 1290, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置拐角形状

setStrokeJoin(Paint.Join join);

共三种形状：MITER(尖角)、BEVEL(平角)、ROUND(圆角)

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setStyle(Paint.Style.STROKE);
    mPaint.setStrokeWidth(50);
    mPaint.setColor(Color.GREEN);

    mPath.moveTo(50, 300);
    mPath.lineTo(500, 300);
    mPath.lineTo(200, 450);
    canvas.drawPath(mPath, mPaint);
    
    mPaint.setStrokeJoin(Paint.Join.MITER);
    mPath.reset();
    mPath.moveTo(50, 500);
    mPath.lineTo(500, 500);
    mPath.lineTo(200, 650);
    canvas.drawPath(mPath, mPaint);
    
    mPaint.setStrokeMiter(50);//设置MITER型拐角的延长线的最大值
    mPath.reset();
    mPath.moveTo(50, 700);
    mPath.lineTo(500, 700);
    mPath.lineTo(200, 850);
    canvas.drawPath(mPath, mPaint);
    
    mPaint.setStrokeJoin(Paint.Join.BEVEL);
    mPath.reset();
    mPath.moveTo(50, 900);
    mPath.lineTo(500, 900);
    mPath.lineTo(200, 1050);
    canvas.drawPath(mPath, mPaint);
    
    mPaint.setStrokeJoin(Paint.Join.ROUND);
    mPath.reset();
    mPath.moveTo(50, 1100);
    mPath.lineTo(500, 1100);
    mPath.lineTo(200, 1250);
    canvas.drawPath(mPath, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置抗锯齿

setAntiAlias(boolean aa);

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.RED);
    canvas.drawCircle(170, 1500, 150, mPaint);
    mPaint.setAntiAlias(true);
    canvas.drawCircle(520, 1500, 150, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置文字大小

setTextSize(float textSize);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawText(mDescription, 100, 500, mPaint);
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 600, mPaint);
    mPaint.setAntiAlias(true);
    canvas.drawText(mDescription, 100, 750, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置文字间距

setLetterSpacing(float letterSpacing);

左右间距，文字本身宽度的倍数，默认是0

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    mPaint.setLetterSpacing(0.5f);
    canvas.drawText(mDescription, 100, 650, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置删除线

setStrikeThruText(boolean strikeThruText);

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    mPaint.setStrikeThruText(true);
    canvas.drawText(mDescription, 100, 650, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置下划线

setUnderlineText(boolean underlineText);

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    mPaint.setUnderlineText(true);
    canvas.drawText(mDescription, 100, 650, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置字体类型

setTypeface(Typeface typeface);

系统提供了5种字体：DEFAULT、DEFAULT_BOLD、SANS_SERIF、SERIF、MONOSPACE

还有3种常见字体类型：BOLD(粗体)、ITALIC(斜体)、BOLD_ITALIC(粗斜体)

可以组合5种系统和3种常见类型创建组合类型字体

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    mPaint.setTypeface(Typeface.DEFAULT_BOLD);
    canvas.drawText(mDescription, 100, 650, mPaint);
    mPaint.setTypeface(Typeface.SANS_SERIF);
    canvas.drawText(mDescription, 100, 800, mPaint);
    mPaint.setTypeface(Typeface.SERIF);
    canvas.drawText(mDescription, 100, 950, mPaint);
    mPaint.setTypeface(Typeface.MONOSPACE);
    canvas.drawText(mDescription, 100, 1100, mPaint);
    
    Typeface bold = Typeface.create(Typeface.DEFAULT, Typeface.BOLD);
    mPaint.setTypeface(bold);
    canvas.drawText(mDescription, 100, 1300, mPaint);
    Typeface italic = Typeface.create(Typeface.DEFAULT, Typeface.ITALIC);
    mPaint.setTypeface(italic);
    canvas.drawText(mDescription, 100, 1450, mPaint);
    Typeface boldItalic = Typeface.create(Typeface.DEFAULT, Typeface.BOLD_ITALIC);
    mPaint.setTypeface(boldItalic);
    canvas.drawText(mDescription, 100, 1600, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置文字倾斜度

setTextSkewX(float skewX);

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    mPaint.setTextSkewX(-0.25f);
    canvas.drawText(mDescription, 100, 650, mPaint);
    mPaint.setTextSkewX(0.25f);
    canvas.drawText(mDescription, 100, 800, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置文字对齐方式

setTextAlign(Paint.Align align);

共三种：LEFT(左对齐)、CENTER(居中对齐)、RIGHT(右对齐)

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    mPaint.setTextAlign(Paint.Align.LEFT);
    canvas.drawText(mDescription, 100, 650, mPaint);
    mPaint.setTextAlign(Paint.Align.CENTER);
    canvas.drawText(mDescription, 100, 800, mPaint);
    mPaint.setTextAlign(Paint.Align.RIGHT);
    canvas.drawText(mDescription, 100, 950, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 测量文字宽度

int breakText(String text, boolean measureForwords, float maxWidth, float[] measuredWidth);

text 是要测量的文字；

measureForwards 表示文字的测量方向，true表示由左往右测量；

maxWidth 是给出的宽度上限；

measureWidth 是用于接受宽度数据，赋值给measuredWidth[0]；

返回值为测量的文字个数

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    
    int width = mPaint.breakText(mDescription, true, 200, mMeasureWidth);
    canvas.drawText(String.valueOf(width), 100, 650, mPaint);
    canvas.drawText(String.valueOf(mMeasureWidth[0]), 100, 800, mPaint);
    
    int widthLarge = mPaint.breakText(mDescription, true, 2000, mMeasureWidth);
    canvas.drawText(String.valueOf(widthLarge), 100, 1000, mPaint);
    canvas.drawText(String.valueOf(mMeasureWidth[0]), 100, 1150, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 获取文字的显示范围

getTextBounds(String text, int start, int end, Rect bounds);

text 是要测量的文字；

start和end 分别是文字的起始和结束位置；

bounds是存储文字显示范围的对象，测量后会把结果写进bounds

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setTextSize(100);
    canvas.drawText(mDescription, 100, 500, mPaint);
    Rect bounds = new Rect();
    mPaint.getTextBounds(mDescription, 0, 3, bounds);
    canvas.save();
    mPaint.setColor(Color.RED);
    mPaint.setStyle(Paint.Style.STROKE);
    canvas.translate(100, 500);
    canvas.drawRect(bounds, mPaint);
    canvas.restore();
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色过滤

setColorFilter(ColorFilter filter);

ColorFilter有三个子类：

**ColorMatrixColorFilter**

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 10, 10, mPaint);
    ColorMatrix colorMatrix = new ColorMatrix(
        new float[]{
            1/2f,1/2f,1/2f,0,0,
            1/3f,1/3f,1/3f,0,0,
            1/4f,1/4f,1/4f,0,0,
            0,0,0,0,0
        }
    );
    mPaint.setColorFilter(new ColorMatrixColorFilter(colorMatrix));
    canvas.drawBitmap(mBitmap, 900, 10, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

**LightingColorFilter**

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 10, 10, mPaint);
    mPaint.setColorFilter(new LightingColorFilter(0xffffff, 0x0000f0));
    canvas.drawBitmap(mBitmap, 900, 10, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

**PorterDuffColorFilter**

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 10, 10, mPaint);
    mPaint.setColorFilter(new PorterDuffColorFilter(Color.GREEN, PorterDuff.Mode.MULTIPLY));
    canvas.drawBitmap(mBitmap, 900, 10, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置混合模式

setXfermode(Xfermode xfermode);

Xfermode共三个子类

<center><img src=./img/setcolor.png width=500/></center>

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawCircle(500, 450, 400, mPaint);
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    canvas.drawCircle(1350, 410, 400, mPaint);
    mPaint.setXfermode(new PorterDuffXfermode(PorterDuff.Mode.SRC_IN);
    canvas.drawBItmap(mBitmap, 950, 0, mPaint);
    mPaint.setXfermode(null);
}
```

注：绘制之前要禁用硬件加速：setLayerType(View.LAYER_TYPE_SOFTWARE, null);

**效果图**

<center><img src=./img/setcolor.png width=500/></center>



## Canvas：画布

#### 保存&恢复画布状态

save();//保存

restore();//恢复上一次保存前的状态

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.save();
    canvas.clipRect(50, 50, 600, 600);
    mPaint.setColor(Color.GREEN);
    canvas.drawPaint(mPaint);
    canvas.restore();
    canvas.save();
    canvas.clipRect(300, 300, 800, 800);
    mPaint.setColor(Color.BLUE);
    canvas.drawPaint(mPaint);
    canvas.restore();
    
    canvas.clipRect(1050, 50, 1600, 600);
    mPaint.setColor(Color.GREEN);
    canvas.drawPaint(mPaint);
    canvas.clipRect(1300, 300, 1800, 800);
    mPaint.setColor(Color.BLUE);
    canvas.drawPaint(mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 裁剪

clipPath(Path path);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    mPath.addCircle(1350, 410, 400, Path.Direction.CCW);//CW顺时针绘制，CCW逆时针绘制
    canvas.save();
    canvas.clipPath(mPath);
    canvas.drawBitmap(mBitmap, 950, 0, mPaint);
    canvas.restore();
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

clipRect(Rect rect);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    Rect rect = new Rect(1050, 50, 1600, 600);
    canvas.save();
    canvas.clipRect(rect);
    canvas.drawBitmap(mBitmap, 950, 0, mPaint);
    canvas.restore();
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 移动

translate(float dx, float dy);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    canvas.translate(950， 50);
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 缩放

scale(float sx, float sy);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    canvas.scale(0.8f， 1.5f);
    canvas.drawBitmap(mBitmap, 950, 0, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 缩放并移动

scale(float sx, float sy，float px, float py);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    canvas.scale(0.6f， 0.8f, 1500, 200);
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 旋转

rotate(float degrees);

以画布左上角为圆心旋转

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    canvas.rotate(10)
    canvas.drawBitmap(mBitmap, 900, 0, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

rotate(float degrees, float dx, float dy);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    canvas.rotate(10, 300, 100);
    canvas.drawBitmap(mBitmap, 900, 0, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置画布倾斜

skew(float sx, float sy);

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);
    canvas.skew(0.2f, 0);
    canvas.drawBitmap(mBitmap, 900, 0, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 画圆

drawCircle(float cx, float cy, float radius, Paint paint);

cx 圆心x坐标；

cy 圆心y坐标；

radius 半径

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.BLUE);
    canvas.drawCircle(520, 1500, 150, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 画椭圆

drawArc(float left, float top, float right, float bottom, float startAngle, float sweepAngle, boolean useCenter, Paint paint);

left 椭圆所在矩形左上角x坐标；

top 椭圆所在矩形左上角y坐标；

right 椭圆所在矩形右下角x坐标；

bottom 椭圆所在矩形右下角y坐标；

startAngle 起始角度

sweepAngle 结束角度

useCenter 是否连接圆心

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.BLUE);
    if(Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP) {
        canvas.drawArc(50, 50, 500, 300, 0, 360, true, mPaint);
        mPaint.setStyle(Paint.Style.STROKE);
        mPaint.setStrokeWidth(2);
        canvas.drawArc(50, 350, 500, 600, 0, 360, true, mPaint);
        canvas.translate(600, 0);
        canvas.drawArc(50, 50, 500, 300, 0, 100, true, mPaint);
        canvas.drawArc(50, 350, 500, 600, 0, 100, false, mPaint);
    }
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

drawArc(RectF oval, float startAngle, float sweepAngle, boolean useCenter, Paint paint);

oval 椭圆所在矩形；

startAngle 起始角度

sweepAngle 结束角度

useCenter 是否连接圆心

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setColor(Color.BLUE);
    RectF rectF = new RectF(50, 50, 500, 300);
    canvas.drawArc(rectF, 0, 360, true, mPaint);
    mPaint.setStyle(Paint.Style.STROKE);
    mPaint.setStrokeWidth(2);
    rectF.set(50, 350, 500, 600);
    canvas.drawArc(rectF, 0, 360, true, mPaint);
    canvas.translate(600, 0);
    rectF.set(50, 50, 500, 300);
    canvas.drawArc(rectF, 0, 100, true, mPaint);
    rectF.set(50, 350, 500, 600);
    canvas.drawArc(rectF, 0, 100, false, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 画Bitmap

drawBitmap(Bitmap bitmap, float left, float top, Paint paint);

left：图片左上角X坐标

top：图片左上角Y坐标

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmap(mBitmap, 20, 20, mPaint);
}
```

**效果图**

<center><img src=./img/drawbitmap.png width=500/></center>



drawBitmap(Bitmap bitmap, Matrix matrix, Paint paint);

matrix：绘制位图时用于变换位图的矩阵

```java
@Override
protected void onDraw(Canvas canvas) {
    Matrix matrix = new Matrix();
    matrix.postTranslate(100f, 100f);
    canvas.drawBitmap(mBitmap, matrix, mPaint);
}
```

**效果图**

<center><img src=./img/drawbitmapmatrix.png width=500/></center>



drawBitmap(Bitmap bitmap, Rect src, RectF dst, Paint paint);

src：以图片左上角为坐标原点，选择矩形区域的图片作为绘制对象

dst：把绘制对象绘制到该矩形内，完全充满该矩形

```java
@Override
protected void onDraw(Canvas canvas) {
    mPaint.setStyle(Paint.Style.STROKE);
    mPaint.setStrokeWidth(2);
    mPaint.setColor(Color.RED);
    canvas.drawBitmap(mBitmap, 0, 0, mPaint);

    Rect rectRes = new Rect(100, 100 ,400, 500);
    canvas.drawRect(rectRes,mPaint);
    Rect rectDst = new Rect(500, 300, 800, 800);
    canvas.drawBitmap(mBitmap, rectRes, rectDst, mPaint);
}
```

**效果图**

<center><img src=./img/drawbitmaprect.png width=500/></center>



drawBitmapMesh(Bitmap bitmap, int meshWidth, int meshHeight, float[] verts, int vertOffset, int[] colors, int colorOffset, Paint paint);

meshWidth：横向上把图片划分成多少格

meshHeight：纵向上把图片划分成多少格

verts：记录扭曲后的位图各“顶点”(网格线的交点)位置，它记录的数据是形如(x0, y0)、(x1, y1)、(x2，y2)格式的数据

vertOffset：控制verts数组中从第几个数组元素开始对bitmap进行扭曲

colors：设置网格顶点的颜色，该颜色会和位图对应像素的颜色叠加，数组大小为 (meshWidth+1) * (meshHeight+1) + colorOffset，可以传 null

colorOffset：从第几个顶点开始转换颜色，通常传 0



https://www.jianshu.com/p/28568b8a1c3f#comments

```java
@Override
protected void onDraw(Canvas canvas) {
    canvas.drawBitmapMesh(mBitmap, 20, 20, verts, 0, null, 0, mPaint);
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>

#### 设置颜色

setColor(Color.BLUE);

```java
@Override
protected void onDraw(Canvas canvas) {
    
}
```

**效果图**

<center><img src=./img/setcolor.png width=500/></center>











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