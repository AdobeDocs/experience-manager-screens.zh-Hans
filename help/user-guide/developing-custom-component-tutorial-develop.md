---
title: 为AEM Screens开发自定义组件
seo-title: 为AEM Screens开发自定义组件
description: 以下教程将逐步介绍为AEM Screens创建自定义组件的步骤。 AEM Screens重新使用其他AEM产品的许多现有设计模式和技术。 本教程重点介绍了为AEM Screens进行开发时的差异和特殊注意事项。
seo-description: 为AEM Screens构建一个简单的“Hello World”组件的介绍性教程。 AEM Screens重新使用其他AEM产品的许多现有设计模式和技术。 下面的教程旨在突出显示在为AEM Screens进行开发时的特定差异和注意事项。
uuid: 8ec8be5a-6348-48f2-9cb7-75b2bad555a6
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 24eb937f-ab51-4883-8236-8ebe6243f6e3
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 为AEM Screens开发自定义组件 {#developing-a-custom-component-for-aem-screens}

以下教程将逐步介绍为AEM Screens创建自定义组件的步骤。 AEM Screens重新使用其他AEM产品的许多现有设计模式和技术。 本教程重点介绍了为AEM Screens进行开发时的差异和特殊注意事项。

## 概述 {#overview}

本教程面向不熟悉AEM Screens的开发人员。 在本教程中，为AEM Screens中的序列渠道构建了一个简单的“Hello World”组件。 一个对话框允许作者更新显示的文本。

![超视低](assets/overviewhellow.png)

## 前提条件 {#prerequisites}

要完成本教程，需要执行以下操作：

1. [AEM 6.5或](https://helpx.adobe.com/experience-manager/6-4/release-notes.html)[AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) +最新屏幕功能包

1. [AEM Screens 播放器](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-screens-introduction.html)
1. 本地开发环境

教程步骤和屏幕截图是使用 **CRXDE-Lite执行的**。 IDE还可用于完成教程。 有关使用IDE与AEM进行开发的更 [多信息，请参阅此处。](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#eclipse-ide)


## 项目设置 {#project-setup}

Screens项目的源代码通常作为多模块Maven项目进行管理。 为了加速教程，使用 [AEM Project Archetype 13预生成了一个项目](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)。 有关使用Maven AEM [项目原型创建项目的更多详细信息，请参阅此处](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#maven-multimodule)。

1. 使用 [CRX包管理器下载并安装以下包](http://localhost:4502/crx/packmgr/index.jsp):

   [获取文件](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [获取文件](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **(可选** )如果使用Eclipse或其他IDE，请下载以下源包。 使用Maven命令将项目部署到本地AEM实例：

   **`mvn -PautoInstallPackage clean install`**

   启动HelloWorld SRC屏幕We.Retail运行项目

   [获取文件](assets/src-screens-weretail-run.zip)

1. 在 [CRX包管理器中](http://localhost:4502/crx/packmgr/index.jsp) ，验证是否已安装以下两个包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![Screens We.Retail运行通过CRX包管理器安装的Ui.Apps和Ui.Content包](assets/crx-packages.png)

   Screens We.Retail运行通过CRX包管理器安装的Ui.Apps和Ui.Content包

1. screens-weretail-run.ui.ap **ps** package在下面安装代码 `/apps/weretail-run`。

   此包中包含负责为项目渲染自定义组件的代码。 此包中包括组件代码以及所需的任何JavaScript或CSS。 此包还嵌 **入了screens-weretail-run.core-0.0.1-SNAPSHOT.jar** ，其中包含项目所需的任何Java代码。

   >[!NOTE]
   >
   >在本教程中，不会编写任何Java代码。 如果需要更复杂的业务逻辑，可以使用核心Java捆绑包创建和部署后端Java。

   ![CRXDE Lite中ui.apps代码的表示](assets/uipps-contents.png)

   CRXDE Lite中ui.apps代码的表示

   helloworld **组件** 当前只是一个占位符。 在教程中，将添加允许作者更新组件显示的消息的功能。

1. screens-weretail-run.ui.content **包** ，将安装以下代码：

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`
   此包中包含项目所需的启动内容和配置结构。 **`/conf/we-retail-run`** 包含We.Retail Run项目的所有配置。 **`/content/dam/we-retail-run`** 包括为项目启动数字资产。 **`/content/screens/we-retail-run`** 包含Screens内容结构。 所有这些路径下的内容主要在AEM中更新。 为了提高环境（本地、开发、舞台、产品）之间的一致性，通常在源控件中保存基本内容结构。

1. **导航到AEM Screens &gt; We.Retail Run项目：**

   从AEM开始菜单&gt;单击屏幕，然后单击图标。 验证是否可以看到We.Retail Run Project。

   ![我们继续运行的起动器](assets/we-retaiul-run-starter.png)

## 创建Hello world组件 {#hello-world-cmp}

Hello world组件是一个简单的组件，它允许用户输入要在屏幕上显示的消息。 该组件基于 [AEM Screens组件模板：https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)。

AEM Screens有一些有趣的限制，这对于传统的WCM Sites组件未必是如此。

* 大多数Screens组件需要在目标数字标牌设备上全屏运行
* 大多数Screens组件需要可嵌入到序列渠道中才能生成幻灯片
* 创作应允许在序列渠道中编辑单个组件，因此无需全屏渲染它们

1. 在 **CRXDE-Lite**`http://localhost:4502/crx/de/index.jsp` （或选择的IDE）中，导航到 `/apps/weretail-run/components/content/helloworld.`

   将以下属性添加到组 `helloworld` 件：

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![/apps/weretail-run/components/content/helloworld的属性](assets/2018-04-28_at_4_23pm.png)

   /apps/weretail-run/components/content/helloworld的属性

   Helloworld **组件扩展** 了基础／组件/parbase组件 **** ，因此它可以在序列通道中正确使用。

1. 在名称下创建文 `/apps/weretail-run/components/content/helloworld` 件 `helloworld.html.`

   用以下内容填充文件：

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   Screens组件需要两种不同的渲染，具体取决于 [使用的创作模式](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/author-environment-tools.html#PageModes) :

   1. **生产**:预览或发布模式(wcmmode=disabled)
   1. **编辑**:用于所有其他创作模式，如编辑、设计、基架、开发人员……
   `helloworld.html`充当交换机，检查当前处于活动状态的创作模式并重定向到另一个HTL脚本。 屏幕组件使用的一个常见约定是具有“编 `edit.html` 辑”模式的脚本和“生 `production.html` 产”模式的脚本。

1. 在名称下创建文 `/apps/weretail-run/components/content/helloworld` 件 `production.html.`

   用以下内容填充文件：

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   以上是Hello world组件的制作标记。 由于 `data-duration` 组件在序列渠道上使用，因此包含属性。 序 `data-duration` 列渠道使用该属性来了解要显示序列项的时长。

   组件使用文 `div` 本呈现 `h1` 和标记。 `${properties.message}` 是HTL脚本的一部分，它将输出名为的JCR属性的内容 `message`。 稍后会创建一个对话框，允许用户为属性文本输 `message` 入值。

   另请注意，BEM（块元素修饰符）记号用于组件。 BEM是一种CSS编码惯例，它使创建可重用组件更加容易。 BEM是 [AEM核心组件使用的表示法](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)。 更多信息，请访问： [https://getbem.com/](https://getbem.com/)

1. 在名称下创建文 `/apps/weretail-run/components/content/helloworld` 件 `edit.html.`

   用以下内容填充文件：

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   以上是Hello world组件的编辑标记。 如果填充了对话框消息，则第一个块会显示组件的编辑版本。

   如果未输入对话框消息，则呈现第二块。 在此 `cq-placeholder` 情 `data-emptytext` 况下，将标签 ***Hello World*** 作为占位符呈现。 标签的字符串可以使用i18n进行国际化，以便支持在多个区域设置中进行创作。

1. **复制屏幕图像对话框，用于Hello world组件。**

   最简单的方法是从现有对话框开始，然后进行修改。

   1. 从以下位置复制对话框： `/libs/screens/core/components/content/image/cq:dialog`
   1. 将对话框粘贴到下方 `/apps/weretail-run/components/content/helloworld`
   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **更新“Hello World”对话框以包含消息选项卡。**

   更新对话框，使其与以下内容匹配。 最终对话框的JCR节点结构在XML中如下所示：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image will be shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   消息的文本字段将保存到名为的属性中， `message` 持续时间的数字字段将保存到名为的属性中 `duration`。 这两个属性都由HTL `/apps/weretail-run/components/content/helloworld/production.html` as和引 `${properties.message}` 用 `${properties.duration}`。

   ![Hello World —— 已完成对话框](assets/2018-04-29_at_5_21pm.png)

   Hello World —— 已完成对话框

## 创建客户端库 {#clientlibs}

客户端库提供了组织和管理AEM实施所需的CSS和JavaScript文件的机制。

在编辑模式与预览／生产模式下，AEM Screens组件的呈现方式不同。 将创建两个客户端库，一个用于编辑模式，另一个用于预览／制作。

1. 为Hello world组件的客户端库创建一个文件夹。

   在下 `/apps/weretail-run/components/content/helloworld`面创建一个名为的新文件夹 `clientlibs`。

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. 在文件 `clientlibs` 夹下面创建一个名为的 `shared` 新节点 `cq:ClientLibraryFolder.`

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. 将以下属性添加到共享客户端库：

   * `allowProxy` | 布尔型 | `true`

   * `categories`|字符串[] | `cq.screens.components`
   ![/apps/weretail-run/components/content/helloworld/clientlibs/shared的属性](assets/2018-05-03_at_1026pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/shared的属性

   类别属性是标识客户端库的字符串。 cq.screens.components类别在“编辑”和“预览／生产”模式中都使用。 因此，在sharedclientlib中定义的任何CSS/JS都会在所有模式下加载。

   在生产环境中，绝不直接向/apps公开任何路径是最佳做法。 allowProxy属性确保客户端库CSS和JS通过前缀of/etc.clientlibs被引用。

1. 创建名为共享 `css.txt` 文件夹下的文件。

   用以下内容填充文件：

   ```
   #base=css
   
   styles.less
   ```

1. 创建名为文件夹 `css` 下的文 `shared` 件夹。 在文件夹下添加 `style.less` 一个名 `css` 称文件。 客户端库的结构现在应当如下：

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   本教程不是直接编写CSS，而是使用LESS。 [LESS](https://lesscss.org/) 是一款流行的CSS预编译器，它支持CSS变量、混合和函数。 AEM客户端库本机支持LESS编译。 Sass或其他预编译器可用，但需要在AEM之外进行编译。

1. 填充 `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` 以下内容：

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. 复制并粘贴客 `shared` 户端库文件夹，以创建名为的新客户端库 `production`。

   ![复制共享客户端库以创建新的生产客户端库](assets/copy-clientlib.gif)

   复制共享客户端库以创建新的生产客户端库

1. 将生产 `categories` 客户端库的属性更新为 `cq.screens.components.production.`

   这可确保仅在“预览／生产”模式下加载样式。

   ![/apps/weretail-run/components/content/helloworld/clientlibs/production的属性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/production的属性

1. 填充 `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` 以下内容：

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   上述样式将以屏幕中间居中的方式显示消息，但仅在生产模式下显示。

第三个clientlibrary类别：可 `cq.screens.components.edit` 用于向组件添加仅编辑特定样式。

| Clientlib类别 | 使用情况 |
|---|---|
| `cq.screens.components` | 在编辑模式和生产模式之间共享的样式和脚本 |
| `cq.screens.components.edit` | 仅在编辑模式中使用的样式和脚本 |
| `cq.screens.components.production` | 仅在生产模式中使用的样式和脚本 |

## 创建设计页面 {#design-page}

AEM Screens使用静 [态页面模板](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/page-templates-static.html)[和设计配](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/default-components-designmode.html) 置进行全局更改。 设计配置通常用于为渠道上的Parsys配置允许的组件。 最佳实践是以特定于应用程序的方式存储这些配置。

在We.Retail Run设计页面下创建，该页面将存储特定于We.Retail Run项目的所有配置。

1. 在 **CRXDE-Lite中**`http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs` ，导航到 `/apps/settings/wcm/designs`
1. 在设计文件夹下创建一个新节点，该节 `we-retail-run` 点以类型命名 `cq:Page`。
1. 在页面 `we-retail-run` 下方，添加另一个名为类 `jcr:content` 型的节点 `nt:unstructured`。 将以下属性添加到节 `jcr:content` 点：

   | 名称 | 类型 | 值 |
   |---|---|---|
   | jcr:title | 字符串 | We.Retail Run |
   | sling:resourceType | 字符串 | wcm/core/components/designer |
   | cq:doctype | 字符串 | html_5 |

   ![设计页面，网址为：/apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   设计页面，网址为：/apps/settings/wcm/designs/we-retail-run

## 创建序列渠道 {#create-sequence-channel}

Hello World组件旨在用于序列渠道。 要测试组件，将创建新的序列渠道。

1. 从AEM开始菜单中，导航到 **Screens** &gt; **We.Retail** Run &gt;并选择 **渠道**。

1. 单击“创 **建** ”按钮

   1. 选择“ **创建实体”**
   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. 在创建向导中：

1. 模板步骤——选择**序列渠道**

   1. 属性步骤
   * 基本选项卡&gt;标题=空 **闲渠道**
   * 渠道选项卡&gt;选中使 **渠道联机**
   ![空闲通道](assets/idle-channel.gif)

1. 打开空闲渠道的页面属性。 更新“设计”字段，以指 `/apps/settings/wcm/designs/we-retail-run,`向在上一节中创建的设计页面。

   ![设计配置/apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   指向/apps/settings/wcm/designs/we-retail-run的设计配置

1. 编辑新创建的空闲渠道以将其打开。

1. 将页面模式切换为“设 **计** ”模式

   1. 单击Parsys中 **的扳手图标** ，以配置允许的组件

   1. 选择 **Screens组** ，选择 **We.Retail Run - Content** 组。
   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. 将页面模式切换为“ **编辑”**。 Hello world组件现在可添加到页面并与其他序列渠道组件组合。

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. 在 **CRXDE-Lite中** ，导航到 `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par``/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`。 注意， `components` 该属性现在包 `group:Screens`括 `group:We.Retail Run - Content`。

   ![在/apps/settings/wcm/designs/we-retail-run下进行设计配置](assets/2018-05-07_at_1_14pm.png)

   在/apps/settings/wcm/designs/we-retail-run下进行设计配置

## 整合 {#putting-it-all-together}

以下视频显示完成的组件以及如何将其添加到序列渠道。 然后，该渠道会添加到位置显示屏，并最终分配给Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9&captions=chi_hans)

## 完成的代码 {#finished-code}

下面是教程中完成的代码。 screens-weretail-run.ui.ap **ps-0.0.1-SNAPSHOT.zip** 和 **** screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip是编译的AEM包。 **SRC-screens-weretail-run-0.0.1.zip **是未编译的源代码，可使用Maven部署。

[获取文件](assets/screens-weretail-runuiapps-001-snapshot.zip)

[获取文件](assets/screens-weretail-runuicontent-001-snapshot.zip)

[获取文件](assets/screens-weretail-run.zip)
