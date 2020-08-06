---
title: 在 Web 应用程序中使用 URL 访问 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd31f76658f8160cbb2a576debc335588f77e72c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576545"
---
# <a name="using-url-access-in-a-web-application"></a><span data-ttu-id="93753-102">在 Web 应用程序中使用 URL 访问</span><span class="sxs-lookup"><span data-stu-id="93753-102">Using URL Access in a Web Application</span></span>
  <span data-ttu-id="93753-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 URL 访问是为实现通过网络访问单独报表而专门设计的。</span><span class="sxs-lookup"><span data-stu-id="93753-103">URL access in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is specifically designed to enable access to individual reports over a network.</span></span> <span data-ttu-id="93753-104">此类型的访问最适合于将报表查看和导航集成到自定义 Web 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="93753-104">This type of access is best for integrating report viewing and navigation into a custom Web application.</span></span> <span data-ttu-id="93753-105">为了在 Web 应用程序中使用 URL 访问，您可以：</span><span class="sxs-lookup"><span data-stu-id="93753-105">To use URL access in Web applications, you can:</span></span>  
  
-   <span data-ttu-id="93753-106">将 URL 从某一网站或门户寻址到特定的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="93753-106">Address a URL to a specific report server from a Web site or portal.</span></span>  
  
-   <span data-ttu-id="93753-107">使用窗体 POST 方法并使用窗体字段将查询字符串参数传递到报表服务器 URL。</span><span class="sxs-lookup"><span data-stu-id="93753-107">Use a form POST method and pass query string parameters to a report server URL using form fields.</span></span>  
  
