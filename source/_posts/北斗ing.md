---
title: 北斗ing
date: 2019-08-27 17:52:00
tags: 折腾ing
comment:  false
top: true

---
RIENX格式（上）：2.10版本内容解析和说明

<!-- more -->
![0](1.png)
![1](2.png)
![2](3.png)
![3](4.png)
![4](5.png)
###  RTK（ Real-time kinematic）指的是实时动态测量，也叫载波相位差分定位
是 GNSS 相对定位技术的一种，主要通过基准站和流动站（接收机位置）之间的实时数据链路和载波相对定位快速解算技术，实现高精度动态相对定位。

具体实现方法就是，在地面设置固定的基准站（要保证位置精准标定），用来接收卫星信号，通过两种方式为用户提供差分服务，一种是用已知的基准站位置解算所收到信号中的误差，误差通过网络播发的形式传输给附近的用户接收机，由于参考站和接收机端的误差存在时间和空间上的相关性，在接收机端减掉误差后，得到的就是一个高精度位置信息了。另一种方法是将基准站接收机收到的观测量直接发送给用户，用户端通过“求差”的方式消除或减少误差的影响。这就是高精度 GNSS 定位技术的基本原理。第二种方法的效果较好，所以被广泛采用。

### 可以用的
由于载波相位观测值的波长仅为对应伪距观测值的1/100，其测量精度相对较高，所以在精密定位时通常使用载波相位方法。但由于GPS信号结构的限制，在相位观测量中总是包含着一个初始相位整周数，因此，GPS整周模糊度的解算成了采用载波相位进行精密相对定位的关键问题。准确、快速的解算出整周模糊度，不仅能够缩短定位时间，还能够保障相对定位的精度。
其主要思路可分为3个步骤：（1）标准最小二乘平差求基线和整周模糊度浮点解；（2）整数最小二乘估计求整周模糊度固定解；（3）基线固定解。


