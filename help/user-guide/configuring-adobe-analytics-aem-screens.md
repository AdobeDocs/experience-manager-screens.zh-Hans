---
title: 配置Adobe Analytics与AEM Screens
seo-title: 配置Adobe Analytics与AEM Screens
description: '可查看本节以了解有关使用脱机Adobe Analytics排序和发送自定义事件的更多信息 '
seo-description: '可查看本节以了解有关使用脱机Adobe Analytics排序和发送自定义事件的更多信息 '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 8%

---


# 配置Adobe Analytics与AEM Screens {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>只有安装了AEM 6.4.2功能包2和AEM 6.3.3功能包4，此AEM Screens功能才可用。
>
>要访问这些功能包中的任何一个，您必须联系Adobe支持并请求访问权限。 您获得权限后，就可以从“包共享”下载它。

本节涵盖下列主题：

* **Adobe Analytics与AEM Screens测序**
* **使用脱机发送自定义事件Adobe Analytics**

## Adobe Analytics与AEM Screens测序 {#sequencing-in-adobe-analytics-with-aem-screens}

排序 ***过程开始*** ，数据存储服务激活Adobe Analytics服务。 渠道内容向Adobe Analytics事件发送带工资单，即数据测试捕获到Windows I/O并触发保留事件。 事件被保存到索引数据库中，并进一步被放入对象存储中。 管理员根据计划设置，从对象存储中剪切数据，并在区块存储中进一步传输数据。 连接时，它会尝试发送最大数据量。

### 排序图 {#sequencing-diagram}

以下序列图解释了Adobe Analytics与AEM Screens的整合：

![analytics_chunking](assets/analytics_chunking.png)

## 使用脱机发送自定义事件Adobe Analytics {#sending-custom-events-using-offline-adobe-analytics}

下表总结了事件的标准数据模型。 它列表发送到Adobe Analytics的所有字段：

<table>
 <tbody>
  <tr>
   <td><strong>区域</strong></td> 
   <td><strong>属性标签</strong></td> 
   <td><strong>属性名称／密钥</strong></td> 
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
   <td>时间戳- UTC</td> 
   <td>收集日期时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件日期时间(开始)</td> 
   <td>event.dts_start</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td>时间戳- UTC</td> 
   <td>事件开始日期时间，如果未指定此时间，则事件时间将假定为服务器收到该时间的时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期时间（结束）</td> 
   <td>event.dts_end</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td>时间戳- UTC</td> 
   <td>事件完成日期时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>工作流</td> 
   <td>event.workflow</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>工作流名称（屏幕）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>主DMe类别</td> 
   <td>event.category</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>主类别（桌面、移动、WEB、进程、SDK、服务、生态系统）-事件类型分组——我 <strong>们发送播放器</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子类别</td> 
   <td>event.subcategory</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>子类别-工作流的部分或屏幕的区域等。 （近期文件、CC文件、移动创作等。）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件/操作类型</td> 
   <td>event.type</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件类型（渲染、单击、开合、缩放）-主用户操作</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子类型</td> 
   <td>event.subtype</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件子类型（创建、更新、删除、发布等） -用户操作的其他详细信息</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>脱机</td> 
   <td>event.offline</td> 
   <td>可选</td> 
   <td>布尔型</td> 
   <td> </td> 
   <td>事件在操作脱机／联机时生成(true/false)</td> 
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
   <td>语言／区域设置</td> 
   <td>event.language</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>用户区域设置是基于RFC 3066的语言标记约定（例如，en-US、fr-FR或es-ES）的字符串</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>设备GUID</td> 
   <td>event.device_guid</td> 
   <td>可选</td> 
   <td>字符串<br /> </td> 
   <td>UUID</td> 
   <td>标识设备GUID（例如，计算机ID或IP地址的哈希+子网掩码+网络ID +用户代理）-在此我们将发送注册时生成的播放器的用户名。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>计数</td> 
   <td>event.count</td> 
   <td>可选</td> 
   <td>数字</td> 
   <td> </td> 
   <td>发生事件的次数——在此我们发送视频持续时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>值</td> 
   <td>event.value</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件的值（例如，设置开启／关闭）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>AA要求</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>Adobe Analytics对自定义页面名称的支持</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>Web属性或移动模式的URL —— 必须包含完全限定的URL</td> 
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
   <td>失败说明<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>源／源产品</em></strong></td> 
   <td>名称</td> 
   <td>source.name</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>应用程序名称(AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>版本</td> 
   <td>source.version</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>固件版本</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>平台</td> 
   <td>source.platform</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>设备</td> 
   <td>source.device</td> 
   <td>必需的w/exceptions</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>播放器名称</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>操作系统版本</td> 
   <td>source.os_version</td> 
   <td>必需的w/exceptions</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>O/S版本</td> 
  </tr>
  <tr>
   <td><strong><em>内容</em></strong></td> 
   <td>操作</td> 
   <td>content.action</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>资产的URL，包括实际播放的演绎版</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>MIME类型</td> 
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
   <td>必需</td> 
   <td>字符串</td> 
   <td>UUID</td> 
   <td>优选附于UUID v4的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>产品说明</td> 
   <td>trn.product</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>资产的URL（不包括演绎版）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>数量</td> 
   <td>trn.quantity</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>播放的持续时间</td> 
  </tr>
 </tbody>
</table>

