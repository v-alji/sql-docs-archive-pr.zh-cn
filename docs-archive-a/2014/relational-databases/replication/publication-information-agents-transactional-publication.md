---
title: 发布信息，代理（事务发布）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1a3d50da15ea653a7911e65ad888d5997f47a3f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577536"
---
# <a name="publication-information-agents-transactional-publication"></a><span data-ttu-id="108b1-102">发布信息，代理（事务发布）</span><span class="sxs-lookup"><span data-stu-id="108b1-102">Publication Information, Agents (Transactional Publication)</span></span>
  <span data-ttu-id="108b1-103">**“代理”** 选项卡显示所选发布的代理的摘要信息。</span><span class="sxs-lookup"><span data-stu-id="108b1-103">The **Agents** tab displays summary information on the agents for the selected publication.</span></span> <span data-ttu-id="108b1-104">为所有事务发布显示有关快照代理和日志读取器代理的信息。</span><span class="sxs-lookup"><span data-stu-id="108b1-104">Information on the Snapshot Agent and Log Reader Agent is displayed for all transactional publications.</span></span> <span data-ttu-id="108b1-105">对于那些为排队更新订阅启用的事务发布，将显示有关队列读取器代理的信息。</span><span class="sxs-lookup"><span data-stu-id="108b1-105">Information on the Queue Reader Agent is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="108b1-106">选项</span><span class="sxs-lookup"><span data-stu-id="108b1-106">Options</span></span>  
 <span data-ttu-id="108b1-107">有关代理的详细信息及相关任务，请右键单击相应代理所在的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="108b1-107">For more detailed information and tasks related to an agent, right-click the row for that agent, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="108b1-108">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="108b1-108">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="108b1-109">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="108b1-109">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="108b1-110">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="108b1-110">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="108b1-111">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="108b1-111">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="108b1-112">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="108b1-112">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="108b1-113">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="108b1-113">Filter settings are specific to each grid.</span></span> <span data-ttu-id="108b1-114">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="108b1-114">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="108b1-115">**Status**</span><span class="sxs-lookup"><span data-stu-id="108b1-115">**Status**</span></span>  
 <span data-ttu-id="108b1-116">与该发布关联的各个复制代理的状态。</span><span class="sxs-lookup"><span data-stu-id="108b1-116">The status of each replication agent associated with the publication.</span></span> <span data-ttu-id="108b1-117">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="108b1-117">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="108b1-118">错误</span><span class="sxs-lookup"><span data-stu-id="108b1-118">Error</span></span>  
  
-   <span data-ttu-id="108b1-119">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="108b1-119">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="108b1-120">未运行</span><span class="sxs-lookup"><span data-stu-id="108b1-120">Not running</span></span>  
  
-   <span data-ttu-id="108b1-121">正在运行</span><span class="sxs-lookup"><span data-stu-id="108b1-121">Running</span></span>  
  
-   <span data-ttu-id="108b1-122">已完成</span><span class="sxs-lookup"><span data-stu-id="108b1-122">Completed</span></span>  
  
 <span data-ttu-id="108b1-123">**代理**</span><span class="sxs-lookup"><span data-stu-id="108b1-123">**Agent**</span></span>  
 <span data-ttu-id="108b1-124">与该发布关联的各个复制代理的名称。</span><span class="sxs-lookup"><span data-stu-id="108b1-124">The name of each replication agent associated with the publication.</span></span> <span data-ttu-id="108b1-125">分发代理与此发布的订阅关联。</span><span class="sxs-lookup"><span data-stu-id="108b1-125">The Distribution Agent is associated with subscriptions to this publication.</span></span> <span data-ttu-id="108b1-126">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="108b1-126">For more information, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="108b1-127">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="108b1-127">**Last Start Time**</span></span>  
 <span data-ttu-id="108b1-128">代理上次启动的时间。</span><span class="sxs-lookup"><span data-stu-id="108b1-128">The last time the agent started.</span></span>  
  
 <span data-ttu-id="108b1-129">**持续时间**</span><span class="sxs-lookup"><span data-stu-id="108b1-129">**Duration**</span></span>  
 <span data-ttu-id="108b1-130">代理已运行的时间。</span><span class="sxs-lookup"><span data-stu-id="108b1-130">The amount of time the agent has run.</span></span> <span data-ttu-id="108b1-131">如果代理当前正在运行，该时间表示已用时间；如果代理已在之前运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="108b1-131">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="108b1-132">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="108b1-132">**Last Action**</span></span>  
 <span data-ttu-id="108b1-133">在此代理最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="108b1-133">The last action performed during the most recent run of the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108b1-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="108b1-134">See Also</span></span>  
 <span data-ttu-id="108b1-135">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="108b1-135">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="108b1-136">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="108b1-136">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="108b1-137">监视复制</span><span class="sxs-lookup"><span data-stu-id="108b1-137">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
