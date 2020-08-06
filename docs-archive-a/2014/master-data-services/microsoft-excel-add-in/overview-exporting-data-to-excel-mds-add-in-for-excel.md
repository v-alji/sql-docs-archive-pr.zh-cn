---
title: MDS Add-in for Excel) 中加载数据 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c01bbbc90fcc68c3de976332721b69ad26e606e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590875"
---
# <a name="loading-data-mds-add-in-for-excel"></a><span data-ttu-id="21fb2-102">加载数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="21fb2-102">Loading Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="21fb2-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] ，必须先将数据从 MDS 存储库加载到活动 Excel 工作表中，然后才能使用该工作表。</span><span class="sxs-lookup"><span data-stu-id="21fb2-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository into an active Excel worksheet before you can work with it.</span></span> <span data-ttu-id="21fb2-104">完成数据处理后，将其发布到 MDS 存储库以便其他用户可以共享这些数据。</span><span class="sxs-lookup"><span data-stu-id="21fb2-104">When you are done working with the data, publish it to the MDS repository so other users can share it.</span></span>  
  
 <span data-ttu-id="21fb2-105">您可以加载的数据仅限于您具有访问权限的数据。</span><span class="sxs-lookup"><span data-stu-id="21fb2-105">The data you can load is limited to the data you have permission to access.</span></span> <span data-ttu-id="21fb2-106">访问数据的权限是在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序中或以编程方式设置的。</span><span class="sxs-lookup"><span data-stu-id="21fb2-106">Permission to access data is set in the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application or set programmatically.</span></span>  
  
 <span data-ttu-id="21fb2-107">加载大量数据时，您可以设置在数据可能需要较长时间加载时显示警告。</span><span class="sxs-lookup"><span data-stu-id="21fb2-107">When you load large amounts of data, you can set warnings that are displayed when the data that might take a long time to load.</span></span> <span data-ttu-id="21fb2-108">若要执行此操作，请在 **“选项”** 组中单击 **“设置”**。</span><span class="sxs-lookup"><span data-stu-id="21fb2-108">To do this, in the **Options** group, click **Settings**.</span></span> <span data-ttu-id="21fb2-109">在 **“数据”** 选项卡上，选择 **“显示针对大型数据集的筛选警告”**。</span><span class="sxs-lookup"><span data-stu-id="21fb2-109">On the **Data** tab, select the **Display filter warning for large data sets**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="21fb2-110">只能使用用于 Excel 的 MDS 外接程序在 Excel 中打开和更新启用 MDS 的工作薄。</span><span class="sxs-lookup"><span data-stu-id="21fb2-110">An MDS-enabled workbook must be opened and updated only in Excel with the MDS Add-in for Excel.</span></span> <span data-ttu-id="21fb2-111">不支持在未安装 MDS Excel 外接程序的计算机上的 Excel 中打开启用 MDS 的工作簿，并且可能导致工作簿文件损坏。</span><span class="sxs-lookup"><span data-stu-id="21fb2-111">Opening an MDS-enabled workbook in Excel on a computer in which the MDS Excel Add-in is not installed is not supported, and could cause corruption of the workbook file.</span></span> <span data-ttu-id="21fb2-112">若要与他人共享数据，应该通过电子邮件向他人发送快捷查询文件，而不是保存该工作表并通过电子邮件发送。</span><span class="sxs-lookup"><span data-stu-id="21fb2-112">If you want to share data with someone else, email a shortcut query file to them, rather than saving the worksheet and emailing it.</span></span> <span data-ttu-id="21fb2-113">有关查询的详细信息，请参阅[以电子邮件形式发送快捷查询文件（用于 Excel 的 MDS 外接程序）](email-a-shortcut-query-file-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="21fb2-113">For more information on the query, see [Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).</span></span>  
  
## <a name="filtering-data"></a><span data-ttu-id="21fb2-114">筛选数据</span><span class="sxs-lookup"><span data-stu-id="21fb2-114">Filtering Data</span></span>  
 <span data-ttu-id="21fb2-115">可以在加载前筛选数据，以限制要下载的数据量。</span><span class="sxs-lookup"><span data-stu-id="21fb2-115">You can filter data before loading to limit the amount of data that you're going to download.</span></span> <span data-ttu-id="21fb2-116">这包括选择要加载的属性（列）、属性的显示顺序，以及要处理的成员（数据行）。</span><span class="sxs-lookup"><span data-stu-id="21fb2-116">This includes choosing which attributes (columns) you want to load, the order you want to display the attributes, and the members (rows of data) you want to work with.</span></span> <span data-ttu-id="21fb2-117">有关详细信息，请参阅[在加载前筛选数据 &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="21fb2-117">For more info see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="21fb2-118">自动连接和加载常用数据</span><span class="sxs-lookup"><span data-stu-id="21fb2-118">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="21fb2-119">如果总要连接同一服务器并加载相同的一组数据，您可以创建快捷查询文件，其中包含连接和筛选器信息。</span><span class="sxs-lookup"><span data-stu-id="21fb2-119">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="21fb2-120">有关查询文件的详细信息，请参阅 [快捷查询文件（用于 Excel 的 MDS 外接程序）](shortcut-query-files-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="21fb2-120">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="refreshing-data"></a><span data-ttu-id="21fb2-121">刷新数据</span><span class="sxs-lookup"><span data-stu-id="21fb2-121">Refreshing Data</span></span>  
 <span data-ttu-id="21fb2-122">在您加载 MDS 存储库中的数据后，其他用户可能更新这些数据。</span><span class="sxs-lookup"><span data-stu-id="21fb2-122">Data in the MDS repository may be updated by other users after you load it.</span></span> <span data-ttu-id="21fb2-123">可以检索此数据，而不会丢失对非 MDS 数据所做的更改。</span><span class="sxs-lookup"><span data-stu-id="21fb2-123">You can retrieve this data without losing changes you've made to non-MDS data.</span></span> <span data-ttu-id="21fb2-124">有关详细信息，请参阅[刷新数据（用于 Excel 的 MDS 外接程序）](refreshing-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="21fb2-124">For more information, see [Refreshing Data &#40;MDS Add-in for Excel&#41;](refreshing-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="21fb2-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="21fb2-125">Related Tasks</span></span>  
  
|<span data-ttu-id="21fb2-126">任务说明</span><span class="sxs-lookup"><span data-stu-id="21fb2-126">Task Description</span></span>|<span data-ttu-id="21fb2-127">主题</span><span class="sxs-lookup"><span data-stu-id="21fb2-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="21fb2-128">将 MDS 数据加载到 Excel 中之前先对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="21fb2-128">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="21fb2-129">在加载 &#40;MDS Add-in for Excel 前筛选数据&#41;</span><span class="sxs-lookup"><span data-stu-id="21fb2-129">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|<span data-ttu-id="21fb2-130">将 MDS 数据加载到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="21fb2-130">Load MDS data into Excel.</span></span>|[<span data-ttu-id="21fb2-131">将数据从 MDS 加载到 Excel</span><span class="sxs-lookup"><span data-stu-id="21fb2-131">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="21fb2-132">下载数据前更改列的顺序。</span><span class="sxs-lookup"><span data-stu-id="21fb2-132">Change the order of columns before you download data.</span></span>|[<span data-ttu-id="21fb2-133">对列重新排序（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="21fb2-133">Reorder Columns &#40;MDS Add-in for Excel&#41;</span></span>](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="21fb2-134">相关内容</span><span class="sxs-lookup"><span data-stu-id="21fb2-134">Related Content</span></span>  
  
-   [<span data-ttu-id="21fb2-135">连接（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="21fb2-135">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="21fb2-136">快捷查询文件（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="21fb2-136">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="21fb2-137">用于 Microsoft Excel 的 Master Data Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="21fb2-137">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="21fb2-138">安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="21fb2-138">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  
