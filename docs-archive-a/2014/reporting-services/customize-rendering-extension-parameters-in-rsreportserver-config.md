---
title: 在 RSReportServer.Config 中自定义呈现扩展插件参数 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- configuration options [Reporting Services]
- DeviceInfo settings
- rendering extensions [Reporting Services], overriding behaviors
- parameters [Reporting Services], report rendering
- overriding report rendering behavior
- extensions [Reporting Services], rendering
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35a01e12fa4016d03717b008e4241c3be5e55236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693656"
---
# <a name="customize-rendering-extension-parameters-in-rsreportserverconfig"></a><span data-ttu-id="96337-102">在 RSReportServer.Config 中自定义呈现扩展插件参数</span><span class="sxs-lookup"><span data-stu-id="96337-102">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>
  <span data-ttu-id="96337-103">可以在 RSReportServer 配置文件中指定呈现扩展插件参数，以覆盖在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器上运行的报表的默认报表呈现行为。</span><span class="sxs-lookup"><span data-stu-id="96337-103">You can specify rendering extension parameters in the RSReportServer configuration file to override default report rendering behavior for reports that run on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="96337-104">可通过修改呈现扩展插件参数来实现以下目标：</span><span class="sxs-lookup"><span data-stu-id="96337-104">You can modify rendering extension parameters to achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="96337-105">更改呈现扩展插件名称在报表工具栏的“导出”列表中的显示方式（例如，将“Web 存档”更改为“MHTML”），或将该名称本地化为其他语言。</span><span class="sxs-lookup"><span data-stu-id="96337-105">Change how the rendering extension name appears in the Export list of the report toolbar (for example, to change "Web archive" to "MHTML"), or localize the name to a different language.</span></span>  
  
-   <span data-ttu-id="96337-106">创建同一呈现扩展插件的多个实例以支持不同的报表显示选项（例如，图像呈现扩展插件的纵向模式和横向模式版本）。</span><span class="sxs-lookup"><span data-stu-id="96337-106">Create multiple instances of the same rendering extension to support different report presentation options (for example, a portrait and landscape mode version of the Image rendering extension).</span></span>  
  
