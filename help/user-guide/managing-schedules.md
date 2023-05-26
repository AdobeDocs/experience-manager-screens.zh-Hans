---
title: 创建和管理调度
seo-title: Managing Schedules
description: 按照本页了解“计划”，该计划可让您将渠道组织到可重复使用的组中，这样您就不必为要显示内容的每个显示分别重复其分配。
seo-description: Follow this page to learn about Schedules, that lets you organize channels into re-usable groups so that you do not have to repeat their assignment individually for each display on which you want to show your content.
uuid: c05328a0-620a-4597-b7b3-f4433e78d4e9
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 75ed3c42-4be9-42ae-9d76-e0343af81516
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 创建和管理调度 {#creating-and-managing-schedules}

**时间表**&#x200B;在AEM Screens中，您可以将渠道组织到可重复使用的组中，这样您就不必为要显示内容的每个显示分别重复其分配。

与合并时的计划 ***日期分段***，允许您设置一个全局计划，在一天中的特定时间运行多个渠道，并一次为所有显示重复使用该设置。

>[!NOTE]
>
>此AEM Screens功能仅在安装了AEM 6.3 Sites Feature Pack 1时才可用。 要访问此功能包，您必须联系Adobe支持部门并请求获取访问权限。 一旦您拥有权限，就可以从包共享下载它。

## 创建调度 {#creating-a-schedule}

您可以为Screens项目创建一个计划，用于管理用例的所有活动。

请按照以下步骤为您的渠道创建计划：

1. 选择Adobe Experience Manager链接（左上方），然后选择Screens。 或者，您可以直接转到： `http://localhost:4502/screens.html/content/screens`.
1. 导航到屏幕项目并单击 **时间表**.
1. 单击 **创建** 操作栏中的。
1. 选择 **计划** 从 **创建** 向导并单击 **下一个**.

1. 输入 **名称** 和 **标题** 并单击 **创建**.

您将在项目中看到一个具有指定名称和标题的计划文件夹。


## 查看功能板 {#viewing-dashboard}

在项目中创建了计划文件夹后，可以从计划仪表板查看详细信息。

按照以下步骤查看计划仪表板。 以下示例显示了We.Retail项目的仪表板：

1. 导航到 **时间表** 屏幕（例如，We.Retail）项目的文件夹。

   ![chlimage_1](assets/chlimage_1.png)

1. 单击 **仪表板** 从操作栏中打开计划的仪表板。

   您可以查看三个不同的面板，例如 **时间表信息**， **已分配渠道**、和 **已分配显示区**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **“计划信息”面板** 单击“计划信息”面板右上角的属性以查看/更改计划的属性。

   **“分配的渠道”面板** 从“分配的渠道”面板的右上角，单击+分配渠道以打开“渠道分配”对话框。

   **已分配显示面板** 从“指定的显示”面板中选择任意显示以打开显示仪表板。
