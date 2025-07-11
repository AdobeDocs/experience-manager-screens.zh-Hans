---
title: 使用AEM Screens配置Adobe Analytics
description: 了解有关使用离线Adobe Analytics对自定义事件进行排序和发送的更多信息。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 10%

---

# 使用AEM Screens配置Adobe Analytics {#configuring-adobe-analytics-with-aem-screens}

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.4.2 Feature Pack 2 and AEM 6.3.3 Feature Pack 4.
>
>To get access to either of these Feature Packs, contact Adobe Support and request access. When you have permissions, download it from Package Share. -->

本节涵盖以下主题：

* 使用AEM Screens在Adobe Analytics中排序&#x200B;**&#x200B;**
* **使用离线Adobe Analytics发送自定义事件**

## 使用AEM Screens在Adobe Analytics中排序 {#sequencing-in-adobe-analytics-with-aem-screens}

***排序流程***&#x200B;以激活Adobe Analytics服务的数据存储服务开始。 渠道内容使用工资单发送Adobe Analytics事件，即将数据测试捕获发送到Windows I/O，并触发保持事件。 这些事件被保存到索引DB中，并进一步被放入对象存储中。 它根据管理员设置的计划从对象存储中剪切数据，然后进一步在区块存储中传输这些数据。 连接后，它会尝试发送最大数量的数据。

### 排序图 {#sequencing-diagram}

以下顺序图说明了Adobe Analytics与AEM Screens的集成：

![analytics_chunking](assets/analytics_chunking.png)

## 使用离线Adobe Analytics发送自定义事件 {#sending-custom-events-using-offline-adobe-analytics}

下表总结了事件的标准数据模型。 其中列出了发送到Adobe Analytics的所有字段：

<table>
 <tbody>
  <tr>
   <td><strong>分区</strong></td> 
   <td><strong>属性标签</strong></td> 
   <td><strong>属性名称/键</strong></td> 
   <td><strong>必填</strong></td> 
   <td><strong>数据类型</strong></td> 
   <td><strong>属性类型</strong><br /> </td> 
   <td><strong>描述</strong></td> 
  </tr>
  <tr>
   <td><strong><em>核心/事件</em></strong></td> 
   <td>事件GUID</td> 
   <td>event.guid</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td>UUID</td> 
   <td>标识事件实例的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>收集事件的日期时间</td> 
   <td>event.coll_dts</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>收藏集日期时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期时间（开始）</td> 
   <td>event.dts_start</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>事件开始日期时间，如果未指定此时间，则事件时间将被假定为服务器收到该事件的时间。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期时间（结束）</td> 
   <td>event.dts_end</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>事件完成日期时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>工作流</td> 
   <td>event.workflow</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>工作流名称(Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>主要数据挖掘类别</td> 
   <td>event.category</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>主类别(桌面、移动设备、WEB、进程、SDK、服务、生态系统) — 事件类型分组 — <strong>已发送播放器</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子类别</td> 
   <td>event.subcategory</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>子类别 — 工作流的部分、屏幕的区域等。 （最近使用的文件、CC文件、移动设备创建等。）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件/操作类型</td> 
   <td>event.type</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件类型（渲染、单击、捏合、缩放） — 主用户操作</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子类型</td> 
   <td>event.subtype</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件子类型（创建、更新、删除、发布等） — 用户操作的更多详细信息</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>离线</td> 
   <td>event.offline</td> 
   <td>可选</td> 
   <td>布尔型</td> 
   <td> </td> 
   <td>在操作脱机/联机(true/false)时生成了事件</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>用户代理</td> 
   <td>event.user_agent</td> 
   <td>推荐（Web属性）</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>用户代理</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>语言/区域设置</td> 
   <td>event.language</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>用户区域设置是一个基于RFC 3066的语言标记约定的字符串（例如，en-US、fr-FR或es-ES）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>设备GUID</td> 
   <td>event.device_guid</td> 
   <td>可选</td> 
   <td>字符串<br /> </td> 
   <td>UUID</td> 
   <td>标识设备GUID（例如，计算机ID或IP地址哈希+子网掩码+网络ID +用户代理） — 此处发送注册时生成的播放器用户名。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>计数</td> 
   <td>event.count</td> 
   <td>可选</td> 
   <td>数字</td> 
   <td> </td> 
   <td>事件发生的次数 — 发送视频持续时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>值</td> 
   <td>event.value</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件的值（例如，设置打开/关闭）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>AA必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>Adobe Analytics中支持自定义页面名称</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>Web属性或移动架构的URL — 必须包含完全限定的URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>错误代码</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>字符串</td> 
   <td> </td> 
   <td>失败代码</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>错误类型</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>字符串</td> 
   <td> </td> 
   <td>失败类型</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>错误描述</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>字符串</td> 
   <td> </td> 
   <td>失败描述<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Source/原始产品</em></strong></td> 
   <td>名称</td> 
   <td>source.name</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>应用程序名称(AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>版本</td> 
   <td>source.version</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>固件版本</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Platform</td> 
   <td>source.platform</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>设备</td> 
   <td>source.device</td> 
   <td>必需（包含例外）</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>播放器名称</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>操作系统版本</td> 
   <td>source.os_version</td> 
   <td>必需（包含例外）</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>操作系统版本</td> 
  </tr>
  <tr>
   <td><strong><em>内容</em></strong></td> 
   <td>操作</td> 
   <td>content.action</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>资源（包括已播放的演绎版）的URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Mime 类型</td> 
   <td>content.mimetype</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>内容的MIME类型</td> 
  </tr>
  <tr>
   <td><strong><em>交易</em></strong></td> 
   <td>交易编号</td> 
   <td>trn.number</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td>UUID</td> 
   <td>优选遵守UUID v4的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>产品描述</td> 
   <td>trn.product</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>资产的URL（不包括演绎版）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>数量</td> 
   <td>trn.quantity</td> 
   <td>必填</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>播放持续时间</td> 
  </tr>
 </tbody>
</table>
