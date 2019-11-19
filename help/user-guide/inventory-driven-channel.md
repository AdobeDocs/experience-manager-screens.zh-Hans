---
title: 库存驱动型渠道
seo-title: 库存驱动型渠道
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 库存驱动型渠道{#inventory-driven-channel}

## 库存驱动型渠道快速入门 {#getting-started-with-inventory-driven-channels}

本节介绍一个使用案例示例，该示例着重介绍如何使用Google工作表创建和管理数据驱动的资产更改。

### 先决条件 {#preconditions}

在开始此使用案例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理计划](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要演员 {#primary-actors}

内容作者

### 术语 {#terminolgies}

按照以下条款，在了解和设置不同用例中的项目时发挥重要作用：

**活动** “活动”指类别。

**Area** Project main

**数据的受众位置**

**品牌** -品牌-

**区段** “区段”是指您尝试定位的资产容器。

### 基本流程：设置项目 {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**入门项目：**
>
>在深入了解有关在项目中设置和使用数据驱动的资产更改的详细信息之前，请确保您使用序列渠道创建AEM Screens项目。 为便于演示，将创建标题为 **DataDrivenAsset** ，并将标题为DataDrivenTextOverlay的频道排序为 **DataRestaurant**、 **DataDrivenTextOverlay**、 ******** DataDrivenWeatherThaster、DataDrivenDeplind和RetaRetaRetaistalMary的频道添加到项目中，如下图所示的项目。
>
>创建四个不同的渠道仅用于演示目的，并在不同渠道中展示四个不同的使用案例。 如果您只希望根据自己的要求遵循一个用例，请随意创建一个序列渠道。

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

请按照以下各节，在AEM Screens项目中使用Google工作表创建和管理数据驱动型资产更改的示例项目：

## 第1步：设置数据库 {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets在以下示例数据库系统中使用，从中获取值并仅用于教育目的。 Adobe不支持将Google工作表用于生产环境。
>
>有关详细信息，请参 [阅Google文档中的Get API Key](https://developers.google.com/maps/documentation/javascript/get-api-key) 。

1. 登录Google Docs。

   >[!NOTE]
   >
   >在创建新的Google工作表之前，您必须在Google drive中拥有帐户。

1. 启动新的空白电子表格。 将内容添加到Google工作表并保存。 为便于演示，将Google工作表命名为 **ContextHubDemo**。
1. 单 **击Google Sheet** 右上角的“共享”以打开“与其 **他人共享** ”对话框。 单击 **“高级** ”选项并将设置更改为“ **打开——任何人”(On - Anywhere with the link**)，如下图所示。

   此步骤允许您访问Google工作表中的值。

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. 单击上 **一步的** “保存”后，您将获得Google工作表的链接。 保存单击以供将来引用，然后单击“ **完成**”。

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets在以下示例中用于教育用途。 Adobe不支持将Google工作表用于生产环境。

## 第2步：启用Google Sheets REST API {#step-enabling-the-google-sheets-rest-apis}

设置Google工作表后，必须启用Google工作表REST API才能访问这些值。

要了解如何为Google工作表启用REST API，请参阅Google API文档。

1. 导航到 [Google API控制台](https://console.developers.google.com/apis/credentials)。 Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. 在项目名 **称中输入** AssetChange **，然后单** 击创建 ****。
1. 创建需要设置API密钥的项目后。 单 **击创建凭据** ，然后选择**API密钥**以为项目生成API密钥。 保存API密钥以供将来参考。

   >[!NOTE]
   >
   >此演示项目使用免费的Google API密钥。 有关详细信息，您可能想要参阅Google网站 **Get API key的定价和限制** 。

### 验证Google工作表的设置 {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;您的工作表id&gt;/values/Sheet1?key=&lt;您的API密钥&gt;

例如：

如果** Google Sheets**链接如 *下所示：*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`, then

**工作表ID** : `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**API密钥** : `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

在上述语法中添加这两个值：

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

您现在应该可以查看工作表中的数据。

## 第2步：配置AEM以获取Google工作表的内容 {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

以下部分介绍如何配置Adobe Experience Manager(AEM)以从Google工作表中提取内容。

1. 导航到您的AEM实例，然后单击左侧提要栏中的工具图标。 单 **击Sites** —&gt; **ContextHub**，如下图所示。

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **创建新的ContextHub存储配置**

   1. 导航到 **全局** &gt; **default** &gt; **ContextHub配置**。

   1. 单击**“创建”&gt;“配置容 **器”，然后输入** ContextHubDemo**的标题。

   1. **** 导航到&#x200B;**ContextHubDemo**&gt;**** ContentHub存储配置……打开配置 **向导**
   1. 输入Google **Sheets** , **Store Sheets,** Store Name **, as************Google Sheets, Store Store Sheets Sheets, Store Name, as Contexthub-jsonp.**
   1. Click **Next**
   1. 输入您的特定json配置。 例如，您可以将以下json用于演示目的。
   1. 单击&#x200B;**保存**。

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >在上述示例代码中， **pollInterval** 定义刷新值的频率（以毫秒为单位）。
   >
   >
   >将您从步骤1 *获取的代码替换为**&lt;Sheet ID&gt;和*&lt;API Key&gt; **:设置数据库。**

   >[!CAUTION]
   如果您在旧版文件夹（例如您自己的项目文件夹中）之外创建Google工作表存储配置，则定位将不会开箱即用。
   如果要在全局旧文件夹之外配置Google Sheets商店配置，则必须将 **Store Name** （商店名称）设置为 **segmentation** ，将 **Store Type** （商店类型）设 ****&#x200B;置为aem.segmentationProducer。 此外，您还必须跳过定义上述定义的json的过程。

1. **在活动中创建品牌**

   1. 从AEM实例导航到“个性化” **&gt;“活****动”**

   1. 单击**创建** &gt;创 **建品牌**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. 您的品牌现在创建如下。
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
已知问题：
要添加区域，请从URL中删除主页，如
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. 在品牌中创建区域**

   1. 单击“ **创建** ”&gt;“ **创建区域”**

   1. Select **Area** from the** Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**. 您的区域将在活动中创建。

1. **在受众中创建区段**

   1. 从您的AEM实例导航到“个 **性化** ”&gt;“受众 **”** &gt;“ **We.Retail**”。
   1. 单击 **创建** &gt; **创建Context Hub区段**。 “新建ContextHub区段”对话框打开。
   1. Enter the **Title** as **SheetA1 1** and click **Create**. 同样，创建标题为 **SheetA2 2的另一个区段**。

1. **编辑区段**

   1. 选择区段 **工作表A1 1** (在步骤(5)中创建)，然后单击操 **作栏中的编** 辑。

   1. 拖放比 **较：属性——编辑器的值组件** 。
   1. 单击扳手图标以打开“ **将属性与值比较** ”对话框。
   1. 从 **属性名称的下拉菜单中选择** googlesheets/value/1/0 ****。

   1. 从下 **拉菜单中** ，将运算符选为**Equal **。

   1. 输入 **值** 1 ****。
   >[!NOTE]
   AEM会将区段显示为绿色，以验证Google工作表中的数据。

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   同样，编辑表A1 2 **的属性值**。

   1. 拖放比 **较：属性——编辑器的值组件** 。
   1. 单击扳手图标以打开“ **将属性与值比较** ”对话框。
   1. 从 **属性名称的下拉菜单中选择** googlesheets/value/1/0 ****。

   1. 从下 **拉菜单中** ，将运算符选为**Equal **。

   1. 将值输 **入****为2**。
   >[!NOTE]
   在前面的步骤中应用的规则只是一个示例，说明如何设置区段以实现以下用例。

## 第3步：在AEM Screens渠道中设置Context Hub配置 {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

请按照以下步骤设置指向AEM Screens渠道的ContextHub配置和区段路径。

1. 导航到您作为入门项目创建的某个AEM Screens **渠道(DataDrivenRetail**)。
1. 选择渠道(**DataDrivenRetail**)，然后单 **击操作栏中的** “属性”。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 选择“个 **性化** ”选项卡以设置ContextHub配置。

   1. 选择“ **Hub Path** ”作 **为** Libs **&gt;** &gt; Settings &gt; DefaultHub **&gt;DefaultHob Context Configurations(Libs**************&gt; Settings &gt; DefaultHub Context And Click SelectCloud”的Context路径。

   1. 选择段路 **径** Path **Conf** &gt; **We.Retail *&gt; **Settings** &gt; ************ Wcm Select Select Josect Select Jost Select Jost。

   1. 单击 **保存并关闭**。
   >[!NOTE]
   使用ContextHub和“区段”路径，您最初在该路径中保存了Context Hub配置和区段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   如果未从上面的对话 **框中选择** “定位配置”下的品牌 **** ，则在启动定位过程时，您必须选择品牌和活动。

1. 从DataDrivenAssets &gt; **Channels **中导 **航并选择DataDrivenRetail** ，然后单击操作栏中的 **Edit****** 。

   >[!NOTE]
   如果您正确设置了所有内容，您将在编辑器的下拉框中看到 **Targeting** （定位）选项，如下图所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   为渠道配置ContextHub配置后，如果您希望遵循以下所有使用案例，请确保对其他三个序列渠道也遵循前面的步骤（从1到4）。

## 用例1:零售库存激活 {#use-case-retail-inventory-activation}

以下用例根据Google工作表中的值演示了三个不同的图像。

### 描述 {#description}

此“用例”显示三种不同颜色的血汗衫的零售库存。 根据Google Sheets中记录的库存中可用的运动衫数量，屏幕上将显示编号最高的图像（红色、绿色或蓝色运动衫）。

对于此用例，红色、绿色或蓝色毛衣将根据可用毛衣数量的最高值显示在屏幕上。

### 过程 {#procedure}

请按照以下步骤实施“零售库存激活”用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo google工作表。
   1. 添加三列（红色、绿色和蓝色），并为三个不同的运动衫添加相应的值。
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根据要求配置受众**

   1. 导航到受众中的区段(在步骤2的第(5)节中 ***创建):配置AEM以获取Google工作表的内容***)。
   1. 添加三个 **新段For_Red**、 **For_Green**&#x200B;和 **For_Blue**。

   1. 选 **择For_Red** ，然后单 **击操作栏中的** “编辑”。

   1. 拖放比 **较：属性** -编辑器的属性，然后单击配置图标以编辑属性。
   1. 从“ **第一个属性名称”的下拉菜单中选择“****工具表／值/1/2”**

   1. 从下 **拉菜单中选择运算符** **greater-than **

   1. 选择数 **据类型** ，作为 **数字**

   1. 从 **第二个属性名称的下拉菜单中选择****googlesheets/value/1/1**

   1. 拖放**另一个比较：属性——对于编辑器的属性**，单击配置图标以编辑属性。
   1. 从“ **第一个属性名称”的下拉菜单中选择“****工具表／值/1/2”**

   1. 从下 **拉菜单中选择运算符** **greater-than **

   1. 选择数 **据类型** ，作为 **数字**

   1. 从“ **第二个属性名称** ”的下拉菜单中选择 **googlesheets/value/1/0**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同样，编辑比较属性规则并将其添加到 **For_Blue段** ，如下图所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同样，编辑比较属性规则并将其添加到** For_Green **区段，如下图所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   您会注意到，对于区段 **For_Green** 和 **For_Green**，数据无法加载到编辑器中，因为目前仅第一个比较有效，与Google工作表中的值相同。

1. 导航并选择您的**DataDrivenRetail **渠道（序列渠道），然后单击操 **作栏中的** “编辑”。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   您应该已使用“ **Properties** Properties **—********** Personalization Chub”选项卡设置ContextHub配置。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   如上图所示，如果您在为项目设置 **ContextHub** （定位配置）下未添加 **Brand** ContextConfigurations(品牌 **BrandHub)配置时，确实需要在开始定位过程时选择********** BrandActivityApprigation，同时在下一步中进行定位。

1. **添加默认图像**

   1. 将默认图像添加到渠道，然后单击定 **位**。
   1. 从下 **拉菜单中选择品** 牌 **和活动** ，然后单击开始 **定位**。

   1. 单击&#x200B;**开始定位**。
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在开始定位之前，必须通过单击侧边栏中的&#x200B;**+ Add Experience Targeting来添加区段(** For_Green **、** For_Red **和** For_Blue **** )，如下图所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 将图像添加到所有三个不同的屏幕，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **检查预览**

   1. 单击“ **预览”。** 此外，打开Google工作表并更新其值。
   1. 更改所有三个不同列的值，您会注意到显示图像会根据库存中的最高值进行更新。
   ![retail_result](assets/retail_result.gif)

## 用例2:旅游中心天气激活 {#use-case-travel-center-weather-activation}

以下用例根据Google工作表中的值演示了两个不同的图像。

### 描述 {#description-1}

对于此“用例”，如果您的Google Sheets的“值”小于50，则将显示含有热饮的图像，如果该值大于或等于50，则将显示含有冷饮的图像。 如果存在其他值或没有值，播放器将显示默认图像。

### 过程 {#procedure-1}

请按照以下步骤为您的AEM Screens项目实施旅游中心天气激活用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo google工作表。
   1. 添加一个带有 **Heading1的列** ，其中具有相应的温度值。
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(在步骤2的第(5)节中 ***创建):配置AEM以获取Google工作表的内容***)。
   1. 选择“ **工作表A1 1** ”，然后单 **击编辑**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择“Googlesheets/value/1/0** ”( **Property name)**

   1. 从下 **拉菜单中** ，将运算符选为**greater-than-or-equal **

   1. 输入 **值** 50 **。**

   1. 同样，选择**工作表A1 2 **并单击“编 **辑”**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择“Googlesheets/value/1/0** ”( **Property name)**

   1. 从下 **拉菜单中选择运算符** **less-than **

   1. 输入 **值** 50 **。**

1. 导航并选择渠道()，然后单击操 **作栏** 中的编辑。 在以下示例中， **DataDrivenWeather**，使用顺序通道来展示该功能。

   >[!NOTE]
   您的渠道应已拥有默认图像，并且应按步骤(3)中所述预配置受众

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   您应该已使用“ **Properties** Properties **—********** Personalization Chub”选项卡设置ContextHub配置。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   如上图所示，如果您在为项目设置 **ContextHub** （定位配置）下未添加 **Brand** ContextConfigurations(品牌 **BrandHub)配置时，确实需要在开始定位过程时选择********** BrandActivityApprigation，同时在下一步中进行定位。

1. 从编 **辑器中选择** “定位”，从 **Brand** （品牌）和 **Activity** （活动）下拉菜单中选择，然后单击“开始定 ****&#x200B;位”。

   >[!NOTE]
   如果在为项目设置 **** ContextHub **Configurations时在“定位配置”下添加了Brand** Brand，则无需在此步骤中选择 ************ BrandBrand和Activity。

   ![new_activity3](assets/new_activity3.gif)

1. 检查预览

   1. 单击“ **预览”。** 此外，打开Google工作表并更新其值。
   1. 将值更改为小于50，您应该能够查看夏季饮料的图像。 如果Google Sheet中的值大于或等于50，则应该能够查看热饮图像。
   ![result3](assets/result3.gif)

## 用例3:酒店预订激活 {#use-case-hospitality-reservation-activation}

以下用例根据Google工作表中应用的值和公式演示了两个不同的图像。

### 描述 {#description-2}

对于此用例，Google Sheet填充了两家餐馆 **Restaurant1和****Restaurant2的预订百分比**。 根据Restaurant1和Restaurant2的值应用公式，并根据公式将值1或2分配给 **AdTarget** 列。

如果Restaurant1 **&gt;** Restaurant2 **，则** AdTaget **值为1，否则****** AdTarget的分配值为2。 Value 1生成 *牛排美食* ,Value 2在显示屏上 *显示泰式美食* 。

### 程序方法 {#procedural-approach}

请按照以下步骤为AEM Screens项目实施酒店预订激活用例：

1. 填充Google工作表并添加公式。

   例如，将公式应用到第三列 **AdTarget**，如下图所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(在步骤2的第(5)节中 ***创建):配置AEM以获取Google工作表的内容***)。
   1. 选择“ **工作表A1 1** ”，然后单 **击编辑**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择Googlesheets/value/1/2****。**

   1. 从下 **拉菜单中选择运算符** **equal **

   1. 输入 **值** 1 **。**

   1. 同样，选择**工作表A1 2 **并单击“编 **辑”**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择Googlesheets/value/1/2****。**

   1. 选择运 **算符** ( **2)**

1. 导航并选择渠道()，然后单击操 **作栏** 中的编辑。 在以下示例中， **DataDrivenRestaurant**，使用顺序渠道来展示该功能。

   >[!NOTE]
   您的渠道应已拥有默认图像，并且应按步骤(3)中所述预配置受众。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   您应该已使用“ **Properties** Properties **—********** Personalization Chub”选项卡设置ContextHub配置。

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   如上图所示，如果您在为项目设置 **ContextHub** （定位配置）下未添加 **Brand** ContextConfigurations(品牌 **BrandHub)配置时，确实需要在开始定位过程时选择********** BrandActivityApprigation，同时在下一步中进行定位。

1. 从编 **辑器中选择** “定位”，从 **Brand** （品牌）和 **Activity** （活动）下拉菜单中选择，然后单击“开始定 ****&#x200B;位”。
1. 检查预览

   1. 单击“ **预览”。** 此外，打开Google工作表并更新其值。
   1. 在Restaurant1 &gt; Restaurant2中更改值，您应该能够查看牛排图像和Restaurant1 &lt; Restaurant12的图像，您应该能够在显示屏上查看泰式美食图像。
   ![result5](assets/result5.gif)

## 用例4:数字菜单板文本叠加 {#use-case-digital-menu-board-text-overlay}

以下用例演示了在餐馆和快餐店中常见的数字菜单板使用案例。

### 描述 {#description-3}

以下用例介绍了顺序渠道中文本叠加的用法，以及Google工作表中价格值更新如何触发文本叠加组件更新中的更新。

### 程序方法 {#procedural-approach-1}

请按照以下步骤为AEM Screens项目实施带有文本叠加用例的数字菜单板：

1. **填充Google工作表**

   1. 导航到您的Google工作表。
   1. 为用例添加一个定价值列，如下图所示。
   ![screen_shot_2019-05-05at11344am](assets/screen_shot_2019-05-05at111344am.png)

1. **向序列渠道添加图像**

   1. 导航并选择您的渠道(**DataDrivenAssets** —&gt; **Channels** —&gt; **DataDrivenTextOverlay**)。

   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
   1. 在编辑器中拖放一个苹果饼图。
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **向图像添加文本叠加**

   1. 在编辑器中选择图像，然后单击“配置”。
   1. 导航到“文 **本叠加** ”选项卡，并将文本叠加添加到图像。 要从Google工作表中获取该值，请确保该值包含在大括号中。 例如，从google工作表中获取价格，在定义文本叠加时， **该价格被提** 及为{price}。

   1. 导航到 **ContextHub** 选项卡，并配置要从google工作表中获取的值，如下图所示。
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **检查预览**

   <!-- Edit text in steps below. wonky-->

   1. 单击“ **预览**”。  此外，打开Google工作表并更新其值。
   1. 更改“ **价格** ”下的值，您会注意到文本叠加中使用的值会相应更新，如下图所示。
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
