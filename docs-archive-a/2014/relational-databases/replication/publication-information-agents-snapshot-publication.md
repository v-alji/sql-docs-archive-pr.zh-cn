---
title: 发布信息，代理（快照发布）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.snapshot.f1
ms.assetid: 599ff80b-392c-43aa-9db2-dc4ed33d4f6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8deb4ac1d8721550c50df40b307aeeb5d3818d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577535"
---
# <a name="publication-information-agents-snapshot-publication"></a><span data-ttu-id="1b310-102">发布信息，代理（快照发布）</span><span class="sxs-lookup"><span data-stu-id="1b310-102">Publication Information, Agents (Snapshot Publication)</span></span>
  <span data-ttu-id="1b310-103">**“代理”** 选项卡显示所选发布的快照代理的摘要信息。</span><span class="sxs-lookup"><span data-stu-id="1b310-103">The **Agents** tab displays summary information on the Snapshot Agent for the selected publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b310-104">选项</span><span class="sxs-lookup"><span data-stu-id="1b310-104">Options</span></span>  
 <span data-ttu-id="1b310-105">有关快照代理的详细信息及相关任务，请右键单击该代理的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="1b310-105">For more detailed information and tasks related to the Snapshot Agent, right-click the row for the agent, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="1b310-106">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="1b310-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="1b310-107">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="1b310-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="1b310-108">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="1b310-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="1b310-109">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="1b310-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="1b310-110">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="1b310-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="1b310-111">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="1b310-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="1b310-112">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="1b310-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="1b310-113">**Status**</span><span class="sxs-lookup"><span data-stu-id="1b310-113">**Status**</span></span>  
 <span data-ttu-id="1b310-114">快照代理的状态。</span><span class="sxs-lookup"><span data-stu-id="1b310-114">The status of the Snapshot Agent.</span></span> <span data-ttu-id="1b310-115">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="1b310-115">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="1b310-116">错误</span><span class="sxs-lookup"><span data-stu-id="1b310-116">Error</span></span>  
  
-   <span data-ttu-id="1b310-117">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="1b310-117">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="1b310-118">未运行</span><span class="sxs-lookup"><span data-stu-id="1b310-118">Not running</span></span>  
  
-   <span data-ttu-id="1b310-119">已完成</span><span class="sxs-lookup"><span data-stu-id="1b310-119">Completed</span></span>  
  
 <span data-ttu-id="1b310-120">**代理**</span><span class="sxs-lookup"><span data-stu-id="1b310-120">**Agent**</span></span>  
 <span data-ttu-id="1b310-121">快照代理。</span><span class="sxs-lookup"><span data-stu-id="1b310-121">The Snapshot Agent.</span></span> <span data-ttu-id="1b310-122">这是与快照发布关联的唯一代理。</span><span class="sxs-lookup"><span data-stu-id="1b310-122">This is the only agent associated with a snapshot publication.</span></span> <span data-ttu-id="1b310-123">分发代理与此发布的订阅关联。</span><span class="sxs-lookup"><span data-stu-id="1b310-123">The Distribution Agent is associated with subscriptions to this publication.</span></span> <span data-ttu-id="1b310-124">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="1b310-124">For more information, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="1b310-125">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="1b310-125">**Last Start Time**</span></span>  
 <span data-ttu-id="1b310-126">代理上次启动的时间。</span><span class="sxs-lookup"><span data-stu-id="1b310-126">The last time the agent started.</span></span>  
  
 <span data-ttu-id="1b310-127">**持续时间**</span><span class="sxs-lookup"><span data-stu-id="1b310-127">**Duration**</span></span>  
 <span data-ttu-id="1b310-128">代理已运行的时间。</span><span class="sxs-lookup"><span data-stu-id="1b310-128">The amount of time the agent has run.</span></span> <span data-ttu-id="1b310-129">如果代理当前正在运行，该时间表示已用时间；如果代理已在之前运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="1b310-129">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="1b310-130">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="1b310-130">**Last Action**</span></span>  
 <span data-ttu-id="1b310-131">在此代理最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="1b310-131">The last action performed during the most recent run of the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b310-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b310-132">See Also</span></span>  
 <span data-ttu-id="1b310-133">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1b310-133">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="1b310-134">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1b310-134">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="1b310-135">监视复制</span><span class="sxs-lookup"><span data-stu-id="1b310-135">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
