---
title: 图像、文本框、矩形和线条（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aa7ad08f-dd49-401e-9619-522e27055bb9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fb9a47bb3b8d68d48be42f8f0a2adddfc3ba130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688583"
---
# <a name="images-text-boxes-rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="0107b-102">图像、文本框、矩形和线条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="0107b-102">Images, Text Boxes, Rectangles, and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0107b-103">除了像表、矩阵和图表这样的数据区域外，报表还可以使用图像、文本框和矩形等其他报表项增添视觉吸引力、突出显示关键信息或提供相关信息。</span><span class="sxs-lookup"><span data-stu-id="0107b-103">In addition to data regions like tables, matrices, and charts, reports use other report items like images, text boxes, and rectangles to add visual interest, highlight key information, or provide related information.</span></span> <span data-ttu-id="0107b-104">您可以更改报表项的格式设置。</span><span class="sxs-lookup"><span data-stu-id="0107b-104">You can change the formatting of a report item.</span></span> <span data-ttu-id="0107b-105">例如，可以添加边框或填充、更改初始可见性或方向，或指定报表项的准确大小和位置。</span><span class="sxs-lookup"><span data-stu-id="0107b-105">For example, you can add a border or padding, change the initial visibility or direction, or specify an exact size and location for the item.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="0107b-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="0107b-106">In This Section</span></span>  
 [<span data-ttu-id="0107b-107">文本框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="0107b-107">Text Boxes &#40;Report Builder and SSRS&#41;</span></span>](text-boxes-report-builder-and-ssrs.md)  
 <span data-ttu-id="0107b-108">文本框可以放在报表上的任何位置，可以包含标签、字段或计算数据。</span><span class="sxs-lookup"><span data-stu-id="0107b-108">Text boxes can be placed anywhere on a report and can contain labels, fields, or calculated data.</span></span> <span data-ttu-id="0107b-109">使用表达式可以定义查看报表时显示在文本框中的值。</span><span class="sxs-lookup"><span data-stu-id="0107b-109">You use expressions to define the value to display in a text box when you view a report.</span></span>  
  
 <span data-ttu-id="0107b-110">表或矩阵中的每个单元也是文本框，您可以按设置独立文本框格式的方式设置这些文本框的格式。</span><span class="sxs-lookup"><span data-stu-id="0107b-110">Every cell in a table or matrix is also a text box, which you can format in the same way that you format stand-alone text boxes.</span></span>  
  
 [<span data-ttu-id="0107b-111">矩形和线条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="0107b-111">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
 <span data-ttu-id="0107b-112">**线条** 以水平、垂直，或沿对角线方向显示。</span><span class="sxs-lookup"><span data-stu-id="0107b-112">**Lines** display horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="0107b-113">线条由起点和终点来定义，可以为其指定各种样式（如粗细和颜色）。</span><span class="sxs-lookup"><span data-stu-id="0107b-113">A line is defined with a start and end point and can have various styles (for example, weight and color) assigned to it.</span></span> <span data-ttu-id="0107b-114">线条没有关联的数据。</span><span class="sxs-lookup"><span data-stu-id="0107b-114">A line has no data associated with it.</span></span>  
  
 <span data-ttu-id="0107b-115">**矩形** 可用作图形元素或其他报表项的容器。</span><span class="sxs-lookup"><span data-stu-id="0107b-115">**Rectangles** can be used as a graphical element, or as a container for other report items.</span></span> <span data-ttu-id="0107b-116">作为图形元素，矩形和线条具有相同的属性。</span><span class="sxs-lookup"><span data-stu-id="0107b-116">As a graphical element, a rectangle has the same properties as a line.</span></span> <span data-ttu-id="0107b-117">作为容器，矩形可用作容纳所有报表项的父容器。</span><span class="sxs-lookup"><span data-stu-id="0107b-117">As a container, a rectangle acts as a parent container for all report items inside it.</span></span> <span data-ttu-id="0107b-118">将报表项放置在父容器中，有助于控制报表项在每个报表页中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="0107b-118">Placing report items in a parent container helps control how they appear on each report page.</span></span>  
  
 [<span data-ttu-id="0107b-119">图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="0107b-119">Images &#40;Report Builder and SSRS&#41;</span></span>](images-report-builder-and-ssrs.md)  
 <span data-ttu-id="0107b-120">图像用于显示报表中的二进制图像数据。</span><span class="sxs-lookup"><span data-stu-id="0107b-120">Images display binary image data in a report.</span></span> <span data-ttu-id="0107b-121">您为图像提供源。</span><span class="sxs-lookup"><span data-stu-id="0107b-121">You provide the source for the image.</span></span> <span data-ttu-id="0107b-122">源可以是对存储在 Web 服务器中的图像的 URL 引用、对嵌入的图像数据的引用，也可以是对数据库中二进制图像数据的引用。</span><span class="sxs-lookup"><span data-stu-id="0107b-122">The source can be a URL reference to an image stored on a Web server, a reference to embedded image data, or a reference to binary image data in a database.</span></span> <span data-ttu-id="0107b-123">报表生成器和报表设计器支持 .bmp、.jpeg、.gif 和 .png 文件。</span><span class="sxs-lookup"><span data-stu-id="0107b-123">Report Builder and Report Designer support .bmp, .jpeg, .gif, and .png files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0107b-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0107b-124">See Also</span></span>  
 [<span data-ttu-id="0107b-125">设置报表项的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="0107b-125">Formatting Report Items &#40;Report Builder and SSRS&#41;</span></span>](formatting-report-items-report-builder-and-ssrs.md)  
  
  
