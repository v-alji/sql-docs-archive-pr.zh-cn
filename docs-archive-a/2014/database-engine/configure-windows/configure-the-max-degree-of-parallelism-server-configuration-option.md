---
title: 配置 max degree of parallelism 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 824dc837142acc4a0898cb04b4a8687bc5be4043
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588044"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a><span data-ttu-id="b42df-102">配置 max degree of parallelism 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="b42df-102">Configure the max degree of parallelism Server Configuration Option</span></span>
  <span data-ttu-id="b42df-103">本主题说明如何 `max degree of parallelism` 使用或在中配置服务器配置选项 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b42df-103">This topic describes how to configure the `max degree of parallelism` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b42df-104">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例在具有多个微处理器或 CPU 的计算机上运行时，它将为每个并行计划的执行检测最佳并行度（即运行一个语句所使用的处理器数）。</span><span class="sxs-lookup"><span data-stu-id="b42df-104">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on a computer that has more than one microprocessor or CPU, it detects the best degree of parallelism, that is, the number of processors employed to run a single statement, for each parallel plan execution.</span></span> <span data-ttu-id="b42df-105">您可以使用 `max degree of parallelism` 选项来限制执行并行计划时所用的处理器数量。</span><span class="sxs-lookup"><span data-stu-id="b42df-105">You can use the `max degree of parallelism` option to limit the number of processors to use in parallel plan execution.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b42df-106">考虑为查询、索引数据定义语言 (DDL) 操作、静态的和由键集驱动的游标填充实施并行执行计划。</span><span class="sxs-lookup"><span data-stu-id="b42df-106">considers parallel execution plans for queries, index data definition language (DDL) operations, and static and keyset-driven cursor population.</span></span>  
  
 <span data-ttu-id="b42df-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b42df-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b42df-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b42df-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b42df-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b42df-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b42df-110">建议</span><span class="sxs-lookup"><span data-stu-id="b42df-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b42df-111">安全性</span><span class="sxs-lookup"><span data-stu-id="b42df-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b42df-112">**配置 max degree of parallelism 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="b42df-112">**To configure the max degree of parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="b42df-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b42df-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b42df-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b42df-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="b42df-115">**跟进：**  [在配置最大并行度选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="b42df-115">**Follow Up:**  [After you configure the max degree of parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b42df-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="b42df-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b42df-117">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b42df-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b42df-118">如果 affinity mask 选项不设置为默认值，则可能会限制可用于对称多处理 (SMP) 系统上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的处理器数。</span><span class="sxs-lookup"><span data-stu-id="b42df-118">If the affinity mask option is not set to the default, it may restrict the number of processors available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on symmetric multiprocessing (SMP) systems.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b42df-119">建议</span><span class="sxs-lookup"><span data-stu-id="b42df-119">Recommendations</span></span>  
  
-   <span data-ttu-id="b42df-120">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="b42df-120">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="b42df-121">若要使服务器能够确定最大并行度，请将此选项设置为默认值 0。</span><span class="sxs-lookup"><span data-stu-id="b42df-121">To enable the server to determine the maximum degree of parallelism, set this option to 0, the default value.</span></span> <span data-ttu-id="b42df-122">若将 maximum degree of parallelism 设置为 0， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将能够使用至多 64 个可用的处理器。</span><span class="sxs-lookup"><span data-stu-id="b42df-122">Setting maximum degree of parallelism to 0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use all the available processors up to 64 processors.</span></span> <span data-ttu-id="b42df-123">若要取消生成并行计划，请将 `max degree of parallelism` 设置为 1。</span><span class="sxs-lookup"><span data-stu-id="b42df-123">To suppress parallel plan generation, set `max degree of parallelism` to 1.</span></span> <span data-ttu-id="b42df-124">将该值设置为 1 到 32,767 之间的数值来指定执行单个查询所使用的最大处理器核数。</span><span class="sxs-lookup"><span data-stu-id="b42df-124">Set the value to a number from 1 to 32,767 to specify the maximum number of processor cores that can be used by a single query execution.</span></span> <span data-ttu-id="b42df-125">如果指定的值比可用的处理器数大，则使用实际可用数量的处理器。</span><span class="sxs-lookup"><span data-stu-id="b42df-125">If a value greater than the number of available processors is specified, the actual number of available processors is used.</span></span> <span data-ttu-id="b42df-126">如果计算机只有一个处理器，则将忽略 `max degree of parallelism` 值。</span><span class="sxs-lookup"><span data-stu-id="b42df-126">If the computer has only one processor, the `max degree of parallelism` value is ignored.</span></span>  
  
