---
layout: post
title: "CSRC暑研结束"
tagline: "大三暑假在北京计算科学研究中心..."
#categories: 
#author: ""
#meta: ""
---
7月17号出发来北京，买了8月17号的票回上海，整整在北京待了一个月，CSRC暑研告一段落，在此总结一下我在北京的工作。

## **工作背景** 

来到中心的第一天，徐老师跟我简单聊了聊组里的工作，展示了一些工作成果，给了我一个开放性的研究题目（ 他的一个博士后正在做 ），还有一本 Steven H. Strogatz 的《 [*Nonlinear Dynamics and Chaos: With Applications to Physics, Biology, Chemistry, and Engineering*](https://www.stevenstrogatz.com/books/nonlinear-dynamics-and-chaos-with-applications-to-physics-biology-chemistry-and-engineering "Steven H. Strogatz") 》，让我自己先看一看。我的工作主要涉及到了这本书里的 fixed point 和 bifurcation 等概念:

* In an $$n$$-dimensional phase space with coordiantes $$(x_1, \dots,x_n)$$, we introduced the general system:

$$\dot{x}_1=f_1(x_1,\dots,x_n)$$

$$\vdots$$

$$\dot{x}_n=f_n(x_1,\dots,x_n)$$

&ensp;&ensp;&ensp;&ensp;and its solutions could be visualized as trajectories.

* The simplest case $$n=1$$ one-dimensional system, namely $$\dot{x}=f(x)$$. Plot $$\dot{x}$$ versus $$x$$, and draw arrows on the $$x$$-axis to indicate the corresponding velocity vector at each $$x$$: for $$\dot{x}>0$$, $$\rightarrow$$; for $$\dot{x}<0$$, $$\leftarrow$$. At points where $$\dot{x}=0$$, there is no flow; such points are called ***fixed points***.

* Assuming the fixed points of $$\dot{x}=f(x)$$ is $$x^*$$: &ensp;&ensp;$$f'(x^*)<0 \Rightarrow x^*$$ is a stable fixed point; $$f'(x^x)>0 \Rightarrow x^*$$ is an unstable fixed point.

* **bifurcation:** &ensp;&ensp;the qualitative structure of flow (vector fields) can chages as parameters are varied, and fixed points can be created or destroyed, or their stability can change. These qualitative changes in the dynamics are called ***bifurcation***.


## **工作开始**

我在北京的工作围绕着一篇文献展开 [*Geometric capture and escape of a microswimmer colliding with an obstacle*](https://pubs.rsc.org/en/content/articlelanding/2015/SM/C4SM02785J#!divAbstract "The Royal Society of Chemistry, Soft Matter, 2015")，这篇文献主要模拟了当 microswimmer 在流体中和一个固定的球形 obstacle 碰撞会产生的 geometric capture 和 escape 现象。

<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/Takagi.png" alt="Snapshots from the experiments of Takagi et al." title="Snapshots from the experiments of Takagi et al." width="300"/>
</center>
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;▲ Snapshots from the experiments of Takagi et al.

在实验中已经观察到这个现象，Takagi *et al* 实验给出图中就可以看到一个 self-propelled body 在 colloid-filled bath 中运动时，有时会一直绕着球体circling，有时又会随机逃逸出绕球运动的轨道。对于这个固定球体来说，即存在一个临界半径，当半径大于这个 critical 半径 $$A_c$$ 时，swimmer就会一直绕着球体运动。

## **分析研究**

为了分析这个现象，我们要考虑 microswimmer 在流体中的运动方程，它的速度由两部分组成，一个是 swimmer 自身的驱动速度 $$\mathbf{e}$$ , 另一部分即流场的速度 $$\mathbf{u}$$ , 故 microswimmer 的速度可以写成 $$\frac{\mathrm{d}\mathbf{x}_0}{\mathrm{d}t}=\mathbf{e}+\mathbf{u}$$ ，其中 $$\mathbf{e}$$ 的方向由 Faxén's Law 确定: $$\frac{\mathrm{d}\mathbf{e}}{\mathrm{d}t}=\mathbf{\Omega}\times\mathbf{e}$$ 。

<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/colloid_swimmer.png" alt="Illustration of the colloid/swimmer system" title="Illustration of the colloid/swimmer system" width="500"/>
</center>
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;▲ Illustration of the colloid/swimmer system

根据上图可将其改写成 $$h$$ 和 $$\theta$$ 的方程，便可以得到 $$\frac{\mathrm{d}h}{\mathrm{d}t}$$ 和 $$\frac{\mathrm{d}\theta}{\mathrm{d}t}$$ 的表达式，由此画出 $$h-\theta$$ 相图以寻找 fixed points.

<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/theta_h-1_large.png" width="400"/><img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/theta_h-1.png" width="400"/>
</center> &ensp;&ensp;&ensp;▲ $$A=16, \gamma=1, \alpha=0.8$$ 时的 $$h-\theta$$ 相图 &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;▲ 放大后 $$h=1$$ 附近的 $$h-\theta$$ 相图

从图中可以看到红色点是解出来的 fixed point 所在，但不幸的是,它并不是一个稳定的 fixed point ，只要有一点微扰，他就会偏向其他 $$h$$ 和 $$\theta$$, 但是如果我们取 swimmer 的半径为1，仅考虑 $$h\geqslant1$$ 时的情况，就可以发现在绿点所在位置存在一个 fixed point。如果仅保留一阶小量可以退出存在临界半径 

$$A_c=\frac{128\bar{h}^5}{9\alpha^2(2-\it{\Gamma})}.$$

通过数值计算模拟 swimmer 在流体中的 trajectories, 确实可以得到绕球和不绕球两种运动轨迹：

<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/Rtra15.gif" width="380"/><img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/Rtra20.gif" width="400"/>
</center> &ensp;&ensp;&ensp;▲ $$A=15, \gamma=1, \alpha=0.8$$ 时的运动轨迹 &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;▲ $$A=20, \gamma=1, \alpha=0.8$$ 时的运动轨迹

再利用CSRC的高性能服务器我们可以进行大量数据的计算，在这里展示部分计算结果：

<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/contour2.png" width="400"/><img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/dh_dt.png" width="400"/>
</center> &ensp;▲ 不同 $$A$$ 和入射纵坐标 $$b$$ 对出射角 $$\theta$$ 的影响 &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; ▲ 径向速度 $$\mathrm{d}h/\mathrm{d}t$$ 理论和实际值的差别


&ensp;

[Go to the Home Page]({{ site.url }}{{ site.baseurl }})