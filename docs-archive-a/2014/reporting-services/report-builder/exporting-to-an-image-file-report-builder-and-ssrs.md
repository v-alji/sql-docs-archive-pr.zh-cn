---
title: 导出到图像文件（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc1c8539b39a99c252ebfcb0275b674f657de6c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586487"
---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a><span data-ttu-id="8726d-102">导出到图像文件（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="8726d-102">Exporting to an Image File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8726d-103">图像呈现扩展插件可以将报表呈现为位图或图元文件。</span><span class="sxs-lookup"><span data-stu-id="8726d-103">The Image rendering extension renders a report to a bitmap or metafile.</span></span> <span data-ttu-id="8726d-104">默认情况下，图像呈现扩展插件将生成报表的 TIFF 文件，您可以按多页形式查看此类文件。</span><span class="sxs-lookup"><span data-stu-id="8726d-104">By default, the Image rendering extension produces a TIFF file of the report, which can be viewed in multiple pages.</span></span> <span data-ttu-id="8726d-105">客户端收到图像时，可以在图像查看器中显示图像，并可以打印图像。</span><span class="sxs-lookup"><span data-stu-id="8726d-105">When the client receives the image, it can be displayed in an image viewer and printed.</span></span> <span data-ttu-id="8726d-106">本主题提供了特定于图像呈现器的信息并说明了呈现规则的例外情况。</span><span class="sxs-lookup"><span data-stu-id="8726d-106">This topic provides Image renderer-specific information and describes exceptions to the rendering rules.</span></span>  
  
 <span data-ttu-id="8726d-107">图像呈现扩展插件可以生成 [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]支持的以下任意格式的文件：BMP、EMF、EMFPlus、GIF、JPEG、PNG 和 TIFF。</span><span class="sxs-lookup"><span data-stu-id="8726d-107">The Image rendering extension can generate files in any of the formats supported by [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]: BMP, EMF, EMFPlus, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="8726d-108">对于 TIFF 格式，主输出流的文件名为 *ReportName*.tif。</span><span class="sxs-lookup"><span data-stu-id="8726d-108">For TIFF format, the file name of the primary stream is *ReportName*.tif.</span></span> <span data-ttu-id="8726d-109">对于其他按照每个文件一页的方式进行呈现的所有格式，文件名为 *ReportName_Page.ext* ，其中，</span><span class="sxs-lookup"><span data-stu-id="8726d-109">For all other formats, which render as a single page per file, the file name is *ReportName_Page.ext* where.</span></span> <span data-ttu-id="8726d-110">*ext* 是所选格式的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="8726d-110">*ext* is the file extension for the chosen format.</span></span> <span data-ttu-id="8726d-111">若要以另一种受图像支持的格式生成文件，请在 **OutputFormatDeviceInfo** 设置中指定上面列出的任意字符串。</span><span class="sxs-lookup"><span data-stu-id="8726d-111">To produce a file in another Image-supported format, specify any of the above listed strings in the **OutputFormatDeviceInfo** setting.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="supported-image-formats"></a><a name="SupportedImageFormats"></a> <span data-ttu-id="8726d-112">支持的图像格式</span><span class="sxs-lookup"><span data-stu-id="8726d-112">Supported Image Formats</span></span>  
 <span data-ttu-id="8726d-113">下表显示了每种图像呈现器格式的文件扩展名和 MimeType。</span><span class="sxs-lookup"><span data-stu-id="8726d-113">The following table shows the file extension and MimeType for each Image renderer format.</span></span>  
  
