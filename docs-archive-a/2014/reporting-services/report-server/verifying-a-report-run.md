---
title: 验证报表运行情况 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- auditing [Reporting Services]
- verifying report execution
- logs [Reporting Services], verifying report run
- report execution data [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services], verifying execution
- checking report execution
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c11c57f7c5f67b2557f5637ad10658abc9f80606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586313"
---
# <a name="verifying-a-report-run"></a><span data-ttu-id="3ac97-102">验证报表运行情况</span><span class="sxs-lookup"><span data-stu-id="3ac97-102">Verifying a Report Run</span></span>
  <span data-ttu-id="3ac97-103">若要查看报表处理状态的有关信息，则可以使用日志文件或参考在报表管理器中随报表显示的状态信息。</span><span class="sxs-lookup"><span data-stu-id="3ac97-103">To view information about the status of report processing, you can use log files or refer to status information that is displayed with the report in Report Manager.</span></span>  
  
## <a name="sources-of-report-execution-data"></a><span data-ttu-id="3ac97-104">报表执行数据的源</span><span class="sxs-lookup"><span data-stu-id="3ac97-104">Sources of Report Execution Data</span></span>  
 <span data-ttu-id="3ac97-105">报表执行日志提供了有关报表执行情况的综合信息，其中包括：报表的名称、运行报表的用户的名称、报表执行时间以及用于分发报表的传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="3ac97-105">The report execution logs provide comprehensive information about report execution, including the name of the report, the name of the user who ran the report, report execution time, and the delivery extension used to distribute the report.</span></span> <span data-ttu-id="3ac97-106">若要查看和分析此数据，可以将报表执行日志复制到便于查询和报告的数据库表中。</span><span class="sxs-lookup"><span data-stu-id="3ac97-106">To view and analyze this data, you can copy the report execution log into database tables that are easy to query and report on.</span></span>  
  
 <span data-ttu-id="3ac97-107">日志文件包含有关报表执行情况和其他服务器活动的许多条目。</span><span class="sxs-lookup"><span data-stu-id="3ac97-107">Log files contain many entries about report execution and other server activity.</span></span> <span data-ttu-id="3ac97-108">由于日志文件包含大量数据，因此，如果您只想验证上一次运行报表的时间，则可以使用报表管理器。</span><span class="sxs-lookup"><span data-stu-id="3ac97-108">Because log files contain so much data, you may want to use Report Manager if you only want to verify when the report last ran.</span></span> <span data-ttu-id="3ac97-109">如果需要其他信息，就必须查看日志文件。</span><span class="sxs-lookup"><span data-stu-id="3ac97-109">If you require additional information, you must view the log files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ac97-110">报表管理器不显示按需运行的报表的处理时间。</span><span class="sxs-lookup"><span data-stu-id="3ac97-110">Report Manager does not show the processing times of reports that run on demand.</span></span>  
  
 <span data-ttu-id="3ac97-111">下表对如何查看各种报表的处理日期和时间进行了说明：</span><span class="sxs-lookup"><span data-stu-id="3ac97-111">The following table describes how to view the processing date and time for various types of reports.</span></span>  
  
|<span data-ttu-id="3ac97-112">报表类型</span><span class="sxs-lookup"><span data-stu-id="3ac97-112">For this type of report</span></span>|<span data-ttu-id="3ac97-113">日期和时间信息所在位置</span><span class="sxs-lookup"><span data-stu-id="3ac97-113">Date and time information is located here</span></span>|<span data-ttu-id="3ac97-114">查看信息所需操作</span><span class="sxs-lookup"><span data-stu-id="3ac97-114">To view the information, do the following</span></span>|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|<span data-ttu-id="3ac97-115">作为报表快照运行的报表。</span><span class="sxs-lookup"><span data-stu-id="3ac97-115">A report that runs as a report snapshot.</span></span>|<span data-ttu-id="3ac97-116">在“内容”页上。</span><span class="sxs-lookup"><span data-stu-id="3ac97-116">On the Contents page.</span></span> <span data-ttu-id="3ac97-117">有关详细信息，请参阅[“内容”页（报表管理器）](../contents-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="3ac97-117">For more information, see [Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md).</span></span>|<span data-ttu-id="3ac97-118">1) 找到包含该报表的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ac97-118">1) Locate the folder that contains the report.</span></span><br /><span data-ttu-id="3ac97-119">2) 在“详细信息”视图中设置该文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ac97-119">2) Set the folder in Details view.</span></span><br /><span data-ttu-id="3ac97-120">3) 3) 请注意 "**运行时间**" 列中的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="3ac97-120">3) 3) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="3ac97-121">报表历史记录中的快照。</span><span class="sxs-lookup"><span data-stu-id="3ac97-121">A snapshot in report history.</span></span>|<span data-ttu-id="3ac97-122">在“历史记录”属性页上。</span><span class="sxs-lookup"><span data-stu-id="3ac97-122">On the History Properties page.</span></span> <span data-ttu-id="3ac97-123">有关详细信息，请参阅[“快照选项”属性页（报表管理器）](../snapshot-options-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="3ac97-123">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../snapshot-options-properties-page-report-manager.md).</span></span>|<span data-ttu-id="3ac97-124">1) 打开该报表。</span><span class="sxs-lookup"><span data-stu-id="3ac97-124">1) Open the report.</span></span><br /><span data-ttu-id="3ac97-125">2) 单击“属性”页  。</span><span class="sxs-lookup"><span data-stu-id="3ac97-125">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="3ac97-126">3) 单击“历史记录”选项卡  。</span><span class="sxs-lookup"><span data-stu-id="3ac97-126">3) Click the **History** tab.</span></span><br /><span data-ttu-id="3ac97-127">4) 请注意“运行时间”列中的日期和时间  。</span><span class="sxs-lookup"><span data-stu-id="3ac97-127">4) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="3ac97-128">缓存的报表。</span><span class="sxs-lookup"><span data-stu-id="3ac97-128">A cached report.</span></span>|<span data-ttu-id="3ac97-129">在用于创建和刷新该缓存报表的计划中。</span><span class="sxs-lookup"><span data-stu-id="3ac97-129">In the schedule used to create and refresh the cached report.</span></span>|<span data-ttu-id="3ac97-130">1) 打开该报表。</span><span class="sxs-lookup"><span data-stu-id="3ac97-130">1) Open the report.</span></span><br /><span data-ttu-id="3ac97-131">2) 单击“属性”页  。</span><span class="sxs-lookup"><span data-stu-id="3ac97-131">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="3ac97-132">3) 单击“执行”选项卡  。</span><span class="sxs-lookup"><span data-stu-id="3ac97-132">3) Click the **Execution** tab.</span></span><br /><span data-ttu-id="3ac97-133">4) 打开该计划。</span><span class="sxs-lookup"><span data-stu-id="3ac97-133">4) Open the schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ac97-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ac97-134">See Also</span></span>  
 <span data-ttu-id="3ac97-135">[Reporting Services 日志文件和来源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="3ac97-135">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="3ac97-136">[设置报表处理属性](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3ac97-136">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="3ac97-137">报表管理器（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="3ac97-137">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
