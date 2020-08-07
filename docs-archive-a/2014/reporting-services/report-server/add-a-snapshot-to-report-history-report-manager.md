---
title: 向报表历史记录添加快照（报表管理器）| Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
helpviewer_keywords:
- report history [Reporting Services], adding snapshots
- historical data [Reporting Services]
- snapshots [Reporting Services], adding report snapshots
- adding snapshots to report history
- report snapshots [Reporting Services], adding
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 84d4c264ab0b82fca2a34e6356b53113d63e6994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588325"
---
# <a name="add-a-snapshot-to-report-history-report-manager"></a><span data-ttu-id="0933a-102">向报表历史记录添加快照（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="0933a-102">Add a Snapshot to Report History (Report Manager)</span></span>

<span data-ttu-id="0933a-103">报表历史记录是随着时间变化而创建的报表快照的集合。</span><span class="sxs-lookup"><span data-stu-id="0933a-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="0933a-104">报表快照是包含在特定时间点检索到的布局信息以及查询结果的报表。</span><span class="sxs-lookup"><span data-stu-id="0933a-104">A report snapshot is a report that contains layout information and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="0933a-105">与按需运行报表（在选择该报表时可获得最新的查询结果）不同，报表快照按计划进行处理，再保存到报表服务器中。</span><span class="sxs-lookup"><span data-stu-id="0933a-105">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="0933a-106">当您选择报表快照进行查看时，报表服务器将在报表服务器数据库中检索存储的报表，然后显示快照创建时报表的数据和布局。</span><span class="sxs-lookup"><span data-stu-id="0933a-106">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
<span data-ttu-id="0933a-107">报表快照不以特定的呈现格式进行保存。</span><span class="sxs-lookup"><span data-stu-id="0933a-107">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="0933a-108">相反，将以用户或应用程序发出请求时的最终查看格式（如 HTML）来呈现报表快照。</span><span class="sxs-lookup"><span data-stu-id="0933a-108">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="0933a-109">延迟呈现会使快照具有可移植性。</span><span class="sxs-lookup"><span data-stu-id="0933a-109">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="0933a-110">报表可以采用适用于请求设备或 Web 浏览器的正确格式呈现。</span><span class="sxs-lookup"><span data-stu-id="0933a-110">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
## <a name="to-manually-add-snapshots-to-report-history"></a><span data-ttu-id="0933a-111">向报表历史记录中手动添加快照</span><span class="sxs-lookup"><span data-stu-id="0933a-111">To manually add snapshots to report history</span></span>

1. <span data-ttu-id="0933a-112">在报表管理器中，导航到“目录”页，将鼠标悬停在要查看其历史记录的项之上，然后单击下拉箭头  。</span><span class="sxs-lookup"><span data-stu-id="0933a-112">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>
  
2. <span data-ttu-id="0933a-113">在下拉菜单中，单击 **“查看报表历史记录”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-113">In the drop-down menu, click **View Report History**.</span></span>  
  
