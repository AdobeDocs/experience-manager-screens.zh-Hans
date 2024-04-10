---
title: AEM Screens常见问题解答
description: 阅读与AEM Screens项目相关的常见问题解答。
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '2121'
ht-degree: 0%

---

# AEM Screens常见问题解答 {#aem-screens-faqs}

以下部分提供了与AEM Screens项目相关的几个常见问题解答。

## 空白屏幕问题 {#blank-screen}

>[!NOTE]
>列出的强制检查，在引发问题之前应由主要支持或客户端支持尝试。

### 1.对于面对黑屏或未播放内容的客户，应该采取哪些急救故障排除步骤？ {#troubleshooting-blank-screen}

* 检查渠道预览是否有效。
* 检查显示预览是否有效
* 尝试将播放器注册为系统上的浏览器扩展，以使其使用该显示器，并检查此操作是否有效。
* 在系统上运行播放器后，导航至 `http://localhost:24502`. 检查是否正确下载了所有内容。
* 检查资源，以便您可以确保已创建相应的演绎版并且正在播放正确的演绎版。
* 检查任何计划内容以及时间是否正确。 检查播放器中设置的时间是否正确。
* Inspect播放器控制台将记录并检查任何错误。 右键单击并检查以查看控制台日志。 如果您使用的是Windows Player，请按 `CTRL + ALT +I` 以调出开发控制台以查看日志。

### 2.如何通过创建默认渠道或计划来解决AEM Screens中的灰屏问题？

要避免出现字段中的空白或灰色屏幕，请创建一个默认全局渠道或计划，将其分配给优先级最低的每个显示器1。 如果内容更新出现问题（由于网络、播放器、服务器或复制），因为播放器已在光盘上缓存了此内容，播放应该可以正常进行，并避免出现灰屏。

所有其他内容（例如渠道或计划）的优先级大于1，因此其他内容具有优先级，并且全局渠道或计划内容（优先级为1）仅作为回退选项播放。

## 渠道管理 {#channel-management}

### 1.在线渠道和离线渠道有何区别？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

An ***线上渠道*** 在实时环境中显示更新的内容，而 ***脱机渠道*** 显示缓存的内容。

### 2.如何在线创建频道？ {#how-do-i-make-a-channel-online}

选择渠道并从操作栏导航到渠道属性。 Check **开发人员模式（强制渠道联机）** 下 **渠道** 选项卡，使渠道联机。

### 3. “渠道角色”字段有什么用处？ {#what-is-the-use-of-the-channel-role-field}

渠道角色是实际运行的渠道的抽象，以便作者可以直接关注一般体验。 您可以将其视为一种标记，用于唯一标识上下文中的渠道（显示或计划）。

### 4.如何解决实际渠道问题？ {#how-does-actual-channel-resolution-happen}

对象 *静态引用*，则分辨率仅遵循指定的路径。

对象 *动态引用*，在将渠道分配给显示区（而不是计划）后，就会发生分辨率。 显示路径将成为渠道的上下文，分辨率如下所示（优先级从高到低）：

1. 显示内容有一个与引用的渠道名称匹配的子节点
1. 该显示区有一个与引用的渠道名称匹配的同级节点
1. 显示的父位置有一个与引用的渠道名称匹配的子节点
1. 显示器的父级位置有一个与引用的渠道名称匹配的子节点

等等，直到您访问位置文件夹并在此时停止（例如，您不能引用将位于渠道文件夹中的渠道，而只能引用位置子树中的渠道）。

### 5.如何在AEM Screens渠道中设置自定义clientlib离线配置？

使用内置的自定义客户端代码时 `clientlib` 在AEM Screens渠道中，需要执行以下步骤来确保 `clientlib` 文件在渠道中加载成功(`manifest.json`)并包含 `clientlib`.

在渠道编辑器中执行以下步骤：

1. 选择一个渠道，然后选择 **编辑** 从操作栏中。
1. 选择要添加自定义的组件 `clientlib`.
1. 选择配置按钮（扳手图标）。
1. 导航至 **脱机配置** 选项卡，并在中添加自定义clientlib的路径 **客户端库**.

## 设备注册 {#device-registration}

### 1.如果发现端点（如设备载入和注册请求），则可以编写许多设备的脚本并注册这些设备。 除了将此锁定到分支Wi-Fi之外，是否可以保护这些请求？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

当前只能在创作实例上注册。 尽管注册服务未经身份验证，但它仅在AEM中创建挂起设备，实际上并不注册该设备或分配任何显示。

