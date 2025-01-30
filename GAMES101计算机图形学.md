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

















 







































