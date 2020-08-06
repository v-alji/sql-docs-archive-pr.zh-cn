---
title: "\"添加发布服务器\" 对话框"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.addpublisher.f1
helpviewer_keywords:
- Add Publisher dialog box
ms.assetid: 4b57e298-655f-42c2-82bc-25cdad94a194
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c7e607c04aa74db7e5facf13051bf0c47c9dae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578154"
---
# <a name="sql-server-replication-add-publisher-dialog-box"></a><span data-ttu-id="93aff-102">SQL Server 复制 "添加发布服务器" 对话框</span><span class="sxs-lookup"><span data-stu-id="93aff-102">SQL Server Replication 'Add Publisher' dialog box</span></span> 
  <span data-ttu-id="93aff-103">可以使用 **“添加发布服务器”** 对话框，将一个或多个发布服务器添加到复制监视器的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="93aff-103">The **Add Publisher** dialog box allows you to add to one or more Publishers to the left pane of Replication Monitor.</span></span> <span data-ttu-id="93aff-104">添加发布服务器之后，如果在左窗格中选择发布服务器，将在右窗格中显示该发布服务器的有关信息。</span><span class="sxs-lookup"><span data-stu-id="93aff-104">After adding a Publisher, selecting the Publisher in the left pane shows information on the Publisher in the right pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="93aff-105">选项</span><span class="sxs-lookup"><span data-stu-id="93aff-105">Options</span></span>  
 <span data-ttu-id="93aff-106">**添加**</span><span class="sxs-lookup"><span data-stu-id="93aff-106">**Add**</span></span>  
 <span data-ttu-id="93aff-107">单击可选择要添加的发布服务器的类型，单击后将启动 **“连接到服务器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="93aff-107">Click to select a type of Publisher to add, which launches the **Connect to Server** dialog box.</span></span> <span data-ttu-id="93aff-108">选项包括：</span><span class="sxs-lookup"><span data-stu-id="93aff-108">The options are:</span></span>  
  
-   <span data-ttu-id="93aff-109">**添加 SQL Server 发布者 .。。**</span><span class="sxs-lookup"><span data-stu-id="93aff-109">**Add SQL Server Publisher...**</span></span>  
  
     <span data-ttu-id="93aff-110">使用 **“连接到服务器”** 对话框连接到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="93aff-110">Connect to the Publisher using the **Connect to Server** dialog box.</span></span>  
  
-   <span data-ttu-id="93aff-111">**添加 Oracle 发布服务器 .。。**</span><span class="sxs-lookup"><span data-stu-id="93aff-111">**Add Oracle Publisher...**</span></span>  
  
     <span data-ttu-id="93aff-112">使用“连接到服务器”对话框连接到与 Oracle 发布服务器关联的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分发服务器  。</span><span class="sxs-lookup"><span data-stu-id="93aff-112">Connect to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher using the **Connect to Server** dialog box.</span></span>  
  
