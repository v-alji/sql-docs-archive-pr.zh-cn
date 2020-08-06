---
title: 查询执行 (选项： SQL Server： "高级" 页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAdvanced
ms.assetid: 3ec788c7-22c3-4216-9ad0-81a168d17074
author: rothja
ms.author: jroth
ms.openlocfilehash: 3efc3dc8b42fc08969cc1afb85d4e629f6759e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590344"
---
# <a name="options-query-executionsql-serveradvanced-page"></a><span data-ttu-id="6dc9d-102">选项（“查询执行”:“SQL Server”:“高级”页）</span><span class="sxs-lookup"><span data-stu-id="6dc9d-102">Options (Query Execution:SQL Server:Advanced Page)</span></span>
  <span data-ttu-id="6dc9d-103">有几个使用 SET 命令的选项。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-103">Several options are available using the SET command.</span></span> <span data-ttu-id="6dc9d-104">使用此页可以指定在 SQL Server 查询编辑器中运行 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询时的 **set** 选项。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-104">Use this page to specify a **set** option for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries in the SQL Server Query Editor.</span></span> <span data-ttu-id="6dc9d-105">这些选项对其他代码编辑器不起任何作用。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-105">They have no effect on other code editors.</span></span> <span data-ttu-id="6dc9d-106">对这些选项所做的更改仅应用于新的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-106">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="6dc9d-107">若要更改当前查询的选项，请单击 **“查询”** 菜单或 **查询窗口中快捷菜单上的** “查询选项” [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-107">To change the options for the current queries, click **Query Options** on the **Query** menu or the shortcut menu of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window.</span></span> <span data-ttu-id="6dc9d-108">在 **“执行”** 下，单击 **“高级”**。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-108">Under **Execution**, click **Advanced**.</span></span> <span data-ttu-id="6dc9d-109">有关每个选项的详细信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-109">For more information on each of these, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6dc9d-110">选项</span><span class="sxs-lookup"><span data-stu-id="6dc9d-110">Options</span></span>  
 <span data-ttu-id="6dc9d-111">**SET NOCOUNT**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-111">**SET NOCOUNT**</span></span>  
 <span data-ttu-id="6dc9d-112">不随结果集以消息形式返回行计数。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-112">Does not return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="6dc9d-113">默认情况下清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-113">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="6dc9d-114">**SET NOEXEC**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-114">**SET NOEXEC**</span></span>  
 <span data-ttu-id="6dc9d-115">不运行查询。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-115">Does not run the query.</span></span> <span data-ttu-id="6dc9d-116">默认情况下清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-116">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="6dc9d-117">**SET PARSEONLY**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-117">**SET PARSEONLY**</span></span>  
 <span data-ttu-id="6dc9d-118">检查每个查询的语法，但不运行查询。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-118">Checks the syntax of each query but does not run the queries.</span></span> <span data-ttu-id="6dc9d-119">默认情况下清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-119">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="6dc9d-120">**SET CONCAT_NULL_YIELDS_NULL**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-120">**SET CONCAT_NULL_YIELDS_NULL**</span></span>  
 <span data-ttu-id="6dc9d-121">选中此复选框时，对于现有值与 NULL 相串联的查询，结果将始终返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-121">When this check box is selected, queries that concatenate an existing value with a NULL, always return a NULL as the result.</span></span> <span data-ttu-id="6dc9d-122">清除此复选框时，对于现有值与 NULL 相串联的查询，将返回该现有值。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-122">When this check box is cleared, an existing value concatenated with a NULL, returns the existing value.</span></span> <span data-ttu-id="6dc9d-123">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-123">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="6dc9d-124">**SET ARITHABORT**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-124">**SET ARITHABORT**</span></span>  
 <span data-ttu-id="6dc9d-125">选中此复选框时，如果 INSERT、DELETE 或 UPDATE 语句在表达式计算过程中遇到算术错误（溢出、被零除或域错误）时，则会终止查询或批。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-125">When this check box is selected, when an INSERT, DELETE, or UPDATE statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="6dc9d-126">清除此复选框时，如果可能的话，该值为 NULL，查询将继续进行，而结果中还会包含一条消息。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-126">When this check box is cleared, a NULL is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="6dc9d-127">有关详细信息，请参阅 [SET ARITHABORT (Transact-SQL)](/sql/t-sql/statements/set-arithabort-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-127">For more information, see [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).</span></span> <span data-ttu-id="6dc9d-128">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-128">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="6dc9d-129">**SET SHOWPLAN_TEXT**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-129">**SET SHOWPLAN_TEXT**</span></span>  
 <span data-ttu-id="6dc9d-130">选中此复选框时，将以文本格式返回每个查询的查询计划。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-130">When this check box is selected, the query plan is returned in text format with each query.</span></span> <span data-ttu-id="6dc9d-131">默认情况下，此复选框处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-131">This check box cleared by default.</span></span>  
  
 <span data-ttu-id="6dc9d-132">**SET STATISTICS TIME**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-132">**SET STATISTICS TIME**</span></span>  
 <span data-ttu-id="6dc9d-133">选中此复选框时，将返回每个查询的时间统计信息。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-133">When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="6dc9d-134">默认情况下清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-134">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="6dc9d-135">**SET STATISTICS IO**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-135">**SET STATISTICS IO**</span></span>  
 <span data-ttu-id="6dc9d-136">选中此复选框时，将返回每个查询的输入和输出统计信息。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-136">When this check box is selected, statistics regarding input and output are returned with each query.</span></span> <span data-ttu-id="6dc9d-137">默认情况下清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-137">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="6dc9d-138">**SET TRANSACTION ISOLATION LEVEL**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-138">**SET TRANSACTION ISOLATION LEVEL**</span></span>  
 <span data-ttu-id="6dc9d-139">默认情况下，将设置 READ COMMITTED 事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-139">The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="6dc9d-140">有关详细信息，请参阅 [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-140">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="6dc9d-141">SNAPSHOT 事务隔离级别不可用。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-141">SNAPSHOT transaction isolation level is not available.</span></span> <span data-ttu-id="6dc9d-142">若要使用 SNAPSHOT 隔离，请添加以下 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="6dc9d-142">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 <span data-ttu-id="6dc9d-143">**SET DEADLOCK PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-143">**SET DEADLOCK PRIORITY**</span></span>  
 <span data-ttu-id="6dc9d-144">如果使用默认值“正常”，则允许在发生死锁时每个查询具有相同的优先级。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-144">The default value of Normal allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="6dc9d-145">如果希望此查询在任何死锁冲突中都靠后考虑，并且选作要终止的查询，请选择优先级“低”。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-145">Select a priority of Low if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>  
  
 <span data-ttu-id="6dc9d-146">**SET LOCK TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-146">**SET LOCK TIMEOUT**</span></span>  
 <span data-ttu-id="6dc9d-147">默认值为 -1，指示在完成事务之前始终保留锁。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-147">The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="6dc9d-148">值为 0 时表示根本不等待，一遇到锁就返回信息。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-148">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="6dc9d-149">如果事务的锁的保留时间必须长于此时间，请提供一个大于 0 毫秒的值以终止事务。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-149">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>  
  
 <span data-ttu-id="6dc9d-150">**SET QUERY_GOVERNOR_COST_LIMIT**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-150">**SET QUERY_GOVERNOR_COST_LIMIT**</span></span>  
 <span data-ttu-id="6dc9d-151">使用 **QUERY_GOVERNOR_COST_LIMIT** 选项可以指定查询运行时间长度的上限。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-151">Use the **QUERY_GOVERNOR_COST_LIMIT** option to specify an upper limit for the time in which a query can run.</span></span> <span data-ttu-id="6dc9d-152">查询开销是指在特定硬件配置中完成查询所需的估计占用时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-152">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="6dc9d-153">默认设置 0 表示不限制查询运行时间的长度。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-153">The default setting of 0 indicates no limit to the length of time a query will run.</span></span>  
  
 <span data-ttu-id="6dc9d-154">**取消提供程序消息标头**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-154">**Suppress provider message headers**</span></span>  
 <span data-ttu-id="6dc9d-155">选中此复选框时，将不显示提供程序（如 SQLClient 提供程序）的状态消息。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-155">When this check box is selected, status messages from the provider (such as the SQLClient provider) are not displayed.</span></span> <span data-ttu-id="6dc9d-156">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-156">This check box is selected by default.</span></span> <span data-ttu-id="6dc9d-157">在排除可能在提供程序级别上失败的查询故障时，清除此复选框可查看提供程序消息。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-157">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>  
  
 <span data-ttu-id="6dc9d-158">**执行查询后断开连接**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-158">**Disconnect after the query executes**</span></span>  
 <span data-ttu-id="6dc9d-159">选中此复选框时，查询完成后会终止与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之间的连接。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-159">When this check box is selected, the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is terminated after the query completes.</span></span> <span data-ttu-id="6dc9d-160">默认情况下清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-160">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="6dc9d-161">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="6dc9d-161">**Reset to Default**</span></span>  
 <span data-ttu-id="6dc9d-162">将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="6dc9d-162">Resets all values on this page to the original default values.</span></span>  
  
  
