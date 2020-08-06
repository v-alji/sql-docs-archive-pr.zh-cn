---
title: 图像（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fcc2db5c-5c26-4607-ae2b-f65c80360536
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f0840a10cc1082ba8dc7912862f7cf34c64972d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688587"
---
# <a name="images-report-builder-and-ssrs"></a><span data-ttu-id="fe7b8-102">图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fe7b8-102">Images (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fe7b8-103">图像是一种报表项，包含对嵌入在报表中、存储在数据库中、存储在报表服务器上或存储在 Web 上其他位置的图像的引用。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-103">An image is a report item that contains a reference to an image that is embedded in the report, stored in a database, stored on the report server, or stored elsewhere on the Web.</span></span> <span data-ttu-id="fe7b8-104">图像可以是数据行重复使用的图片。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-104">An image can be a picture that is repeated with rows of data.</span></span> <span data-ttu-id="fe7b8-105">您还可以将图像用作某些报表项的背景。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-105">You can also use an image as a background for certain report items.</span></span>  
  
 <span data-ttu-id="fe7b8-106">在服务器上存储徽标的想法很好，因为您可以在许多报表中使用相同的徽标。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-106">Storing logos on a server is a good idea because you can use the same logo in many reports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="comparing-external-embedded-and-data-bound-images"></a><a name="ComparingImages"></a> <span data-ttu-id="fe7b8-107">比较外部图像、嵌入图像和数据绑定图像</span><span class="sxs-lookup"><span data-stu-id="fe7b8-107">Comparing External, Embedded, and Data-Bound Images</span></span>  
 <span data-ttu-id="fe7b8-108">如果在报表中使用基于服务器的图像或其他外部图像，则该图像项会包含一个路径，指向位于报表服务器上的图像或 Web 上图像所在的位置。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-108">When you use a server-based or other external image in a report, the image item contains a path that points to an image on the report server or wherever it exists on the Web.</span></span> <span data-ttu-id="fe7b8-109">但是，在使用嵌入图像时，图像数据存储在报表定义中，而不是作为独立的文件存在。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-109">When you use an embedded image, however, the image data is stored within the report definition and does not exist as a separate file.</span></span>  
  
 <span data-ttu-id="fe7b8-110">基于服务器的图像适合用作在多个报表或网页间共享的徽标和静态图片。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-110">Server-based images work well for logos and static pictures that are shared among several reports or Web pages.</span></span> <span data-ttu-id="fe7b8-111">嵌入图像可确保图像始终对报表可用，但是嵌入图像不能共享。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-111">Embedded images ensure that the images are always available to the report, but they cannot be shared.</span></span> <span data-ttu-id="fe7b8-112">含有外部图像的报表定义要比含有嵌入图像的报表定义小。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-112">Report definitions with external images are smaller than definitions with embedded images.</span></span>  
  
 <span data-ttu-id="fe7b8-113">数据绑定图像还可以通过数据库中存储的二进制数据进行显示。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-113">Data-bound images can also be displayed from binary data stored in a database.</span></span> <span data-ttu-id="fe7b8-114">例如，在产品列表中产品名旁边显示的图片就属于数据库图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-114">For example, the pictures that appear alongside product names in a product list are database images.</span></span> <span data-ttu-id="fe7b8-115">在下图中，自行车图像存储于数据库中并且在报表中检索，以便说明各产品。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-115">In the following picture, the images of bicycles are stored in a database and retrieved in the report to illustrate each product.</span></span>  
  
 <span data-ttu-id="fe7b8-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span><span class="sxs-lookup"><span data-stu-id="fe7b8-116">![rs_DataboundBikes](../media/rs-databoundbikes.gif "rs_DataboundBikes")</span></span>  
  

  
##  <a name="images-as-report-parts"></a><a name="ImagesReportParts"></a> <span data-ttu-id="fe7b8-117">作为报表部件的图像</span><span class="sxs-lookup"><span data-stu-id="fe7b8-117">Images as Report Parts</span></span>  
 <span data-ttu-id="fe7b8-118">您可以将图像作为报表部件与报表分开保存。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-118">You can save images separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 
  
