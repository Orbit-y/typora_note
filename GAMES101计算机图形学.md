# GAMES101计算机图形学

## chapter1 绪论

#### **应用**

全局光照 风格化 movies 特效 面部捕捉 动画animations 几何表述 渲染  计算光线 模拟\仿真(simulation) 设计(CDA\CG) 仿真(?)  可视化(visualzation) 虚拟现实(vr) digital lllustration(数字插图) GUI Typography(字体) 

#### **内容**

###### 1.rasterization(光栅化)

三维空间的几何形体实时显示在屏幕上

实时：30fps 离线：offline

###### 2.curves and meshes

曲线、曲面

###### 3.ray tracing(光线追踪)

###### 4.animation/simulation

#### **本课程不包含**

opengl/DirectX/vulkan 图形学API

the syntax of shaders

三维建模和游戏开发

计算机视觉cv(猜测、识别)

<img src="images/image-20250128200944661.png" alt="image-20250128200944661" style="zoom: 33%;" />

## chapter2 线性代数

​	向量、矩阵

#### dependencies of computer graphics

数学：线性代数、微积分、统计

物理：光学、力学

其他：信号处理、数值分析

美学

#### 向量(矢量)

方向、长度
$$
\vec{AB}=B-A
$$
normalization：单位向量，表示方向

点乘：夹角余弦，结果是一个数 -> **求夹角、投影、向量分解、向前向后（点乘正负）、向量是否接近**

叉乘：
$$
\vec{a}×\vec{b}=-\vec{b}×\vec{a}
$$

$$
||\vec{a}×\vec{b}||=||\vec{a}||||\vec{b}||sinΦ
$$



<img src="images/image-20250128212841839.png" alt="image-20250128212841839" style="zoom: 25%;" />



方向和a与b垂直，右手定则确定

叉乘自己是0向量

**建立三维空间直角坐标系、判断左右内外**

叉乘同号判断内外，叉乘正负判断左右

<img src="images/image-20250128213050980-1738253029137.png" alt="image-20250128213050980" style="zoom: 25%;" />



#### 矩阵

无交换律

有结合律和分配律

变换



## chapter3 变换transformer

#### 变换的作用

模型变换

视图变换

旋转，缩放，投影

#### 2D变换

矩阵与变换

一些线性变换

###### 1.缩放 scale

<img src="images/image-20250129135801071.png" alt="image-20250129135801071" style="zoom: 50%;" />

###### 2.翻转 reflection

###### 3.切变 shear

###### 4.旋转

<img src="images/image-20250129135809042.png" alt="image-20250129135809042" style="zoom:50%;" />





#### 齐次坐标

###### 5.平移变换/仿射变换 translation 不是线性变换

<img src="images/image-20250129135818623.png" alt="image-20250129135818623" style="zoom:50%;" />

<img src="images/image-20250129135928549.png" alt="image-20250129135928549" style="zoom:50%;" />



2维向量和点增加一个维度

![image-20250131001125862](images/image-20250131001125862.png)

1和0的作用：

0 ->平移不变  点加上点->中点

<img src="images/image-20250131001136520.png" alt="image-20250131001136520" style="zoom:50%;" />

#### 逆变换

逆矩阵

#### 变换合成

复杂变换可以通过一系列简单的变换得到

变换的顺序（矩阵不具有交换律）

#### 变换分解

<img src="images/image-20250131001155480.png" alt="image-20250131001155480" style="zoom: 50%;" />

绕C旋转分解

1.移动到原点 2.旋转 3.移动到c点

#### 3D变换

###### 三维空间的齐次表示

![image-20250131001224482](images/image-20250131001224482.png)

变换

![image-20250131001238625](images/image-20250131001238625.png)

线性变换 放射变换 平移变换

先线性变换再平移，如下图所示分解

<img src="images/image-20250131001248034.png" alt="image-20250131001248034" style="zoom:50%;" />



###### scale in 3D

![image-20250131001300064](images/image-20250131001300064.png)

###### translation in 3D

![image-20250131001307176](images/image-20250131001307176.png)

###### rotation in 3D

绕轴旋转：

<img src="images/image-20250131001316665.png" alt="image-20250131001316665" style="zoom:50%;" />



任意旋转

![image-20250131001326583](images/image-20250131001326583.png)

欧拉角

###### 旋转公式:绕轴n旋转角度α

<img src="images/image-20250131001333791.png" alt="image-20250131001333791" style="zoom:50%;" />



#### 观测变换之视图变换和投影变换 

拍照 

step1 地点和人物model transformation

step2角度和相机view transformation

step3拍照projection transformation

