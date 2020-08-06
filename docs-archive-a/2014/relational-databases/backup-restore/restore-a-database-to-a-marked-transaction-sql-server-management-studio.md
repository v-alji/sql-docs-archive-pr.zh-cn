---
title: 将数据库还原到标记的事务 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8de9ef5bed389f020f14e60ccd99f39698e7110f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589166"
---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a><span data-ttu-id="9f0d6-102">将数据库还原到标记的事务 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9f0d6-102">Restore a Database to a Marked Transaction (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9f0d6-103">数据库处于还原状态时，可以使用 **“还原事务日志”** 对话框将数据库还原到可用日志备份中的标记的事务。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-103">When a database is in the restoring state, you can use the **Restore Transaction Log** dialog box to restore the database to a marked transaction in the available log backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f0d6-104">有关详细信息，请参阅[使用标记事务一致恢复相关数据库（完全恢复模式）](use-marked-transactions-to-recover-related-databases-consistently.md)和[恢复包含标记事务的相关数据库](recovery-of-related-databases-that-contain-marked-transaction.md)。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-104">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) and [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
### <a name="to-restore-a-marked-transaction"></a><span data-ttu-id="9f0d6-105">还原标记的事务</span><span class="sxs-lookup"><span data-stu-id="9f0d6-105">To restore a marked transaction</span></span>  
  
1.  <span data-ttu-id="9f0d6-106">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-106">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="9f0d6-107">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-107">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="9f0d6-108">右键单击数据库，指向“任务”  ，再单击“还原”  。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-108">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="9f0d6-109">单击 **“事务日志”** ，这将打开 **“还原事务日志”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-109">Click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
5.  <span data-ttu-id="9f0d6-110">在 **“常规”** 页上的 **“还原到”** 部分中，选择 **“标记的事务”** ，将打开 **“选择标记的事务”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-110">On the **General** page, in the **Restore To** section, select **Marked transaction**, which opens the **Select Marked Transaction** dialog box.</span></span> <span data-ttu-id="9f0d6-111">此对话框中将以网格列表的形式显示选择的事务日志备份中可用的标记的事务。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-111">This dialog box displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
     <span data-ttu-id="9f0d6-112">默认情况下，将一直还原到（但不包含）标记的事务为止。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-112">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="9f0d6-113">若要同时还原标记的事务，请选择 **“包含标记的事务”** 。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-113">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
     <span data-ttu-id="9f0d6-114">下表列出了网格的列标题并对列值进行了说明。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-114">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="9f0d6-115">标头</span><span class="sxs-lookup"><span data-stu-id="9f0d6-115">Header</span></span>|<span data-ttu-id="9f0d6-116">值</span><span class="sxs-lookup"><span data-stu-id="9f0d6-116">Value</span></span>|  
    |------------|-----------|  
    |\<blank>|<span data-ttu-id="9f0d6-117">显示一个用于选择标记的复选框。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-117">Displays a checkbox for selecting the mark.</span></span>|  
    |<span data-ttu-id="9f0d6-118">**事务标记**</span><span class="sxs-lookup"><span data-stu-id="9f0d6-118">**Transaction Mark**</span></span>|<span data-ttu-id="9f0d6-119">提交事务时，用户为标记的事务指定的名称。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-119">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
    |<span data-ttu-id="9f0d6-120">**Date**</span><span class="sxs-lookup"><span data-stu-id="9f0d6-120">**Date**</span></span>|<span data-ttu-id="9f0d6-121">事务的提交日期及时间。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-121">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="9f0d6-122">事务日期和时间显示为 **msdbgmarkhistory** 表中所记录的日期和时间，而非客户端计算机的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-122">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
    |<span data-ttu-id="9f0d6-123">**说明**</span><span class="sxs-lookup"><span data-stu-id="9f0d6-123">**Description**</span></span>|<span data-ttu-id="9f0d6-124">提交事务时，用户为标记的事务指定的说明（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-124">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
    |<span data-ttu-id="9f0d6-125">**LSN**</span><span class="sxs-lookup"><span data-stu-id="9f0d6-125">**LSN**</span></span>|<span data-ttu-id="9f0d6-126">所标记事务的日志序列号。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-126">Log sequence number of the marked transaction.</span></span>|  
    |<span data-ttu-id="9f0d6-127">**Database**</span><span class="sxs-lookup"><span data-stu-id="9f0d6-127">**Database**</span></span>|<span data-ttu-id="9f0d6-128">提交标记的事务时所在数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-128">Name of the database where the marked transaction was committed.</span></span>|  
    |<span data-ttu-id="9f0d6-129">**用户名**</span><span class="sxs-lookup"><span data-stu-id="9f0d6-129">**User Name**</span></span>|<span data-ttu-id="9f0d6-130">提交标记事务的数据库用户的名称。</span><span class="sxs-lookup"><span data-stu-id="9f0d6-130">Name of the database user who committed the marked transaction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f0d6-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f0d6-131">See Also</span></span>  
 <span data-ttu-id="9f0d6-132">[还原数据库备份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="9f0d6-132">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 [<span data-ttu-id="9f0d6-133">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9f0d6-133">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
  
