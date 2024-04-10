---
title: 创建和管理时间表
description: 了解可将渠道组织成可重复使用的组的计划，这样您就不必为要显示内容的每个显示分别重复其分配。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 创建和管理时间表 {#creating-and-managing-schedules}

**时间表** 通过AEM Screens中的将渠道组织为可重复使用的组，您不必为要显示内容的每个显示分别重复其分配。

时间表，与组合使用 ***DayParting***，可让您设置一个全局计划，其中多个渠道在一天中的特定时间运行，并重复使用为全部显示设置的设置。

>[!NOTE]
>
>此AEM Screens功能仅在您安装了AEM 6.3 Sites Feature Pack 1时才可用。 要访问此功能包，您必须联系Adobe支持部门并请求获取访问权限。 在获得必要的权限后，您可以从包共享中下载它。

## 创建时间表 {#creating-a-schedule}

您可以为Screens项目创建计划，以便管理用例的所有活动。

请按照以下步骤为您的渠道创建计划：

1. 选择Adobe Experience Manager链接（左上方），然后选择Screens。 或者，您可以直接转到： `http://localhost:4502/screens.html/content/screens`.
1. 导航到屏幕项目并单击 **时间表**.
1. 单击 **创建** 从操作栏中。
1. 选择 **计划** 从 **创建** 向导并单击 **下一个**.

1. 输入 **名称** 和 **标题** 并单击 **创建**.

您可以在项目中看到一个具有指定名称和标题的计划文件夹。


## 查看仪表板 {#viewing-dashboard}

在项目中创建计划文件夹后，可以从计划仪表板查看详细信息。

按照以下步骤查看计划仪表板。 以下示例显示了 `We.Retail` 项目：

1. 导航至 **时间表** 屏幕文件夹(例如， `We.Retail`)项目。

   ![chlimage_1](assets/chlimage_1.png)

1. 选择 **仪表板** 从操作栏中。

   您可以查看三个不同的面板，例如 **时间表信息**， **已分配渠道**、和 **已分配显示区**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **计划信息面板** 单击“计划信息”面板右上角的属性以查看/更改计划的属性。

   **已分配渠道面板** 从“分配的渠道”面板右上角单击+分配渠道，打开“渠道分配”对话框。

   **已分配显示面板** 从“指定的显示”面板中选择任意显示以打开显示仪表板。
