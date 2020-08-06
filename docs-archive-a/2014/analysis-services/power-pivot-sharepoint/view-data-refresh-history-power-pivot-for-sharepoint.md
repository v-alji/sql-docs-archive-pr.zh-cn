---
title: 查看数据刷新历史记录 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- data refresh history [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 4c8d8aa8-794d-4f72-ace3-78d0e688e1a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: c7a858aedcbca7aa1436ff06bdf9ebc61724f511
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692592"
---
# <a name="view-data-refresh-history-powerpivot-for-sharepoint"></a><span data-ttu-id="6982b-102">查看数据刷新历史记录 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="6982b-102">View Data Refresh History (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="6982b-103">数据刷新历史记录用于记录 Excel 工作簿中 PowerPivot 数据的所有数据刷新活动。</span><span class="sxs-lookup"><span data-stu-id="6982b-103">Data refresh history is a record of all data refresh activity for PowerPivot data in an Excel workbook.</span></span> <span data-ttu-id="6982b-104">将根据您提供的计划，对 SharePoint 场中的 Analysis Services 服务器实例执行数据刷新操作。</span><span class="sxs-lookup"><span data-stu-id="6982b-104">Data refresh operations are performed on an Analysis Services server instance in a SharePoint farm on a schedule that you provide.</span></span> <span data-ttu-id="6982b-105">默认情况下，数据刷新历史记录将保留一年时间。</span><span class="sxs-lookup"><span data-stu-id="6982b-105">By default, data refresh history is retained for one year.</span></span> <span data-ttu-id="6982b-106">但是，场管理员可以为使用情况和事件历史记录指定不同的保持策略，以确定将数据刷新记录保留多长时间。</span><span class="sxs-lookup"><span data-stu-id="6982b-106">However, a farm administrator can specify a different retention policy for usage and event history that determines how long data refresh records are kept.</span></span>  
  
 <span data-ttu-id="6982b-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 |SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="6982b-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span></span>  
  
 <span data-ttu-id="6982b-108">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="6982b-108">**In this topic:**</span></span>  
  
 [<span data-ttu-id="6982b-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="6982b-109">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="6982b-110">查看单个工作簿的数据刷新历史记录</span><span class="sxs-lookup"><span data-stu-id="6982b-110">View Data Refresh History for an Individual Workbook</span></span>](#viewhistory)  
  
 [<span data-ttu-id="6982b-111">查看所有工作簿的数据刷新历史记录</span><span class="sxs-lookup"><span data-stu-id="6982b-111">View Data Refresh History for All Workbooks</span></span>](#viewITOps)  
  
 [<span data-ttu-id="6982b-112">使用历史记录信息</span><span class="sxs-lookup"><span data-stu-id="6982b-112">Use History Information</span></span>](#pageelements)  
  
##  <a name="prerequisites"></a><a name="prereq"></a><span data-ttu-id="6982b-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="6982b-113">Prerequisites</span></span>  
 <span data-ttu-id="6982b-114">您必须具有“参与讨论”权限或更高权限，才能查看数据刷新历史记录。</span><span class="sxs-lookup"><span data-stu-id="6982b-114">You must have Contribute permissions or greater to view the data refresh history.</span></span>  
  
 <span data-ttu-id="6982b-115">您必须已启用和计划对包含 PowerPivot 数据的工作簿进行数据刷新。</span><span class="sxs-lookup"><span data-stu-id="6982b-115">You must have enabled and scheduled data refresh on a workbook that contains PowerPivot data.</span></span> <span data-ttu-id="6982b-116">如果您未计划数据刷新，您将看到计划定义页，而不是历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="6982b-116">If you have not scheduled data refresh, you will see the schedule definition page instead of history information.</span></span>  
  
##  <a name="view-data-refresh-history-for-an-individual-workbook"></a><a name="viewhistory"></a> <span data-ttu-id="6982b-117">查看单独工作簿的数据刷新历史记录</span><span class="sxs-lookup"><span data-stu-id="6982b-117">View Data Refresh History for an Individual Workbook</span></span>  
  
1.  <span data-ttu-id="6982b-118">在 SharePoint 站点上，打开一个包含 Excel 工作簿（其中包含 PowerPivot 数据）的库。</span><span class="sxs-lookup"><span data-stu-id="6982b-118">On a SharePoint site, open the library that contains an Excel workbook that contains PowerPivot data.</span></span>  
  
     <span data-ttu-id="6982b-119">没有可视的指示器用于标识 SharePoint 库中的哪些工作簿包含 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="6982b-119">There is no visual indicator that identifies which workbooks in a SharePoint library contain PowerPivot data.</span></span> <span data-ttu-id="6982b-120">您必须事先知道哪个工作簿包含可刷新的 PowerPivot 数据。</span><span class="sxs-lookup"><span data-stu-id="6982b-120">You must know in advance which workbook contains refreshable PowerPivot data.</span></span>  
  
2.  <span data-ttu-id="6982b-121">选择工作簿，然后单击显示在右侧的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="6982b-121">Select the workbook, and then click the down arrow that appears to the right.</span></span>  
  
3.  <span data-ttu-id="6982b-122">选择 **“管理 PowerPivot 数据刷新”**。</span><span class="sxs-lookup"><span data-stu-id="6982b-122">Select **Manage PowerPivot Data Refresh**.</span></span>  
  
 <span data-ttu-id="6982b-123">将出现历史记录页，其中显示当前 Excel 工作簿中 PowerPivot 数据的所有刷新活动的完整记录。</span><span class="sxs-lookup"><span data-stu-id="6982b-123">The history page appears, showing a complete record for all refresh activity for PowerPivot data in the current Excel workbook.</span></span>  
  
##  <a name="view-data-refresh-history-for-all-workbooks"></a><a name="viewITOps"></a> <span data-ttu-id="6982b-124">查看所有工作簿的数据刷新历史记录</span><span class="sxs-lookup"><span data-stu-id="6982b-124">View Data Refresh History for All Workbooks</span></span>  
 <span data-ttu-id="6982b-125">通过使用管理中心中的 PowerPivot 管理面板，场管理员和服务应用程序管理员可全面了解所有 PowerPivot 工作簿的数据刷新历史记录和状态。</span><span class="sxs-lookup"><span data-stu-id="6982b-125">Using the PowerPivot Management Dashboard in Central administration, farm administrators and service application administrators can get a comprehensive view of data refresh history and status for all PowerPivot workbooks.</span></span> <span data-ttu-id="6982b-126">有关详细信息，请参阅 [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md)。</span><span class="sxs-lookup"><span data-stu-id="6982b-126">For more information, see [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).</span></span>  
  
##  <a name="use-history-information"></a><a name="pageelements"></a> <span data-ttu-id="6982b-127">使用历史记录信息</span><span class="sxs-lookup"><span data-stu-id="6982b-127">Use History Information</span></span>  
 <span data-ttu-id="6982b-128">数据刷新历史记录页提供有关每个刷新操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6982b-128">The data refresh history page provides detailed information about each refresh operation.</span></span> <span data-ttu-id="6982b-129">可以使用此页上的信息来确认是否发生了刷新或确定失败原因。</span><span class="sxs-lookup"><span data-stu-id="6982b-129">You can use the information on this page to confirm whether refresh occurred or determine why it failed.</span></span>  
  
|<span data-ttu-id="6982b-130">项</span><span class="sxs-lookup"><span data-stu-id="6982b-130">Item</span></span>|<span data-ttu-id="6982b-131">说明</span><span class="sxs-lookup"><span data-stu-id="6982b-131">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6982b-132">名称</span><span class="sxs-lookup"><span data-stu-id="6982b-132">Name</span></span>|<span data-ttu-id="6982b-133">指定包含 PowerPivot 数据的 Excel 工作簿的文件名。</span><span class="sxs-lookup"><span data-stu-id="6982b-133">Specifies the file name of the Excel workbook that contains PowerPivot data.</span></span>|  
|<span data-ttu-id="6982b-134">当前状态</span><span class="sxs-lookup"><span data-stu-id="6982b-134">Current status</span></span>|<span data-ttu-id="6982b-135">值包括 **“已计划”**、 **“正在刷新”**、 **“成功”** 或 **“失败”**。</span><span class="sxs-lookup"><span data-stu-id="6982b-135">Values include **Scheduled**, **Refreshing**, **Succeeded**, or **Failed**.</span></span><br /><br /> <span data-ttu-id="6982b-136">当您首次创建计划时，将显示 **“已计划”** 。</span><span class="sxs-lookup"><span data-stu-id="6982b-136">**Scheduled** appears when you first create the schedule.</span></span> <span data-ttu-id="6982b-137">在首次运行数据刷新后，将不再显示此状态消息。</span><span class="sxs-lookup"><span data-stu-id="6982b-137">After data refresh runs the first time, this status message no longer appears.</span></span><br /><br /> <span data-ttu-id="6982b-138">**“正在刷新”** 表示正在进行数据刷新。</span><span class="sxs-lookup"><span data-stu-id="6982b-138">**Refreshing** indicates that data refresh is in progress.</span></span> <span data-ttu-id="6982b-139">请求位于进程队列中或当前正在服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="6982b-139">A request is either in the process queue or actively running on the server.</span></span><br /><br /> <span data-ttu-id="6982b-140">**“成功”** 表示最后一个数据刷新操作已完成，并且已将更新的工作簿签回到 SharePoint 库中。</span><span class="sxs-lookup"><span data-stu-id="6982b-140">**Succeeded** indicates that the last data refresh operation completed and the updated workbook is checked back into the SharePoint library.</span></span><br /><br /> <span data-ttu-id="6982b-141">**“失败”** 表示最后一个数据刷新操作未成功。</span><span class="sxs-lookup"><span data-stu-id="6982b-141">**Failed** indicates that the last data refresh operation did not succeed.</span></span> <span data-ttu-id="6982b-142">刷新的数据未保存。</span><span class="sxs-lookup"><span data-stu-id="6982b-142">The refreshed data was not saved.</span></span> <span data-ttu-id="6982b-143">工作簿与开始刷新数据之前包含相同的数据。</span><span class="sxs-lookup"><span data-stu-id="6982b-143">The workbook contains the same data it had before data refresh began.</span></span>|  
|<span data-ttu-id="6982b-144">最近成功刷新</span><span class="sxs-lookup"><span data-stu-id="6982b-144">Last successful refresh</span></span>|<span data-ttu-id="6982b-145">指定成功完成最后一次数据刷新的日期。</span><span class="sxs-lookup"><span data-stu-id="6982b-145">Specifies the date on which the last data refresh completed successfully.</span></span>|  
|<span data-ttu-id="6982b-146">下次计划刷新</span><span class="sxs-lookup"><span data-stu-id="6982b-146">Next schedule refresh</span></span>|<span data-ttu-id="6982b-147">指定计划进行的下一次数据刷新的日期。</span><span class="sxs-lookup"><span data-stu-id="6982b-147">Specifies the date on which the next data refresh is scheduled to occur.</span></span><br /><br /> <span data-ttu-id="6982b-148">**“配置计划”** 链接将您引向计划定义页。</span><span class="sxs-lookup"><span data-stu-id="6982b-148">The **Configure schedule** link takes you to the schedule definition page.</span></span> <span data-ttu-id="6982b-149">如果您对工作簿具有“参与讨论”权限，可以单击此链接，以查看和修改控制工作簿中 PowerPivot 数据的无人参与数据刷新的计划信息。</span><span class="sxs-lookup"><span data-stu-id="6982b-149">If you have Contribute permissions on the workbook, you can click the link to view and modify the schedule information that controls unattended data refresh for PowerPivot data in the workbook.</span></span>|  
|<span data-ttu-id="6982b-150">Started</span><span class="sxs-lookup"><span data-stu-id="6982b-150">Started</span></span>|<span data-ttu-id="6982b-151">在历史记录详细信息部分中， **“已启动”** 表示实际的处理时间。</span><span class="sxs-lookup"><span data-stu-id="6982b-151">Within the history details section, **Started** indicates the actual processing time.</span></span> <span data-ttu-id="6982b-152">实际的处理时间可能与您计划的时间不同。</span><span class="sxs-lookup"><span data-stu-id="6982b-152">The actual processing time might be different from what you scheduled.</span></span> <span data-ttu-id="6982b-153">当服务器上有足够的内存时，将开始处理。</span><span class="sxs-lookup"><span data-stu-id="6982b-153">Processing will begin when sufficient memory is available on the server.</span></span> <span data-ttu-id="6982b-154">如果服务器很忙，处理过程可能在您指定的开始时间之后的若干小时才开始。</span><span class="sxs-lookup"><span data-stu-id="6982b-154">If the server is very busy, the processing might begin several hours after the start time you specified.</span></span>|  
|<span data-ttu-id="6982b-155">已完成</span><span class="sxs-lookup"><span data-stu-id="6982b-155">Completed</span></span>|<span data-ttu-id="6982b-156">在历史记录详细信息部分中， **“已完成”** 指示完成数据刷新操作的时间。</span><span class="sxs-lookup"><span data-stu-id="6982b-156">Within the history details section, **Completed** indicates when the data refresh operation finished.</span></span> <span data-ttu-id="6982b-157">此日期和时间表示将工作簿检回到库中的时间。</span><span class="sxs-lookup"><span data-stu-id="6982b-157">The date and time indicates when the workbook was checked back into the library.</span></span><br /><br /> <span data-ttu-id="6982b-158">如果数据刷新失败，将显示一条或多条错误消息来说明失败的原因。</span><span class="sxs-lookup"><span data-stu-id="6982b-158">If data refresh fails, one or more error messages explain the cause of the failure.</span></span> <span data-ttu-id="6982b-159">您可以展开每条记录，以查看详细状态。</span><span class="sxs-lookup"><span data-stu-id="6982b-159">You can expand each record to view detailed status.</span></span> <span data-ttu-id="6982b-160">将单独列出每个数据源，以及成功消息或解释数据刷新为何未完成的失败消息。</span><span class="sxs-lookup"><span data-stu-id="6982b-160">Each data source is listed individually, alongside success or failure messages that explain why data refresh did not complete.</span></span>|  
|<span data-ttu-id="6982b-161">时间</span><span class="sxs-lookup"><span data-stu-id="6982b-161">Time</span></span>|<span data-ttu-id="6982b-162">提供从开始数据刷新到完成刷新的累计时间。</span><span class="sxs-lookup"><span data-stu-id="6982b-162">Provides the cumulative time from when data refresh started to when it was completed.</span></span>|  
|<span data-ttu-id="6982b-163">状态</span><span class="sxs-lookup"><span data-stu-id="6982b-163">Status</span></span>|<span data-ttu-id="6982b-164">提供有关刷新操作是成功还是失败的历史记录。</span><span class="sxs-lookup"><span data-stu-id="6982b-164">Provides a historical record of whether a refresh operation succeeded or failed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6982b-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6982b-165">See Also</span></span>  
 <span data-ttu-id="6982b-166">[为 &#40;配置使用情况数据收集 PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="6982b-166">[Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="6982b-167">[计划数据刷新 &#40;PowerPivot for SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="6982b-167">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="6982b-168">PowerPivot 数据刷新</span><span class="sxs-lookup"><span data-stu-id="6982b-168">PowerPivot Data Refresh</span></span>](power-pivot-data-refresh.md)  
  
  
