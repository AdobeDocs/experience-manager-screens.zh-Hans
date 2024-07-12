---
title: 播放器设备的硬件选择准则
description: 了解AEM Screens Player设备的硬件选择准则。
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 3%

---


# 播放器设备的硬件选择准则 {#hardware-selection}

以下部分提供了AEM Screens Player的硬件选择指南。

## 重要注意事项 {#important-considerations}

* 始终为PC播放器和显示面板或投影仪提供&#x200B;***商业***&#x200B;或&#x200B;***工业***&#x200B;级组件。

* 始终与为数字标牌市场提供服务的供应商接洽。
* 始终考虑环境因素，如环境温度和相对湿度。
* 始终查看电源要求和电源调节。
* 仔细查看应用程序所需的性能需求和I/O端口。

## 硬件配置 {#hardware-configurations}

下表总结了AEM Screens项目的硬件配置以及典型用例：

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>播放器配置</strong></td>
   <td><strong>处理器</strong></td>
   <td><strong>内存</strong></td>
   <td><strong>存储SSD</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>显示区</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>典型用例</strong></td>
  </tr>
  <tr>
   <td>基本</td>
   <td>双核、i3或入门级四核英特尔®凌动处理器</td>
   <td><p>4 GB内存</p> <p>2 MB缓存</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>板载</td>
   <td>1920 x 1080</td>
   <td>DVI<br />以太网/无线，<br /> 2个USB</td>
   <td>
    <ul>
     <li>标准全屏循环<br /> </li>
     <li>日划分</li>
    </ul> </td>
  </tr>
  <tr>
   <td>标准</td>
   <td>四核、英特尔®酷睿™ i5处理器</td>
   <td><p>8 GB内存</p> <p>4 MB缓存</p> </td>
   <td>128 GB</td>
   <td>板载</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI、HDMI<br />以太网/无线、<br /> 2个USB</td>
   <td>
    <ul>
     <li>单个Source动态内容</li>
     <li>简单交互式</li>
     <li>1-3区域布局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>高级</td>
   <td>四核，带超线程，英特尔®酷睿™ i7处理器</td>
   <td><p>16 GB内存</p> <p>8 MB缓存</p> </td>
   <td>256 GB</td>
   <td>专用显卡GPU</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI、HDMI<br />以太网/无线、<br /> 4个USB</td>
   <td>
    <ul>
     <li>4个或更多内容区域，并行视频播放</li>
     <li>多页交互式</li>
     <li>多Source数据触发器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
