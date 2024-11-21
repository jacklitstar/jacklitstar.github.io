---
title: Computer Vision
date: 2024-11-22 00:00:00
categories: Learn
---
# <center> 《计算机视觉》课程技术报告（3）</center>

## 图像的成像原理以及摄像机模型
摄像机模型 Camera Model 描述了一个光路映射坐标的数学模型。模型概括为将三维世界中的立体模型所发出的光线通过光学元件投影称为二维的图像的数学化。
$$s[x',y',1]^T = K[R,T][x,y,z,1]^T$$
其中 $x,y,z$ 为三维坐标，$(x',y')$ 为平面上的点，$K$ 为参数矩阵，与小孔有关。$R，T$ 为外参矩阵，与摄像机的旋转和平移有关。$s$ 为尺度因子。
### 针孔摄像机模型
针孔摄像机模型pinhole camera model来源于简单的物理学光路原理，是最基本的摄像机模型。假设摄像机主体为小孔，光纤通过小孔投影到平面上。

![](/img/pic1.png)  


在这种结构中，胶片通常称为像或视网膜平面。光圈称为针孔 O 或相机中心。图像平面和针孔 O 之间的距离是焦距 f。有时，视网膜平面位于 O 和 3D 物体之间，与 O 的距离为 f。在这种情况下，它被称为虚拟图像或虚拟视网膜平面。模型满足公式：
$$[x',y'] = \left[f\frac x z, f\frac y z\right]$$
但是当小孔不再足够小后，光先不再满足都通过一个小点的条件，这就导致图像产生虚化直到完全消失。

### 透镜模型
现代相机中一般都采用了多种透镜的组合代替以上的小孔。这些透镜通过某种组合仍然满足所有由同一点发出的光线最终都达到像平面上同一点。

![](/img/pic2.png)

对于一般简单透镜，将所有平行入射光汇聚到的一点称为**焦点** ，焦点到透镜中心的距离称为 **焦距** 。类比针孔模型，可以给出数学建模： 
$$[x',y'] = [z' \frac x z , z' \frac y z]$$

![焦点和焦平面](/img/pic3.png)

以上模型假设了透镜足够薄且光学性能足够良好。径向畸变由于透镜不同位置焦距不同导致。

![焦点和焦平面](/img/pic4.png)

## 数学模型
摄像机的矩阵模型，引入齐次坐标。假设三维空间中点的坐标为 $P = (x,y,z,1)$ , 像点 $P' = (x' ,y' ,1)$ 
$$
P' = \begin{bmatrix} \alpha &0 &c_x &0\\
0 &\beta &c_y &0\\
0 &0 &1 &0 \end{bmatrix} \begin{bmatrix} x\\ y\\ z\\1 \end{bmatrix} = K \begin{bmatrix}I &0\end{bmatrix}MP
$$
其中 $K$ 矩阵称为 **摄像机矩阵** ，$c_x ,c_y$ 为像的偏差，是真实坐标和摄像机像素真实坐标之差。 $\alpha = fk, \beta = fl$。 $l,k$ 为两个方向的像素密度。
$$K =  \begin{bmatrix} x'\\ y'\\ z'\end{bmatrix} = \begin{bmatrix} \alpha &-\alpha \cot\theta &c_x \\
0 &\frac{\beta}{\sin \theta} &c_y \\
0 &0 &1  \end{bmatrix}$$
建立真实坐标与相机坐标的关系： 
$$P = \begin{bmatrix} R&T\\ 0 &1\end{bmatrix}P_w$$
其中$R$ 为旋转矩阵，它是一个正交矩阵 $R^TR = I$ 。 $T$ 为平移矩阵。
对于世界坐标下为 $P_w$ 的点在相机坐标下为 $P$ .
将其代入上面公式，最终得到齐次坐标下的摄像机模型： 
$$P' = K\begin{bmatrix}R &T\end{bmatrix}P_w$$
另外由于透镜质地原因，透镜可能并不是处处焦距相等造成**径向畸变**，透镜安装可能有偏差造成非对称性，称为**切向畸变**。可以使用多项式描述径向畸变：
$$x_d = x(1 + k_1r^2 + k_2r^4 + \dots)\\y_d = y(1 + k_1r^2 + k_2r^4 + \dots)$$
其中$x_d, y_d$ 为径向畸变后的坐标，多项式系数称为畸变参数，$r^2 = x^2 +y^2$。于是实际坐标$x_a, y_a$ 满足：
$$x_a = \alpha x_d +c_x\\y_a = \beta y_d + c_y$$

Images are from [stanford cs231a](https://web.stanford.edu/class/cs231a/course_notes/01-camera-models.pdf) 