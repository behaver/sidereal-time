# SiderealTime

## 简介

SiderealTime 是用于天文学恒星时计算的 JS 组件。

## 背景知识

**恒星时**是天文学和大地测量学标定的天球子午圈位置的值。恒星时是根据地球自转来计算的，它的基础是恒星日。由于地球环绕太阳的公转运动，恒星日比平太阳日(也就是日常生活中所使用的日)短约 1/365 (相应约四分钟或一度)。

**本地恒星时** 的定义是一个 *地方的子午圈* 与天球的 *春分点* 之间的时角，各地方的经度不同，所以子午圈不同，因此 地球上每个地方的恒星时都与它的经度有关。

恒星时的参考点是**春分点**，所以春分点的变化也将对恒星时产生影响。

由于地球的章动春分点在天球上并不固定，因此恒星时又分 **真恒星时** 和 **平恒星时** 。真恒星时是通过直接测量子午线与实际的春分点之 间的时角获得的，平恒星时则忽略了地球的章动。真恒星时与平恒星时之间的差异最大可达约 0.4 秒。

一个地方的 **当地恒星时** 与 **格林尼治天文台的恒星时** 之间的差就是这个 **地方的经度**。因此通过观测恒星时可以确定当地的经度(假如格林尼治天文台的恒星时已知的话)或者可以确定时间(假如当地的经度已知的话)。

## 用例

使用 npm 安装组件库，在项目目录下执行：

`npm install @behaver/sidereal-time`

---

使用 SiderealTime 组件进行恒星时计算：

```js
const SiderealTime = require('@behaver/sidereal-time');
const { JDateRepository } = require('@behaver/jdate');

// 实例化基于当前时间的儒略时间对象
let jdr = new JDateRepository(new Date(), 'date');

// 实例化观测经度为 120 的恒星时组件
let st = new SiderealTime(jdr, 120);

// 输出 地球自转角(ERA)
console.log(st.ERA);

// 输出 平恒星时
console.log(st.meanVal);

// 输出 真恒星时
console.log(st.trueVal);
```

## API

`constructor(obTime, obGLon = 0, options)` 构造函数
* 参数 obTime: 观测时间 JDateRepository 对象
* 参数 obGLon: 观测经度, 缺省为 0 , 单位: 度
* 参数 options.precessionModel: 岁差计算模型, 包括: iau2006, iau2000, iau1976
* 参数 options.nutationModel: 章动计算模型, 包括: iau2000b, lp

`get ERA()` 获取 地球自转角(ERA)，单位：角秒

`get meanVal()` 获取 平恒星时，单位：角秒

`get trueVal()` 获取 真恒星时，单位：角秒

## 许可证书

The MIT license.