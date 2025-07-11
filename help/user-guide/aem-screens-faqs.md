---
title: AEM Screens常见问题解答
description: 阅读与AEM Screens项目相关的常见问题解答。
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 0%

---

# AEM Screens常见问题解答 {#aem-screens-faqs}

本主题提供了与AEM Screens项目相关的常见问题解答。

## 空白屏幕问题 {#blank-screen}

>[!NOTE]
>列出的强制检查在引发问题之前是否应该尝试主要支持或客户端支持。

### 1.对于面对黑屏或未播放内容的客户，应该采取哪些急救故障排除步骤？ {#troubleshooting-blank-screen}

* 检查渠道预览是否有效。
* 检查显示预览是否有效
* 尝试将播放器注册为系统上的浏览器扩展，以使其使用该显示屏，并检查其是否正常工作。
* 在系统上运行播放器后，导航到`http://localhost:24502`。 检查是否正确下载了所有内容。
* 检查资源，以便您可以确保已创建相应的演绎版并且正在播放正确的演绎版。
* 检查任何计划内容以及时间是否正确。 检查播放器中设置的时间是否正确。
* 检查播放器控制台日志，并检查任何错误。 右键单击并检查以查看控制台日志。 如果您使用的是Windows Player，请按`CTRL + ALT +I`启动开发控制台以查看日志。

### 2.如何通过创建默认渠道或计划来解决AEM Screens中的灰屏问题？

要避免出现字段中的空白或灰色屏幕，请创建一个默认全局渠道或计划，将其分配给优先级最低的每个显示器1。 如果内容更新出现问题，因为播放器已在磁盘上缓存此内容。 它应该可以正常播放，避免出现灰色屏幕。

所有其他内容（例如渠道或计划）的优先级大于1，因此其他内容具有优先级，并且全局渠道或计划内容（优先级为1）仅作为回退选项播放。

## 渠道管理 {#channel-management}

### 1.在线渠道和离线渠道有何区别？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

***联机频道***&#x200B;显示实时环境中的更新内容，而&#x200B;***脱机频道***&#x200B;显示缓存的内容。

### 2.如何在线创建频道？ {#how-do-i-make-a-channel-online}

单击渠道，然后从操作栏导航到渠道属性。 检查&#x200B;**频道**&#x200B;选项卡下的&#x200B;**开发人员模式（强制频道联机）**&#x200B;以使频道联机。

### &#x200B;3. “渠道角色”字段有什么用处？ {#what-is-the-use-of-the-channel-role-field}

渠道角色是实际运行的渠道的抽象，以便作者可以直接关注一般体验。 您可以将其视为一种标记，用于唯一标识上下文中的渠道（显示或计划）。

### 4.如何解决实际渠道问题？ {#how-does-actual-channel-resolution-happen}

对于&#x200B;*静态引用*，分辨率仅遵循指定的路径。

对于&#x200B;*动态引用*，将渠道分配给显示区（而非计划）后，就会进行分辨率。 显示路径将成为渠道的上下文，分辨率如下所示（优先级从高到低）：

1. 显示内容有一个与引用的渠道名称匹配的子节点
1. 该显示区有一个与引用的渠道名称匹配的同级节点
1. 显示的父位置有一个与引用的渠道名称匹配的子节点
1. 显示器的父级位置有一个与引用的渠道名称匹配的子节点

等等，直到您访问位置文件夹。 此时在此处停止（以便不能引用位于渠道文件夹中的渠道，例如，仅引用位置子树中的渠道）。

### 5.如何在AEM Screens渠道中设置自定义clientlib离线配置？

在AEM Screens渠道中使用内置的自定义客户端代码`clientlib`时，需要执行以下步骤。 这些步骤确保`clientlib`文件在通道(`manifest.json`)中成功加载并包含`clientlib`的路径。

在渠道编辑器中执行以下步骤：

1. 单击渠道，然后单击操作栏中的&#x200B;**编辑**。
1. 单击要添加自定义`clientlib`的组件。
1. 单击配置按钮（扳手图标）。
1. 导航到&#x200B;**脱机配置**&#x200B;选项卡，并在&#x200B;**客户端库**&#x200B;中添加自定义clientlib的路径。

## 设备注册 {#device-registration}

### 1.如果发现端点（如设备载入和注册请求），则可以编写许多设备的脚本并注册这些设备。 除了将其锁定在分支Wi-Fi上之外，是否可以保护这些请求？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

当前只能在创作实例上注册。 尽管注册服务未经身份验证，但它仅在AEM中创建待处理的设备，而不会实际注册设备或分配任何显示。

要注册设备(在AEM中为设备创建用户)，请向AEM进行身份验证并手动按照注册向导完成注册。 理论上，恶意用户可能会创建多个挂起的设备，但如果没有AEM登录信息，则无法注册任何设备。

