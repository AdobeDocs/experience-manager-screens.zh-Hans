---
title: 为AEM Screens开发自定义组件
seo-title: 为AEM Screens开发自定义组件
description: 以下教程将逐步介绍为AEM Screens创建自定义组件的步骤。 AEM Screens重用了其他AEM产品的许多现有设计模式和技术。 本教程重点介绍在为AEM Screens开发时的差异和特殊注意事项。
seo-description: 为AEM Screens构建一个简单的“Hello World”组件的入门教程。 AEM Screens重用了其他AEM产品的许多现有设计模式和技术。 下面的教程将重点介绍在为AEM Screens进行开发时的具体差异和考虑事项。
uuid: 8ec8be5a-6348-48f2-9cb7-75b2bad555a6
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 24eb937f-ab51-4883-8236-8ebe6243f6e3
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '2186'
ht-degree: 1%

---


# 为AEM Screens开发自定义组件{#developing-a-custom-component-for-aem-screens}

以下教程将逐步介绍为AEM Screens创建自定义组件的步骤。 AEM Screens重用了其他AEM产品的许多现有设计模式和技术。 本教程重点介绍在为AEM Screens开发时的差异和特殊注意事项。

## 概述 {#overview}

本教程面向不熟悉AEM Screens的开发人员。 在本教程中，为AEM Screens的序列渠道构建了一个简单的“Hello World”组件。 通过对话框，作者可以更新显示的文本。

![过度低沉](assets/overviewhellow.png)

## 前提条件 {#prerequisites}

要完成本教程，需要以下内容：

