---
title: 播放器裝置的硬體選擇准則
description: 播放器裝置的硬體選擇准則
source-git-commit: 7fdd812c71c995424a27db18264ef2db420d5717
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# 播放器裝置的硬體選擇准則 {#hardware-selection}

下節提供AEM Screens播放器的硬體選擇准則。

## 重要注意事项 {#important-considerations}

* 永遠來源 ***商業*** 或 ***工業*** PC播放器及顯示面板或投影機的等級元件。

* 永遠與數位看板市場的供應商互動。
* 請務必考量環境因素，例如環境溫度和相對濕度。
* 請務必檢閱電源需求與電源調節。
* 請仔細檢閱應用程式所需的效能需求和I/O連線埠。

## 硬體組態 {#hardware-configurations}

下表總結列出AEM Screens專案的硬體組態與典型使用案例：

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>播放器設定</strong></td>
   <td><strong>處理器</strong></td>
   <td><strong>内存</strong></td>
   <td><strong>儲存固態硬碟</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>显示器</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>典型使用案例</strong></td>
  </tr>
  <tr>
   <td>基本</td>
   <td>雙核心、i3或入門級四核心Intel® Atom處理器</td>
   <td><p>4GB記憶體</p> <p>2MB快取記憶體</p> </td>
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128GB</p> </td>
   <td>內建</td>
   <td>1920x1080</td>
   <td>DVI、<br /> 乙太網路/無線、<br /> 2個USB</td>
   <td>
    <ul>
     <li>標準全熒幕回圈<br /> </li>
     <li>日時段分割</li>
    </ul> </td>
  </tr>
  <tr>
   <td>标准</td>
   <td>四核心、Intel® Core i5處理器</td>
   <td><p>8GB記憶體</p> <p>4MB快取記憶體</p> </td>
   <td>128 GBB</td>
   <td>內建</td>
   <td>3840x2160 (4K)</td>
   <td>DVI、HDMI<br /> 乙太網路/無線、<br /> 2個USB</td>
   <td>
    <ul>
     <li>單一來源動態內容</li>
     <li>簡單互動式</li>
     <li>1-3區域配置</li>
    </ul> </td>
  </tr>
  <tr>
   <td>高级</td>
   <td>四核心，含超執行緒、Intel® Core i7處理器</td>
   <td><p>16GB記憶體</p> <p>8MB快取記憶體</p> </td>
   <td>256 GB</td>
   <td>專用圖形GPU</td>
   <td>3840x2160 (4K)</td>
   <td>DVI、HDMI<br /> 乙太網路/無線、<br /> 4個USB</td>
   <td>
    <ul>
     <li>4個或多個內容區域，同時播放視訊</li>
     <li>多頁互動式</li>
     <li>多來源資料觸發程式</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
