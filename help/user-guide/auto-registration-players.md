---
title: 自動註冊播放器
seo-title: Auto Registration of Players
description: 請詳閱本頁面，瞭解如何使用AMS/內部部署畫面自動註冊播放器。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# 自動註冊播放器 {#auto-registration}

手動大量註冊數千個播放器可能會變得非常麻煩，並增加時間和成本。 為簡化此程式，大量註冊功能可讓您在AEM中指定預先共用金鑰，並可透過設定檔案或行動裝置管理(MDM)解決方案將其布建至播放器。

## 實作播放器自動註冊 {#bulk-registering-implementation}

請依照下列步驟實作播放器的自動註冊：

1. 登入您的AEM執行個體並選取您的AEM畫面專案，然後按一下 **屬性** 動作列中的。
1. 選取 **進階** 標籤以檢視 **裝置註冊** 區段。

1. 在中指定自動註冊代碼 **大量註冊代碼** 欄位和選用的預設顯示於 **預設顯示指派** 以指派給自動註冊的播放器。
   >[!NOTE]
   >輸入您選擇的程式碼，並視需要選取預設顯示。

   ![图像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或設定JSON檔案，為播放器布建適當的伺服器URL和註冊代碼。

   >[!NOTE]
   >如需詳細資訊，請參閱作業系統(OS)專用播放器的實作頁面。 您也可以使用管理員UI來輸入註冊代碼。

1. 如果 `registrationKey` 屬性與AEM中設定的屬性相符，播放器會自動註冊，而且如果設定了預設顯示，則會下載並播放該內容。

   ![图像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全性最佳實務 {#security-best-practices}

請參考以下章節，思考一些安全性最佳實務：

* 為確保註冊代碼不被破壞，請在開始大量註冊之前先在AEM中設定代碼，完成後，請清除該欄位並儲存在AEM中。

* 您可以設定路徑 `/bin/screens/registration` ，以儘可能從已知的IP範圍存取。

* 考慮使用MDM以設定布建播放器。

* 永遠使用 `HTTPS` 而非 `HTTP` 用於與AEM的播放器通訊。

   >[!NOTE]
   >預設顯示指定目前僅適用於大量註冊，不適用於沒有註冊代碼的手動註冊。
