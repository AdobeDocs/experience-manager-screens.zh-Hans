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
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 1%

---


# 在AEM Screens配置ContextHub {#configuring-contexthub-in-aem-screens}

本节重点介绍如何使用数据存储创建和管理数据驱动的资产更改。

## 主要条款 {#key-terms}

在我们了解有关在您的AEM Screens项目中创建和管理库存驱动型渠道的详细信息之前，您必须了解一些重要且与不同方案相关的关键术语。

**品牌** -指您的高级项目描述。

**区域** ：指您的AEM Screens项目名称，如数字广告标牌

**活动** 定义规则类别，如库存驱动、天气驱动、部门可用性驱动等。

**受众** 定义规则。

**区段** ：指要根据给定规则播放的资产版本，例如，如果温度低于50华氏度，则屏幕将显示热咖啡的图像，否则显示冷饮。

下图直观地显示了ContextHub配置如何与活动、受众和渠道保持一致。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先决条件 {#preconditions}

在开始为AEM Screens项目配置Context Hub配置之前，必须设置Google工作表（用于演示目的）。

>[!IMPORTANT]
>
>在以下示例中，Google Sheets用作获取值并仅用于教育目的的示例数据库系统。 Adobe不认可将Google Sheets用于生产环境。
>
>有关详细信息，请参 [阅Google文档中的](https://developers.google.com/maps/documentation/javascript/get-api-key) “获取API密钥”。

## 第1步：设置数据存储 {#step-setting-up-a-data-store}

可以将数据存储设置为本地I/O事件或本地数据库事件。

以下资产级事件触发器示例展示一个本地数据库，该数据库设置一个数据存储，如一个excel表，它允许您使用ContextHub配置和段路径到AEM Screens渠道。

在正确设置google工作表后，例如，如下所示：

![图像](/help/user-guide/assets/context-hub/context-hub1.png)

以下验证是检查连接时要视图的内容，输入以下格 *式的google表ID**和API密钥* :

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![图像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>以下特定示例将google工作表显示为一个数据存储，如果该值高于100或小于50，则该数据存储将触发资产更改。

## 第2步：设置存储配置 {#step-setting-store-configurations}

1. **导航到ContextHub**

   导航到AEM实例，然后单击左侧提要栏中的工具图标。 单 **击** Sites — **> ContextHub**，如下图所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **创建新的ContextHub存储配置**

   1. 导航到标题为“屏幕”的配 **置容器**。

   1. 单击 **“创建** ” > **“创建配置容器** ”，然后输入 **ContextHubDemo作为标题**。

      ![图像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **导航到** ContextHubDemo **>** 创建 **ContentHub ConfigurationHub** Save **(保存******)。

      >[!NOTE]
      > 单击“保 **存** ”后，将显示 **在ContextHub Configuration屏幕** 。

   1. 从ContextHub **配置屏幕** ，单击 **创建** > **ContentHub存储配置。**

      ![图像](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >作为AEM 6.5 Feature Pack 4或AEM 6.4 Feature Pack 8的一部分，客户应更新 `/conf/screens/settings/cloudsettings` 至 `sling:Folder`。
      > 
      >应遵循以下步骤：
      >
      >1. 导航到CRXDE Lite，然后导航到 `/conf/screens/settings/cloudsettings`。
      >1. 检查是 `cloudsettings jcr:primaryType` 否在 `sling:Folder`中。 如果未 `jcr:primaryType` 在，请 `sling:folder`继续执行后续步骤。
      > 1. 右键单 `/conf/screens/settings` 击并创建一个名 *称为* cloudsettings1的新节点 **,** 类型为 *sling* :Folder **** ，并保存更改。
      >1. 将下面的所有节点移 `/conf/screens/settings/cloudsettings` 动到 `cloudsettings1`。
      >1. 删除 `cloudsettings` 并保存。
      >1. 重命名 `cloudsettings1` 为 `cloudsettings` 并保存。
      >1. 您现在应观察/conf/screens/settings/cloudsettings的 `jcr:primaryType` 身份 `sling:Folder`。
您应按照创作步骤操作，并在升级前后发布。


   1. 在标题中 **输入** Google Sheets、Store Store Name **(** Google Sheets、 **Google Sheets、Type StoreAs****************** Conthub.Jsonp类和单击Nexit GoogleSheets Sheets、Google Store Store名称)。

      >[!CAUTION]
      >如果您使用Adobe Experience Manager(AEM)6.4，请将“配 **置标题** ”输 **入为****googlesheets** ，将“类型 **”输入**&#x200B;为contexthub.generic-jsonp存储。

      ![图像](/help/user-guide/assets/context-hub/context-hub6.png)



   1. 输入您的特定json配置。 例如，您可以将以下json用于演示目的并单击“保 **存** ”，您将在ContextHub配置中看到标题 **为Google Sheets** 的存储配置。

      >[!IMPORTANT]
      >确保将代码替换为您在设 *置Google工作表**时获取的&lt;Sheet ID>和*&lt;API Key>。

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
      在上述示例代码 **中** ,pollInterval定义刷新值的频率（毫秒）。
将代码替换 *为您在设置Google* Sheets *时获取的&lt;Sheet ID>和*&lt;API Key>。

      >[!CAUTION]
      如果您在全局文件夹（例如您自己的项目文件夹中）之外创建Google工作表存储配置，则定位将不会立即生效。

1. **设置商店分段**

   1. 导航到 **ContentHub存储配置。** 并在屏幕配置容器中创建另一个存储配置， **将** Title设置为 **-contexthub**, **将存储名称** 设置为和分 ************&#x200B;分区商店类型TypeAem.segmentation。

      ![图像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
您必须跳过定义json的过程并将其留空。


## 第3步：在受众中设置区段 {#setting-up-audience}

1. **在受众中创建区段**

   1. 从AEM实例导航到“个 **性化** ”> **受众** > **屏幕**。

   1. 单击 **创建** > **创建Context Hub区段。** 将打 **开“新建ContextHub区段** ”对话框。

   1. Enter the **Title** as **Higherthan50** and click **Create**. 同样，创建标题为Lowerthan50的 **另一个区段**。

      ![图像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 选择区段 **高于** 50，然 **后单击操** 作栏中的“属性”。
      ![图像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 从区段 **属性** 中选择个 **性化选项卡**。 将ContextHub路 **径设置为** ，将 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` ContextHub路径 **设置为** ，并单击“保 `/conf/screens/settings/wcm/segments` 存”, ****&#x200B;如下图所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同样，为Lowerthan **50段** 设置 **ContextHub** Path和 **Segments Path** （Lowerthan50段的ContextHub路径）。

## 第4步：设置品牌和区域 {#setting-brand-area}

请按照以下步骤在您的活动和品牌下的区域创建品牌：

1. **在活动中创建品牌**

   1. 从AEM实例导航到“个 **性化** ”> **活动**。

   1. 单击 **创建** > **创建品牌**。

   1. Select **Brand** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. 您的品牌现在创建如下。

      ![图像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      已知问题：要添加区域，请从URL中删除主控，如
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在品牌中创建区域**

   按照以下步骤在品牌中创建区域：

   1. 单击 **创建** ，然后 **单击创建区域**。

      ![图像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Select **Area** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
将在您的品牌中创建区域。

## 第5步：在活动中创建区段 {#step-setting-up-audience-segmentation}

设置活动存储并定义活动（品牌和区域）后，请按照以下步骤在中创建区段。

1. **在活动中创建区段**

   1. 从AEM实例导航到个 **性化** > **活动** > Screens **品牌** >**Screens**&#x200B;价值。

   1. 单击 **创建** >创 **建活动。** 将打 **开配置活动** 向导。

   1. 将标题 **输入****ValueCheck50** ，将名 **称输** 入 **valuecheck50**。 从下拉 **菜单中选择****ContextHub(AEM** )作为定位引擎，然后单击 **下一步**。

      ![图像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 单击 **配置活动** 向导中 **的添加体验**。

   1. 从受众 **中**，选择Higherthan 50 **** ，然 **后单击Higheradd Experience(Higherthon50),** 并输入Higheradd 50higherName(Highererthan **************** 5050。 Click **Ok**.

   1. 从受众 **中**，选择 **Lowerthan50** 并单击Add Experience, **将Lowerthan Add体验** 输入Lowerthan550, ****************&#x200B;将LowerthanLowerName作为名称小于50。 Click **Ok**.

      ![图像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Click **Next** and then **Save**. **ValueCheck** 50活动现已创建和配置。

      ![图像](/help/user-guide/assets/context-hub/context-hub16.png)

## 第5步：在受众中编辑区段{#editing-audience-segmentation}

1. **编辑区段**

   1. 从AEM实例导航到“个 **性化** ”> **受众** > **屏幕**。

   1. 选择区段 **高于** 50，然后 **单击操** 作栏中的“编辑”。

   1. 拖放比 **较：属性** -编辑器的值组件。

   1. 单击扳手图标以打开“ **比较属性与值** ”对话框。

   1. 从 **属性名称的下拉菜单中选择** “googlesheets/value/1/ **0”**。

      >[!NOTE]
Google **Sheets/value/1/0** ，是指在下图的google Sheet中填充的行2和列：

      ![图像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 从下 **拉菜** 单中选 **择“Operator** as greater-than”。

   1. 输入 **值****70**。

      >[!NOTE]
      AEM通过将您的区段显示为绿色来验证来自Google工作表的数据。

      ![图像](/help/user-guide/assets/context-hub/context-hub18.png)
   同样，编辑属性值 **为Lowerthan50**。

   1. 拖放比 **较：属性** -编辑器的值组件。

   1. 单击扳手图标以打开“ **比较属性与值** ”对话框。

   1. 从 **属性名称的下拉菜单中选择** “googlesheets/value/1/ **0”**。

   1. 从下 **拉菜** 单中选 **择运算符** “小于”。

   1. 输入 **值** 50 ****。



## 在渠道中启用定位 {#step-enabling-targeting-in-channels}

按照以下步骤在您的渠道中启用定位。

1. 导航到某个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens **渠道中创建** 的DataDrivenChannel启用定位。

1. 选择渠道 **TargetChannel** ，然后 **单击操** 作栏中的“属性”。

   ![图像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 选择“个 **性化** ”选项卡以设置ContextHub配置。

   1. 将ContextHub路 **径设置为** ，将 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` ContextHub路径 **设置为** ，并单 `/conf/screens/settings/wcm/segments` 击“保 ****&#x200B;存”。

   1. 单击&#x200B;**保存并关闭**。

      >[!NOTE]
      使用ContextHub和“区段”路径，您最初在其中保存了Context Hub配置和区段。

      ![图像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. 导航并选择 **TargetChannel** 渠道，然 **后单** 击操作栏中的“编辑”。

      >[!NOTE]
      如果您正确设置了所有内容，您将在 **编辑器** 的下拉框中看到“定位”选项，如下图所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub21.png)

## 了解更多：示例使用案例 {#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的使用案例了解数据触发资产如何在不同行业中发挥关键作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**
