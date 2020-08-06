---
title: 为报表和共享数据集处理设置超时值 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time-outs [Reporting Services]
- query time-outs [Reporting Services]
- report processing [Reporting Services], time-outs
- report execution time-outs [Reporting Services]
ms.assetid: 0f9dc61d-d03c-4bbf-8090-7a53844350f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c891b4911994ba2814a612439f141d16e4ad12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586329"
---
# <a name="setting-time-out-values-for-report-and-shared-dataset-processing-ssrs"></a><span data-ttu-id="e1997-102">为报表和共享数据集处理设置超时值 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e1997-102">Setting Time-out Values for Report and Shared Dataset Processing (SSRS)</span></span>
  <span data-ttu-id="e1997-103">可以通过指定超时值来限制使用系统资源的方式。</span><span class="sxs-lookup"><span data-stu-id="e1997-103">You can specify time-out values to set limits on how system resources are used.</span></span> <span data-ttu-id="e1997-104">报表服务器支持两种类型的超时值：</span><span class="sxs-lookup"><span data-stu-id="e1997-104">Report server supports two time-out values:</span></span>  
  
-   <span data-ttu-id="e1997-105">嵌入数据集查询超时值，即报表服务器等待数据库响应的秒数。</span><span class="sxs-lookup"><span data-stu-id="e1997-105">An embedded dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="e1997-106">此值在报表中定义。</span><span class="sxs-lookup"><span data-stu-id="e1997-106">This value is defined in a report.</span></span>  
  
-   <span data-ttu-id="e1997-107">共享数据集查询超时值，即报表服务器等待数据库响应的秒数。</span><span class="sxs-lookup"><span data-stu-id="e1997-107">A shared dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="e1997-108">该值是共享数据集定义的一部分，并且可在您在报表服务器上管理共享数据集时进行管理。</span><span class="sxs-lookup"><span data-stu-id="e1997-108">This value is part of the shared dataset definition and can be changed when you manage the shared dataset on the report server.</span></span>  
  
-   <span data-ttu-id="e1997-109">报表执行超时值，即在停止前报表可持续处理的最大秒数。</span><span class="sxs-lookup"><span data-stu-id="e1997-109">A report execution time-out value is the maximum number of seconds that report processing can continue before it is stopped.</span></span> <span data-ttu-id="e1997-110">此值在系统级定义。</span><span class="sxs-lookup"><span data-stu-id="e1997-110">This value is defined at the system level.</span></span> <span data-ttu-id="e1997-111">可以针对不同的报表采用不同的设置。</span><span class="sxs-lookup"><span data-stu-id="e1997-111">You can vary this setting for individual reports.</span></span>  
  
 <span data-ttu-id="e1997-112">大多数超时错误出现在查询处理期间。</span><span class="sxs-lookup"><span data-stu-id="e1997-112">Most time-out errors occur during query processing.</span></span> <span data-ttu-id="e1997-113">如果遇到超时错误，请尝试增大查询超时值。</span><span class="sxs-lookup"><span data-stu-id="e1997-113">If you are encountering time-out errors, try increasing the query time-out value.</span></span> <span data-ttu-id="e1997-114">请确保将报表执行超时值调整为大于查询超时值。时间段应该足以完成查询和报表处理。</span><span class="sxs-lookup"><span data-stu-id="e1997-114">Make sure to adjust the report execution time-out value so that it is larger than the query time-out. The time period should be sufficient to complete both query and report processing.</span></span>  
  
## <a name="setting-a-query-time-out-for-an-embedded-dataset-in-a-report"></a><span data-ttu-id="e1997-115">为报表中的嵌入数据集设置查询超时值</span><span class="sxs-lookup"><span data-stu-id="e1997-115">Setting a Query Time-Out for an Embedded Dataset in a Report</span></span>  
 <span data-ttu-id="e1997-116">查询超时值是在创作报表过程中在定义嵌入数据集时指定的。</span><span class="sxs-lookup"><span data-stu-id="e1997-116">Query time-out values are specified during report authoring when you define an embedded dataset.</span></span> <span data-ttu-id="e1997-117">该超时值随报表一起存储，它存储在报表定义的 `Timeout` 元素中。</span><span class="sxs-lookup"><span data-stu-id="e1997-117">The time-out value is stored with the report, in the `Timeout` element of the report definition.</span></span> <span data-ttu-id="e1997-118">默认情况下，此值设置为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="e1997-118">By default, this value is set to 30 seconds.</span></span> <span data-ttu-id="e1997-119">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e1997-119">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e1997-120">对已发布报表的属性具有修改权限的用户可以通过编辑报表定义文件来重置此值。</span><span class="sxs-lookup"><span data-stu-id="e1997-120">Users who have permission to modify the properties of a published report can reset this value by editing the report definition file.</span></span>  
  
 <span data-ttu-id="e1997-121">还可以为数据驱动订阅指定查询超时值。</span><span class="sxs-lookup"><span data-stu-id="e1997-121">You can also specify a query time-out value for data-driven subscriptions.</span></span> <span data-ttu-id="e1997-122">查询超时值是在“数据驱动订阅”页中指定的。</span><span class="sxs-lookup"><span data-stu-id="e1997-122">The query time-out value is specified in the Data-Driven Subscription pages.</span></span> <span data-ttu-id="e1997-123">指定的值决定了报表服务器在从订阅服务器数据源检索数据时等待查询处理完成的时间。</span><span class="sxs-lookup"><span data-stu-id="e1997-123">The value you specify determines how long the report server waits for query processing to complete when retrieving data from the subscriber data source.</span></span>  
  
