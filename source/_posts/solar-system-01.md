---
title: solar-system-01
date: 2024-12-22 09:33:40
tags: solar panel, solar system, solar
---

# Solar System 01

## Overview of a Solar System
![Solar Overview 1](/img/solar/solar-overview-01.png)
总体系统结构大概如上图，后面是每个模块的思路。

### Solar Panels
这个是generator的部分，目前太阳能板其实差别不大，而且就算不好，也可以换掉。作为DIY的话，一开始可以准备几种试试看，反正不好的就后院随便用用就好。可以先买些200W的板子小一点，然后确保技术差不多就行。

一块solar panel，一般参数有这些：
- 发电功率。譬如400W，200W这种。
- 价格。不错的板子，400W现在也常常在$100左右，一般不会超过$150。
- 转化效率。单晶板的话，一般在20%~21%之间。所以随便找个靠谱点对品牌买单晶板就够了，都不会有太大差别的。
- 输出电压和电流。譬如37V x 13.8A这样。这个反而比较重要，因为这个关系到我们怎么接板子，串并联怎么做。
- 板子大小。一般400W的大概是1m x 2m这样的。
- datasheet。一般正常的板子都有完整的datasheet的，里面可以看到更详细的参数。
- 合格证标号。我好像还没查这个，不过这个应该也比较重要。

所以，其实只要是一块合格的单晶板（关于单晶板和其它太阳能板的技术啥的，其实对DIY不太重要。DIY记住现在阶段买单晶板就够了，至于具体太阳能板技术，以后有时间我们再说），一般都是符合要求的。

### MPPT
这个主要是对不同时候调整太阳能板发电效率的技术。这个技术后面值的详细讨论，这里我们可以简单的先确认有个MPPT模块就可以。

当然，现在MPPT一般集成在Inverter中，所以后面要换会稍微浪费一点。所以，我可能后面还是会仔细去看一下MPPT是什么技术，它跟PWM有什么差别之类。

### Inverter
这个是整个系统中最重要的部分。

它的原理大致是这样的，它需要达成DC Input => 50Hz AC Ouput的作用，它与整流器的功能刚好相反。

对于这样的需要关注的参数：
- 可接受输入电压
- 支持功率
- 

这里部分我参考的主要是这么个材料：[DIY光伏系统 选对充电控制器才是重点](https://www.bilibili.com/video/BV1wP4y1x7Fh/?spm_id_from=333.337.search-card.all.click)

![Solar Real System Example](/img/solar/solar-real-system.png)