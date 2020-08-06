---
title: 刷新数据 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 58dbe99a-288d-4f1c-9cd5-704d6836c945
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 49b6e7bc19c41911c626965b9d1de132796367f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693394"
---
# <a name="refreshing-data-mds-add-in-for-excel"></a><span data-ttu-id="706e0-102">刷新数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="706e0-102">Refreshing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="706e0-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，当你要从 MDS 存储库中获取最新信息但不想打开新工作表时，可刷新数据。</span><span class="sxs-lookup"><span data-stu-id="706e0-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], refresh data when you want to get the latest information from the MDS repository without opening a new worksheet.</span></span> <span data-ttu-id="706e0-104">您可以刷新所有单元，也可以刷新所选单元。</span><span class="sxs-lookup"><span data-stu-id="706e0-104">You can refresh either all cells or a selection of cells.</span></span> <span data-ttu-id="706e0-105">如果您插入的列中包含自定义公式或其他不由 MDS 管理但您想要保留的数据，这样做会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="706e0-105">This can be useful when you have inserted columns with custom formulas or other data that is not managed in MDS and you want to preserve it.</span></span>  
  
## <a name="when-you-can-refresh-mds-managed-data"></a><span data-ttu-id="706e0-106">何时可以刷新 MDS 管理的数据</span><span class="sxs-lookup"><span data-stu-id="706e0-106">When You Can Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="706e0-107">如果活动工作表已包含 MDS 管理的数据，则您可以刷新该活动工作表中 MDS 管理的数据。</span><span class="sxs-lookup"><span data-stu-id="706e0-107">You can refresh MDS-managed data in an active worksheet if the active worksheet already contains MDS-managed data.</span></span> <span data-ttu-id="706e0-108">如果更改了工作表中的属性值或向工作表添加了成员，则必须在刷新之前先发布所做更改。</span><span class="sxs-lookup"><span data-stu-id="706e0-108">If you have changed attribute values or added members to the worksheet, you must publish your changes before you can refresh.</span></span>  
  
## <a name="refreshing-a-selection"></a><span data-ttu-id="706e0-109">刷新选定内容</span><span class="sxs-lookup"><span data-stu-id="706e0-109">Refreshing a Selection</span></span>  
 <span data-ttu-id="706e0-110">您可以选择刷新所有单元还是只刷新所选单元。</span><span class="sxs-lookup"><span data-stu-id="706e0-110">You have the choice of refreshing all cells or refreshing only selected cells.</span></span> <span data-ttu-id="706e0-111">所选单元必须是连续的。</span><span class="sxs-lookup"><span data-stu-id="706e0-111">The selected cells must be contiguous.</span></span> <span data-ttu-id="706e0-112">如果选择了一组连续单元，则该组中所有的 MDS 托管单元都将更新，以显示服务器上当前存储的值。</span><span class="sxs-lookup"><span data-stu-id="706e0-112">If a set of contiguous cells is selected, all MDS managed cells in that set will be updated to display the values currently stored on the server.</span></span> <span data-ttu-id="706e0-113">并非由 MDS 管理的未更改的行和列不会受任何影响。</span><span class="sxs-lookup"><span data-stu-id="706e0-113">Unchanged rows and columns that are not managed by MDS are not affected in any way.</span></span>  
  
## <a name="what-happens-when-you-refresh-mds-managed-data"></a><span data-ttu-id="706e0-114">刷新 MDS 管理的数据时执行的操作</span><span class="sxs-lookup"><span data-stu-id="706e0-114">What Happens When You Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="706e0-115">在 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中刷新数据时，对工作表中 MDS 管理的数据执行的操作取决于自上次加载数据以来 MDS 存储库中所发生的更改。</span><span class="sxs-lookup"><span data-stu-id="706e0-115">When you refresh data in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], what happens to the MDS-managed data in the sheet depends on what has changed in the MDS repository since you last loaded the data.</span></span>  
  
-   <span data-ttu-id="706e0-116">如果向存储库添加了新成员，这些成员将添加到工作表的末尾并以绿色突出显示。</span><span class="sxs-lookup"><span data-stu-id="706e0-116">If new members have been added to repository, they are added to the end of the worksheet and are highlighted in green.</span></span>  
  
