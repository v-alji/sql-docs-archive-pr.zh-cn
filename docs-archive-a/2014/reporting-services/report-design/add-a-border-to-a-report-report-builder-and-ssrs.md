---
title: 向报表添加边框（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf4a0c2c117774a0f3b25ca0644796fd067bc971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692739"
---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="221ca-102">向报表添加边框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="221ca-102">Add a Border to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="221ca-103">通过向表头、表尾和表体本身添加边框（而不是添加线条或矩形），可以为报表添加边框。</span><span class="sxs-lookup"><span data-stu-id="221ca-103">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span>  
  
 <span data-ttu-id="221ca-104">如果在表头和表尾上添加了报表边框，请不要在报表的第一页和最后一页禁用表头和表尾。</span><span class="sxs-lookup"><span data-stu-id="221ca-104">If you add a report border that appears on the page header and footer, do not suppress the header and footer on the first and last pages of the report.</span></span> <span data-ttu-id="221ca-105">如果禁用了，那么报表的第一页和最后一页的顶部或底部的边框可能不完整。</span><span class="sxs-lookup"><span data-stu-id="221ca-105">If you do, the border may appear cut off at the top or bottom of the first and last pages of the report.</span></span> <span data-ttu-id="221ca-106">有关详细信息，请参阅[页眉和页脚（报表生成器和 SSRS）](page-headers-and-footers-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="221ca-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-border-to-a-report"></a><span data-ttu-id="221ca-107">向报表添加边框</span><span class="sxs-lookup"><span data-stu-id="221ca-107">To add a border to a report</span></span>  
  
1.  <span data-ttu-id="221ca-108">右键单击页眉中任何项的外部，然后单击“页眉属性”  。</span><span class="sxs-lookup"><span data-stu-id="221ca-108">Right-click in the header outside any items in the header, and click **Header Properties**.</span></span> <span data-ttu-id="221ca-109">在 **“边框”** 选项卡上，添加所需样式的左边框、上边框和右边框。</span><span class="sxs-lookup"><span data-stu-id="221ca-109">On the **Border** tab, add a left, top, and right border with the style you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="221ca-110"> 如果没有在报表中使用表头，则可以仅围绕表体放置边框，也可以从 **“插入”** 选项卡中添加表头。</span><span class="sxs-lookup"><span data-stu-id="221ca-110">If you do not use headers in your report, you can place borders around just the report body, or you can add headers from the **Insert** tab.</span></span>  
  
2.  <span data-ttu-id="221ca-111">右键单击设计图面上任何项外部的主体，然后单击“主体属性”  。</span><span class="sxs-lookup"><span data-stu-id="221ca-111">Right-click in the body outside any items on the design surface, and click **Body Properties**.</span></span> <span data-ttu-id="221ca-112">在 **“边框”** 选项卡上，添加所需样式的左边框和右边框。</span><span class="sxs-lookup"><span data-stu-id="221ca-112">On the **Border** tab, add a left and right border with the style you want.</span></span>  
  
3.  <span data-ttu-id="221ca-113">右键单击页脚中任何项的外部，然后单击“页脚属性”  。</span><span class="sxs-lookup"><span data-stu-id="221ca-113">Right-click in the footer outside any items in the footer, and click **Footer Properties**.</span></span> <span data-ttu-id="221ca-114">在 **“边框”** 选项卡上，添加所需样式的左边框、下边框和右边框。</span><span class="sxs-lookup"><span data-stu-id="221ca-114">On the **Border** tab, add a left, bottom, and right border with the style you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221ca-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="221ca-115">See Also</span></span>  
 [<span data-ttu-id="221ca-116">矩形和线条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="221ca-116">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
  
  
