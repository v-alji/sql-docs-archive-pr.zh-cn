---
title: 实现 IRenderingExtension 接口 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f57c4aa41ccfed165b69581cbf3917e4dfbb4960
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587229"
---
# <a name="implementing-the-irenderingextension-interface"></a><span data-ttu-id="b99ee-102">实现 IRenderingExtension 接口</span><span class="sxs-lookup"><span data-stu-id="b99ee-102">Implementing the IRenderingExtension Interface</span></span>
  <span data-ttu-id="b99ee-103">呈现扩展插件从与实际数据相结合的报表定义中获取结果，并将得到的数据呈现为某种可用的格式。</span><span class="sxs-lookup"><span data-stu-id="b99ee-103">The rendering extension takes the results from a report definition that is combined with the actual data and renders the resulting data to a format that is useable.</span></span> <span data-ttu-id="b99ee-104">组合的数据和格式的转换是通过一个实现 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 的公共语言运行时 (CLR) 类完成的。</span><span class="sxs-lookup"><span data-stu-id="b99ee-104">The transformation of the combined data and formatting is done by using a common language runtime (CLR) class that implements <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>.</span></span> <span data-ttu-id="b99ee-105">该类将对象模型转换为可由查看器、打印机或其他输出目标使用的输出格式。</span><span class="sxs-lookup"><span data-stu-id="b99ee-105">This transforms the object model into an output format that is consumable by a viewer, printer, or other output target.</span></span>  
  
 <span data-ttu-id="b99ee-106"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 具有三个必须进行编码的方法：</span><span class="sxs-lookup"><span data-stu-id="b99ee-106">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> has three methods that must be coded:</span></span>  
  
-   <span data-ttu-id="b99ee-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> - 呈现报表。</span><span class="sxs-lookup"><span data-stu-id="b99ee-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> - renders the report.</span></span>  
  
-   <span data-ttu-id="b99ee-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> - 呈现报表中特定的流。</span><span class="sxs-lookup"><span data-stu-id="b99ee-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> - renders a specific stream from the report.</span></span>  
  
-   <span data-ttu-id="b99ee-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> - 获取报表所需的其他信息，如图标。</span><span class="sxs-lookup"><span data-stu-id="b99ee-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> - gets additional information, such as icons, that are required for the report.</span></span>  
  
 <span data-ttu-id="b99ee-110">下列各节更为详细地讨论这些方法。</span><span class="sxs-lookup"><span data-stu-id="b99ee-110">The following sections discuss these methods in more detail.</span></span>  
  
## <a name="render-method"></a><span data-ttu-id="b99ee-111">Render 方法</span><span class="sxs-lookup"><span data-stu-id="b99ee-111">Render Method</span></span>  
 <span data-ttu-id="b99ee-112"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 方法包含表示以下对象的参数：</span><span class="sxs-lookup"><span data-stu-id="b99ee-112">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> method contains arguments that represent the following objects:</span></span>  
  
-   <span data-ttu-id="b99ee-113">要呈现的 report 本身  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-113">The *report* that you want to render.</span></span> <span data-ttu-id="b99ee-114">此对象包含报表的属性、数据和布局信息。</span><span class="sxs-lookup"><span data-stu-id="b99ee-114">This object contains properties, data, and layout information for the report.</span></span> <span data-ttu-id="b99ee-115">report 是报表对象模型树的根。</span><span class="sxs-lookup"><span data-stu-id="b99ee-115">The report is the root of the report object model tree.</span></span>  
  
-   <span data-ttu-id="b99ee-116">ServerParameters，包含字符串字典对象以及用于报表服务器的参数（如果有）  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-116">The *ServerParameters* that contain the string dictionary object, with the parameters for the report server, if any.</span></span>  
  
-   <span data-ttu-id="b99ee-117">deviceInfo 参数，其中包含设备设置  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-117">The *deviceInfo* parameter that contain the device settings.</span></span> <span data-ttu-id="b99ee-118">有关详细信息，请参阅[将设备信息设置传递给呈现扩展插件](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="b99ee-118">For more information, see [Passing Device Information Settings to Rendering Extensions](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
-   <span data-ttu-id="b99ee-119">clientCapabilities 参数，其中包含 <xref:System.Collections.Specialized.NameValueCollection> 字典对象，此字典对象具有与要向其呈现的客户端的信息。</span><span class="sxs-lookup"><span data-stu-id="b99ee-119">The *clientCapabilities* parameter that contains a <xref:System.Collections.Specialized.NameValueCollection> dictionary object that has information about the client to which you are rendering.</span></span>  
  
-   <span data-ttu-id="b99ee-120">RenderProperties，其中包含有关呈现结果的信息  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-120">The *RenderProperties* that contains information about the rendering result.</span></span>  
  
-   <span data-ttu-id="b99ee-121">createAndRegisterStream 是一个委托函数，可以调用它来获取要呈现到的流  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-121">The *createAndRegisterStream* is a delegate function to be called to get a stream to render into.</span></span>  
  
