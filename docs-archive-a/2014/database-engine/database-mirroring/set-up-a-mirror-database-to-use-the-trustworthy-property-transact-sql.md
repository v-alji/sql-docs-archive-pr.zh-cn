---
title: 将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd46a08037bcb6eee178a96d84bdab358e5350d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690098"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a><span data-ttu-id="9e02f-102">将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9e02f-102">Set Up a Mirror Database to Use the Trustworthy Property (Transact-SQL)</span></span>
  <span data-ttu-id="9e02f-103">备份数据库时，TRUSTWORTHY 数据库属性设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="9e02f-103">When a database is backed up, the TRUSTWORTHY database property is set to OFF.</span></span> <span data-ttu-id="9e02f-104">因此，在新的镜像数据库中，TRUSTWORTHY 始终为 OFF。</span><span class="sxs-lookup"><span data-stu-id="9e02f-104">Therefore, on a new mirror database TRUSTWORTHY is always OFF.</span></span> <span data-ttu-id="9e02f-105">如果数据库在故障转移后需要得到信任，则必须在镜像开始后执行额外的设置步骤。</span><span class="sxs-lookup"><span data-stu-id="9e02f-105">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e02f-106">有关此数据库属性的信息，请参阅 [TRUSTWORTHY 数据库属性](../../relational-databases/security/trustworthy-database-property.md)。</span><span class="sxs-lookup"><span data-stu-id="9e02f-106">For information about this database property, see [TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="9e02f-107">过程</span><span class="sxs-lookup"><span data-stu-id="9e02f-107">Procedure</span></span>  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a><span data-ttu-id="9e02f-108">将镜像数据库设置为使用 Trustworthy 属性</span><span class="sxs-lookup"><span data-stu-id="9e02f-108">To setup a mirror database to use the Trustworthy Property</span></span>  
  
1.  <span data-ttu-id="9e02f-109">在主体服务器实例上，验证主体数据库是否已打开 Trustworthy 属性。</span><span class="sxs-lookup"><span data-stu-id="9e02f-109">On the principal server instance, verify that the principal database has the Trustworthy property turned on.</span></span>  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     <span data-ttu-id="9e02f-110">有关详细信息，请参阅 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9e02f-110">For more information, see [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).</span></span>  
  
2.  <span data-ttu-id="9e02f-111">开始镜像后，验证数据库当前是否为主体数据库，会话是否正在使用同步运行模式以及是否已同步了会话。</span><span class="sxs-lookup"><span data-stu-id="9e02f-111">After starting mirroring, verify that the database is currently the principal database, the session is using a synchronous operating mode, and the session is already synchronized.</span></span>  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     <span data-ttu-id="9e02f-112">有关详细信息，请参阅 [sys.database_mirroring (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9e02f-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
3.  <span data-ttu-id="9e02f-113">一旦同步了镜像会话，就要手动故障转移到镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="9e02f-113">Once the mirroring session is synchronized, manually fail over to the mirror database.</span></span>  
  
     <span data-ttu-id="9e02f-114">此操作既可以在 SQL Server Management Studio 中执行，也可以使用 Transact-SQL 执行：</span><span class="sxs-lookup"><span data-stu-id="9e02f-114">This can be done in either SQL Server Management Studio or using Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="9e02f-115">手动故障转移数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9e02f-115">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="9e02f-116">手动故障转移数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9e02f-116">Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  <span data-ttu-id="9e02f-117">使用以下 ALTER DATABASE 命令打开 Trustworthy 数据库属性：</span><span class="sxs-lookup"><span data-stu-id="9e02f-117">Turn on the trustworthy database property using the following ALTER DATABASE command:</span></span>  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     <span data-ttu-id="9e02f-118">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9e02f-118">For more information, see[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
5.  <span data-ttu-id="9e02f-119">或者，再次手动故障转移，返回原始主体。</span><span class="sxs-lookup"><span data-stu-id="9e02f-119">Optionally, manually failover again to return to the original principal.</span></span>  
  
6.  <span data-ttu-id="9e02f-120">或者，通过将 SAFETY 设置为 OFF 并确保 WITNESS 也设置为 OFF，切换到异步、高性能模式。</span><span class="sxs-lookup"><span data-stu-id="9e02f-120">Optionally, switch to asynchronous, high-performance mode by setting SAFETY to OFF and ensuring that WITNESS is also set to OFF.</span></span>  
  
     <span data-ttu-id="9e02f-121">在 Transact-SQL 中：</span><span class="sxs-lookup"><span data-stu-id="9e02f-121">In Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="9e02f-122">更改数据库镜像会话中的事务安全 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9e02f-122">Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [<span data-ttu-id="9e02f-123">从数据库镜像会话删除见证服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9e02f-123">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     <span data-ttu-id="9e02f-124">在 SQL Server Management Studio 中：</span><span class="sxs-lookup"><span data-stu-id="9e02f-124">In SQL Server Management Studio:</span></span>  
  
    -   [<span data-ttu-id="9e02f-125">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9e02f-125">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e02f-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e02f-126">See Also</span></span>  
 <span data-ttu-id="9e02f-127">[TRUSTWORTHY 数据库属性](../../relational-databases/security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="9e02f-127">[TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="9e02f-128">设置加密的镜像数据库</span><span class="sxs-lookup"><span data-stu-id="9e02f-128">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
