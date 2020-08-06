---
title: 手动故障转移数据库镜像会话 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c04ea4908ccbc4cfe4f6bb3606347dd444ef416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578388"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="6b31e-102">手动故障转移数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6b31e-102">Manually Fail Over a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="6b31e-103">同步镜像数据库时（即数据库处于 SYNCHRONIZED 状态时），数据库所有者可以启动到镜像服务器的手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="6b31e-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span> <span data-ttu-id="6b31e-104">手动故障转移只能从主体服务器启动。</span><span class="sxs-lookup"><span data-stu-id="6b31e-104">Manual failover can be initiated only from the principal server.</span></span>  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a><span data-ttu-id="6b31e-105">手动故障转移数据库镜像会话</span><span class="sxs-lookup"><span data-stu-id="6b31e-105">To manually fail over a database mirroring session</span></span>  
  
1.  <span data-ttu-id="6b31e-106">连接到主体服务器。</span><span class="sxs-lookup"><span data-stu-id="6b31e-106">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="6b31e-107">将数据库上下文设置为 **master** 数据库：</span><span class="sxs-lookup"><span data-stu-id="6b31e-107">Set the database context to the **master** database:</span></span>  
  
     `USE master;`  
  
3.  <span data-ttu-id="6b31e-108">在主体服务器上执行下列语句：</span><span class="sxs-lookup"><span data-stu-id="6b31e-108">Issue the following statement on the principal server:</span></span>  
  
     <span data-ttu-id="6b31e-109">[ALTER DATABASE database_name SET PARTNER FAILOVER，其中 database_name 是镜像数据库](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b31e-109">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET PARTNER FAILOVER, where *database_name* is the mirrored database.</span></span>  
  
     <span data-ttu-id="6b31e-110">此语句将立即启动从镜像服务器到主体角色的转换。</span><span class="sxs-lookup"><span data-stu-id="6b31e-110">This initiates an immediate transition of the mirror server to the principal role.</span></span>  
  
 <span data-ttu-id="6b31e-111">在前一主体上，客户端断开了与数据库的连接，并且未提交的事务将回滚。</span><span class="sxs-lookup"><span data-stu-id="6b31e-111">On the former principal, clients are disconnected from the database and in-flight transactions are rolled back.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b31e-112">当发生故障转移时，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器准备就绪但尚未提交的事务被认为在数据库故障转移后已中止。</span><span class="sxs-lookup"><span data-stu-id="6b31e-112">Transactions that have been prepared by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator but are still not committed when a failover occurs are considered aborted after the database has failed over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b31e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b31e-113">See Also</span></span>  
 <span data-ttu-id="6b31e-114">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="6b31e-114">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="6b31e-115">[手动故障转移数据库镜像会话 &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6b31e-115">[Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="6b31e-116">数据库镜像会话期间的角色切换 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6b31e-116">Role Switching During a Database Mirroring Session &#40;SQL Server&#41;</span></span>](role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