### 2.是否可以通过某种形式的身份验证将HTTP GET请求转换为HTTP POST？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

注册请求是POST请求。

建议从会话中获取设备ID，而不是将其作为参数传递。 这样做会清理服务器日志、浏览器缓存等。 这不是安全问题。 语义上。 当服务器上没有状态更改时使用GET，而状态更改时使用POST。

### 3.是否可以拒绝设备注册请求？ {#is-there-a-way-to-decline-a-device-registration-request}

您不能拒绝注册请求。 相反，注册请求应在`Adobe Experience Manager Web Console`中配置的超时后过期。 默认情况下，此值设置为一天，并存储在内存缓存中。

## 设备监控和运行状况报告 {#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens Player显示空白屏幕，如何进行故障排除？

检查以下是否可能解决空白屏幕问题：

* AEM无法推送离线内容
* 渠道没有任何内容
* 没有任何资源被安排在当前时间显示

### 2.如果AEM Screens Player无法注册且其状态显示为“失败”，我该怎么做？

启用Apache Sling引用过滤器允许为空。 在AEM Screens Player和AEM Screens服务器之间优化控制协议操作所需。

1. 导航到&#x200B;**Adobe Experience Manager Web控制台配置**
1. 选中&#x200B;**allow.empty**&#x200B;选项。
1. 单击&#x200B;**保存**。

### 3.如果在注册AEM Screens Player时，设备显示“失败”，且控制台日志显示“ENAME_NOT_FOUND”错误，如何进行故障排除？

如果播放器无法找到AEM Screens服务器DNS，则可能会发生此问题。 您可以尝试使用IP地址进行连接。 要获取服务器的IP，请使用： *arp &lt;server_dns_name>*。

### &#x200B;4. AMS是否建议在所有设备上实施Android™ Watchdog？ Watchdog (Cordova)插件是否包含在APK中？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用纯Android™ API的跨平台Android™监视程序已是apk的一部分。 无需其他软件。 但是，根据您使用的设备，您可以退出apk以获得完整电源周期(`Powermanager` api)的系统权限（如有必要）。 如果使用制造商密钥没有放弃，它会退出并重新启动应用程序，但不会重新启动电源。

有关如何实施Android™ Player的更多信息，请参阅&#x200B;[**实施Android™ Player**](implementing-android-player.md)。

### &#x200B;5. Adobe/AMS建议使用哪些第三方远程监控和警报工具（软件）来监控每台设备？ {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根据您希望在监视和警报中显示的内容，如果设备一段时间未发出信号，AEM Screens Notifications服务会向您发送通知。 第三方工具取决于您的操作系统(OS)、其功能以及客户的特定需求。

有关可在何处监视设备活动的详细信息，请参阅&#x200B;[**AEM屏幕通知服务**](screens-notifications-service.md)。

## AEM Screens 播放器

### 1.如何将ChromeOS播放器安装为Chrome浏览器插件？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

在开发人员模式下，ChromeOS播放器可作为Chrome浏览器插件安装，而无需实际的Chrome Player设备。 要安装，请执行以下步骤：

