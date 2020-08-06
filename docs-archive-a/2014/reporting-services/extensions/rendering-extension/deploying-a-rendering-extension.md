---
title: 部署呈现扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1c70d9cdc947134c682132b0baea02274ddf4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587232"
---
# <a name="deploying-a-rendering-extension"></a><span data-ttu-id="644aa-102">部署呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="644aa-102">Deploying a Rendering Extension</span></span>
  <span data-ttu-id="644aa-103">在编写 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 报表呈现扩展插件并将其编译为 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 库之后，需要使其变得可供报表服务器和报表设计器发现。</span><span class="sxs-lookup"><span data-stu-id="644aa-103">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report rendering extension into a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="644aa-104">为此，请将此扩展插件复制到适当的目录并向适当的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配置文件添加条目。</span><span class="sxs-lookup"><span data-stu-id="644aa-104">To do so, copy the extension to the appropriate directory and add entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-rendering-extension-element"></a><span data-ttu-id="644aa-105">配置文件呈现扩展插件元素</span><span class="sxs-lookup"><span data-stu-id="644aa-105">Configuration File Rendering Extension Element</span></span>  
 <span data-ttu-id="644aa-106">将呈现扩展插件编译为 .DLL 后，您可以在 rsreportserver.config 文件中添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="644aa-106">Once a rendering extension has been compiled into a .DLL, you add an entry into the rsreportserver.config file.</span></span> <span data-ttu-id="644aa-107">默认情况下，该位置为%ProgramFiles%\Microsoft SQL Server \ MSRS10_50。 \<InstanceName>\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="644aa-107">By default, the location is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="644aa-108">父元素为 \<Render>。</span><span class="sxs-lookup"><span data-stu-id="644aa-108">The parent element is \<Render>.</span></span> <span data-ttu-id="644aa-109">在 Render 元素之下是用于每个呈现扩展插件的 Extension 元素。</span><span class="sxs-lookup"><span data-stu-id="644aa-109">Under the Render element is an Extension element for each rendering extension.</span></span> <span data-ttu-id="644aa-110">`Extension` 元素包含两个属性，即 Name 和 Type。</span><span class="sxs-lookup"><span data-stu-id="644aa-110">The `Extension` element contains two attributes, Name and Type.</span></span>  
  
 <span data-ttu-id="644aa-111">下表描述了 `Extension` 呈现扩展插件的元素的属性：</span><span class="sxs-lookup"><span data-stu-id="644aa-111">The following table describes the attributes for the `Extension` element for rendering extensions:</span></span>  
  
|<span data-ttu-id="644aa-112">Attribute</span><span class="sxs-lookup"><span data-stu-id="644aa-112">Attribute</span></span>|<span data-ttu-id="644aa-113">说明</span><span class="sxs-lookup"><span data-stu-id="644aa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="644aa-114">**名称**</span><span class="sxs-lookup"><span data-stu-id="644aa-114">**Name**</span></span>|<span data-ttu-id="644aa-115">扩展插件的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="644aa-115">A unique name for the extension.</span></span> <span data-ttu-id="644aa-116">**Name** 属性的最大长度是 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="644aa-116">The maximum length for the **Name** attribute is 255 characters.</span></span> <span data-ttu-id="644aa-117">该名称在配置文件的 **Extensions** 元素内的所有条目中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="644aa-117">The name must be unique among all entries within the **Extensions** element of a configuration file.</span></span> <span data-ttu-id="644aa-118">如果存在重复的名称，则报表服务器返回错误。</span><span class="sxs-lookup"><span data-stu-id="644aa-118">If a duplicate name is present, the report server returns an error.</span></span>|  
|<span data-ttu-id="644aa-119">类型 </span><span class="sxs-lookup"><span data-stu-id="644aa-119">**Type**</span></span>|<span data-ttu-id="644aa-120">以逗号分隔的列表，其中包含完全限定的命名空间以及程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="644aa-120">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|<span data-ttu-id="644aa-121">**Visible**</span><span class="sxs-lookup"><span data-stu-id="644aa-121">**Visible**</span></span>|<span data-ttu-id="644aa-122">值为 `false` 指示在用户界面中将不显示该呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="644aa-122">A value of `false` indicates that the rendering extension should not be visible in user interfaces.</span></span> <span data-ttu-id="644aa-123">如果未包含此属性，则默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="644aa-123">If the attribute is not included, the default value is `true`.</span></span>|  
|<span data-ttu-id="644aa-124">**LogAllExecutionRequests**</span><span class="sxs-lookup"><span data-stu-id="644aa-124">**LogAllExecutionRequests**</span></span>|<span data-ttu-id="644aa-125">值 `false` 表示在一个会话中只对第一次报表执行记录一个条目。</span><span class="sxs-lookup"><span data-stu-id="644aa-125">A value of `false` indicates that an entry is logged for only the first report execution in a session.</span></span> <span data-ttu-id="644aa-126">如果未包含此属性，则默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="644aa-126">If the attribute is not included, the default value is `true`.</span></span><br /><br /> <span data-ttu-id="644aa-127">例如，此设置决定着是只对报表中呈现的第一页记录一个条目（设为 `false` 时），还是对报表中呈现的每一页都记录一个条目（设为 `true` 时）。</span><span class="sxs-lookup"><span data-stu-id="644aa-127">For example, this setting determines whether to log an entry for only the first page rendered in a report (when `false`) or an entry for each page rendered in the report (when `true`).</span></span>|  
  
 <span data-ttu-id="644aa-128">有关详细信息，请参阅 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="644aa-128">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="644aa-129">将扩展插件部署到报表服务器</span><span class="sxs-lookup"><span data-stu-id="644aa-129">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="644aa-130">报表服务器使用呈现扩展插件将报表导出为其他格式。</span><span class="sxs-lookup"><span data-stu-id="644aa-130">The report server uses rendering extensions to export reports to other formats.</span></span> <span data-ttu-id="644aa-131">您应将呈现扩展插件程序集作为专用程序集部署到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="644aa-131">You should deploy your rendering extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="644aa-132">还需要在报表服务器配置文件 rsreportserver.config 中生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="644aa-132">You also need to make an entry in the report server configuration file, rsreportserver.config.</span></span>  
  