##  <a name="embedding-images"></a><a name="EmbedImages"></a> <span data-ttu-id="fe7b8-119">嵌入图像</span><span class="sxs-lookup"><span data-stu-id="fe7b8-119">Embedding Images</span></span>  
 <span data-ttu-id="fe7b8-120">您可以将图像嵌入报表，使所有的图像数据都存储在报表定义中。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-120">You can embed images in a report so that all image data is stored within the report definition.</span></span> <span data-ttu-id="fe7b8-121">嵌入图像时，将对该图像进行 MIME 编码，然后以文本形式将其存储到报表定义中。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-121">When you embed an image, the image is MIME-encoded and stored as text in the report definition.</span></span> <span data-ttu-id="fe7b8-122">使用嵌入图像可确保图像始终对报表可用，但它也会增大报表定义的大小。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-122">Using an embedded image ensures that the image is always available to the report, but it also increases the size of the report definition.</span></span>  
  
 <span data-ttu-id="fe7b8-123">有关嵌入图像的详细信息，请参阅 [在报表中嵌入图像（报表生成器和 SSRS）](embed-an-image-in-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-123">For more information about embedding an image, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="external-images"></a><a name="ExternalImages"></a> <span data-ttu-id="fe7b8-124">外部图像</span><span class="sxs-lookup"><span data-stu-id="fe7b8-124">External Images</span></span>  
 <span data-ttu-id="fe7b8-125">通过指定图像的 URL 可以在报表中包括存储的图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-125">You can include stored images in a report by specifying a URL to the image.</span></span> <span data-ttu-id="fe7b8-126">在报表中使用外部图像时，图像源设置为 `External`，图像的值是该图像的 URL 地址或路径。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-126">When you use an external image in a report, the image source is set to `External` and the value for the image is the URL address or path to the image.</span></span>  
  
 <span data-ttu-id="fe7b8-127">有关详细信息，请参阅[指定外部项的路径（报表生成器和 SSRS）](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-127">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="fe7b8-128">当报表在报表生成器或报表设计器中运行时，预览将使用用户的凭据来显示图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-128">When the report is run in Report Builder or Report Designer, preview uses the credentials of the user to display the image.</span></span> <span data-ttu-id="fe7b8-129">当报表在报表服务器上运行时，如果服务器凭据没有足够权限来访问图像，则报表中的图像可能无法显示。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-129">When the report is run on the report server, the image in the report may not be displayed if the server credentials are not sufficient to access the image.</span></span> <span data-ttu-id="fe7b8-130">在此种情况下，请与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-130">In that case, contact your system administrator.</span></span>  
  
 <span data-ttu-id="fe7b8-131">有关向报表添加外部图像的详细信息，请参阅 [添加外部图像（报表生成器和 SSRS）](add-an-external-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-131">For more information about adding an external image to a report, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="background-images"></a><a name="BackgroundImages"></a> <span data-ttu-id="fe7b8-132">背景图像</span><span class="sxs-lookup"><span data-stu-id="fe7b8-132">Background Images</span></span>  
 <span data-ttu-id="fe7b8-133">您可以使用图像作为表体或者矩形框、文本框、列表，矩阵或表的背景图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-133">You can use an image as a background image in the body of the report or in a rectangle, text box, list, matrix, or table.</span></span> <span data-ttu-id="fe7b8-134">背景图像与图像具有类似的属性。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-134">A background image and an image have similar properties.</span></span> <span data-ttu-id="fe7b8-135">您还可以指定如何重复图像来填充项的背景。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-135">You can also specify how the image is repeated to fill the background of the item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe7b8-136">某些呈现扩展插件（例如 HTML 呈现扩展插件）可以在表体、页眉和页脚中呈现表体的背景图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-136">Some rendering extensions, like the HTML rendering extension, render the background image for the report body in the body, the page header, and the page footer.</span></span> <span data-ttu-id="fe7b8-137">可以为页眉和页脚单独定义背景图像，但如果没有定义图像，则报表将使用表体的背景图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-137">You can define a separate background image for the page header and footer, but if no image is defined, the report uses the background image of the body.</span></span> <span data-ttu-id="fe7b8-138">其他呈现扩展插件（例如图像呈现扩展插件）不能在页眉和页脚中呈现表体的背景图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-138">Other rendering extensions, like the Image rendering extension, do not render the body background image in the page header and footer.</span></span>  
  
 <span data-ttu-id="fe7b8-139">有关添加背景图像的详细信息，请参阅 [添加背景图像（报表生成器和 SSRS）](add-a-background-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-139">For more information about adding a background image, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="data-bound-images"></a><a name="DataboundImages"></a> <span data-ttu-id="fe7b8-140">数据绑定图像</span><span class="sxs-lookup"><span data-stu-id="fe7b8-140">Data-bound Images</span></span>  
 <span data-ttu-id="fe7b8-141">您可以向报表中添加存储于数据库中的图像。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-141">You can add images that are stored in a database to your report.</span></span> <span data-ttu-id="fe7b8-142">您使用的图像报表项与静态图像所用的相同，但还需要使用一组指示该图像存储在数据库中的属性。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-142">You use the same image report item as the one used for static images, but with a set of properties that indicate that the image is stored in a database.</span></span> <span data-ttu-id="fe7b8-143">若要查看有关使用数据绑定图像的说明，请参阅 [添加数据绑定图像（报表生成器和 SSRS）](add-a-data-bound-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fe7b8-143">To view instructions about working with data-bound images, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="fe7b8-144">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="fe7b8-144">How-to Topics</span></span>  
 [<span data-ttu-id="fe7b8-145">添加外部图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fe7b8-145">Add an External Image &#40;Report Builder and SSRS&#41;</span></span>](add-an-external-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="fe7b8-146">在报表中嵌入图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fe7b8-146">Embed an Image in a Report &#40;Report Builder and SSRS&#41;</span></span>](embed-an-image-in-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="fe7b8-147">添加背景图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fe7b8-147">Add a Background Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-background-image-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="fe7b8-148">添加数据绑定图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fe7b8-148">Add a Data-Bound Image &#40;Report Builder and SSRS&#41;</span></span>](add-a-data-bound-image-report-builder-and-ssrs.md)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="fe7b8-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe7b8-149">See Also</span></span>  
 <span data-ttu-id="fe7b8-150">[导出到图像文件（报表生成器和 SSRS）](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fe7b8-150">[Exporting to an Image File &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fe7b8-151">呈现行为（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="fe7b8-151">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
