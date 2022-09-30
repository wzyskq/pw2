---
title: '电功与电能（十一、十二章）'
date: 2022-05-17 15:18:22
tags: [物理公式]
published: true
hideInList: false
feature: 
isTop: false
---
>文档已完结！！🔮
勘误记得联系我👀

# 目录

@[TOC]

## 一、快速查找

### 1.求$I$ (标量)
|公式|备注|
| --- | --- |
| $I = \frac{q}{t}$ | 宏观（定义式）|
| $I = neSv$ | 微观（定义式）n：单位体积内电子数 e：电子电荷量|
| $I =\frac{U}{R}$ | 欧姆定律 |
| $I = I{\tiny 1} = I{\tiny 2}$| 串联电路 |
| $I = I{\tiny 1} + I{\tiny 2}$| 并联电路 |
| $I = \frac{E}{R + r}$ | 适用**纯电阻**电路 |
| $I = \frac{E}{r}$ | 电源短路 |

### 2.求$R$ (标量）
| 公式 | 备注 |
| --- | --- |
| $R = \frac{U}{I}$ | 定义式 |
| $R =\rho \frac{l}{S}$ | 决定式 （ Ps：T越大，$\rho$ ($\Omega \cdot m$) 越大；合金受温度影响小）|
| $R = R{\tiny 1} + R{\tiny 2}$| 适用串联电路 |
| $\frac{1}{R} = \frac{1}{R{\tiny 1}} + \frac{1}{R{\tiny 2}}$| 适用并联电路 |
| $\frac{R{\tiny A} }{R{\tiny B} } = \frac{tan\theta {\tiny A} }{tan\theta {\tiny B} }$ | 适用导体AB的U-I图像 |

### 3.求$E$ (标量 电动势！)
|公式|备注|
| --- | --- |
| $E = \frac{W}{q}$ | 定义式 (1 V=1 J/C)|
| $E = IR + Ir$ | 适用纯电阻电路，r 为内阻 |
| $E =U{\tiny 外}+U{\tiny 内}$ | 适合任何电阻 |

### 4.功的表达式
|公式|备注|
| --- | --- |
| $EIt = I^2Rt + I^2rt$ | 适用纯电阻电路 |
| $W = W{\tiny 外} + W{\tiny 内}$ | 适合任何电阻 |


## 二、专题分类

### 电功与电热
| | 纯电阻电路 | 非纯电阻电路 |
| ---| --- | ---|
| 电功 | $W = IUt = I^2Rt = \frac{U^2}{R}t$ | $W = IUt$ |
| 电热 | $Q = IUt = I^2Rt = \frac{U^2}{R}t$ | $Q = I^2Rt$ |
|电功率| $P = IU = I^2R = \frac{U^2}{R}$ | $P = UI$ |
|热功率| $P = IU = I^2R = \frac{U^2}{R}$ | $P = I^2R$ |

### 表头改装
| 电压表 | 电流表 |
| --- | --- |
| ![1](https://pic.lienav.com/i/2022/05/20/6287aff086253.png) | ![2](https://pic.lienav.com/i/2022/05/20/6287afeec9a23.png) |
| $R=\frac{U-I{\tiny g}R{\tiny g}}{I{\tiny g}}$ | $R=\frac{I{\tiny g}R{\tiny g}}{I-I{\tiny g}}$ |
| $\frac{R}{R{\tiny g}}=\frac{U-U{\tiny g}}{U{\tiny g}}$ | |
| ❓ $U=nU{\tiny g}$? ⇩ | ❓ $I=nI{\tiny g}$? ⇩ |
| $R{\tiny 串}=(n-1)R{\tiny g}$ | $R{\tiny 并}=\frac{R{\tiny g}}{n-1}$ |

###  电路动态分析的方法
![3](https://pic.lienav.com/i/2022/05/21/6287bd54dece1.png)

## 三、文字概念

1.$U$，外电压也叫**路端电压**
2.$I$，电路的总电流，通常称为**干路电流**
3.电源的电动势和内阻（E，r）都是由电源*本身的性质决定*，与外电路无关.
4.电池正常工作时，其*电动势*可以看做不变. 在较短时间内，电池的*内阻*也可以看做不变.
5.外电路中的用电器叫做**负载**（电路中消耗电能的元件；负载既可能是纯电阻，也可能是电动机等）
6.当 R=r 时，电源输出功率最大，$P{\tiny max} = \frac{E^2}{4r}$