[RIENX格式（上）：2.10版本内容解析和说明](https://blog.csdn.net/yuan22900/article/details/50435499)https://blog.csdn.net/yuan22900/article/details/50435499
MATLAB算法VIP可见：
[MATLAB算法VIP可见：](https://blog.csdn.net/iamlsj/article/details/38061929)https://blog.csdn.net/iamlsj/article/details/38061929
[VIP](https://blog.csdn.net/weixin_41498178/article/details/79304849)
[载波相位 单差法 双查发 三叉发](https://wenku.baidu.com/view/54fde5f1f61fb7360b4c653a.html?rec_flag=default) https://wenku.baidu.com/view/54fde5f1f61fb7360b4c653a.html?rec_flag=default
[载波毕设](https://wenku.baidu.com/view/fb3ff54efe4733687e21aa24.html)https://wenku.baidu.com/view/fb3ff54efe4733687e21aa24.html
[记得领完积分下东西 搜载波相位 （看过1—4）](https://www.dssz.com/user/down.php)https://www.dssz.com/user/down.php
[matlab载波相位符号定时联合估计](http://www.doc88.com/p-536463024180.html)http://www.doc88.com/p-536463024180.html
[GPS载波相位平滑伪距](https://download.csdn.net/download/songliang12/9563542)https://download.csdn.net/download/songliang12/9563542
[纯下载无介绍 不靠谱](http://www.pudn.com/Download/item/id/1774260.html)http://www.pudn.com/Download/item/id/1774260.html
Google  载波相位 测距 程序
Google 载波相位观测值的组成部分
[貌似同一个毕设](https://www.docin.com/p-2126879971.html)https://www.docin.com/p-2126879971.html
[武汉大学老师讲解](https://www.bilibili.com/video/av39735562/)https://www.bilibili.com/video/av39735562/
[武汉大学老师继续讲解](https://www.bilibili.com/video/av39840214/?p=2)https://www.bilibili.com/video/av39840214/?p=2
[GPS测距码测量合集](https://www.bilibili.com/video/av39761085/?spm_id_from=333.788.videocard.3)https://www.bilibili.com/video/av39761085/?spm_id_from=333.788.videocard.3
[高精度GNSS技术如何解决IoT场景下的时空定位问题](https://mp.weixin.qq.com/s/cx3gF6sRMwyPTg81fGUrwg)
[莫名其妙的网站还有一些零碎的源代码](http://kom.aau.dk/~borre/easy/)


###  DGPS简介
DGPS:差分全球定位系统(Differential Global Position System).

目前 GPS 系统提供的定位精度是优于 10 米，而为得到更高的定位精度，我们通常采用差分 GPS 技术：将一台 GPS 接收机安置在基准站上进行观测。根据基准站已知精密坐标，计算出基准站到卫星的距离改正数，并由基准站实时将这一数据发送出去。用户接收机在进行 GPS 观测的同时，也接收到基准站发出的改正数，并对其定位结果进行改正，从而提高定位精度。

 

### 差分 GPS 分为两大类：伪距差分和载波相位差分

差分的优点

（1）消除卫星钟钟差

（2）消除卫星星历误差

（3）消除电离层延迟

（4）消除对流层延迟

（5）将接收机钟钟差做为未知数求出以上措施将有效地提高GPS定位精度，一般而言，以坐标方式差分可达±5m的精度，以伪距方式可达±（1～3）m级精度，以载波相位方式可达±（1～3）cm的精度，高程精度为平面精度的2～3倍。
### 导航电文概述
 导航电文划分
根据速率和结构不同，导航电文分为 D1 导航电文和 D2 导航电文。D1
导航电文速率为 50 bps，并调制有速率为 1 kbps 的二次编码，内容包含基
本导航信息（本卫星基本导航信息、全部卫星历书信息、与其它系统时间
同步信息）；D2 导航电文速率为 500 bps，内容包含基本导航信息和增强服
务信息（北斗系统的差分及完好性信息和格网点电离层信息）。
MEO/IGSO 卫星的 B1I 信号播发 D1 导航电文，GEO 卫星的 B1I 信号
播发 D2 导航电文。
### 整周模糊度
如果需要高精度定位，需要用到载波相位测量值，一般是N个载波波长加上相位差再加上其他误差（如电离层延迟、对流层延迟、时钟误差、多径效应误差等），这里的N就是整周模糊度，因为信号发射和接收存在时钟误差，所以是一个未知的模糊值。
### LAMBDA方法基于模糊度及其方差协方差矩阵提供模糊度的整数最小二乘估计。
![9](9.png)
![10](10.png)
### 整周模糊度的求解技术  
按精密相对定位的应用不同，整周模糊度求解算法大致可以分为两类：一类是，用于接收机可静止几小时甚至几天的静态定位；一类是包括实时动态RTK在内的非静态定位。

整周模糊度的求解不但要求移动中用户接收机在不经静态初始化的情况下完成整周模糊度的求解，而且还要求接收机能够容忍不时发生的对卫星信号的跟踪失锁。

不同的整周模糊度求解算法有着不同的求解思路。

1.利用伪距帮助估算整周模糊度的取整算法是最简单，最直接的一种。

2.其他的算法则集中在求解一个整数型最小二乘问题。基于求解整数型最小二乘问题的整周模糊度求解算法一般是将某个目标函数最小化。目前应用最多的是使模糊度残余平方和最小。

因为一类整周模糊度求解算法是依据某种准则通过搜索的方式来确定整周模糊度，因而在那些基于模糊度残余平方和最小原则的整数型最小二乘估计算法中，较为著名的是最小二乘模糊度搜索法（LSAST），LAMBDA算法等。

还有一类整周模糊度求解算法不需要搜索，他是利用不同频率测量值组合出不同波长的测量值，并逐级确定他们的整周模糊度。

整周模糊度的求解一般需要两步完成：首先是通过一定算法求解出整周模糊度，然后再验证所解得的整周模糊度值得正确性。模糊度残差值的大小通常被用来验证整周模糊度求解值得正误，而有的验证方法需要首先求解出最优和次优两个整周模糊度。

评价一个整周模糊度求解算法的好坏通常是依据他的计算量和准确度。同时，既然载波相位测量值中的整周模糊度能被求解出来，那么测量值中的周跳错误自然也就能被检测出来，并且还有可能被修复。
### 快速求解整周模糊度：
![6](6.png)
![7](7.png)
![11](11.png)
<blockquote class="blockquote-center" >O : 观测数据   N ： 星历数据</blockquote>
[发布源码功能目前已关闭。](http://www.biguo100.com/user/unew.asp)

### LAMBDA法
LAMBDA法全称最小二乘模糊度降相关平差法（Least-square AMBiguity Decorrelation Adjustment）是由荷兰Delft大学的Teunissen教授提出的。该方法可缩小搜索的范围，加快搜索过程，是目前快速静态定位中最成功的一种模糊度搜索方法。

整数变换
经典算法中在确定整数模糊度组合主要遇到问题为，由于观测时间短，初始解中的实数模糊度参数精度低，参数的相关性又很强。
在LAMBDA中，不直接对实数模糊度参数进行搜索，而是先对初始解中的实数模糊度N^及其协因数阵QN^进行整数变换。N^及其协因数阵QN^进行整数变换。
![8](8.png)
逆变换求得的参数NN就是我们最初要寻找的最佳的整数模糊度向量。
书上讲到，通过对协因数阵Q−1N^进行LTDL分解进行整数变换，但是具体方法并未进行详细的叙述
### LAMDA1
This version (lambda1) is intended to be used mainly for research.
% It has more options than the original code, such as output of
% intermediate results, optional number of candidates to be returned
% and so on. If you are not interested in these options, you can use
% "lambda2"
### LAMDA2
This is the other one of the main routines. Compared to routine lambda1.m, this routine is simplified. It is not
possible to generate intermediate output, and it is not possible to select the number of candidates to be computed
(the routine will return 2 candidates).
Usage: [afixed,sqnorm,Qahat,Z] = lambda2 (afloat,Qahat);


afloat  Input  Original float ambiguities
Qahat   Input  Corresponding variance-covariance matrix
afixed   Output Array with estimated integer candidates, sorted according
to the corresponding squared norms, best candidate first
sqnorm  Output Corresponding squared norms
Qzhat   Output Decorrelated variance-covariance matrix
Z      Output Z-transformation matrix
