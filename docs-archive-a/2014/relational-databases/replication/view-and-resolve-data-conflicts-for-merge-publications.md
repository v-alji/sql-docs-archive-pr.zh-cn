---
title: 查看和解决 (SQL Server Management Studio) 的合并发布的数据冲突 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77aa9ece0073149c017f6eca35a756b22751a74b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580667"
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications-sql-server-management-studio"></a><span data-ttu-id="96dc7-102">查看和解决合并发布的数据冲突 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="96dc7-102">View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="96dc7-103">可以根据为每个项目指定的冲突解决程序来解决合并发布中的冲突。</span><span class="sxs-lookup"><span data-stu-id="96dc7-103">Conflicts in merge replication are resolved based on the resolver specified for each article.</span></span> <span data-ttu-id="96dc7-104">默认情况下，解决冲突无需用户干预。</span><span class="sxs-lookup"><span data-stu-id="96dc7-104">By default, conflicts are resolved without the need for user intervention.</span></span> <span data-ttu-id="96dc7-105">但是，可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 复制冲突查看器中查看冲突，并更改解决的结果。</span><span class="sxs-lookup"><span data-stu-id="96dc7-105">But conflicts can be viewed, and the outcome of the resolution can be changed, in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span>  
  
 <span data-ttu-id="96dc7-106">在冲突保持期的指定时间（默认值为 14 天）内，可以在复制冲突查看器中查看冲突数据。</span><span class="sxs-lookup"><span data-stu-id="96dc7-106">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period (with a default of 14 days).</span></span> <span data-ttu-id="96dc7-107">若要设置冲突保持期，请执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="96dc7-107">To set the conflict retention period, either:</span></span>  
  
