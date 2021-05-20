---
title: 播放器设备的硬件选择准则
description: 播放器设备的硬件选择准则
source-git-commit: 7fdd812c71c995424a27db18264ef2db420d5717
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 2%

---


# 播放器设备{#hardware-selection}的硬件选择指南

以下部分提供了AEM Screens播放器的硬件选择指南。

## 重要注意事项{#important-considerations}

* 始终为PC播放器和显示面板或投影仪提供&#x200B;***Commercial***&#x200B;或&#x200B;***Industrial***&#x200B;等级组件。

* 请始终与提供数字标牌市场的供应商接洽。
* 始终考虑环境因素，如环境温度和相对湿度。
* 请务必查看电源要求和电源调节。
* 仔细审查应用程序所需的性能需求和I/O端口。

## 硬件配置{#hardware-configurations}

下表概述了硬件配置以及AEM Screens项目的典型用例：

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>播放器配置</strong></td>
   <td><strong>处理器</strong></td>
   <td><strong>内存</strong></td>
   <td><strong>存储固态硬盘</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>显示器</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>典型用例</strong></td>
  </tr>
  <tr>
   <td>基本</td>
   <td>双核、i3或入门级四核英特尔®凌动处理器</td>
   <td><p>4GB内存</p> <p>2MB高速缓存</p> </td>
   <td><p>·ChromeOS 32 GB</p> <p>· Windows 128 GB</p> </td>
   <td>板载</td>
   <td>1920 x 1080</td>
   <td>DVI，<br />以太网/无线，<br /> 2xUSB</td>
   <td>
    <ul>
     <li>标准全屏循环<br /> </li>
     <li>将日期分开</li>
    </ul> </td>
  </tr>
  <tr>
   <td>标准</td>
   <td>四核，英特尔®酷睿i5处理器</td>
   <td><p>8GB内存</p> <p>4MB高速缓存</p> </td>
   <td>128吉比特</td>
   <td>板载</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br />以太网/无线，<br /> 2xUSB</td>
   <td>
    <ul>
     <li>单源动态内容</li>
     <li>简单交互式</li>
     <li>1-3区域布局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>高级</td>
   <td>四核超线程，英特尔®酷睿i7处理器</td>
   <td><p>16GB内存</p> <p>8MB的高速缓存</p> </td>
   <td>256 GB</td>
   <td>专用图形GPU</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br />以太网/无线，<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4个或更多内容区域，并行视频播放</li>
     <li>多页面交互式</li>
     <li>多源数据触发器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