1. [AEM 6.5](https://helpx.adobe.com/cn/experience-manager/6-4/release-notes.html) 或 [AEM 6.3](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html) +最新屏幕功能包

1. [AEM Screens 播放器](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-screens-introduction.html)
1. 本地开发环境

教程步骤和屏幕截图是使用&#x200B;**CRXDE-Lite**&#x200B;执行的。 IDE还可用于完成教程。 有关使用IDE开发[和AEM的更多信息，请参阅此处。](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#eclipse-ide)


## 项目设置{#project-setup}

Screens项目的源代码通常作为多模块Maven项目进行管理。 为了加快教程的进行，项目是使用[AEM Project Archetype 13](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)预生成的。 有关使用Maven AEM项目原型创建项目的[详细信息，请参阅此](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#maven-multimodule)。

1. 使用[CRX包管理器](http://localhost:4502/crx/packmgr/index.jsp)下载并安装以下包：

   [获取文件](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [获取文件](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **(** 可选)如果使用Eclipse或其他IDE，请下载以下源包。使用Maven命令将项目部署到本地AEM实例：

   **`mvn -PautoInstallPackage clean install`**

   开始HelloWorld SRC屏幕We.Retail运行项目

   [获取文件](assets/src-screens-weretail-run.zip)

1. 在[CRX包管理器](http://localhost:4502/crx/packmgr/index.jsp)中，验证以下两个包是否已安装：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens We.Retail运行通过CRX包管理器安装的Ui.Apps和Ui.Content包](assets/crx-packages.png)

   Screens We.Retail运行通过CRX包管理器安装的Ui.Apps和Ui.Content包

1. **screens-weretail-run.ui.apps**&#x200B;软件包在`/apps/weretail-run`下安装代码。

   此包包含负责渲染项目自定义组件的代码。 此包包含组件代码以及所需的任何JavaScript或CSS。 此包还嵌入&#x200B;**screens-weretail-run.core-0.0.1-SNAPSHOT.jar**，其中包含项目所需的任何Java代码。

   >[!NOTE]
   >
   >在本教程中，不编写任何Java代码。 如果需要更复杂的业务逻辑，可以使用核心Java包创建和部署后端Java。

   ![在CRXDE Lite中表示ui.apps代码](assets/uipps-contents.png)

   在CRXDE Lite中表示ui.apps代码

   **helloworld**&#x200B;组件当前仅是占位符。 在教程中，将添加允许作者更新组件显示的消息的功能。

1. **screens-weretail-run.ui.content**&#x200B;软件包在以下位置安装代码：

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   此包包含项目所需的启动内容和配置结构。 **`/conf/we-retail-run`** 包含We.Retail Run项目的所有配置。**`/content/dam/we-retail-run`** 包括为项目启动数字资产。**`/content/screens/we-retail-run`** 包含Screens内容结构。所有这些路径下的内容主要在AEM中更新。 为了提高环境（本地、开发、舞台、产品）之间的一致性，通常在源代码控件中保存基本内容结构。

1. **导航到“AEM Screens”>“We.Retail Run”项目：**

   从AEM开始菜单>单击屏幕图标。 验证是否可以看到We.Retail Run Project。

   ![We-Retaiul-run-starter](assets/we-retaiul-run-starter.png)

## 创建Hello World组件{#hello-world-cmp}

Hello World组件是一个简单的组件，它允许用户输入要在屏幕上显示的消息。 组件基于[AEM Screens组件模板：https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)。

AEM Screens有一些有趣的限制条件，传统的WCM Sites组件未必如此。

* 大多数屏幕组件需要在目标数字标牌设备上全屏运行
* 大多数Screens组件需要可嵌入到序列渠道中才能生成幻灯片
* 创作应允许在序列渠道中编辑单个组件，因此无需全屏渲染它们

1. 在&#x200B;**CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp`（或选择的IDE）中，导航到`/apps/weretail-run/components/content/helloworld.`

   将以下属性添加到`helloworld`组件：

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![/apps/weretail-run/components/content/helloworld的属性](assets/2018-04-28_at_4_23pm.png)

   /apps/weretail-run/components/content/helloworld的属性

   **helloworld**&#x200B;组件扩展了&#x200B;**foundation/components/parbase**&#x200B;组件，因此它可以正确地在序列渠道内使用。

1. 在`/apps/weretail-run/components/content/helloworld`下创建名为`helloworld.html.`的文件

   使用以下内容填充文件：

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   Screens组件需要两种不同的呈现方式，具体取决于使用的[创作模式](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/author-environment-tools.html#PageModes):

   1. **生产**:预览模式或发布模式(wcmmode=disabled)
   1. **编辑**:用于所有其他创作模式，如编辑、设计、基架、开发人员……

   `helloworld.html`充当交换机，检查当前处于活动状态的创作模式并重定向到另一个HTL脚本。屏幕组件使用的常见约定是：“编辑”模式使用`edit.html`脚本，“生产”模式使用`production.html`脚本。

1. 在`/apps/weretail-run/components/content/helloworld`下创建名为`production.html.`的文件

   使用以下内容填充文件：

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   以上是Hello World组件的制作标记。 包含`data-duration`属性，因为组件用于序列渠道。 序列渠道使用`data-duration`属性来了解序列项的显示时间。

   组件呈现一个`div`和一个带有文本的`h1`标签。 `${properties.message}` 是HTL脚本的一部分，它将输出名为的JCR属性的内容 `message`。稍后会创建一个对话框，允许用户为`message`属性文本输入值。

   另请注意，BEM（块元素修饰符）记号用于组件。 BEM是一种CSS编码规范，它使创建可重用组件更加容易。 BEM是[AEM核心组件](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)使用的记号法。 更多信息，请访问：[https://getbem.com/](https://getbem.com/)

1. 在`/apps/weretail-run/components/content/helloworld`下创建名为`edit.html.`的文件

   使用以下内容填充文件：

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

   上面是Hello World组件的编辑标记。 如果填充了对话框消息，则第一个块显示组件的编辑版本。

   如果未输入对话消息，则呈现第二块。 在这种情况下，`cq-placeholder`和`data-emptytext`将标签&#x200B;***Hello World***&#x200B;呈现为占位符。 标签的字符串可以使用i18n进行国际化，以便支持在多个语言环境中进行创作。

1. **复制屏幕要用于Hello World组件的图像对话框。**

   最容易从现有对话框中开始，然后进行修改。

   1. 从以下位置复制对话框：`/libs/screens/core/components/content/image/cq:dialog`
   1. 将对话框粘贴到`/apps/weretail-run/components/content/helloworld`下

   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **更新“Hello World”对话框以包含消息选项卡。**

   更新对话框，使其与以下内容匹配。 最终对话框的JCR节点结构以XML形式显示：

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

   消息的文本字段将保存到名为`message`的属性中，持续时间的编号字段将保存到名为`duration`的属性中。 HTL在`/apps/weretail-run/components/content/helloworld/production.html`中将这两个属性均作为`${properties.message}`和`${properties.duration}`引用。

   ![Hello World —— 已完成对话框](assets/2018-04-29_at_5_21pm.png)

   Hello World —— 已完成对话框

## 创建客户端库{#clientlibs}

客户端库提供一种机制，用于组织和管理AEM实现所需的CSS和JavaScript文件。

AEM Screens组件在编辑模式与预览/生产模式下的呈现方式不同。 将创建两个客户端库，一个用于编辑模式，另一个用于预览/生产。

1. 为Hello World组件的客户端库创建文件夹。

   在`/apps/weretail-run/components/content/helloworld`下面创建一个名为`clientlibs`的新文件夹。

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. 在`clientlibs`文件夹下，创建一个名为`shared`的类型为`cq:ClientLibraryFolder.`的新节点

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. 将以下属性添加到共享客户端库：

   * `allowProxy` | 布尔型 | `true`

   * `categories`|字符串[] |  `cq.screens.components`

   ![/apps/weretail-run/components/content/helloworld/clientlibs/shared的属性](assets/2018-05-03_at_1026pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/shared的属性

   类别属性是标识客户端库的字符串。 cq.screens.components类别在“编辑”和“预览/生产”模式下都使用。 因此，在sharedclientlib中定义的任何CSS/JS都以所有模式加载。

   在生产环境，绝不直接向/apps显示任何路径是最佳做法。 allowProxy属性确保客户端库CSS和JS通过前缀of/etc.clientlibs进行引用。

1. 在共享文件夹下创建名为`css.txt`的文件。

   使用以下内容填充文件：

   ```
   #base=css
   
   styles.less
   ```

1. 在`shared`文件夹下创建一个名为`css`的文件夹。 在`css`文件夹下添加一个名为`style.less`的文件。 客户端库的结构现在应当如下：

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   本教程使用的不是直接编写CSS，而是LESS。 [LESS](https://lesscss.org/) 是一种流行的CSS预编译器，它支持CSS变量、混合和函数。AEM客户端库本机支持LESS编译。 Sass或其他预编译器可以使用，但需要在AEM之外进行编译。

1. 使用以下内容填充`/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less`:

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

1. 复制并粘贴`shared`客户端库文件夹，以创建名为`production`的新客户端库。

   ![复制共享客户端库以创建新的生产客户端库](assets/copy-clientlib.gif)

   复制共享客户端库以创建新的生产客户端库

1. 将生产客户端库的`categories`属性更新为`cq.screens.components.production.`

   这确保样式仅在预览/生产模式下加载。

   ![/apps/weretail-run/components/content/helloworld/clientlibs/production的属性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/production的属性

1. 使用以下内容填充`/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less`:

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

   以上样式将在屏幕中间显示消息，但仅在生产模式下显示。

第三个客户端库类别:`cq.screens.components.edit`可用于向组件添加仅编辑特定样式。

| Clientlib类别 | 使用 |
|---|---|
| `cq.screens.components` | 在编辑和制作模式之间共享的样式和脚本 |
| `cq.screens.components.edit` | 仅在编辑模式下使用的样式和脚本 |
| `cq.screens.components.production` | 仅在生产模式中使用的样式和脚本 |

## 创建设计页{#design-page}

AEM Screens使用[静态页面模板](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/page-templates-static.html)和[设计配置](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/default-components-designmode.html)进行全局更改。 设计配置经常用于在渠道上为Parsys配置允许的组件。 最佳实践是以特定于应用程序的方式存储这些配置。

将在创建的“We.Retail Run Design”页面下存储特定于We.Retail Run项目的所有配置。

1. 在&#x200B;**中，CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs`导航到`/apps/settings/wcm/designs`
1. 在设计文件夹下新建一个名为`we-retail-run`的节点，类型为`cq:Page`。
1. 在`we-retail-run`页面下，添加另一个名为`jcr:content`的`nt:unstructured`类型的节点。 将以下属性添加到`jcr:content`节点：

   | 名称 | 类型 | 值 |
   |---|---|---|
   | jcr:title | 字符串 | We.Retail Run |
   | sling:resourceType | 字符串 | wcm/core/components/designer |
   | cq:doctype | 字符串 | html_5 |

   ![设计页面，网址为：/apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   设计页面，网址为：/apps/settings/wcm/designs/we-retail-run

## 创建序列渠道{#create-sequence-channel}

Hello World组件用于序列渠道。 要测试组件，将创建新的序列渠道。

1. 从AEM开始菜单，导航到&#x200B;**屏幕** > **We.Retail Ru** n >并选择&#x200B;**渠道**。

1. 单击&#x200B;**创建**&#x200B;按钮

   1. 选择&#x200B;**创建实体**

   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. 在创建向导中：

1. 模板步骤——选择&#x200B;**序列渠道**

   1. 属性步骤
   * 基本选项卡>标题= **空闲渠道**
   * 渠道选项卡>选中&#x200B;**使渠道联机**

   ![空闲渠道](assets/idle-channel.gif)

1. 打开空闲渠道的页面属性。 更新“设计”字段，以指向在上一节中创建的`/apps/settings/wcm/designs/we-retail-run,`设计页面。

   ![设计配置/apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   指向/apps/settings/wcm/designs/we-retail-run的设计配置

1. 编辑新创建的空闲渠道以将其打开。

1. 将页面模式切换为&#x200B;**Design**&#x200B;模式

   1. 单击Parsys中的&#x200B;**扳手**&#x200B;图标以配置允许的组件

   1. 选择&#x200B;**Screens**&#x200B;组和&#x200B;**We.Retail Run - Content**&#x200B;组。

   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. 将页面模式切换为&#x200B;**编辑**。 现在可以将Hello World组件添加到页面并与其他序列渠道组件组合。

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. 在&#x200B;**中，CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par`导航到`/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`。 请注意，`components`属性现在包括`group:Screens`、`group:We.Retail Run - Content`。

   ![/apps/settings/wcm/designs/we-retail-run下的设计配置](assets/2018-05-07_at_1_14pm.png)

   /apps/settings/wcm/designs/we-retail-run下的设计配置

## 自定义处理函数{#custom-handlers}的模板

如果您的自定义组件使用外部资源(如资产（图像、视频、字体、图标等）、特定资产演绎版或客户端库（css、js等），则这些资源不会自动添加到脱机配置中，因为默认情况下我们仅捆绑HTML标记。

为了让您自定义和优化下载到播放器的确切资产，我们优惠了自定义组件的扩展机制，以在Screens中显示其依赖关系到脱机缓存逻辑。

以下部分显示自定义脱机资源处理程序的模板以及该特定项目的`pom.xml`中的最低要求。

```java
package …;

import javax.annotation.Nonnull;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceUtil;
import org.apache.sling.api.resource.ValueMap;

import com.adobe.cq.screens.visitor.OfflineResourceHandler;

@Service(value = OfflineResourceHandler.class)
@Component(immediate = true)
public class MyCustomHandler extends AbstractResourceHandler {

 @Reference
 private …; // OSGi services injection

 /**
  * The resource types that are handled by the handler.
  * @return the handled resource types
  */
 @Nonnull
 @Override
 public String[] getSupportedResourceTypes() {
     return new String[] { … };
 }

 /**
  * Accept the provided resource, visit and traverse it as needed.
  * @param resource The resource to accept
  */
 @Override
 public void accept(@Nonnull Resource resource) {
     ValueMap properties = ResourceUtil.getValueMap(resource);
     
     /* You can directly add explicit paths for offline caching using the `visit`
        method of the visitor. */
     
     // retrieve a custom property from the component
     String myCustomRenditionUrl = properties.get("myCustomRenditionUrl", String.class);
     // adding that exact asset/rendition/path to the offline manifest
     this.visitor.visit(myCustomRenditionUrl);
     
     
     /* You can delegate handling for dependent resources so they are also added to
        the offline cache using the `accept` method of the visitor. */
     
     // retrieve a referenced dependent resource
     String referencedResourcePath = properties.get("myOtherResource", String.class);
     ResourceResolver resolver = resource.getResourceResolver();
     Resource referencedResource = resolver.getResource(referencedResourcePath);
     // let the handler for that resource handle it
     if (referencedResource != null) {
         this.visitor.accept(referencedResource);
     }
   }
}
```

以下代码在`pom.xml`中提供了该特定项目的最低要求：

```css
   <dependencies>
        …
        <!-- Felix annotations -->
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.9.0</version>
            <scope>provided</scope>
        </dependency>

        <!-- Screens core bundle with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.cq.screens</groupId>
            <artifactId>com.adobe.cq.screens</artifactId>
            <version>1.5.90</version>
            <scope>provided</scope>
        </dependency>
        …
      </dependencies>
```

## 将它们整合在一起{#putting-it-all-together}

以下视频显示完成的组件以及如何将其添加到序列渠道。 然后，该渠道会添加到“位置”显示屏，并最终分配给Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## 完成的代码{#finished-code}

下面是教程中完成的代码。 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**&#x200B;和&#x200B;**screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**&#x200B;是编译的AEM包。 **SRC-screens-weretail-run-0.0.1.zip **是未编译的源代码，可使用Maven进行部署。

[获取文件](assets/screens-weretail-runuiapps-001-snapshot.zip)

[获取文件](assets/screens-weretail-runuicontent-001-snapshot.zip)

[获取文件](assets/screens-weretail-run.zip)
