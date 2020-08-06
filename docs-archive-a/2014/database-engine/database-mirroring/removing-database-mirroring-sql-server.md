---
title: 删除数据库镜像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8044fcef9d9f9bfc1fb41c1faa17b76c827da5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690109"
---
# <a name="removing-database-mirroring-sql-server"></a><span data-ttu-id="9765a-102">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9765a-102">Removing Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="9765a-103">数据库所有者可以在任一伙伴上随时手动停止数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="9765a-103">The database owner can manually stop a database mirroring session at any time, at either partner.</span></span>  
  
## <a name="impact-of-removing-mirroring"></a><span data-ttu-id="9765a-104">删除镜像的影响</span><span class="sxs-lookup"><span data-stu-id="9765a-104">Impact of Removing Mirroring</span></span>  
 <span data-ttu-id="9765a-105">删除镜像时，将发生以下情况：</span><span class="sxs-lookup"><span data-stu-id="9765a-105">When mirroring is removed, the following occurs:</span></span>  
  
-   <span data-ttu-id="9765a-106">伙伴间的关系以及每个伙伴与见证服务器间的关系都将永久中断（如果存在任何关系）。</span><span class="sxs-lookup"><span data-stu-id="9765a-106">The relationship between the partners and between each partner and the witness breaks permanently, if any relationship exists.</span></span>  
  
     <span data-ttu-id="9765a-107">如果在停止会话时伙伴之间正在相互通信，则在两台计算机上的关系将立即中断。</span><span class="sxs-lookup"><span data-stu-id="9765a-107">If the partners are communicating with each other when the session is stopped, their relationship is immediately broken on both computers.</span></span> <span data-ttu-id="9765a-108">如果伙伴之间未通信（在停止时数据库处于 DISCONNECTED 状态），停止镜像的伙伴上的关系将立即中断；当另一个伙伴试图重新连接时，将会发现数据库镜像会话已经终止。</span><span class="sxs-lookup"><span data-stu-id="9765a-108">If the partners are not communicating (the database is in a DISCONNECTED state at the time of stopping), the relationship is broken immediately on the partner from which mirroring is stopped; when the other partner tries to reconnect, it discovers that the database mirroring session has ended.</span></span>  
  
-   <span data-ttu-id="9765a-109">有关镜像会话的信息已经清除，这一点与暂停会话不同。</span><span class="sxs-lookup"><span data-stu-id="9765a-109">Information about the mirroring session is dropped, unlike when pausing a session.</span></span> <span data-ttu-id="9765a-110">删除了主体数据库和镜像数据库上的镜像。</span><span class="sxs-lookup"><span data-stu-id="9765a-110">Mirroring is removed on both the principal database and the mirror database.</span></span> <span data-ttu-id="9765a-111">在 **sys.databases** 中，**mirroring_state** 列及所有其他镜像列都设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="9765a-111">In **sys.databases**, the **mirroring_state** column and all other mirroring columns are set to NULL.</span></span> <span data-ttu-id="9765a-112">有关详细信息，请参阅 [sys.database_mirroring (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9765a-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
-   <span data-ttu-id="9765a-113">每台伙伴服务器实例使用的数据库为数据库的单独副本。</span><span class="sxs-lookup"><span data-stu-id="9765a-113">Each partner server instance is left with a separate copy of the database.</span></span>  
  
-   <span data-ttu-id="9765a-114">由于镜像数据库是使用 RESTORE WITH NORECOVERY 创建的，因此镜像数据库的状态为 RESTORING（请查看 **sys.databases** 的 **state**列）。</span><span class="sxs-lookup"><span data-stu-id="9765a-114">The mirror database is left in the RESTORING state (see the **state** column of **sys.databases**), because the mirror database was created by using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="9765a-115">此时，您可以删除以前的镜像数据库或使用 WITH RECOVERY 还原以前的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="9765a-115">At this point, you can drop the former mirror database or restore it using WITH RECOVERY.</span></span> <span data-ttu-id="9765a-116">恢复该数据库时，由于恢复将启动新的恢复分支，因此将与以前的主体数据库不同。</span><span class="sxs-lookup"><span data-stu-id="9765a-116">When you recover the database, it will have diverged from the former principal database because the recovery starts a new recovery fork.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9765a-117">若要在停止会话后继续镜像，必须建立新的数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="9765a-117">To continue mirroring after stopping a session, you must establish a new database mirroring session.</span></span> <span data-ttu-id="9765a-118">如果在停止镜像后创建日志备份，必须在重新启动镜像之前将该日志备份应用到镜像数据库中。</span><span class="sxs-lookup"><span data-stu-id="9765a-118">If you create a log backup after stopping mirroring, you must apply it to the mirror database before restarting mirroring.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9765a-119">相关任务</span><span class="sxs-lookup"><span data-stu-id="9765a-119">Related Tasks</span></span>  
 <span data-ttu-id="9765a-120">**删除数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="9765a-120">**To remove database mirroring**</span></span>  
  
-   [<span data-ttu-id="9765a-121">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9765a-121">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
 <span data-ttu-id="9765a-122">**启动数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="9765a-122">**To start database mirroring**</span></span>  
  
-   [<span data-ttu-id="9765a-123">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9765a-123">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="9765a-124">使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9765a-124">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="9765a-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9765a-125">See Also</span></span>  
 <span data-ttu-id="9765a-126">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="9765a-126">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="9765a-127">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9765a-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="9765a-128">[暂停和恢复数据库镜像 (SQL Server)](pausing-and-resuming-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9765a-128">[Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="9765a-129">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9765a-129">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
