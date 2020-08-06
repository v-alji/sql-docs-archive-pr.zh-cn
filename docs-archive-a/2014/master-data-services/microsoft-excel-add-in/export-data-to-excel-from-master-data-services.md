---
title: 将数据从 MDS 加载到 Excel |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 35672807d5bb108e9386f892aea1847d45ebeb33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689475"
---
# <a name="load-data-from-mds-into-excel"></a><span data-ttu-id="ce28d-102">将数据从 MDS 加载到 Excel</span><span class="sxs-lookup"><span data-stu-id="ce28d-102">Load Data from MDS into Excel</span></span>
  <span data-ttu-id="ce28d-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] ，必须从 MDS 存储库中加载数据，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="ce28d-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository in order to work with it.</span></span>  
  
 <span data-ttu-id="ce28d-104">如果你想要在加载前筛选数据集，请参阅[在加载前筛选数据 &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) 。</span><span class="sxs-lookup"><span data-stu-id="ce28d-104">If you want to filter the dataset before loading, see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) instead.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ce28d-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="ce28d-105">Prerequisites</span></span>  
 <span data-ttu-id="ce28d-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="ce28d-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ce28d-107">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="ce28d-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-load-data-from-mds-into-excel"></a><span data-ttu-id="ce28d-108">将数据从 MDS 加载到 Excel</span><span class="sxs-lookup"><span data-stu-id="ce28d-108">To load data from MDS into Excel</span></span>  
  
1.  <span data-ttu-id="ce28d-109">打开 Excel，在 **“主数据”** 选项卡上连接到 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="ce28d-109">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="ce28d-110">有关详细信息，请参阅[连接到 MDS 存储库（用于 Excel 的 MDS 外接程序）](connect-to-an-mds-repository-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="ce28d-110">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="ce28d-111">在 **“主数据资源管理器”** 窗格中，选择所需模型和版本。</span><span class="sxs-lookup"><span data-stu-id="ce28d-111">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="ce28d-112">随之填充实体列表。</span><span class="sxs-lookup"><span data-stu-id="ce28d-112">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="ce28d-113">如果 **“主数据资源管理器”** 窗格不可见，请在 **“连接并加载”** 组中，单击 **“显示资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="ce28d-113">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="ce28d-114">如果 **“主数据资源管理器”** 窗格被禁用，则是因为现有工作表中已包含 MDS 管理的数据。</span><span class="sxs-lookup"><span data-stu-id="ce28d-114">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="ce28d-115">若要启用该窗格，请打开一个新工作表。</span><span class="sxs-lookup"><span data-stu-id="ce28d-115">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="ce28d-116">在“主数据资源管理器”\*\*\*\* 窗格的实体列表中，双击要加载的实体。</span><span class="sxs-lookup"><span data-stu-id="ce28d-116">In the **Master Data Explorer** pane, in the list of entities, double-click the entity you want to load.</span></span>  
  
    > [!NOTE]  
    >  -   <span data-ttu-id="ce28d-117">只有前一百万个成员才能加载到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="ce28d-117">Only the first one million members are loaded into Excel.</span></span> <span data-ttu-id="ce28d-118">若要在加载前对列表进行筛选，请在 **“连接并加载”** 组中，单击 **“筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="ce28d-118">To filter the list before loading, on the ribbon in the **Connect and Load** group, click **Filter**.</span></span>  
    > -   <span data-ttu-id="ce28d-119">在作为约束列表（基于域的属性）的列中，只加载前 25,000 个值。</span><span class="sxs-lookup"><span data-stu-id="ce28d-119">In columns that are constrained lists (domain-based attributes), only the first 25,000 values are loaded.</span></span> <span data-ttu-id="ce28d-120">您可以在 excelusersettings.config 文件（位于安装 Excel 的计算机上）的 MaximumDbaEntitySize 属性中更改该数值。</span><span class="sxs-lookup"><span data-stu-id="ce28d-120">You can change this number in the MaximumDbaEntitySize property in the excelusersettings.config file located on the computer that Excel is installed on.</span></span> <span data-ttu-id="ce28d-121">此文件位于 C:\Users \\<user \> \AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices 中 \\ 。</span><span class="sxs-lookup"><span data-stu-id="ce28d-121">This file is located in C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices\\.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce28d-122">使用用于 32 位 Excel 的 Microsoft Excel 外接程序加载文本分隔数据时，如果“要加载的单元计数”\*\*\*\* 和“要发布的单元计数”\*\*\*\* 属性均设置为最大值 1000，则将出现内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="ce28d-122">When you load text-delimited data using the Add-in for Microsoft Excel with 32-bit Excel, and the settings for the **Cell Count to Load** and **Cell Count to Publish** properties are both set to the maximum of 1000, an out-of-memory error will occur.</span></span> <span data-ttu-id="ce28d-123">必须使用 64 位 Excel，才能使用“要加载的单元计数”\*\*\*\* 和“要发布的单元计数”\*\*\*\* 的最大值设置。</span><span class="sxs-lookup"><span data-stu-id="ce28d-123">You have to use 64-bit Excel to use the maximum settings for **Cell Count to Load** and **Cell Count to Publish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ce28d-124">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ce28d-124">Next Steps</span></span>  
 [<span data-ttu-id="ce28d-125">将数据从 Excel 发布到 MDS &#40;MDS Add-in for Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="ce28d-125">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="ce28d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce28d-126">See Also</span></span>  
 <span data-ttu-id="ce28d-127">[MDS Add-in for Excel&#41;中加载数据 &#40;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="ce28d-127">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="ce28d-128">["筛选器" 对话框 &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="ce28d-128">[Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="ce28d-129">MDS Add-in for Excel&#41;发布数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="ce28d-129">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