### <a name="to-deploy-the-assembly"></a><span data-ttu-id="644aa-133">部署程序集</span><span class="sxs-lookup"><span data-stu-id="644aa-133">To deploy the assembly</span></span>  
  
1.  <span data-ttu-id="644aa-134">将程序集从临时位置复制到您要在其上使用此呈现扩展插件的报表服务器的 bin 目录中。</span><span class="sxs-lookup"><span data-stu-id="644aa-134">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the rendering extension.</span></span> <span data-ttu-id="644aa-135">Report Server Bin 目录的默认位置为 "%ProgramFiles%\Microsoft SQL Server \ MSRS10_50"。 \<InstanceName>\Reporting Services\reportserver\bin。</span><span class="sxs-lookup"><span data-stu-id="644aa-135">The default location of the report server Bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\Bin.</span></span>  
  
2.  <span data-ttu-id="644aa-136">在复制程序集文件后，打开 rsreportserver.config 文件。</span><span class="sxs-lookup"><span data-stu-id="644aa-136">After the assembly file is copied, open the rsreportserver.config file.</span></span> <span data-ttu-id="644aa-137">rsreportserver.config 文件也位于报表服务器 bin 目录中。</span><span class="sxs-lookup"><span data-stu-id="644aa-137">The rsreportserver.config file is also located in the report server bin directory.</span></span> <span data-ttu-id="644aa-138">还需要在配置文件中为扩展插件程序集文件生成一个条目。</span><span class="sxs-lookup"><span data-stu-id="644aa-138">You need to make an entry in the configuration file for your extension assembly file.</span></span> <span data-ttu-id="644aa-139">可使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或简单的文本编辑器打开该文件。</span><span class="sxs-lookup"><span data-stu-id="644aa-139">You can open the file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor.</span></span>  
  
     <span data-ttu-id="644aa-140">有关详细信息，请参阅 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="644aa-140">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
3.  <span data-ttu-id="644aa-141">在 Rsreportserver.config 文件中找到 **Render** 元素。</span><span class="sxs-lookup"><span data-stu-id="644aa-141">Locate the **Render** element in the Rsreportserver.config file.</span></span> <span data-ttu-id="644aa-142">应当在以下位置为新创建的扩展插件生成一个条目：</span><span class="sxs-lookup"><span data-stu-id="644aa-142">An entry for your newly created extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="644aa-143">为呈现扩展插件添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="644aa-143">Add an entry for your rendering extension.</span></span> <span data-ttu-id="644aa-144">此条目应包含一个具有 **Name** 和 **Type**值的元素，可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="644aa-144">Your entry should include an element that has values for **Name** and **Type**, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     <span data-ttu-id="644aa-145">**Name** 的值必须是呈现扩展插件的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="644aa-145">The value for **Name** is the unique name of the rendering extension.</span></span> <span data-ttu-id="644aa-146">Type 的值是一个以逗号分隔的列表，它包含 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 实现的完全限定命名空间的一个条目，后跟程序集的名称（不包含 .dll 文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="644aa-146">The value for **Type** is a comma-separated list that includes an entry for the fully qualified namespace of your <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> implementation, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="644aa-147">默认情况下，呈现扩展插件是可见的。</span><span class="sxs-lookup"><span data-stu-id="644aa-147">By default, rendering extensions are visible.</span></span> <span data-ttu-id="644aa-148">若要从用户界面（如报表管理器）中隐藏扩展插件，请将**Visible**属性添加到 `Extension` 元素，并将其设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="644aa-148">To hide an extension from user interfaces, such as Report Manager, add a **Visible** attribute to the `Extension` element, and set it to `false`.</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="644aa-149">验证部署</span><span class="sxs-lookup"><span data-stu-id="644aa-149">Verifying the deployment</span></span>  
 <span data-ttu-id="644aa-150">还可以打开报表管理器，并验证您的扩展插件是否包括在报表的可用导出类型列表中。</span><span class="sxs-lookup"><span data-stu-id="644aa-150">You can also open Report Manager and verify that your extension is included in the list of available export types for a report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644aa-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="644aa-151">See Also</span></span>  
 <span data-ttu-id="644aa-152">[实现呈现扩展插件](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="644aa-152">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="644aa-153">[呈现扩展插件概述](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="644aa-153">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="644aa-154">[实现 IRenderingExtension 接口](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="644aa-154">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 [<span data-ttu-id="644aa-155">扩展插件的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="644aa-155">Security Considerations for Extensions</span></span>](../security-considerations-for-extensions.md)  
  
  
