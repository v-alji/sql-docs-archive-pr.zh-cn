---
title: "\"分发服务器设置\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.DistributorSettings.f1
helpviewer_keywords:
- Distributor Settings dialog box
ms.assetid: 8276a521-bdd1-4783-bdb6-7ab43499c0ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b864620f155e899868c95f58350f98e2b659c4e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578110"
---
# <a name="sql-server-replication-distributor-settings-dialog-box"></a><span data-ttu-id="c2cf6-102">SQL Server 复制 "分发服务器设置" 对话框</span><span class="sxs-lookup"><span data-stu-id="c2cf6-102">SQL Server Replication 'Distributor Settings' dialog box</span></span>
  <span data-ttu-id="c2cf6-103">使用 **“分发服务器设置”** 对话框，可以更改已添加到复制监视器左窗格中的分发服务器的设置。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-103">The **Distributor Settings** dialog box enables you to change settings for Distributors that were added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c2cf6-104">选项</span><span class="sxs-lookup"><span data-stu-id="c2cf6-104">Options</span></span>  
 <span data-ttu-id="c2cf6-105">**复制监视器启动时自动连接**</span><span class="sxs-lookup"><span data-stu-id="c2cf6-105">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="c2cf6-106">选择此选项可以允许复制监视器连接到分发服务器并检索状态信息。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-106">Select to let Replication Monitor connect to the Distributor and retrieve status information.</span></span>  
  
 <span data-ttu-id="c2cf6-107">**Connection**</span><span class="sxs-lookup"><span data-stu-id="c2cf6-107">**Connection**</span></span>  
 <span data-ttu-id="c2cf6-108">单击此选项可以显示 **“连接到服务器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-108">Click to display the **Connect to Server** dialog box.</span></span> <span data-ttu-id="c2cf6-109">通过该对话框可以查看和更改复制监视器用来连接分发服务器的连接属性和凭据。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-109">This enables you to view and change the connection properties and credentials that Replication Monitor uses to connect to the Distributor.</span></span>  
  
 <span data-ttu-id="c2cf6-110">**自动刷新此分发服务器及其发布的状态**</span><span class="sxs-lookup"><span data-stu-id="c2cf6-110">**Automatically refresh the status of this Distributor and its publications**</span></span>  
 <span data-ttu-id="c2cf6-111">选择此选项可以允许复制监视器自动刷新分发服务器的状态。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-111">Select to let Replication Monitor automatically refresh the status for the Distributor.</span></span> <span data-ttu-id="c2cf6-112">如果选择了此选项，复制监视器将基于 **“刷新速率”** 选项中设置的轮询间隔轮询分发服务器，以获取状态信息。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-112">If this option is selected, Replication Monitor polls the Distributor for status information based on the polling interval set by the **Refresh rate** option.</span></span> <span data-ttu-id="c2cf6-113">有关在复制监视器中刷新的详细信息，请参阅 [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-113">For more information about refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="c2cf6-114">**“刷新速率”**</span><span class="sxs-lookup"><span data-stu-id="c2cf6-114">**Refresh rate**</span></span>  
 <span data-ttu-id="c2cf6-115">输入一个值（秒），指定复制监视器对分发服务器的轮询频率（以了解状态信息）。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-115">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="c2cf6-116">较低的值会导致更频繁地轮询。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-116">Lower values result in more frequent polling.</span></span> <span data-ttu-id="c2cf6-117">如果您正在监视多个发布服务器，这可能会影响分发服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-117">This can affect performance at the Distributor if you are monitoring many Publishers.</span></span> <span data-ttu-id="c2cf6-118">建议您测试系统，以确定一个适当的值。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-118">We recommend that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="c2cf6-119">如果在复制监视器的任意详细信息窗口中选择 **“自动刷新”** ，则也将使用 **“刷新速率”** 设置。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-119">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="c2cf6-120">**在以下组中显示此分发服务器的所有发布服务器**</span><span class="sxs-lookup"><span data-stu-id="c2cf6-120">**Show all Publishers of this Distributor in the following group**</span></span>  
 <span data-ttu-id="c2cf6-121">从该列表中选择某个发布服务器组。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-121">Select a Publisher group from the list.</span></span> <span data-ttu-id="c2cf6-122">该发布服务器显示在左窗格中此组下面。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-122">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="c2cf6-123">通过组可以组织发布服务器，而且对复制的功能没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-123">Groups provide a way for you to organize Publishers and do not affect how replication functions.</span></span>  
  
 <span data-ttu-id="c2cf6-124">**新建组**</span><span class="sxs-lookup"><span data-stu-id="c2cf6-124">**New Group**</span></span>  
 <span data-ttu-id="c2cf6-125">单击此项可创建新的发布服务器组。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-125">Click to create a new Publisher group.</span></span> <span data-ttu-id="c2cf6-126">发布服务器组提供了在复制监视器内组织发布服务器的简便方法。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-126">A Publisher group provides a way for you to conveniently organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="c2cf6-127">组既不影响数据的复制，也不影响复制拓扑中服务器之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c2cf6-127">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cf6-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2cf6-128">See Also</span></span>  
 <span data-ttu-id="c2cf6-129">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c2cf6-129">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="c2cf6-130">监视复制</span><span class="sxs-lookup"><span data-stu-id="c2cf6-130">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
