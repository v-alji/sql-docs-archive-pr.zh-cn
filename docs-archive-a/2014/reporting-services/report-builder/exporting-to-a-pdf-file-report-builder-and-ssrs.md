---
title: 导出到 PDF 文件（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f22497b7-f6c1-4c7b-b831-8c731e26ae37
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b4a324ad40d01d302196fe40ffb4232deb62a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577353"
---
# <a name="exporting-to-a-pdf-file-report-builder-and-ssrs"></a><span data-ttu-id="fa291-102">导出到 PDF 文件（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fa291-102">Exporting to a PDF File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fa291-103">PDF 呈现扩展插件可将报表呈现为特定格式的文件，以便在 Adobe Acrobat 和其他支持 PDF 1.3 的第三方 PDF 查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="fa291-103">The PDF rendering extension renders a report to files that can be opened in Adobe Acrobat and other third-party PDF viewers that support PDF 1.3.</span></span> <span data-ttu-id="fa291-104">尽管 PDF 1.3 与 Adobe Acrobat 4.0 及更高版本兼容，但 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 支持 Adobe Acrobat 6 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="fa291-104">Although PDF 1.3 is compatible with Adobe Acrobat 4.0 and later versions, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supports Adobe Acrobat 6 or later.</span></span> <span data-ttu-id="fa291-105">呈现扩展插件不需要使用 Adobe 软件呈现报表。</span><span class="sxs-lookup"><span data-stu-id="fa291-105">The rendering extension does not require Adobe software to render the report.</span></span> <span data-ttu-id="fa291-106">不过，该插件需要使用 PDF 查看器（例如 Adobe Acrobat）才可查看或打印 PDF 格式的报表。</span><span class="sxs-lookup"><span data-stu-id="fa291-106">However, PDF viewers such as Adobe Acrobat are required to view or print a report in PDF format.</span></span>  
  
 <span data-ttu-id="fa291-107">PDF 呈现扩展插件支持 ANSI 字符，并且可以从日语、朝鲜语、繁体中文、简体中文、西里尔语、希伯来语和阿拉伯语转换 Unicode 字符，但存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="fa291-107">The PDF rendering extension supports ANSI characters and can translate Unicode characters from Japanese, Korean, Traditional Chinese, Simplified Chinese, Cyrillic, Hebrew, and Arabic with certain limitations.</span></span> <span data-ttu-id="fa291-108">有关限制的详细信息，请参阅[导出报表 &#40;报表生成器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fa291-108">For more information about the limitations, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="fa291-109">PDF 呈现器是一个物理页呈现器，因此其分页行为与诸如 HTML 和 Excel 等其他呈现器不同。</span><span class="sxs-lookup"><span data-stu-id="fa291-109">The PDF renderer is a physical page renderer and, therefore, has pagination behavior that differs from other renderers such as HTML and Excel.</span></span> <span data-ttu-id="fa291-110">本主题提供了特定于 PDF 呈现器的信息并说明了呈现规则的例外情况。</span><span class="sxs-lookup"><span data-stu-id="fa291-110">This topic provides PDF renderer-specific information and describes exceptions to the rules.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="font-embedding"></a><a name="FontRequirements"></a> <span data-ttu-id="fa291-111">嵌入字体</span><span class="sxs-lookup"><span data-stu-id="fa291-111">Font Embedding</span></span>  
 <span data-ttu-id="fa291-112">如有可能，PDF 呈现扩展插件会在 PDF 文件中嵌入显示报表所需的每个字体的子集。</span><span class="sxs-lookup"><span data-stu-id="fa291-112">When possible, the PDF rendering extension embeds the subset of each font that is needed to display the report in the PDF file.</span></span> <span data-ttu-id="fa291-113">因此报表服务器上必须安装有报表中使用的字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-113">Fonts that are used in the report must be installed on the report server.</span></span> <span data-ttu-id="fa291-114">当报表服务器以 PDF 格式生成报表时，它将使用报表引用的字体中所存储的信息在 PDF 文件内创建字符映射。</span><span class="sxs-lookup"><span data-stu-id="fa291-114">When the report server generates a report in PDF format, it uses the information stored in the font referenced by the report to create character mappings within the PDF file.</span></span> <span data-ttu-id="fa291-115">如果报表服务器上未安装所引用的字体，生成的 PDF 文件可能不会包含正确的映射，因而在查看该 PDF 文件时可能不会正常显示。</span><span class="sxs-lookup"><span data-stu-id="fa291-115">If the referenced font is not installed on the report server, the resulting PDF file might not contain the correct mappings and might not display correctly when viewed.</span></span>  
  
 <span data-ttu-id="fa291-116">满足以下条件时，将在 PDF 文件中嵌入字体：</span><span class="sxs-lookup"><span data-stu-id="fa291-116">Fonts are embedded in the PDF file when the following conditions apply:</span></span>  
  
-   <span data-ttu-id="fa291-117">字体作者授予了嵌入字体的权限。</span><span class="sxs-lookup"><span data-stu-id="fa291-117">Font embedding privileges are granted by the font author.</span></span> <span data-ttu-id="fa291-118">安装的字体包含一个属性，该属性指示字体作者是否打算允许在文档中嵌入字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-118">Installed fonts include a property that indicates whether the font author intends to allow embedding a font in a document.</span></span> <span data-ttu-id="fa291-119">如果该属性值为 EMBED_NOEMBEDDING，将不会在 PDF 文件中嵌入字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-119">If the property value is EMBED_NOEMBEDDING, the font is not embedded in the PDF file.</span></span> <span data-ttu-id="fa291-120">有关详细信息，请参阅 msdn.microsoft.com 上的“TTGetEmbeddingType”。</span><span class="sxs-lookup"><span data-stu-id="fa291-120">For more information, see "TTGetEmbeddingType" on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="fa291-121">该字体为 TrueType。</span><span class="sxs-lookup"><span data-stu-id="fa291-121">The Font is TrueType.</span></span>  
  
-   <span data-ttu-id="fa291-122">字体由报表中的可见项引用。</span><span class="sxs-lookup"><span data-stu-id="fa291-122">Fonts are referenced by visible items in a report.</span></span> <span data-ttu-id="fa291-123">如果字体由 Hidden 属性设置为 True 的项引用，则显示呈现的数据不需要字体，所以不会在文件中包含字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-123">If a font is referenced by an item that has the Hidden property set to True, the font is not needed to display rendered data and will not be included in the file.</span></span> <span data-ttu-id="fa291-124">只有显示所呈现的报表数据需要字体时，才会嵌入字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-124">Fonts are embedded only when they are needed to display the rendered report data.</span></span>  
  
 <span data-ttu-id="fa291-125">如果某个字体满足上述所有条件，将在 PDF 文件中嵌入该字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-125">If all of these conditions are met for a font, the font is embedded in the PDF file.</span></span> <span data-ttu-id="fa291-126">如果不满足上述一个或多个条件，将不会在 PDF 文件中嵌入该字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-126">If one or more of these conditions is not met, the font is not embedded in the PDF file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa291-127">即使条件满足，还会有一种 PDF 文件未嵌入字体的情况。</span><span class="sxs-lookup"><span data-stu-id="fa291-127">Although the conditions are met, there is one circumstance under which fonts are not embedded in the PDF file.</span></span> <span data-ttu-id="fa291-128">如果所用字体包含在 PDF 规范（常称作 standard type 1 字体或十四个基础字体）中，则对于 ANSI 内容，将不嵌入字体。</span><span class="sxs-lookup"><span data-stu-id="fa291-128">If the fonts used are the ones in the PDF specification that are commonly known as standard type 1 fonts or the base fourteen fonts, then fonts are not embedded for ANSI content.</span></span>  
  
  
  
### <a name="fonts-on-the-client-computer"></a><span data-ttu-id="fa291-129">客户端计算机上的字体</span><span class="sxs-lookup"><span data-stu-id="fa291-129">Fonts on the Client Computer</span></span>  
 <span data-ttu-id="fa291-130">如果在 PDF 文件中嵌入了字体，则用于查看报表的计算机（客户端计算机）不必安装字体即可正确显示报表。</span><span class="sxs-lookup"><span data-stu-id="fa291-130">When a font is embedded in the PDF file, the computer that is used to view the report (the client computer) does not need to have the font installed for the report to display correctly.</span></span>  
  
 <span data-ttu-id="fa291-131">如果 PDF 文件中没有嵌入字体，则客户端计算机必须安装正确的字体才能正确显示报表。</span><span class="sxs-lookup"><span data-stu-id="fa291-131">When a font is not embedded in the PDF file, the client computer must have the correct font installed for the report to display correctly.</span></span> <span data-ttu-id="fa291-132">如果客户端计算机上没有安装字体，则对于不支持的字符，PDF 文件将显示问号字符 (?)。</span><span class="sxs-lookup"><span data-stu-id="fa291-132">If the font is not installed on the client computer, the PDF file displays a question mark character (?) for unsupported characters.</span></span>  
  
### <a name="verifying-fonts-in-a-pdf-file"></a><span data-ttu-id="fa291-133">验证 PDF 文件中的字体</span><span class="sxs-lookup"><span data-stu-id="fa291-133">Verifying Fonts in a PDF File</span></span>  
 <span data-ttu-id="fa291-134">PDF 输出差异通常在报表中使用不支持非拉丁字符的字体并随后将非拉丁字符添加到报表时发生。</span><span class="sxs-lookup"><span data-stu-id="fa291-134">Differences in PDF output occur most often when a font that does not support non-Latin characters is used in a report and then non-Latin characters are added to the report.</span></span> <span data-ttu-id="fa291-135">应在报表服务器和客户端计算机上测试 PDF 呈现输出，以验证报表是否正常呈现。</span><span class="sxs-lookup"><span data-stu-id="fa291-135">You should test the PDF rendering output on both the report server and the client computers to verify that the report renders correctly.</span></span>  
  
 <span data-ttu-id="fa291-136">请勿依赖在预览模式下查看报表或导出到 HTML，这是因为报表会因图形设计界面或 Microsoft Internet Explorer 分别执行的自动字体替换而正确显示。</span><span class="sxs-lookup"><span data-stu-id="fa291-136">Do not rely on viewing the report in Preview or exporting to HTML because the report will look correct due to automatic font substitution performed by the graphical design interface or by Microsoft Internet Explorer, respectively.</span></span> <span data-ttu-id="fa291-137">如果服务器上缺少 Unicode 标志符号，您可能会看到字符被替换为问号 (?)。</span><span class="sxs-lookup"><span data-stu-id="fa291-137">If there are Unicode Glyphs missing on the server, you may see characters replaced with a question mark (?).</span></span> <span data-ttu-id="fa291-138">如果客户端上缺少字体，你可能会看到字符被替换为方框 (□)。</span><span class="sxs-lookup"><span data-stu-id="fa291-138">If there is a font missing on the client, you may see characters replaced with boxes (□).</span></span>  
  
 <span data-ttu-id="fa291-139">嵌入 PDF 文件的字体包含在“字体”属性中，该属性随文件一起作为元数据保存。</span><span class="sxs-lookup"><span data-stu-id="fa291-139">The fonts that are embedded in the PDF file are included in the Fonts property that is saved with the file, as metadata.</span></span>  
  
##  <a name="metadata"></a><a name="Metadata"></a> <span data-ttu-id="fa291-140">元数据</span><span class="sxs-lookup"><span data-stu-id="fa291-140">Metadata</span></span>  
 <span data-ttu-id="fa291-141">除了报表布局外，PDF 呈现扩展插件会将以下元数据写入 PDF 文档信息字典。</span><span class="sxs-lookup"><span data-stu-id="fa291-141">In addition to the report layout, the PDF rendering extension writes the following metadata to the PDF Document Information Dictionary.</span></span>  
  
|<span data-ttu-id="fa291-142">PDF 属性</span><span class="sxs-lookup"><span data-stu-id="fa291-142">PDF property</span></span>|<span data-ttu-id="fa291-143">创建自</span><span class="sxs-lookup"><span data-stu-id="fa291-143">Created from</span></span>|  
|------------------|------------------|  
|`Title`|<span data-ttu-id="fa291-144">`Name` RDL 元素的 `Report` 属性。</span><span class="sxs-lookup"><span data-stu-id="fa291-144">The `Name` attribute of the `Report` RDL element.</span></span>|  
|`Author`|<span data-ttu-id="fa291-145">`Author` RDL 元素。</span><span class="sxs-lookup"><span data-stu-id="fa291-145">The `Author` RDL element.</span></span>|  
|`Subject`|<span data-ttu-id="fa291-146">`Description` RDL 元素。</span><span class="sxs-lookup"><span data-stu-id="fa291-146">The `Description` RDL element.</span></span>|  
|`Creator`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fa291-147">产品的名称和版本。</span><span class="sxs-lookup"><span data-stu-id="fa291-147">product name and version.</span></span>|  
|`Producer`|<span data-ttu-id="fa291-148">呈现扩展插件的名称和版本。</span><span class="sxs-lookup"><span data-stu-id="fa291-148">Rendering extension name and version.</span></span>|  
|`CreationDate`|<span data-ttu-id="fa291-149">报表执行时间，以 PDF `datetime` 格式表示。</span><span class="sxs-lookup"><span data-stu-id="fa291-149">Report execution time in PDF `datetime` format.</span></span>|  
  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="fa291-150">互动</span><span class="sxs-lookup"><span data-stu-id="fa291-150">Interactivity</span></span>  
 <span data-ttu-id="fa291-151">PDF 支持一些交互元素。</span><span class="sxs-lookup"><span data-stu-id="fa291-151">Some interactive elements are supported in PDF.</span></span> <span data-ttu-id="fa291-152">下面是对一些特定行为的说明。</span><span class="sxs-lookup"><span data-stu-id="fa291-152">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="fa291-153">显示和隐藏</span><span class="sxs-lookup"><span data-stu-id="fa291-153">Show and Hide</span></span>  
 <span data-ttu-id="fa291-154">PDF 不支持动态显示和隐藏元素。</span><span class="sxs-lookup"><span data-stu-id="fa291-154">Dynamic show and hide elements are not supported in PDF.</span></span> <span data-ttu-id="fa291-155">呈现 PDF 文档是为了与报表中任意项的当前状态相匹配。</span><span class="sxs-lookup"><span data-stu-id="fa291-155">The PDF document is rendered to match the current state of any items in the report.</span></span> <span data-ttu-id="fa291-156">例如，如果在报表初次运行时显示了某项，则会呈现该项。</span><span class="sxs-lookup"><span data-stu-id="fa291-156">For example, if the item is displayed when the report is run initially, then the item is rendered.</span></span> <span data-ttu-id="fa291-157">如果可切换的图像在导出报表时隐藏，则不会呈现这些图像。</span><span class="sxs-lookup"><span data-stu-id="fa291-157">Images that can be toggled are not rendered, if they are hidden when the report is exported.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="fa291-158">文档结构图</span><span class="sxs-lookup"><span data-stu-id="fa291-158">Document Map</span></span>  
 <span data-ttu-id="fa291-159">如果报表中存在任何文档结构图标签，则会将文档大纲添加到 PDF 文件。</span><span class="sxs-lookup"><span data-stu-id="fa291-159">If there are any document map labels present in the report, a document outline is added to the PDF file.</span></span> <span data-ttu-id="fa291-160">每个文档结构图标签在文档大纲中显示为一个条目，显示顺序与其在报表中的显示顺序相同。</span><span class="sxs-lookup"><span data-stu-id="fa291-160">Each document map label appears as an entry in the document outline in the order that it appears in the report.</span></span> <span data-ttu-id="fa291-161">在 Acrobat 中，仅当目标书签所在的页呈现出来时，才会将该标签添加到文档大纲中。</span><span class="sxs-lookup"><span data-stu-id="fa291-161">In Acrobat, a target bookmark is added to the document outline only if the page it is on is rendered.</span></span>  
  
 <span data-ttu-id="fa291-162">如果仅呈现单个页，则不添加文档大纲。</span><span class="sxs-lookup"><span data-stu-id="fa291-162">If only a single page is rendered, no document outline is added.</span></span> <span data-ttu-id="fa291-163">文档结构图是分层排列的，以反映报表中的嵌套级别。</span><span class="sxs-lookup"><span data-stu-id="fa291-163">The document map is arranged hierarchically to reflect the level of nesting in the report.</span></span> <span data-ttu-id="fa291-164">文档大纲在 Acrobat 中的 "书签" 选项卡下是可访问的。单击文档大纲内的条目将导致文档进入带有书签的位置。</span><span class="sxs-lookup"><span data-stu-id="fa291-164">The document outline is accessible in Acrobat under the Bookmarks tab. Clicking an entry within the document outline causes the document to go to the bookmarked location.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="fa291-165">书签</span><span class="sxs-lookup"><span data-stu-id="fa291-165">Bookmarks</span></span>  
 <span data-ttu-id="fa291-166">PDF 呈现不支持书签。</span><span class="sxs-lookup"><span data-stu-id="fa291-166">Bookmarks are not supported in PDF rendering.</span></span>  
  
### <a name="drillthrough-links"></a><span data-ttu-id="fa291-167">钻取链接</span><span class="sxs-lookup"><span data-stu-id="fa291-167">Drillthrough Links</span></span>  
 <span data-ttu-id="fa291-168">在 PDF 呈现中不支持钻取链接。</span><span class="sxs-lookup"><span data-stu-id="fa291-168">Drillthrough links are not supported in PDF rendering.</span></span> <span data-ttu-id="fa291-169">钻取链接不呈现为可单击链接，并且钻取报表不能连接到钻取的目标。</span><span class="sxs-lookup"><span data-stu-id="fa291-169">The drillthrough links are not rendered as clickable links and drillthrough reports cannot connect to the target of the drillthrough.</span></span>  
  
### <a name="hyperlinks"></a><span data-ttu-id="fa291-170">超链接</span><span class="sxs-lookup"><span data-stu-id="fa291-170">Hyperlinks</span></span>  
 <span data-ttu-id="fa291-171">报表中的超链接在 PDF 文件中呈现为可单击的链接。</span><span class="sxs-lookup"><span data-stu-id="fa291-171">Hyperlinks in reports are rendered as clickable links in the PDF file.</span></span> <span data-ttu-id="fa291-172">单击超链接时，Acrobat 将打开默认的客户端浏览器并导航到超链接 URL。</span><span class="sxs-lookup"><span data-stu-id="fa291-172">When clicked, Acrobat will open the default client browser and navigate to the hyperlink URL.</span></span>  
  
  
  
##  <a name="compression"></a><a name="Compression"></a><span data-ttu-id="fa291-173">折叠</span><span class="sxs-lookup"><span data-stu-id="fa291-173">Compression</span></span>  
 <span data-ttu-id="fa291-174">图像压缩基于图像的原始文件类型。</span><span class="sxs-lookup"><span data-stu-id="fa291-174">Image compression is based on the original file type of the image.</span></span> <span data-ttu-id="fa291-175">默认情况下，PDF 呈现扩展插件会压缩 PDF 文件。</span><span class="sxs-lookup"><span data-stu-id="fa291-175">The PDF rendering extension compresses PDF files by default.</span></span>  
  
 <span data-ttu-id="fa291-176">为了尽可能保留 PDF 文件中所包含图像的任何压缩状态，JPEG 图像存储为 JPEG，所有其他图像类型都存储为 BMP。</span><span class="sxs-lookup"><span data-stu-id="fa291-176">To preserve any compression for images included in the PDF file when possible, JPEG images are stored as JPEG and all other image types are stored as BMP.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa291-177">PDF 文件不支持嵌入 PNG 图像。</span><span class="sxs-lookup"><span data-stu-id="fa291-177">PDF files don't support embedding PNG images.</span></span>  
  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="fa291-178">设备信息设置</span><span class="sxs-lookup"><span data-stu-id="fa291-178">Device Information Settings</span></span>  
 <span data-ttu-id="fa291-179">您可以通过更改设备信息设置来更改此呈现器的某些默认设置。</span><span class="sxs-lookup"><span data-stu-id="fa291-179">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="fa291-180">有关详细信息，请参阅 [PDF Device Information Settings](../pdf-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="fa291-180">For more information, see [PDF Device Information Settings](../pdf-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="fa291-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa291-181">See Also</span></span>  
 <span data-ttu-id="fa291-182">[Reporting Services &#40;报表生成器和 SSRS 中的分页&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fa291-182">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fa291-183">[呈现行为 &#40;报表生成器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fa291-183">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fa291-184">[不同报表呈现扩展插件的交互功能 &#40;报表生成器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="fa291-184">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="fa291-185">[&#40;报表生成器和 SSRS 呈现报表项&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fa291-185">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fa291-186">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fa291-186">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
