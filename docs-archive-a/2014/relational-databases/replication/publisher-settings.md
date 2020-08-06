---
title: SQL Server 复制“发布服务器设置”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a9a5ca5b0d7bfae895287708af159f3316e4474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693243"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a><span data-ttu-id="40986-102">SQL Server 复制“发布服务器设置”对话框</span><span class="sxs-lookup"><span data-stu-id="40986-102">SQL Server Replication 'Publisher Settings' dialog box</span></span>
  <span data-ttu-id="40986-103">可以使用 **“发布服务器设置”** 对话框，更改已添加到复制监视器左窗格中的发布服务器的设置。</span><span class="sxs-lookup"><span data-stu-id="40986-103">The **Publisher Settings** dialog box allows you to change settings for Publishers that have been added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="40986-104">选项</span><span class="sxs-lookup"><span data-stu-id="40986-104">Options</span></span>  
 <span data-ttu-id="40986-105">**发布服务器连接**</span><span class="sxs-lookup"><span data-stu-id="40986-105">**Publisher Connection**</span></span>  
 <span data-ttu-id="40986-106">单击此项可打开 **“连接到服务器”** 对话框，通过该对话框可以查看和更改复制监视器用来连接发布服务器的连接属性和凭据。</span><span class="sxs-lookup"><span data-stu-id="40986-106">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to a Publisher.</span></span>  
  
 <span data-ttu-id="40986-107">**分发服务器连接**</span><span class="sxs-lookup"><span data-stu-id="40986-107">**Distributor Connection**</span></span>  
 <span data-ttu-id="40986-108">只有当发布服务器使用了远程分发服务器时，才会显示此项。</span><span class="sxs-lookup"><span data-stu-id="40986-108">Displayed only if the Publisher uses a remote Distributor.</span></span> <span data-ttu-id="40986-109">单击此项可打开 **“连接到服务器”** 对话框，通过该对话框可以查看和更改复制监视器用来连接远程分发服务器的连接属性和凭据。</span><span class="sxs-lookup"><span data-stu-id="40986-109">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to the remote Distributor.</span></span>  
  
 <span data-ttu-id="40986-110">**复制监视器启动时自动连接**</span><span class="sxs-lookup"><span data-stu-id="40986-110">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="40986-111">选择此项可以使复制监视器自动连接到分发服务器，并检索在该对话框顶部网格中所选发布服务器的状态信息。</span><span class="sxs-lookup"><span data-stu-id="40986-111">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="40986-112">如果清除了此复选框，则必须在启动复制监视器后手动进行连接：在复制监视器左窗格中右键单击发布服务器，然后单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="40986-112">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="40986-113">**自动刷新此发布服务器及其发布的状态**</span><span class="sxs-lookup"><span data-stu-id="40986-113">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="40986-114">选择此项可以使复制监视器自动刷新在该对话框顶部网格中所选发布服务器的状态。</span><span class="sxs-lookup"><span data-stu-id="40986-114">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="40986-115">如果选择了此选项，复制监视器将轮询分发服务器，以获取发布服务器及其发布的状态信息。</span><span class="sxs-lookup"><span data-stu-id="40986-115">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="40986-116">轮询间隔是由 **“刷新速率”** 选项设置的。</span><span class="sxs-lookup"><span data-stu-id="40986-116">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="40986-117">有关在复制监视器中刷新的详细信息，请参阅[缓存、刷新和复制监视器性能](monitor/caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="40986-117">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="40986-118">**“刷新速率”**</span><span class="sxs-lookup"><span data-stu-id="40986-118">**Refresh rate**</span></span>  
 <span data-ttu-id="40986-119">输入一个值（秒），指定复制监视器对分发服务器的轮询频率（以了解状态信息）。</span><span class="sxs-lookup"><span data-stu-id="40986-119">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="40986-120">值越小表示轮询越频繁，如果监视大量的发布服务器，则可能会影响分发服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="40986-120">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="40986-121">建议您测试系统，以确定一个适当的值。</span><span class="sxs-lookup"><span data-stu-id="40986-121">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="40986-122">如果在复制监视器的任意详细信息窗口中选择 **“自动刷新”** ，则也将使用 **“刷新速率”** 设置。</span><span class="sxs-lookup"><span data-stu-id="40986-122">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="40986-123">**在以下组中显示此发布服务器**</span><span class="sxs-lookup"><span data-stu-id="40986-123">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="40986-124">从该列表中选择某个发布服务器组。</span><span class="sxs-lookup"><span data-stu-id="40986-124">Select a Publisher group from the list.</span></span> <span data-ttu-id="40986-125">该发布服务器显示在左窗格中此组下面。</span><span class="sxs-lookup"><span data-stu-id="40986-125">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="40986-126">通过组可以组织发布服务器，而且对复制的功能没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="40986-126">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span>  
  
 <span data-ttu-id="40986-127">**新建组**</span><span class="sxs-lookup"><span data-stu-id="40986-127">**New Group**</span></span>  
 <span data-ttu-id="40986-128">单击此项可创建新的发布服务器组。</span><span class="sxs-lookup"><span data-stu-id="40986-128">Click to create a new Publisher group.</span></span> <span data-ttu-id="40986-129">发布服务器组提供了在复制监视器内组织发布服务器的简便方法。</span><span class="sxs-lookup"><span data-stu-id="40986-129">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="40986-130">组既不影响数据的复制，也不影响复制拓扑中服务器之间的关系。</span><span class="sxs-lookup"><span data-stu-id="40986-130">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40986-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40986-131">See Also</span></span>  
 <span data-ttu-id="40986-132">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="40986-132">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="40986-133">监视复制</span><span class="sxs-lookup"><span data-stu-id="40986-133">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
