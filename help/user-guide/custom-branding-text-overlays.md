---
title: 为文本叠加应用自定义品牌和样式
seo-title: 为文本叠加应用自定义品牌和样式
description: 可查看本页以了解如何为文本叠加应用自定义品牌和样式。
seo-description: 可查看本页以了解如何为文本叠加应用自定义品牌和样式。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: fdbe57b2cd927c112e9faa4888e3565626712c7a

---


# 文本叠加的自定义品牌和样式 {#creating-custom-branding-styling}

可查看本页以了解如何在Screens渠道中将应用于您的资产的文本叠加的自定义品牌和样式应用。

## 为文本叠加创建自定义品牌和样式 {#steps-custom-branding}

请按照以下步骤为文本叠加创建自定义品牌和样式：

1. 创建AEM Screens项目。 此示例通过创建名为customstyle的项目和标题为 **DemoBrand****** 的渠道来展示该功能，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 从编辑器中拖放图像，并向资产添加文本叠加。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >要了解如何在渠道编辑器中向资产添加文本叠加，请参阅文 [本叠加](/help/user-guide/text-overlay.md)。

1. 从AEM实例—>工具—> **CRXDE Lite导航到CRXDE Lite**。

1. 您必须创建自定义设 `/apps/settings/wcm/designs/<your-project>/`计，例如，在这种情况下，导航到 `/apps/settings/wcm/designs/customstyle/`

   ![图像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 导航到 *static.css文件* ，并设置以下css规则。 另示为css规则下图的示例。

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

1. 将路径复制到您的项目，在这种情况下，该路径将为 `/apps/settings/wcm/designs/customstyle`。

1. 导航到标题为 **DemoBrand** (在第(1)步中创建)的渠道，选择该渠道后，从操作栏中单击 **属性** 。

1. 导航到高 **级选项卡** ，并选中 **设计字段** 。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >默认情况下， **Design** （设计）字段显示指向libs文件夹中设计的路径。

1. 使用项 **目文件夹的路径** ，更新“设计”字段。 在这种情况下，会是， `/apps/settings/wcm/designs/customstyle`

   ![图像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 单击 **保存并关闭** ，以更新设计路径。

### 更新ACL {#updating-acls}

您必须更新这些设计的ACL，以便播放器下载它们。

1. 导航到用户群，选择 `screens-<project>-devices group` 该路径，并为其授予自定义设计路径的读取权限。

1. 提供 `screens-<project>-administrators` 用户组对此路径的读取和修改权限。

## 查看结果 {#viewing-the-result}

完成上述步骤后，您可以从 *CRXDE Lite***** ，更新statis.css文件，然后将更新视图到已添加到资产的文本叠加。

按照以下步骤将更新的设计视图为文本叠加：

1. 导航到标题为customstyle —> **渠道** —> **DemoBrand的AEM Screens** 项目 ****。 Select the channel and click **Edit** from the action bar to open the editor.

1. 由于您现在已如上所述将设计添加到 **“设计** ”字段中，请单击“预览” **** ，在图像上视图当前样式和文本叠加。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 导览至CRXDE *Lite中的static.css* 文件，然后将字体（如）添加到此文件， `font-family: "Lucida Console", Courier, monospace;` 如下所示。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 保存更改并重新加载预览后，您将看到文本叠加字体的更新，如下图所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，您还可以从 *static.css文件中删除最后两个代码块* ，以删除文本叠加周围的盒装样式。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您将在将文本叠加添加到图像的预览中视图更新的更改。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand11.png)

参阅本教程，您现在可以更新添加到资源中的文本叠加的品牌和自定义样式。









