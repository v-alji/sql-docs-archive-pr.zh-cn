---
title: 在数据库镜像会话中强制服务 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b909f3602a78f3244ab3cf4479b8745956a7bd62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694122"
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="86c2e-102">在数据库镜像会话中强制服务 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="86c2e-102">Force Service in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="86c2e-103">在高性能模式和不带自动故障转移功能的高安全性模式下，如果主体服务器失败而镜像服务器可用，则数据库所有者可以强制将服务故障转移到镜像数据库（可能造成数据丢失），从而使数据库可用。</span><span class="sxs-lookup"><span data-stu-id="86c2e-103">In high-performance mode and high-safety mode without automatic failover, if the principal server fails while the mirror server is available, the database owner can make the database available by forcing service to fail over (with possible data loss) to the mirror database.</span></span> <span data-ttu-id="86c2e-104">此选项仅在以下情况中可用：</span><span class="sxs-lookup"><span data-stu-id="86c2e-104">This option is available only under all the following conditions:</span></span>  
  
-   <span data-ttu-id="86c2e-105">主体服务器已关闭。</span><span class="sxs-lookup"><span data-stu-id="86c2e-105">The principal server is down.</span></span>  
  
-   <span data-ttu-id="86c2e-106">WITNESS 设置为 OFF 或连接到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="86c2e-106">WITNESS is set to OFF or is connected to the mirror server.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="86c2e-107">严格讲来，强制服务是一种灾难恢复方法。</span><span class="sxs-lookup"><span data-stu-id="86c2e-107">Forced service is strictly a disaster recovery method.</span></span> <span data-ttu-id="86c2e-108">强制服务可能会导致一些数据丢失。</span><span class="sxs-lookup"><span data-stu-id="86c2e-108">Forcing service may involve some data loss.</span></span> <span data-ttu-id="86c2e-109">因此，只有在为了立即恢复数据库服务而不惜丢失某些数据时，才可强制执行服务。</span><span class="sxs-lookup"><span data-stu-id="86c2e-109">Therefore, force service only if you are willing to risk losing some data in order to restore service to the database immediately.</span></span> <span data-ttu-id="86c2e-110">如果强制服务面临丢失重要数据的风险，则建议您停止镜像并手动重新同步数据库。</span><span class="sxs-lookup"><span data-stu-id="86c2e-110">If forcing service risks losing significant data, we recommend that you stop mirroring and manually resynchronize the databases.</span></span> <span data-ttu-id="86c2e-111">有关强制服务所面临风险的详细信息，请参阅 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="86c2e-111">For more information about the risks of forcing service, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="86c2e-112">强制服务会挂起会话并启动新的恢复分叉。</span><span class="sxs-lookup"><span data-stu-id="86c2e-112">Forcing service suspends the session and starts a new recovery fork.</span></span> <span data-ttu-id="86c2e-113">强制服务的结果相当于删除镜像并恢复以前的主体数据库。</span><span class="sxs-lookup"><span data-stu-id="86c2e-113">The effect of forcing service is similar to removing mirroring and recovering the former principal database.</span></span> <span data-ttu-id="86c2e-114">但是，强制服务便于在恢复镜像时重新同步数据库（可能造成数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="86c2e-114">However, forcing service facilitates resynchronizing the databases (with possible data loss) when mirroring resumes.</span></span>  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a><span data-ttu-id="86c2e-115">在数据库镜像会话中强制执行服务</span><span class="sxs-lookup"><span data-stu-id="86c2e-115">To force service in a database mirroring session</span></span>  
  
1.  <span data-ttu-id="86c2e-116">连接到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="86c2e-116">Connect to the mirror server.</span></span>  
  
2.  <span data-ttu-id="86c2e-117">发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="86c2e-117">Issue the following statement:</span></span>  
  
     <span data-ttu-id="86c2e-118">ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span><span class="sxs-lookup"><span data-stu-id="86c2e-118">ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span></span>  
  
     <span data-ttu-id="86c2e-119">其中， *<database_name>* 为镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="86c2e-119">where *<database_name>* is the mirrored database.</span></span>  
  
     <span data-ttu-id="86c2e-120">镜像服务器将立即转换为主体服务器，并且镜像挂起。</span><span class="sxs-lookup"><span data-stu-id="86c2e-120">The mirror server immediately transitions to principal server, and mirroring is suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c2e-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86c2e-121">See Also</span></span>  
 <span data-ttu-id="86c2e-122">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="86c2e-122">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="86c2e-123">数据库镜像运行模式</span><span class="sxs-lookup"><span data-stu-id="86c2e-123">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
