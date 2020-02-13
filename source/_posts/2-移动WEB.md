---
title: 移动WEB
date: 2017-03-05 12:42:32
tag:
---
# day-01

* 在页面做2D、动画效果，页面表现更为丰富；
* 目标：
  * **2D：重点居中方案；**
  * 动画：知道动画属性代想·表什么意见即可；



# 2D变换

* 使元素旋转缩放等，页面表现丰富。配合动画做效果；

## 坐标系

### 介绍

* 2D：direction 方向 坐标系：

![](./imgs/007.png)

- 每个盒子都自我构成一个自己的坐标系。

![1568896378748](imgs/1568896378748.png)





### 工具

* 伸出左胳膊，手掌朝向自己，四指朝下，大拇指X轴，四指Y轴；







## 移动 translate

* 可以改变元素在页面中的位置，类似**定位**；

### 语法

```css
/* 单个写*/
transform: translateX(100px);
transform: translateY(-50%);

/* 合起来写*/
transform: translate(100px, 100px);

/* 百分数*/
transform: translate(50%, 50%);
```

### 与定位(、margin)的区别

* 定位：
  * **会影响其他盒子位置（脱离标准流）；**
  * 行内元素定位，直接变为块级元素；
* 移动：
  * **不影响其他元素的位置；**
  * 在行内元素无效；对块级元素生效；
* 扩展：http://www.caotama.com/4285.html；

### 场景

* **居中的解决方案：**不用关心被居中盒子本身的宽高是多少；
* 微调盒子的位置；



## 旋转 rotate

* 旋转使页面表现更为丰富

### 语法

* 单位是deg，正值顺时针。关键词：**绕着；**

```css
transform: rotate(45deg);
```

### 特点

* 默认：为中心点旋转；

* 补充：伪元素

  * 为什么叫伪元素：页面HTML结构中没有元素，但是页面中却真实存在；

  * 常用：做小图标引用；

  * 特点：

    * 行内元素，
    * **content属性不能丢；**
    * div::before:hover不能这样用；用法：div:hover::before
    * **伪元素只能用在双标签上；**







## 中心点（了解）

* 改变中心点位置，2D转化（旋转、缩放）的效果不一样；

* 语法：默认旋转的基准点是中心点；50% 50%；

```css
/* 具体PX值*/
transform-origin:100px 100px;
/* 百分数*/
transform-origin:50% 50%;
/* 方位名词*/
transform-origin:left bottom;

/* 单个参数，第二个值默认为50%*/
transform-origin:0;
```





## 缩放 scale

* 场景：鼠标悬浮，盒子放大；

* 后面的参数 为 倍数；（无单位）

```css
/* 长度、宽度方向 缩放 */
transform:scale(2,3);

/* 长度、宽度方向 缩放为同一个比例*/
transform:scale(2);
transform:scale(0.5);
```

* 特点
  * 会受 中心点 影响；
  * **下面的子元素、文字、属性会被缩放；**
  * 使用场景：放大父级元素，下面的所有子元素都会跟着被放大；



## 2D简写

* 更为简洁地综合起来写2D相关的属性；

* 单独多次写，不生效，下面的会把上面的层叠掉；

```css
transform: translate(x,y);
transform: rotate(90deg);
```

* 使用顺序不同，出现的效果不同，因为旋转会改变初始轴向；

```css
/* 移动在旋转前面 */
transform: translate(x,y) rotate(90deg) scale(x,y);

/* 旋转在前面 */
transform: rotate(90deg) translate(x,y) scale(x,y);
```



# animation 动画

- 页面内实现一些列动画，可以循环播放，也可以播放几次；使丰富页面；

## 定义动画

- 要掌握实现动画最基本核心步骤，可以完成一个动画；

### 介绍

- 动画 animation 是CSS3中具有**颠覆性**的特征之一，可通过设置一个元素在多个时间节点上的不同样式来达到一个动画的效果；

### 语法

- 三要素：1定义及调用；2.时间

```css
/* 1. 定义:*/ 帧
@keyframes dong_hua {
    /* 开始状态:*/
    from {
        transform: translateX(0px);
        background-color: red;
    }
    /* 结束状态 */
    to {
        transform: translateX(1000px);
        background-color: #222;
    }
}

div {
    /* 调用:*/
    animation-name: dong_hua;
    
    /* 2. 时间:*/
    animation-duration: 3s;
}
```

### 重点

- 和过度的区别：动画可以实现**更多的控制**，且可连续自动播放；
- 拓展思路：节点里可以写2D转化，也可以写我们基础班学习的各种属性；



## 动画序列

- 时间节点，可以更为精准的控制动画的多个状态节点，动画的变化更为丰富；

### 语法

```css
@keyframes name {
    /* 开始状态:*/
    from {
    }
    /* 结束状态 */
    to {
    }
}

@keyframes name {
    /* 开始状态:*/
    0% {
        
    }
    50% {
    }
    75% {
    }
    83% {
       
    }
    
    /* 结束状态 */
    100% {
    }
}
```