3. <span data-ttu-id="0933a-114">单击 **“新建快照”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-114">Click **New Snapshot**.</span></span> <span data-ttu-id="0933a-115">将在 **“运行时间”** 列中创建一个新快照。</span><span class="sxs-lookup"><span data-stu-id="0933a-115">A new snapshot is created in the **When Run** column.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0933a-116">为此，管理员必须将报表历史记录配置为 **“允许手动创建历史记录”**。</span><span class="sxs-lookup"><span data-stu-id="0933a-116">In order to do this, the report history must be configured by the administrator to **Allow history to be created manually**.</span></span> <span data-ttu-id="0933a-117">有关详细信息，请参阅 [限制报表历史记录（报表管理器）](../reports/limit-report-history-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0933a-117">For more information, see [Limit Report History &#40;Report Manager&#41;](../reports/limit-report-history-report-manager.md).</span></span>

4. <span data-ttu-id="0933a-118">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="0933a-118">Click **Apply**.</span></span>

## <a name="to-automatically-add-all-snapshots-to-report-history"></a><span data-ttu-id="0933a-119">自动向报表历史记录中添加所有快照</span><span class="sxs-lookup"><span data-stu-id="0933a-119">To automatically add all snapshots to report history</span></span>  
  
1. <span data-ttu-id="0933a-120">对于已配置为作为报表执行快照运行的报表，可以设置其他属性以在每次刷新该快照时将该快照的副本保存到报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="0933a-120">For a report that is already configured to run as a report execution snapshot, you can set additional properties to save a copy of the snapshot to report history each time the snapshot is refreshed.</span></span>  
  
2. <span data-ttu-id="0933a-121">在报表管理器中，导航到“目录”页，将鼠标悬停在要查看其历史记录的项之上，然后单击下拉箭头  。</span><span class="sxs-lookup"><span data-stu-id="0933a-121">In Report Manager, navigate to the **Contents** page, hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
3. <span data-ttu-id="0933a-122">在下拉菜单中，单击 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-122">In the drop-down menu, click **Manage**.</span></span>  
  
4. <span data-ttu-id="0933a-123">单击 **“快照选项”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-123">Click **Snapshot Options**.</span></span>  
  
5. <span data-ttu-id="0933a-124">选中 **“在历史记录中存储所有报表执行快照”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="0933a-124">Select the check box for **Store all report execution snapshots in history**.</span></span>  
  
6. <span data-ttu-id="0933a-125">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="0933a-125">Click **Apply**.</span></span>  
  
### <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a><span data-ttu-id="0933a-126">基于计划自动向报表历史记录中添加快照</span><span class="sxs-lookup"><span data-stu-id="0933a-126">To automatically add snapshots to report history based on a schedule</span></span>  
  
1. <span data-ttu-id="0933a-127">在报表管理器中，导航到“目录”页，将鼠标悬停在要查看其历史记录的项之上，然后单击下拉箭头  。</span><span class="sxs-lookup"><span data-stu-id="0933a-127">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
2. <span data-ttu-id="0933a-128">在下拉菜单中，单击 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-128">In the drop-down menu, click **Manage**.</span></span>  
  
3. <span data-ttu-id="0933a-129">单击 **“快照选项”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-129">Click **Snapshot Options**.</span></span>  
  
4. <span data-ttu-id="0933a-130">选中 **“使用以下计划将快照添加到报表历史记录中”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="0933a-130">Select the check box for **Use the following schedule to add snapshots to report history**.</span></span> <span data-ttu-id="0933a-131">执行以下某种方案：</span><span class="sxs-lookup"><span data-stu-id="0933a-131">Perform one of the following:</span></span>  
  
    - <span data-ttu-id="0933a-132">选择“报表特定计划”  。</span><span class="sxs-lookup"><span data-stu-id="0933a-132">Select **Report-specific schedule**.</span></span> <span data-ttu-id="0933a-133">填入计划详细信息，选择计划的开始日期和结束日期，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-133">Fill in the schedule details, select the start and end dates for the schedule, and then click **OK**.</span></span>  
  
    - <span data-ttu-id="0933a-134">选择 **“共享计划”** 。</span><span class="sxs-lookup"><span data-stu-id="0933a-134">Select **Shared schedule**.</span></span> <span data-ttu-id="0933a-135">从列表中选择首选计划。</span><span class="sxs-lookup"><span data-stu-id="0933a-135">From the list, select the preferred schedule.</span></span>  
  
5. <span data-ttu-id="0933a-136">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="0933a-136">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0933a-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0933a-137">See Also</span></span>

- [<span data-ttu-id="0933a-138">配置报表的执行属性（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="0933a-138">Configure Execution Properties for a Report  &#40;Report Manager&#41;</span></span>](../reports/configure-execution-properties-for-a-report-report-manager.md)
- [<span data-ttu-id="0933a-139">打开和关闭报表（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="0933a-139">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)
- [<span data-ttu-id="0933a-140">限制报表历史记录（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="0933a-140">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)
- [<span data-ttu-id="0933a-141">计划</span><span class="sxs-lookup"><span data-stu-id="0933a-141">Schedules</span></span>](../subscriptions/schedules.md)   
- [<span data-ttu-id="0933a-142">报表管理器（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="0933a-142">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)