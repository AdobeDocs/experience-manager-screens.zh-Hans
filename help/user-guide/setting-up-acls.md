---
title: 设置ACL
description: 了解如何使用ACL隔离项目，以便每个个人或团队处理自己的项目。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 2%

---

# 设置ACL {#setting-up-acls}

下节将介绍如何使用ACL隔离项目，以便每个个人或团队处理自己的项目。

作为AEM管理员，您需要确保项目的团队成员不会干预其他项目，并根据项目要求为每个用户分配特定的角色。

## 设置权限 {#setting-up-permissions}

以下步骤概述了为项目设置ACL的过程：

1. 登录AEM并导航至 **工具** > **安全性**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 选择 **组** 并输入ID（例如，Acme）。

   或者，使用此链接， `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   接下来，选择 **保存**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 选择 **参与者** 从列表中并双击它。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 添加 **Acme** （您创建的项目）到 **将成员添加到组**. 选择&#x200B;**保存**。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果您希望项目团队成员注册播放器（包括为每个播放器创建用户），请查找用户管理员组并将ACME组添加到用户管理员

1. 添加所有正在处理的用户 **Acme** 项目目标位置 **Acme** 组。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 设置组的权限 **Acme** 使用此 `(http://localhost:4502/useradmin)`.

   选择组 **Acme** 并选择 **权限**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 权限 {#permissions}

下表汇总了具有项目级别权限的路径：

| **路径** | **权限** | **描述** |
|---|---|---|
| `/apps/<project>` | 读取 | 提供对项目文件的访问权限（如果适用）。 |
| `/content/dam/<project>` | 全部 | 提供在DAM中存储项目资产（如图像或视频）的访问权限。 |
| `/content/screens/<project>` | 全部 | 删除对/content/screens下的所有其他项目的访问权限。 |
| `/content/screens/svc` | 读取 | 提供对注册服务的访问。 |
| `/libs/screens` | 读取 | 提供对DCC的访问权限。 |
| `/var/contentsync/content/screens/` | 全部 | 允许您更新项目的离线内容。 |

>[!NOTE]
>
>有时，您可以将创作功能（例如管理资产和创建渠道）与管理员功能（例如注册播放器）分开。 在此类场景中，创建两个组，并将作者组添加到参与者并将管理员组添加到参与者以及用户管理员。

### 创建组 {#creating-groups}

创建项目时，还应该创建默认用户组，为其分配一组基本权限。 将权限扩展到AEM Screens中定义的典型角色。

例如，您可以创建以下特定于项目的组：

* 屏幕项目管理员
* Screens项目操作员（注册播放器，以及管理位置和设备）
* 屏幕项目用户（处理渠道、时间表和渠道分配）

下表汇总了对AEM Screens项目具有描述和权限的组：

<table>
 <tbody>
  <tr>
   <td><strong>群组名称</strong></td>
   <td><strong>描述</strong></td>
   <td><strong>权限</strong></td>
  </tr>
  <tr>
   <td>Screens管理员<br /> <em><code>screens-admins</code></em></td>
   <td>对AEM Screens功能的管理员级别访问权限</td>
   <td>
    <ul>
     <li>撰稿人成员</li>
     <li>用户管理员成员</li>
     <li>所有/content/screens</li>
     <li>ALL /content/dam</li>
     <li>所有/content/experience-fragments</li>
     <li>所有/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens用户<br /> <em><code>screens-users</code></em></td>
   <td>在AEM Screens中创建和更新渠道和计划并分配给位置</td>
   <td>
    <ul>
     <li>撰稿人成员</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens运算符<br /> <em><code>screens-operators</code></em></td>
   <td>在AEM Screens中创建和更新位置结构并注册播放器</td>
   <td>
    <ul>
     <li>撰稿人成员</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens播放器<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>将所有播放器和所有播放器/设备自动分组为参与者。</td>
   <td><p> 撰稿人成员</p> </td>
  </tr>
 </tbody>
</table>