###### model/view/camera transformation

1.确定相机的三个向量：位置 朝向 向上

![image-20250131001343597](images/image-20250131001343597.png)

2.移动相机到固定的标准位置上，原点，-z方向看，y向上方向

<img src="images/image-20250131001351642.png" alt="image-20250131001351642" style="zoom:50%;" />

step1：e移动到原点

![image-20250131001403527](images/image-20250131001403527.png)

step2:旋转轴，考虑逆旋转(转置)

<img src="images/image-20250131001411504.png" alt="image-20250131001411504" style="zoom:67%;" />

###### projection transformation

<img src="images/image-20250131001429305.png" alt="image-20250131001429305" style="zoom: 50%;" />



###### 正交投影

<img src="images/image-20250131001455431.png" alt="image-20250131001455431" style="zoom:50%;" />



<img src="images/image-20250131001507246.png" alt="image-20250131001507246" style="zoom:50%;" />

 

###### 透视投影

平行线不再相交

一些数学基础

<img src="images/image-20250131001550923.png" alt="image-20250131001550923" style="zoom:50%;" />

<img src="images/image-20250131001617107.png" alt="image-20250131001617107" style="zoom: 25%;" />



先变成长方体，再做正交投影

<img src="images/image-20250131001647412.png" alt="image-20250131001647412" style="zoom:80%;" />

有一个相似三角形的数学关系

<img src="images/image-20250131001700031.png" alt="image-20250131001700031" style="zoom:50%;" />

如下计算，来寻找压缩变换的矩阵

<img src="images/image-20250131001714024.png" alt="image-20250131001714024" style="zoom:50%;" />



观察到：近和远平面的z不变

![image-20250131001723940](images/image-20250131001723940.png)

先看近平面上的任意一点在矩阵作用下是自己，对其 变换齐次坐标

<img src="images/image-20250131001733624.png" alt="image-20250131001733624" style="zoom:50%;" />

再看远平面的点，考虑中心点

<img src="images/image-20250131001744203.png" alt="image-20250131001744203" style="zoom:50%;" />

最后解出A和B

<img src="images/image-20250131001755068.png" alt="image-20250131001755068" style="zoom:50%;" />

## chapter4 光栅化Rasterization/三角形

复习：perspective projection

<img src="images/image-20250131172433444.png" alt="image-20250131172433444" style="zoom:33%;" />

长宽比（宽高比）aspect ratio和垂直可视角度Y 作业1会用到

<img src="images/image-20250131172546508.png" alt="image-20250131172546508" style="zoom:50%;" />

做完三个步骤后，所有的物体都会在[-1,1]³中

<img src="images/image-20250131172750890.png" alt="image-20250131172750890" style="zoom:50%;" />

接下来会讲正交立方体放到屏幕上

<img src="images/image-20250131172959647.png" alt="image-20250131172959647" style="zoom:50%;" />

##### 光栅化：将物体画在屏幕上

屏幕：像素的排列，是典型的栅格

分辨率：像素排列的大小

像素：有颜色的小方格，颜色由RGB三色组成

##### 定义屏幕空间

像素的坐标indices，整数坐标，(0,0) to (width-1,height-1)

像素中心(x+0.5,y+0.5)，覆盖(0,0) to (width,height)

原点在屏幕空间的左下角

<img src="images/image-20250131174635481.png" alt="image-20250131174635481" style="zoom:33%;" />

<img src="images/image-20250131174651998.png" alt="image-20250131174651998" style="zoom:50%;" />

##### 立方体变换到屏幕上

先把立方体的xy平面缩放到屏幕上

再平移（保证原点在左下角）

也就是视口变换，变化的矩阵如下所示

这样我们得到一个2维的图

<img src="images/image-20250131175600661.png" alt="image-20250131175600661" style="zoom:33%;" />

##### 把三角形坐标变成屏幕空间的像素

drawing machines

###### 一些成像设备

光栅显示设备:示波器，显示器（显存，内存中的一个区域），LCD（计算器，手机，视网膜级别）,电子墨水屏

LCD，液晶显示器

LED，发光二极管

###### 三角形

最简单的多边形，能表示别的多边形，确定一个平面

内部外部对应清楚，渐变性质（插值）

像素中心点和三角形的位置关系

###### **采样，sampling ：**

在某个点对函数求值就是采样，我们通过采样将函数离散化。

###### **计算一个函数在某个点的值**

**离散化某个函数**

如对像素中心采样，对时间，空间采样

<img src="images/image-20250131193010947.png" alt="image-20250131193010947" style="zoom:50%;" />



