---
title: 在AEM Screens中配置ContextHub
description: 了解定位引擎中的ContextHub，以便您可以定义数据存储来触发内容更改。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 1%

---

# 在AEM Screens中配置ContextHub {#configuring-contexthub-in-aem-screens}

本节重点介绍如何使用数据存储来创建和管理数据驱动的资源更改。

## 关键术语 {#key-terms}

在详细介绍如何在AEM Screens项目中创建和管理库存驱动型渠道之前，请先了解各种方案的一些关键术语。

**品牌** — 您的高级项目说明。

**区域** — 您的AEM Screens项目名称，如数字广告标牌

**活动** — 定义类别规则，如库存驱动、天气驱动或部门可用性驱动。

**受众** — 定义规则。

**区段** — 要为给定规则播放的资源版本。 例如，如果温度低于华氏50度，则屏幕显示热饮的图像，否则显示冷饮。

下图直观地展示了ContextHub配置如何与“活动”、“受众”和“渠道”一致。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 前提条件 {#preconditions}

在开始为AEM Screens项目配置ContextHub配置之前，请设置Google工作表（用于演示目的）。

>[!IMPORTANT]
>
>在以下示例中，Google Sheets用作示例数据库系统，其中值是从中获取的，且仅用于教育目的。 对于将Google Sheets用于生产环境，Adobe不认可。
>
>有关详细信息，请参阅Google文档中的[获取API密钥](https://developers.google.com/maps/documentation/javascript/get-api-key)。

## 步骤1：设置数据存储 {#step-setting-up-a-data-store}

您可以将数据存储设置为本地I/O事件或本地数据库事件。

以下资产级别数据触发器示例展示了本地数据库事件。 事件会设置一个数据存储，例如Excel工作表，该工作表允许您使用ContextHub配置和到AEM Screens渠道的区段路径。

正确设置`google`工作表后，如以下示例所示：

![图像](/help/user-guide/assets/context-hub/context-hub1.png)

以下验证是您在检查连接时查看的内容，方法是以下列格式输入两个值： `*google sheet ID*`和`*API key*`：

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![图像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>以下特定示例将Google工作表显示为数据存储，如果值大于100或小于50，则会触发资产更改。

## 步骤2：设置存储配置 {#step-setting-store-configurations}

1. **导航到ContextHub**

   导航到您的AEM实例，然后单击左侧边栏中的工具图标。 单击&#x200B;**站点** > **ContextHub**，如下图所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **创建ContextHub存储配置**

   1. 导航到标题为&#x200B;**屏幕**&#x200B;的配置容器。

   1. 单击&#x200B;**创建** > **创建配置容器**，然后输入标题&#x200B;**ContextHubDemo**。

      ![图像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **导航**&#x200B;到&#x200B;**ContextHubDemo** > **创建** **ContentHub配置**，然后单击&#x200B;**保存**。

      >[!NOTE]
      > 单击&#x200B;**保存**&#x200B;后，您即进入&#x200B;**ContextHub配置**&#x200B;屏幕。

   1. 在&#x200B;**ContextHub配置**&#x200B;屏幕中，单击&#x200B;**创建** > **ContentHub存储配置**

   ![图像](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >作为AEM 6.5 Feature Pack 4或AEM 6.4 Feature Pack 8的一部分，客户应将`/conf/screens/settings/cloudsettings`更新为`sling:Folder`。
   >
   >应遵循以下步骤：
   >
   >1. 导航到CRXDE Lite，然后导航到`/conf/screens/settings/cloudsettings`。
   >1. 检查`cloudsettings jcr:primaryType`是否在`sling:Folder`中。 如果`jcr:primaryType`不在`sling:folder`中，请继续执行后续步骤。
   >1. 右键单击`/conf/screens/settings`并创建一个&#x200B;*名称*&#x200B;为&#x200B;**`cloudsettings1`**&#x200B;且&#x200B;*类型*&#x200B;为&#x200B;**`sling:Folder`**&#x200B;的节点，然后保存更改。
   >1. 将`/conf/screens/settings/cloudsettings`下的所有节点移动到`cloudsettings1`。
   >1. 删除`cloudsettings`并保存。
   >1. 将`cloudsettings1`重命名为`cloudsettings`并保存。
   >1. 请注意，`/conf/screens/settings/cloudsettings`具有`jcr:primaryType`作为`sling:Folder`。
   >
   >在升级之前或之后，请按照创作和Publish中的以下步骤操作。

   1. 输入&#x200B;**标题**&#x200B;作为&#x200B;**Google工作表**，**存储名称**&#x200B;作为&#x200B;**`googlesheets`**，**存储类型**&#x200B;作为&#x200B;**c`ontexthub.generic-jsonp`**，然后单击&#x200B;**下一步**。

      >[!CAUTION]
      >如果您使用的是Adobe Experience Manager (AEM) 6.4，请输入&#x200B;**配置标题**&#x200B;作为&#x200B;**`googlesheets`**，输入&#x200B;**存储类型**&#x200B;作为&#x200B;**c`ontexthub.generic-jsonp`**。

      ![图像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 输入特定的json配置。 例如，您可以将以下json用于演示目的，然后单击&#x200B;**保存**。 您在ContextHub配置中看到标题为&#x200B;**Google Sheets**&#x200B;的存储区配置。

      >[!IMPORTANT]
      >请确保将您在设置Google工作表时获取的`*<Sheet ID>*`和`*<API Key>*`代码替换为您输入的代码。

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      >
      >在上述示例代码中，**pollInterval**&#x200B;定义值的刷新频率（以毫秒为单位）。
      >
      >将代码替换为您在设置Google工作表时获取的`*<Sheet ID>*`和`*<API Key>*`。

      >[!CAUTION]
      >
      >如果您创建的Google工作表将配置存储在全局文件夹之外（例如，在您自己的项目文件夹中），则定位将无法立即使用。

1. **设置商店分段**

   1. 导航到&#x200B;**ContentHub存储区配置**&#x200B;并在AEM Screens配置容器中创建另一个存储区配置，并将&#x200B;**Title**&#x200B;设置为&#x200B;**segmentation-contexthub**，**存储区名称**&#x200B;设置为&#x200B;**segmentation**，**存储类型**&#x200B;设置为&#x200B;**aem.segmentation**。

      ![图像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 单击&#x200B;**下一步**，然后单击&#x200B;**保存**。

      >[!NOTE]
      >跳过定义json的过程，并将其留空。


## 步骤3：在Audience中设置区段 {#setting-up-audience}

1. **在受众中创建区段**

   1. 从您的AEM实例导航到&#x200B;**Personalization** > **受众** > **屏幕**。

   1. 单击&#x200B;**创建** > **创建ContextHub区段。**&#x200B;将打开&#x200B;**新ContextHub区段**&#x200B;对话框。

   1. 输入&#x200B;**标题**&#x200B;作为`**Higherthan50**`，然后单击&#x200B;**创建**。 同样，创建另一个标题为`**Lowerthan50**`的区段。

      ![图像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 单击区段`**Higherthan50**`，然后单击操作栏中的&#x200B;**属性**。

      ![图像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 从&#x200B;**区段属性**&#x200B;中单击&#x200B;**Personalization**&#x200B;选项卡。 将&#x200B;**ContextHub路径**&#x200B;设置为`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`，将&#x200B;**区段路径**&#x200B;设置为`/conf/screens/settings/wcm/segments`，然后单击&#x200B;**保存**，如下图所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同样，也为`**Lowerthan50**`区段设置&#x200B;**ContextHub路径**&#x200B;和&#x200B;**区段路径**。

## 步骤4：设置品牌和区域 {#setting-brand-area}

请按照以下步骤在品牌下的活动和区域中创建品牌：

1. **在活动中创建品牌**

   1. 从您的AEM实例导航到&#x200B;**Personalization** > **活动**。

   1. 单击&#x200B;**创建** > **创建品牌**。

   1. 从&#x200B;**创建页面**&#x200B;向导中单击&#x200B;**品牌**，然后单击&#x200B;**下一步**。

   1. 输入&#x200B;**标题**&#x200B;作为&#x200B;**ScreensBrand**，然后单击&#x200B;**创建**。 您的品牌现已创建，如下所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >已知问题：
      >要添加区域，请从URL中删除主区域，例如
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在您的品牌中创建区域**

   请按照以下步骤在品牌中创建区域：

   1. 单击&#x200B;**创建**，然后单击&#x200B;**创建区域**。

      ![图像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 从&#x200B;**创建页面**&#x200B;向导中单击&#x200B;**区域**，然后单击&#x200B;**下一步**。

   1. 输入&#x200B;**标题**&#x200B;作为&#x200B;**ScreensValue**，然后单击&#x200B;**创建**。
即会在您的品牌中创建区域。

## 步骤5：在活动中创建区段 {#step-setting-up-audience-segmentation}

在设置数据存储并定义活动（品牌和区域）后，请按照以下步骤在活动中创建区段。

1. **在活动中创建区段**

   1. 从您的AEM实例导航到&#x200B;**Personalization** > **活动** > **ScreensBrand** >**ScreensValue**。

   1. 单击&#x200B;**创建** > **创建活动。** **配置活动向导**&#x200B;打开。

   1. 输入&#x200B;**Title**&#x200B;作为&#x200B;**ValueCheck50**，输入&#x200B;**Name**&#x200B;作为&#x200B;**valuecheck50**。 从下拉列表中单击&#x200B;**定位引擎**&#x200B;作为&#x200B;**ContextHub (AEM)**，然后单击&#x200B;**下一步**。

      ![图像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 从`**Configure Activity**`向导中单击&#x200B;**添加体验**。

   1. 在&#x200B;**受众**&#x200B;中，单击`**Higherthan50**`并单击&#x200B;**添加体验**&#x200B;并输入&#x200B;**标题**&#x200B;作为`**higherthan50**` **名称**&#x200B;作为`**higherthan50**`。 单击&#x200B;**确定**。

   1. 在&#x200B;**受众**&#x200B;中，单击`**Lowerthan50**`并单击&#x200B;**添加体验**&#x200B;并输入&#x200B;**标题**&#x200B;作为`**lowerthan50**` **名称**&#x200B;作为`**lowerthan50**`。 单击&#x200B;**确定**。

   ![图像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 单击&#x200B;**下一步**，然后单击&#x200B;**保存**。 `**ValueCheck50**`活动现已创建并配置。

      ![图像](/help/user-guide/assets/context-hub/context-hub16.png)

## 步骤5：编辑受众中的区段{#editing-audience-segmentation}

1. **编辑区段**

   1. 从您的AEM实例导航到&#x200B;**Personalization** > **受众** > **屏幕**。

   1. 单击区段`**Higherthan50**`，然后单击操作栏中的&#x200B;**编辑**。

   1. 将&#x200B;**比较：属性 — 值**&#x200B;组件拖放到编辑器中。

   1. 单击扳手图标，以便打开&#x200B;**比较属性与值**&#x200B;对话框。

   1. 从&#x200B;**属性名称**&#x200B;中的下拉列表中单击&#x200B;**Googlesheets/value/1/0**。

      >[!NOTE]
      > **googlesheets/value/1/0**&#x200B;引用了下图中填充在`google`工作表中的行2和列：

      ![图像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 从下拉菜单中单击&#x200B;**运算符**&#x200B;作为&#x200B;**大于**。

   1. 输入&#x200B;**值**&#x200B;作为&#x200B;**70**。

      >[!NOTE]
      >
      >AEM会将您的区段显示为绿色，以验证Google工作表中的数据。

      ![图像](/help/user-guide/assets/context-hub/context-hub18.png)

   同样，将属性值编辑为`**Lowerthan50**`。

   1. 将&#x200B;**比较：属性 — 值**&#x200B;组件拖放到编辑器中。

   1. 单击扳手图标。

   1. 在&#x200B;**比较属性与值**&#x200B;对话框中，从&#x200B;**属性名称**&#x200B;中的下拉菜单中单击&#x200B;**googleHeets/value/1/0**。

   1. 从下拉菜单中单击&#x200B;**运算符**&#x200B;作为&#x200B;**小于**。

   1. 输入&#x200B;**值**&#x200B;作为&#x200B;**50**。


## 在渠道中启用定位 {#step-enabling-targeting-in-channels}

执行以下步骤以在渠道中启用定位。

1. 导航到某个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens渠道中创建的&#x200B;**DataDrivenChannel**&#x200B;启用定位。

1. 单击频道&#x200B;**TargetChannel**，然后单击操作栏中的&#x200B;**属性**。

   ![图像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 单击&#x200B;**Personalization**&#x200B;选项卡，以便设置ContextHub配置。

   1. 将&#x200B;**ContextHub路径**&#x200B;设置为`/conf/screens/settings/wcm/segments`，将&#x200B;**区段路径**&#x200B;设置为`/conf/screens/settings/wcm/segments`。
   1. 从下拉列表中将Brand设置为&#x200B;**ScreensBrand**&#x200B;并将Area Reference **设置为** ScreensValue **。**

   1. 单击“**保存并关闭**”。

      >[!NOTE]
      >
      >使用ContextHub和区段路径，您最初保存了ContextHub配置和区段。

      ![图像](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. 导航并单击&#x200B;**TargetChannel**&#x200B;频道，然后单击操作栏中的&#x200B;**编辑**。

      >[!NOTE]
      >
      >如果一切设置正确，您会在编辑器的下拉列表中看到&#x200B;**定位**&#x200B;选项，如下图所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub21.png)

## 了解详情：示例用例 {#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的用例来了解数据触发的资源如何在不同的行业中发挥重要作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**
