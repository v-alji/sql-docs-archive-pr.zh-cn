---
title: URL 访问 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services]
- links [Reporting Services], URL access
- URL access [Reporting Services], about URL access
- parameters [Reporting Services], URL access
- report servers [Reporting Services], URL access
- hyperlinks [Reporting Services]
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf44ea3c15c12f37eebf6e89faf4ff3affd64433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580549"
---
# <a name="url-access-ssrs"></a><span data-ttu-id="29248-102">URL 访问 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="29248-102">URL Access (SSRS)</span></span>
  <span data-ttu-id="29248-103">通过 SQL Server Reporting Services (SSRS) 中报表服务器的 URL 访问，您可以通过 URL 请求将命令发送到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="29248-103">URL access of the report server in SQL Server Reporting Services (SSRS) enables you to send commands to a report server through a URL request.</span></span> <span data-ttu-id="29248-104">例如，您可以自定义报表在本机模式报表服务器上或 SharePoint 库中的呈现。</span><span class="sxs-lookup"><span data-stu-id="29248-104">For example, you can customize the rendering of a report on a native mode report server or in a SharePoint library.</span></span> <span data-ttu-id="29248-105">您可能已经使用了一组特定的报表参数值查看了报表，或者可能正在查看报表中感兴趣的特定页。</span><span class="sxs-lookup"><span data-stu-id="29248-105">You may have viewed the report using a specific set of report parameter values, or you may have been viewing a particular page of interest in the report.</span></span> <span data-ttu-id="29248-106">您可以使用预定义的 URL 访问参数在 URL 中封装这些信息。</span><span class="sxs-lookup"><span data-stu-id="29248-106">You can encapsulate this information in the URL using predefined URL access parameters.</span></span> <span data-ttu-id="29248-107">您可以通过为呈现格式嵌入参数，或者为报表查看器的外观嵌入参数，进一步自定义报表服务器处理报表的方式。</span><span class="sxs-lookup"><span data-stu-id="29248-107">You can further customize how the report server processes the report by embedding parameters for rendering formats or for the look and feel of the report viewer.</span></span> <span data-ttu-id="29248-108">然后，您可以将此 URL 直接粘贴到电子邮件或网页中，让他人在浏览器中采用相同的方式访问您的报表。</span><span class="sxs-lookup"><span data-stu-id="29248-108">You can then paste this URL directly into an email or Web page to let others to access your report in the same manner in the browser.</span></span>  
  
 <span data-ttu-id="29248-109">您可以通过 URL 访问执行的其他操作包括：</span><span class="sxs-lookup"><span data-stu-id="29248-109">Other actions you can perform through URL access are:</span></span>  
  
-   <span data-ttu-id="29248-110">将命令发送到 HTML 查看器，例如调整其外观</span><span class="sxs-lookup"><span data-stu-id="29248-110">Send commands to the HTML viewer, such as adjusting its look and feel</span></span>  
  
-   <span data-ttu-id="29248-111">列出目录文件夹的子级</span><span class="sxs-lookup"><span data-stu-id="29248-111">List the children of a catalog folder</span></span>  
  
-   <span data-ttu-id="29248-112">检索目录项的 XML 定义</span><span class="sxs-lookup"><span data-stu-id="29248-112">Retrieve the XML definition of a catalog item</span></span>  
  
-   <span data-ttu-id="29248-113">呈现特定的报表历史记录快照</span><span class="sxs-lookup"><span data-stu-id="29248-113">Render a specific report history snapshot</span></span>  
  
