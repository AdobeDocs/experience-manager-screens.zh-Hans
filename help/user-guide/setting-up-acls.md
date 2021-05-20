---
title: 设置ACL
seo-title: 设置ACL
description: 请阅读本页，了解如何使用ACL分隔项目，以便每个人或团队都能够处理自己的项目。
seo-description: 请阅读本页，了解如何使用ACL分隔项目，以便每个人或团队都能够处理自己的项目。
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: 管理屏幕
role: Administrator
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---

# 设置ACL {#setting-up-acls}

以下部分介绍如何使用ACL分隔项目，以便每个人或团队都能够处理自己的项目。

作为AEM管理员，您需要确保项目的团队成员不会妨碍其他项目，并且每个用户都会根据项目要求分配特定角色。

## 设置权限{#setting-up-permissions}

以下步骤概述了为项目设置ACL的过程：

1. 登录AEM并导航到&#x200B;**工具** > **安全**。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 单击&#x200B;**Groups**&#x200B;并输入ID（例如Acme）。

   或者，使用此链接`http://localhost:4502/libs/granite/security/content/groupadmin.html`。

   随后，单击&#x200B;**Save**。

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 从列表中选择&#x200B;**参与者** ，然后双击该列表。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 将&#x200B;**Acme**（您创建的项目）添加到&#x200B;**将成员添加到组**。 单击&#x200B;**保存**。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果希望项目团队成员注册播放器（包括为每个播放器创建用户），请找到群组用户管理员，并将ACME群组添加到用户管理员

1. 将要在&#x200B;**Acme**&#x200B;项目中工作的所有用户添加到&#x200B;**Acme**&#x200B;组。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 使用此`(http://localhost:4502/useradmin)`设置组&#x200B;**Acme**&#x200B;的权限。

   选择组&#x200B;**Acme**&#x200B;并单击&#x200B;**permissions**。

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 权限 {#permissions}

下表汇总了项目级别具有权限的路径：

| **路径** | **权限** | **描述** |
|---|---|---|
| `/apps/<project>` | 读取 | 提供对项目文件的访问（如果适用） |
| `/content/dam/<project>` | 全部 | 提供在DAM中存储图像或视频等项目资产的访问权限 |
| `/content/screens/<project>` | 全部 | 删除对/content/screens下所有其他项目的访问权限 |
| `/content/screens/svc` | 读取 | 提供对注册服务的访问 |
| `/libs/screens` | 读取 | 提供对DCC的访问 |
| `/var/contentsync/content/screens/` | 全部 | 用于更新项目的离线内容 |

>[!NOTE]
>
>在某些情况下，您可以将创作功能（例如管理资产和创建渠道）与管理功能（例如注册播放器）分开。 在这种情况下，请创建两个组，并将作者组添加到参与者，将管理员组添加到参与者和用户管理员。

### 创建组{#creating-groups}

创建新项目时，还应创建默认用户组，并分配一组基本权限。 您应该将权限扩展到我们拥有的典型AEM Screens角色。

例如，您可以创建以下特定于项目的组：

* Screens项目管理员
* Screens项目运营商（注册播放器，并管理位置和设备）
* 屏幕项目用户（处理渠道、计划和渠道分配）

下表汇总了具有AEM Screens项目说明和权限的组：

<table>
 <tbody>
  <tr>
   <td><strong>群组名称</strong></td>
   <td><strong>描述</strong></td>
   <td><strong>权限</strong></td>
  </tr>
  <tr>
   <td>Screens管理员<br /> <em>screens-admins</em></td>
   <td>对AEM Screens功能的管理员级别访问权限</td>
   <td>
    <ul>
     <li>派遣国成员</li>
     <li>用户管理员成员</li>
     <li>所有/content/screens</li>
     <li>所有/content/dam</li>
     <li>所有/content/experience-fragments</li>
     <li>所有/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens用户<br /> <em>screens-users</em></td>
   <td>创建和更新渠道和计划，并将其分配给AEM Screens中的位置</td>
   <td>
    <ul>
     <li>派遣国成员</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens运算符<br /> <em>screens-operators</em></td>
   <td>在AEM Screens中创建和更新位置结构并注册播放器</td>
   <td>
    <ul>
     <li>派遣国成员</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens播放器<br /> <em>screens-&lt;项目&gt; — 设备</em></td>
   <td>自动将所有播放器和所有播放器/设备分组为参与者的成员。</td>
   <td><p> 撰稿人</p> </td>
  </tr>
 </tbody>
</table>
