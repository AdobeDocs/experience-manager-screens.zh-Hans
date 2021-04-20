---
title: 扩展AEM Screens组件
seo-title: 扩展AEM Screens组件
description: 以下教程将介绍扩展开箱即用式AEM Screens组件的步骤和最佳实践。 图像组件经过扩展以添加可创作的文本叠加。
seo-description: 以下教程将介绍扩展开箱即用式AEM Screens组件的步骤和最佳实践。 图像组件经过扩展以添加可创作的文本叠加。
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 1%

---


# 扩展AEM Screens组件{#extending-an-aem-screens-component}

以下教程将介绍扩展开箱即用式AEM Screens组件的步骤和最佳实践。 图像组件经过扩展以添加可创作的文本叠加。

## 概述 {#overview}

本教程面向初次接触AEM Screens的开发人员。 在本教程中，Screens图像组件经过扩展以创建海报组件。 标题、描述和徽标会叠加在图像顶部，以在序列渠道中创建引人入胜的体验。

>[!NOTE]
>
>在开始本教程之前，建议您先完成本教程：[开发AEM Screens的自定义组件](developing-custom-component-tutorial-develop.md)。

![自定义海报组件](assets/2018-05-07_at_4_09pm.png)

自定义海报组件是通过扩展图像组件创建的。

## 前提条件 {#prerequisites}

要完成本教程，需要执行以下操作：

