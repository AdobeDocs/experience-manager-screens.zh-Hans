---
title: 向渠道添加组件
seo-title: 向渠道添加组件
description: 可查看本页以了解有关向 AEM Screens 项目中的渠道添加组件的更多信息。
seo-description: 可查看本页以了解有关向 AEM Screens 项目中的渠道添加组件的更多信息。
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 向渠道添加组件{#adding-components-to-a-channel}

组件是 AEM (Adobe Experience Manager) 体验的基本元素。您可以使用多个组件，并将其添加到 AEM Screens 项目中的渠道。

## AEM Screens 中的组件 {#components-in-aem-screens}

AEM Screens 提供了可用于 Screens 项目的不同 AEM 组件。

### 查看 AEM Screens 组件 {#viewing-aem-screens-components}

无论何时创建 AEM Screens 项目，您都将会看到可添加到项目的默认组件列表。

要查看 Screens 项目的默认组件，请按照以下步骤操作：

1. 选择渠道。例如，**We.Retail In Store** --&gt; **渠道** --&gt; **Idle Channel**。

1. 从操作栏中单击&#x200B;**编辑**&#x200B;以打开 AEM 编辑器。
1. 单击侧栏中的 **+** 图标以打开组件。
1. 此时会显示 AEM Screens 项目中默认包含的所有组件，如下图所示。

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 添加新组件 {#adding-a-new-component}

AEM 提供了许多其他组件。鉴于这些组件与 AEM Screens 兼容，您始终可以向项目中添加其他组件（默认情况下未包含）。

以下示例显示了如何向 AEM Screens 项目中添加 Livefyre 组件：

1. 选择要添加新组件的渠道。例如，**We.Retail In Store** --&gt; **渠道** --&gt; **Idle Channel**。

1. 单击操作栏中的**编辑**以打开编辑器。
1. Select **Design** mode.
1. 选择右侧的整个设计编辑器，然后单击设置符号以打开 **ParSys 设计**&#x200B;对话框。
1. 您可以选择要导入到 AEM Screens 项目的组件。以下示例显示 **了向AEM Screens项目添加的Livefyre** 组件。

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>同样，您可以向项目中添加任意数量的与 AEM Screens 兼容的新组件。

## 了解 AEM Screens 组件 {#understanding-aem-screen-components}

以下部分介绍了可在项目中使用的AEM Screens组件。

>[!NOTE]
>
>要查看任何组件的属性，请选择该组件，然后单击锤子图标以打开/查看属性。

### 应用程序 {#application}

**应用程序**&#x200B;组件允许您向渠道中添加应用程序。

应用程序组件具有以下属性：

| **属性** | **描述** |
|---|---|
| ***应用程序路径*** | 选择应用程序所在的绝对路径。 |
| ***持续时间（毫秒）*** | 选择应用程序的持续时间。默认情况下，持续时间设置为-1，这意味着元素将永远运行（即单页应用程序）。 将持续时间值设置为大于 0 会在指定的持续时间内显示该元素，然后移至下一个元素。 |

以下示例显示了如何嵌入应用程序组件以及其属性的预览：

![adding_components应用程序](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>请参阅上面的示例以查看下面每个组件的属性。

### 渠道 {#channel}

**渠道**&#x200B;组件允许您向项目中添加完整的渠道。

渠道组件具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>渠道路径</em></strong></td>
   <td>选择渠道所在的绝对路径。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>选择渠道的整个持续时间。将持续时间设置为-1表示嵌入式渠道将在特定渠道中运行其完整长度。</td>
  </tr>
 </tbody>
</table>

### 嵌入式页面 {#embedded-page}

**嵌入式页面**&#x200B;允许您向项目中添加嵌入式页面。例如，它可以是 Web 应用程序或产品目录。

嵌入式页面具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>页面路径<br /> </em></strong></td>
   <td>选择页面所在的绝对路径。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>选择渠道的整个持续时间。将持续时间设置为-1表示嵌入式渠道将在特定渠道中运行其完整长度。</td>
  </tr>
 </tbody>
</table>

### 嵌入式序列 {#embedded-sequence}

>[!NOTE]
>
>Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

嵌入式序列允许您在现有渠道（包含其他资产）内添加嵌入式序列渠道。

嵌入式序列具有以下页面属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td>渠道路径</td>
   <td>选择要包含在渠道中的序列的绝对路径。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>选择渠道的整个持续时间。将持续时间设置为-1表示嵌入式渠道将在特定渠道中运行其完整长度。</td>
  </tr>
  <tr>
   <td><strong><em>战略</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### 动态嵌入式序列 {#dynamic-embedded-sequence}

动态嵌入式序列允许您添加与上述类似的序列，但渠道角色除外。

Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

动态嵌入式序列具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>渠道分配角色</em></strong><br /> </td>
   <td>输入渠道角色。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>选择渠道的整个持续时间。将持续时间设置为-1表示嵌入式渠道将在特定渠道中运行其完整长度。</td>
  </tr>
  <tr>
   <td><strong><em>战略</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### 体验片段 {#experience-fragment}

体验片段允许您将体验片段（由一个或多个组件组成的组件，包括可在页面中引用的内容和布局）添加到AEM Screens渠道。 将组件拖放到AEM编辑器中，然后选择体验片段。

要了解有关如何创建体验片段并将其用于AEM Screens项目的更多信息，请参阅使 [用体验片段](experience-fragments-in-screens.md)。

![exp](assets/exp.gif)

| **属性** | **描述** |
|---|---|
| **体验片段** |
| ***体验片段*** | 选择体验片段。 |
| ***持续时间*** | 选择在渠道中播放的体验片段的整个持续时间。 |
| **脱机配置** |
| ***客户端库*** | Javascript和CSS文件。 |
| ***静态文件*** | 静态文件，您可以将其作为脱机配置添加到体验片段。 |

>[!NOTE]
>
>从 **此组件添加的客户端库和静态文件** ，除了已配置的客户端库和从体验片段的属性添加的静态 ************&#x200B;文件外。

### 图像 {#image}

图像允许您向渠道中添加图像。

图像资产有三个选项卡：**图像**、**辅助功能**&#x200B;和&#x200B;**序列**：

| **属性** | **描述** |
|---|---|
| **图像** |
| ***图像资产*** | 选择图像资产。 |
| ***标题*** | 图像的标题。 |
| ***链接到*** | 添加指向图像的链接。 |
| ***描述*** | 图像的简短描述。 |
| ***大小*** | 图像的大小。 |
| **辅助功能** |
| ***替换文本*** | 图像的替换文本。 |
| **序列** |
| ***持续时间*** | 选择图像的整个持续时间。将持续时间设置为-1表示嵌入式图像将在特定渠道中运行其全长。 |

### 过渡 {#transition}

过渡组件允许您向 Screens 项目中添加过渡。

下图显示了向编辑器添加的过渡组件（通过拖放添加）。

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

选择过渡图标，然后单击 **配置** （扳手图标）以打开“过渡 **** ”对话框。 该对话框包括三个选项卡：

* **过渡**
* **序列**
* **激活**

>[!NOTE]
>
>默认情况下，序列设置为600毫秒。 您可以使用“序列”选项卡将过渡序列更新为 **其他值** 。

![过渡](assets/transition.gif)

过渡组件具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong>过渡</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>类型</em></strong></td>
   <td><p>前一个元素和后一个元素之间的过渡类型。过渡 <strong>类型</strong> ，包括以下选项：</p>
    <ul>
     <li><strong>标准</strong></li>
     <li><strong>淡化</strong></li>
     <li><strong>从右侧滑入</strong></li>
     <li><strong>从左侧滑入</strong></li>
     <li><strong>从顶部滑入</strong></li>
     <li><strong>从底部滑入</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>序列</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>持续时间</em></strong></td>
   <td>选择过渡的整个持续时间。默认情况下，它设置为600 ms。</td>
  </tr>
  <tr>
   <td><strong>激活</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>活动自</em></strong></td>
   <td>描述何时过渡可处于活动状态的时间戳。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>活动到</em></strong></td>
   <td>时间戳，描述直到过渡可以处于活动状态。</td>
  </tr>
  <tr>
   <td><strong><em>计划</em></strong></td>
   <td>添加预定义的计划。</td>
  </tr>
 </tbody>
</table>

### 视频 {#video}

视频组件允许您向 Screens 项目中添加视频。

视频组件具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><em><strong>视频资产</strong></em></td>
   <td>选择指向视频的链接。</td>
  </tr>
  <tr>
   <td><em><strong>持续时间</strong></em></td>
   <td>选择视频的持续时间。默认情况下，持续时间设置为-1，这意味着元素会一直运行。 将持续时间值设置为大于 0 会在指定的持续时间内显示该元素，然后移至下一个元素。<br /> </td>
  </tr>
  <tr>
   <td><em><strong>呈现</strong></em></td>
   <td><p>如果视频宽高比不适合屏幕，则可以将呈现方式调整为<strong>包含</strong>或<strong>覆盖</strong>。</p> <p><em>包含</em>表示显示完整视频，缺少的区域用黑色边框填充。</p> <p><em>覆盖</em>表示视频覆盖整个视区，但在侧面溢出的某些部分会被隐藏。</p> </td>
  </tr>
  <tr>
   <td><em><strong>大小</strong></em></td>
   <td>视频的大小。</td>
  </tr>
 </tbody>
</table>
