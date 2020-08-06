---
title: 添加或删除页眉或页脚（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 72988623-fee8-4a05-9f72-8fcb8e668576
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b29db3f72323c460360c872a0f60d13a808e3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691092"
---
# <a name="add-or-remove-a-page-header-or-footer-report-builder-and-ssrs"></a><span data-ttu-id="f467b-102">添加或删除页眉或页脚（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f467b-102">Add or Remove a Page Header or Footer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f467b-103">您可以向页眉或页脚添加静态文本、图像、线条、矩形和边框。</span><span class="sxs-lookup"><span data-stu-id="f467b-103">You can add static text, images, lines, rectangles, and borders to page headers or footers.</span></span> <span data-ttu-id="f467b-104">如果您希望在页眉或页脚中添加变量或计算数据，还可以在文本框中包含表达式和数据绑定图像。</span><span class="sxs-lookup"><span data-stu-id="f467b-104">You can place expressions and data-bound images in a textbox if you want variable or computed data in a header or footer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f467b-105">各呈现扩展插件处理页眉和页脚的方式互不相同。</span><span class="sxs-lookup"><span data-stu-id="f467b-105">Each rendering extension processes page headers and footers differently.</span></span> <span data-ttu-id="f467b-106">有关详细信息，请参阅[页眉和页脚（报表生成器和 SSRS）](page-headers-and-footers-report-builder-and-ssrs.md)和 [Reporting Services 中的分页（报表生成器和 SSRS）](pagination-in-reporting-services-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f467b-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) and [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-header-or-footer"></a><span data-ttu-id="f467b-107">添加页眉或页脚</span><span class="sxs-lookup"><span data-stu-id="f467b-107">To add a page header or footer</span></span>  
  
1.  <span data-ttu-id="f467b-108">打开报表。</span><span class="sxs-lookup"><span data-stu-id="f467b-108">Open a report.</span></span>  
  
2.  <span data-ttu-id="f467b-109">在设计图面上，右键单击该报表，指向“插入”，然后单击“页眉”或“页脚”    。</span><span class="sxs-lookup"><span data-stu-id="f467b-109">On the design surface, right-click the report, point to **Insert**, and then click **Header** or **Footer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f467b-110">只有当页眉或页脚不是报表的一部分时，才会显示“页眉”和“页脚”选项   。</span><span class="sxs-lookup"><span data-stu-id="f467b-110">The **Header** and **Footer** options appear only when a header or footer is not already part of the report.</span></span>  
  
### <a name="to-configure-a-page-header-or-footer"></a><span data-ttu-id="f467b-111">配置页眉或页脚</span><span class="sxs-lookup"><span data-stu-id="f467b-111">To configure a page header or footer</span></span>  
  
1.  <span data-ttu-id="f467b-112">在设计图面上，右键单击页眉或页脚。</span><span class="sxs-lookup"><span data-stu-id="f467b-112">On the design surface, right-click the page header or footer.</span></span>  
  
2.  <span data-ttu-id="f467b-113">指向 **“插入”** ，然后单击以下项之一将其添加到页眉或页脚区：</span><span class="sxs-lookup"><span data-stu-id="f467b-113">Point to **Insert**, and then click one of the following items to add it to the header or footer area:</span></span>  
  
    -   <span data-ttu-id="f467b-114">**文本框**</span><span class="sxs-lookup"><span data-stu-id="f467b-114">**Textbox**</span></span>  
  
    -   <span data-ttu-id="f467b-115">**线条**</span><span class="sxs-lookup"><span data-stu-id="f467b-115">**Line**</span></span>  
  
    -   <span data-ttu-id="f467b-116">**矩形**</span><span class="sxs-lookup"><span data-stu-id="f467b-116">**Rectangle**</span></span>  
  
    -   <span data-ttu-id="f467b-117">**图像**</span><span class="sxs-lookup"><span data-stu-id="f467b-117">**Image**</span></span>  
  
3.  <span data-ttu-id="f467b-118">右键单击页眉，然后单击“页眉属性”  添加边框、背景图像或颜色，或调整页眉宽度。</span><span class="sxs-lookup"><span data-stu-id="f467b-118">Right-click the page header, and then click **Header Properties** to add borders, background images, or colors, or to adjust the width of the header.</span></span> <span data-ttu-id="f467b-119">然后单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="f467b-119">Then click **OK**.</span></span>  
  
4.  <span data-ttu-id="f467b-120">右键单击页脚，然后单击“页脚属性”  添加边框、背景图像或颜色，或调整页脚宽度。</span><span class="sxs-lookup"><span data-stu-id="f467b-120">Right-click the page footer, and then click **Footer Properties** to add borders, background images, or colors, or to adjust the width of the footer.</span></span> <span data-ttu-id="f467b-121">然后单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="f467b-121">Then click **OK**.</span></span>  
  
### <a name="to-remove-a-page-header-or-footer"></a><span data-ttu-id="f467b-122">删除页眉或页脚</span><span class="sxs-lookup"><span data-stu-id="f467b-122">To remove a page header or footer</span></span>  
  
1.  <span data-ttu-id="f467b-123">打开报表。</span><span class="sxs-lookup"><span data-stu-id="f467b-123">Open a report.</span></span>  
  
2.  <span data-ttu-id="f467b-124">在设计图面上，右键单击页眉或页脚，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="f467b-124">On the design surface, right-click the page header or footer, and then click **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f467b-125">一旦删除，报表中将不再包含页眉或页脚。</span><span class="sxs-lookup"><span data-stu-id="f467b-125">When you remove a page header or footer, you delete it from the report.</span></span> <span data-ttu-id="f467b-126">如果随后再次添加页眉或页脚，您之前添加到页眉或页脚中的任何项都将不再显示。</span><span class="sxs-lookup"><span data-stu-id="f467b-126">Any items that you previously added to the page header or footer will not reappear if you subsequently add the header or footer again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f467b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f467b-127">See Also</span></span>  
 [<span data-ttu-id="f467b-128">页眉和页脚（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f467b-128">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