<img src="images/image-20250131193157564.png" alt="image-20250131193157564" style="zoom:33%;" />

<img src="images/image-20250131193211011.png" alt="image-20250131193211011" style="zoom: 33%;" />

<img src="images/image-20250131193344572.png" alt="image-20250131193344572" style="zoom:33%;" />

用叉乘判断是否在内部，同为正或者同为负

边界情况：不做处理或者特殊处理

<img src="images/image-20250131194355294.png" alt="image-20250131194355294" style="zoom:33%;" />

锯齿？

抗锯齿和反走样

##### sampling artifacts(瑕疵？)

Aliasing/Jaggies 空间采样

摩尔纹 空间采样

车轮效应 时间采样

##### 时域与频域

频域是描述信号在频率方面特性时用到的一种坐标系

时域是描述数学函数或物理信号对时间的关系的一种坐标系。



信号变换速度大于采样速度 和频率有关 数字信号

![image-20250131200517347](images/image-20250131200517347.png)

模糊/滤波信号 用于抗锯齿和反走样

![image-20250131200751905](images/image-20250131200751905.png)

定义 频率f 周期T

傅里叶级数展开：周期函数写成正弦余弦函数的线性组合加常数

随着展开式越来越多，越来越接近我们想要表达的函数

<img src="images/image-20250131200932879.png" alt="image-20250131200932879" style="zoom:33%;" />

傅里叶变换：在时域和频域之间转换信号的技术

<img src="images/image-20250131201008596.png" alt="image-20250131201008596" style="zoom:33%;" />



<img src="images/image-20250131201200466.png" alt="image-20250131201200466" style="zoom: 33%;" />

随着频率越高，采样效果越差

走样：不同的函数在一个采样方法下得到相同的结果

##### 滤波：去掉一些频率的内容

时域到频域

<img src="images/image-20250131203206856.png" alt="image-20250131203206856" style="zoom:33%;" />

<img src="https://pic2.zhimg.com/v2-31e1e5040824924a05f61794171aeed1_1440w.jpg" alt="img" style="zoom: 33%;" />

右边是频率内容

中间低频，四周高频

<img src="images/image-20250131203349810.png" alt="image-20250131203349810" style="zoom:33%;" />

高通滤波  信号变化很大-高频率-边界

<img src="images/image-20250131203506660.png" alt="image-20250131203506660" style="zoom:33%;" />

低通滤波 边界变得很模糊

<img src="images/image-20250131203602913.png" alt="image-20250131203602913" style="zoom:33%;" />

<img src="images/image-20250131203710887.png" alt="image-20250131203710887" style="zoom:33%;" />

###### 滤波=卷积=平均 

<img src="images/image-20250131203905784.png" alt="image-20250131203905784" style="zoom:33%;" />

任意个数=周围数加权平均

<img src="images/image-20250131204051304.png" alt="image-20250131204051304" style="zoom:33%;" />

滤波器，卷积核

<img src="images/image-20250131204257014.png" alt="image-20250131204257014" style="zoom:33%;" />

归一化的九分之一

###### 采样=重复频域上的内容

<img src="images/image-20250131204705784.png" alt="image-20250131204705784" style="zoom:50%;" />

冲激函数

采样=重复频谱

为什么会走样

<img src="images/image-20250131204852442.png" alt="image-20250131204852442" style="zoom:33%;" />

采样率不够，频谱的复制粘贴的间隔越小，发生了混合

##### 如何反走样？

1.增加采样率 频率高 增加分辨率

2.先模糊，再采样

低通滤波（模糊）

<img src="images/image-20250131205156587.png" alt="image-20250131205156587" style="zoom:50%;" />

<img src="images/image-20250131205338762.png" alt="image-20250131205338762" style="zoom:50%;" />

##### <img src="images/image-20250131205438856.png" alt="image-20250131205438856" style="zoom:50%;" />

在光栅化一个三角形时，像素颜色的平均值f（x,y）= 三角形的覆盖像素的面积

##### 实际做法

###### MSAA：模糊和滤波操作，不是提高采样率

一个像素划分成更多的小像素，然后每个判断，然后取平均，覆盖率

<img src="images/image-20250131205727810.png" alt="image-20250131205727810" style="zoom:50%;" />

模糊效果如上，然后进行采样

代价：计算量

**采样点可以用不同的图案，也可以复用

<img src="images/image-20250131210050506.png" alt="image-20250131210050506" style="zoom:50%;" />

###### FXAA 方案 边界处理

###### TAA方案 

###### 超分辨率

![image-20250131210317255](images/image-20250131210317255.png)

































 







































