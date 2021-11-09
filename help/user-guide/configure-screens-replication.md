---
title: 配置Screens复制代理
description: 请阅读本页以获取有关如何配置Screens复制代理的信息。
role: Developer
level: Intermediate
source-git-commit: 75250cf11254499dbb30b3a5b04b1849753ea266
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 6%

---


# 配置Screens复制代理 {#configuring-screens-replication-agent}

本节介绍如何配置Screens复制代理。

## 启用用户和更新密码 {#enable-users}

应遵循以下步骤：

1. 导航到您的AEM实例。

1. 单击工具 — > **安全性** —> **用户**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜索 **screens-receiver-user**.

1. 选择 **screens-receiver-user** 单击 **启用** 中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 单击 **确定** 确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   启用用户后，您将看到 **screens-receiver-user** as **已启用** 下 **状态** 字段。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 选择 **screens-receiver-user** 单击 **属性** 中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 单击 **更改密码** 在 **帐户设置** 从 **详细信息** 选项卡，如下图所示。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 在 **更改密码** 对话框，单击 **保存**.

   >[!NOTE]
   >您应输入 **管理员** in **您的密码** 字段。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 单击 **保存并关闭**.

1. 选择 **screens-receiver-user** 单击 **激活** 中。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 单击 **确定** 确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 选择 **screens-receiver-user** 单击 **禁用** 中。

   >[!IMPORTANT]
   > 禁用 **screens-receiver-user** 仅禁用此用户在创作实例中的权限，并且发布实例中的所有用户仍保持活动状态。 请勿单击 **停用** 在操作栏中，由于取消激活将也会从发布实例中删除用户。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 单击 **确定** 确认。

## 更新Screens复制代理 {#replicate-agent}

请按照以下部分更新Screens复制代理中的设置：

1. 导航到您的AEM实例。

1. 单击工具 — > **部署** —> **复制**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 单击 **作者代理**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 单击链接，如下图所示。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 单击 **编辑**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 检查 **已启用** 从 **设置** 选项卡。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 导航到 **运输** 选项卡 **代理设置** ，并输入您在步骤(8)中之前设置的相同密码 [启用用户和更新密码](#enable-users). 单击 **确定**.

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. 完成上述步骤后，您可以单击 **测试连接** 来验证连接。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果连接验证成功，则表示您已完成Screens复制代理的配置。