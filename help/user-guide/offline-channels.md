---
title: 脱机渠道
seo-title: 脱机渠道
description: 'AEM Screens播放器通过利用ContentSync技术为渠道提供离线支持。 可查看本页以了解有关更新处理函数和为渠道启用脱机配置的更多信息。  '
seo-description: 'AEM Screens播放器通过利用ContentSync技术为渠道提供离线支持。 可查看本页以了解有关更新处理函数和为渠道启用脱机配置的更多信息。  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---


# 脱机渠道 {#offline-channels}

Screens播放器通过利用ContentSync技术为渠道提 ***供离线*** 支持。

播放器使用本地http服务器来提供解压缩的内容。

将渠道配置为联 *机运行*&#x200B;时，播放器会通过访问AEM服务器来提供渠道资源，但将渠道配置为脱机运行 *时*，播放器会从本地http服务器提供渠道资源。

该流程的工作流如下：

1. 解析所需页面
1. 收集所有相关资产
1. 将所有内容打包到一个zip文件中
1. 下载zip文件并将其解压缩到本地
1. 显示内容的本地副本

## 更新处理函数 {#update-handlers}

ContentSync ***使用*** 更新处理程序来分析和收集特定项目的所有必要页面和资产。 AEM Screens使用以下更新处理程序：

### 常用选项 {#common-options}

* *类型*: 要使用的更新处理函数类型
* *路径*: 资源路径
* *[targetRootDirectory]*: 目标文件中的文件夹

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
   <td>扩展： 要收集的资源的扩展<br /> [pathSuffix="]: 添加到渠道路径的后缀<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>收集指定的客户端库</td> 
   <td>[扩展="]: 可以是css或js，以仅收集前者，或仅收集后者</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>收集资产演绎版</td> 
   <td>[再现=[]]: 要收集的演绎版列表。 默认为原始演绎版</td> 
  </tr>
  <tr>
   <td>复制</td> 
   <td>从路径复制指定的结构</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### 测试ContentSync配置 {#testing-contentsync-configuration}

请按照以下步骤测试ContentSync配置：

1. 打开 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 在列表中选择配置
1. 单击清除缓存
1. 单击“更新缓存”
1. 单击“下载完整版”
1. 解压zip文件
1. 开始解压缩的文件夹中的本地服务器
1. 打开开始页面并检查应用程序状态

## 为渠道启用脱机配置 {#enabling-offline-config-for-a-channel}

请按照以下步骤为渠道启用脱机配置：

1. 检查渠道内容并检查是否从AEM实例（联机）请求它。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 导航到渠道仪表板，然 **后单击** “渠道 **信息”面** 板中的……以更改属性。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 导航到渠道属性，并确保复选框在渠道选项卡下处 **于禁** 用状态。 Click **Save &amp; Close**.

   ![screen_shot_2017-12-19at122422下午](assets/screen_shot_2017-12-19at122422pm.png)

   在将内容正确部署到设备之前，请单击“更 **新脱机内容”**。

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   “属 **性** ”下的 **“脱机** ”状态也会相应更新。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. 检查渠道内容并检查是否从本地播放器缓存请求它。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>要进一步了解自定义脱机资源处理程序的模板以及特定项目中的 `pom.xml` 最低要求，请参 [阅为AEM Screens开发自](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) 定义组件中的自定义处理 **程序模板**。