-   <span data-ttu-id="b42df-127">您可以通过在查询语句中指定 MAXDOP 查询提示来覆盖查询中的 max degree of parallelism 值。</span><span class="sxs-lookup"><span data-stu-id="b42df-127">You can override the max degree of parallelism value in queries by specifying the MAXDOP query hint in the query statement.</span></span> <span data-ttu-id="b42df-128">有关详细信息，请参阅[查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)。</span><span class="sxs-lookup"><span data-stu-id="b42df-128">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
-   <span data-ttu-id="b42df-129">索引操作（如创建或重新生成索引、或删除聚集索引）可能会大量占用资源。</span><span class="sxs-lookup"><span data-stu-id="b42df-129">Index operations that create or rebuild an index, or that drop a clustered index, can be resource intensive.</span></span> <span data-ttu-id="b42df-130">您可以通过在索引语句中指定 MAXDOP 索引选项来覆盖索引操作的 max degree of parallelism 值。</span><span class="sxs-lookup"><span data-stu-id="b42df-130">You can override the max degree of parallelism value for index operations by specifying the MAXDOP index option in the index statement.</span></span> <span data-ttu-id="b42df-131">MAXDOP 值在执行时应用于语句，但不存储在索引元数据中。</span><span class="sxs-lookup"><span data-stu-id="b42df-131">The MAXDOP value is applied to the statement at execution time and is not stored in the index metadata.</span></span> <span data-ttu-id="b42df-132">有关详细信息，请参阅 [配置并行索引操作](../../relational-databases/indexes/configure-parallel-index-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="b42df-132">For more information, see [Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md).</span></span>  
  
-   <span data-ttu-id="b42df-133">除了查询和索引操作之外，此选项还控制 DBCC CHECKTABLE、DBCC CHECKDB 和 DBCC CHECKFILEGROUP 的并行。</span><span class="sxs-lookup"><span data-stu-id="b42df-133">In addition to queries and index operations, this option also controls the parallelism of DBCC CHECKTABLE, DBCC CHECKDB, and DBCC CHECKFILEGROUP.</span></span> <span data-ttu-id="b42df-134">使用跟踪标志 2528，可以禁用为这些语句所做的并行执行计划。</span><span class="sxs-lookup"><span data-stu-id="b42df-134">You can disable parallel execution plans for these statements by using trace flag 2528.</span></span> <span data-ttu-id="b42df-135">有关详细信息，请参阅[跟踪标志 (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b42df-135">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b42df-136">Security</span><span class="sxs-lookup"><span data-stu-id="b42df-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b42df-137">权限</span><span class="sxs-lookup"><span data-stu-id="b42df-137">Permissions</span></span>  
 <span data-ttu-id="b42df-138">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="b42df-138">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="b42df-139">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="b42df-139">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="b42df-140">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="b42df-140">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b42df-141">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b42df-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="b42df-142">配置 max degree of parallelism 选项</span><span class="sxs-lookup"><span data-stu-id="b42df-142">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="b42df-143">在“对象资源管理器”中，右键单击服务器并选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="b42df-143">In **Object Explorer**, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b42df-144">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="b42df-144">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="b42df-145">在 **“最大并行度”** 框中，选择执行并行计划时所使用的最大处理器数。</span><span class="sxs-lookup"><span data-stu-id="b42df-145">In the **Max Degree of Parallelism** box, select the maximum number of processors to use in parallel plan execution.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b42df-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b42df-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="b42df-147">配置 max degree of parallelism 选项</span><span class="sxs-lookup"><span data-stu-id="b42df-147">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="b42df-148">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b42df-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b42df-149">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b42df-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b42df-150">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b42df-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b42df-151">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `max degree of parallelism` 选项的值配置为 `8`。</span><span class="sxs-lookup"><span data-stu-id="b42df-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max degree of parallelism` option to `8`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 <span data-ttu-id="b42df-152">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="b42df-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-degree-of-parallelism-option"></a><a name="FollowUp"></a> <span data-ttu-id="b42df-153">跟进：在配置“最大并行度”选项之后</span><span class="sxs-lookup"><span data-stu-id="b42df-153">Follow Up: After you configure the max degree of parallelism option</span></span>  
 <span data-ttu-id="b42df-154">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="b42df-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42df-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b42df-155">See Also</span></span>  
 <span data-ttu-id="b42df-156">[affinity mask 服务器配置选项](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="b42df-156">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="b42df-157">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="b42df-158">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b42df-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="b42df-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="b42df-160">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-160">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="b42df-161">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-161">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="b42df-162">[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-162">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="b42df-163">[DBCC CHECKTABLE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-163">[DBCC CHECKTABLE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span></span>  
 <span data-ttu-id="b42df-164">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-164">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="b42df-165">[DBCC CHECKFILEGROUP &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b42df-165">[DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="b42df-166">[配置并行索引操作](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="b42df-166">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="b42df-167">[查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="b42df-167">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="b42df-168">设置索引选项</span><span class="sxs-lookup"><span data-stu-id="b42df-168">Set Index Options</span></span>](../../relational-databases/indexes/set-index-options.md)  
  
  
