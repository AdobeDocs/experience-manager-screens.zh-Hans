---
title: 在多區域版面中建立自訂範本
seo-title: Creating Custom Templates in MultiZone Layouts
description: 請依照本頁面瞭解如何在MultiZone配置圖中建立自訂範本。
seo-description: Follow this page to learn about creating custom templates in MultiZone layouts.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 1%

---

# 建立MultiZone配置圖的自訂範本 {#creating-custom-templates-multizone}

本頁面說明如何建立多區域版面的自訂範本。

## 重要注意事项 {#considerations}

以多區域版面配置建立自訂範本之前，您必須注意兩個重要事項：

1. **固定畫素大小或百分比**：

   您必須決定是否要針對自訂配置圖的不同區域使用固定畫素大小，或是要使用百分比建立自訂配置。

   >[!NOTE]
   >使用百分比為您的自訂配置設定區域的好處可讓您在各種熒幕大小上重複使用範本。

1. **命名慣例**：

   在瞭解如何建立要在AEM Screens專案中使用的自訂多區域範本之前，建議您先瞭解要建立的範本的措辭。

   | **版面名稱** | **描述** |
   |---|---|
   | Left20-LandscapeHD3Zone | 請參考3區域的橫向配置，讓您建立3個區域，區域1為水準熒幕與垂直熒幕左側的20%，區域2為水準熒幕與垂直熒幕右側對齊的80%，區域3為水準熒幕的100%，垂直熒幕的80%，外觀比例為16:9 |
   | Upper20-PortraitHD2Zone | 請參考2區縱向範本，從上到上覆蓋熒幕的20%，外觀比例為16:9 |
   | Right20-LandscapeSD3Zone | 指從右側覆蓋20%熒幕的3區域範本，外觀比例為4:3 |

   >[!IMPORTANT]
   >自訂配置中定義的區域可能與整個配置的整體外觀比例不符。 本檔案遵循的命名慣例會指定自訂配置整體外觀比例。

## 使用案例Left20-LandscapeHD3Zone配置範例 {#custom-template-one}

請依照以下章節建立自訂範本 *Left20-LandscapeHD3Zone* 搭配下列設定：

* **Left20** 指左上方的區域，涵蓋水平與垂直熒幕大小的20%。
* **橫向** 參考熒幕方向
* **HD** 是指長寬比為16:9
* **3Zone** 是指顯示的三個區域

## 多區域配置的視覺呈現 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone配置可讓您在專案中建立下列多區域配置：

![图像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 建立Left20-LandscapeHD3Zone配置 {#landscape-layout-one}

請依照下列步驟，為AEM Screens專案建立Left20-LandscapeHD3Zone版面配置：

1. 建立標題為的AEM Screens專案 **customtemplate**.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 導覽至 **CRXDE Lite** 從您的AEM執行個體 — >工具 — > **CRXDE Lite**.

1. 在下建立資料夾 **應用程式** 標題為 **customtemplate**. 同樣地，建立另一個資料夾，標題為 **範本** 在 **customtemplate**，如下圖所示。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >建議您按一下 **全部儲存** 每次建立、編輯內容或複製內容至任何節點時，都會從CRXDE Lite中的動作列執行，否則將無法提交更新。

1. 從以下位置複製左方列範本： `/libs/screens/core/templates/splitscreenchannel/lbar-left` 至 `/apps/customtemplate/template`.

1. 重新命名複製的專案 **左邊欄** (`/apps/customtemplate/template`)至 **my-custom-layout**.
   ![图像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 導覽至 `/apps/customtemplate/template/my-custom-layout` 並更新屬性 **jcr：description** 至 *Left20-LandscapeHD3Zone範本* 和 **jcr：title** 至 *Left20-LandscapeHD3Zone*.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 導覽至 **offline-config** 節點來源 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 並更新 **jcr：title** 至 *Left20-LandscapeHD3Zone*.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 導覽至 *jcr：content* 屬性 **my-custom-template** 從 `/apps/customtemplate/template/my-custom-layout/jcr:content` 並更新 **cq：cssClass** 屬性至 **aem-Layout my-custom-layout**.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 請參考步驟(4)，您複製了lbar左側範本，您將會在下檢視3個回應式格點 `my-custom-layout/jcr:content`. 將自訂css類別新增至 *cq：cssClass* 屬性，例如， *my-custom-layout — 左上方* 的 *r1c1* 節點。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同樣地，新增 *my-custom-layout — 右上方* 的 *r1c2*  和 *my-custom-layout — 底部* 的 *r2c1* 節點。

   >[!NOTE]
   >這些自訂類別將用於在css中設定這些回應式格點的寬度/高度。

   >[!NOTE]
   >您可以根據您想要的格點總數來新增或移除回應式格點。 在此範例中，我們在第一列顯示2個格點，在第二列顯示1個格點，因此共有3個回應式格點(r1c1、r1c2、r2c1)。

1. 複製 `/libs/settings/wcm/designs/screens` 至 `/apps/settings/wcm/designs/` 並將複製的設計重新命名為 **custom-template-designs**.

1. 導覽至 `/apps/settings/wcm/designs/custom-template-designs` 並更新屬性 *jcr：title* 之 **custom-template-designs** 至 **customtemplate-design**.

1. 導覽至 `/apps/settings/wcm/designs/custom-template-designs` 並建立static.css檔案。

1. 將內容複製到 `static.css` 檔案：

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >您可以更新百分比以符合自訂範本的要求。

1. 導覽至 `/apps/<project>/templates/my-custom-layout/jcr:content` 並更新屬性 *cq：designPath* 至 `/apps/settings/wcm/designs/customtemplate-designs` 以載入在static.css中設定的樣式

   >[!NOTE]
   >建議您輸入所有樣式，而非複製或貼上，因為這樣可能會導致空白字元導致css樣式問題。

## 檢視結果 {#viewing-result}

請依照下列步驟，在您的AEM Screens專案中使用上述自訂範本：

1. 導覽至您在步驟(1)中建立的Screens專案，然後選取 **頻道** 資料夾。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 按一下 **建立** 從動作列選取範本 **Left20-LandscapeHD3Zone** 從 **建立** 精靈。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自訂範本建立管道後，您可以從編輯器將資產新增至您的管道。 以下預覽顯示自訂範本中的影像。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 插入影像做為背景圖層  {#inserting-image}

您可以將影像作為背景圖層插入版面：

您可以調整CSS規則，以使用稱為「data-uri」的內容，並直接在您（步驟13）建立的CSS檔案中內嵌影像（Base64編碼）。 *static.css*.

其完成方式如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以遵循下列步驟：

1. 確定影像以某種方式包含在頻道的離線設定中
1. 使用上述CSS中影像的直接連結，而非「data-uri」變體


## 更新背景顏色 {#updating-color}

若要變更背景顏色，請將下列程式碼新增至xml檔案（步驟13）， *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