### 重点

- 动画序列就是时间节点时的状态；
- **动画从开始执行到经过动画节点，都是基于上一个状态进行变化；**





## 动画属性

- 丰富我们的动画特性，能做更多的属性控制；

### 语法

![](./imgs/009.png)

- animation-timing-function：动画 运动 速度曲线：速度快慢的体现；

```css
div{
    /* 匀速  */
    animation-timing-function: linear;

    /* 慢-快-慢  默认值  */
    animation-timing-function: ease;

    /* 慢-快  */
    animation-timing-function: ease-in;

    /* 快-慢  */
    animation-timing-function: ease-out;

    /* 慢-快-慢  */
    animation-timing-function: ease-in-out;
}
```

- animation-timing-function：steps(n)  分步 实现 老电影一帧一帧，整个动画分为几步骤完成

```css
/* 分步 实现 老电影一帧一帧，整个动画分为几步骤完成*/
animation-timing-function: steps(n);
```

- animation-delay：动画推迟多久执行；动画得等待。
- animation-iteration-count：播放循坏次数 1 2  infinite无限次 

```css
div{
    /* 指定次数设置  */
    animation-iteration-count: 2;

    /* 无限次数设置  */
    animation-iteration-count: infinite;
}
```

- animation-direction：循环方向：若0% 红色; 100% 黑色

```css
div{
    /*1 默认值 0-100 */
    animation-direction: normal;
    
    /*2 100-0 */
    animation-direction: reverse;
    
    /*3 0-100-0 */
    animation-direction: alternate;

    /*4 100-0-100 */
    animation-direction: alternate-reverse;
}
```

- animation-fill-mode：动画等待或者结束的状态;

```css
div{
    /*1 动画结束后，元素样式停留在 动画结束时的状态 */
    animation-fill-mode: forwards;
    
    /*2 在延迟等待的时间内，元素样式停留在 动画开始的状态 
    动画结束的时候，回到div本身的样式（回到起始状态）
    */
    animation-fill-mode: backwards;
    
    /*3 同时设置了 forwards和backwards两个属性值
    在动画等待时间，样式为元素样式停留在 动画开始的状态，
    动画结束时，元素样式停留在 动画结束时的样式
     */
    animation-fill-mode: both;
}
```

- animation-play-state：暂停和播放

```css
div{
    /*1 播放 */
    animation-play-state: running;
    /*2 暂停*/
    animation-play-state: paused;
}
```

### 注意

- 设置 animation-direction ，需设置动画 多次 执行；
- 设置 animation-fill-mode，设置forwards ，动画不能设置 无限 执行；





## 简写

- 简单把动画属性写在一起，代码简单；vscode有提示；

### 语法

- 简写语法：动画名称  持续时间  速度曲线  等待时间  执行次数  执行的方向  动画等待或结束的状态

```css
div{
    animation: name duration timing-function delay iteration-count direction fill-mode;
}
```

- 组动画：需要用 逗号 隔开每一个动画的相关属性设定（一个动画的多个属性设定之间用空格隔开）。

```css
animation: 动画名1 5s linear, 动画名2 2s linear;
```

### 重点

- animation-play-state 没有在简写内
- 记忆：知道意思即可，记不住去查就行；



## 案例分析步骤

- 目标：自己拿到需求，可以按照步骤进行分解动画步骤，最后满足业务需求；

### 步骤

- 布局：不要被动画干扰，先把动画屏蔽掉；
- 分析：
  - **几个动画时间节点？**
  - 节点设置？CSS样式；
  - 其他动画属性？
    - 一样的动画分析一个；
    - 连续动画和分步动画？
    - 匀速变化？还是变速变化？
    - 执行多次？无限次？

### 案例

- 热点：
  - 底图：w:797px;h:616px;
  - 分析：
    - 动画节点：3个；
    - 节点设置：缩放？或者width 0-40-70?
    - 动画属性：等待？线性？时间1.2s;



- 大白熊：
  - 盒子：宽高
  - 第一个动画：左侧移动到中间
  - 第二个动画：自己动（变换熊的姿势）
    - 节点：2个
    - 节点设置：背景图位置移动
    - 动画属性：分帧动画，共8帧







# 5.前缀（了解）

- 新特性，对各家浏览器更好的兼容，以便以后出了兼容问题，我们可以从这个方向想；

## 介绍

- -moz-：代表 firefox 浏览器私有属性
- -ms-：代表 ie 浏览器私有属性
- -webkit-：代表 safari、chrome 私有属性
- -o-：代表 Opera 私有属性

## 语法

```css
-moz-border-radius: 10px; 
-webkit-border-radius: 10px; 
-o-border-radius: 10px; 
border-radius: 10px;   /* 应该将不带前缀的属性写在最后 */
```

- 没有工程化工具，根据业务需要写这些前缀，解决样式的兼容；
- 以后，有了工程化工具，注意这些工具包的配置就可以。

























