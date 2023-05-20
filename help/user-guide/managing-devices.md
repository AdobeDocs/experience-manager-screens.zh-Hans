---
title: 管理裝置
seo-title: Managing Devices
description: 此頁面說明裝置指定任務。
seo-description: Follow this page to learn about device assignment. The Devices console allows you to access the device manager to assign your device to a display.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 管理裝置 {#managing-devices}

此頁面說明裝置指定任務。

「裝置」主控台可讓您存取裝置管理員，以將裝置指派給顯示器。

>[!CAUTION]
>
>指派裝置之前，您必須先註冊該裝置。 如需詳細資訊，請參閱 [裝置註冊](device-registration.md).

## 裝置指派 {#device-assignment}

請依照下列步驟指派裝置給顯示器：

1. 導覽至專案的Devices資料夾，例如

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 選取您的 **裝置** 資料夾並點選/按一下 **裝置管理員** 在動作列中。 已指派和未指派的裝置隨即顯示。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 從清單中選取未指派的裝置，然後點選/按一下 **指派裝置** 在動作列中。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 從清單中選取您要指派裝置的顯示區，然後點選/按一下 **指派**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 點選/按一下 **完成** 以完成指定流程。


   顯示儀表板會在以下位置顯示指派的裝置： **裝置** 面板。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   按一下(**...**)的右上角 **裝置** 面板以新增裝置設定或更新裝置。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次將第一個裝置新增到新的Screens專案時，都會建立使用者群組。
>例如，如果專案節點名稱為 *we-retail*，則使用者群組名稱為 *screens-we-retail-devices*.
>此群組將新增為 **貢獻者** 群組，如下圖所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 后续步骤 {#the-next-steps}

熟悉指定顯示區的管道後，請參閱下列資源：

* [監視和疑難排解](monitoring-screens.md)