-   <span data-ttu-id="29248-114">管理报表会话</span><span class="sxs-lookup"><span data-stu-id="29248-114">Manage report sessions</span></span>  
  
 <span data-ttu-id="29248-115">有关可通过 URL 访问提供的命令和设置的完整列表，请参阅 [URL 访问参数引用](url-access-parameter-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="29248-115">For the complete list of commands and settings available through URL access, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="url-access-concepts"></a><span data-ttu-id="29248-116">URL 访问概念</span><span class="sxs-lookup"><span data-stu-id="29248-116">URL Access Concepts</span></span>  
 <span data-ttu-id="29248-117">对报表服务器的 URL 请求包含报表服务器处理的参数。</span><span class="sxs-lookup"><span data-stu-id="29248-117">URL requests to the report server contain parameters that are processed by the report server.</span></span> <span data-ttu-id="29248-118">报表服务器处理 URL 请求的方式取决于在 URL 中包括的参数、参数前缀和项的类型。</span><span class="sxs-lookup"><span data-stu-id="29248-118">The way in which the report server handles URL requests depends on the parameters, parameter prefixes, and types of items that are included in the URL.</span></span> <span data-ttu-id="29248-119">报表服务器 URL 符合万维网联合会 W3C/IETF 标准草案建议的 URL 格式准则。</span><span class="sxs-lookup"><span data-stu-id="29248-119">Report server URLs adhere to the URL formatting guidelines as proposed by the joint World Wide Web Consortium W3C/IETF draft standard.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="29248-120">URL 功能与支持标准 URL 寻址的大多数 Internet 浏览器或应用程序兼容。</span><span class="sxs-lookup"><span data-stu-id="29248-120">URL functionality is compatible with most Internet browsers or applications that support standard URL addressing.</span></span>  
  
### <a name="url-access-syntax"></a><span data-ttu-id="29248-121">URL 访问语法</span><span class="sxs-lookup"><span data-stu-id="29248-121">URL Access Syntax</span></span>  
 <span data-ttu-id="29248-122">URL 请求可包含以任何顺序列出的多个参数。</span><span class="sxs-lookup"><span data-stu-id="29248-122">URL requests can contain multiple parameters that are listed in any order.</span></span> <span data-ttu-id="29248-123">参数通过“与”符号 (&) 分隔开，名称/值对通过等号 (=) 分隔开。</span><span class="sxs-lookup"><span data-stu-id="29248-123">Parameters are separated by an ampersand (&) and name/value pairs are separated by an equal sign (=).</span></span>  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### <a name="syntax-description"></a><span data-ttu-id="29248-124">语法说明</span><span class="sxs-lookup"><span data-stu-id="29248-124">Syntax Description</span></span>  
 <span data-ttu-id="29248-125">*rswebserviceurl*</span><span class="sxs-lookup"><span data-stu-id="29248-125">*rswebserviceurl*</span></span>  
 <span data-ttu-id="29248-126">报表服务器的 Web 服务 URL。</span><span class="sxs-lookup"><span data-stu-id="29248-126">The Web service URL of the report server.</span></span> <span data-ttu-id="29248-127">对于本机模式，它是在 Reporting Services 配置管理器中配置的报表服务器实例的 Web 服务 URL（请参阅[配置报表服务器 URL（SSRS 配置管理器）](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)）。</span><span class="sxs-lookup"><span data-stu-id="29248-127">For native mode, it is the Web service URL of the report server instance configured in Reporting Services Configuration Manager (see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)).</span></span> <span data-ttu-id="29248-128">例如：</span><span class="sxs-lookup"><span data-stu-id="29248-128">For example:</span></span>  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 <span data-ttu-id="29248-129">对于 SharePoint 集成模式，它是位于与 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 集成的 SharePoint 站点处的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]代理的 URL。</span><span class="sxs-lookup"><span data-stu-id="29248-129">For SharePoint integrated mode, it is the URL of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxy at a SharePoint site integrated with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="29248-130">例如：</span><span class="sxs-lookup"><span data-stu-id="29248-130">For example:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  <span data-ttu-id="29248-131">非常重要的一点是，URL 包括用于通过 SharePoint 和 `_vti_bin` HTTP 代理路由请求的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 代理语法。</span><span class="sxs-lookup"><span data-stu-id="29248-131">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="29248-132">该代理会向 HTTP 请求中添加某一上下文，该上下文是确保为 SharePoint 模式报表服务器正确执行报表所需要的。</span><span class="sxs-lookup"><span data-stu-id="29248-132">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
 <span data-ttu-id="29248-133">*pathinfo*</span><span class="sxs-lookup"><span data-stu-id="29248-133">*pathinfo*</span></span>  
 <span data-ttu-id="29248-134">本机模式报表服务器数据库中该项的相对路径名称，或者是 SharePoint 目录中该项的完全限定 URL。</span><span class="sxs-lookup"><span data-stu-id="29248-134">The relative path name of the item in the native mode report server database, or the fully qualified URL of the item in a SharePoint catalog.</span></span>  
  
 <span data-ttu-id="29248-135">目录项的路径。</span><span class="sxs-lookup"><span data-stu-id="29248-135">The path of the catalog item.</span></span> <span data-ttu-id="29248-136">对于本机模式，它是报表服务器数据库中该项的相对路径，以斜杠 (`/`) 开头。</span><span class="sxs-lookup"><span data-stu-id="29248-136">For native mode, it is the relative path of the item in the report server database, beginning with a slash (`/`).</span></span> <span data-ttu-id="29248-137">例如：</span><span class="sxs-lookup"><span data-stu-id="29248-137">For example:</span></span>  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 <span data-ttu-id="29248-138">对于 SharePoint 集成模式，它是 SharePoint 库中的项的完全限定 URL，包括项扩展名。</span><span class="sxs-lookup"><span data-stu-id="29248-138">For SharePoint integrated mode, it is the fully qualified URL of the item in the SharePoint library, including the item extension.</span></span> <span data-ttu-id="29248-139">例如：</span><span class="sxs-lookup"><span data-stu-id="29248-139">For example:</span></span>  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 `&`  
 <span data-ttu-id="29248-140">用于分隔 URL 访问参数的名称和值对。</span><span class="sxs-lookup"><span data-stu-id="29248-140">Used to separate name and value pairs of URL access parameters.</span></span>  
  
 <span data-ttu-id="29248-141">**prefix**</span><span class="sxs-lookup"><span data-stu-id="29248-141">**prefix**</span></span>  
 <span data-ttu-id="29248-142">可选。</span><span class="sxs-lookup"><span data-stu-id="29248-142">Optional.</span></span> <span data-ttu-id="29248-143">访问在报表服务器内正运行的特定进程的 URL 访问参数的前缀（例如 `rs:` 或 `rc:`）。</span><span class="sxs-lookup"><span data-stu-id="29248-143">A prefix for the URL access parameter (for example, `rs:` or `rc:`) that accesses a specific process running within the report server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29248-144">如果不包括用于某一 URL 访问参数的前缀，则该参数将被报表服务器作为报表参数处理。</span><span class="sxs-lookup"><span data-stu-id="29248-144">If a prefix for a URL access parameter is not included, the parameter is processed by the report server as a report parameter.</span></span> <span data-ttu-id="29248-145">报表参数不使用参数前缀并且区分大小写。</span><span class="sxs-lookup"><span data-stu-id="29248-145">Report parameters do not use a parameter prefix and are case-sensitive.</span></span>  
  
 <span data-ttu-id="29248-146">**param**</span><span class="sxs-lookup"><span data-stu-id="29248-146">**param**</span></span>  
 <span data-ttu-id="29248-147">参数名称。</span><span class="sxs-lookup"><span data-stu-id="29248-147">The parameter name.</span></span>  
  
 <span data-ttu-id="29248-148">*value*</span><span class="sxs-lookup"><span data-stu-id="29248-148">*value*</span></span>  
 <span data-ttu-id="29248-149">与要使用的参数值相对应的 URL 文本。</span><span class="sxs-lookup"><span data-stu-id="29248-149">URL text corresponding to the value of the parameter being used.</span></span>  
  
 <span data-ttu-id="29248-150">**注意：** 有关可用 URL 访问参数的列表，请参阅 [URL Access Parameter Reference](url-access-parameter-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="29248-150">**Note:** For a list of the available URL access parameters, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span> <span data-ttu-id="29248-151">有关在 URL 中传递报表参数的示例，请参阅 [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="29248-151">For examples passing report parameters on the URL, see [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="29248-152">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="29248-152">Related Tasks</span></span>  
  
|<span data-ttu-id="29248-153">任务说明</span><span class="sxs-lookup"><span data-stu-id="29248-153">Task Descriptions</span></span>|<span data-ttu-id="29248-154">链接</span><span class="sxs-lookup"><span data-stu-id="29248-154">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="29248-155">访问报表服务器项，例如报表、共享数据源和资源。</span><span class="sxs-lookup"><span data-stu-id="29248-155">Access report server items, such as reports, shared data sources, and resources.</span></span>|[<span data-ttu-id="29248-156">使用 URL 访问来访问报表服务器项</span><span class="sxs-lookup"><span data-stu-id="29248-156">Access Report Server Items Using URL Access</span></span>](access-report-server-items-using-url-access.md)|  
|<span data-ttu-id="29248-157">将报表参数传递到报表。</span><span class="sxs-lookup"><span data-stu-id="29248-157">Pass report parameters to a report.</span></span>|[<span data-ttu-id="29248-158">在 URL 内传递报表参数</span><span class="sxs-lookup"><span data-stu-id="29248-158">Pass a Report Parameter Within a URL</span></span>](pass-a-report-parameter-within-a-url.md)|  
|<span data-ttu-id="29248-159">设置 URL 访问字符串中报表参数的区域设置，它定义日期、货币等特定于区域设置的解释。</span><span class="sxs-lookup"><span data-stu-id="29248-159">Set the locale of the report parameters in the URL access string, which defines the locale-specific interpretations of dates, currencies, and so on.</span></span>|[<span data-ttu-id="29248-160">设置 URL 中的报表语言参数</span><span class="sxs-lookup"><span data-stu-id="29248-160">Set the Language for Report Parameters in a URL</span></span>](set-the-language-for-report-parameters-in-a-url.md)|  
|<span data-ttu-id="29248-161">发送自定义报表呈现方式的报表扩展插件特定的设置。</span><span class="sxs-lookup"><span data-stu-id="29248-161">Send rendering extension specific settings that customize how the report is rendered.</span></span>|[<span data-ttu-id="29248-162">在 URL 中指定设备信息设置</span><span class="sxs-lookup"><span data-stu-id="29248-162">Specify Device Information Settings in a URL</span></span>](specify-device-information-settings-in-a-url.md)|  
|<span data-ttu-id="29248-163">将报表直接导出到某一文件格式而无需在浏览器中查看它。</span><span class="sxs-lookup"><span data-stu-id="29248-163">Export a report directly to a file format without viewing it in the browser.</span></span>|[<span data-ttu-id="29248-164">使用 URL 访问导出报表</span><span class="sxs-lookup"><span data-stu-id="29248-164">Export a Report Using URL Access</span></span>](export-a-report-using-url-access.md)|  
|<span data-ttu-id="29248-165">打开报表并且直接导航到某一字符串位置。</span><span class="sxs-lookup"><span data-stu-id="29248-165">Open a report and navigate directly to the location of a string.</span></span>|[<span data-ttu-id="29248-166">使用 URL 访问搜索报表</span><span class="sxs-lookup"><span data-stu-id="29248-166">Search a Report Using URL Access</span></span>](search-a-report-using-url-access.md)|  
|<span data-ttu-id="29248-167">呈现特定的报表历史记录快照。</span><span class="sxs-lookup"><span data-stu-id="29248-167">Render a specific report history snapshot.</span></span>|[<span data-ttu-id="29248-168">使用 URL 访问呈现报表历史记录快照</span><span class="sxs-lookup"><span data-stu-id="29248-168">Render a Report History Snapshot Using URL Access</span></span>](render-a-report-history-snapshot-using-url-access.md)|  
  
## <a name="see-also"></a><span data-ttu-id="29248-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29248-169">See Also</span></span>  
 <span data-ttu-id="29248-170">[Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md) </span><span class="sxs-lookup"><span data-stu-id="29248-170">[Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md) </span></span>  
 <span data-ttu-id="29248-171">[URL 访问参数引用](url-access-parameter-reference.md) </span><span class="sxs-lookup"><span data-stu-id="29248-171">[URL Access Parameter Reference](url-access-parameter-reference.md) </span></span>  
 <span data-ttu-id="29248-172">[使用 URL 访问集成 Reporting Services](application-integration/integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="29248-172">[Integrating Reporting Services Using URL Access](application-integration/integrating-reporting-services-using-url-access.md) </span></span>  
 [<span data-ttu-id="29248-173">查找、查看和管理报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="29248-173">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
