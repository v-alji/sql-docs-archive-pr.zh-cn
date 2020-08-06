---
title: 在加载 (MDS Add-in for Excel) 之前筛选数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6d0ccf667f37763326e27dcd8d0cfc005627ebc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689474"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a><span data-ttu-id="6b29b-102">加载前筛选数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="6b29b-102">Filter Data before Loading (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="6b29b-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] ，当您想要限制要加载到 Excel 中的数据的大小或范围时，可以筛选数据。</span><span class="sxs-lookup"><span data-stu-id="6b29b-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filter data when you want to limit the size or scope of data that you are loading into Excel.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6b29b-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="6b29b-104">Prerequisites</span></span>  
 <span data-ttu-id="6b29b-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="6b29b-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="6b29b-106">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="6b29b-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-filter-data-before-loading"></a><span data-ttu-id="6b29b-107">加载前筛选数据</span><span class="sxs-lookup"><span data-stu-id="6b29b-107">To filter data before loading</span></span>  
  
1.  <span data-ttu-id="6b29b-108">打开 Excel，在 **“主数据”** 选项卡上连接到 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="6b29b-108">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="6b29b-109">有关详细信息，请参阅[连接到 MDS 存储库（用于 Excel 的 MDS 外接程序）](connect-to-an-mds-repository-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="6b29b-109">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="6b29b-110">在 **“主数据资源管理器”** 窗格中，选择所需模型和版本。</span><span class="sxs-lookup"><span data-stu-id="6b29b-110">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="6b29b-111">随之填充实体列表。</span><span class="sxs-lookup"><span data-stu-id="6b29b-111">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="6b29b-112">如果 **“主数据资源管理器”** 窗格不可见，请在 **“连接并加载”** 组中，单击 **“显示资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="6b29b-112">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="6b29b-113">如果 **“主数据资源管理器”** 窗格被禁用，则是因为现有工作表中已包含 MDS 管理的数据。</span><span class="sxs-lookup"><span data-stu-id="6b29b-113">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="6b29b-114">若要启用该窗格，请打开一个新工作表。</span><span class="sxs-lookup"><span data-stu-id="6b29b-114">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="6b29b-115">在 **“主数据资源管理器”** 窗格的实体列表中，单击要筛选的实体。</span><span class="sxs-lookup"><span data-stu-id="6b29b-115">In the **Master Data Explorer** pane, in the list of entities, click the entity you want to filter.</span></span>  
  
4.  <span data-ttu-id="6b29b-116">在功能区上的 **“连接并加载”** 组中，单击 **“筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="6b29b-116">On the ribbon, in the **Connect and Load** group, click **Filter**.</span></span>  
  
5.  <span data-ttu-id="6b29b-117">通过选择要显示的属性（列）、设置列顺序，以及按需筛选数据以便返回较少行，完成填写 **“筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="6b29b-117">Complete the **Filter** dialog box by selecting the attributes (columns) to display, setting the order of the columns, and if needed, filtering the data so fewer rows are returned.</span></span> <span data-ttu-id="6b29b-118">查看 **“摘要”** 窗格了解将返回的数据量。</span><span class="sxs-lookup"><span data-stu-id="6b29b-118">View the **Summary** pane for how much data will be returned.</span></span> <span data-ttu-id="6b29b-119">有关详细信息，请参阅[“筛选器”对话框 &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="6b29b-119">For more information, see [Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md).</span></span>  
  
6.  <span data-ttu-id="6b29b-120">单击 **“加载数据”**。</span><span class="sxs-lookup"><span data-stu-id="6b29b-120">Click **Load Data**.</span></span> <span data-ttu-id="6b29b-121">将使用 MDS 管理的数据填充工作表。</span><span class="sxs-lookup"><span data-stu-id="6b29b-121">The sheet is populated with MDS-managed data.</span></span>  
  
    > [!NOTE]  
    >  -   <span data-ttu-id="6b29b-122">只有前一百万个成员才能加载到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="6b29b-122">Only the first one million members are loaded into Excel.</span></span>  
    > -   <span data-ttu-id="6b29b-123">在受约束的列 (基于域的属性) 中，只加载前1000个值。</span><span class="sxs-lookup"><span data-stu-id="6b29b-123">In columns that are constrained lists (domain-based attributes), only the first 1000 values are loaded.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6b29b-124">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6b29b-124">Next Steps</span></span>  
 [<span data-ttu-id="6b29b-125">将数据从 Excel 发布到 MDS &#40;MDS Add-in for Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="6b29b-125">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b29b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b29b-126">See Also</span></span>  
 <span data-ttu-id="6b29b-127">[MDS Add-in for Excel&#41;中加载数据 &#40;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6b29b-127">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="6b29b-128">["筛选器" 对话框 &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6b29b-128">[Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="6b29b-129">对列重新排序（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="6b29b-129">Reorder Columns &#40;MDS Add-in for Excel&#41;</span></span>](reorder-columns-mds-add-in-for-excel.md)  
  
  
