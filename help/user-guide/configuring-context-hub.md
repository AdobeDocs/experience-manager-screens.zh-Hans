---
title: 在AEM Screens中配置ContextHub
seo-title: 在AEM Screens中配置ContextHub
description: 可查看本页以了解定位引擎中的ContextHub，以定义数据存储，以便触发内容更改。
seo-description: 可查看本页以了解定位引擎中的ContextHub，以定义数据存储，以便触发内容更改。
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: f5062a0610f7258240c3ed698e0c4c276b0823a2

---


# 在AEM Screens中配置ContextHub {#configuring-contexthub-in-aem-screens}

本节重点介绍如何使用数据存储创建和管理数据驱动的资产更改。

## 主要条款 {#key-terms}

在我们了解有关在AEM Screens项目中创建和管理库存驱动型渠道的详细信息之前，您必须了解一些重要且与不同方案相关的关键术语。

**品牌** -指您的高级项目描述。

**区域** ：指您的AEM Screens项目名称，如数字广告标牌

**活动** 定义规则类别，如库存驱动、天气驱动、部门可用性驱动等。

**受众** 定义规则。

**细分** ：指按照给定规则播放的资产版本，例如，如果温度低于50华氏度，则屏幕将显示热咖啡的图像，否则显示冷饮。

下图直观地显示了ContextHub配置如何与活动、受众和渠道保持一致。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先决条件 {#preconditions}

在开始为AEM Screens项目配置Context Hub配置之前，您必须设置Google工作表（用于演示目的）。

>[!IMPORTANT]
>
>在以下示例中，Google Sheets用作获取值的示例数据库系统，仅用于教育目的。 Adobe不支持将Google Sheets用于生产环境。
>
>有关详细信息，请参 [阅Google文档中的Get API Key](https://developers.google.com/maps/documentation/javascript/get-api-key) 。

## 第1步：设置数据存储 {#step-setting-up-a-data-store}

可以将数据存储设置为本地I/O事件或本地数据库事件。

以下资产级数据触发器示例展示了一个本地数据库事件，该数据库渠道设置了数据存储（如Excel表），允许您使用ContextHub配置和AEM Screens的区段路径。

在正确设置Google工作表后，例如，如下所示：

![图像](/help/user-guide/assets/context-hub/context-hub1.png)

以下验证是通过输入以下格式的 *googlesheet ID和* API密钥这两个值检查连接时要视图的验证内容 ** :

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![图像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
> 以下特定示例将google工作表显示为一个数据存储库，如果该值大于100或小于50，则该数据存储将触发资产更改。

## 第2步：设置存储配置 {#step-setting-store-configurations}

1. **导航到ContextHub**

   导航到您的AEM实例，然后单击左侧提要栏中的工具图标。 单 **击Sites** —> **ContextHub**，如下图所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **创建新的ContextHub存储配置**

   1. 导航到标题为屏幕的配置容器 ****。

   1. 单击 **创建** >创 **建配置容器** ，然后输入 **ContextHubDemo作为标题**。

      ![图像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **导航到** ContextHubDemo **>创建** ContentHubDemo配 **置中心** ，然后单击 **Save******（保存）。

      >[!NOTE]
      > 单击“保 **存** ”后，将显示在 **ContextHub“配置”屏幕中** 。

   1. 在ContextHub配置 **屏幕中** ，单击 **创建** > **ContentHub存储配置。**

      ![图像](/help/user-guide/assets/context-hub/context-hub5.png)

   1. 在“ **Google Store Name** , **Google Store Sheets Type Store Store** AsConthuthub. ********************Jsonp”中输入Google Store Sheets、Google SheetsType StoreStoreS和ConteGleName。
      ![图像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 输入您的特定json配置。 例如，您可以将以下json用于演示目的，然后单击“ **保存** ”，您会在ContextHub配置中看到标题为“ **Google工作表** ”的存储配置。

      >[!IMPORTANT]
      >确保将代码替换为您在设 *置Google工作表时获取的**&lt;Sheet ID>和*&lt;API Key>。

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
      在上述示例代码中， **pollInterval** 定义刷新值的频率（以毫秒为单位）。
将代码替换为您在设 *置Google工作表时获取的**&lt;Sheet ID>和*&lt;API Key>。

      >[!CAUTION]
      如果您在全局文件夹（例如您自己的项目文件夹中）之外创建Google工作表存储配置，则定位将不会立即生效。

1. **设置商店分段**

   1. 导航到 **ContentHub存储配置。** 在屏幕配置容器中创建另一个存储配置，并将 **Title** -contexthub **、** Store Name设置为 **************** Store分段，TypeStoreSegmentationAs.aem.segmentationStore。

      ![图像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
您必须跳过定义json的过程，将其留空。


## 第3步：设置受众 {#setting-up-audience}

待定：添加属性

1. **在受众中创建区段**

   1. 从AEM实例导航到“个 **性化** ” > **受众** > **屏幕**。

   1. 单击 **创建** > **创建Context Hub区段。** “新 **建ContextHub区段** ”对话框打开。

   1. Enter the **Title** as **TargetValue1** and click **Create**. 同样，创建标题为 **TargetValue2的另一个区段**。

      ![图像](/help/user-guide/assets/context-hub/context-hub10.png)



## 第4步：设置受众分段 {#step-setting-up-audience-segmentation}

待添加编辑

设置数据存储并定义活动（品牌和区域）后，请按照以下步骤设置受众区段：

1. **在受众中创建区段**

   1. 从AEM实例导航到“个 **性化** ” > **受众** > **屏幕**。

   1. 单击 **创建** > **创建Context Hub区段。** “新 **建ContextHub区段** ”对话框打开。

   1. Enter the **Title** as **TargetValue1** and click **Create**. 同样，创建标题为 **TargetValue2的另一个区段**。

      ![图像](/help/user-guide/assets/context-hub/context-hub10.png)


1. **编辑区段**

   1. 选择区段 **TargetValue1**，然后单 **击操作栏中的** “编辑”。

   1. 拖放比 **较：属性——编辑器的值组件** 。
   1. 单击扳手图标以打开“ **将属性与值比较** ”对话框。
   1. 从 **属性名称的下拉菜单中选择** googlesheets/value/1/0 ****。

   1. 从下拉 **菜单中** , **选择“Operator** as equal”（运算符为等）。

   1. 输入 **值** 1 ****。
   >[!NOTE]
   AEM会将区段显示为绿色，以验证Google工作表中的数据。

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   同样，将属性值编辑为 **TargetValue2**。

   1. 拖放比 **较：属性——编辑器的值组件** 。
   1. 单击扳手图标以打开“ **将属性与值比较** ”对话框。
   1. 从 **属性名称的下拉菜单中选择** googlesheets/value/1/0 ****。

   1. 从下拉 **菜单中** ，将运 **算符选为Equal** 。

   1. 将值输 **入****为2**。



## 第5步：设置品牌和区域 {#setting-brand-area}

请按照以下步骤在您的活动和品牌下的区域中创建品牌：

1. **在活动中创建品牌**

   1. 从您的AEM实例导航到“个 **性化** ”> **活动**。

   1. 单击 **创建** > **创建品牌**。

   1. Select **Brand** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. 您的品牌现在创建如下。

      ![图像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      已知问题：要添加区域，请从URL中删除主页，如
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **在品牌中创建区域**

   按照以下步骤在品牌中创建区域：

   1. 单击 **创建** ，然后单 **击创建区域**。

      ![图像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Select **Area** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
将在您的品牌中创建区域。

## 第6步：设置活动 {#step-setting-up-activity}

按照以下步骤在品牌中创建区域：

1. 导航到 **ScreensValue** （在前一步中创建），然后单击“创 **建** ” **>“**&#x200B;创建活动”。

1. 将打 **开配置活动向导** 。 将标题输 **入为** targetvaluecheck **，将名称输** 入为 ******** targetvaluecheck。 从下拉 **菜单中选择****ContextHub(AEM)** 作为定位引擎，然后单击“下 **一步**”。

1. 单击 **配置活动向导** 中的 **添加体验**。

1. 从 **受众中**，选择TargetTargetValue ************************，然后单击Add ExperienceAdd TitleExperience，并将TitleHitleInter作为ValuececheckNameHeckAsValueCheckNameHeckAdAl进入ExperireAntAntAntAnAl的AnAntAAAAAAAAASSSAASSASAAAASSAASSASSASAAASReASAAAAASSAASiSASAASSA

1. 同样，从 **受众中**，选择 **Value2Value2** ，然后单击TargetValue2 **,Experience As** ValuecheckNameAs **AstValueCheckAstValueCheckAsProducts的TargetValue2并进入AdExpecheckExperienceirience** 和 ************ AtireiechAs。

1. Click **Next** and then **Save**.

## 在渠道中启用定位 {#step-enabling-targeting-in-channels}

按照以下步骤在您的渠道中启用定位。

1. 导航到其中一个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens渠道中创 **建的DataDrivenRetail** 启用定位。

1. 选择渠道 **DataDrivenRetail** ，然后 **单击操作栏中的Properties** 。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 选择“个 **性化** ”选项卡以设置ContextHub配置。

   1. 选择“ **Hub Path** ”作 **为** Libs **>** > Settings > DefaultHub **>DefaultHob Context Configurations(Libs**************> Settings > DefaultHub Context And Click SelectCloveCt”。

   1. 选择“路径 **”** >“会议” **>“零售”****>“零售”** >“Wcm **”**************>“Adobe ClickSelectSelectDign”的段。

   1. 单击 **保存并关闭**。
   >[!NOTE]
   使用ContextHub和“区段”路径，您最初在该路径中保存了Context Hub配置和区段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 导航并从DataDrivenAssets >中选 **择DataDriven Retail** ，然后单 **击渠道** 栏中的 **DataDriven Retail** , **** 然后单击EditFrom the action bar。

   >[!NOTE]
   如果您正确设置了所有内容，您将在编辑器的下拉框中看到 **Targeting** （定位）选项，如下图所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   为渠道配置ContextHub配置后，如果您希望遵循以下所有使用案例，请确保对于其他三个序列渠道也遵循前面的步骤（从1到4）。

## 了解更多：示例用例 {#learn-more-example-use-cases}

在为AEM Screens项目配置ContextHub后，您可以按照不同的使用案例了解数据触发资产如何在不同行业中扮演关键角色：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**