要注册设备(在AEM中为设备创建用户)，请向AEM进行身份验证，当前请手动按照注册向导完成注册。 理论上，恶意用户可以创建多个挂起的设备，但若没有AEM登录则无法注册任何设备。

### 2.是否有办法通过某种形式的身份验证将HTTPGET请求转换为HTTPPOST？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

注册请求是POST请求。

建议从会话中获取设备ID，而不是作为参数传递。 这将清理服务器日志、浏览器缓存等。 这不是安全问题。 语义上。 当服务器上没有状态更改时使用GET，而状态更改时使用POST。

### 3.是否可以拒绝设备注册请求？ {#is-there-a-way-to-decline-a-device-registration-request}

您不能拒绝注册请求。 相反，注册请求应在中配置的超时后过期 `Adobe Experience Manager Web Console`. 默认情况下，此值设置为一天，并存储在内存缓存中。

## 设备监控和运行状况报告 {#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens播放器显示空白屏幕，我如何进行故障排除？

检查以下是否可能解决空白屏幕问题：

* AEM无法推送离线内容
* 渠道没有任何内容
* 没有任何资源被安排在当前时间显示

### 2.如果AEM Screens Player无法注册且其状态显示为“失败”，我该怎么做？

启用Apache Sling引用过滤器允许为空。 要在AEM Screens Player和AEM Screens服务器之间优化控制协议的操作，需要此项。

1. 导航到 **Adobe Experience Manager Web控制台配置**
1. 查看 **allow.empty** 选项。
1. 单击&#x200B;**保存**。

### 3.如果在注册AEM Screens播放器时，设备显示故障，并且控制台日志显示ENAME_NOT_FOUND错误，如何进行故障排除？

如果播放器无法找到AEM Screens服务器DNS，则可能会发生此问题。 您可以尝试使用IP地址进行连接。 要获取服务器的IP，请使用： *arp &lt;server_dns_name>*.

### 4. AMS是否建议在所有设备上实施Android™监视程序？ Watchdog (Cordova)插件是否包含在APK中？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

一个使用纯Android™ API的跨平台Android™监视程序已经是应用程序的一部分。 无需其他软件。 但是，根据您使用的设备，您可以退出该应用程序以获取完整电源周期的系统权限(`Powermanager` api)（如有必要）。 如果使用制造商密钥没有放弃，它会退出并重新启动应用程序，但不会重新启动电源。

有关如何实施Android™ Player的更多信息，请参阅 [**实施Android™ Player**](implementing-android-player.md).

### 5.Adobe/AMS建议使用哪些第三方远程监控和警报工具（软件）来监控每台设备？ {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根据您希望在监视和警报中显示的内容，如果设备一段时间未发出信号，AEM Screens Notifications服务会向您发送通知。 第三方工具取决于您的操作系统(OS)、其功能以及客户的特定需求。

有关可在何处监视设备活动的详细信息，请参见 [**AEM屏幕通知服务**](screens-notifications-service.md).

## AEM Screens 播放器

### 1.如何将ChromeOS播放器安装为Chrome浏览器插件？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

在开发人员模式下，可以将ChromeOS播放器安装为Chrome浏览器插件，而无需实际的Chrome播放器设备。 要安装，请执行以下步骤：