-   <span data-ttu-id="96dc7-108">为 **@conflict_retention** [&#40;transact-sql&#41;sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)的参数指定保持值。</span><span class="sxs-lookup"><span data-stu-id="96dc7-108">Specify a retention value for the **@conflict_retention** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
-   <span data-ttu-id="96dc7-109">将参数的值**conflict_retention**指定为 conflict_retention **@property** ，并为 **@value** [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)的参数指定保持值。</span><span class="sxs-lookup"><span data-stu-id="96dc7-109">Specify a value of **conflict_retention** for the **@property** parameter and a retention value for the **@value** parameter of [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="96dc7-110">默认情况下，冲突信息存储在下列位置：</span><span class="sxs-lookup"><span data-stu-id="96dc7-110">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="96dc7-111">如果发布兼容级别为 90RTM 或更高，则存储在发布服务器和订阅服务器上。</span><span class="sxs-lookup"><span data-stu-id="96dc7-111">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="96dc7-112">如果发布兼容级别低于 80RTM，则存储在发布服务器上。</span><span class="sxs-lookup"><span data-stu-id="96dc7-112">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="96dc7-113">如果订阅服务器运行的是 [!INCLUDE[ssEW](../../includes/ssew-md.md)]，则存储在发布服务器上。</span><span class="sxs-lookup"><span data-stu-id="96dc7-113">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="96dc7-114">冲突数据不能存储在 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 订阅服务器上。</span><span class="sxs-lookup"><span data-stu-id="96dc7-114">Conflict data cannot be stored on [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="96dc7-115">冲突信息的存储受 **conflict_logging** 发布属性的控制。</span><span class="sxs-lookup"><span data-stu-id="96dc7-115">Storage of conflict information is controlled by the **conflict_logging** publication property.</span></span> <span data-ttu-id="96dc7-116">有关详细信息，请参阅 [sp_addmergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) 和 [sp_changemergepublication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="96dc7-116">For more information, see [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) and [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="96dc7-117">也可以在同步过程中使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 交互式冲突解决程序以交互方式解决冲突。</span><span class="sxs-lookup"><span data-stu-id="96dc7-117">Conflicts can also be resolved interactively during synchronization using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Interactive Resolver.</span></span> <span data-ttu-id="96dc7-118">交互式冲突解决程序可以通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同步管理器获取。</span><span class="sxs-lookup"><span data-stu-id="96dc7-118">The Interactive Resolver is available through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="96dc7-119">有关详细信息，请参阅[使用 Windows 同步管理器同步订阅（Windows 同步管理器）](synchronize-a-subscription-using-windows-synchronization-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="96dc7-119">For more information, see [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a><span data-ttu-id="96dc7-120">查看和解决合并发布的冲突</span><span class="sxs-lookup"><span data-stu-id="96dc7-120">To view and resolve conflicts for merge publications</span></span>  
  
1.  <span data-ttu-id="96dc7-121">如果适当) ，则连接到发布服务器 (或订阅服务器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="96dc7-121">Connect to the Publisher (or Subscriber if appropriate) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="96dc7-122">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="96dc7-122">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="96dc7-123">右键单击要查看其冲突的发布，然后单击 **“查看冲突”**。</span><span class="sxs-lookup"><span data-stu-id="96dc7-123">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="96dc7-124">如果为 **conflict_logging** 属性指定了值 **“subscriber”** ， **“查看冲突”** 菜单选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="96dc7-124">If you specified a value of **'subscriber'** for the **conflict_logging** property, the **View Conflicts** menu option is not available.</span></span> <span data-ttu-id="96dc7-125">若要查看冲突，请在命令提示符下启动 ConflictViewer.exe。</span><span class="sxs-lookup"><span data-stu-id="96dc7-125">To view conflicts, start ConflictViewer.exe from the command prompt.</span></span> <span data-ttu-id="96dc7-126">默认情况下，ConflictViewer.exe 位于以下目录中：Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="96dc7-126">By default, ConflictViewer.exe is located in the following directory: Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.</span></span> <span data-ttu-id="96dc7-127">要获取有效引导参数的列表，请运行 ConflictViewer.exe -?。</span><span class="sxs-lookup"><span data-stu-id="96dc7-127">For a list of valid startup parameters, run ConflictViewer.exe -?.</span></span>  
  
4.  <span data-ttu-id="96dc7-128">在 **“选择冲突表”** 对话框中，选择要查看冲突的数据库、发布和表。</span><span class="sxs-lookup"><span data-stu-id="96dc7-128">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="96dc7-129">在复制冲突查看器中可以：</span><span class="sxs-lookup"><span data-stu-id="96dc7-129">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="96dc7-130">使用上部网格右侧的按钮来筛选行。</span><span class="sxs-lookup"><span data-stu-id="96dc7-130">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="96dc7-131">在上部网格中选择行，以在下部网格中显示该行的信息。</span><span class="sxs-lookup"><span data-stu-id="96dc7-131">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="96dc7-132">在上部网格中选择一行或多行，然后单击 **“删除”**，这与单击 **“提交入选方”** 按钮的效果相同（不对数据进行任何更改）。</span><span class="sxs-lookup"><span data-stu-id="96dc7-132">Select one or more rows in the upper grid, and then click **Remove**, which is equivalent to clicking the **Submit Winner** button (without making any changes to the data).</span></span>  
  
    -   <span data-ttu-id="96dc7-133">单击属性按钮 (...) 查看有关冲突所涉及的列的详细信息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96dc7-133">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="96dc7-134">编辑 **“冲突解决入选方”** 或 **“冲突解决落选方”** 列中的数据，然后再提交数据（如果列为灰色，则数据为只读）。</span><span class="sxs-lookup"><span data-stu-id="96dc7-134">Edit data in the **Conflict winner** or **Conflict loser** column before submitting the data (data is read-only if the column is gray).</span></span>  
  
    -   <span data-ttu-id="96dc7-135">单击 **“提交入选方”** 接受指定为冲突入选方的行。</span><span class="sxs-lookup"><span data-stu-id="96dc7-135">Click **Submit Winner** to accept the row designated as the winner of the conflict.</span></span>  
  
    -   <span data-ttu-id="96dc7-136">单击 **“提交落选方”** 覆盖解决结果，并将指定为冲突落选方的值传播到拓扑中的所有节点。</span><span class="sxs-lookup"><span data-stu-id="96dc7-136">Click **Submit Loser** to override the resolution and to propagate the value designated as the loser of the conflict to all nodes in the topology.</span></span>  
  
    -   <span data-ttu-id="96dc7-137">选择 **“记录此冲突的详细信息”** 将冲突数据记录到一个文件中。</span><span class="sxs-lookup"><span data-stu-id="96dc7-137">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="96dc7-138">若要指定文件的位置，请指向 **“查看”** 菜单，然后单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="96dc7-138">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="96dc7-139">输入一个值，或单击浏览按钮 (**...**)，然后导航到相应文件。</span><span class="sxs-lookup"><span data-stu-id="96dc7-139">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="96dc7-140">单击 **“确定”** 可退出 **“选项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="96dc7-140">Click **OK** to exit the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="96dc7-141">关闭复制冲突查看器。</span><span class="sxs-lookup"><span data-stu-id="96dc7-141">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96dc7-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96dc7-142">See Also</span></span>  
 <span data-ttu-id="96dc7-143">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="96dc7-143">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="96dc7-144">指定合并项目冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="96dc7-144">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)  
  
  
