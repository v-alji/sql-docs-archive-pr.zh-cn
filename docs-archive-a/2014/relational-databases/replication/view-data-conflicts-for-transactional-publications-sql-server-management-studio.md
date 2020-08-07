---
title: 查看事务发布的数据冲突 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
- viewing conflict information
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 228753c113bcf43ed276d989a3996e9bf23bfc16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589509"
---
# <a name="view-data-conflicts-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="c74d6-102">查看事务发布的数据冲突 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c74d6-102">View Data Conflicts for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="c74d6-103">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 复制冲突查看器中，您可以查看对等事务复制和具有排队更新订阅的事务复制的冲突。</span><span class="sxs-lookup"><span data-stu-id="c74d6-103">You can view conflicts for peer-to-peer transactional replication and transactional replication with queued updating subscriptions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span> <span data-ttu-id="c74d6-104">有关如何检测和解决冲突的信息，请参阅[对等复制中的冲突检测](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)和[设置排队更新冲突解决选项 (SQL Server Management Studio)](publish/create-an-updatable-subscription-to-a-transactional-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="c74d6-104">For information about how conflicts are detected and resolved, see [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) and [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](publish/create-an-updatable-subscription-to-a-transactional-publication.md).</span></span>  
  
 <span data-ttu-id="c74d6-105">冲突数据的可用性取决于复制的类型和冲突保持期：</span><span class="sxs-lookup"><span data-stu-id="c74d6-105">The availability of conflict data depends on the type of replication and the conflict retention period:</span></span>  
  
-   <span data-ttu-id="c74d6-106">对于对等复制，默认情况下，分发代理在检测到冲突时将会失败。</span><span class="sxs-lookup"><span data-stu-id="c74d6-106">For peer-to-peer replication, by default, the Distribution Agent fails when it detects a conflict.</span></span> <span data-ttu-id="c74d6-107">冲突错误会记录到错误日志中，但是冲突数据不会记录到冲突表中；因此没有可供查看的冲突数据。</span><span class="sxs-lookup"><span data-stu-id="c74d6-107">A conflict error is logged into the error log, but no conflict data is logged into the conflict table; therefore it is not available for viewing.</span></span> <span data-ttu-id="c74d6-108">如果允许分发代理继续运行，将在检测到冲突的每个节点本地记录冲突。</span><span class="sxs-lookup"><span data-stu-id="c74d6-108">If the Distribution Agent is allowed to continue, a conflict is logged locally on each node where it was detected.</span></span> <span data-ttu-id="c74d6-109">有关详细信息，请参阅 [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)中的“处理冲突”。</span><span class="sxs-lookup"><span data-stu-id="c74d6-109">For more information, see "Handling Conflicts" in [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
-   <span data-ttu-id="c74d6-110">对于排队更新订阅，每个冲突的数据都可用。</span><span class="sxs-lookup"><span data-stu-id="c74d6-110">For queued updating subscriptions, data is available for every conflict.</span></span> <span data-ttu-id="c74d6-111">在冲突保持期的指定时间（默认值为 14 天）内，可以在复制冲突查看器中查看冲突数据。</span><span class="sxs-lookup"><span data-stu-id="c74d6-111">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period, with a default of 14 days.</span></span> <span data-ttu-id="c74d6-112">若要设置冲突保持期，请执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="c74d6-112">To set the conflict retention period, perform either of the following:</span></span>  
  
    -   <span data-ttu-id="c74d6-113">为 @conflict_retention sp_addpublication [的](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)参数指定保持值。</span><span class="sxs-lookup"><span data-stu-id="c74d6-113">Specify a retention value for the @conflict_retention parameter of [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="c74d6-114">指定参数的值 `'conflict_retention'` @property ，并为 sp_changepublication 的参数指定保持值 @value 。 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="c74d6-114">Specify a value of `'conflict_retention'` for the @property parameter and a retention value for the @value parameter of [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span>  
  
### <a name="to-view-conflicts"></a><span data-ttu-id="c74d6-115">查看冲突</span><span class="sxs-lookup"><span data-stu-id="c74d6-115">To view conflicts</span></span>  
  
1.  <span data-ttu-id="c74d6-116">连接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的相应服务器，然后展开该服务器节点：</span><span class="sxs-lookup"><span data-stu-id="c74d6-116">Connect to the appropriate server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="c74d6-117">对于对等复制，此为发生冲突的节点。</span><span class="sxs-lookup"><span data-stu-id="c74d6-117">For peer-to-peer replication, this is the node at which the conflict occurred.</span></span>  
  
    -   <span data-ttu-id="c74d6-118">对于排队更新订阅，此为发布服务器。</span><span class="sxs-lookup"><span data-stu-id="c74d6-118">For queued updating subscriptions, this is the Publisher.</span></span>  
  
2.  <span data-ttu-id="c74d6-119">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c74d6-119">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="c74d6-120">右键单击要查看其冲突的发布，然后单击 **“查看冲突”**。</span><span class="sxs-lookup"><span data-stu-id="c74d6-120">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
4.  <span data-ttu-id="c74d6-121">在 **“选择冲突表”** 对话框中，选择要查看冲突的数据库、发布和表。</span><span class="sxs-lookup"><span data-stu-id="c74d6-121">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="c74d6-122">在复制冲突查看器中可以：</span><span class="sxs-lookup"><span data-stu-id="c74d6-122">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="c74d6-123">使用上部网格右侧的按钮来筛选行。</span><span class="sxs-lookup"><span data-stu-id="c74d6-123">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="c74d6-124">在上部网格中选择行，以在下部网格中显示该行的信息。</span><span class="sxs-lookup"><span data-stu-id="c74d6-124">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="c74d6-125">在上部网格中选择一行或多行，再单击 **“删除”**，即从冲突元数据表中删除相应行。</span><span class="sxs-lookup"><span data-stu-id="c74d6-125">Select one or more rows in the upper grid, and then click **Remove**, which removes the row from the conflicts metadata table.</span></span>  
  
    -   <span data-ttu-id="c74d6-126">单击属性按钮 (...) 查看有关冲突所涉及的列的详细信息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c74d6-126">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="c74d6-127">选择 **“记录此冲突的详细信息”** 将冲突数据记录到一个文件中。</span><span class="sxs-lookup"><span data-stu-id="c74d6-127">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="c74d6-128">若要指定文件的位置，请指向 **“查看”** 菜单，然后单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="c74d6-128">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="c74d6-129">输入一个值，或单击浏览按钮 (**...**)，然后导航到相应文件。</span><span class="sxs-lookup"><span data-stu-id="c74d6-129">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="c74d6-130">单击“确定”关闭“选项”对话框 。</span><span class="sxs-lookup"><span data-stu-id="c74d6-130">Click **OK** to close the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="c74d6-131">关闭复制冲突查看器。</span><span class="sxs-lookup"><span data-stu-id="c74d6-131">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74d6-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c74d6-132">See Also</span></span>  
 <span data-ttu-id="c74d6-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="c74d6-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span></span>  
 [<span data-ttu-id="c74d6-134">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="c74d6-134">Queued Updating Conflict Detection and Resolution</span></span>](transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