|<span data-ttu-id="8726d-114">**Type**</span><span class="sxs-lookup"><span data-stu-id="8726d-114">**Type**</span></span>|<span data-ttu-id="8726d-115">**扩展名**</span><span class="sxs-lookup"><span data-stu-id="8726d-115">**Extension**</span></span>|<span data-ttu-id="8726d-116">**MIMEType**</span><span class="sxs-lookup"><span data-stu-id="8726d-116">**MIMEType**</span></span>|  
|--------------|-------------------|------------------|  
|<span data-ttu-id="8726d-117">BMP</span><span class="sxs-lookup"><span data-stu-id="8726d-117">BMP</span></span>|<span data-ttu-id="8726d-118">bmp</span><span class="sxs-lookup"><span data-stu-id="8726d-118">bmp</span></span>|<span data-ttu-id="8726d-119">image/bmp</span><span class="sxs-lookup"><span data-stu-id="8726d-119">image/bmp</span></span>|  
|<span data-ttu-id="8726d-120">GIF</span><span class="sxs-lookup"><span data-stu-id="8726d-120">GIF</span></span>|<span data-ttu-id="8726d-121">GIF</span><span class="sxs-lookup"><span data-stu-id="8726d-121">gif</span></span>|<span data-ttu-id="8726d-122">image/gif</span><span class="sxs-lookup"><span data-stu-id="8726d-122">image/gif</span></span>|  
|<span data-ttu-id="8726d-123">JPEG</span><span class="sxs-lookup"><span data-stu-id="8726d-123">JPEG</span></span>|<span data-ttu-id="8726d-124">jpeg</span><span class="sxs-lookup"><span data-stu-id="8726d-124">jpeg</span></span>|<span data-ttu-id="8726d-125">image/jpeg</span><span class="sxs-lookup"><span data-stu-id="8726d-125">image/jpeg</span></span>|  
|<span data-ttu-id="8726d-126">PNG</span><span class="sxs-lookup"><span data-stu-id="8726d-126">PNG</span></span>|<span data-ttu-id="8726d-127">png</span><span class="sxs-lookup"><span data-stu-id="8726d-127">png</span></span>|<span data-ttu-id="8726d-128">image/png</span><span class="sxs-lookup"><span data-stu-id="8726d-128">image/png</span></span>|  
|<span data-ttu-id="8726d-129">TIFF</span><span class="sxs-lookup"><span data-stu-id="8726d-129">TIFF</span></span>|<span data-ttu-id="8726d-130">tif</span><span class="sxs-lookup"><span data-stu-id="8726d-130">tif</span></span>|<span data-ttu-id="8726d-131">image/tiff</span><span class="sxs-lookup"><span data-stu-id="8726d-131">image/tiff</span></span>|  
|<span data-ttu-id="8726d-132">EMF</span><span class="sxs-lookup"><span data-stu-id="8726d-132">EMF</span></span>|<span data-ttu-id="8726d-133">EMF</span><span class="sxs-lookup"><span data-stu-id="8726d-133">emf</span></span>|<span data-ttu-id="8726d-134">image/emf</span><span class="sxs-lookup"><span data-stu-id="8726d-134">image/emf</span></span>|  
|<span data-ttu-id="8726d-135">EMFPlus</span><span class="sxs-lookup"><span data-stu-id="8726d-135">EMFPlus</span></span>|<span data-ttu-id="8726d-136">EMF</span><span class="sxs-lookup"><span data-stu-id="8726d-136">emf</span></span>|<span data-ttu-id="8726d-137">image/emf</span><span class="sxs-lookup"><span data-stu-id="8726d-137">image/emf</span></span>|  
  
  
##  <a name="rendering-multiple-pages"></a><a name="RenderingMultiplePages"></a> <span data-ttu-id="8726d-138">呈现多页</span><span class="sxs-lookup"><span data-stu-id="8726d-138">Rendering Multiple Pages</span></span>  
 <span data-ttu-id="8726d-139">TIFF 是唯一一种支持在单个文件中包含多页文档的格式。</span><span class="sxs-lookup"><span data-stu-id="8726d-139">TIFF is the only format that supports multiple page documents in a single file.</span></span> <span data-ttu-id="8726d-140">JPG 或 PNG 等其他格式一次只能输出一页并且需要单独为每页调用呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="8726d-140">Other formats, such as JPG or PNG, output one page at a time and require a separate call to the rendering extension for each page.</span></span>  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="8726d-141">互动</span><span class="sxs-lookup"><span data-stu-id="8726d-141">Interactivity</span></span>  
 <span data-ttu-id="8726d-142">此呈现器生成的任何图像格式都不支持交互。</span><span class="sxs-lookup"><span data-stu-id="8726d-142">Interactivity is not supported in any Image formats generated by this renderer.</span></span> <span data-ttu-id="8726d-143">不会呈现以下交互元素：</span><span class="sxs-lookup"><span data-stu-id="8726d-143">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="8726d-144">超链接</span><span class="sxs-lookup"><span data-stu-id="8726d-144">Hyperlinks</span></span>  
  
-   <span data-ttu-id="8726d-145">显示或隐藏</span><span class="sxs-lookup"><span data-stu-id="8726d-145">Show or Hide</span></span>  
  
-   <span data-ttu-id="8726d-146">文档结构图</span><span class="sxs-lookup"><span data-stu-id="8726d-146">Document Map</span></span>  
  
-   <span data-ttu-id="8726d-147">钻取链接或点击链接</span><span class="sxs-lookup"><span data-stu-id="8726d-147">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="8726d-148">最终用户排序</span><span class="sxs-lookup"><span data-stu-id="8726d-148">End user sort</span></span>  
  
-   <span data-ttu-id="8726d-149">固定标题</span><span class="sxs-lookup"><span data-stu-id="8726d-149">Fixed headers</span></span>  
  
-   <span data-ttu-id="8726d-150">书签</span><span class="sxs-lookup"><span data-stu-id="8726d-150">Bookmarks</span></span>  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="8726d-151">设备信息设置</span><span class="sxs-lookup"><span data-stu-id="8726d-151">Device Information Settings</span></span>  
 <span data-ttu-id="8726d-152">您可以通过更改设备信息设置来更改此呈现器的某些默认设置。</span><span class="sxs-lookup"><span data-stu-id="8726d-152">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="8726d-153">有关详细信息，请参阅 [Image Device Information Settings](../image-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="8726d-153">For more information, see [Image Device Information Settings](../image-device-information-settings.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="8726d-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8726d-154">See Also</span></span>  
 <span data-ttu-id="8726d-155">[Reporting Services &#40;报表生成器和 SSRS 中的分页&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8726d-155">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8726d-156">[呈现行为 &#40;报表生成器和 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8726d-156">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8726d-157">[不同报表呈现扩展插件的交互功能 &#40;报表生成器和 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="8726d-157">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="8726d-158">[&#40;报表生成器和 SSRS 呈现报表项&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8726d-158">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8726d-159">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="8726d-159">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
