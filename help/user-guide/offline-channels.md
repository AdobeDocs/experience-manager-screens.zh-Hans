---
title: 离线渠道
seo-title: 离线渠道
description: 'AEM Screens播放器通过利用ContentSync技术为渠道提供离线支持。 可查看本页以了解有关更新处理程序和启用渠道离线配置的更多信息。  '
seo-description: 'AEM Screens播放器通过利用ContentSync技术为渠道提供离线支持。 可查看本页以了解有关更新处理程序和启用渠道离线配置的更多信息。  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: 开发屏幕
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 1%

---


# 脱机渠道{#offline-channels}

Screens播放器利用&#x200B;***ContentSync***&#x200B;技术为渠道提供离线支持。

播放器使用本地http服务器来提供解压缩的内容。

当通道配置为运行&#x200B;*online*&#x200B;时，播放器通过访问AEM服务器来提供渠道资源，但当该通道配置为运行&#x200B;*offline*&#x200B;时，播放器会从本地http服务器提供渠道资源。

该流程的工作流如下所示：

1. 解析所需的页面
1. 收集所有相关资产
1. 将所有内容打包到zip文件中
1. 下载zip文件并将其解压缩到本地
1. 显示内容的本地副本

## 更新处理程序{#update-handlers}

***ContentSync***&#x200B;使用更新处理程序来解析和收集特定项目的所有必需页面和资产。 AEM Screens使用以下更新处理程序：

### 常用选项{#common-options}

* *类型*:要使用的更新处理程序类型
* *路径*:资源路径
* *[targetRootDirectory]*:zip文件中的target文件夹

<table>
 <tbody>
  <tr>
   <td><strong>类型</strong></td> 
   <td><strong>描述</strong></td> 
   <td><strong>选项</strong></td> 
  </tr>
  <tr>
   <td>渠道</td> 
   <td>收集渠道</td> 
   <td>扩展：用于收集<br /> [pathSuffix="]的资源扩展：添加到渠道路径的后缀<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>收集指定的客户端库</td> 
   <td>[extension="]:可以是css或js，以仅收集前者，或仅收集后者</td> 
  </tr>
  <tr>
   <td>assetrentions</td> 
   <td>收集资产演绎版</td> 
   <td>[演绎版=[]]:要收集的演绎版列表。 默认为原始演绎版</td> 
  </tr>
  <tr>
   <td>复制</td> 
   <td>从路径复制指定的结构</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### 测试ContentSync配置{#testing-contentsync-configuration}

请按照以下步骤测试ContentSync配置：

1. 打开 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 在列表中选择您的配置
1. 单击清除缓存
1. 单击Update Cache
1. 单击Download Full
1. 解压缩zip文件
1. 在提取的文件夹中启动本地服务器
1. 打开开始页面并检查应用程序状态

## 为渠道{#enabling-offline-config-for-a-channel}启用离线配置

请按照以下步骤为渠道启用离线配置：

1. Inspect渠道内容，并检查是否从AEM实例（在线）请求渠道内容。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 导航到渠道功能板，然后单击&#x200B;**...**&#x200B;渠道信息&#x200B;**面板中的**&#x200B;以更改属性。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 导航到渠道属性，并确保在&#x200B;**Channel**&#x200B;选项卡下禁用该复选框。 单击&#x200B;**保存并关闭**。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   在将内容正确部署到设备之前，请单击&#x200B;**更新离线内容**。

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   在&#x200B;**PROPERTIES**&#x200B;下的&#x200B;**Offline**&#x200B;状态也会相应地更新。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect渠道内容，并检查是否从本地播放器缓存中请求。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>要详细了解自定义离线资源处理程序的模板以及该特定项目`pom.xml`中的最低要求，请参阅&#x200B;**为AEM Screens开发自定义组件**&#x200B;中的[自定义处理程序的模板](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)。