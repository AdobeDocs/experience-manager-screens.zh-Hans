---
title: 为文本叠加应用自定义品牌和样式
description: 了解如何在AEM Screens渠道中为应用于资产的文本叠加应用自定义品牌和样式。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---

# 文本叠加图的自定义品牌和样式 {#creating-custom-branding-styling}

了解如何在AEM Screens渠道中为应用于资源的文本叠加应用自定义品牌和样式。

## 为文本叠加图创建自定义品牌和样式 {#steps-custom-branding}

请按照以下步骤为文本叠加创建自定义品牌和样式：

1. 创建一个AEM Screens项目。 此示例通过创建名为&#x200B;**`customstyle`**&#x200B;的项目和名为&#x200B;**DemoBrand**&#x200B;的渠道来展示功能，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 从编辑器中，拖放图像并向资源添加文本叠加。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >要了解如何在渠道编辑器中向资产添加文本叠加，请参阅[文本叠加](/help/user-guide/text-overlay.md)。

1. 从AEM实例导航到CRXDE Lite> tools > **CRXDE Lite**。

1. 在`/apps/settings/wcm/designs/<your-project>/`中创建自定义设计，例如，在此例中，导航到`/apps/settings/wcm/designs/customstyle/`

   ![图像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 创建&#x200B;*static.css*&#x200B;文件并设置以下css规则。 另显示为css规则下图的示例。

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![图像](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. 将路径复制到您的项目，在本例中，路径为`/apps/settings/wcm/designs/customstyle`。

1. 导航到标题为&#x200B;**DemoBrand**(在步骤(1)中创建)的频道，然后在选择该频道后，从操作栏中单击&#x200B;**属性**。

1. 导航到&#x200B;**高级**&#x200B;选项卡并检查&#x200B;**设计**&#x200B;字段。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >默认情况下，**设计**&#x200B;字段显示指向libs文件夹中设计的路径。

1. 使用项目文件夹的路径更新&#x200B;**设计**&#x200B;字段。 在这种情况下，它是`/apps/settings/wcm/designs/customstyle`。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 单击&#x200B;**保存并关闭**&#x200B;以更新设计路径。

   >[!IMPORTANT]
   >您可以选择覆盖现有Screens模板，以默认注入您自己的设计或完全创建您自己的模板。 有关更多详细信息，请参阅以下步骤。

1. 要叠加现有Screens模板，以便在默认情况下注入您自己的设计，请执行以下操作：

   1. 在`/apps/screens/core/templates/sequencechannel`中叠加`/libs/screens/core/templates/sequencechannel`。
   1. 修改`/apps/screens/core/templates/sequencechannel/jcr:content`中的&#x200B;*`cq:designPath`*&#x200B;属性，使其指向新设计。

1. 要创建您自己的模板，请执行以下操作：
   1. 将`/libs/screens/core/templates/sequencechannel`复制到`/apps/customstyle/templates/styled-sequencechannel`。
   1. 修改`/apps/customstyle/templates/styled-sequencechannel/jcr:content`中的&#x200B;*`cq:designPath`*&#x200B;属性，使其指向新设计。


### 更新ACL {#updating-acls}

更新这些设计的ACL，以便播放器可以下载。

1. 导航到用户管理员，然后选择`screens-<project>-devices group`并为其授予对自定义设计路径的读取权限。

1. 为此路径提供`screens-<project>-administrators`组读取和修改权限。

## 查看结果 {#viewing-the-result}

完成上述步骤后，您可以从&#x200B;**CRXDE Lite**&#x200B;中更新&#x200B;*statis.css*&#x200B;文件，从而查看已添加到资源的文本覆盖的更新。

请按照以下步骤查看更新后的设计以文本覆盖：

1. 导航到标题为&#x200B;**`customstyle`** > **渠道** > **演示品牌**&#x200B;的AEM Screens项目。 单击频道，然后单击操作栏中的&#x200B;**编辑**。

1. 由于您现在已将设计添加到&#x200B;**设计**&#x200B;字段，如上所述，请单击&#x200B;**预览**&#x200B;以查看带有文本覆盖的图像上的当前样式。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 导航到CRXDE Lite为&#x200B;*static.css*&#x200B;的文件，并将字体（如`font-family: "Lucida Console", Courier, monospace;`）添加到该文件中，如下所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 在保存更改并重新加载预览时，您会看到文本覆盖字体的更新，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，您可以从&#x200B;*static.css*&#x200B;文件中删除最后两个代码块，以删除文本覆盖周围的盒装样式。

![图像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 在预览中查看更新后的更改，其中文本覆盖将添加到图像。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   现在，您可以为添加到资产的文本叠加更新品牌和自定义样式。
