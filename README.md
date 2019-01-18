# 前言

## 阅读本教程需要什么

### 完善的硬件与软件

教程涉及的部分软件会对操作系统等条件有硬性限制，所以开始前请先确认您拥有：

* 基础的计算机文化知识
* 一台64位的电脑，Windows 7以上的操作系统
* 安装过Direct 3D以及VC Redist 2015运行库

### 对游戏本体及补丁机制的基本了解

本教程不提供从零开始的补丁制作教程，阅读前请确认您已对以下内容有了基本的认识：

* JMP文件内的目录结构
* PATCH2与GPK补丁的制作与安装
* 资源管理器等基础工具的使用

### 对三维模型基础知识有基本了解

本教程不提供对于一些基础术语的讲解，阅读前请确认您已对以下内容有了基本的了解：

* 网格、材质与贴图
* 骨骼、蒙皮与动画
* 平移、旋转与缩放变换
* 粒子系统

进阶内容，了解这些内容对于补丁制作的理解有至关重要的作用：

* 深度缓存
* 贴图坐标变换
* 坐标系

### 一个合格补丁作者的基本素质

嗯这条其实是最重要的

* 做出优秀补丁的热情与毅力
* 自行查阅资料解决问题的能力
* 自行反复实验以尝试或求证的耐心
* 适当的脑洞与想象力

## 本教程提供了什么

教程包含对于JumpX Editor（跳跃X模型编辑工具），Max Exporter（3ds Max导出X模型插件），JUMP2FBX（X模型导出FBX工具）三个软件的介绍与讲解，其中第一个工具为主要内容。教程并不包含对修改ini、dat、bank等其余文件的讲解。

## 工作环境的准备

### JumpX Editor

* 导出游戏JMP内的全部文件到一个文件夹内，包含data1中的文件。
* 添加软件自动寻找贴图的路径。打开工具所在文件夹，打开其下的texpath.txt文件，将所有贴图存储路径写入其中，以回车分隔。比如本人的游戏文件解压在了`D:\Program Files (x86)\Jump\300英雄\Unpack`，那么txt文件的内容应如下所示。软件读取贴图的优先级为：与X模型文件同目录下的贴图优先级最高，之后texpath.txt中的路径优先级自上而下依次降低。此项操作可以免去每次导出模型都要寻找对应贴图的麻烦。
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\dian  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\dilie  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\kuosan  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\moxing  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\shandian  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\shui  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\tiaodai  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\tuxing  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\ui  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\xingguang  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\xuanzhuan  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\xulie  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\yanwu  
> D:\Program Files (x86)\Jump\300英雄\Unpack\data\magic\textures\zheshe  

* 修改软件目录下的splash.png可以自定义启动画面。

### Max Exporter

* 添加导出X模型插件。将Max Exporter下的JumpXExporter.dle文件复制到3ds Max程序目录下的stdplugs文件夹内，之后在导出时便可以选择导出X文件（是导出导出不是保存！）。3ds Max软件请使用2016版本，添加前请先安装 VC Redist 2015。

### JUMP2FBX

* 方便FBX格式的转换。在JUMP2FBX文件夹下创建run.bat文件，输入以下内容并保存，之后转换FBX只需将X文件拖动到bat文件图标上即可。
``` bash
@echo off
"%~dp0jump2fbx.exe" %1 %~n1.fbx
pause
```