---
title: 配置Screens复制代理
description: 按照本页获取有关如何配置Screens复制代理的信息。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: 93bbffa2d752bfbd92702487802d40e7e8e287b8
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---

# 配置Screens复制代理 {#configuring-screens-replication-agent}

以下页面介绍了如何配置Screens复制代理。

## 目标 {#objective}

Screens复制代理负责将命令数据 *用户*， *密码*， *rebootSchedule*， *maxNumberOfLogFilesToKeep*、以及更多此类值（从发布到创作）。 必须对此进行配置，以便作者可以显示设备ping。

>[!NOTE]
>要了解有关Screens复制代理的更多信息，请参阅 [Screens复制代理和命令](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

必须完成以下两个部分才能完成Screens复制代理的配置：

1. [启用用户和更新密码](#enable-users)
1. [正在更新Screens复制代理的设置](#replicate-agent)

## 启用用户和更新密码 {#enable-users}

按照以下步骤启用用户并更新screens-receiver-user的密码：

>[!NOTE]
>出于安全原因，建议避免使用screens-receiver-user的管理密码。

1. 导航到您的AEM创作实例。

1. 单击工具 — > **安全性** —> **用户**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜索 **screens-receiver-user**.

1. 选择 **screens-receiver-user** 并单击 **启用** 操作栏中的。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 单击 **确定** 以确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   启用用户后，您将看到 **screens-receiver-user** 作为 **已启用** 在 **状态** 字段。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 选择 **screens-receiver-user** 并单击 **属性** 操作栏中的。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 单击 **更改密码** 下 **帐户设置** 从 **详细信息** 选项卡，如下图所示。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 在 **更改密码** 对话框，然后单击 **保存**.

   >[!NOTE]
   >您应在中输入现有的管理员用户密码 **您的密码** 字段。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 单击 **保存并关闭**.

1. 选择 **screens-receiver-user** 并单击 **激活** 操作栏中的。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 单击 **确定** 以确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 选择 **screens-receiver-user** 并单击 **禁用** 操作栏中的。

   >[!IMPORTANT]
   > 正在禁用 **screens-receiver-user** 仅从创作实例中禁用此用户，并且发布实例中的所有用户仍保持活动状态。 请勿单击 **取消激活** ，因为停用也会将用户从发布实例中删除。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 单击 **确定** 以确认。

## 正在更新Screens复制代理的设置 {#replicate-agent}

请阅读以下章节，以更新Screens复制代理中的设置：

>[!IMPORTANT]
>必须在所有现有Screens复制代理上完成以下步骤。

1. 导航到您的AEM实例。

1. 单击工具 — > **部署** —> **复制**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 单击 **作者代理**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 搜索作者身上的所有Screens复制代理，然后单击链接，如下图所示。

   >[!NOTE]
   >搜索所有Screens复制代理。 Screens复制代理名称将包含字母 **S** 在标题中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 单击 **编辑**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Check **已启用** 从 **设置** 选项卡。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 导航到 **传输** 选项卡 **代理设置** 对话框并更新 **用户** 到 **screens-receiver-user** 并输入之前在的步骤(8)中设置的相同密码 [启用用户和更新密码](#enable-users).

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 单击 **确定**.

1. 完成上述步骤后，您可以单击 **测试连接** 以验证连接。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果连接验证成功，则表示您已完成Screens复制代理的配置。
