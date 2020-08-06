---
title: 发布信息，跟踪令牌 (事务发布，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.tracertokens.f1
ms.assetid: a115ba95-17ae-45df-91bd-5a1a35f3745f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af84ab9b9122a55367780976056ce95aa597f62a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691662"
---
# <a name="publication-information-tracer-tokens-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="e4119-102">发布信息，跟踪令牌（事务发布，SQL Server 2005 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="e4119-102">Publication Information, Tracer Tokens (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="e4119-103">可以使用“跟踪令牌”\*\*\*\* 选项卡验证连接，以及测量使用事务复制的系统的滞后时间。</span><span class="sxs-lookup"><span data-stu-id="e4119-103">The **Tracer Tokens** tab allows you to validate connections and to measure the latency of a system that uses transactional replication.</span></span> <span data-ttu-id="e4119-104">将令牌（少量数据）写入发布数据库的事务日志中，就像标记典型的复制事务一样对其进行标记，使用令牌可以执行以下计算：</span><span class="sxs-lookup"><span data-stu-id="e4119-104">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="e4119-105">计算在发布服务器上提交事务和在分发服务器上将相应命令插入分发数据库之间所间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="e4119-105">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="e4119-106">计算在分发数据库中插入命令和在订阅服务器上提交相应事务之间所间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="e4119-106">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="e4119-107">通过这些计算可以回答许多问题，包括：</span><span class="sxs-lookup"><span data-stu-id="e4119-107">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="e4119-108">哪个订阅服务器在从发布服务器接收更改时所需的时间最长？</span><span class="sxs-lookup"><span data-stu-id="e4119-108">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="e4119-109">在应当收到跟踪令牌的订阅服务器中，哪些订阅服务器（如果有）没有收到跟踪令牌？</span><span class="sxs-lookup"><span data-stu-id="e4119-109">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
## <a name="options"></a><span data-ttu-id="e4119-110">选项</span><span class="sxs-lookup"><span data-stu-id="e4119-110">Options</span></span>  
 <span data-ttu-id="e4119-111">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="e4119-111">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="e4119-112">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="e4119-112">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="e4119-113">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="e4119-113">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="e4119-114">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="e4119-114">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="e4119-115">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="e4119-115">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="e4119-116">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="e4119-116">Filter settings are specific to each grid.</span></span> <span data-ttu-id="e4119-117">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="e4119-117">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="e4119-118">**插入跟踪器**</span><span class="sxs-lookup"><span data-stu-id="e4119-118">**Insert Tracer**</span></span>  
 <span data-ttu-id="e4119-119">单击此项可以在发布服务器的事务日志中插入跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="e4119-119">Click to insert a tracer token in the transaction log at the Publisher.</span></span>  
  
 <span data-ttu-id="e4119-120">**插入时间**</span><span class="sxs-lookup"><span data-stu-id="e4119-120">**Time inserted**</span></span>  
 <span data-ttu-id="e4119-121">选择插入跟踪令牌的时间，以便从该时间开始显示滞后时间信息。</span><span class="sxs-lookup"><span data-stu-id="e4119-121">Select a time at which a tracer token was inserted to display latency information from that time.</span></span> <span data-ttu-id="e4119-122">默认情况下，从当前时间开始显示信息。</span><span class="sxs-lookup"><span data-stu-id="e4119-122">By default, information from the most recent time is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4119-123">跟踪令牌信息的保留时间与其他历史数据的保留时间一样长，该时间由分发数据库的历史记录保持期来控制。</span><span class="sxs-lookup"><span data-stu-id="e4119-123">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="e4119-124">若要了解如何更改分发数据库属性，请参阅[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e4119-124">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
 <span data-ttu-id="e4119-125">**订阅**</span><span class="sxs-lookup"><span data-stu-id="e4119-125">**Subscription**</span></span>  
 <span data-ttu-id="e4119-126">发布的每个订阅的名称。</span><span class="sxs-lookup"><span data-stu-id="e4119-126">The name of each subscription to the publication.</span></span>  
  
 <span data-ttu-id="e4119-127">**发布服务器到分发服务器**</span><span class="sxs-lookup"><span data-stu-id="e4119-127">**Publisher to Distributor**</span></span>  
 <span data-ttu-id="e4119-128">在发布服务器上提交事务和在分发服务器上将相应命令插入分发数据库之间所间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="e4119-128">The elapsed time between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span> <span data-ttu-id="e4119-129">值为 **“挂起”** 指示令牌尚未到达分发服务器。</span><span class="sxs-lookup"><span data-stu-id="e4119-129">A value of **Pending** indicates that the token has not yet reached the Distributor.</span></span> <span data-ttu-id="e4119-130">如果持续显示挂起状态，请确保日志读取器代理正在运行。</span><span class="sxs-lookup"><span data-stu-id="e4119-130">If the pending state persists, ensure that the Log Reader Agent is running.</span></span>  
  
 <span data-ttu-id="e4119-131">**分发服务器到订阅服务器**</span><span class="sxs-lookup"><span data-stu-id="e4119-131">**Distributor to Subscriber**</span></span>  
 <span data-ttu-id="e4119-132">在分发数据库中插入命令和在订阅服务器上提交相应事务之间所间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="e4119-132">The elapsed time between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span> <span data-ttu-id="e4119-133">值为 **“挂起”** 指示令牌尚未到达订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e4119-133">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span> <span data-ttu-id="e4119-134">如果持续显示挂起状态，请确保分发代理正在运行。</span><span class="sxs-lookup"><span data-stu-id="e4119-134">If the pending state persists, ensure that the Distribution Agent is running.</span></span>  
  
 <span data-ttu-id="e4119-135">**总延迟**</span><span class="sxs-lookup"><span data-stu-id="e4119-135">**Total Latency**</span></span>  
 <span data-ttu-id="e4119-136">在发布服务器上提交事务和在订阅服务器上提交相应事务之间所间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="e4119-136">The elapsed time between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="e4119-137">该值表示对于此订阅服务器，此时复制系统的端对端滞后时间。</span><span class="sxs-lookup"><span data-stu-id="e4119-137">This represents the end-to-end latency of the replication system for this Subscriber at this time.</span></span> <span data-ttu-id="e4119-138">值为 **“挂起”** 指示令牌尚未到达订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e4119-138">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4119-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4119-139">See Also</span></span>  
 <span data-ttu-id="e4119-140">[启动和停止复制代理 (SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="e4119-140">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="e4119-141">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e4119-141">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="e4119-142">[为事务复制测量滞后时间并验证连接](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e4119-142">[Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span></span>  
 <span data-ttu-id="e4119-143">[用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e4119-143">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="e4119-144">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e4119-144">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="e4119-145">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="e4119-145">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
