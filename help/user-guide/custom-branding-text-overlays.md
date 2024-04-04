---
title: 为文本叠加应用自定义品牌和样式
seo-title: Applying Custom Branding and Styling for Text Overlays
description: 关注此页面，了解如何为文本叠加应用自定义品牌和样式。
seo-description: Follow this page to learn how to apply custom branding and styling for Text Overlays.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 1%

---

# 文本叠加图的自定义品牌和样式 {#creating-custom-branding-styling}

关注此页面，了解如何在AEM Screens渠道中为应用于资源的文本叠加应用自定义品牌和样式。

## 为文本叠加图创建自定义品牌和样式 {#steps-custom-branding}

请按照以下步骤为文本叠加创建自定义品牌和样式：

1. 创建一个AEM Screens项目。 此示例通过创建名为的项目来展示功能 **自定义样式** 和一个标题为 **DemoBrand** ，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 从编辑器中，拖放图像并将文本覆盖添加到资源。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >要了解如何在渠道编辑器中向资源添加文本叠加，请参阅 [文本叠加](/help/user-guide/text-overlay.md).

1. 从AEM实例导航到CRXDE Lite>工具> **CRXDE Lite**.

1. 您必须在中创建自定义设计 `/apps/settings/wcm/designs/<your-project>/`例如，在本例中，导航到 `/apps/settings/wcm/designs/customstyle/`

   ![图像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 创建 *static.css* 并设置以下css规则。 另显示为css规则下图的示例。

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

1. 将路径复制到项目，在这种情况下，路径将为 `/apps/settings/wcm/designs/customstyle`.

1. 导航到标题为 **DemoBrand** (在步骤(1)中创建)并单击 **属性** 从操作栏中选择渠道。

1. 导航至 **高级** 制表符并检查 **设计** 字段。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >默认情况下， **设计** 字段显示指向libs文件夹中设计的路径。

1. 更新 **设计** 包含项目文件夹路径的字段。 这种情况下， `/apps/settings/wcm/designs/customstyle`.

   ![图像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 单击 **保存并关闭** 以更新设计路径。

   >[!IMPORTANT]
   >您可以选择覆盖现有Screens模板，以默认注入您自己的设计或完全创建您自己的模板。 有关更多详细信息，请参阅以下步骤。

1. 要叠加现有Screens模板以默认注入您自己的设计，请执行以下操作：

   1. 叠加 `/libs/screens/core/templates/sequencechannel` 在 `/apps/screens/core/templates/sequencechannel`.
   1. 修改 *cq：designPath* 中的属性 `/apps/screens/core/templates/sequencechannel/jcr:content` 指向新的设计。

1. 要创建您自己的模板，请执行以下操作：
   1. 复制 `/libs/screens/core/templates/sequencechannel` 到 `/apps/customstyle/templates/styled-sequencechannel`.
   1. 修改 *cq：designPath* 中的属性 `/apps/customstyle/templates/styled-sequencechannel/jcr:content` 指向新的设计。


### 更新ACL {#updating-acls}

您必须更新这些设计的ACL，以便播放器可以下载它们。

1. 导航到用户管理员，然后选择 `screens-<project>-devices group` 并为其授予对自定义设计路径的读取权限。

1. 提供 `screens-<project>-administrators` 组读取和修改此路径的权限。

## 查看结果 {#viewing-the-result}

完成上述步骤后，您可以更新 *statis.css* 文件来源 **CRXDE Lite** 因此，您可以查看已添加到资产的文本叠加图的更新。

请按照以下步骤查看更新后的设计以文本覆盖：

1. AEM Screens导航到标题为 **自定义样式** > **渠道** > **DemoBrand**. 选择渠道并单击 **编辑** 以打开编辑器。

1. 由于您现在已将该设计添加到 **设计** 字段，如上所述，单击 **预览** 用于查看带文本覆盖的图像上的当前样式。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 导航到 *static.css* 文件，并添加CRXDE Lite，例如 `font-family: "Lucida Console", Courier, monospace;` 添加到此文件，如下所示。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 保存更改并重新加载预览后，您将看到文本覆盖字体的更新，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，您还可以从删除最后两个代码块 *static.css* 文件以移除文本覆盖周围的盒装样式。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您将在预览中查看更新后的更改，其中文本覆盖将添加到图像中。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   现在，您可以为添加到资产的文本叠加更新品牌和自定义样式。