-   <span data-ttu-id="706e0-117">如果从存储库中删除了成员，这些成员会从工作表中删除。</span><span class="sxs-lookup"><span data-stu-id="706e0-117">If members were deleted from the repository, they are deleted from the worksheet.</span></span>  
  
-   <span data-ttu-id="706e0-118">如果属性值在 MDS 存储库中发生了更改，工作表中的值将随 MDS 存储库中的值更新。</span><span class="sxs-lookup"><span data-stu-id="706e0-118">If an attribute value has changed in the MDS repository, the value in the worksheet is updated with value from the MDS repository.</span></span> <span data-ttu-id="706e0-119">单元颜色不会更改。</span><span class="sxs-lookup"><span data-stu-id="706e0-119">The cell color does not change.</span></span>  
  
> [!WARNING]
>  -   <span data-ttu-id="706e0-120">在活动工作表中，如果在 MDS 管理的数据之下的行中存在非 MDS 管理的数据，则可能覆盖这些非 MDS 管理的数据。</span><span class="sxs-lookup"><span data-stu-id="706e0-120">In the active worksheet, if non-managed data exists in rows beneath the MDS-managed data, the non-managed data may be overwritten.</span></span> <span data-ttu-id="706e0-121">发生这种情况是由于您刷新了工作表，添加了与非 MDS 管理的数据重叠的 MDS 管理的新数据行。</span><span class="sxs-lookup"><span data-stu-id="706e0-121">This occurs when you refresh the sheet and new rows of MDS-managed data, which overlap with the non-managed data, are added.</span></span>  
> -   <span data-ttu-id="706e0-122">刷新时，将删除 MDS 管理的单元上的注释。</span><span class="sxs-lookup"><span data-stu-id="706e0-122">When you refresh, comments on MDS-managed cells are deleted.</span></span>  
  
## <a name="how-to-refresh-mds-managed-data"></a><span data-ttu-id="706e0-123">如何刷新 MDS 管理的数据</span><span class="sxs-lookup"><span data-stu-id="706e0-123">How to Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="706e0-124">在功能区上的 **“连接并加载”** 组中， **“刷新”** 按钮提供两个选项： **“全部刷新”** 和 **“刷新所选内容”**。</span><span class="sxs-lookup"><span data-stu-id="706e0-124">In the **Connect and Load** group on the ribbon, the **Refresh** button has two options, **Refresh All** and **Refresh Selection**.</span></span> <span data-ttu-id="706e0-125">功能区按钮的默认操作是 **“全部刷新”**。</span><span class="sxs-lookup"><span data-stu-id="706e0-125">The default action of the ribbon button is **Refresh All**.</span></span> <span data-ttu-id="706e0-126">若要使用服务器的值刷新整个工作表，请单击 **“刷新”** 按钮或选择 **“全部刷新”** 选项。</span><span class="sxs-lookup"><span data-stu-id="706e0-126">To refresh the entire sheet with values from the server, click the **Refresh** button or choose the **Refresh All** option.</span></span> <span data-ttu-id="706e0-127">若要仅刷新工作表中的部分单元格，请选择这些单元格（必须是一个连续选择的单元格区域），然后选择“刷新所选内容”选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="706e0-127">To refresh only some of the cells in a sheet, select the cells (must be one contiguous selection) and choose the **Refresh Selection** option.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="706e0-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="706e0-128">Related Tasks</span></span>  
  
|<span data-ttu-id="706e0-129">任务说明</span><span class="sxs-lookup"><span data-stu-id="706e0-129">Task Description</span></span>|<span data-ttu-id="706e0-130">主题</span><span class="sxs-lookup"><span data-stu-id="706e0-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="706e0-131">创建与 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="706e0-131">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="706e0-132">连接到 MDS 存储库（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="706e0-132">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="706e0-133">将 MDS 数据加载到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="706e0-133">Load MDS data into Excel.</span></span>|[<span data-ttu-id="706e0-134">将数据从 MDS 加载到 Excel</span><span class="sxs-lookup"><span data-stu-id="706e0-134">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="706e0-135">相关内容</span><span class="sxs-lookup"><span data-stu-id="706e0-135">Related Content</span></span>  
  
-   [<span data-ttu-id="706e0-136">连接（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="706e0-136">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="706e0-137">MDS Add-in for Excel&#41;中加载数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="706e0-137">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="706e0-138">用于 Microsoft Excel 的 Master Data Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="706e0-138">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