1. 单击[此处](https://download.macromedia.com/screens/)下载最新的Chrome播放器。
1. 解压缩并将其保存在磁盘上。
1. 打开Chrome浏览器，然后单击菜单中的&#x200B;**扩展**，或直接导航到&#x200B;***chrome://extensions***。
1. 从右上角打开&#x200B;**开发人员模式**。
1. 从左上角单击&#x200B;**加载解压缩**，然后加载解压缩的Chrome Player。
1. 如果扩展列表中存在，请检查&#x200B;**AEM Screens Chrome Player**&#x200B;插件。
1. 打开新选项卡并单击左上角的&#x200B;**应用程序**&#x200B;图标，或直接导航到&#x200B;***chrome://apps***。
1. 单击&#x200B;**AEM Screens**&#x200B;插件。 默认情况下，播放器将以全屏模式启动。 按&#x200B;**Esc**&#x200B;退出全屏模式。

### 2.如果Screens Player无法使用自定义错误处理程序通过发布实例进行身份验证，如何进行故障排除？

AEM Screens Player启动时，会在播放器收到404错误时向&#x200B;***/content/screens/svc.ping.json***&#x200B;发出请求。 播放器发起身份验证请求，以针对发布实例进行身份验证。 如果发布实例中存在自定义错误处理程序，请确保在&#x200B;***/content/screens/svc.ping.json***&#x200B;上返回匿名用户的404状态代码。

### 3.如何在Android™ Player中设置设备屏幕？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

执行以下步骤，在任何Android™播放器上启用“保持唤醒”：

1. 导航到Android™播放器设置> **关于**。
1. 点按内部版本号七次，以便在&#x200B;**设置**&#x200B;中启用&#x200B;**开发人员选项**。
1. 导航到&#x200B;**开发人员选项**。
1. 启用&#x200B;**保持清醒**。

### 4.如何为Windows Player启用窗口模式？{#enable-player}

Windows Player中没有窗口模式。 它始终处于全屏模式。

### 5.如果AEM Screens Player持续发送登录请求，如何进行故障排除？

请按照以下步骤对持续向`/content/screens/svc.json`和`/libs/granite/core/content/login.validate/j_security_check`发送请求的AEM Screens Player进行故障排除：

1. AEM Screens Player启动时，会向`/content/screens/svc.json`发出请求。 当播放器在响应中获得404状态代码时，它将对&#x200B;*发布*&#x200B;实例使用`/libs/granite/core/content/login.validate/j_security_check`来启动身份验证请求。 如果&#x200B;*发布*&#x200B;实例中存在自定义错误处理程序，请确保在`/content/screens/svc.json`或`/content/screens/svc.ping.json`上返回匿名用户的404状态代码。

1. 检查您的Dispatcher配置是否允许在`/filters`中处理这些请求。

   有关详细信息，请参阅[配置Screens筛选器](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters)。

1. 检查您的Dispatcher重写规则是否正在将任何屏幕路径重写为其他路径。

1. 检查您在&#x200B;*作者*&#x200B;或&#x200B;*发布*&#x200B;实例上是否有`/etc/map`规则，并且Screens路径与`sling:match`匹配并在内部重定向到其他路径。 解析`/system/console/jcrresolver`中的确切URL有助于识别&#x200B;*发布*&#x200B;实例是否正在将这些URL重写为任何其他路径。

1. 检查Apache Sling Resource Resolver Factory配置是否导致内部重写。

### 6.如何从播放器API获取显示器和设备的详细信息？

您可以通过以下方式获取显示器和设备的详细信息：

* **内部JS API**
* **ContextHub存储**：在`/libs/screens/clientlibs/contexthub`中定义了三个ContextHub存储，以公开渠道、设备和显示信息。

  请按照以下步骤使用这些ContentHub存储值：

   * 编辑渠道属性并将“个性化”选项卡中的ContextHub路径设置为值（如上所述）
   * 在渠道JS中，您可以使用：

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## 一般疑难解答提示 {#general-troubleshooting-tips}

### 1.如何禁用Livefyre以避免A/P Screens错误？

通过执行以下操作，禁用Livefyre以避免日志错误。

1. ***禁用Livefyre包：***

   * 导航到 `https://<host>:<port>/system/console/bundles`。
   * 搜索AEM Livefyre捆绑包： `com.adobe.cq.social.cq-social-livefyre`。
   * 单击&#x200B;**停止**。

1. ***禁用Livefyre轮询程序：***

   * 在CRXDE Lite中，导航到`/etc/importers/polling/livefyre-poller/jcr:content`。
   * 添加属性&#x200B;*已启用*&#x200B;类型&#x200B;*布尔值*。
   * 将&#x200B;**启用属性**&#x200B;设置为&#x200B;**false**。

### 2.如何添加Oak索引信息？ {#add-oak-index-info}

AEM Screens为产品使用的查询创建索引定义。
如果`error.log`中有任何&#x200B;*查询遍历WARN*，请为您的查询创建自定义索引。 有关详细信息，请参阅[配置索引](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes)。

您还可以在[Oak文档](https://jackrabbit.apache.org/oak/docs/query/lucene.html)上看到其他资源。


### 3.配置v3清单需要什么？ {#configure-v3}

要启用v3清单，请执行以下操作：

* 更新Dispatcher。
有关更多详细信息，请参阅[为清单版本v3](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)配置Dispatcher 。

* 更新自定义组件。
有关详细信息，请参阅[自定义处理程序模板](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)。

* 在`/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`中禁用ContentSync。

* 在`/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`中启用SmartSync。

* 编辑`channel/experience fragment/page components`。

* 导航到&#x200B;**脱机配置**&#x200B;选项卡。

* 为必须添加到清单中的静态文件输入`clientlibs `和文件夹。

### 4.如果在软件包screens-cloud-ams-pkg-0.0.20、screens-cloud-ams-pkg-0.0.16和screens核心包已安装但未处于活动状态，您应该怎么做？

安装最低版本的AEM 6.5 Feature Pack 8以便AMS连接器正常工作。 请参阅[可用性](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability)，以便您可以获取AEM Screens Feature Pack的最低版本。

### 5.如何在Screens中配置CQ Link Externalizer服务？

该服务用于定义创作实例和发布实例的公共主机名，然后使用这些值更新设备服务器URL并用于ContextHub定位。

Screens中的CQ Link Externalizer服务可通过以下方式配置：

1. 导航到`http://localhost:4502/system/console/configMgr`
1. Day CQ链接外部化器
1. 根据需要更改`author/publish`条目的主机名