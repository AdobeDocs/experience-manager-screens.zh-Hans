---
title: 使用动态嵌入式序列
seo-title: 使用动态嵌入式序列
description: 可查看本页以了解如何在AEM Screens项目中实施动态嵌入式序列。
seo-description: 可查看本页以了解如何在AEM Screens项目中实施动态嵌入式序列。
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: 119d5bdf854674ae86682ed82fee390f63972c0a

---


# 使用动态嵌入式序列 {#using-dynamic-embedded-sequence}

使用动态嵌入式序列涵盖以下主题：

* **概述**
* **在AEM Screens中使用动态嵌入式体验**
* **查看结果**
* **限制用户和修改ACL**

## 概述 {#overview}

***为遵循父子层次结构的大型项目创建动态嵌入式序列*** ，其中子项在位置文件夹而非渠道文件夹中引用。 It allows the user to embed a sequence inside a channel by ***Channel Role***. 它允许用户使用主渠道中的嵌入式序列为不同办公室定义特定位置的占位符。

将渠道分配给显示屏时，您可以选择指定显示屏的路径或渠道角色，这些渠道将按上下文解析为实际渠道。

要使用动态嵌入式序列，请按渠道角色分配 ***渠道***。 渠道角色定义显示的上下文。 该角色由各种操作定位，并且与完成该角色的实际渠道无关。 此部分描述了一个按角色定义渠道的用例，以及如何将该内容用于全局渠道。您还可以将角色视为分配的标识符，或在的上下文中将该渠道的别名。

### 使用动态嵌入式序列的优势 {#benefits-of-using-dynamic-embedded-sequences}

将序列渠道放置在位置而不是渠道文件夹内的主要好处是允许本地或区域作者编辑与其相关的内容，同时限制本地或区域作者在层次结构中从较高位置编辑渠道。

Referencing a *Channel By Role*, allows you to create local version of a channel, in order to dynamically resolve location-specific content and also allows you to create a global channel that leverages the content for the location-specific channels.

>[!NOTE]
>
>**嵌入式序列与动态嵌入式序列**
>
>动态嵌入式序列与嵌入式序列类似，但允许用户遵循一个层次结构，在该层次结构中，对一个渠道所做的更改／更新会传播到相关的其他渠道。 它遵循父子层次结构，还包括图像或视频等资产。
>
>***“动态嵌入式序列*** ”允许您显示特定于位置的内容，而“嵌入式序 ***列*** ”仅显示内容的常规幻灯片。 此外，在设置动态嵌入式序列时，您需要使用渠道角色和名称配置渠道。 有关实际实施，请参阅以下步骤。
>
>要了解有关实现嵌入式序列的更多信息，请参 [阅AEM Screens中的嵌入式序列](embedded-sequences.md) 。

以下示例重点介绍以下关键术语，从而提供解决方案：

* 全 ***局序列的主序列*** -通道
* ***用于序列的每个本地可自定义部分的动态嵌入式序列组件*** ，该动态嵌入式序列组件包括：
* ***单个序列渠道*** ，在显示屏中具有 *角色* ，该角色与动态嵌入式序 **列组件的角色相&#x200B;*匹配*。**

>[!NOTE]
>
>To learn more about channel assignment, see **[Channel Assignment](channel-assignment.md)**under Authoring section in AEM Screens documentation.

## 使用动态嵌入式序列 {#using-dynamic-embedded-sequence-2}

以下部分介绍如何在AEM Screens渠道中创建动态嵌入式序列。

### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保您已准备好以下先决条件以开始实施动态嵌入式序列：

* 创建AEM Screens项目(在此示例中， **Demo**)

* 在“渠道”文件夹下 **创建** “ **全局** ”

