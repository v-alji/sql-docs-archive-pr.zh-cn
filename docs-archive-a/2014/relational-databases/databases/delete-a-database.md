---
title: 删除数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 633d97815cf69da12f1aa67fd8ef626a2d46e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693937"
---
# <a name="delete-a-database"></a><span data-ttu-id="ac7a7-102">删除数据库</span><span class="sxs-lookup"><span data-stu-id="ac7a7-102">Delete a Database</span></span>
  <span data-ttu-id="ac7a7-103">本主题说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除用户定义的数据库。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-103">This topic describes how to delete a user-defined database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ac7a7-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ac7a7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ac7a7-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ac7a7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ac7a7-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ac7a7-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ac7a7-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="ac7a7-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ac7a7-108">建议</span><span class="sxs-lookup"><span data-stu-id="ac7a7-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ac7a7-109">安全性</span><span class="sxs-lookup"><span data-stu-id="ac7a7-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ac7a7-110">**删除数据库，使用：**</span><span class="sxs-lookup"><span data-stu-id="ac7a7-110">**To delete a database, using:**</span></span>  
  
     [<span data-ttu-id="ac7a7-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ac7a7-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ac7a7-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ac7a7-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ac7a7-113">**跟进：** [在删除数据库之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ac7a7-113">**Follow Up:**  [After deleting a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ac7a7-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="ac7a7-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ac7a7-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ac7a7-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ac7a7-116">不能删除系统数据库。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-116">System databases cannot be deleted.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="ac7a7-117">先决条件</span><span class="sxs-lookup"><span data-stu-id="ac7a7-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="ac7a7-118">删除数据库中的所有数据库快照。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-118">Delete any database snapshots that exist on the database.</span></span> <span data-ttu-id="ac7a7-119">有关详细信息，请参阅 [删除数据库快照 (Transact-SQL)](drop-a-database-snapshot-transact-sql.md)实例。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-119">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="ac7a7-120">如果日志传送涉及数据库，请删除日志传送。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-120">If the database is involved in log shipping, remove log shipping.</span></span>  
  
-   <span data-ttu-id="ac7a7-121">如果为事务复制发布了数据库，或将数据库发布或订阅到合并复制，请从数据库中删除复制。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-121">If the database is published for transactional replication, or published or subscribed to merge replication, remove replication from the database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ac7a7-122">建议</span><span class="sxs-lookup"><span data-stu-id="ac7a7-122">Recommendations</span></span>  
  
-   <span data-ttu-id="ac7a7-123">考虑对数据库进行完整备份。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-123">Consider taking a full backup of the database.</span></span> <span data-ttu-id="ac7a7-124">只有通过还原备份才能重新创建已删除的数据库。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-124">A deleted database can be re-created only by restoring a backup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ac7a7-125">Security</span><span class="sxs-lookup"><span data-stu-id="ac7a7-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ac7a7-126">权限</span><span class="sxs-lookup"><span data-stu-id="ac7a7-126">Permissions</span></span>  
 <span data-ttu-id="ac7a7-127">若要执行 DROP DATABASE 操作，用户必须至少对数据库具有 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-127">To execute DROP DATABASE, at a minimum, a user must have CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ac7a7-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ac7a7-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="ac7a7-129">删除数据库</span><span class="sxs-lookup"><span data-stu-id="ac7a7-129">To delete a database</span></span>  
  
1.  <span data-ttu-id="ac7a7-130">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-130">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ac7a7-131">展开 **“数据库”** ，右键单击要删除的数据库，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-131">Expand **Databases**, right-click the database to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="ac7a7-132">确认选择了正确数据库，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-132">Confirm the correct database is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ac7a7-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ac7a7-133">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="ac7a7-134">删除数据库</span><span class="sxs-lookup"><span data-stu-id="ac7a7-134">To delete a database</span></span>  
  
1.  <span data-ttu-id="ac7a7-135">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ac7a7-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ac7a7-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ac7a7-138">此示例删除 `Sales` 和 `NewSales` 数据库。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-138">The example removes the `Sales` and `NewSales` databases.</span></span>  
  
```sql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="follow-up-after-deleting-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="ac7a7-139">跟进：在删除数据库之后</span><span class="sxs-lookup"><span data-stu-id="ac7a7-139">Follow Up: After deleting a database</span></span>  
 <span data-ttu-id="ac7a7-140">备份 **master** 数据库。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-140">Back up the **master** database.</span></span> <span data-ttu-id="ac7a7-141">如果必须还原 **master** ，则自上次备份 **master** 之后删除的所有数据库都将仍在系统目录视图中具有引用，并且可能会导致出现错误消息。</span><span class="sxs-lookup"><span data-stu-id="ac7a7-141">If **master** must be restored, any database that has been deleted since the last backup of **master** will still have references in the system catalog views and may cause error messages to be raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7a7-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac7a7-142">See Also</span></span>  
 <span data-ttu-id="ac7a7-143">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ac7a7-143">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="ac7a7-144">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ac7a7-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
