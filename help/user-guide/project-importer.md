---
title: 从文件新建项目导入程序
seo-title: 从文件新建项目导入程序
description: 此功能允许您将一组位置从CSV/XLS电子表格批量导入到AEM Screens项目。
seo-description: 此功能允许您将一组位置从CSV/XLS电子表格批量导入到AEM Screens项目。
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 从文件新建项目导入程序 {#new-project-importer-from-file}

本节介绍将一组位置从CSV/XLS电子表格批量导入到AEM Screens项目的功能。

## 简介 {#introduction}

在您的组织中首次设置AEM Screens项目时，您也需要创建所有位置。 如果您的项目涉及大量位置，则会导致一个繁琐的任务，该任务需要在UI中多次单击并等待。

此功能的目标是缩短设置项目所需的时间，从而解决预算问题。

通过让作者提供一个电子表格作为输入文件，并让系统在后端自动创建位置树，此功能：

* *与通过UI手动单击相比，可以实现更好的性能*
* *允许客户从自己的系统中导出他们拥有的位置，并将它们直接导入AEM*

这既节省了初始项目设置期间或将现有AEM Screens扩展到新位置时的时间和资金。

## 架构概述 {#architectural-overview}

下图显示了项目导入程序功能的架构概述：

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### 数据模型 {#data-model}

项目导入程序的数据模型如下所述：

>[!NOTE]
>
>当前版本仅支持导入位置。

| **属性** | **描述** |
|---|---|
| ***path {string*}** | 位置的资源路径 |
| ***[./jcr:title]{string*}** | 要使用的模板的名称(即屏幕／核心／模 *板／位置的位置*) |
| ***模板{string}*** | 用于页面的可选标题 |
| ***[./jcr:description]{string}*** | 用于页面的可选说明 |

因此，电子表格(CSV/XLS)文件需要以下列：

* **path {string}** the path for the location the imported, where the path root of the project is the location folder for the project( */foo* will imported to */content/screens/&lt;project&gt;/locations/foo*)

* **模板{string}** （用于新位置的模板），目前唯一允许的值是“location”，但此值将扩展到将来的所有Screens模板（“display”、“sequencechannel”等）
* [**./*] {string}**要在该位置（即，）上设置的任何可选属性。/jcr:title, ./jcr:description, ./foo、。/条形图). 当前版本不允许过滤

>[!NOTE]
>
>任何与上述条件不匹配的列将被忽略。 例如，如果工作表(CSV/XLS)文件中定义了 **path**、template **、** title **和********** descriptionImporter文件以外的任何其他列，则这些字段将被忽略，Project Importer将不会验证将项目导入到CSV Screens屏幕的其他字段。

## 使用项目导入程序 {#using-project-importer}

以下部分介绍如何在AEM Screens项目中使用项目导入程序。

>[!CAUTION]
>
>限制:
>
>* 当前版本不支持CSV/XLS/XLSX扩展以外的文件。
>* 对于导入的文件和以“”开头的任何内容，不存在对属性的筛选。/”。
>



### 前提条件 {#prerequisites}

* 创建标题为DemoProjectImport的新项 **目**

* 使用需要导入的示例CSV或Excel文件。

为便于演示，您可以从以下部分下载Excel文件。

[获取文件](assets/minimal-file.xls)

### 导入包含最小必填字段的文件 {#importing-the-file-with-minimum-required-fields}

请按照以下步骤将文件导入位置文件夹，其中包含最少的必填字段：

>[!NOTE]
>
>以下示例展示了导入项目所需的至少四个字段：

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. 导航到您的AEM Screens项目(**DemoProjectImport**)。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. 从侧栏中选择项目，** DemoProjectImporter **—** &gt; **创建—** &gt;导入位置**。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. 此时将 **打开** “导入”向导。 选择您拥有的包含位置的项目文件，或从“入门项目”部分&#x200B;***选择您下载的文件(minimal-file.xls***** )。

   选择文件后，单击“下 **一步”**。

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 从“导入”向导中验证文件（位置）的内容，然后单击“导 **入”**。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. 因此，您现在可以查看导入到项目的所有位置。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

