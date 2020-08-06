---
title: 以 HTML 格式呈现（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf559b0a-499a-4d74-b520-b382b87e0b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44f43d079aa81b566a39fe053bdf80c7800fc500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579514"
---
# <a name="rendering-to-html-report-builder-and-ssrs"></a><span data-ttu-id="a031a-102">以 HTML 格式呈现（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a031a-102">Rendering to HTML (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a031a-103">HTML 呈现扩展插件以 HTML 格式呈现报表。</span><span class="sxs-lookup"><span data-stu-id="a031a-103">The HTML rendering extension renders a report in HTML format.</span></span> <span data-ttu-id="a031a-104">该呈现扩展插件还可以生成完整的 HTML 页面，或生成 HTML 片段以嵌入其他 HTML 页面。</span><span class="sxs-lookup"><span data-stu-id="a031a-104">The rendering extension can also produce fully formed HTML pages or fragments of HTML to embed in other HTML pages.</span></span> <span data-ttu-id="a031a-105">所有 HTML 都是使用 UTF-8 编码生成的。</span><span class="sxs-lookup"><span data-stu-id="a031a-105">All HTML is generated with UTF-8 encoding.</span></span>  
  
 <span data-ttu-id="a031a-106">在浏览器中查看报表时，包括报表在报表管理器中运行时，HTML 呈现扩展插件都是默认的呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="a031a-106">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span>  
  
 <span data-ttu-id="a031a-107">在浏览器中查看报表时，包括报表在报表管理器中运行时，HTML 呈现扩展插件都是默认的呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="a031a-107">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span> <span data-ttu-id="a031a-108">HTML 呈现扩展插件可以将 HTML 呈现为片段或完整的 HTML 文档。</span><span class="sxs-lookup"><span data-stu-id="a031a-108">The HTML rendering extension can render HTML as a fragment or as a full HTML document.</span></span> <span data-ttu-id="a031a-109">如果 HTML 为片断形式，则会删除 HTML 文档的 `HEAD`、`HTML` 和 `BODY` 标记。</span><span class="sxs-lookup"><span data-stu-id="a031a-109">If the HTML is a fragment, the `HEAD`, `HTML`, and `BODY` tags of the HTML document are removed.</span></span> <span data-ttu-id="a031a-110">只有 `BODY` 标记的内容才会呈现。</span><span class="sxs-lookup"><span data-stu-id="a031a-110">Only the contents of the `BODY` tag are rendered.</span></span> <span data-ttu-id="a031a-111">这在将此 HTML 片段嵌入其他应用程序生成的 HTML 时颇为有用。</span><span class="sxs-lookup"><span data-stu-id="a031a-111">This is useful for embedding the HTML in the HTML produced by another application.</span></span>  
  
 <span data-ttu-id="a031a-112">在某些情况下，以 HTML 格式呈现报表时，报表参数可用于发起脚本注入攻击。</span><span class="sxs-lookup"><span data-stu-id="a031a-112">In some scenarios, report parameters can be used to launch script injection attacks when rendering reports to HTML.</span></span> <span data-ttu-id="a031a-113">有关保护报表的详细信息，请参阅 [保护报表和资源](../security/secure-reports-and-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="a031a-113">For more information about securing reports, see [Secure Reports and Resources](../security/secure-reports-and-resources.md).</span></span>  
  
 <span data-ttu-id="a031a-114">有关浏览器的详细信息，请参阅[规划 Reporting Services 和 Power View 浏览器支持 &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a031a-114">For more information about browsers, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rendering-in-mhtml"></a><a name="RenderingMHTML"></a><span data-ttu-id="a031a-115">以 MHTML 格式呈现</span><span class="sxs-lookup"><span data-stu-id="a031a-115">Rendering in MHTML</span></span>  
 <span data-ttu-id="a031a-116">HTML 呈现扩展插件还可以将报表呈现为 MHTML 格式（聚合 HTML 文档的 MIME 封装）。</span><span class="sxs-lookup"><span data-stu-id="a031a-116">The HTML rendering extension can also render reports in MHTML (MIME Encapsulation of Aggregate HTML Documents).</span></span> <span data-ttu-id="a031a-117">MHTML 扩展了 HTML 以实现在 HTML 文档中嵌入图像等编码对象。</span><span class="sxs-lookup"><span data-stu-id="a031a-117">MHTML extends HTML to embed encoded objects, such as images, in the HTML document.</span></span> <span data-ttu-id="a031a-118">使用 MHTML 呈现扩展插件后，可将图像、文档或其他二进制文件等资源作为报表 HTML 内的 MIME 结构嵌入单个文件中。</span><span class="sxs-lookup"><span data-stu-id="a031a-118">Using the MHTML rendering extension, you can embed resources such as images, documents, or other binary files as MIME structures within the report HTML, into a single file.</span></span> <span data-ttu-id="a031a-119">MHTML 报表也可用于嵌入到电子邮件中，因为所有资源都包含在报表中。</span><span class="sxs-lookup"><span data-stu-id="a031a-119">MHTML reports are also useful for embedding within e-mail messages because all resources are included with the report.</span></span> <span data-ttu-id="a031a-120">虽然实际上呈现 MHTML 的是 HTML 呈现扩展插件，但此功能也可称为 MHTML 呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="a031a-120">Although it is actually the HTML rendering extension that renders MHTML, this functionality may also be referred to as the MHTML rendering extension.</span></span>  
  
##  <a name="browser-support"></a><a name="BrowserSupport"></a><span data-ttu-id="a031a-121">浏览器支持</span><span class="sxs-lookup"><span data-stu-id="a031a-121">Browser Support</span></span>  
 <span data-ttu-id="a031a-122">此呈现扩展插件支持以下浏览器版本：</span><span class="sxs-lookup"><span data-stu-id="a031a-122">This rendering extension supports the following browser versions:</span></span>  
  
-   <span data-ttu-id="a031a-123">Internet Explorer 5.5 和更高版本</span><span class="sxs-lookup"><span data-stu-id="a031a-123">Internet Explorer 5.5 and later</span></span>  
  
-   <span data-ttu-id="a031a-124">FireFox 1.5 和更高版本</span><span class="sxs-lookup"><span data-stu-id="a031a-124">Firefox 1.5 and later</span></span>  
  
-   <span data-ttu-id="a031a-125">Safari 3.0 和更高版本</span><span class="sxs-lookup"><span data-stu-id="a031a-125">Safari 3.0 and later</span></span>  
  
 <span data-ttu-id="a031a-126">出于跨浏览器的考虑，呈现的报表可能因浏览器的不同而稍有差别。</span><span class="sxs-lookup"><span data-stu-id="a031a-126">Due to cross browser considerations, the rendered report may vary slightly from browser to browser.</span></span> <span data-ttu-id="a031a-127">例如，文本框包含名为 WritingMode 的属性。</span><span class="sxs-lookup"><span data-stu-id="a031a-127">For example, the text box contains a property called WritingMode.</span></span> <span data-ttu-id="a031a-128">Firefox 不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="a031a-128">This property is not supported in Firefox.</span></span>  
  
##  <a name="html-specific-rendering-rules"></a><a name="HTMLSpecificRenderingRules"></a> <span data-ttu-id="a031a-129">特定于 HTML 的呈现规则</span><span class="sxs-lookup"><span data-stu-id="a031a-129">HTML-Specific Rendering Rules</span></span>  
 <span data-ttu-id="a031a-130">呈现时将应用下列特定于 HTML 的规则：</span><span class="sxs-lookup"><span data-stu-id="a031a-130">The following HTML-specific rules are applied when rendering:</span></span>  
  
-   <span data-ttu-id="a031a-131">呈现器生成一个 HTML 表结构，以包含每个 `ReportItems` 集合（如果存在多个集合）中的所有项。</span><span class="sxs-lookup"><span data-stu-id="a031a-131">The renderer builds an HTML table structure to contain all of the items in each `ReportItems` collection, if there is more than one.</span></span>  
  
-   <span data-ttu-id="a031a-132">表结构中的每一项都占用一个单元。</span><span class="sxs-lookup"><span data-stu-id="a031a-132">Every item within the table structure occupies a single cell.</span></span>  
  
-   <span data-ttu-id="a031a-133">空单元会尽可能折叠在一起以减少 HTML 的大小。</span><span class="sxs-lookup"><span data-stu-id="a031a-133">Empty cells are collapsed together as much as possible to reduce the size of the HTML.</span></span>  
  
-   <span data-ttu-id="a031a-134">会向上边缘添加一行空单元并向左边缘添加一列空单元以提高浏览器呈现表的速度。</span><span class="sxs-lookup"><span data-stu-id="a031a-134">A row of empty cells is added to the top edge and another column to the left edge to improve the speed at which browsers can render the table.</span></span>  
  
-   <span data-ttu-id="a031a-135">对于不包含任何项的表行或表列，即项之间的空白，以固定宽度和高度显示。</span><span class="sxs-lookup"><span data-stu-id="a031a-135">Table rows or columns that contain no items, just gaps between items, are given fixed widths and heights.</span></span>  
  
-   <span data-ttu-id="a031a-136">其他所有行和列均允许根据每个报表项的尺寸增长。</span><span class="sxs-lookup"><span data-stu-id="a031a-136">All other rows and columns are allowed to grow depending on the size of each report item.</span></span>  
  
-   <span data-ttu-id="a031a-137">所有坐标和报表项尺寸的单位均转换为毫米。</span><span class="sxs-lookup"><span data-stu-id="a031a-137">All coordinates and report item sizes are converted to millimeters.</span></span> <span data-ttu-id="a031a-138">其他所有尺寸（包括样式属性）均保留其原始单位。</span><span class="sxs-lookup"><span data-stu-id="a031a-138">All other sizes, including style properties, retain their original units.</span></span> <span data-ttu-id="a031a-139">小于 0.2mm 的尺寸差和位置差均视为 0mm。</span><span class="sxs-lookup"><span data-stu-id="a031a-139">Size and position differences smaller than .2mm are treated as 0mm.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="a031a-140">互动</span><span class="sxs-lookup"><span data-stu-id="a031a-140">Interactivity</span></span>  
 <span data-ttu-id="a031a-141">HTML 支持一些交互元素。</span><span class="sxs-lookup"><span data-stu-id="a031a-141">Some interactive elements are supported in HTML.</span></span> <span data-ttu-id="a031a-142">下面是对一些特定行为的说明。</span><span class="sxs-lookup"><span data-stu-id="a031a-142">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="a031a-143">显示和隐藏</span><span class="sxs-lookup"><span data-stu-id="a031a-143">Show and Hide</span></span>  
 <span data-ttu-id="a031a-144">可以切换可见性的报表项呈现时会带有一个 +/- 切换图像，并且该报表项是可以单击的。</span><span class="sxs-lookup"><span data-stu-id="a031a-144">A report item whose visibility can be toggled is rendered with a +/- toggle image and is clickable.</span></span> <span data-ttu-id="a031a-145">单击该项后，将回调到服务器以重新呈现该项在更改了显示或隐藏状态后的输出。</span><span class="sxs-lookup"><span data-stu-id="a031a-145">When the item is clicked, a call back to the server takes place in order to re-render the output with the changed show or hide state.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="a031a-146">文档结构图</span><span class="sxs-lookup"><span data-stu-id="a031a-146">Document Map</span></span>  
 <span data-ttu-id="a031a-147">文档结构图标签将呈现出来，并可通过在查看器控件中使用文档结构图进行定位。</span><span class="sxs-lookup"><span data-stu-id="a031a-147">Document map labels are rendered and can be navigated to by using the document map in the viewer control.</span></span> <span data-ttu-id="a031a-148">如果数据区域表头已省略，标签将呈现在第一个子单元上。</span><span class="sxs-lookup"><span data-stu-id="a031a-148">For omitted data region headers, labels are rendered on the first child cell.</span></span> <span data-ttu-id="a031a-149">如果不存在相应的子单元，标签将呈现在其标记处前面的子单元上。</span><span class="sxs-lookup"><span data-stu-id="a031a-149">If there is no child cell present, the label is rendered on the child that precedes it.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="a031a-150">书签</span><span class="sxs-lookup"><span data-stu-id="a031a-150">Bookmarks</span></span>  
 <span data-ttu-id="a031a-151">书签链接以超链接形式呈现和显示。</span><span class="sxs-lookup"><span data-stu-id="a031a-151">Bookmark links are rendered and appear as hyperlinks.</span></span> <span data-ttu-id="a031a-152">标签目标将呈现出来并可通过单击书签链接进行定位。</span><span class="sxs-lookup"><span data-stu-id="a031a-152">Bookmark targets are rendered and can be navigated to by clicking the bookmark links.</span></span> <span data-ttu-id="a031a-153">单击书签链接后，报表将跳转到目标书签标签的首次出现处，并且如有可能，浏览器将滚动以便书签链接处于窗口顶部。</span><span class="sxs-lookup"><span data-stu-id="a031a-153">When a bookmark link is clicked, the report goes to the first occurrence of the target bookmark label and, when possible, the browser is scrolled so that the bookmark link is at the top of the window.</span></span> <span data-ttu-id="a031a-154">HTML 定位点 (\<a>) 标记用于标记书签目标。</span><span class="sxs-lookup"><span data-stu-id="a031a-154">HTML anchor (\<a>) tags are used to mark bookmark targets.</span></span>  
  
### <a name="interactive-sorting"></a><span data-ttu-id="a031a-155">交互式排序</span><span class="sxs-lookup"><span data-stu-id="a031a-155">Interactive Sorting</span></span>  
 <span data-ttu-id="a031a-156">如果已为某一文本框定义了用户排序，则 HTML 呈现扩展插件将在该文本框内呈现排序图标，呈现位置为文本框内容的右侧。</span><span class="sxs-lookup"><span data-stu-id="a031a-156">If a text box has user sort defined, the HTML rendering extension renders the sort icons in the text box to the right of its contents.</span></span> <span data-ttu-id="a031a-157">如果报表包含任何已定义用户排序的文本框，则单击相应排序图标后将呈现导致回发到服务器的 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="a031a-157">If a report contains any text box where user sort is defined, JavaScript is rendered that causes a postback to the server when the sort image is clicked.</span></span>  
  
### <a name="hyperlinks-and-drillthrough"></a><span data-ttu-id="a031a-158">超链接和钻取</span><span class="sxs-lookup"><span data-stu-id="a031a-158">Hyperlinks and Drillthrough</span></span>  
 <span data-ttu-id="a031a-159">超链接和钻取链接使用 HTML 定位点呈现为报表项的超链接， (在 \<a> 其上定义的项周围) 标记。</span><span class="sxs-lookup"><span data-stu-id="a031a-159">Hyperlinks and drillthrough links are rendered as hyperlinks on report items using the HTML anchor (\<a>) tags around the item on which they are defined.</span></span>  
  
### <a name="search"></a><span data-ttu-id="a031a-160">搜索</span><span class="sxs-lookup"><span data-stu-id="a031a-160">Search</span></span>  
 <span data-ttu-id="a031a-161">搜索功能允许用户在报表内搜索文本字符串。</span><span class="sxs-lookup"><span data-stu-id="a031a-161">The Search feature allows users to search for a string of text within the report.</span></span>  
  
 <span data-ttu-id="a031a-162">其他搜索和查找功能由 ReportViewer Web 窗体控件提供。</span><span class="sxs-lookup"><span data-stu-id="a031a-162">Additional search and find functionality is provided by the ReportViewer Web Forms control.</span></span>  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="a031a-163">设备信息设置</span><span class="sxs-lookup"><span data-stu-id="a031a-163">Device Information Settings</span></span>  
 <span data-ttu-id="a031a-164">您可以通过更改设备信息设置来更改此呈现器的某些默认设置（包括以哪个模式呈现）。</span><span class="sxs-lookup"><span data-stu-id="a031a-164">You can change some default settings for this renderer, including which mode to render in, by changing the device information settings.</span></span> <span data-ttu-id="a031a-165">有关详细信息，请参阅 [HTML Device Information Settings](../html-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="a031a-165">For more information, see [HTML Device Information Settings](../html-device-information-settings.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="a031a-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a031a-166">See Also</span></span>  
 <span data-ttu-id="a031a-167">[Reporting Services &#40;报表生成器和 SSRS 中的分页&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a031a-167">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a031a-168">[呈现行为 &#40;报表生成器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a031a-168">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a031a-169">[不同报表呈现扩展插件的交互功能 &#40;报表生成器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="a031a-169">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="a031a-170">[&#40;报表生成器和 SSRS 呈现报表项&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a031a-170">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a031a-171">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a031a-171">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
