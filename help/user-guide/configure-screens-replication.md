---
title: 配置Screens复制代理
description: 了解如何配置Screens复制代理。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
TQID: https://experienceleague.adobe.com/ms01oXXn6BqzkscgjG0o0g1pq-wEawpMy1eel6Uz1uM
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 531
ht-degree: 5%

---

# 配置Screens复制代理 {#configuring-screens-replication-agent}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

以下页面介绍了如何配置Screens复制代理。

## 目标 {#objective}

Screens复制代理负责将命令数据（如&#x200B;*user*、*password*、*rebootSchedule*、*maxNumberOfLogFilesToKeep*&#x200B;以及更多此类值）从发布到创作。 必须配置此代理，以便作者可以显示设备ping。

>[!NOTE]
>要了解有关Screens复制代理的更多信息，请参阅[Screens复制代理和命令](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands)。

如果要完成Screens复制代理的配置，请完成以下两个部分：

1. [启用用户和更新密码](#enable-users)
1. [更新Screens复制代理的设置](#replicate-agent)

## 启用用户和更新密码 {#enable-users}

请按照以下步骤启用用户并更新`screens-receiver-user`的密码：

>[!NOTE]
>出于安全原因，建议避免使用`screens-receiver-user`的管理密码。

1. 导航到您的AEM Author实例。

1. 单击“工具”>“**安全性**”>“**用户**”。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜索 **`screens-receiver-user`**。

1. 单击&#x200B;**`screens-receiver-user`**，然后单击操作栏中的&#x200B;**启用**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 单击&#x200B;**确定**&#x200B;确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   启用该用户后，您会在&#x200B;**状态**&#x200B;字段下看到&#x200B;**`screens-receiver-user`**&#x200B;为&#x200B;**已启用**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 单击&#x200B;**`screens-receiver-user`**，然后单击操作栏中的&#x200B;**属性**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 从&#x200B;**详细信息**&#x200B;选项卡中单击&#x200B;**帐户设置**&#x200B;下的&#x200B;**更改密码**，如下图所示。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 在&#x200B;**更改密码**&#x200B;对话框中输入新密码，然后单击&#x200B;**保存**。

   >[!NOTE]
   >在&#x200B;**您的密码**&#x200B;字段中输入现有的管理员用户密码。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 单击&#x200B;**保存并关闭**。

1. 单击&#x200B;**`screens-receiver-user`**，然后单击操作栏中的&#x200B;**激活**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 单击&#x200B;**确定**&#x200B;确认。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 单击&#x200B;**`screens-receiver-user`**，然后单击操作栏中的&#x200B;**禁用**。

   >[!IMPORTANT]
   > 禁用&#x200B;**`screens-receiver-user`**&#x200B;只会从创作实例中禁用此用户，并且发布实例中的所有用户都保持活动状态。 请勿在操作栏中单击&#x200B;**取消激活**，因为取消激活也会从发布实例中删除用户。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 单击&#x200B;**确定**&#x200B;确认。

## 更新Screens复制代理的设置 {#replicate-agent}

请阅读以下部分，以更新AEM Screens复制代理中的设置：

>[!IMPORTANT]
>在所有现有AEM Screens复制代理上完成以下步骤。

1. 导航到您的AEM实例。
1. 单击“工具”>“**部署”**>“**复制”**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 单击作者上的&#x200B;**代理**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 搜索创作实例上的所有AEM Screens复制代理，然后单击链接，如下图所示。

   >[!NOTE]
   >搜索所有AEM Screens复制代理。 Screens复制代理名称在标题中包含字母&#x200B;**S**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 单击&#x200B;**编辑**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 从&#x200B;**设置**&#x200B;选项卡中选中&#x200B;**已启用**。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 从&#x200B;**代理设置**&#x200B;对话框中导航到&#x200B;**传输**&#x200B;选项卡，并将&#x200B;**用户**&#x200B;更新为&#x200B;**`screens-receiver-user`**，并输入您在[启用用户和更新密码](#enable-users)的步骤(8)中之前设置的相同密码。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 单击&#x200B;**确定**。

1. 完成上述步骤后，单击&#x200B;**测试连接**&#x200B;以验证连接。

   ![图像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果连接验证成功，则表示您已经完成Screens复制代理的配置。
