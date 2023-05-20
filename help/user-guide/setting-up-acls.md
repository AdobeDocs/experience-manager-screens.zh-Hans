---
title: 設定ACL
seo-title: Setting up ACLs
description: 請依照本頁面的說明操作，瞭解如何使用ACL區隔專案，讓每個個人或團隊自行處理專案。
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

# 設定ACL {#setting-up-acls}

下節將說明如何使用ACL分隔專案，以便每個個人或團隊處理自己的專案。

作為AEM管理員，您想要確保專案的團隊成員不會干預其他專案，並且每個使用者都會根據專案需求被指派特定角色。

## 設定許可權 {#setting-up-permissions}

下列步驟摘要說明為專案設定ACL的程式：

1. 登入AEM並導覽至 **工具** > **安全性**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 按一下 **群組** 並輸入ID （例如Acme）。

   或者，使用此連結， `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   接著，按一下 **儲存**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 選取 **貢獻者** ，然後按兩下。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 新增 **Acme** （您建立的專案）至 **新增成員至群組**. 单击“**保存**”。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果您希望專案團隊成員註冊播放器（包括為每個播放器建立使用者），請找到群組使用者管理員並將ACME群組新增到使用者管理員

1. 新增所有將處理「 」的使用者 **Acme** 專案至 **Acme** 群組。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 設定群組的許可權 **Acme** 使用此 `(http://localhost:4502/useradmin)`.

   選取群組 **Acme** 並按一下 **許可權**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 权限 {#permissions}

下表總結了具有專案層級許可權的路徑：

| **路径** | **权限** | **描述** |
|---|---|---|
| `/apps/<project>` | 讀取 | 提供專案檔案的存取權（如果適用） |
| `/content/dam/<project>` | 全部 | 提供在DAM中儲存影像或影片等專案資產的存取權 |
| `/content/screens/<project>` | 全部 | 移除/content/screens底下所有其他專案的存取權 |
| `/content/screens/svc` | 讀取 | 提供註冊服務的存取權 |
| `/libs/screens` | 讀取 | 提供DCC的存取權 |
| `/var/contentsync/content/screens/` | 全部 | 允許更新專案的離線內容 |

>[!NOTE]
>
>在某些情況下，您可以將作者功能（例如管理資產和建立管道）與管理功能（例如註冊播放器）分開。 在這種情況下，請建立兩個群組，並將作者群組新增至貢獻者，並將管理員群組新增至貢獻者和使用者管理員。

### 建立群組 {#creating-groups}

建立新專案時，也應建立具有指派基本許可權集的預設使用者群組。 您應該將許可權擴充至我們對AEM Screens所擁有的典型角色。

例如，您可以建立下列專案特定群組：

* 畫面專案管理員
* Screens專案操作員（註冊播放器，以及管理位置和裝置）
* 畫面專案使用者（使用頻道、時程表和頻道指派）

下表概述具有AEM Screens專案說明和許可權的群組：

<table>
 <tbody>
  <tr>
   <td><strong>群組名稱</strong></td>
   <td><strong>描述</strong></td>
   <td><strong>权限</strong></td>
  </tr>
  <tr>
   <td>Screens管理員<br /> <em>screens-admins</em></td>
   <td>管理員層級存取AEM Screens功能</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li>使用者管理員成員</li>
     <li>所有/content/screens</li>
     <li>ALL /content/dam</li>
     <li>所有/content/experience-fragments</li>
     <li>所有/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens使用者<br /> <em>screens-users</em></td>
   <td>建立和更新管道和排程，並指派至AEM Screens中的位置</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens運運算元<br /> <em>screens-operators</em></td>
   <td>在AEM Screens中建立和更新位置結構並註冊播放器</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li>jcr：all /home/users/screens</li>
     <li>jcr：all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens播放器<br /> <em>畫面 — &lt;project&gt; — 裝置</em></td>
   <td>所有播放器及所有播放器/裝置皆為貢獻者自動群組。</td>
   <td><p> 貢獻者成員</p> </td>
  </tr>
 </tbody>
</table>
