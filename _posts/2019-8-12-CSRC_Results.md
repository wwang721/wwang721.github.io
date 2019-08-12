---
layout: post
title: "CSRC暑研结束"
tagline: "大三暑假在北京计算科学研究中心..."
#categories: 
#author: ""
#meta: ""
---
7月17号出发来北京，买了8月17号的票回上海，整整在北京待了一个月，CSRC暑研告一段落，在此总结一下我在北京的工作。

## **工作开始** 

来到中心的第一天，徐老师跟我简单聊了聊组里的工作，展示了一些工作成果，给了我一个开放性的研究题目（ 他的一个博士后正在做 ），还有一本 Steven H. Strogatz 的《 [*Nonlinear Dynamics and Chaos: With Applications to Physics, Biology, Chemistry, and Engineering*](https://www.onacademic.com/detail/journal_1000036431031610_498b.html, "Steven H. Strogatz") 》，让我自己先看一看。我的工作主要涉及到了这本书里的 fixed point 和 bifurcation 等概念:

* In an $$n$$-dimensional phase space with coordiantes $$(x_1, \dots,x_n)$$, we introduced the general system:

$$\dot{x}_1=f_1(x_1,\dots,x_n)$$

$$\vdots$$

$$\dot{x}_n=f_n(x_1,\dots,x_n)$$

&ensp;&ensp;&ensp;&ensp;and its solutions could be visualized as trajectories.

* The simplest case $$n=1$$ one-dimensional system, namely $$\dot{x}=f(x)$$. Plot $$\dot{x}$$ versus $$x$$, and draw arrows on the $$x$$-axis to indicate the corresponding velocity vector at each $$x$$: for $$\dot{x}>0$$, $$\rightarrow$$; for $$\dot{x}<0$$, $$\leftarrow$$. At points where $$\dot{x}=0$$, there is no flow; such points are called ***fixed points***.

* Assuming the fixed points of $$\dot{x}=f(x)$$ is $$x^*$$: &ensp;&ensp;$$f'(x^*)<0 \Rightarrow x^*$$ is a stable fixed point; $$f'(x^x)>0 \Rightarrow x^*$$ is an unstable fixed point.

* **bifurcation:** &ensp;&ensp;the qualitative structure of flow (vector fields) can chages as parameters are varied, and fixed points can be created or destroyed, or their stability can change. These qualitative changes in the dynamics are called ***bifurcation***.


## **工作背景**

我在北京的工作围绕着一篇文献展开 [Geometric capture and escape of a microswimmer colliding with an obstacle](https://pubs.rsc.org/en/content/articlelanding/2015/SM/C4SM02785J#!divAbstract "The Royal Society of Chemistry, Soft Matter, 2015")，这篇文献主要模拟了当 microswimmer 在流体中和一个固定的球形 obstacle 碰撞会产生的 geometric capture 和 escape 现象。在实验中已经观察到这个现象，Takagi *et al* 实验给出图中就可以看到一个 self-propelled body 在 colloid-filled bath 中运动时，有时会一直绕着球体circling，有时又会随机逃逸出绕球运动的轨道。

&ensp;

[Go to the Home Page]({{ site.url }}{{ site.baseurl }})