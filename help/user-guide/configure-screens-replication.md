---
title: 配置Screens复制代理
description: 了解如何配置Screens复制代理。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 4%

---

# 配置Screens复制代理 {#configuring-screens-replication-agent}

以下页面介绍了如何配置Screens复制代理。

## 目标 {#objective}

Screens复制代理负责将命令数据 *用户*， *密码*， *rebootSchedule*， *maxNumberOfLogFilesToKeep*、以及更多此类值（从发布到创作）。 必须对此进行配置，以便作者可以显示设备ping。

>[!NOTE]
>要了解有关Screens复制代理的更多信息，请参阅 [Screens复制代理和命令](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

如果要完成Screens复制代理的配置，请完成以下两个部分：

1. [启用用户和更新密码](#enable-users)
1. [更新Screens复制代理的设置](#replicate-agent)

## 启用用户和更新密码 {#enable-users}

执行以下步骤以启用用户并更新密码 `screens-receiver-user`：

>[!NOTE]
>出于安全原因，建议避免对使用管理员密码 `screens-receiver-user`.

1. 导航到您的AEM创作实例。

1. 选择工具> **安全性** > **用户**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜索 **`screens-receiver-user`**.

1. 选择 **`screens-receiver-user`** 并选择 **启用** 从操作栏中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 选择 **确定** 以确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   启用用户后，您会看到 **`screens-receiver-user`** 作为 **已启用** 在 **状态** 字段。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 选择 **`screens-receiver-user`** 并选择 **属性** 从操作栏中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 选择 **更改密码** 下 **帐户设置** 从 **详细信息** 选项卡，如下图所示。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 在 **更改密码** 对话框并选择 **保存**.

   >[!NOTE]
   >在中输入现有的管理员用户密码 **您的密码** 字段。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 选择&#x200B;**保存并关闭**。

1. 选择 **`screens-receiver-user`** 并选择 **激活** 从操作栏中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 选择 **确定** 以确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 选择 **`screens-receiver-user`** 并选择 **禁用** 从操作栏中。

   >[!IMPORTANT]
   > 正在禁用 **`screens-receiver-user`** 仅从创作实例中禁用此用户，并且发布实例中的所有用户保持活动状态。 不选择 **取消激活** （从操作栏中），因为停用也会将用户从“发布”实例中删除。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 选择 **确定** 以确认。

## 更新Screens复制代理的设置 {#replicate-agent}

请阅读以下部分，以更新AEM Screens复制代理中的设置：

>[!IMPORTANT]
>在所有现有AEM Screens复制代理上完成以下步骤。

1. 导航到您的AEM实例。
1. 选择工具> **部署** > **复制**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 选择 **作者代理**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 搜索创作实例上的所有AEM Screens复制代理，然后选择相应的链接，如下图所示。

   >[!NOTE]
   >搜索所有AEM Screens复制代理。 Screens复制代理名称包含字母 **S** 在标题中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 选择&#x200B;**编辑**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Check **已启用** 从 **设置** 选项卡。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 导航到 **传输** 选项卡 **代理设置** 对话框并更新 **用户** 到 **`screens-receiver-user`** 并输入您在步骤(8)之前设置的相同密码 [启用用户和更新密码](#enable-users).

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 选择 **确定**.

1. 完成上述步骤后，选择 **测试连接** 以验证连接。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果连接验证成功，则表示您已经完成Screens复制代理的配置。