1. 单击 [此处](https://download.macromedia.com/screens/) 以下载最新的Chrome播放器。
1. 解压缩并将其保存在磁盘上。
1. 打开Chrome浏览器并选择 **扩展** 或直接导航到 ***chrome://extensions***.
1. 打开 **开发人员模式** 从右上角。
1. 选择 **加载已解压缩** 从左上角，加载解压的Chrome播放器。
1. 如果扩展列表中存在，请选中 **AEM Screens Chrome Player** 插件。
1. 打开新选项卡，然后单击 **应用程序** 图标，或直接导航到 ***chrome://apps***.
1. 选择 **AEM Screens** 插件。 默认情况下，播放器将以全屏模式启动。 按 **Esc** 退出全屏模式。

### 2.如果Screens播放器无法通过使用自定义错误处理程序通过发布实例进行身份验证，如何进行故障排除？

AEM Screens播放器启动时，会向 ***/content/screens/svc.ping.json***，播放器收到404错误时。 播放器发起身份验证请求，以针对发布实例进行身份验证。 如果发布实例中存在自定义错误处理程序，请确保您在上返回匿名用户的404状态代码。 ***/content/screens/svc.ping.json***.

### 3.如何在Android™ Player中设置设备屏幕？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

执行以下步骤，在任何Android™播放器上启用“Stay Awake in（保持清醒状态）”：

1. 导航到Android™播放器设置> **关于**.
1. 点按7次内部版本号，以便您能够启用 **开发人员选项** 在 **设置**.
1. 导航到 **开发人员选项**.
1. 启用 **保持清醒**.

### 4.如何为Windows Player启用窗口模式？{#enable-player}

Windows Player中没有窗口模式。 它始终为全屏模式。

### 5.如果AEM Screens播放器持续发送登录请求，如何进行故障排除？

请按照以下步骤对持续向发送请求的AEM Screens播放器排除故障 `/content/screens/svc.json` 和 `/libs/granite/core/content/login.validate/j_security_check`：

1. AEM Screens播放器启动时，会请求 `/content/screens/svc.json`. 当播放器在响应中获得404状态代码时，它会使用启动身份验证请求 `/libs/granite/core/content/login.validate/j_security_check` 针对 *发布* 实例。 如果中存在自定义错误处理程序，则 *发布* 实例中，请确保返回匿名用户的404状态代码 `/content/screens/svc.json` 或 `/content/screens/svc.ping.json`.

1. 检查您的Dispatcher配置是否允许在 `/filters`.

   请参阅 [配置屏幕过滤器](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters) 以了解更多详细信息。

1. 检查您的Dispatcher重写规则是否正在将任何屏幕路径重写到其他路径。

1. 检查您是否拥有 `/etc/map` 规则 *作者* 或 *发布* 实例和屏幕路径与 `sling:match` 并在内部重定向到其他路径。 解析中的确切url `/system/console/jcrresolver` 帮助识别 *发布* 实例正在将这些URL重写为任何其他路径。

1. 检查Apache Sling资源解析器工厂配置是否导致内部重写。

### 6.如何从播放器API获取显示器和设备的详细信息？

您可以通过以下方式获取显示器和设备的详细信息：

* **内部JS API**
* **ContextHub存储**：在中定义了三个ContextHub存储 `/libs/screens/clientlibs/contexthub` 以公开渠道、设备和显示信息。

  请按照以下步骤使用这些ContentHub存储值：

   * 编辑渠道属性并将“个性化”选项卡中的ContextHub路径设置为值（如上所述）
   * 在渠道JS中，您可以使用：

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## 一般疑难解答提示 {#general-troubleshooting-tips}

### 1.如何禁用Livefyre以避免A/P屏幕错误？

通过执行以下操作，禁用Livefyre以避免日志错误。

1. ***禁用Livefyre捆绑包：***

   * 导航到 `https://<host>:<port>/system/console/bundles`。
   * 搜索AEM Livefyre捆绑包： `com.adobe.cq.social.cq-social-livefyre`.
   * 选择 **停止**.

1. ***禁用Livefyre轮询程序：***

   * 在CRXDE Lite中，导航到 `/etc/importers/polling/livefyre-poller/jcr:content`.
   * 添加属性 *已启用* type *布尔型*.
   * 设置 **启用的属性** 到 **false**.

### 2.如何添加Oak索引信息？ {#add-oak-index-info}

AEM Screens为产品使用的查询创建索引定义。
如果存在 *查询遍历WARN* 在 `error.log`，为您的查询创建自定义索引。 请参阅 [配置索引](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes) 以了解更多详细信息。

您还可以在上查看其他资源 [Oak文档](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3.配置v3清单需要什么？ {#configure-v3}

要启用v3清单，您必须：

* 更新Dispatcher。
请参阅 [为清单版本v3配置Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) 以了解更多详细信息。

* 更新自定义组件。
请参阅 [自定义处理程序模板](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers) 以了解更多详细信息。

* 在中禁用ContentSync `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* 在中启用智能同步 `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* 编辑 `channel/experience fragment/page components`.

* 导航至 **脱机配置** 选项卡。

* 输入 `clientlibs `和文件夹中必须添加到清单中的静态文件。

### 4.如果在软件包screens-cloud-ams-pkg-0.0.20、screens-cloud-ams-pkg-0.0.16和screens核心包已安装但未处于活动状态，您应该怎么做？

安装AEM 6.5 Feature Pack 8的最低版本以便AMS连接器正常工作。 请参阅 [可用性](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) 以便获取AEM Screens功能包的最低版本。

### 5.如何在Screens中配置CQ Link Externalizer服务？

该服务用于定义创作实例和发布实例的公共主机名，然后使用这些值更新设备服务器URL并用于ContextHub定位。

Screens中的CQ Link Externalizer服务可通过以下方式配置：

1. 导航到 `http://localhost:4502/system/console/configMgr`
1. Day CQ链接外部化器
1. 更改主机名 `author/publish` 根据需要输入内容