---
title: 设置ACL
seo-title: Setting up ACLs
description: 按照本页面了解如何使用ACL分隔项目，以便每个个人或团队处理自己的项目。
seo-description: Follow this page to learn how to segregate projects using ACLs so that each individual or team handles their own project.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 2%

---

# 设置ACL {#setting-up-acls}

以下部分将介绍如何使用ACL分隔项目，以便每个人员或团队处理自己的项目。

作为AEM管理员，您需要确保项目的团队成员不会干预其他项目，并根据项目要求为每个用户分配特定的角色。

## 设置权限 {#setting-up-permissions}

以下步骤概述了为项目设置ACL的过程：

1. 登录到AEM并导航到 **工具** > **安全性**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 单击 **组** 并输入ID（例如，Acme）。

   或者，使用此链接， `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   随后，单击 **保存**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 选择 **参与者** ，然后双击该列表。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 添加 **Acme** （您创建的项目）至 **将成员添加到组**. 单击“**保存**”。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果您希望项目团队成员注册播放器（包括为每个播放器创建用户），请查找组user-administrators并将ACME组添加到user-administrators

1. 添加所有将处理 **Acme** 项目目标 **Acme** 组。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 设置组的权限 **Acme** 使用此 `(http://localhost:4502/useradmin)`.

   选择组 **Acme** 并单击 **权限**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 权限 {#permissions}

下表总结了具有项目级别权限的路径：

| **路径** | **权限** | **描述** |
|---|---|---|
| `/apps/<project>` | 读取 | 提供对项目文件的访问权限（如果适用） |
| `/content/dam/<project>` | 全部 | 提供在DAM中存储图像或视频等项目资产的访问权限 |
| `/content/screens/<project>` | 全部 | 删除对/content/screens下的所有其他项目的访问权限 |
| `/content/screens/svc` | 读取 | 提供对注册服务的访问权限 |
| `/libs/screens` | 读取 | 提供对DCC的访问 |
| `/var/contentsync/content/screens/` | 全部 | 允许更新项目的离线内容 |

>[!NOTE]
>
>在某些情况下，您可以将作者功能（例如管理资产和创建渠道）与管理员功能（例如注册播放器）分开。 在此类场景中，创建两个组并将“作者”组添加到参与者，将“管理员”组添加到参与者和“用户管理员”。

### 创建组 {#creating-groups}

创建新项目时，还应该通过分配的一组基本权限来创建默认用户组。 您应该将权限扩展到我们对AEM Screens拥有的典型角色。

例如，您可以创建以下特定于项目的组：

* 屏幕项目管理员
* 屏幕项目操作员（注册播放器并管理位置和设备）
* 屏幕项目用户（使用渠道、时间表和渠道分配）

下表汇总了对AEM Screens项目具有描述和权限的组：

<table>
 <tbody>
  <tr>
   <td><strong>组名称</strong></td>
   <td><strong>描述</strong></td>
   <td><strong>权限</strong></td>
  </tr>
  <tr>
   <td>Screens管理员<br /> <em>screens-admin</em></td>
   <td>管理员级别的AEM Screens功能访问权限</td>
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
   <td>Screens用户<br /> <em>screens-users</em></td>
   <td>在AEM Screens中创建和更新渠道和计划并分配到位置</td>
   <td>
    <ul>
     <li>撰稿人成员</li>
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
     <li>撰稿人成员</li>
     <li>jcr：all /home/users/screens</li>
     <li>jcr：all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens播放器<br /> <em>屏幕 — &lt;project&gt; — 设备</em></td>
   <td>所有播放器和所有播放器/设备自动成为参与者的成员。</td>
   <td><p> 撰稿人成员</p> </td>
  </tr>
 </tbody>
</table>
