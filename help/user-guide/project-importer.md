---
title: 从文件新建项目导入程序
seo-title: New Project Importer from File
description: 此功能允许您将CSV/XLS电子表格中的一组位置批量导入到AEM Screens项目。
seo-description: This functionality allows you to bulk-import a set of locations from a CSV/XLS spreadsheet to your AEM Screens project.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 2%

---

# 从文件新建项目导入程序 {#new-project-importer-from-file}

本节介绍的功能可将一组位置从CSV/XLS电子表格批量导入到您的AEM Screens项目。

## 简介 {#introduction}

在组织中首次设置AEM Screens项目时，还需要创建所有位置。 如果您的项目涉及大量位置，则会导致一项繁琐的任务，即需要在UI中多次单击和等待。

此功能的目标是减少设置项目所需的时间，从而解决预算问题。

通过让作者提供电子表格作为输入文件，并让系统在后端自动创建位置树，此功能：

* *获得比通过UI手动点击更好的性能*
* *允许客户从自己的系统导出其位置，并轻松地直接在AEM中导入这些位置*

在初始项目设置期间或将现有AEM Screens扩展到新位置时，这既节省了时间，又节约了资金。

## 架构概述 {#architectural-overview}

下图显示了项目导入程序功能的架构概述：

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### 数据模型 {#data-model}

项目导入程序的数据模型描述如下：

>[!NOTE]
>
>当前版本仅支持导入位置。

| **属性** | **描述** |
|---|---|
| ***路径{string*}** | 位置的资源路径 |
| ***[。/jcr：title] {string*}** | 要使用的模板的名称(即 *screens/core/templates/location*) |
| ***模板{string}*** | 用于页面的可选标题 |
| ***[。/jcr：description] {string}*** | 用于页面的可选描述 |

因此，电子表格(CSV/XLS)文件需要以下列：

* **路径{string}** 要导入位置的路径，其中路径的根是项目的位置文件夹(即 */foo* 将被导入到 */content/screens/&lt;project>/locations/foo*)

* **模板{string}** 用于新位置的模板，目前唯一允许的值是“location”，但未来这将扩展到所有Screens模板（“display”、“sequencechannel”等）
* **[。/*] {string}** 要在位置上设置的任何可选属性（即）。/jcr:title, ./jcr：description， 。/foo， 。/条形图). 当前版本目前不允许筛选

>[!NOTE]
>
>任何不符合上述条件的列都将被忽略。 例如，如果工作表(CSV/XLS)文件中定义了任何其他列，而不是 **路径**，**模板**，**标题**、和 **描述** 在文件中，这些字段将被忽略，并且 **项目导入程序** 将不会验证这些附加字段，以便将您的项目导入到AEM Screens项目。

## 使用项目导入程序 {#using-project-importer}

以下部分介绍了如何在AEM Screens项目中使用项目导入器。

>[!CAUTION]
>
>限制：
>
>* 当前版本不支持CSV/XLS/XLSX扩展名以外的文件。
>* 对于导入的文件和任何以“”开头的文件，不存在属性过滤。“/”将被导入。
>


### 前提条件 {#prerequisites}

* 创建标题为 **DemoProjectImport**

* 使用需要导入的示例CSV或Excel文件。

出于演示目的，您可以从以下部分下载Excel文件。

[获取文件](assets/minimal-file.xls)

### 导入具有最少必填字段的文件 {#importing-the-file-with-minimum-required-fields}

按照以下步骤将文件导入到具有最少必填字段的“位置”文件夹：

>[!NOTE]
>
>以下示例展示了导入项目所需的最少四个字段：

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. 导航到您的AEM Screens项目(**DemoProjectImport**)。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. 选择项目，**DemoProjectImporter **—>** 创建 **—>** 导入位置**从侧栏中。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. 此 **导入** 向导打开。 选择您项目中具有位置的文件，或选择文件(***最小文件.xls***)从 *先决条件* 部分。

   选择文件后，单击 **下一个**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 从“导入”向导中验证文件的内容（位置），然后单击 **导入**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. 因此，您现在将能够查看导入到项目的所有位置。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
