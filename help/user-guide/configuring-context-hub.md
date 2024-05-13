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

**品牌**  — 您的高级项目说明。

**面积图**  — 您的AEM Screens项目名称，如数字广告标牌

**活动**  — 定义类别规则，如库存驱动、天气驱动或部门可用性驱动。

**受众**  — 定义规则。

**区段**  — 要为给定规则播放的资产版本。 例如，如果温度低于华氏50度，则屏幕显示热饮的图像，否则显示冷饮。

下图直观地展示了ContextHub配置如何与“活动”、“受众”和“渠道”一致。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 前提条件 {#preconditions}

在开始为AEM Screens项目配置ContextHub配置之前，请设置Google工作表（用于演示目的）。

>[!IMPORTANT]
>
>在以下示例中，Google Sheets用作示例数据库系统，其中值是从中获取的，且仅用于教育目的。 对于将Google Sheets用于生产环境，Adobe不认可。
>
>有关更多信息，请参阅 [获取API密钥](https://developers.google.com/maps/documentation/javascript/get-api-key) 在Google文档中。

## 步骤1：设置数据存储 {#step-setting-up-a-data-store}

您可以将数据存储设置为本地I/O事件或本地数据库事件。

以下资产级别数据触发器示例展示了本地数据库事件。 事件会设置一个数据存储，例如Excel工作表，该工作表允许您使用ContextHub配置和到AEM Screens渠道的区段路径。

在您设置 `google` 正确填写工作表，如下面的示例所示：

![图像](/help/user-guide/assets/context-hub/context-hub1.png)

以下验证是您在通过输入这两个值检查连接时所查看的内容， `*google sheet ID*` 和 `*API key*` 的格式：

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![图像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>以下特定示例将Google工作表显示为数据存储，如果值大于100或小于50，则会触发资产更改。

## 步骤2：设置存储配置 {#step-setting-store-configurations}

1. **导航到ContextHub**

   导航到您的AEM实例，然后单击左侧边栏中的工具图标。 单击 **站点** > **ContextHub**，如下图所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **创建ContextHub存储配置**

   1. 导航到标题为的配置容器 **屏幕**.

   1. 单击 **创建** > **创建配置容器** 并输入标题为 **ContextHubDemo**.

      ![图像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **导航** 到 **ContextHubDemo** > **创建** **ContentHub配置** 并单击 **保存**.

      >[!NOTE]
      > 单击之后 **保存**，您处于 **ContextHub配置** 屏幕。

   1. 从 **ContextHub配置** 屏幕，单击 **创建** > **ContentHub存储配置**

   ![图像](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >作为AEM 6.5功能包4或AEM 6.4功能包8的一部分，客户应更新 `/conf/screens/settings/cloudsettings` 到 `sling:Folder`.
   >
   >应遵循以下步骤：
   >
   >1. 导航到CRXDE Lite，然后导航到 `/conf/screens/settings/cloudsettings`.
   >1. 检查 `cloudsettings jcr:primaryType` 位于 `sling:Folder`. 如果 `jcr:primaryType` 不在 `sling:folder`，继续后续步骤。
   >1. 右键单击 `/conf/screens/settings` 并创建节点，使用 *name* 作为 **`cloudsettings1`** 和 *类型* 作为 **`sling:Folder`** 并保存更改。
   >1. 将所有节点移动到 `/conf/screens/settings/cloudsettings` 到 `cloudsettings1`.
   >1. 删除 `cloudsettings` 并保存。
   >1. 重命名 `cloudsettings1` 到 `cloudsettings` 并保存。
   >1. 请观察 `/conf/screens/settings/cloudsettings` 具有 `jcr:primaryType` 作为 `sling:Folder`.
   >
   >在升级之前或之后，请按照创作和发布中的以下步骤操作。

   1. 输入 **标题** 作为 **Google工作表**， **存储名称** 作为 **`googlesheets`**、和 **存储类型** 作为 **c`ontexthub.generic-jsonp`** 并单击 **下一个**.

      >[!CAUTION]
      >如果您使用的是Adobe Experience Manager (AEM) 6.4，请输入 **配置标题** 作为 **`googlesheets`** 和 **存储类型** 作为 **c`ontexthub.generic-jsonp`**.

      ![图像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 输入特定的json配置。 例如，您可以将以下json用于演示目的，然后单击 **保存**. 您会看到标题为 **Google工作表** 在ContextHub配置中。

      >[!IMPORTANT]
      >确保将代码替换为 `*<Sheet ID>*` 和 `*<API Key>*`，在设置Google工作表时获取的数据。

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
      >在上述示例代码中， **pollInterval** 定义值的刷新频率（毫秒）。
      >
      >将代码替换为 `*<Sheet ID>*` 和 `*<API Key>*`，在设置Google工作表时获取的数据。

      >[!CAUTION]
      >
      >如果您创建的Google工作表将配置存储在全局文件夹之外（例如，在您自己的项目文件夹中），则定位将无法立即使用。

1. **设置商店分段**

   1. 导航到 **ContentHub存储配置** 并在AEM Screens配置容器中创建另一个商店配置，并设置 **标题** 作为 **segmentation-contexthub**， **存储名称** 作为 **分段** 和 **存储类型** 作为 **aem.segmentation**.

      ![图像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 单击 **下一个** 然后 **保存**.

      >[!NOTE]
      >跳过定义json的过程，并将其留空。


## 步骤3：在Audience中设置区段 {#setting-up-audience}

1. **在受众中创建区段**

   1. 从您的AEM实例导航到 **个性化** > **受众** > **屏幕**.

   1. 单击 **创建** > **创建ContextHub区段。** 此 **新ContextHub区段** 对话框打开。

   1. 输入 **标题** 作为 `**Higherthan50**` 并单击 **创建**. 同样，创建另一个标题为 `**Lowerthan50**`.

      ![图像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 单击区段 `**Higherthan50**` 并单击 **属性** 从操作栏中。
      ![图像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 单击 **个性化** 选项卡 **区段属性**. 设置 **ContextHub路径** 到 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 和 **区段路径** 到 `/conf/screens/settings/wcm/segments` 并单击 **保存**，如下图所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同样，设置 **ContextHub路径** 和 **区段路径** 对象 `**Lowerthan50**` 区段也是。

## 步骤4：设置品牌和区域 {#setting-brand-area}

请按照以下步骤在品牌下的活动和区域中创建品牌：

1. **在活动中创建品牌**

   1. 从您的AEM实例导航到 **个性化** > **活动**.

   1. 单击 **创建** > **创建品牌**.

   1. 单击 **品牌** 从 **创建页面** 向导并单击 **下一个**.

   1. 输入 **标题** 作为 **ScreensBrand** 并单击 **创建**. 您的品牌现已创建，如下所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >已知问题：
      >要添加区域，请从URL中删除主区域，例如
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在品牌中创建区域**

   请按照以下步骤在品牌中创建区域：

   1. 单击 **创建** 然后 **创建区域**.

      ![图像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 单击 **面积图** 从 **创建页面** 向导并单击 **下一个**.

   1. 输入 **标题** 作为 **Screens值** 并单击 **创建**.
即会在您的品牌中创建区域。

## 步骤5：在活动中创建区段 {#step-setting-up-audience-segmentation}

在设置数据存储并定义活动（品牌和区域）后，请按照以下步骤在活动中创建区段。

1. **在活动中创建区段**

   1. 从您的AEM实例导航到 **个性化** > **活动** > **ScreensBrand** >**Screens值**.

   1. 单击 **创建** > **创建活动。** 此 **配置活动向导** 打开。

   1. 输入 **标题** 作为 **ValueCheck50** 和 **名称** 作为 **valuecheck50**. 单击 **定位引擎** 作为 **ContextHub (AEM)** 从下拉菜单中单击 **下一个**.

      ![图像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 单击 **添加体验** 从 `**Configure Activity**` 向导。

   1. 从 **受众**，单击 `**Higherthan50**` 并单击 **添加体验** 并输入 **标题** 作为 `**higherthan50**` **名称** 作为 `**higherthan50**`. 单击 **确定**.

   1. 从 **受众**，单击 `**Lowerthan50**` 并单击 **添加体验** 并输入 **标题** 作为 `**lowerthan50**` **名称** 作为 `**lowerthan50**`. 单击 **确定**.

   ![图像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 单击 **下一个** 然后 **保存**. `**ValueCheck50**` 现已创建并配置活动。

      ![图像](/help/user-guide/assets/context-hub/context-hub16.png)

## 步骤5：编辑受众中的区段{#editing-audience-segmentation}

1. **编辑区段**

   1. 从您的AEM实例导航到 **个性化** > **受众** > **屏幕**.

   1. 单击区段 `**Higherthan50**`，然后单击 **编辑** 从操作栏中。

   1. 拖放 **比较：属性 — 值** 组件添加到编辑器中。

   1. 单击扳手图标，以打开 **比较属性和值** 对话框。

   1. 单击 **google表/value/1/0** 从的下拉菜单中 **属性名称**.

      >[!NOTE]
      > 此 **google表/value/1/0** 引用中填充的行2和列 `google` 工作表：

      ![图像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 单击 **运算符** 作为 **大于** 从下拉菜单中。

   1. 输入 **值** 作为 **70**.

      >[!NOTE]
      >
      >AEM会将您的区段显示为绿色，以验证Google工作表中的数据。

      ![图像](/help/user-guide/assets/context-hub/context-hub18.png)

   同样，将属性值编辑为 `**Lowerthan50**`.

   1. 拖放 **比较：属性 — 值** 组件添加到编辑器中。

   1. 单击扳手图标。

   1. 在 **比较属性和值** 对话框中，单击 **google表/value/1/0** 从的下拉菜单中 **属性名称**.

   1. 单击 **运算符** 作为 **小于** 从下拉菜单中。

   1. 输入 **值** 作为 **50**.


## 在渠道中启用定位 {#step-enabling-targeting-in-channels}

执行以下步骤以在渠道中启用定位。

1. 导航到某个AEM Screens渠道。 以下步骤演示了如何使用启用定位 **DataDrivenChannel** 在AEM Screens渠道中创建。

1. 单击渠道 **TargetChannel** 并单击 **属性** 从操作栏中。

   ![图像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 单击 **个性化** 选项卡，以便设置ContextHub配置。

   1. 设置 **ContextHub路径** 到 `/conf/screens/settings/wcm/segments` 和 **区段路径** 到 `/conf/screens/settings/wcm/segments`.
   1. 将品牌设置为 **ScreensBrand** 从下拉菜单和 **设置区域引用** 到 **Screens值**.

   1. 单击“**保存并关闭**”。

      >[!NOTE]
      >
      >使用ContextHub和区段路径，您最初保存了ContextHub配置和区段。

      ![图像](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. 导航并单击 **TargetChannel** 渠道并单击 **编辑** 从操作栏中。

      >[!NOTE]
      >
      >如果一切设置正确，您会看到 **定位** 选项，如下图所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub21.png)

## 了解详情：示例用例 {#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的用例来了解数据触发的资源如何在不同的行业中发挥重要作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[行程中心温度激活](local-temperature-activation.md)**
1. **[Hospitality Reservation Activation](hospitality-reservation-activation.md)**