## <a name="setting-a-query-time-out-for-a-shared-dataset"></a><span data-ttu-id="e1997-124">为共享数据集设置查询超时值</span><span class="sxs-lookup"><span data-stu-id="e1997-124">Setting a Query Time-Out for a Shared Dataset</span></span>  
 <span data-ttu-id="e1997-125">当您创建或管理共享数据集时在报表服务器上以秒为单位指定查询超时值。</span><span class="sxs-lookup"><span data-stu-id="e1997-125">Query time-out values are specified in seconds on the report server when you create or manage a shared dataset.</span></span> <span data-ttu-id="e1997-126">默认情况下，该值设置为 0 秒，这相当于无超时值。</span><span class="sxs-lookup"><span data-stu-id="e1997-126">By default, this value is set to 0 seconds, which is the equivalent of no time-out value.</span></span> <span data-ttu-id="e1997-127">有关详细信息，请参阅 [管理共享数据集](../report-data/manage-shared-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="e1997-127">For more information, see [Manage Shared Datasets](../report-data/manage-shared-datasets.md).</span></span>  
  
## <a name="setting-a-report-execution-time-out"></a><span data-ttu-id="e1997-128">设置报表执行超时值</span><span class="sxs-lookup"><span data-stu-id="e1997-128">Setting a Report Execution Time-Out</span></span>  
 <span data-ttu-id="e1997-129">可以通过设置报表执行超时值来限制报表服务器用于处理报表的时间量。</span><span class="sxs-lookup"><span data-stu-id="e1997-129">You can set the report execution time-out value to limit the amount of time that a report server uses to process a report.</span></span> <span data-ttu-id="e1997-130">报表执行超时值可以在报表管理器中指定。</span><span class="sxs-lookup"><span data-stu-id="e1997-130">Report execution time-out values can be specified in Report Manager.</span></span> <span data-ttu-id="e1997-131">可以为“站点设置”页中的所有报表设置默认值，然后覆盖特定报表的“执行”属性页中的值。</span><span class="sxs-lookup"><span data-stu-id="e1997-131">You can set a default value for all reports in the Site Settings page, and then override that value in the Execution properties page for a specific report.</span></span> <span data-ttu-id="e1997-132">默认情况下，该值设置为 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="e1997-132">By default, the value is set to 1800 seconds.</span></span> <span data-ttu-id="e1997-133">有关详细信息，请参阅 [设置报表处理属性](set-report-processing-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e1997-133">For more information, see [Set Report Processing Properties](set-report-processing-properties.md).</span></span>  
  
## <a name="how-report-execution-time-out-values-are-evaluated"></a><span data-ttu-id="e1997-134">报表执行超时值的计算方法</span><span class="sxs-lookup"><span data-stu-id="e1997-134">How Report Execution Time-Out Values are Evaluated</span></span>  
 <span data-ttu-id="e1997-135">报表服务器每隔 60 秒对正在运行的作业进行一次计算。</span><span class="sxs-lookup"><span data-stu-id="e1997-135">The report server evaluates running jobs at 60 second intervals.</span></span> <span data-ttu-id="e1997-136">每隔 60 秒，报表服务器就会将实际处理时间与报表执行超时值进行比较。</span><span class="sxs-lookup"><span data-stu-id="e1997-136">At each 60 second interval, the report server compares actual process time against the report execution time-out value.</span></span> <span data-ttu-id="e1997-137">如果报表的执行时间超过了报表执行超时值，则将停止报表处理。</span><span class="sxs-lookup"><span data-stu-id="e1997-137">If the processing time for a report exceeds the report execution time-out value, report processing will stop.</span></span>  
  
 <span data-ttu-id="e1997-138">请注意，如果指定的超时值小于 60 秒，且报表处理的开始时间和完成时间均发生在报表服务器未对正在运行的作业进行计算的空闲时间段，则报表可以完全执行。</span><span class="sxs-lookup"><span data-stu-id="e1997-138">Note that if you specify a time-out value that is smaller than 60 seconds, the report may execute in full if processing starts and completes during the quiet part of the cycle when the report server is not evaluating running jobs.</span></span> <span data-ttu-id="e1997-139">例如，如果将报表的超时值设置为 10 秒，而运行报表需要 20 秒，并且报表处理开始于 60 秒周期的前期，则报表可以完全处理。</span><span class="sxs-lookup"><span data-stu-id="e1997-139">For example, if you set a time-out value of 10 seconds for a report that takes 20 seconds to run, the report will process in full if report execution starts early in the 60 second cycle.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1997-140">可以在 RSReportServer.config 文件中设置 `RunningRequestsDbCycle` 设置，以更改计算正在运行的作业的频率。</span><span class="sxs-lookup"><span data-stu-id="e1997-140">You can set the `RunningRequestsDbCycle` setting in the RSReportServer.config file to change the frequency of how often running jobs are evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1997-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1997-141">See Also</span></span>  
 <span data-ttu-id="e1997-142">[在 SharePoint 集成模式下 &#40;Reporting Services 设置处理选项&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e1997-142">[Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="e1997-143">[Reporting Services 报表服务器（本机模式）](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e1997-143">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="e1997-144">[管理正在运行的进程](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="e1997-144">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="e1997-145">报表管理器（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="e1997-145">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
