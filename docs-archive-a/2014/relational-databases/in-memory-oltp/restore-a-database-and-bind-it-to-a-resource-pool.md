---
title: 还原数据库并将它绑定到资源池 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0b518c93ca9d5e7157ceaa20d9548d7b6061017d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576757"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a><span data-ttu-id="4b3bb-102">还原数据库并将它绑定到资源池</span><span class="sxs-lookup"><span data-stu-id="4b3bb-102">Restore a Database and Bind it to a Resource Pool</span></span>
  <span data-ttu-id="4b3bb-103">即使有足够的内存来还原带有内存优化表的数据库，也想要采用最佳做法，将数据库绑定到命名资源池。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-103">Even though you have enough memory to restore a database with memory-optimized tables, you want to follow best practices and bind the database to a named resource pool.</span></span> <span data-ttu-id="4b3bb-104">因为数据库在绑定到池之前必须存在，所以还原数据库这个过程分为几个步骤。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-104">Since the database must exist before you can bind it to the pool restoring your database is a multi-step process.</span></span> <span data-ttu-id="4b3bb-105">本主题将演练这一过程。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-105">This topic walks you through that process.</span></span>  
  
##  <a name="restore-with-norecovery"></a><span data-ttu-id="4b3bb-106">使用 NORECOVERY 还原</span><span class="sxs-lookup"><span data-stu-id="4b3bb-106">Restore with NORECOVERY</span></span>  
 <span data-ttu-id="4b3bb-107">还原数据库时 ，NORECOVERY 将创建数据库并在不使用内存的情况下还原磁盘映像。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-107">When you restore a database, NORECOVERY causes the database to be created and the disk image restored without consuming memory.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
##  <a name="create-the-resource-pool"></a><span data-ttu-id="4b3bb-108">创建资源池</span><span class="sxs-lookup"><span data-stu-id="4b3bb-108">Create the resource pool</span></span>  
 <span data-ttu-id="4b3bb-109">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 创建了名为 Pool_IMOLTP 的资源池，有 50% 内存可供其使用。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-109">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a resource pool named Pool_IMOLTP with 50% of memory available for its use.</span></span>  <span data-ttu-id="4b3bb-110">创建该池后，资源调控器重新配置为包括 Pool_IMOLTP。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-110">After the pool is created, the Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
##  <a name="bind-the-database-and-resource-pool"></a><span data-ttu-id="4b3bb-111">绑定数据库和资源池</span><span class="sxs-lookup"><span data-stu-id="4b3bb-111">Bind the database and resource pool</span></span>  
 <span data-ttu-id="4b3bb-112">使用系统函数 `sp_xtp_bind_db_resource_pool` 将数据库绑定到资源池。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-112">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="4b3bb-113">该函数使用两个参数：数据库名称，然后是资源池名称。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-113">The function takes two parameters: the database name followed by the resource pool name.</span></span>  
  
 <span data-ttu-id="4b3bb-114">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 定义数据库 IMOLTP_DB 与资源池 Pool_IMOLTP 的绑定。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-114">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="4b3bb-115">完成下一步骤后，绑定才生效。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-115">The binding does not become effective until you complete the next step.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
##  <a name="restore-with-recovery"></a><span data-ttu-id="4b3bb-116">使用 RECOVERY 还原</span><span class="sxs-lookup"><span data-stu-id="4b3bb-116">Restore with RECOVERY</span></span>  
 <span data-ttu-id="4b3bb-117">使用 RECOVERY 还原数据库时，数据库将联机并还原所有数据。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-117">When you restore the database with recovery the database is brought online and all the data restored.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
##  <a name="monitor-the-resource-pool-performance"></a><span data-ttu-id="4b3bb-118">监视资源池性能</span><span class="sxs-lookup"><span data-stu-id="4b3bb-118">Monitor the resource pool performance</span></span>  
 <span data-ttu-id="4b3bb-119">一旦数据库绑定到命名的资源池并使用 RECOVERY 还原，请监视 Resource Pool Stats 对象 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-119">Once the database is bound to the named resource pool and restored with recovery, monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Resource Pool Stats Object.</span></span> <span data-ttu-id="4b3bb-120">有关详细信息，请参阅 [SQL Server, Resource Pool Stats 对象](../performance-monitor/sql-server-resource-pool-stats-object.md)。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-120">For more information see [SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3bb-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b3bb-121">See Also</span></span>  
 <span data-ttu-id="4b3bb-122">[数据库与资源池绑定的指南，请参阅主题](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="4b3bb-122">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 <span data-ttu-id="4b3bb-123">[sys.sp_xtp_bind_db_resource_pool (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b3bb-123">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="4b3bb-124">[SQL Server，Resource Pool Stats 对象](../performance-monitor/sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="4b3bb-124">[SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="4b3bb-125">sys.dm_resource_governor_resource_pools</span><span class="sxs-lookup"><span data-stu-id="4b3bb-125">sys.dm_resource_governor_resource_pools</span></span>](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)  
  
  
