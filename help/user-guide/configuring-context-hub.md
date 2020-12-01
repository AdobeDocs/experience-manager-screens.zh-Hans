---
title: 在AEM Screens配置ContextHub
seo-title: 在AEM Screens配置ContextHub
description: 可查看本页以了解定位引擎中的ContextHub，以定义数据存储，以便数据触发内容发生更改。
seo-description: 可查看本页以了解定位引擎中的ContextHub，以定义数据存储，以便数据触发内容发生更改。
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 1%

---


# 在AEM Screens配置ContextHub {#configuring-contexthub-in-aem-screens}

本节重点介绍如何使用数据存储创建和管理数据驱动的资产更改。

## 关键术语{#key-terms}

在我们了解有关在您的AEM Screens项目中创建和管理库存驱动型渠道的详细信息之前，您必须了解一些重要且与不同方案相关的关键术语。

**品** 牌是指您的高级项目描述。

**区** 域指您的AEM Screens项目名称，如数字广告标牌

**活** 动定义规则类别，如库存驱动、天气驱动、部门可用性驱动等。

**受** 众定义规则。

**区** 段指根据给定规则播放的资产版本，例如，如果温度低于50华氏度，则屏幕将显示热咖啡的图像，否则显示冷饮。

下图直观地显示了ContextHub配置如何与活动、受众和渠道保持一致。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先决条件{#preconditions}

在开始为AEM Screens项目配置Context Hub配置之前，必须设置Google工作表（用于演示目的）。

>[!IMPORTANT]
>
>在以下示例中，Google Sheets用作获取值并仅用于教育目的的示例数据库系统。 Adobe不认可将Google Sheets用于生产环境。
>
>有关详细信息，请参阅Google文档中的[获取API密钥](https://developers.google.com/maps/documentation/javascript/get-api-key)。

## 第1步：设置数据存储{#step-setting-up-a-data-store}

可以将数据存储设置为本地I/O事件或本地数据库事件。

以下资产级事件触发器示例展示一个本地数据库，该数据库设置一个数据存储，如一个excel表，它允许您使用ContextHub配置和段路径到AEM Screens渠道。

在正确设置google工作表后，例如，如下所示：

![图像](/help/user-guide/assets/context-hub/context-hub1.png)

以下验证是检查连接时要视图的，输入以下格式的两个值&#x200B;*google表ID*&#x200B;和&#x200B;*API密钥*:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![图像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>以下特定示例将google工作表显示为一个数据存储，如果该值高于100或小于50，则该数据存储将触发资产更改。

## 第2步：设置存储配置{#step-setting-store-configurations}

1. **导航到ContextHub**

   导航到AEM实例，然后单击左侧提要栏中的工具图标。 单击&#x200B;**站点** —> **ContextHub**，如下图所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **创建新的ContextHub存储配置**

   1. 导航到标题为&#x200B;**screens**&#x200B;的配置容器。

   1. 单击&#x200B;**创建** > **创建配置容器**&#x200B;并输入&#x200B;**ContextHubDemo**&#x200B;的标题。

      ![图像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **导** 航到 **ContextHubDemo** > CreateContentHub  **** **Configuration,** 然后单击“ **保存**”。

      >[!NOTE]
      > 单击&#x200B;**Save**&#x200B;后，您将出现在&#x200B;**ContextHub Configuration**&#x200B;屏幕中。

   1. 在&#x200B;**ContextHub配置**&#x200B;屏幕中，单击&#x200B;**创建** > **ContentHub存储配置……**

      ![图像](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >作为AEM 6.5 Feature Pack 4或AEM 6.4 Feature Pack 8的一部分，客户应将`/conf/screens/settings/cloudsettings`更新为`sling:Folder`。
      >
      >应遵循以下步骤：
      >
      >1. 导航到CRXDE Lite，然后导航到`/conf/screens/settings/cloudsettings`。
      >1. 检查`cloudsettings jcr:primaryType`是否在`sling:Folder`中。 如果`jcr:primaryType`不在`sling:folder`中，请继续执行后续步骤。
      >1. 右键单击`/conf/screens/settings`并创建一个新节点，其名称&#x200B;**&#x200B;为&#x200B;**cloudsettings1**，类型&#x200B;*为&#x200B;**sling:Folder**并保存更改。*
      >1. 将`/conf/screens/settings/cloudsettings`下的所有节点移动到`cloudsettings1`。
      >1. 删除`cloudsettings`并保存。
      >1. 将`cloudsettings1`重命名为`cloudsettings`并保存。
      >1. 您现在应该观察到/conf/screens/settings/cloudsettings的`jcr:primaryType`为`sling:Folder`。

      >
      >您应按照创作步骤操作，并在升级前后发布。

   1. 将&#x200B;**标题**&#x200B;输入为&#x200B;**Google工作表**、**商店名称**&#x200B;输入为&#x200B;**谷物表**，将&#x200B;**商店类型**&#x200B;输入为&#x200B;**contexthub.generic-jsonp**&#x200B;并单击&#x200B;**Next**。

      >[!CAUTION]
      >如果您使用Adobe Experience Manager(AEM)6.4，请将&#x200B;**配置标题**&#x200B;输入为&#x200B;**googlesheets**，将&#x200B;**存储类型**&#x200B;输入为&#x200B;**contexthub.generic-jsonp**。

      ![图像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 输入您的特定json配置。 例如，您可以将以下json用于演示目的，然后单击&#x200B;**保存**，您将在ContextHub配置中看到标题为&#x200B;**Google Sheets**&#x200B;的存储配置。

      >[!IMPORTANT]
      >确保在设置Google工作表时将代码替换为您的&#x200B;*&lt;工作表ID>*&#x200B;和&#x200B;*&lt;API密钥>*。

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
      在上述示例代码中，**pollInterval**&#x200B;定义刷新值的频率（以毫秒为单位）。
      将代码替换为您在设置Google工作表时读取的&#x200B;*&lt;工作表ID>*&#x200B;和&#x200B;*&lt;API密钥>*。

      >[!CAUTION]
      如果您在全局文件夹（例如您自己的项目文件夹中）之外创建Google工作表存储配置，则定位将不会立即生效。


1. **设置商店分段**

   1. 导航到&#x200B;**ContentHub存储配置。** 并在屏幕配置容器中创建另一个存储配 **** 置，将 **Leleas segmentation-contexthub、** Store  **Store设置为** segmanta **** 和Store  ****  **** Typeas.asegmation的。

      ![图像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 单击&#x200B;**下一步**，然后单击&#x200B;**保存**。

      >[!NOTE]
您必须跳过定义json的过程并将其留空。


## 第3步：在受众{#setting-up-audience}中设置区段

1. **在受众中创建区段**

   1. 从AEM实例导航到&#x200B;**个性化** > **受众** > **屏幕**。

   1. 单击&#x200B;**创建** > **创建Context Hub区段。** 将打 **开“新建** ContextHub区段”对话框。

   1. 输入&#x200B;**标题**&#x200B;作为&#x200B;**高于50**，然后单击&#x200B;**创建**。 同样，创建标题为&#x200B;**Lowerthan50**&#x200B;的另一个段。

      ![图像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 选择段&#x200B;**高于50**，然后单击操作栏中的&#x200B;**属性**。
      ![图像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 从&#x200B;**区段属性**&#x200B;中选择&#x200B;**个性化**&#x200B;选项卡。 将&#x200B;**ContextHub路径**&#x200B;设置为`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`，将&#x200B;**区段路径**&#x200B;设置为`/conf/screens/settings/wcm/segments`，然后单击&#x200B;**保存**，如下图所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同样，也可以设置&#x200B;**Lowerthan 50**&#x200B;段的&#x200B;**ContextHub路径**&#x200B;和&#x200B;**段路径**。

## 第4步：设置品牌和区域{#setting-brand-area}

请按照以下步骤在您的活动和品牌下的区域创建品牌：

1. **在活动中创建品牌**

   1. 从AEM实例导航到&#x200B;**个性化** > **活动**。

   1. 单击&#x200B;**创建** > **创建品牌**。

   1. 从&#x200B;**创建页面**&#x200B;向导中选择&#x200B;**品牌**，然后单击&#x200B;**下一步**。

   1. 输入&#x200B;**Title**&#x200B;作为&#x200B;**ScreensBrand**，然后单击&#x200B;**创建**。 您的品牌现在创建如下。

      ![图像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      已知问题：
要添加区域，请从URL中删除主控，如
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在品牌中创建区域**

   按照以下步骤在品牌中创建区域：

   1. 单击&#x200B;**创建**，然后单击&#x200B;**创建区域**。

      ![图像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 从&#x200B;**创建页面**&#x200B;向导中选择&#x200B;**区域**，然后单击&#x200B;**下一步**。

   1. 输入&#x200B;**Title**&#x200B;作为&#x200B;**ScreensValue**，然后单击&#x200B;**创建**。
将在您的品牌中创建区域。

## 第5步：在活动{#step-setting-up-audience-segmentation}中创建区段

设置活动存储并定义活动（品牌和区域）后，请按照以下步骤在中创建区段。

1. **在活动中创建区段**

   1. 从AEM实例导航到&#x200B;**个性化** > **活动** > **ScreensBrand** >**ScreensValue**。

   1. 单击&#x200B;**创建** > **创建活动。** 配置 **活动** 向导。

   1. 将&#x200B;**标题**&#x200B;输入为&#x200B;**ValueCheck50**，将&#x200B;**名称**&#x200B;输入为&#x200B;**值heck50**。 从下拉菜单中选择&#x200B;**定位引擎**&#x200B;作为&#x200B;**ContextHub(AEM)**&#x200B;并单击&#x200B;**下一步**。

      ![图像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 单击&#x200B;**配置活动向导**&#x200B;中的&#x200B;**添加体验**。

   1. 在&#x200B;**受众**&#x200B;中，选择&#x200B;**高于50**&#x200B;并单击&#x200B;**添加体验**，然后输入&#x200B;**标题**&#x200B;高于50 ****&#x200B;名称&lt;a10/>1/>为&#x200B;**高于50**。 ****&#x200B;单击&#x200B;**确定**。

   1. 在&#x200B;**受众**&#x200B;中，选择&#x200B;**低于50**&#x200B;并单击&#x200B;**添加体验**，将&#x200B;**标题**&#x200B;输入为低于50 ****&#x200B;名称&#x200B;**作为** lower than50 **。**&#x200B;单击&#x200B;**确定**。

      ![图像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 单击&#x200B;**下一步**，然后单击&#x200B;**保存**。 **ValueCheck50** 活动现已创建和配置。

      ![图像](/help/user-guide/assets/context-hub/context-hub16.png)

## 第5步：编辑受众{#editing-audience-segmentation}中的区段

1. **编辑区段**

   1. 从AEM实例导航到&#x200B;**个性化** > **受众** > **屏幕**。

   1. 选择段&#x200B;**高于50**，然后单击操作栏中的&#x200B;**编辑**。

   1. 拖放&#x200B;**比较：属性——编辑器的值**&#x200B;组件。

   1. 单击扳手图标以打开&#x200B;**将属性与值**&#x200B;比较对话框。

   1. 从&#x200B;**属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/0**。

      >[!NOTE]
Google **Sheets/value/1/** 0引用如下图中Google Sheets中填入的行2和列：

      ![图像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 从下拉菜单中选择&#x200B;**运算符**&#x200B;作为&#x200B;**greater-than**。

   1. 输入&#x200B;**值**&#x200B;作为&#x200B;**70**。

      >[!NOTE]
      AEM通过将您的区段显示为绿色来验证来自Google工作表的数据。

      ![图像](/help/user-guide/assets/context-hub/context-hub18.png)
   同样，编辑属性值至&#x200B;**Lowerthan50**。

   1. 拖放&#x200B;**比较：属性——编辑器的值**&#x200B;组件。

   1. 单击扳手图标以打开&#x200B;**将属性与值**&#x200B;比较对话框。

   1. 从&#x200B;**属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/0**。

   1. 从下拉菜单中选择&#x200B;**运算符**&#x200B;作为&#x200B;**less-than**。

   1. 输入&#x200B;**值**&#x200B;作为&#x200B;**50**。



## 在渠道{#step-enabling-targeting-in-channels}中启用定位

按照以下步骤在您的渠道中启用定位。

1. 导航到某个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens渠道中创建的&#x200B;**DataDrivenChannel**&#x200B;启用定位。

1. 选择渠道&#x200B;**TargetChannel**，然后单击操作栏中的&#x200B;**属性**。

   ![图像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 选择&#x200B;**个性化**&#x200B;选项卡以设置ContextHub配置。

   1. 将&#x200B;**ContextHub路径**&#x200B;设置为`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`，将&#x200B;**区段路径**&#x200B;设置为`/conf/screens/settings/wcm/segments`，然后单击&#x200B;**保存**。

   1. 单击&#x200B;**保存并关闭**。

      >[!NOTE]
      使用ContextHub和“区段”路径，您最初在其中保存了Context Hub配置和区段。

      ![图像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. 导航并选择&#x200B;**TargetChannel**&#x200B;渠道，然后单击操作栏中的&#x200B;**编辑**。

      >[!NOTE]
      如果您正确设置了所有内容，您将在编辑器的下拉框中看到&#x200B;**定位**&#x200B;选项，如下图所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub21.png)

## 了解更多：示例用例{#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的使用案例了解数据触发资产如何在不同行业中发挥关键作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**
