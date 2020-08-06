---
title: 查看收集组报告 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb8755c67e6c03bb318fdb86d703f6d647d5a3eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589710"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a><span data-ttu-id="e1790-102">查看收集组报表 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e1790-102">View a Collection Set Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e1790-103">配置了管理数据仓库后，可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看收集组报表。</span><span class="sxs-lookup"><span data-stu-id="e1790-103">After you have configured the management data warehouse, you can view a collection set report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e1790-104">针对安装过程中安装的系统数据收集组提供了报表。</span><span class="sxs-lookup"><span data-stu-id="e1790-104">Reports are provided for the System Data collection sets that are installed during Setup.</span></span> <span data-ttu-id="e1790-105">这些报表包括：</span><span class="sxs-lookup"><span data-stu-id="e1790-105">The reports include the following:</span></span>  
  
-   <span data-ttu-id="e1790-106">磁盘使用情况摘要</span><span class="sxs-lookup"><span data-stu-id="e1790-106">Disk Usage Summary</span></span>  
  
-   <span data-ttu-id="e1790-107">查询统计信息历史记录</span><span class="sxs-lookup"><span data-stu-id="e1790-107">Query Statistics History</span></span>  
  
-   <span data-ttu-id="e1790-108">服务器活动历史记录</span><span class="sxs-lookup"><span data-stu-id="e1790-108">Server Activity History</span></span>  
  
 <span data-ttu-id="e1790-109">此过程会显示 **“磁盘使用情况”** 收集组的报表。</span><span class="sxs-lookup"><span data-stu-id="e1790-109">This procedure displays the report for the **Disk Usage** collection set.</span></span> <span data-ttu-id="e1790-110">您可以使用同样的常规过程来查看其他系统数据收集组的报表。</span><span class="sxs-lookup"><span data-stu-id="e1790-110">You can follow the same general procedure to view the reports for the other System Data collection sets.</span></span>  
  
### <a name="to-view-a-collection-set-report"></a><span data-ttu-id="e1790-111">查看收集组报表</span><span class="sxs-lookup"><span data-stu-id="e1790-111">To view a collection set report</span></span>  
  
1.  <span data-ttu-id="e1790-112">首次上载收集的数据时会为报表创建表。</span><span class="sxs-lookup"><span data-stu-id="e1790-112">The tables for a report are created the first time that the collected data is uploaded.</span></span> <span data-ttu-id="e1790-113">如果尝试在首次上载之前查看报表，则将出现错误并且不会显示报表。</span><span class="sxs-lookup"><span data-stu-id="e1790-113">If you try to view a report before this first upload, an error occurs and no report is displayed.</span></span> <span data-ttu-id="e1790-114">若要上传磁盘使用情况收集组的数据，请在对象资源管理器中依次展开“管理”  文件夹、“数据收集”  和“系统数据收集组”  ，右键单击“磁盘使用情况”  收集组，然后单击“立即收集并上传”  。</span><span class="sxs-lookup"><span data-stu-id="e1790-114">To upload data for the Disk Usage collection set, in Object Explorer, expand the **Management** folder, expand **Data Collection**, expand **System Data Collection Sets**, right-click the **Disk Usage** collection set, and then click **Collect and Upload Now**.</span></span>  
  
2.  <span data-ttu-id="e1790-115">若要查看报表，请在对象资源管理器中依次“管理”  文件夹，右键单击“数据收集”  ，依次指向“报表”  “管理数据仓库”  ，然后单击“磁盘使用情况摘要”  。</span><span class="sxs-lookup"><span data-stu-id="e1790-115">To view the report, in Object Explorer, expand the **Management** folder, right-click **Data Collection**, point to **Reports**, point to **Management Data Warehouse**, and then click **Disk Usage Summary**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1790-116">有些报告可能会在数据收集时间线下显示日历按钮。</span><span class="sxs-lookup"><span data-stu-id="e1790-116">Some reports might display a calendar button under the data collection timeline.</span></span> <span data-ttu-id="e1790-117">单击此按钮可访问 **“数据收集报告日历”** 。</span><span class="sxs-lookup"><span data-stu-id="e1790-117">Click this button to access the **Data Collection Report Calendar**.</span></span>  
  
#### <a name="data-collection-report-calendar"></a><span data-ttu-id="e1790-118">“数据收集报告日历”</span><span class="sxs-lookup"><span data-stu-id="e1790-118">Data Collection Report Calendar</span></span>  
 <span data-ttu-id="e1790-119">使用该对话框可指定要报告的数据的开始日期、开始时间和持续时间。</span><span class="sxs-lookup"><span data-stu-id="e1790-119">Use this dialog box to specify the start date, start time, and duration of the data that you want to report on.</span></span> <span data-ttu-id="e1790-120">例如，可能要报告上星期三某特定 12 小时内服务器的磁盘使用活动。</span><span class="sxs-lookup"><span data-stu-id="e1790-120">For example, you may want to report on the disk usage activity of a server for a specific 12-hour period last Wednesday.</span></span>  
  
 <span data-ttu-id="e1790-121">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="e1790-121">**Start date**</span></span>  
 <span data-ttu-id="e1790-122">输入报表数据的开始日期，或从日历选择一个日期。</span><span class="sxs-lookup"><span data-stu-id="e1790-122">Enter a beginning date for the report data, or select one from the calendar.</span></span>  
  
 <span data-ttu-id="e1790-123">**开始时间**</span><span class="sxs-lookup"><span data-stu-id="e1790-123">**Start time**</span></span>  
 <span data-ttu-id="e1790-124">输入报表数据的开始时间或单击箭头以指定一个时间。</span><span class="sxs-lookup"><span data-stu-id="e1790-124">Enter a beginning time for the report data or specify one by clicking the arrows.</span></span>  
  
 <span data-ttu-id="e1790-125">**Duration**</span><span class="sxs-lookup"><span data-stu-id="e1790-125">**Duration**</span></span>  
 <span data-ttu-id="e1790-126">指定在报表中要包括的时间范围。</span><span class="sxs-lookup"><span data-stu-id="e1790-126">Specify the time range to include in the report.</span></span> <span data-ttu-id="e1790-127">默认值为 240 分钟。</span><span class="sxs-lookup"><span data-stu-id="e1790-127">The default value is 240 minutes.</span></span> <span data-ttu-id="e1790-128">可从以下值中进行选择：15 分钟、60 分钟、240 分钟（4 小时）、720 分钟（12 小时）和 1440 分钟（24 小时）。</span><span class="sxs-lookup"><span data-stu-id="e1790-128">The possible values to select from are 15 minutes, 60 minutes, 240 minutes (4 hours), 720 minutes (12 hours), and 1440 minutes (24 hours).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1790-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1790-129">See Also</span></span>  
 <span data-ttu-id="e1790-130">[数据收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="e1790-130">[Data Collection](data-collection.md) </span></span>  
 <span data-ttu-id="e1790-131">[Management Studio 中的自定义报表](../../ssms/object/custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="e1790-131">[Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) </span></span>  
 [<span data-ttu-id="e1790-132">配置管理数据仓库 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e1790-132">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
