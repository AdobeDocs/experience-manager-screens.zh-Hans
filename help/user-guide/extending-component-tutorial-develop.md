---
title: 扩展AEM Screens组件
seo-title: 扩展AEM Screens组件
description: 以下教程将演示扩展开箱即用AEM Screens组件的步骤和最佳实践。 图像组件经过扩展，可添加可创作的文本叠加。
seo-description: 以下教程将演示扩展开箱即用AEM Screens组件的步骤和最佳实践。 图像组件经过扩展，可添加可创作的文本叠加。
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: 开发屏幕
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1854'
ht-degree: 1%

---


# 扩展AEM Screens组件{#extending-an-aem-screens-component}

以下教程将演示扩展开箱即用AEM Screens组件的步骤和最佳实践。 图像组件经过扩展，可添加可创作的文本叠加。

## 概述 {#overview}

本教程面向不熟悉AEM Screens的开发人员。 在本教程中，扩展了Screens图像组件以创建海报组件。 标题、描述和徽标叠加在图像顶部，以在序列渠道中创建引人入胜的体验。

>[!NOTE]
>
>在开始本教程之前，建议您先完成本教程：[为AEM Screens开发自定义组件](developing-custom-component-tutorial-develop.md)。

![自定义海报组件](assets/2018-05-07_at_4_09pm.png)

自定义海报组件是通过扩展图像组件来创建的。

## 前提条件 {#prerequisites}

要完成本教程，需要满足以下条件：