-   <span data-ttu-id="96337-107">更改默认的呈现扩展插件参数以使用不同的值（例如，图像呈现扩展插件使用 TIFF 作为默认输出格式；您可以修改扩展插件参数以改用 EMF）。</span><span class="sxs-lookup"><span data-stu-id="96337-107">Change the default rendering extension parameters to use different values (for example, the Image rendering extension uses TIFF as the default output format; you can modify the extension parameters to use EMF instead).</span></span>  
  
 <span data-ttu-id="96337-108">更改呈现扩展插件参数只影响报表服务器上的呈现操作。</span><span class="sxs-lookup"><span data-stu-id="96337-108">Changing the rendering extension parameters only affects rendering operations on the report server.</span></span> <span data-ttu-id="96337-109">您不能覆盖报表设计器的报表预览中的呈现扩展插件设置。</span><span class="sxs-lookup"><span data-stu-id="96337-109">You cannot override rendering extension settings in report preview in Report Designer.</span></span>  
  
 <span data-ttu-id="96337-110">在配置文件中指定呈现扩展插件参数会在全局范围内对呈现扩展插件产生影响。</span><span class="sxs-lookup"><span data-stu-id="96337-110">Specifying rendering extension parameters in the configuration files affects rendering extensions globally.</span></span> <span data-ttu-id="96337-111">无论何时使用某个特定的呈现扩展插件，都会使用配置文件中的设置来替代默认值。</span><span class="sxs-lookup"><span data-stu-id="96337-111">The settings in the configuration files are used in place of default values whenever a particular rendering extension is used.</span></span> <span data-ttu-id="96337-112">如果要为特定的报表或呈现操作设置呈现扩展插件参数，必须使用 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法或者通过对报表 URL 指定设备信息设置来以编程方式指定设备信息。</span><span class="sxs-lookup"><span data-stu-id="96337-112">If you want to set rendering extension parameters for a specific report or render operation, you must specify device information programmatically using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method or by specifying device information settings on a report URL.</span></span> <span data-ttu-id="96337-113">有关为呈现操作指定设备信息设置以及查看设备信息设置完整列表的详细信息，请参阅 [将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="96337-113">For more information about specifying device information settings for a render operation, and to view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="finding-and-modifying-rsreportserverconfig"></a><span data-ttu-id="96337-114">查找并修改 RSReportServer.config</span><span class="sxs-lookup"><span data-stu-id="96337-114">Finding and Modifying RSReportServer.config</span></span>  
 <span data-ttu-id="96337-115">报表输出格式的配置设置被指定为 RSReportServer.config 文件中的呈现扩展插件参数。</span><span class="sxs-lookup"><span data-stu-id="96337-115">Configuration settings for report output formats are specified as rendering extension parameters in the RSReportServer.config file.</span></span> <span data-ttu-id="96337-116">若要在配置文件中指定呈现扩展插件参数，必须知道如何定义用于设置呈现参数的 XML 结构。</span><span class="sxs-lookup"><span data-stu-id="96337-116">To specify rendering extension parameters in the configuration files, you must know how to define the XML structures that set rendering parameters.</span></span> <span data-ttu-id="96337-117">有两种 XML 结构可以修改：</span><span class="sxs-lookup"><span data-stu-id="96337-117">There are two XML structures that you can modify:</span></span>  
  
-   <span data-ttu-id="96337-118">`OverrideNames` 元素定义呈现扩展插件的显示名称和语言。</span><span class="sxs-lookup"><span data-stu-id="96337-118">The `OverrideNames` element defines the display name and language of the rendering extension.</span></span>  
  
-   <span data-ttu-id="96337-119">`DeviceInfo` XML 结构定义呈现扩展插件使用的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="96337-119">The `DeviceInfo` XML structure defines the device information settings that are used by a rendering extension.</span></span> <span data-ttu-id="96337-120">大多数呈现扩展插件参数作为设备信息设置进行指定。</span><span class="sxs-lookup"><span data-stu-id="96337-120">Most rendering extension parameters are specified as device information settings.</span></span>  
  
 <span data-ttu-id="96337-121">可以使用文本编辑器修改该文件。</span><span class="sxs-lookup"><span data-stu-id="96337-121">You can use a text editor to modify the file.</span></span> <span data-ttu-id="96337-122">可在 \Reporting Services\Report Server\Bin 文件夹中找到 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="96337-122">The RSReportServer.config file can be found in the \Reporting Services\Report Server\Bin folder.</span></span> <span data-ttu-id="96337-123">有关修改配置文件的详细信息，请参阅[修改 Reporting Services 配置文件 (RSreportserver.config)](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="96337-123">For more information about modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span>  
  
## <a name="changing-the-display-name"></a><span data-ttu-id="96337-124">更改显示名称</span><span class="sxs-lookup"><span data-stu-id="96337-124">Changing the Display Name</span></span>  
 <span data-ttu-id="96337-125">呈现扩展插件的显示名称显示在报表工具栏的“导出”列表中。</span><span class="sxs-lookup"><span data-stu-id="96337-125">The display name for a rendering extension appears in the Export list of the report toolbar.</span></span> <span data-ttu-id="96337-126">默认显示名称的示例包括 Web 存档、TIFF 文件和 Acrobat (PDF) 文件。</span><span class="sxs-lookup"><span data-stu-id="96337-126">Examples of default display names include Web archive, TIFF file, and Acrobat (PDF) file.</span></span> <span data-ttu-id="96337-127">通过在配置文件中指定 `OverrideNames` 元素，可以将默认的显示名称替换为自定义值。</span><span class="sxs-lookup"><span data-stu-id="96337-127">You can replace the default display name with a custom value by specifying the `OverrideNames` element in the configuration files.</span></span> <span data-ttu-id="96337-128">此外，如果您要定义单个呈现扩展插件的两个实例，则可在“导出”列表中使用 `OverrideNames` 元素来区分每个实例。</span><span class="sxs-lookup"><span data-stu-id="96337-128">In addition, if you are defining two instances of a single rendering extension, you can use the `OverrideNames` element to distinguish each instance in the Export list.</span></span>  
  
 <span data-ttu-id="96337-129">由于显示名称已本地化，因此如果要用自定义值来替换默认的显示名称，必须设置 `Language` 属性。</span><span class="sxs-lookup"><span data-stu-id="96337-129">Because display names are localized, you must set the `Language` attribute if you are replacing the default display name with a custom value.</span></span> <span data-ttu-id="96337-130">否则，将忽略您指定的任何名称。</span><span class="sxs-lookup"><span data-stu-id="96337-130">Otherwise, any name that you specify will be ignored.</span></span> <span data-ttu-id="96337-131">设置的语言值必须对报表服务器计算机有效。</span><span class="sxs-lookup"><span data-stu-id="96337-131">The language value that you set must be valid for the report server computer.</span></span> <span data-ttu-id="96337-132">例如，如果报表服务器在法语操作系统中运行，则应该指定“fr-FR”作为属性值。</span><span class="sxs-lookup"><span data-stu-id="96337-132">For example, if the report server is running on a French operating system, you should specify "fr-FR" as the attribute value.</span></span>  
  
 <span data-ttu-id="96337-133">下面的示例说明了如何在英文报表服务器上提供自定义名称：</span><span class="sxs-lookup"><span data-stu-id="96337-133">The following example illustrates how to provide a custom name on an English report server:</span></span>  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## <a name="changing-device-information-settings"></a><span data-ttu-id="96337-134">更改设备信息设置</span><span class="sxs-lookup"><span data-stu-id="96337-134">Changing Device Information Settings</span></span>  
 <span data-ttu-id="96337-135">若要修改已在报表服务器上部署的呈现扩展插件所使用的默认设备信息设置，必须在配置文件中键入 `DeviceInfo` XML 结构。</span><span class="sxs-lookup"><span data-stu-id="96337-135">To modify default device information settings that are used by a rendering extension that is already deployed on your report server, you must type the `DeviceInfo` XML structure into the configuration files.</span></span> <span data-ttu-id="96337-136">每个呈现扩展插件都支持对该扩展插件唯一的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="96337-136">Every rendering extension supports device information settings that are unique to that extension.</span></span> <span data-ttu-id="96337-137">若要查看设备信息设置的完整列表，请参阅 [将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="96337-137">To view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="96337-138">以下示例对用于修改图像呈现扩展插件的默认设置的 XML 结构和语法进行了说明：</span><span class="sxs-lookup"><span data-stu-id="96337-138">The following example provides an illustration of the XML structure and syntax that modifies the default settings of the Image rendering extension:</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="configuring-multiple-entries-for-a-rendering-extension"></a><span data-ttu-id="96337-139">为呈现扩展插件配置多个项</span><span class="sxs-lookup"><span data-stu-id="96337-139">Configuring Multiple Entries for a Rendering Extension</span></span>  
 <span data-ttu-id="96337-140">可以创建同一呈现扩展插件的多个实例，以支持不同的报表显示选项。</span><span class="sxs-lookup"><span data-stu-id="96337-140">You can create multiple instances of the same rendering extension to support different report presentation options.</span></span> <span data-ttu-id="96337-141">定义的每个实例都可以具有不同的参数值组合。</span><span class="sxs-lookup"><span data-stu-id="96337-141">Each instance that you define can have a different combination of parameter values.</span></span> <span data-ttu-id="96337-142">定义现有呈现扩展插件的新实例时，请确保执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="96337-142">When defining new instances of an existing rendering extension, be sure to do the following:</span></span>  
  
-   <span data-ttu-id="96337-143">为该扩展插件指定唯一名称。</span><span class="sxs-lookup"><span data-stu-id="96337-143">Specify a unique name for the extension.</span></span>  
  
     <span data-ttu-id="96337-144">每个实例都必须具有唯一的 `Name` 属性值。</span><span class="sxs-lookup"><span data-stu-id="96337-144">Each instance must have a unique value for the `Name` attribute.</span></span> <span data-ttu-id="96337-145">以下示例使用“IMAGE (EMF Landscape)”和“IMAGE (EMF Portrait)”名称来区分两个实例。</span><span class="sxs-lookup"><span data-stu-id="96337-145">The following example uses the names "IMAGE (EMF Landscape)" and "IMAGE (EMF Portrait)" to distinguish between the two instances.</span></span>  
  
     <span data-ttu-id="96337-146">更改已部署的呈现扩展插件的名称时要谨慎。</span><span class="sxs-lookup"><span data-stu-id="96337-146">Use caution when changing the name of a rendering extension that is already deployed.</span></span> <span data-ttu-id="96337-147">以编程方式指定呈现扩展插件的开发人员将使用扩展插件名称来标识要为某个特定的呈现操作使用哪一个实例。</span><span class="sxs-lookup"><span data-stu-id="96337-147">Developers who specify rendering extensions programmatically use the extension name to identify which instance to use for a particular render operation.</span></span> <span data-ttu-id="96337-148">如果在报表服务器上运行自定义 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 应用程序，请确保开发人员知道您是要修改现有扩展插件名称还是要添加新名称。</span><span class="sxs-lookup"><span data-stu-id="96337-148">If you are running custom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applications on your report server, make sure that the developer knows if you modify an existing extension name or add a new one.</span></span>  
  
-   <span data-ttu-id="96337-149">指定唯一的显示名称，以便用户了解输出格式之间的差异。</span><span class="sxs-lookup"><span data-stu-id="96337-149">Specify a unique display name so that users can understand the differences for each output format.</span></span>  
  
     <span data-ttu-id="96337-150">若要配置同一扩展插件的多个版本，可以通过为 `OverrideNames` 提供一个值来为每个版本提供唯一名称。</span><span class="sxs-lookup"><span data-stu-id="96337-150">If you are configuring multiple versions of the same extension, you can give each version a unique name by providing a value for `OverrideNames`.</span></span> <span data-ttu-id="96337-151">否则，该扩展插件的所有版本在报表工具栏上的“导出”选项列表中都具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="96337-151">Otherwise, all versions of the extension will appear to have the same name in the Export options list on the report toolbar.</span></span>  
  
 <span data-ttu-id="96337-152">以下示例阐释了当存在采用横向模式以 EMF 格式输出报表的第二个实例时，如何使用默认的图像呈现扩展插件（该插件生成 TIFF 输出）在纵向模式下输出 EMF。</span><span class="sxs-lookup"><span data-stu-id="96337-152">The following example illustrates how to use the default Image rendering extension (which produces TIFF output) to output EMF in Portrait mode alongside a second instance that outputs reports in EMF in Landscape mode.</span></span> <span data-ttu-id="96337-153">注意，每个扩展插件名称都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="96337-153">Notice that each extension name is unique.</span></span> <span data-ttu-id="96337-154">测试此示例时，请记住选择不包含交互式功能的报表，如显示/隐藏选项、矩阵或钻取链接（交互式功能在图像呈现扩展插件中不起作用）：</span><span class="sxs-lookup"><span data-stu-id="96337-154">When testing this example, remember to choose reports that do not contain interactive features such as show/hide options, matrices, or drillthrough links (interactive features do not work in the Image rendering extension):</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96337-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96337-155">See Also</span></span>  
 <span data-ttu-id="96337-156">[Rsreportserver.config 配置文件](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="96337-156">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="96337-157">[RSReportDesigner 配置文件](report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="96337-157">[RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="96337-158">[CSV 设备信息设置](csv-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="96337-158">[CSV Device Information Settings](csv-device-information-settings.md) </span></span>  
 <span data-ttu-id="96337-159">[Excel 设备信息设置](excel-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="96337-159">[Excel Device Information Settings](excel-device-information-settings.md) </span></span>  
 <span data-ttu-id="96337-160">[HTML 设备信息设置](html-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="96337-160">[HTML Device Information Settings](html-device-information-settings.md) </span></span>  
 <span data-ttu-id="96337-161">[图像设备信息设置](image-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="96337-161">[Image Device Information Settings](image-device-information-settings.md) </span></span>  
 <span data-ttu-id="96337-162">[MHTML 设备信息设置](mhtml-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="96337-162">[MHTML Device Information Settings](mhtml-device-information-settings.md) </span></span>  
 <span data-ttu-id="96337-163">[PDF 设备信息设置](pdf-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="96337-163">[PDF Device Information Settings](pdf-device-information-settings.md) </span></span>  
 [<span data-ttu-id="96337-164">XML 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="96337-164">XML Device Information Settings</span></span>](xml-device-information-settings.md)  
  
  