1. [AEM 6.4](https://docs.adobe.com/content/help/zh-Hans/experience-manager-64/release-notes/release-notes.html) 或 [AEM 6.](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html) 3+最新屏幕功能包
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本地开发环境

教程步骤和屏幕截图是使用CRXDE-Lite执行的。 [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) Eclipseor  [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) IntelliJIDE还可用于完成教程。有关使用IDE与AEM进行[开发的更多信息，请访问](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide)。

## 项目设置{#project-setup}

Screens项目的源代码通常作为多模块Maven项目进行管理。 为加快教程的进度，已使用[AEM项目原型13](https://github.com/adobe/aem-project-archetype)预生成一个项目。 有关使用Maven AEM项目原型创建项目的[详细信息，请参阅此处](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule)。

1. 使用&#x200B;**CRX包管理** `http://localhost:4502/crx/packmgr/index.jsp)r:`下载并安装以下包

   [获取文件](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [获取文件](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（可选）** 如果使用Eclipse或其他IDE，请下载以下源包。使用Maven命令将项目部署到本地AEM实例：

   **`mvn -PautoInstallPackage clean install`**

   SRC开始屏幕We.Retail运行项目

   [获取文件](assets/start-poster-screens-weretail-run.zip)

1. 在&#x200B;**CRX包管理器** `http://localhost:4502/crx/packmgr/index.jsp`中，安装了以下两个包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens We.Retail运行通过CRX包管理器安装的Ui.Apps和Ui.Content包](assets/crx-packages.png)

   Screens We.Retail运行通过CRX包管理器安装的Ui.Apps和Ui.Content包

## 创建海报组件{#poster-cmp}

海报组件扩展了现成的屏幕图像组件。 Sling的机制`sling:resourceSuperType`用于继承图像组件的核心功能，而无需复制和粘贴。 有关[Sling请求处理基础知识的更多信息，请访问此处。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

海报组件以全屏方式以预览/制作模式呈现。 在编辑模式下，为了便于创作序列渠道，必须以不同方式呈现组件。

1. 在&#x200B;**下方的`/apps/weretail-run/components/content`CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp`（或选择的IDE）中，创建一个名为`poster`的新`cq:Component`。

   向`poster`组件添加以下属性：

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

   通过将`sling:resourceSuperType`属性设置为等于`screens/core/components/content/image`，海报组件可以有效地继承图像组件的所有功能。 可以在`screens/core/components/content/image`组件下添加位于`poster`下的对等节点和文件，以覆盖和扩展功能。

1. 将`cq:editConfig`节点复制到`/libs/screens/core/components/content/image.`组件下方的`cq:editConfig`中。`/apps/weretail-run/components/content/poster`

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

   最容易从现有对话框中开始，然后进行修改。

   1. 从以下位置复制对话框：`/libs/wcm/foundation/components/image/cq:dialog`
   1. 将对话框粘贴到`/apps/weretail-run/components/content/poster`下方

   ![将对话框从/libs/wcm/foundation/components/image/cq:dialog复制到/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   将对话框从/libs/wcm/foundation/components/image/cq:dialog复制到/apps/weretail-run/components/content/poster

   Screens `image`组件被超类型化到WCM Foundation `image`组件。 因此，`poster`组件从两者继承了功能。 海报组件的对话框由“屏幕”和“基础”对话框的组合组成。 **Sling资源合并**&#x200B;的功能用于隐藏从超类型组件继承的无关对话框字段和选项卡。

1. 使用XML中显示的以下更改更新`/apps/weretail-run/components/content/poster`下方的cq:dialog:

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

   `items`节点上使用属性`sling:hideChildren`= `"[linkURL,size]`&quot;，以确保对话框中隐藏&#x200B;**linkURL**&#x200B;和&#x200B;**size**&#x200B;字段。 仅从海报对话框中删除这些节点是不够的。 辅助功能选项卡上的属性`sling:hideResource="{Boolean}true"`用于隐藏整个选项卡。

   在对话框中添加了两个选择字段，以使作者能够控制标题和说明的文本位置和颜色。

   ![海报 — 最终对话框结构](assets/2018-05-03_at_4_49pm.png)

   海报 — 最终对话框结构

   此时，可以将`poster`组件的实例添加到We.Retail Run项目的&#x200B;**Idle 渠道**&#x200B;页面：`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`。

   ![海报对话框字段](assets/poster-dialog-full.png)

   海报对话框字段

1. 在`/apps/weretail-run/components/content/poster`下创建名为`production.html.`的文件

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

   以上是海报组件的制作标记。 HTL脚本将覆盖`screens/core/components/content/image/production.html`。 `image.js`是创建类似POJO的Image对象的服务器端脚本。 然后，可以调用Image对象以将`src`渲染为内联样式background-image。

   `The h1` 添加h2标记后，会根据组件属性显示标题和说明： `${properties.jcr:title}` 和 `${properties.jcr:description}`。

   `h1`和`h2`标记周围是一个div包装器，包含三个CSS类，变量为&quot; `cmp-poster__text`&quot;。 `textPosition`和`textColor`属性的值用于根据作者的对话框选择更改呈现的CSS类。 在下一节中，将编写客户端库中的CSS，以在显示中启用这些更改。

   徽标也作为叠加包含在组件中。 在此示例中，We.Retail徽标的路径硬编码在DAM中。 根据用例，创建新对话框字段可使徽标路径成为动态填充的值可能更有意义。

   另请注意，组件中使用了BEM（块元素修饰符）记号。 BEM是一种CSS编码约定，它使创建可重用组件更加容易。 BEM是[AEM核心组件](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)使用的记号。 有关更多信息，请访问：[https://getbem.com/](https://getbem.com/)

1. 在`/apps/weretail-run/components/content/poster`下创建名为`edit.html.`的文件

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

   上面是海报组件的&#x200B;**edit**&#x200B;标记。 HTL脚本将覆盖`/libs/screens/core/components/content/image/edit.html`。 标记与`production.html`标记类似，并将在图像顶部显示标题和说明。

   将添加`aem-Screens-editWrapper`，以便组件不会在编辑器中呈现全屏。 `data-emptytext`属性确保在未填充图像或内容时显示占位符。

## 创建客户端库{#clientlibs}

客户端库提供了组织和管理AEM实施所需的CSS和JavaScript文件的机制。 有关使用[客户端库的详细信息，请访问此处。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

AEM Screens组件在编辑模式与预览/生产模式下的呈现方式不同。 将创建两组客户端库，一组用于编辑模式，另一组用于预览/生产。

1. 为海报组件的客户端库创建文件夹。

   在`/apps/weretail-run/components/content/poster,`下面创建一个名为`clientlibs`的新文件夹。

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在`clientlibs`文件夹下，创建一个名为`shared`的类型为`cq:ClientLibraryFolder.`的新节点

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 将以下属性添加到共享客户端库：

   * `allowProxy` | 布尔型 | `true`
   * `categories` | String[] |  `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的属性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的属性

   `categories`属性是标识客户端库的字符串。 `cq.screens.components`类别在“编辑”和“预览/生产”模式下均使用。 因此，在`shared` clientlib中定义的所有CSS/JS都会以所有模式加载。

   绝不直接在生产环境中向/apps公开任何路径是最佳做法。 `allowProxy`属性确保客户端库CSS和JS通过前缀`/etc.clientlibs`引用。 有关[allowProxy属性的详细信息，请访问此处。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. 在共享文件夹下创建名为`css.txt`的文件。

   使用以下内容填充文件：

   ```
   #base=css
   
   styles.less
   ```

1. 在`shared`文件夹下创建一个名为`css`的文件夹。 在`css`文件夹下添加一个名为`style.less`的文件。 客户端库的结构现在应当如下：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教程使用LESS，而不是直接编写CSS。 [LESS](https://lesscss.org/) 是一款流行的CSS预编译器，它支持CSS变量、混合和函数。AEM客户端库本身支持LESS编译。 Sass或其他预编译器可以使用，但需要在AEM外部编译。

1. 使用以下内容填充`/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less`:

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
   >Google Web字体用于字体系列。 Web字体需要Internet连接，并且并非所有屏幕实现都会可靠连接。 计划脱机模式是Screens部署的重要考虑事项。

1. 复制`shared`客户端库文件夹。 将其粘贴为同级文件，并将其重命名为`production`。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 将生产clientlibrary的`categories`属性更新为`cq.screens.components.production.`

   `cq.screens.components.production`类别确保样式仅在预览/生产模式下加载。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的属性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的属性

1. 使用以下内容填充`/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less`:

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

   上述样式在屏幕上的绝对位置显示标题和说明。 标题将显示得比描述大很多。 使用组件的BEM记号可以非常轻松地在cmp-poster类中仔细地调整样式范围。

第三个clientlibrary类别:`cq.screens.components.edit`可用于向组件添加仅编辑特定样式。

| Clientlib类别 | 使用 |
|---|---|
| `cq.screens.components` | 在编辑和制作模式之间共享的样式和脚本 |
| `cq.screens.components.edit` | 仅在编辑模式下使用的样式和脚本 |
| `cq.screens.components.production` | 仅在生产模式中使用的样式和脚本 |

## 将海报组件添加到序列渠道{#add-sequence-channel}

海报组件旨在用于序列渠道。 本教程的启动包包含一个空闲渠道。 空闲渠道已预配置为允许组&#x200B;**We.Retail Run - Content**&#x200B;的组件。 海报组件的组设置为`We.Retail Run - Content`，可添加到渠道。

1. 从We.Retail Run项目打开Idle渠道:**`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 将&#x200B;**Poster**&#x200B;组件的新实例从页面的侧栏拖放到页面。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 编辑海报组件的对话框以添加图像、标题和说明。 使用“文本位置”和“文本颜色”选项可确保在图像上可读取标题/说明。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重复上述步骤以添加一些海报组件。 在组件之间添加过渡。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 将所有内容组合在一起{#putting-it-all-together}

以下视频显示完成的组件以及如何将其添加到序列渠道。 然后，该渠道将添加到“位置”显示屏，并最终分配到Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成的代码{#finished-code}

下面是教程中完成的代码。 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**&#x200B;和&#x200B;**screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**&#x200B;是编译的AEM包。 **SRC-screens-weretail-run-0.0.1.zip **是未编译的源代码，可使用Maven进行部署。

[获取文件](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[获取文件](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final Screens We.Retail运行项目

[获取文件](assets/src-screens-weretail-run-001.zip)