### <a name="deviceinfo-parameter"></a><span data-ttu-id="b99ee-122">deviceInfo 参数</span><span class="sxs-lookup"><span data-stu-id="b99ee-122">deviceInfo Parameter</span></span>  
 <span data-ttu-id="b99ee-123">deviceInfo 参数包含呈现参数，而不包含报表参数  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-123">The *deviceInfo* parameter contains rendering parameters, not report parameters.</span></span> <span data-ttu-id="b99ee-124">这些呈现参数将传递给呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="b99ee-124">These rendering parameters are passed to the rendering extension.</span></span> <span data-ttu-id="b99ee-125">报表服务器会将 deviceInfo 值转换为一个 <xref:System.Collections.Specialized.NameValueCollection> 对象。</span><span class="sxs-lookup"><span data-stu-id="b99ee-125">The *deviceInfo* values are converted into a <xref:System.Collections.Specialized.NameValueCollection> object by the report server.</span></span> <span data-ttu-id="b99ee-126">deviceInfo 参数中的项被视为区分大小写的值  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-126">Items in the *deviceInfo* parameter are treated as case-insensitive values.</span></span> <span data-ttu-id="b99ee-127">如果作为 URL 访问的结果提出呈现请求，则格式为 `rc:key=value` 的 URL 参数将转换为 deviceInfo 字段对象中的键/值对  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-127">If the render request came as a result of URL access, the URL parameters in the form `rc:key=value` are converted to key/value pairs in the *deviceInfo* dictionary object.</span></span> <span data-ttu-id="b99ee-128">浏览器检测代码还在 clientCapabilities 字典中提供以下各项：EcmaScriptVersion、JavaScript、MajorVersion、MinorVersion、Win32、Type 以及 AcceptLanguage  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-128">The browser detection code also provides the following items in the *clientCapabilities* dictionary: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type, and AcceptLanguage.</span></span> <span data-ttu-id="b99ee-129">将忽略 deviceInfo 中呈现扩展插件不理解的任何名称/值对  。</span><span class="sxs-lookup"><span data-stu-id="b99ee-129">Any name/value pair in the *deviceInfo* parameter that is not understood by the rendering extension is ignored.</span></span> <span data-ttu-id="b99ee-130">以下代码示例显示用于检索图标的示例 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="b99ee-130">The following code sample shows a sample <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method that retrieves icons:</span></span>  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a><span data-ttu-id="b99ee-131">RenderStream 方法</span><span class="sxs-lookup"><span data-stu-id="b99ee-131">RenderStream Method</span></span>  
 <span data-ttu-id="b99ee-132"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> 方法呈现报表中的特定流。</span><span class="sxs-lookup"><span data-stu-id="b99ee-132">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> method renders a particular stream from the report.</span></span> <span data-ttu-id="b99ee-133">所有流都是在初始 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 调用过程中创建的，但最初不向客户端返回这些流。</span><span class="sxs-lookup"><span data-stu-id="b99ee-133">All streams are created during the initial <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> call, but the streams are not returned to the client initially.</span></span> <span data-ttu-id="b99ee-134">此方法用于辅助流（如 HTML 呈现中的图像）或多页呈现扩展插件的其他页（如图像/EMF）。</span><span class="sxs-lookup"><span data-stu-id="b99ee-134">This method is used for secondary streams, such as images in HTML rendering, or additional pages of a multi-page rendering extension, such as Image/EMF.</span></span>  
  
## <a name="getrenderingresource-method"></a><span data-ttu-id="b99ee-135">GetRenderingResource 方法</span><span class="sxs-lookup"><span data-stu-id="b99ee-135">GetRenderingResource Method</span></span>  
 <span data-ttu-id="b99ee-136"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 方法检索信息而不执行报表的完整呈现。</span><span class="sxs-lookup"><span data-stu-id="b99ee-136">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method retrieves the information without executing an entire rendering of the report.</span></span> <span data-ttu-id="b99ee-137">有时，报表所需的信息并不要求呈现此报表本身。</span><span class="sxs-lookup"><span data-stu-id="b99ee-137">There are times when the report requires information that does not require the report itself to be rendered.</span></span> <span data-ttu-id="b99ee-138">例如，如果需要与呈现扩展插件关联的图标，请使用包含单个标记的*deviceInfo*参数 **\<Icon>** 。</span><span class="sxs-lookup"><span data-stu-id="b99ee-138">For example, if you need the icon associated with the rendering extension, use the *deviceInfo* parameter containing the single tag **\<Icon>**.</span></span> <span data-ttu-id="b99ee-139">在此类情况下，可以使用 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b99ee-139">In these cases, you can use the <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99ee-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b99ee-140">See Also</span></span>  
 <span data-ttu-id="b99ee-141">[实现呈现扩展插件](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="b99ee-141">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 [<span data-ttu-id="b99ee-142">呈现扩展插件概述</span><span class="sxs-lookup"><span data-stu-id="b99ee-142">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
  
  
