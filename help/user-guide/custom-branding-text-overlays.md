---
title: 对文本叠加应用自定义品牌和样式
seo-title: 对文本叠加应用自定义品牌和样式
description: 可查看本页以了解如何为文本叠加应用自定义品牌和样式。
seo-description: 可查看本页以了解如何为文本叠加应用自定义品牌和样式。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 099000dea848810c7ab12a32f0235ca478c0d5dd
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 1%

---


# 文本叠加的自定义品牌和样式{#creating-custom-branding-styling}

可查看本页，了解如何在AEM Screens渠道将应用于您的资源的自定义品牌和文本叠加样式应用到该资源。

## 为文本叠加创建自定义品牌和样式{#steps-custom-branding}

请按照以下步骤为文本叠加创建自定义品牌和样式：

1. 创建AEM Screens项目。 此示例通过创建名为&#x200B;**customstyle**&#x200B;的项目和标题为&#x200B;**DemoBrand**&#x200B;的渠道来展示该功能，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 在编辑器中拖放图像，并向资产添加文本叠加。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >要了解如何在渠道编辑器中向资产添加文本叠加，请参阅[文本叠加](/help/user-guide/text-overlay.md)。

1. 导航到AEM实例中的CRXDE Lite—>工具—> **CRXDE Lite**。

1. 您必须在`/apps/settings/wcm/designs/<your-project>/`中创建自定义设计，例如，在这种情况下，导航到`/apps/settings/wcm/designs/customstyle/`

   ![图像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 创建&#x200B;*static.css*&#x200B;文件并设置以下css规则。 另示为css规则下图的示例。

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

1. 将路径复制到您的项目，在这种情况下，该路径将为`/apps/settings/wcm/designs/customstyle`。

1. 导航到标题为&#x200B;**DemoBrand**(在步骤(1)中创建)的渠道，在选择渠道后，单击操作栏中的&#x200B;**属性**。

1. 导航到&#x200B;**Advanced**&#x200B;选项卡并检查&#x200B;**Design**字段。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >默认情况下，**Design**&#x200B;字段显示指向libs文件夹中设计的路径。

1. 使用项目文件夹的路径更新&#x200B;**Design**&#x200B;字段。 在这种情况下，它将为`/apps/settings/wcm/designs/customstyle`。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 单击&#x200B;**保存并关闭**&#x200B;以更新设计路径。

   >[!IMPORTANT]
   >默认情况下，您可以选择叠加现有的Screens模板以插入您自己的设计或完全创建您自己的模板。 有关更多详细信息，请参阅以下步骤。

1. 要覆盖现有Screens模板以在默认情况下注入您自己的设计，请执行以下操作：

   1. 在`/apps/screens/core/templates/sequencechannel`中叠加`/libs/screens/core/templates/sequencechannel`。
   1. 修改`/apps/screens/core/templates/sequencechannel/jcr:content`中的&#x200B;*cq:designPath*&#x200B;属性以指向新设计。

1. 要完全创建您自己的模板，请执行以下操作：
   1. 将`/libs/screens/core/templates/sequencechannel`复制到`/apps/customstyle/templates/styled-sequencechannel`。
   1. 修改`/apps/customstyle/templates/styled-sequencechannel/jcr:content`中的&#x200B;*cq:designPath*&#x200B;属性以指向新设计。


### 更新ACL {#updating-acls}

您必须更新这些设计的ACL，以便播放器可以下载它们。

1. 导航到用户管理员并选择`screens-<project>-devices group`，并授予它对自定义设计路径的读取权限。

1. 提供`screens-<project>-administrators`组读取和修改此路径的权限。

## 查看结果{#viewing-the-result}

完成上述步骤后，您可以从&#x200B;**CRXDE Lite**&#x200B;更新&#x200B;*statis.css*&#x200B;文件，然后将更新视图到已添加到资产的文本叠加。

按照以下步骤将更新的设计视图为文本叠加：

1. 导航到标题为&#x200B;**customstyle** —> **渠道** —> **DemoBrand**&#x200B;的AEM Screens项目。 选择渠道，然后单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

1. 由于您现在已如上所述将设计添加到&#x200B;**设计**&#x200B;字段，请单击&#x200B;**预览**&#x200B;以使用文本叠加视图图像上的当前样式。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 以CRXDE Lite导航到您的&#x200B;*static.css*&#x200B;文件，并将`font-family: "Lucida Console", Courier, monospace;`等字体添加到此文件，如下所示。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 保存更改并重新加载预览后，您将看到文本叠加字体的更新，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，还可以从&#x200B;*static.css*文件删除最后两个代码块，以删除文本叠加周围的盒装样式。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您将在将文本叠加添加到图像的预览中视图更新的更改。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   现在，您可以更新添加到资源的文本叠加的品牌和自定义样式。