## <a name="url-access-through-direct-addressing"></a><span data-ttu-id="93753-108">通过直接寻址进行 URL 访问</span><span class="sxs-lookup"><span data-stu-id="93753-108">URL Access Through Direct Addressing</span></span>  
 <span data-ttu-id="93753-109">若要使用某一 URL 访问某个报表服务器或报表服务器数据库项，只需从某一 Web 浏览器或应用程序内提供该 URL 地址。</span><span class="sxs-lookup"><span data-stu-id="93753-109">To access a report server or report server database item using a URL, simply provide the URL address from within a Web browser or application.</span></span> <span data-ttu-id="93753-110">还可以向 URL 提供可能影响所访问的报表或资源的外观的参数。</span><span class="sxs-lookup"><span data-stu-id="93753-110">You can also supply parameters to the URL that can affect the appearance of the report or resource that is being accessed.</span></span> <span data-ttu-id="93753-111">URL 可以通过 Web 浏览器的地址栏以某一报表服务器为目标，或者 URL 可以是作为更大的 Web 应用程序或门户的一部分的 IFrame 的来源\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="93753-111">A URL can target a report server through the address bar of a Web browser, or a URL can be the source of an **IFrame** that is part of a larger Web application or portal.</span></span> <span data-ttu-id="93753-112">您可以在门户的不同网页上包括指向报表的超链接，以及以报表的特定框架为目标或在这一过程中打开新的浏览器窗口。</span><span class="sxs-lookup"><span data-stu-id="93753-112">You can include hyperlinks to reports on various Web pages of your portal, as well as target a specific frame for the report or open a new browser window in the process.</span></span>  
  
 <span data-ttu-id="93753-113">在以下示例中，超链接以名为“main”的框架为目标，该框架可能不同于包括该超链接的框架。</span><span class="sxs-lookup"><span data-stu-id="93753-113">In the following example, the hyperlink targets a frame named "main", which might be different from the one that includes the hyperlink.</span></span> <span data-ttu-id="93753-114">该超链接可能是 Web 门户的一部分。</span><span class="sxs-lookup"><span data-stu-id="93753-114">The hyperlink might be part of Web portal.</span></span>  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 <span data-ttu-id="93753-115">在上例中，设备信息设置 LinkTarget 与值“main”一起传递到 URL 的查询字符串中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="93753-115">In the previous example, the device information setting **LinkTarget** is passed with a value of "main" in the query string of the URL.</span></span> <span data-ttu-id="93753-116">这确保报表中的所有钻取超链接也以名为“main”的框架为目标。</span><span class="sxs-lookup"><span data-stu-id="93753-116">This ensures that any drillthrough hyperlinks in the report also target the frame named "main".</span></span>  
  
 <span data-ttu-id="93753-117">有关设备信息设置的详细信息，请参阅[将设备信息设置传递给呈现扩展插件](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="93753-117">For more information about device information settings, see [Passing Device Information Settings to Rendering Extensions](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="93753-118">请注意，许多服务器和浏览器都限制 URL 中允许的字符数。</span><span class="sxs-lookup"><span data-stu-id="93753-118">Note that many servers and browsers limit the number of characters allowed in a URL.</span></span> <span data-ttu-id="93753-119">在某些情况下，这一限制是 256 字符。</span><span class="sxs-lookup"><span data-stu-id="93753-119">In some cases, a 256-character limit is imposed.</span></span> <span data-ttu-id="93753-120">若要避免这一限制，可通过窗体提交使用 POST 请求。</span><span class="sxs-lookup"><span data-stu-id="93753-120">To get around this limitation, you can use POST requests using form submission.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93753-121">Internet Explorer 具有 2,083 个字符的最大 URL 长度。</span><span class="sxs-lookup"><span data-stu-id="93753-121">Internet Explorer has a maximum URL length of 2,083 characters.</span></span> <span data-ttu-id="93753-122">这一限制应用于 POST 和 GET 请求 URL。</span><span class="sxs-lookup"><span data-stu-id="93753-122">This limit applies to both POST and GET request URLs.</span></span> <span data-ttu-id="93753-123">但是，POST 不受将名称/值对作为窗体的一部分提交的 URL 大小的限制，因为它们在标头中传输，而非在 URL 中传输。</span><span class="sxs-lookup"><span data-stu-id="93753-123">POST, however, is not limited by the size of the URL for submitting name/value pairs as part of a form, because they are transferred in the header and not the URL.</span></span>  
  
## <a name="url-access-through-a-form-post-method"></a><span data-ttu-id="93753-124">通过窗体 POST 方法的 URL 访问</span><span class="sxs-lookup"><span data-stu-id="93753-124">URL Access Through a Form POST Method</span></span>  
 <span data-ttu-id="93753-125">在某一用户使用 URL 访问从报表服务器请求数据时，该 HTTP 请求使用 GET 方法。</span><span class="sxs-lookup"><span data-stu-id="93753-125">When a user requests data from a report server using URL access, the HTTP request uses the GET method.</span></span> <span data-ttu-id="93753-126">这等效于 METHOD="GET" 的窗体提交。</span><span class="sxs-lookup"><span data-stu-id="93753-126">This is equivalent to a form submission where METHOD="GET".</span></span> <span data-ttu-id="93753-127">使用 METHOD="GET" 的 URL 请求或窗体提交受到服务器或 Web 浏览器可处理的最大字符数的限制。</span><span class="sxs-lookup"><span data-stu-id="93753-127">URL requests or form submissions that use METHOD="GET" are limited by the maximum number of characters that a server or Web browser can process.</span></span>  
  
 <span data-ttu-id="93753-128">对于 POST 请求（METHOD="POST" 和输入字段），名称/值对在标头中传输，而非在 URL 中传输。</span><span class="sxs-lookup"><span data-stu-id="93753-128">With POST requests (METHOD="POST" and input fields), the name/value pairs are transferred in the header and not the URL.</span></span> <span data-ttu-id="93753-129">因此，查询字符串的名称/值对不是 URL 的一部分，这使您可以提供长得多和更复杂的参数列表。</span><span class="sxs-lookup"><span data-stu-id="93753-129">Therefore, the name/value pairs of the query string are not part of the URL, thus enabling you to provide much longer and more complex parameter lists.</span></span>  
  
 <span data-ttu-id="93753-130">使用直接访问，用户可以看到报表服务器的 URL，并且可能能够修改查询字符串，或者能够记录特定 URL 请求和报表服务器参数以供以后使用。</span><span class="sxs-lookup"><span data-stu-id="93753-130">Using direct access, a user can see the URL for the report server, and may be able to modify the  query string or note the particular URL request and report server parameters for later use.</span></span>  
  
 <span data-ttu-id="93753-131">以下 HTML 示例以某一窗体为例，阐释如何使用该窗体将具有特定 URL 的报表服务器为目标并将查询字符串参数作为该窗体的输入字段的一部分传递。</span><span class="sxs-lookup"><span data-stu-id="93753-131">The following sample HTML demonstrates the use of a form that you can use to target a report server with a specific URL and pass query string parameters as part of the form's input fields.</span></span>  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 <span data-ttu-id="93753-132">在前一示例中，如果某一用户单击该窗体上的按钮，则报表服务器返回以当前框架为目标的 HTML 呈现的报表。</span><span class="sxs-lookup"><span data-stu-id="93753-132">In the previous example, if a user clicks the button on the form, the report server returns an HTML-rendered report targeted at the current frame.</span></span> <span data-ttu-id="93753-133">类似的 URL 访问字符串如下：</span><span class="sxs-lookup"><span data-stu-id="93753-133">A comparable URL access string might look like the following:</span></span>  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a><span data-ttu-id="93753-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93753-134">See Also</span></span>  
 <span data-ttu-id="93753-135">[将 Reporting Services 集成到应用程序中](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="93753-135">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="93753-136">[使用 URL 访问集成 Reporting Services](integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="93753-136">[Integrating Reporting Services Using URL Access](integrating-reporting-services-using-url-access.md) </span></span>  
 <span data-ttu-id="93753-137">[在 Windows 应用程序中使用 URL 访问](integrating-reporting-services-using-url-access-windows-application.md) </span><span class="sxs-lookup"><span data-stu-id="93753-137">[Using URL Access in a Windows Application](integrating-reporting-services-using-url-access-windows-application.md) </span></span>  
 [<span data-ttu-id="93753-138">URL 访问 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="93753-138">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
