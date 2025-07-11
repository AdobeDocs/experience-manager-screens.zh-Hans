---
title: 将组件添加到渠道
description: 了解有关在AEM Screens项目中将组件添加到渠道的更多信息。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 5%

---

# 将组件添加到渠道{#adding-components-to-a-channel}

组件是AEM (Adobe Experience Manager)体验的基本元素。 您可以在AEM Screens项目中使用多个组件并将其添加到渠道。

## AEM Screens中的组件 {#components-in-aem-screens}

AEM Screens提供了可在Screens项目中使用的各种AEM组件。

### 查看AEM Screens组件 {#viewing-aem-screens-components}

每当您创建AEM Screens项目时，您都会看到可添加到该项目的默认组件列表。

要查看Screens项目的默认组件，请执行以下步骤：

1. 单击渠道。 例如，**`We.Retail In Store`** > **频道** > **空闲频道**。

1. 单击操作栏中的&#x200B;**编辑**。
1. 在AEM编辑器中，单击侧栏中的&#x200B;**+**&#x200B;图标。
1. 此时将显示默认包含在AEM Screens项目中的所有组件，如下图所示。

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 添加新组件 {#adding-a-new-component}

AEM提供了其他几个组件。 您始终可以向项目添加其他组件（默认情况下不包括），因为这些组件与AEM Screens兼容。

以下示例显示如何向AEM Screens项目添加Livefyre组件：

1. 单击要在其中添加组件的渠道。 例如，**`We.Retail In Store`** > **频道** > **空闲频道**。

1. 单击操作栏中的&#x200B;**编辑**。
1. 单击&#x200B;**设计**&#x200B;模式。
1. 单击右侧的整个设计编辑器并单击设置符号，以便打开&#x200B;**Parsys设计**&#x200B;对话框。
1. 您可以单击要导入到AEM Screens项目的组件。 以下示例显示将&#x200B;**Livefyre**&#x200B;组件添加到AEM Screens项目。

![正在添加_组件](assets/adding_components.gif)

>[!NOTE]
>
>同样，您可以向项目中添加任意数量的与AEM Screens兼容的其他新组件。

## 了解AEM屏幕组件 {#understanding-aem-screen-components}

以下部分将介绍可在项目中使用的AEM Screens组件。

>[!NOTE]
>
>要查看任何组件的属性，请单击组件，然后单击锤子图标以打开/查看属性。

### 应用程序 {#application}

**应用程序**&#x200B;组件允许您向渠道添加应用程序。

应用程序组件具有以下属性：

| **属性** | **描述** |
|---|---|
| ***应用程序路径*** | 单击应用程序所在的绝对路径。 |
| ***持续时间（毫秒）*** | 单击应用程序的持续时间。 默认情况下，持续时间设置为–1，这意味着元素将永远运行（即单页应用程序）。 设置持续时间值>0，显示指定持续时间的元素，然后转到下一个元素。 |

以下示例显示如何嵌入应用程序组件及其属性的预览：

![添加_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>请参阅上面的示例，以查看下面每个组件的属性。

### 渠道 {#channel}

**渠道**&#x200B;组件允许您向项目添加整个渠道。

渠道组件具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>渠道路径</em></strong></td>
   <td>选择应用程序所在的绝对路径。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>选择渠道的整个持续时间。 将持续时间设置为–1表示嵌入的通道在特定通道中运行其全长。</td>
  </tr>
 </tbody>
</table>

### 嵌入式页面 {#embedded-page}

**嵌入页面**&#x200B;允许您向项目添加嵌入页面。 例如，它可以是Web应用程序或产品目录。

嵌入式页面具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>页面路径<br /> </em></strong></td>
   <td>选择存在渠道的此绝对路径。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>选择渠道的整个持续时间。 将持续时间设置为–1表示嵌入的通道在特定通道中运行其全长。</td>
  </tr>
 </tbody>
</table>

### 嵌入式序列 {#embedded-sequence}

>[!NOTE]
>
>要详细了解嵌入序列，请参阅“创作Screens”部分下的[嵌入序列](embedded-sequences.md)。

嵌入式序列允许您在现有渠道（以及其他资源）中添加嵌入式序列渠道。

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
   <td>选择渠道的整个持续时间。 将持续时间设置为–1表示嵌入的通道在特定通道中运行其全长。</td>
  </tr>
  <tr>
   <td><strong><em>战略</em></strong></td>
   <td>将其设置为<strong>原始</strong>或<strong>单个</strong>。 将该值设置为<strong>原始</strong>表示子序列在父序列的每个循环上完全运行。 其他可能的值为<strong>single</strong>。 每次运行时，此类值只显示子序列的一个项。 例如，第一个循环中的第一个项和第二个循环中的第二个项。</td>
  </tr>
 </tbody>
</table>

### 动态嵌入式序列 {#dynamic-embedded-sequence}

动态嵌入式序列允许您添加与上述序列类似的序列，但渠道角色除外。

要了解有关嵌入序列的更多信息，请参阅“创作Screens”部分下的[嵌入序列](embedded-sequences.md)。

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
   <td>选择渠道的整个持续时间。 将持续时间设置为–1表示嵌入的通道在特定通道中运行其全长。</td>
  </tr>
  <tr>
   <td><strong><em>战略</em></strong></td>
   <td>将其设置为<strong>原始</strong>或<strong>单个</strong>。 将该值设置为<strong>原始</strong>表示子序列在父序列的每个循环上完全运行。 其他可能的值为<strong>single</strong>。 每次运行时，此类值只显示子序列的一个项。 例如，第一个循环中的第一个项和第二个循环中的第二个项。</td>
  </tr>
 </tbody>
</table>

### 体验片段 {#experience-fragment}

体验片段允许您将体验片段（由一个或多个组件组成，包括可在页面中引用的内容和布局）添加到您的AEM Screens渠道中。 将组件拖放到AEM编辑器中，然后单击体验片段。

要了解有关如何创建体验片段并将其应用于AEM Screens项目的更多信息，请参阅[使用体验片段](experience-fragments-in-screens.md)。

![费用](assets/exp.gif)

| **属性** | **描述** |
|---|---|
| **体验片段** |
| ***体验片段*** | 选择体验片段。 |
| ***持续时间*** | 选择在渠道中播放的体验片段的整个持续时间。 |
| **脱机配置** |
| ***客户端库*** | JavaScript和CSS文件。 |
| ***静态文件*** | 可作为离线配置添加到体验片段的静态文件。 |

>[!NOTE]
>
>从此组件添加的&#x200B;**客户端库**&#x200B;和&#x200B;**静态文件**&#x200B;以及已配置的&#x200B;**客户端库**&#x200B;和从体验片段的&#x200B;**属性**&#x200B;添加的静态文件。

### 图像 {#image}

图像允许您向渠道添加图像。

图像资产具有三个选项卡，即&#x200B;**图像**、**辅助功能**&#x200B;和&#x200B;**序列**：

| **属性** | **描述** |
|---|---|
| **图像** |
| ***图像资产*** | 单击图像资源。 |
| ***标题*** | 图像的标题。 |
| ***链接到*** | 添加指向该图像的链接。 |
| ***描述*** | 图像的简短描述。 |
| ***大小*** | 图像的大小。 |
| **辅助功能** |
| ***替换文本*** | 图像的替换文本。 |
| **序列** |
| ***持续时间*** | 默认情况下，持续时间设置为&#x200B;*8000毫秒*。 如果要更改图像的播放持续时间，请更新&#x200B;**持续时间**&#x200B;字段。 |

### 过渡 {#transition}

使用过渡组件，您可以向Screens项目添加过渡。

下图显示了编辑器中的过渡组件（通过拖放方式添加）。

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

单击过渡图标，然后单击&#x200B;**配置** （扳手图标）以打开&#x200B;**过渡**&#x200B;对话框。 此对话框包括三个选项卡：

* **过渡**
* **序列**
* **激活**

>[!NOTE]
>
>默认情况下，序列设置为600毫秒。 您可以使用&#x200B;**序列**&#x200B;选项卡将过渡序列更新为其他值。

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
   <td><p>元素之前和元素之后之间的过渡类型。 转换<strong>类型</strong>包含以下选项：</p>
    <ul>
     <li><strong>一般</strong></li>
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
   <td>选择过渡的整个持续时间。 默认情况下，设置为600毫秒。</td>
  </tr>
  <tr>
   <td><strong>激活</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>保持活动状态起始日期</em></strong></td>
   <td>描述过渡何时可以处于活动状态的时间戳。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>保持活动状态结束日期</em></strong></td>
   <td>时间戳描述过渡处于活动状态之前的各个时间。</td>
  </tr>
  <tr>
   <td><strong><em>计划</em></strong></td>
   <td>添加预定义的计划。</td>
  </tr>
 </tbody>
</table>

### 视频 {#video}

使用视频组件，您可以向Screens项目添加视频。

视频组件具有以下属性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><em><strong>视频资产</strong></em></td>
   <td>单击视频链接。</td>
  </tr>
  <tr>
   <td><em><strong>持续时间</strong></em></td>
   <td>选择视频的持续时间。 默认情况下，持续时间设置为–1，这意味着元素将永远运行。 设置持续时间值&gt;0，显示指定持续时间的元素，然后转到下一个元素。<br /> </td>
  </tr>
  <tr>
   <td><em><strong>呈现</strong></em></td>
   <td><p>如果视频长宽比不适合屏幕，您可以将渲染调整为<strong>包含</strong>或<strong>封面</strong>。</p> <p><em>Contain</em>表示显示完整视频，并且缺少的区域使用黑色边框填充。</p> <p><em>封面</em>表示视频覆盖整个视区，但两侧溢出的部分被隐藏。</p> </td>
  </tr>
  <tr>
   <td><em><strong>大小</strong></em></td>
   <td>视频的大小。</td>
  </tr>
 </tbody>
</table>
