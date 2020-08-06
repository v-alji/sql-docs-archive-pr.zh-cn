---
title: 将设备信息设置传递给呈现扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea50de3955ab152cbd92d5fd50ef8b2281a67eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688532"
---
# <a name="passing-device-information-settings-to-rendering-extensions"></a><span data-ttu-id="73832-102">将设备信息设置传递给呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="73832-102">Passing Device Information Settings to Rendering Extensions</span></span>
  <span data-ttu-id="73832-103">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]中，设备信息设置用于将呈现参数传递到呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="73832-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="73832-104">报表服务器 Web 服务中的设置将以 **DeviceInfo** XML 元素的形式传递并由报表服务器进行处理。</span><span class="sxs-lookup"><span data-stu-id="73832-104">Settings in the Report Server Web service are passed as a **DeviceInfo** XML element and processed by the report server.</span></span> <span data-ttu-id="73832-105">由于设备信息设置均具有默认值，因此在呈现进程中可将其视为可选参数。</span><span class="sxs-lookup"><span data-stu-id="73832-105">Because device information settings have default values, they are considered optional arguments in the rendering process.</span></span> <span data-ttu-id="73832-106">但是，您可以使用设备信息设置对呈现进行自定义并覆盖由服务器提供的默认值。</span><span class="sxs-lookup"><span data-stu-id="73832-106">However, you can use device information settings to customize rendering and to override the default values that are supplied by the server.</span></span>  
  
 <span data-ttu-id="73832-107">可以用多种方式指定设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="73832-107">You can specify device information settings in a variety of ways.</span></span> <span data-ttu-id="73832-108">可以通过编程方式使用 Render 方法。</span><span class="sxs-lookup"><span data-stu-id="73832-108">Programmatically, you can use the Render method.</span></span> <span data-ttu-id="73832-109">如果要通过报表的 URL 访问报表，则可以指定设备信息作为 URL 参数。</span><span class="sxs-lookup"><span data-stu-id="73832-109">If you are accessing a report through its URL, you can specify device information as URL parameters.</span></span> <span data-ttu-id="73832-110">还可以在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配置文件中编辑设备信息设置，以指定全局呈现参数。</span><span class="sxs-lookup"><span data-stu-id="73832-110">You can also edit the device information settings in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files to specify rendering parameters globally.</span></span> <span data-ttu-id="73832-111">有关全局指定呈现参数的详细信息，请参阅[在 RSReportServer.Config 中自定义呈现扩展插件参数](../../customize-rendering-extension-parameters-in-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="73832-111">For more information about specifying rendering parameters globally, see [Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md).</span></span>  
  
## <a name="passing-device-information-using-the-render-method"></a><span data-ttu-id="73832-112">使用 Render 方法传递设备信息</span><span class="sxs-lookup"><span data-stu-id="73832-112">Passing Device Information Using the Render Method</span></span>  
 <span data-ttu-id="73832-113">若要将设备信息设置传递给呈现扩展插件，请使用 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="73832-113">To pass device information settings to a rendering extension, use the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="73832-114">例如，当以 HTML 格式呈现时，可将以下 XML 字符串传递到 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法以创建一个 HTML 段落。</span><span class="sxs-lookup"><span data-stu-id="73832-114">For example, the following XML string can be passed to the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to create an HTML fragment when rendering to HTML.</span></span>  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 <span data-ttu-id="73832-115">当报表作为 HTML 段落呈现时，报表的内容包含在 TABLE 元素内，而不使用 HTML 或 BODY 元素。</span><span class="sxs-lookup"><span data-stu-id="73832-115">When a report is rendered as an HTML fragment, the content of the report is contained within a TABLE element without the use of an HTML or BODY element.</span></span> <span data-ttu-id="73832-116">可以使用 HTML 段落将报表并入现有 HTML 文档中。</span><span class="sxs-lookup"><span data-stu-id="73832-116">You can use the HTML fragment to incorporate the report into an existing HTML document.</span></span> <span data-ttu-id="73832-117">有关 HTML 输出的设备信息设置的详细信息，请参阅 [HTML 设备信息设置](../../html-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="73832-117">For more information about device information settings for HTML output, see [HTML Device Information Settings](../../html-device-information-settings.md).</span></span>  
  
## <a name="passing-device-information-using-url-access"></a><span data-ttu-id="73832-118">使用 URL 访问传递设备信息</span><span class="sxs-lookup"><span data-stu-id="73832-118">Passing Device Information Using URL Access</span></span>  
 <span data-ttu-id="73832-119">您也可以通过 URL 访问传递设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="73832-119">You can also pass device information settings through URL access.</span></span> <span data-ttu-id="73832-120">设备信息设置以 URL 参数的形式传递。</span><span class="sxs-lookup"><span data-stu-id="73832-120">Device information settings are passed as URL parameters.</span></span> <span data-ttu-id="73832-121">可以将以下 URL 访问字符串传递到报表服务器以生成不带 HTML 查看器工具栏的所呈现报表。</span><span class="sxs-lookup"><span data-stu-id="73832-121">The following URL access string can be passed to the report server to generate a rendered report without the HTML viewer toolbar.</span></span>  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 <span data-ttu-id="73832-122">有关详细信息，请参阅[在 URL 中指定设备信息设置](../../specify-device-information-settings-in-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="73832-122">For more information, see [Specify Device Information Settings in a URL](../../specify-device-information-settings-in-a-url.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73832-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73832-123">See Also</span></span>  
 <span data-ttu-id="73832-124">[呈现扩展插件的设备信息设置 &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="73832-124">[Device Information Settings for Rendering Extensions &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span></span>  
 <span data-ttu-id="73832-125">[在 RSReportServer.Config中自定义呈现扩展插件参数](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="73832-125">[Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="73832-126">使用 Web 服务和 .NET Framework 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="73832-126">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