-   <span data-ttu-id="93aff-113">**指定分发服务器并添加其发布服务器 .。。**</span><span class="sxs-lookup"><span data-stu-id="93aff-113">**Specify a Distributor and Add Its Publishers...**</span></span>  
  
     <span data-ttu-id="93aff-114">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] “连接到服务器” **对话框连接到与一个或多个发布服务器关联的** 分发服务器。</span><span class="sxs-lookup"><span data-stu-id="93aff-114">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor associated with one or more Publishers using the **Connect to Server** dialog box.</span></span>  
  
 <span data-ttu-id="93aff-115">成功连接到发布服务器或分发服务器之后，将在对话框顶部的网格中显示每个发布服务器及其分发服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="93aff-115">After successfully connecting to the Publisher or Distributor, the name of each Publisher and its Distributor are displayed in the grid at the top of the dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93aff-116">分发服务器和发布服务器通常运行在同一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上，但分发服务器可以运行在另一个实例上（此配置称为远程分发服务器）。</span><span class="sxs-lookup"><span data-stu-id="93aff-116">The Distributor and Publisher often run on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the Distributor can run on another instance (this configuration is referred to as a remote Distributor).</span></span>  
  
 <span data-ttu-id="93aff-117">**删除**</span><span class="sxs-lookup"><span data-stu-id="93aff-117">**Remove**</span></span>  
 <span data-ttu-id="93aff-118">通过在对话框顶部的网格中选择发布服务器并单击 **“删除”** ，可以从要添加的发布服务器的列表中删除发布服务器。</span><span class="sxs-lookup"><span data-stu-id="93aff-118">Select a Publisher in the grid at the top of the dialog box, and click **Remove** to remove the Publisher from the list of Publishers to be added.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93aff-119">此按钮不能用来删除已经显示在复制监视器中的发布服务器。</span><span class="sxs-lookup"><span data-stu-id="93aff-119">This button cannot be used to remove a Publisher that is already displayed in Replication Monitor.</span></span> <span data-ttu-id="93aff-120">若要删除已经显示的发布服务器，请在复制监视器的左窗格中右键单击该发布服务器，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="93aff-120">To remove a Publisher that is already displayed right-click the Publisher in the left pane of Replication Monitor and click **Remove**.</span></span>  
  
 <span data-ttu-id="93aff-121">**复制监视器启动时自动连接**</span><span class="sxs-lookup"><span data-stu-id="93aff-121">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="93aff-122">选择此项可以使复制监视器自动连接到分发服务器，并检索在该对话框顶部网格中所选发布服务器的状态信息。</span><span class="sxs-lookup"><span data-stu-id="93aff-122">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="93aff-123">如果清除了此复选框，则必须在启动复制监视器后手动进行连接：在复制监视器左窗格中右键单击发布服务器，然后单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="93aff-123">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="93aff-124">**自动刷新此发布服务器及其发布的状态**</span><span class="sxs-lookup"><span data-stu-id="93aff-124">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="93aff-125">选择此项可以使复制监视器自动刷新在该对话框顶部网格中所选发布服务器的状态。</span><span class="sxs-lookup"><span data-stu-id="93aff-125">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="93aff-126">如果选择了此选项，复制监视器将轮询分发服务器，以获取发布服务器及其发布的状态信息。</span><span class="sxs-lookup"><span data-stu-id="93aff-126">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="93aff-127">轮询间隔是由 **“刷新速率”** 选项设置的。</span><span class="sxs-lookup"><span data-stu-id="93aff-127">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="93aff-128">有关在复制监视器中刷新的详细信息，请参阅[缓存、刷新和复制监视器性能](monitor/caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="93aff-128">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="93aff-129">**“刷新速率”**</span><span class="sxs-lookup"><span data-stu-id="93aff-129">**Refresh rate**</span></span>  
 <span data-ttu-id="93aff-130">输入一个值（秒），指定复制监视器对分发服务器的轮询频率（以了解状态信息）。</span><span class="sxs-lookup"><span data-stu-id="93aff-130">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="93aff-131">值越小表示轮询越频繁，如果监视大量的发布服务器，则可能会影响分发服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="93aff-131">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="93aff-132">建议您测试系统，以确定一个适当的值。</span><span class="sxs-lookup"><span data-stu-id="93aff-132">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="93aff-133">如果在复制监视器的任意详细信息窗口中选择 **“自动刷新”** ，则也将使用 **“刷新速率”** 设置。</span><span class="sxs-lookup"><span data-stu-id="93aff-133">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="93aff-134">**在以下组中显示此发布服务器**</span><span class="sxs-lookup"><span data-stu-id="93aff-134">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="93aff-135">从该列表中选择某个发布服务器组。</span><span class="sxs-lookup"><span data-stu-id="93aff-135">Select a Publisher group from the list.</span></span> <span data-ttu-id="93aff-136">该发布服务器显示在左窗格中此组下面。</span><span class="sxs-lookup"><span data-stu-id="93aff-136">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="93aff-137">通过组可以组织发布服务器，而且对复制的功能没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="93aff-137">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span> <span data-ttu-id="93aff-138">如果没有定义任何组或者希望创建新组，请单击 **“新建组”** 。</span><span class="sxs-lookup"><span data-stu-id="93aff-138">If no groups are defined or you want to create a new one, click **New Group**.</span></span>  
  
 <span data-ttu-id="93aff-139">**新建组**</span><span class="sxs-lookup"><span data-stu-id="93aff-139">**New Group**</span></span>  
 <span data-ttu-id="93aff-140">单击此项可创建新的发布服务器组。</span><span class="sxs-lookup"><span data-stu-id="93aff-140">Click to create a new Publisher group.</span></span> <span data-ttu-id="93aff-141">发布服务器组提供了在复制监视器内组织发布服务器的简便方法。</span><span class="sxs-lookup"><span data-stu-id="93aff-141">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="93aff-142">组既不影响数据的复制，也不影响复制拓扑中服务器之间的关系。</span><span class="sxs-lookup"><span data-stu-id="93aff-142">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93aff-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93aff-143">See Also</span></span>  
 <span data-ttu-id="93aff-144">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="93aff-144">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="93aff-145">监视复制</span><span class="sxs-lookup"><span data-stu-id="93aff-145">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
