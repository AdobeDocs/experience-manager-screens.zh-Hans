---
title: 新增元件至管道
seo-title: Adding Components to a Channel
description: 請依照本頁面的說明深入瞭解如何在AEM Screens專案中新增元件至管道。
seo-description: Follow this page to learn more about adding components to channels in an AEM Screens project.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 7%

---

# 新增元件至管道{#adding-components-to-a-channel}

元件是AEM (Adobe Experience Manager)體驗的基本元素。 您可以在AEM Screens專案中使用許多元件，並將其新增至您的頻道。

## AEM Screens中的元件 {#components-in-aem-screens}

AEM Screens提供可在畫面專案中使用的不同AEM元件。

### 檢視AEM Screens元件 {#viewing-aem-screens-components}

每當您建立AEM Screens專案時，都會看到可新增至專案的預設元件清單。

若要檢視Screens專案的預設元件，請執行以下步驟：

1. 選取頻道。 例如， **We.Retail商店內** —> **頻道** —> **閒置頻道**.

1. 按一下 **編輯** 以開啟AEM編輯器。
1. 按一下 **+** 圖示來開啟元件。
1. AEM Screens專案中預設包含的所有元件都會顯示，如下圖所示。

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 新增元件 {#adding-a-new-component}

AEM提供許多其他元件。 您一律可以新增其他元件（預設不包含）至專案，前提是這些元件與AEM Screens相容。

以下範例說明如何將Livefyre元件新增至AEM Screens專案：

1. 選取您要新增元件的管道。 例如， **We.Retail商店內** —> **頻道** —> **閒置頻道**.

1. 按一下 **編輯** 以開啟編輯器。
1. 選取 **設計** 模式。
1. 選取右側的整個設計編輯器，然後按一下設定符號以開啟 **ParSys設計** 對話方塊。
1. 您可以選取要匯入至AEM Screens專案的元件。 以下範例顯示新增的 **Livefyre** 元件至AEM Screens專案。

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>同樣地，您也可以將與AEM Screens相容的任何其他新元件新增至專案。

## 瞭解AEM畫面元件 {#understanding-aem-screen-components}

下節將說明您可在專案中使用的AEM Screens元件。

>[!NOTE]
>
>若要檢視任何元件的屬性，請選取該元件，然後按一下槌子圖示以開啟/檢視屬性。

### 应用程序 {#application}

此 **應用** 元件可讓您將應用程式新增至頻道。

應用程式元件具有下列屬性：

| **属性** | **描述** |
|---|---|
| ***应用程序路径*** | 選取應用程式所在的絕對路徑。 |
| ***持续时间（毫秒）*** | 選取應用程式的持續時間。 根據預設，持續時間設為–1，這表示元素永遠執行（即單頁應用程式）。 設定持續時間值>0，顯示指定持續時間的元素，然後移至下一個專案。 |

以下範例說明如何內嵌應用程式元件及其屬性的預覽：

![adding_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>請參考上述範例，檢視下列每個元件的屬性。

### 渠道 {#channel}

此 **頻道** 元件可讓您將整個管道新增至專案。

Channel元件具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>渠道路径</em></strong></td>
   <td>選取應用程式所在的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道將在特定頻道中執行其完整長度。</td>
  </tr>
 </tbody>
</table>

### 嵌入式页面 {#embedded-page}

一個 **內嵌頁面** 可讓您將內嵌頁面新增至專案。 例如，它可以是網頁應用程式或產品目錄。

內嵌頁面具有下列屬性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>页面路径<br /> </em></strong></td>
   <td>選取此管道所在的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道將在特定頻道中執行其完整長度。</td>
  </tr>
 </tbody>
</table>

### 嵌入式序列 {#embedded-sequence}

>[!NOTE]
>
>請參閱 [內嵌順序](embedded-sequences.md) 在「製作畫面」區段底下，瞭解內嵌序列的詳細資訊。

內嵌序列可讓您在現有管道內新增內嵌序列管道（包含其他資產）。

內嵌序列具有下列頁面屬性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td>渠道路径</td>
   <td>選取您要包含在管道中的序列的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道將在特定頻道中執行其完整長度。</td>
  </tr>
  <tr>
   <td><strong><em>战略</em></strong></td>
   <td>設定為 <strong>原始</strong> 或 <strong>單一</strong>. 將值設定為 <strong>原始</strong> 表示子序號會在父序號的每個週期上完全執行。 另一個可能的值為 <strong>單一</strong> 而且每次執行只會顯示子序列的一個專案（例如，第一個回圈上的第一個專案、第二個回圈上的第二個專案，等等）。</td>
  </tr>
 </tbody>
</table>

### 动态嵌入式序列 {#dynamic-embedded-sequence}

動態內嵌序列可讓您新增與上述類似的序列，但頻道角色除外。

請參閱 [內嵌順序](embedded-sequences.md) 在「製作畫面」區段底下，瞭解內嵌序列的詳細資訊。

動態內嵌序列具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong><em>渠道分配角色</em></strong><br /> </td>
   <td>輸入頻道角色。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持续时间（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道將在特定頻道中執行其完整長度。</td>
  </tr>
  <tr>
   <td><strong><em>战略</em></strong></td>
   <td>設定為 <strong>原始</strong> 或 <strong>單一</strong>. 將值設定為 <strong>原始</strong> 表示子序號會在父序號的每個週期上完全執行。 另一個可能的值為 <strong>單一</strong> 而且每次執行只會顯示子序列的一個專案（例如，第一個回圈上的第一個專案、第二個回圈上的第二個專案，等等）。</td>
  </tr>
 </tbody>
</table>

### 体验片段 {#experience-fragment}

體驗片段可讓您將體驗片段（一或多個元件的群組，包括可在頁面中參考的內容和版面）新增到您的AEM Screens頻道。 將元件拖放至AEM編輯器並選取體驗片段。

若要進一步瞭解如何建立體驗片段並將其運用到AEM Screens專案，請參閱 [使用體驗片段](experience-fragments-in-screens.md).

![費用](assets/exp.gif)

| **属性** | **描述** |
|---|---|
| **体验片段** |
| ***体验片段*** | 選取體驗片段。 |
| ***持续时间*** | 選取在頻道中播放的體驗片段的整個持續時間。 |
| **脱机配置** |
| ***客户端库*** | Javascript和CSS檔案。 |
| ***静态文件*** | 您可以新增為離線設定至體驗片段的靜態檔案。 |

>[!NOTE]
>
>此 **使用者端資料庫** 和 **靜態檔案** 您從此元件新增的專案除了已設定的專案外 **使用者端資料庫** 以及從體驗片段的 **屬性**.

### 图像 {#image}

影像可讓您將影像新增至頻道。

影像資產有三個標籤，即 **影像**， **協助工具**、和 **序列**：

| **属性** | **描述** |
|---|---|
| **图像** |
| ***图像资产*** | 選取影像資產。 |
| ***标题*** | 影像的標題。 |
| ***連結至*** | 新增影像連結。 |
| ***描述*** | 影像的簡短說明。 |
| ***大小*** | 影像大小。 |
| **辅助功能** |
| ***替换文本*** | 影像的替代文字。 |
| **序列** |
| ***持续时间*** | 根據預設，持續時間設為 *8000毫秒*. 如果您想要變更影像的播放持續時間，請更新 **持續時間** 欄位。 |

### 过渡 {#transition}

「轉變」元件可讓您將轉變新增到Screens專案。

下圖顯示編輯器中的轉變元件（透過拖放方式新增）。

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

選取轉變圖示並按一下 **設定** （扳手圖示）開啟 **轉變** 對話方塊。 此對話方塊包含三個索引標籤：

* **过渡**
* **序列**
* **激活**

>[!NOTE]
>
>依預設，序列設定為600毫秒。 您可以使用將轉接序列更新為其他值 **序列** 標籤。

![轉變](assets/transition.gif)

轉變元件具有下列屬性：

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
   <td><p>元素之前和之後之間的轉變型別。 轉變 <strong>型別</strong> 包含下列選項：</p>
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
   <td>選取轉變的整個期間。 預設為600毫秒。</td>
  </tr>
  <tr>
   <td><strong>激活</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>啟用開始日期</em></strong></td>
   <td>說明轉變何時可以啟用的時間戳記。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>啟用結束日期</em></strong></td>
   <td>描述轉換生效時間的時間戳記。</td>
  </tr>
  <tr>
   <td><strong><em>计划</em></strong></td>
   <td>新增預先定義的排程。</td>
  </tr>
 </tbody>
</table>

### 视频 {#video}

視訊元件可讓您將視訊新增至Screens專案。

視訊元件具有下列屬性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><em><strong>视频资产</strong></em></td>
   <td>選取視訊的連結。</td>
  </tr>
  <tr>
   <td><em><strong>持续时间</strong></em></td>
   <td>選取視訊的持續時間。 根據預設，持續時間設為–1，這表示元素會永遠執行。 設定持續時間值&gt;0，顯示指定持續時間的元素，然後移至下一個專案。<br /> </td>
  </tr>
  <tr>
   <td><em><strong>呈现</strong></em></td>
   <td><p>如果視訊外觀比例不符合熒幕，您可以將演算調整為 <strong>contain</strong> 或 <strong>封面</strong>.</p> <p><em>包含</em> 表示顯示完整視訊，並以黑色邊框填入遺失區域。</p> <p><em>封面</em> 表示影片涵蓋整個檢視區，但兩側溢位的部分會隱藏。</p> </td>
  </tr>
  <tr>
   <td><em><strong>大小</strong></em></td>
   <td>視訊的大小。</td>
  </tr>
 </tbody>
</table>
