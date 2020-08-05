---
title: 添加分页符（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55d6be3ae47827c5a8ff4a5b36e3ff2ce80e1034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577289"
---
# <a name="add-a-page-break-report-builder-and-ssrs"></a><span data-ttu-id="6d864-102">添加分页符（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6d864-102">Add a Page Break (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6d864-103">您可以向数据区域内的矩形、数据区域或组添加分页符，以控制每个页面中的信息量。</span><span class="sxs-lookup"><span data-stu-id="6d864-103">You can add a page break to rectangles, data regions, or groups within data regions to control the amount of information on each page.</span></span> <span data-ttu-id="6d864-104">添加分页符能够提高已发布报表的性能，因为在您查看报表时，系统只需处理每个页面中的项。</span><span class="sxs-lookup"><span data-stu-id="6d864-104">Adding page breaks can improve the performance of published reports because only the items on each page have to be processed as you view the report.</span></span> <span data-ttu-id="6d864-105">如果整个报表位于一个页面中，则您只能在所有项都得到处理后才能查看报表。</span><span class="sxs-lookup"><span data-stu-id="6d864-105">When the whole report is a single page, all items must be processed before you can view the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-break-to-a-data-region"></a><span data-ttu-id="6d864-106">向数据区域添加分页符</span><span class="sxs-lookup"><span data-stu-id="6d864-106">To add a page break to a data region</span></span>  
  
1.  <span data-ttu-id="6d864-107">在设计图面上，右键单击数据区域的角部图柄，然后单击“Tablix 属性”  。</span><span class="sxs-lookup"><span data-stu-id="6d864-107">On the design surface, right-click the corner handle of the data region and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="6d864-108">在 **“常规”** 选项卡中的 **“分页符选项”** 下选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="6d864-108">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="6d864-109">**在以下项前面添加分页符**。</span><span class="sxs-lookup"><span data-stu-id="6d864-109">**Add a page break before**.</span></span> <span data-ttu-id="6d864-110">当您希望在表前面添加分页符时可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6d864-110">Select this option when you want to add a page break before the table.</span></span>  
  
    -   <span data-ttu-id="6d864-111">**在以下项后面添加分页符**。</span><span class="sxs-lookup"><span data-stu-id="6d864-111">**Add a page break after**.</span></span> <span data-ttu-id="6d864-112">当您希望在表后面添加分页符时可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6d864-112">Select this option when you want to add a page break after the table.</span></span>  
  
    -   <span data-ttu-id="6d864-113">**如有可能，调整表的大小以显示在同一页上**。</span><span class="sxs-lookup"><span data-stu-id="6d864-113">**Fit table on one page if possible**.</span></span> <span data-ttu-id="6d864-114">当您希望将数据保留在同一页面时可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6d864-114">Select this option when you want the data to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-rectangle"></a><span data-ttu-id="6d864-115">向矩形添加分页符</span><span class="sxs-lookup"><span data-stu-id="6d864-115">To add a page break to a rectangle</span></span>  
  
1.  <span data-ttu-id="6d864-116">在设计图面上，右键单击要在其中添加分页符的矩形，然后单击“矩形属性”  。</span><span class="sxs-lookup"><span data-stu-id="6d864-116">On the design surface, right-click the rectangle where you want to add a page break, and then click **Rectangle Properties**.</span></span>  
  
2.  <span data-ttu-id="6d864-117">在 **“常规”** 选项卡中的 **“分页符选项”** 下选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="6d864-117">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="6d864-118">**在以下项前面添加分页符**。</span><span class="sxs-lookup"><span data-stu-id="6d864-118">**Add a page break before**.</span></span> <span data-ttu-id="6d864-119">当您希望在矩形前面添加分页符时可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6d864-119">Select this option when you want to add a page break before the rectangle.</span></span>  
  
    -   <span data-ttu-id="6d864-120">**在以下项后面添加分页符**。</span><span class="sxs-lookup"><span data-stu-id="6d864-120">**Add a page break after**.</span></span> <span data-ttu-id="6d864-121">当您希望在矩形后面添加分页符时可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6d864-121">Select this option when you want to add a page break after the rectangle.</span></span>  
  
    -   <span data-ttu-id="6d864-122">**去掉分页符上的边框**。</span><span class="sxs-lookup"><span data-stu-id="6d864-122">**Omit border on page break**.</span></span> <span data-ttu-id="6d864-123">当您希望分页符不带边框时可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6d864-123">Select this option when you do not want a border on the page break.</span></span>  
  
    -   <span data-ttu-id="6d864-124">**如有可能，将内容显示在一页中**。</span><span class="sxs-lookup"><span data-stu-id="6d864-124">**Keep contents together on a single page, if possible**.</span></span> <span data-ttu-id="6d864-125">当您希望将矩形中的内容保留在同一页面时可选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6d864-125">Select this option when you want contents inside the rectangle to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-row-group-in-a-table-matrix-or-list"></a><span data-ttu-id="6d864-126">将分页符添加到表、矩阵或列表中的行组</span><span class="sxs-lookup"><span data-stu-id="6d864-126">To add a page break to a row group in a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="6d864-127">在“分组”窗格中，右键单击行组，然后单击“组属性”  。</span><span class="sxs-lookup"><span data-stu-id="6d864-127">In the Grouping pane, right-click a row group, and then click **Group Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d864-128">将忽略列组上的分页符。</span><span class="sxs-lookup"><span data-stu-id="6d864-128">Page breaks are ignored on column groups.</span></span>  
  
2.  <span data-ttu-id="6d864-129">在 **“分页符”** 选项卡中，选择 **“在组的每个实例之间”** ，以便在表中组的每个实例之间添加一个分页符。</span><span class="sxs-lookup"><span data-stu-id="6d864-129">On the **Page Breaks** tab, select **Between each instance of a group** to add a page break between each instance of a group in the table.</span></span>  
  
3.  <span data-ttu-id="6d864-130">此外，还可以选择 **“同样在组的开头”** 或 **“同样在组的结尾”** ，指定为组在表中的开始位置或结束位置添加分页符。</span><span class="sxs-lookup"><span data-stu-id="6d864-130">Optionally, select **Also at the start of a group** or **Also at the end of a group** to specify that a page break be added when a group starts or ends in the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d864-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d864-131">See Also</span></span>  
 <span data-ttu-id="6d864-132">[Reporting Services 中的分页（报表生成器和 SSRS）](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6d864-132">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6d864-133">[呈现行为（报表生成器和 SSRS）](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6d864-133">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6d864-134">页眉和页脚（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6d864-134">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
