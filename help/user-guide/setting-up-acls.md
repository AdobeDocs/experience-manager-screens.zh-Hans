---
title: 设置ACL
seo-title: 设置ACL
description: 可查看本页以了解如何使用ACL隔离项目，以便每个个人或团队都能处理他们自己的项目。
seo-description: 可查看本页以了解如何使用ACL隔离项目，以便每个个人或团队都能处理他们自己的项目。
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 设置ACL {#setting-up-acls}

下节介绍如何使用ACL隔离项目，以便每个个人或团队都能处理他们自己的项目。

作为AEM管理员，您需要确保项目的团队成员不会干扰其他项目，并根据项目要求为每个用户分配特定角色。

## 设置权限 {#setting-up-permissions}

以下步骤概括了为项目设置ACL的过程：

1. 登录到AEM，然后导航到工 **具** &gt;安 **全性**。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 单击 **“组** ”并输入ID（例如，Acme）。

   或者，也可使用此链接 `http://localhost:4502/libs/granite/security/content/groupadmin.html`。

   随后，单击“ **保存**”。

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 从列 **表中选择** “参与者”，然后双击它。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 将 **Acme** （您创建的项目）添加 **到“将成员添加到组”**。 单击&#x200B;**保存**。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果您希望项目团队成员注册播放器（包括为每个播放器创建用户），请查找用户组管理员并将ACME组添加到用户管理员

1. 将要处理 **Acme** Project的所有用户添加到 **Acme** 组。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 使用此设置 **Acme** 组的权限 `(http://localhost:4502/useradmin)`。

   选择Acme **组** ，然后单击 **权限**。

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 权限 {#permissions}

下表汇总了具有项目级别权限的路径：

| **路径** | **权限** | **描述** |
|---|---|---|
| `/apps/<project>` | 阅读 | 允许访问项目文件（如果适用） |
| `/content/dam/<project>` | 全部 | 提供在DAM中存储图像或视频等项目资产的权限 |
| `/content/screens/<project>` | 全部 | 删除对/content/screens下所有其他项目的访问权 |
| `/content/screens/svc` | 阅读 | 提供对注册服务的访问 |
| `/libs/screens` | 阅读 | 提供对DCC的访问 |
| `/var/contentsync/content/screens/` | 全部 | 允许更新项目的脱机内容 |

>[!NOTE]
>
>在某些情况下，您可以将创作功能（如管理资产和创建渠道）与管理功能（如注册播放器）分开。 在这种情况下，创建两个用户组，并将作者组添加到参与者，将管理员组添加到参与者和用户管理员。

### 创建组 {#creating-groups}

创建新项目还应创建默认用户组，并分配基本权限集。 您应将权限扩展到我们对AEM Screens具有的典型角色。

例如，您可以创建以下项目特定用户组：

* Screens项目管理员
* Screens项目运营商（注册播放器，并管理位置和设备）
* 屏幕项目用户（处理渠道、计划和渠道分配）

下表汇总了具有AEM Screens项目描述和权限的用户组：

<table>
 <tbody>
  <tr>
   <td><strong>用户组名称</strong></td>
   <td><strong>描述</strong></td>
   <td><strong>权限</strong></td>
  </tr>
  <tr>
   <td>Screens管理员<br /> Screens <em>管理员</em></td>
   <td>对AEM Screens功能的管理员级别访问权限</td>
   <td>
    <ul>
     <li>参与者成员</li>
     <li>用户管理员的成员</li>
     <li>所有/content/screens</li>
     <li>全部/content/dam</li>
     <li>所有/content/experience-fragments</li>
     <li>所有/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>屏幕用户<br /><em>屏幕用户</em></td>
   <td>在AEM Screens中创建和更新渠道和计划并分配到位置</td>
   <td>
    <ul>
     <li>参与者成员</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens操作员<br /> Screens <em>操作员</em></td>
   <td>在AEM Screens中创建和更新位置结构并注册播放器</td>
   <td>
    <ul>
     <li>参与者成员</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens播放器<br /> - <em>we-retail-devices</em></td>
   <td>将所有播放器和所有播放器／设备自动分组为参与者的成员。</td>
   <td><p> 参与者成员</p> </td>
  </tr>
 </tbody>
</table>