* 将内容添加到 **Global** Channel(*请检查&#x200B;**Resources.zip**，获取相关资产*)

下图显示了Channels文件夹 **中** Global Channel **的Demo****项目** 。
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### 资源 {#resources}

您可以下载以下资源（图像并将这些资源添加到资产中），并进一步将这些资源用作渠道内容以进行演示。

[获取文件](assets/resources.zip)

>[!NOTE]
>
>有关如何创建项目以及如何创建序列渠道的其他信息，请参阅以下资源：
>
>* **[创建和管理项目](creating-a-screens-project.md)**
>* **[管理渠道](managing-channels.md)**
>



在AEM Screens项目中实施动态嵌入式序列涉及三项主要任务：

1. **设置项目分类，包括渠道、位置和显示**
1. **创建计划**
1. **将计划分配给每个显示屏**

请按照以下步骤实现该功能：

>[!CAUTION]
>
>在实施动态嵌入式序列时，在每个位置下创建渠道时， **请注意****“名称”和“标题** ”字段。 请仔细按照命名说明操作。

1. **创建两个位置文件夹。**

   导航到AEM Screens项目 **中的位置** ，并创建两个位置文件夹，分别作为区域A **和区** 域B ****。

   >[!NOTE]
   >
   >在创建 **Region A** location文件夹时，请确保输入 **Title** as **Region A** ，并且您可以将 ******** Name字段留空，以便自动提取Region-a Name。
   >
   >类似情况下，创建位置文件夹 **Region B**，如下所示：

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >
   >要了解如何创建位置，请参阅创 **[建和管理位置](managing-locations.md)**。

1. **在每个位置文件夹下创建两个位置和一个渠道。**

   1. 导航到 **演示** —>位 **置** —> **区域A**。
   1. 选择 **区域A** ，然后单击操 **作栏中的** +创建。
   1. 从 **标题为** Store 1的向导中 **选择** “ **位置”**。 同样，从标题为“商店2”的向导中创建另一个 **位置** ，将标题 **设置为** 商店2 ****。 在创建商店1和 **商店** 2时，您可以将“名称 **”字段保留为空******。
   1. 重复步骤(b)，现在从向导 **中选择序列渠道** 。 对于此 **渠道** ，输 **入标题** （A区域）和名 **称** （A区域）。
   >[!CAUTION]
   >
   >请确保在创建渠道 **A区域时**，输入 **Title** as **Region A，并将NameName**********&#x200B;作为Region A。

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   同样，在标题为“商店3”和“ **商店4** ”的“ **区域B** ”下创建两个位置 ****。 此外，还可以创建序列通 **道，** 其中 **B** 为 **B区域，Name** ******** Channel为Adobe As The Region。

   >[!CAUTION]
   >
   >请确保您可以对在区域A和区域B中创建的渠道使 **用相同的名** 称 **作为区** 域 ****。

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **在每个位置下创建显示屏和渠道。**

   1. 导航到 **Demo** — > **Locations** — > **Region A** — ****> Store 1
   1. 选 **择Store 1** ，然后单击操 **作栏中的Create** 。
   1. 从向 **导中选择** “显示”，然后创建 **Store1Display。**
   1. 重复步骤(b)，此时从向导中 **选择序列渠道** 。 输入 **Title** **as** Store1Channel **,** Name **as store** Therned。
   >[!CAUTION]
   >
   >创建序列渠道时，渠道的 **Title** （标题）可以作为您的要求，但 **Name** （名称）应在所有本地渠道中相同。
   >
   >在这方面， **A** , **B区下的信道与** RegionAndB **StoreStoreStore 2,Store 3Store,Store 4StoreShoreShoreShore的同一RegionA区和** B区下的信道和Stre下的信道相同，例如ShoreShoreSheShopSheShChaShopSheShShopShShore ShoreSShore Shore **************************** ShoreShS

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   同样，在 **Store 2** (名称为 **Store2Display)下创建Store2Display和** Store2Channel **(****** Store 2Channel)显示。

   >[!NOTE]
   >
   >请确保您可以对在商店1和商店2中创建的渠道使 **用同一名** 称 **作商** 店 ****。

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   按照以上步骤，在“区域B”下的“商店3 **”和“商店4”中创建一个** 渠道并显示 **该渠道******。 同样，请确保在创建Channel **** Store3Channel **和** Store4Channel时使用与 ******** store相同的名称。

   下图显示了 **Store 3中的显示屏和渠道**。

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   下图显示了 **Store 4中的显示屏和渠道**。

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **将内容添加到相应位置的渠道。**

   导航到演示 **- >位置** - >区域A **- >区** 域A ************ - >单击操作栏中的A和Edit Bar。 拖放要添加到渠道的资产。

   >[!NOTE]
   >
   >您可以使用上 ***面“资源*** ”部分中的 **** Resources.zip文件，将图像用作渠道内容的资产。

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   同样，导航到 **Demo** -> **Locations** -> **Region B** -> **Region B****** -> ClickBardEditAction from the Action，将资产拖放到您的渠道中，如下所示：

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   请按照上述步骤和资源将内容添加到以下渠道：

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **创建计划**

   在AEM Screens项目中导 **航并选择** “计划”文件夹，然后单击操作栏中的 **创建** ，以创建新计划。

   下图显示了在 **Demo项目中创建的** AdSchedule **** 。

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **将渠道分配到计划**

   1. 导航到演 **示** — **Schedules** —> **AdSchedule** （计划），然后单击 **** 操作栏中的控制面板。
   1. 单击 **+从“已分配渠道** ”面 **板中指定渠道** ，以打开“渠道 **分配** ”对话框。
   1. Select **Reference Channel**.. by path.
   1. 选择Channel **Path** as **Demo** —>Channels ***—*** > Global ****** Reading。
   1. Enter the **Channel Role** as **GlobalAdSegment**.
   1. 选择“ **Events** Intial Load **”(初始加载**)、“Idle Screen **”（空闲屏幕）和“User Interaction Supported**”(用户交互支 ****&#x200B;持的ZhidleJ)。
   1. 单击&#x200B;**保存**。
   **按角色为区域分配渠道：**

   1. 单击 **+从“已分配渠道** ”面 **板中指定渠道** ，以打开“渠道 **分配** ”对话框。
   1. 选择 **引用渠道**.. 按照名称.
   1. 输入渠 **道名称** ，作 **为区域***。
   1. Enter the **Channel Role** as **RegionAdSegment**.
   1. 单击&#x200B;**保存**。
   **按角色为商店分配渠道：

   1. 单击 **+从“已分配渠道** ”面 **板中指定渠道** ，以打开“渠道 **分配** ”对话框。
   1. 选择 **引用渠道**.. 按照名称.
   1. 输入渠 **道名称** ，作 **为商店**。
   1. Enter the **Channel Role** as **StoreAdSegment**.
   1. 单击&#x200B;**保存**。
   下图显示了按路径和角色分配的渠道。

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **将动态嵌入式序列配置为全局渠道。**

   导航到全 **局渠道** ，您最初是在 **Demo项目中创建的** 。

   Click **Edit** from the action to open the editor.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   在渠道编辑器中 **拖放两个动态嵌入式序列组件** 。

   从其中一个组件中打开属性，然后将渠道分配角 **色输入为** RegionAdSegment **（区域AdSegment）**。

   同样，选择其他组件并打开属性以将渠道分配角 **色输入为****StoreAdSegment**。

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **将计划分配给每个显示屏**

   1. 导航到每个显示屏，如 **Adobe** —> **Locations** > **Region A** —>******** Store 1-Display Store 1 DisplayStore。
   1. Click **Dashboard** from the action to open the display dashboard.
   1. 单击 **...** 从“已分 **配的渠道和计划** ”面板，然后单击 **+分配计划**。
   1. 选择计划的路径(例如，此处， **Demo** —>计划 **—>** AdSchedule ****)。
   1. 单击&#x200B;**保存**。

## 查看结果 {#viewing-the-results}

为渠道和显示完成设置后，请启动AEM Screens播放器以查看内容。

>[!NOTE]
>
>要了解AEM Screen Player，请参阅以下资源：
>
>* [AEM Screens播放器下载](https://download.macromedia.com/screens/)
>* [使用AEM Screens播放器](working-with-screens-player.md)



以下输出会根据显示路径确认AEM Screens播放器中的渠道内容。

**方案1**:

如果将显示路径指定为 **Demo** —> **Locations** —> **A区域** —>** Store 1** —> **** Store1DisplayScreens，则以下内容将在您的AEM Screens播放器上显示。

![channeldisplay1](assets/channeldisplay1.gif)

**方案1**:

如果将显示路径指定为 **Demo** —> **Locations** —> **Region B** —> **Region B —>****** Store 3 — Display Store3 Store，则后续内容将在您的AEM Screens播放器上显示。

![channeldisplay2](assets/channeldisplay2.gif)

## 限制用户和修改ACL {#restricting-users-and-modifying-the-acls}

您可以创建全局、区域或本地作者来编辑与其相关的内容，同时限制他们在层次结构中的上级编辑渠道。

您需要修改ACL以根据用户的位置限制用户访问内容。

### 示例用例 {#example-use-case}

以下示例允许您为上述演示项目创建三个用户。

为每个用户组分配的权限如下所示：

**组**:

* **全局作者**:由有权访问 **Demo** project中所有位置和渠道并具有所有读取、写入和编辑权限的用户组成。

* **区域——作者**:由对区域A和区域B具有读取、写入和编辑 **权限的****用户组成**。

* **商店——作者**:由只对 **Store 1**、 **Store 2**、 **Store 3**&#x200B;和 **** Store 4具有读、写和编辑权限的用户组成。

#### 创建用户组、用户和设置ACL的步骤 {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>要详细了解如何使用ACL隔离项目，以便每个个人或团队都能处理自己的项目，请参阅 **设置ACL**。

按照以下步骤创建用户组、用户并根据权限修改ACL:

1. **创建组**

   1. 导航到 **Adobe Experience Manager**。
   1. Click **Tools** --> **Security** --> **Groups**.
   1. 单击 **创建组** ，然后在 **** ID **中输入全局作**&#x200B;者。
   1. 单击 **保存并关闭**。
   同样，创建另外两个组，如 **Region-Author****和Store-Author**。

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **创建用户并将用户添加到用户组**

   1. 导航到 **Adobe Experience Manager**。
   1. Click **Tools** --> **Security** --> **Users**.
   1. 单击 **创建用户** ，然后在 **** ID中输入全局用户 ****。
   1. 输入 **密码** ，并确认此用户的密码。
   1. 单击“ **Groups** ”选项卡，然后在“ **Select Group**”中输入用户组名称，例如，输入 **Global-Author** ，将 **** Global-UserAdd to that specific group。
   1. 单击 **保存并关闭**。
   同样，创建另外两个用户(如 **Region-User** 和 **Store-User** )，并将这些用户分别添加到 **Region-Author** 和 **** Store-Author。

   >[!NOTE]
   >
   >最好将用户添加到组中，然后为每个特定用户组分配权限。

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **将所有组添加到参与者**

   1. 导航到 **Adobe Experience Manager**。
   1. Click **Tools** --> **Security** --> **Groups**.
   1. 从列 **表中选择** “参与者”，然后选择“ **成员** ”选项卡。
   1. 选择 **组** ，如Global-Author **、Region**- **Author和** Store-Author **** 给参与者。
   1. 单击 **保存并关闭**。

1. **访问每个用户组的权限**

   1. 导航到用 *户* ，然后使用此UI修改不同组的权限。
   1. 搜索全 **局作者** ，然后单击 **权限选项卡** ，如下图所示。
   1. 同样，您也可以访问“区域——作 **者”和“商店** -作 **者”的权限**。
   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **修改每个用户组的权限**

   **对于全局作者：**

   1. Navigate to the **Permissions** tab
   1. 导览至 ***/content/screens/demo*** ，并检查所有权限
   1. 导览至 ***/content/screens/demo/locations*** ，并检查所有权限
   1. 导航到 ***/content/screens/demo/locations***/***region-a并检查所有权限*** 。 同样，请检查 **region-b的权限**。
   请参阅下图以了解这些步骤：
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   下图显示，现在 **GlobalUser** Access **Channel And** B区(全局ChannelA **Store 1,StoreStoreStoreA)和GlobalStoreStoreStoreStoreStoreA(全局S********************** AASStoreASSSSSASSSS)都是ASerSSAAStoreASSerSerSerSSSSSSS,SStoreS,StoreSStoreSStoreSStoreStoreStoreSStoreSStoreSSSS

   ![全局](assets/global.gif)

   **对于区域——作者：**

   1. Navigate to the **Permissions** tab.
   1. 导览至 ***/content/screens/demo*** ，并仅选中“读取” **权限** 。
   1. 导览至 ***/content/screens/demo/locations*** ，并仅选中“阅读 **”权限** 。
   1. 导航到***/content/screens/demo/channels，然 ***后取消检查全局渠道&#x200B;**的权限**。***
   1. 导航到 ***/content/screens/demo/locations***/***region-a并检查所有权限*** 。 同样，请检查 **region-b的权限**。
   请参阅下图以了解这些步骤：

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   下图显示，Region-User现在可以访问 **A** 、 **B区域A和B区域Store** 11Store、 ******************** StoreStore 3、StoreStore 3和Store 4StoreStore 3、HutStoreStoreBut不会访问Global Channelobal Chelalous Chorelous Ch Chous Storered Choud Choud Phous（即Sere）的SedSelous(S(S)的(S)的(S)S)的.

   ![地区](assets/region.gif)

   **对于Store-Author:**

   1. Navigate to the **Permissions** tab.
   1. 导览至 ***/content/screens/demo*** ，并仅选中“读取” **权限** 。
   1. 导览至 ***/content/screens/demo/locations*** ，并仅选中“阅读 **”权限** 。
   1. 导航到 ***/content/screens/demo/channels*** ，然后取消选中全局渠道 **的权限** 。
   1. 导航到 ***/content/screens/demo/locations/region-a*** ，然后仅选中“阅读 **”权限** 。 同样，请仅选中 **region** -b的 **“读取”权限**。
   1. 导航到 ***/content/screens/demo/locations***/***region-a /store-1*** ，并检查所有权限。 同样，请检查 **store-2、store-3** 和 **store-4的权限**。
   请参阅下图以了解这些步骤：

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   下图显示， **Store-User** ，只有4家商店1 **、** Store **22、** Store 4、 **Store和Store只能访问Store-User** Store 12、 **************** Store 4，但目前没有到GlobalChops或Grobal区域（即B区）的访问权限。

   ![商店](assets/store.gif)

>[!NOTE]
>
>要详细了解设置权限，请参阅 [设置ACL](setting-up-acls.md)。