1. [AEM 6.4](https://docs.adobe.com/content/help/zh-Hans/experience-manager-64/release-notes/release-notes.html) 或 [AEM 6.3](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html) +最新Screens功能包
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本地开发环境

使用CRXDE-Lite可执行教程步骤和屏幕截图。 [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) ElliJIDE [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) 也可用于完成本教程。有关使用IDE进行[开发以使用AEM的更多信息，请参阅此处](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide)。

## 项目设置{#project-setup}

Screens项目的源代码通常作为多模块Maven项目进行管理。 为加快教程的进度，已使用[AEM项目原型13](https://github.com/adobe/aem-project-archetype)预生成一个项目。 有关[使用Maven AEM项目原型创建项目的更多详细信息，请参阅此处](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule)。

1. 使用&#x200B;**CRX包管理** `http://localhost:4502/crx/packmgr/index.jsp)r:`下载并安装以下包

[获取文件](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [获取文件](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **或者，如果** 使用Eclipse或其他IDE，请下载以下源包。使用Maven命令将项目部署到本地AEM实例：

   **`mvn -PautoInstallPackage clean install`**

   SRC启动屏幕We.Retail运行项目

[获取文件](assets/start-poster-screens-weretail-run.zip)

1. 在&#x200B;**CRX包管理器** `http://localhost:4502/crx/packmgr/index.jsp`中，安装了以下两个包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens We.Retail运行Ui.Apps和Ui.Content包，这些包通过CRX包管理器安装](assets/crx-packages.png)

   Screens We.Retail运行Ui.Apps和Ui.Content包，这些包通过CRX包管理器安装

## 创建海报组件{#poster-cmp}

海报组件可扩展现成的屏幕图像组件。 Sling机制`sling:resourceSuperType`用于继承图像组件的核心功能，而无需复制并粘贴。 有关[Sling请求处理基础知识的更多信息，请参阅此处。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

海报组件在预览/生产模式下以全屏呈现。 在编辑模式下，请务必以不同方式呈现组件，以便于创作序列渠道。

1. 在&#x200B;**** `http://localhost:4502/crx/de/index.jsp`（或选择的IDE）的`/apps/weretail-run/components/content`下方，创建名为`poster`的新`cq:Component`。

   将以下属性添加到`poster`组件：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![/apps/weretail-run/components/content/poster的属性](assets/poster.png)

   /apps/weretail-run/components/content/poster的属性

   通过将`sling:resourceSuperType`属性设置为等于`screens/core/components/content/image`，海报组件可有效地继承图像组件的所有功能。 可以在`screens/core/components/content/image`组件下方添加在`poster`组件下方找到的对等节点和文件，以覆盖和扩展功能。

1. 复制`/libs/screens/core/components/content/image.`组件下方的`cq:editConfig`节点，并在`/apps/weretail-run/components/content/poster`组件下方粘贴`cq:editConfig`。

   在`cq:editConfig/cq:dropTargets/image/parameters`节点上，将`sling:resourceType`属性更新为等于`weretail-run/components/content/poster`。

   ![edit-config](assets/edit-config.png)

   cq:editConfig的XML表示形式如下所示：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. 复制要用于`poster`组件的WCM Foundation `image`对话框。

   最简单的方法是从现有对话框开始，然后进行修改。

   1. 从以下位置复制对话框：`/libs/wcm/foundation/components/image/cq:dialog`
   1. 将对话框粘贴到`/apps/weretail-run/components/content/poster`下方

   ![将对话框从/libs/wcm/foundation/components/image/cq:dialog复制到/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   将对话框从/libs/wcm/foundation/components/image/cq:dialog复制到/apps/weretail-run/components/content/poster

   屏幕`image`组件是WCM Foundation `image`组件的超级类型。 因此，`poster`组件会从这两个组件继承功能。 海报组件的对话框由屏幕和基础对话框的组合组成。 **Sling资源合并器**&#x200B;的功能用于隐藏从超类型组件继承的不相关对话框字段和选项卡。

1. 使用XML中表示的以下更改更新`/apps/weretail-run/components/content/poster`下的cq:dialog:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   `sling:hideChildren`= `"[linkURL,size]`&quot;属性用于`items`节点，以确保在对话框中隐藏&#x200B;**linkURL**&#x200B;和&#x200B;**size**&#x200B;字段。 仅从海报对话框中删除这些节点是不够的。 辅助功能选项卡中的属性`sling:hideResource="{Boolean}true"`用于隐藏整个选项卡。

   对话框中添加了两个选择字段，以便作者控制标题和描述的文本位置和颜色。

   ![海报 — 最终对话框结构](assets/2018-05-03_at_4_49pm.png)

   海报 — 最终对话框结构

   此时，可以将`poster`组件的实例添加到We.Retail Run项目的&#x200B;**Idle Channel**&#x200B;页面中：`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`。

   ![海报对话框字段](assets/poster-dialog-full.png)

   海报对话框字段

1. 在名为`production.html.`的`/apps/weretail-run/components/content/poster`下创建文件

   使用以下内容填充文件：

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   上面是海报组件的生产标记。 HTL脚本会覆盖`screens/core/components/content/image/production.html`。 `image.js`是用于创建类似POJO的图像对象的服务器端脚本。 然后，可以调用Image对象以将`src`渲染为内联样式的background-image。

   `The h1` 和h2标记会根据组件属性显示标题和描述： `${properties.jcr:title}` 和 `${properties.jcr:description}`。

   `h1`和`h2`标记周围是一个div包装器，包含三个CSS类，其变体为“ `cmp-poster__text`”。 `textPosition`和`textColor`属性的值用于根据作者的对话框选择更改呈现的CSS类。 在下一部分中，将编写客户端库中的CSS以在显示中启用这些更改。

   组件中还包含徽标作为叠加。 在此示例中，We.Retail徽标的路径在DAM中进行了硬编码。 根据用例的不同，创建新对话框字段以使徽标路径成为动态填充值可能更有意义。

   另请注意，组件使用BEM（块元素修饰符）符号。 BEM是一种CSS编码约定，可更轻松地创建可重用组件。 BEM是[AEM核心组件](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)使用的符号。 有关更多信息，请访问：[https://getbem.com/](https://getbem.com/)

1. 在名为`edit.html.`的`/apps/weretail-run/components/content/poster`下创建文件

   使用以下内容填充文件：

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   上面是海报组件的&#x200B;**edit**&#x200B;标记。 HTL脚本会覆盖`/libs/screens/core/components/content/image/edit.html`。 标记类似于`production.html`标记，将在图像顶部显示标题和描述。

   添加了`aem-Screens-editWrapper`，以便组件不会在编辑器中呈现全屏。 `data-emptytext`属性可确保在未填充图像或内容时显示占位符。

## 创建客户端库 {#clientlibs}

客户端库提供了一种机制，用于组织和管理实施AEM所必需的CSS和JavaScript文件。 有关使用[客户端库的更多信息，请参阅此处。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

AEM Screens组件在编辑模式与预览/生产模式下的呈现方式不同。 将创建两组客户端库，一组用于“编辑”模式，另一组用于“预览”/“生产”模式。

1. 为海报组件的客户端库创建文件夹。

   在`/apps/weretail-run/components/content/poster,`下方创建一个名为`clientlibs`的新文件夹。

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在`clientlibs`文件夹下，创建一个名为`shared`的类型为`cq:ClientLibraryFolder.`的新节点

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 将以下属性添加到共享客户端库：

   * `allowProxy` | 布尔型 | `true`
   * `categories` |字符串[] |  `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的属性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的属性

   `categories`属性是标识客户端库的字符串。 `cq.screens.components`类别在“编辑”和“预览”/“生产”模式中均使用。 因此，在`shared` clientlib中定义的任何CSS/JS都会在所有模式下加载。

   最佳做法是，切勿在生产环境中直接向/apps显示任何路径。 `allowProxy`属性可确保通过前缀`/etc.clientlibs`引用客户端库CSS和JS。 有关[allowProxy属性的更多信息，请参阅此处。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. 在共享文件夹下方创建名为`css.txt`的文件。

   使用以下内容填充文件：

   ```
   #base=css
   
   styles.less
   ```

1. 在`shared`文件夹下创建一个名为`css`的文件夹。 在`css`文件夹下添加名为`style.less`的文件。 客户端库的结构现在应如下所示：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教程不使用LESS，而是直接编写CSS。 [](https://lesscss.org/) LESS是一种常用的CSS预编译器，它支持CSS变量、混合和函数。AEM客户端库本身支持LESS编译。 Sas或其他预编译器可以使用，但需要在AEM之外进行编译。

1. 使用以下内容填充`/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` :

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >Google Web字体用于字体系列。 Web字体需要Internet连接，而且并非所有屏幕实施都能可靠连接。 规划离线模式是Screens部署的重要注意事项。

1. 复制`shared`客户端库文件夹。 将其粘贴为同级，然后将其重命名为`production`。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 将生产clientlibrary的`categories`属性更新为`cq.screens.components.production.`

   `cq.screens.components.production`类别可确保样式仅在“预览”/“生产”模式下加载。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的属性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的属性

1. 使用以下内容填充`/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` :

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   上述样式将标题和描述显示在屏幕上的绝对位置。 标题的显示量将显着大于描述。 使用组件的BEM符号，可以非常轻松地在cmp-poster类中仔细调整样式。

第三个clientlibrary类别：`cq.screens.components.edit`可用于仅向组件添加编辑特定样式。

| Clientlib类别 | 使用 |
|---|---|
| `cq.screens.components` | 在编辑模式和生产模式之间共享的样式和脚本 |
| `cq.screens.components.edit` | 仅在编辑模式下使用的样式和脚本 |
| `cq.screens.components.production` | 仅在生产模式中使用的样式和脚本 |

## 将海报组件添加到序列渠道{#add-sequence-channel}

海报组件可用于序列渠道。 本教程的起始包中包含一个空闲渠道。 空闲渠道已预配置为允许组&#x200B;**We.Retail Run - Content**&#x200B;的组件。 海报组件的组设置为`We.Retail Run - Content`，并可添加到渠道中。

1. 从We.Retail Run项目中打开Idle Channel:**`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 将&#x200B;**海报**&#x200B;组件的新实例从上的侧栏拖放到页面上。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 编辑海报组件的对话框以添加图像、标题、描述。 使用文本位置和文本颜色选项可确保标题/描述在图像上可读。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重复上述步骤以添加一些海报组件。 在组件之间添加过渡。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 将所有数据放在一起{#putting-it-all-together}

以下视频显示完成的组件以及如何将其添加到序列渠道。 然后，该渠道会添加到“位置”显示屏，并最终分配给Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成的代码{#finished-code}

以下是教程中完成的代码。 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**&#x200B;和&#x200B;**screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**&#x200B;是编译的AEM包。 **SRC-screens-weretail-run-0.0.1.zip **是未编译的源代码，可使用Maven部署。

[获取文件](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[获取文件](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC最终屏幕We.Retail运行项目

[获取文件](assets/src-screens-weretail-run-001.zip)
