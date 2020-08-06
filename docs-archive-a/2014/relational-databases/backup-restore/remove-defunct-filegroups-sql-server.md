---
title: 删除失效文件组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], defunct filegroups
- defunct filegroups
- restoring filegroups [SQL Server]
- deferred transactions
- filegroups [SQL Server], defunct
- unrestored filegroups
ms.assetid: 055f9c6a-5c18-4942-98e7-ec918f0ff975
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2bcba095d668c5c1ab317269a18af4dc996f63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691756"
---
# <a name="remove-defunct-filegroups-sql-server"></a><span data-ttu-id="d40c7-102">删除失效文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d40c7-102">Remove Defunct Filegroups (SQL Server)</span></span>
  <span data-ttu-id="d40c7-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除失效的文件组。</span><span class="sxs-lookup"><span data-stu-id="d40c7-103">This topic describes how to remove defunct filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d40c7-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d40c7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d40c7-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d40c7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d40c7-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d40c7-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="d40c7-107">建议</span><span class="sxs-lookup"><span data-stu-id="d40c7-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d40c7-108">安全性</span><span class="sxs-lookup"><span data-stu-id="d40c7-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d40c7-109">**若要删除失效的文件组，请使用：**</span><span class="sxs-lookup"><span data-stu-id="d40c7-109">**To remove defunct filegroups, using:**</span></span>  
  
     [<span data-ttu-id="d40c7-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d40c7-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d40c7-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d40c7-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d40c7-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="d40c7-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d40c7-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d40c7-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d40c7-114">本主题与包含多个文件或文件组的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关；在简单模式下，仅与包含只读文件组的数据库相关。</span><span class="sxs-lookup"><span data-stu-id="d40c7-114">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
-   <span data-ttu-id="d40c7-115">删除离线文件组后，文件组中的所有文件都将失效。</span><span class="sxs-lookup"><span data-stu-id="d40c7-115">All files in a filegroup become defunct when an offline filegroup is removed.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d40c7-116">建议</span><span class="sxs-lookup"><span data-stu-id="d40c7-116">Recommendations</span></span>  
  
-   <span data-ttu-id="d40c7-117">如果未还原的文件组再也不用还原了，您可以将该文件组从数据库中删除，从而使文件组 *失效* 。</span><span class="sxs-lookup"><span data-stu-id="d40c7-117">If an unrestored filegroup will never have to be restored, you can make the filegroup *defunct* by removing it from the database.</span></span> <span data-ttu-id="d40c7-118">失效文件组再也不能还原到此数据库，但其元数据仍然保留。</span><span class="sxs-lookup"><span data-stu-id="d40c7-118">The defunct filegroup can never be restored to this database, but its metadata remains.</span></span> <span data-ttu-id="d40c7-119">文件组失效后，可以重新启动数据库，恢复数据库会使数据库在还原的文件组中保持一致。</span><span class="sxs-lookup"><span data-stu-id="d40c7-119">After the filegroup is defunct, the database can be restarted, and recovery will make the database consistent across the restored filegroups.</span></span>  
  
     <span data-ttu-id="d40c7-120">例如，可以选择让文件组失效来解决由于数据库中不再需要的脱机文件组而导致的事务延迟。</span><span class="sxs-lookup"><span data-stu-id="d40c7-120">For example, making a filegroup defunct is an option for resolving deferred transactions that were caused by an offline filegroup that you no longer want in the database.</span></span> <span data-ttu-id="d40c7-121">这样的文件组失效之后，由于这些文件组的脱机而延迟的事务将脱离延迟状态。</span><span class="sxs-lookup"><span data-stu-id="d40c7-121">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span> <span data-ttu-id="d40c7-122">有关详细信息，请参阅 [延迟的事务 (SQL Server)](deferred-transactions-sql-server.md)中删除失效的文件组。</span><span class="sxs-lookup"><span data-stu-id="d40c7-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d40c7-123">Security</span><span class="sxs-lookup"><span data-stu-id="d40c7-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d40c7-124">权限</span><span class="sxs-lookup"><span data-stu-id="d40c7-124">Permissions</span></span>  
 <span data-ttu-id="d40c7-125">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="d40c7-125">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d40c7-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d40c7-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="d40c7-127">删除失效的文件组</span><span class="sxs-lookup"><span data-stu-id="d40c7-127">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="d40c7-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="d40c7-128">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d40c7-129">展开 **“数据库”** ，右键单击要从其中删除文件的数据库，再单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="d40c7-129">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d40c7-130">选择 **“文件”** 页。</span><span class="sxs-lookup"><span data-stu-id="d40c7-130">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="d40c7-131">在 **“数据库文件”** 网格中，选择要删除的文件，单击 **“删除”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d40c7-131">In the **Database files** grid, select the files to delete, click **Remove**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="d40c7-132">选择 **“文件组”** 页。</span><span class="sxs-lookup"><span data-stu-id="d40c7-132">Select the **Filegroups** page.</span></span>  
  
6.  <span data-ttu-id="d40c7-133">在 **“行”** 网格中，选择要删除的文件组，单击 **“删除”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d40c7-133">In the **Rows** grid, select the filegroup to delete, click **Remove**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d40c7-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d40c7-134">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="d40c7-135">删除失效的文件组</span><span class="sxs-lookup"><span data-stu-id="d40c7-135">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="d40c7-136">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d40c7-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d40c7-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d40c7-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d40c7-138">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="d40c7-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d40c7-139">（注意：  此示例假定文件和文件组已存在。</span><span class="sxs-lookup"><span data-stu-id="d40c7-139">(**Note:** This example assumes that the files and filegroup already exist.</span></span> <span data-ttu-id="d40c7-140">若要创建这些对象，请参阅 [ALTER DATABASE 和文件组选项](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)主题中的示例 B。）第一个示例通过使用具有 `test1dat3` 子句的 `test1dat4` 语句，从失效的文件组中删除 `ALTER DATABASE` 和 `REMOVE FILE` 文件。</span><span class="sxs-lookup"><span data-stu-id="d40c7-140">To create these objects, see example B in the [ALTER DATABASE File and Filegroup Options](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) topic.) The first example removes the `test1dat3` and `test1dat4` files from the defunct filegroup by using the `ALTER DATABASE` statement with the `REMOVE FILE` clause.</span></span> <span data-ttu-id="d40c7-141">第二个示例通过使用 `Test1FG1`子句，删除失效的文件组 `REMOVE FILEGROUP` 。</span><span class="sxs-lookup"><span data-stu-id="d40c7-141">The second example removes the defunct filegroup `Test1FG1`by using the `REMOVE FILEGROUP` clause.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat3 ;  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4 ;  
GO  
  
```  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILEGROUP Test1FG1 ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d40c7-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d40c7-142">See Also</span></span>  
 <span data-ttu-id="d40c7-143">[ALTER DATABASE 文件和文件组选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span><span class="sxs-lookup"><span data-stu-id="d40c7-143">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span></span>  
 <span data-ttu-id="d40c7-144">[延迟的事务 (SQL Server)](deferred-transactions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d40c7-144">[Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md) </span></span>  
 <span data-ttu-id="d40c7-145">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d40c7-145">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="d40c7-146">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d40c7-146">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="d40c7-147">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d40c7-147">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="d40c7-148">[还原页 (SQL Server)](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d40c7-148">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 [<span data-ttu-id="d40c7-149">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d40c7-149">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
