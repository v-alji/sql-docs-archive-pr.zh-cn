---
title: 删除数据库快照 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0d9d912a092e581fad7d3d53504309f63ba1806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576811"
---
# <a name="drop-a-database-snapshot-transact-sql"></a><span data-ttu-id="70b7e-102">删除数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70b7e-102">Drop a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="70b7e-103">删除数据库快照将删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的数据库快照，并删除快照使用的稀疏文件。</span><span class="sxs-lookup"><span data-stu-id="70b7e-103">Dropping a database snapshot deletes the database snapshot from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and deletes the sparse files that are used by the snapshot.</span></span> <span data-ttu-id="70b7e-104">删除数据库快照会终止所有到此快照的用户连接。</span><span class="sxs-lookup"><span data-stu-id="70b7e-104">When you drop a database snapshot, all user connections to it are terminated.</span></span>  
  
## <a name="security"></a><span data-ttu-id="70b7e-105">安全性</span><span class="sxs-lookup"><span data-stu-id="70b7e-105">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="70b7e-106">权限</span><span class="sxs-lookup"><span data-stu-id="70b7e-106">Permissions</span></span>  
 <span data-ttu-id="70b7e-107">具有 DROP DATABASE 权限的任何用户都可以删除数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70b7e-107">Any user with DROP DATABASE permissions can drop a database snapshot.</span></span>  
  
##  <a name="how-to-drop-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="70b7e-108">如何删除数据库快照（使用 Transact-SQL）</span><span class="sxs-lookup"><span data-stu-id="70b7e-108">How to Drop a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="70b7e-109">**删除数据库快照**</span><span class="sxs-lookup"><span data-stu-id="70b7e-109">**To drop a database snapshot**</span></span>  
  
1.  <span data-ttu-id="70b7e-110">标识要删除的数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70b7e-110">Identify the database snapshot that you want to drop.</span></span> <span data-ttu-id="70b7e-111">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70b7e-111">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="70b7e-112">有关详细信息，请参阅 [查看数据库快照 (SQL Server)](view-a-database-snapshot-sql-server.md)中查看数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70b7e-112">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="70b7e-113">执行 [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) 语句，并指定要删除的数据库快照的名称。</span><span class="sxs-lookup"><span data-stu-id="70b7e-113">Issue a [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) statement, specifying the name of the database snapshot to be dropped.</span></span> <span data-ttu-id="70b7e-114">语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="70b7e-114">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="70b7e-115">DROP DATABASE *database_snapshot_name* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="70b7e-115">DROP DATABASE *database_snapshot_name* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="70b7e-116">其中， *database_snapshot_name* 是要删除的数据库快照的名称。</span><span class="sxs-lookup"><span data-stu-id="70b7e-116">Where *database_snapshot_name* is the name of the database snapshot to be dropped.</span></span>  
  
####  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="70b7e-117">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70b7e-117">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="70b7e-118">此示例将删除名为 SalesSnapshot0600 的数据库快照，而不影响源数据库。</span><span class="sxs-lookup"><span data-stu-id="70b7e-118">This example drops a database snapshot named SalesSnapshot0600, without affecting the source database.</span></span>  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 <span data-ttu-id="70b7e-119">到 SalesSnapshot0600 的所有用户连接都被终止，并删除快照使用的所有 NTFS 文件系统稀疏文件。</span><span class="sxs-lookup"><span data-stu-id="70b7e-119">Any user connections to SalesSnapshot0600 are terminated, and all of the NTFS file system sparse files used by the snapshot are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70b7e-120">有关数据库快照如何使用稀疏文件的信息，请参阅 [数据库快照 (SQL Server)](database-snapshots-sql-server.md)中查看数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70b7e-120">For information about the use of sparse files by database snapshots, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="70b7e-121">相关任务</span><span class="sxs-lookup"><span data-stu-id="70b7e-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="70b7e-122">创建数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70b7e-122">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="70b7e-123">查看数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="70b7e-123">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="70b7e-124">将数据库恢复到数据库快照</span><span class="sxs-lookup"><span data-stu-id="70b7e-124">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="70b7e-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70b7e-125">See Also</span></span>  
 <span data-ttu-id="70b7e-126">[DROP DATABASE (Transact SQL)](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="70b7e-126">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 [<span data-ttu-id="70b7e-127">数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="70b7e-127">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
