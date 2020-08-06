---
title: MSSQLSERVER_1457 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c30ee6149c95d93bdaf1d2877f5fe1871a575ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589656"
---
# <a name="mssqlserver_1457"></a><span data-ttu-id="fd333-102">MSSQLSERVER_1457</span><span class="sxs-lookup"><span data-stu-id="fd333-102">MSSQLSERVER_1457</span></span>
    
## <a name="details"></a><span data-ttu-id="fd333-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="fd333-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd333-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="fd333-104">Product Name</span></span>|<span data-ttu-id="fd333-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fd333-105">SQL Server</span></span>|  
|<span data-ttu-id="fd333-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="fd333-106">Event ID</span></span>|<span data-ttu-id="fd333-107">1457</span><span class="sxs-lookup"><span data-stu-id="fd333-107">1457</span></span>|  
|<span data-ttu-id="fd333-108">事件源</span><span class="sxs-lookup"><span data-stu-id="fd333-108">Event Source</span></span>|<span data-ttu-id="fd333-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fd333-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fd333-110">组件</span><span class="sxs-lookup"><span data-stu-id="fd333-110">Component</span></span>|<span data-ttu-id="fd333-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fd333-111">SQLEngine</span></span>|  
|<span data-ttu-id="fd333-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="fd333-112">Symbolic Name</span></span>|<span data-ttu-id="fd333-113">DBM_PAGE_UNDO_PENDING</span><span class="sxs-lookup"><span data-stu-id="fd333-113">DBM_PAGE_UNDO_PENDING</span></span>|  
|<span data-ttu-id="fd333-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="fd333-114">Message Text</span></span>|<span data-ttu-id="fd333-115">镜像数据库 '%.\*ls' 的同步操作中断，导致数据库处于不一致的状态。</span><span class="sxs-lookup"><span data-stu-id="fd333-115">Synchronization of the mirror database, '%.\*ls', was interrupted, leaving the database in an inconsistent state.</span></span> <span data-ttu-id="fd333-116">ALTER DATABASE 命令失败。</span><span class="sxs-lookup"><span data-stu-id="fd333-116">The ALTER DATABASE command failed.</span></span> <span data-ttu-id="fd333-117">请确保镜像数据库重新启动并联机，然后重新连接镜像服务器实例，并允许镜像数据库完成同步。</span><span class="sxs-lookup"><span data-stu-id="fd333-117">Ensure that the mirror database is back up and online, and then reconnect the mirror server instance and allow the mirror database to finish synchronizing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fd333-118">说明</span><span class="sxs-lookup"><span data-stu-id="fd333-118">Explanation</span></span>  
 <span data-ttu-id="fd333-119">此消息表明 ALTER DATABASE *database_name* SET PARTNER OFF 语句失败。</span><span class="sxs-lookup"><span data-stu-id="fd333-119">This messages indicates that the ALTER DATABASE *database_name* SET PARTNER OFF statement has failed.</span></span> <span data-ttu-id="fd333-120">尝试删除数据库镜像操作失败导致镜像数据库的同步操作中断。</span><span class="sxs-lookup"><span data-stu-id="fd333-120">The failed attempt to remove database mirroring interrupted synchronization of the mirror database.</span></span> <span data-ttu-id="fd333-121">数据库处于不一致状态。</span><span class="sxs-lookup"><span data-stu-id="fd333-121">The database is in an inconsistent state.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fd333-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="fd333-122">User Action</span></span>  
 <span data-ttu-id="fd333-123">若要解决此错误，您可以执行下列某种操作：</span><span class="sxs-lookup"><span data-stu-id="fd333-123">To resolve this error, you can take either of the following actions:</span></span>  
  
-   <span data-ttu-id="fd333-124">恢复镜像服务器和主体服务器之间的连接以允许镜像数据库同步。</span><span class="sxs-lookup"><span data-stu-id="fd333-124">Restore contact between the mirror server and the principal server to allow for the mirror database to synchronize.</span></span>  
  
-   <span data-ttu-id="fd333-125">删除镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="fd333-125">Drop the mirror database.</span></span>  
  
     <span data-ttu-id="fd333-126">删除镜像数据库后，可以从备份创建一个新的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="fd333-126">After you drop the mirror database, you can create a new mirror database from backups.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd333-127">如果仍只是在 SET PARTNER OFF 语句失败后启用镜像，则可以删除镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="fd333-127">You can drop the mirror database when mirroring is still enabled only after a failed SET PARTNER OFF statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd333-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd333-128">See Also</span></span>  
 <span data-ttu-id="fd333-129">[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd333-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="fd333-130">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fd333-130">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="fd333-131">[设置数据库镜像 (SQL Server)](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd333-131">[Setting Up Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="fd333-132">[删除数据库镜像 (SQL Server)](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd333-132">[Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="fd333-133">为镜像准备镜像数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fd333-133">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
