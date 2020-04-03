---
title: 为文本叠加应用自定义品牌和样式
seo-title: 为文本叠加应用自定义品牌和样式
description: 可查看本页以了解如何为文本叠加应用自定义品牌和样式。
seo-description: 可查看本页以了解如何为文本叠加应用自定义品牌和样式。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# 文本叠加的自定义品牌和样式 {#creating-custom-branding-styling}

可查看本页以了解如何为文本叠加应用自定义品牌和样式。

## 为文本叠加创建自定义品牌和样式 {#steps-custom-branding}

请按照以下步骤为文本叠加创建自定义品牌和样式：

1. 创建标题为Customstyle的AEM Screens项目 **和标题为****** DemoBrand的渠道，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 从编辑器中拖放图像，并向资产添加文本叠加。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >要了解如何在渠道编辑器中向资产添加文本叠加，请参阅文 [本叠加](/help/user-guide/text-overlay.md)。

1. 从AEM实例—>工具—> **CRXDE Lite导航到CRXDE Lite**。

1. 例如，您必须在本例中 `/apps/settings/wcm/designs/<your-project>/`创建自定义设计

   ![图像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 导航到static.css文件并设置以下css规则。 如下图所示。

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![图像](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. 将路径复制到您的项目，在这种情况下，该路径将为 `/apps/settings/wcm/designs/customstyle`。

1. 导航到标题为 **DemoBrand** (在步骤(1)中创建)的渠道，选择渠道后，从操作栏中单击 **属性** 。

1. 导航到高 **级选项卡** ，并选中 **设计字段** 。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >默认情况下， **Design** （设计）字段显示指向libs文件夹中设计的路径。

1. 使用项 **目文件夹的路径** ，更新“设计”字段。 在这种情况下，会是， `/apps/settings/wcm/designs/customstyle`

   ![图像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 单击 **保存并关闭** ，以更新设计路径。


## 查看结果 {#viewing-the-result}

完成上述步骤后，您可以从 *CRXDE Lite***** ，更新statis.css文件，然后将更新视图到添加到资产的文本布局。

请按照以下步骤将更新的设计视图为文本布局：

1. 导航到标题为Customstyle的AEM Screens项目和标题为 **DemoBrand的渠道** ，然后单击操作栏中 **的编辑****** ，以打开编辑器。

1. 由于您现在已如上所述将设计添加到 **“设计** ”字段中，请单击“预览” **** ，在图像上视图当前样式和文本叠加。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 导览至CRXDE Lite中的static.css文件，例如，添加字体。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 保存更改并重新加载预览后，您将看到文本叠加字体的更新，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，您还可以从static.css文件中删除最后两个代码块，以删除文本叠加周围的盒装样式。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您将视图预览中更新后的更改，在该更改中，文本叠加将添加到图像，如下所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand11.png)

因此，按照前面几节中的步骤，您可以更新添加到资源的文本叠加的品牌和自定义样式。









