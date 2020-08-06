---
title: MSSQLSERVER_2814 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26b1fae5b683ed72cb93c3f81981bd41e2f4ad4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586738"
---
# <a name="mssqlserver_2814"></a><span data-ttu-id="421ec-102">MSSQLSERVER_2814</span><span class="sxs-lookup"><span data-stu-id="421ec-102">MSSQLSERVER_2814</span></span>
    
## <a name="details"></a><span data-ttu-id="421ec-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="421ec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="421ec-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="421ec-104">Product Name</span></span>|<span data-ttu-id="421ec-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="421ec-105">SQL Server</span></span>|  
|<span data-ttu-id="421ec-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="421ec-106">Event ID</span></span>|<span data-ttu-id="421ec-107">2814</span><span class="sxs-lookup"><span data-stu-id="421ec-107">2814</span></span>|  
|<span data-ttu-id="421ec-108">事件源</span><span class="sxs-lookup"><span data-stu-id="421ec-108">Event Source</span></span>|<span data-ttu-id="421ec-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="421ec-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="421ec-110">组件</span><span class="sxs-lookup"><span data-stu-id="421ec-110">Component</span></span>|<span data-ttu-id="421ec-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="421ec-111">SQLEngine</span></span>|  
|<span data-ttu-id="421ec-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="421ec-112">Symbolic Name</span></span>|<span data-ttu-id="421ec-113">PR_POSSIBLE_INFINITE_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="421ec-113">PR_POSSIBLE_INFINITE_RECOMPILE</span></span>|  
|<span data-ttu-id="421ec-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="421ec-114">Message Text</span></span>|<span data-ttu-id="421ec-115">检测到可能无限的重新编译: SQLHANDLE %hs，PlanHandle %hs，起始偏移量 %d，结束偏移量 %d。</span><span class="sxs-lookup"><span data-stu-id="421ec-115">A possible infinite recompile was detected for SQLHANDLE %hs, PlanHandle %hs, starting offset %d, ending offset %d.</span></span> <span data-ttu-id="421ec-116">上次重新编译的原因为 %d。</span><span class="sxs-lookup"><span data-stu-id="421ec-116">The last recompile reason was %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="421ec-117">说明</span><span class="sxs-lookup"><span data-stu-id="421ec-117">Explanation</span></span>  
 <span data-ttu-id="421ec-118">一个或多个语句导致查询批处理至少重新编译 50 次。</span><span class="sxs-lookup"><span data-stu-id="421ec-118">One or more statements caused the query batch to recompile at least 50 times.</span></span> <span data-ttu-id="421ec-119">应更正指定语句以免进一步重新编译。</span><span class="sxs-lookup"><span data-stu-id="421ec-119">The specified statement should be corrected to avoid further recompilations.</span></span>  
  
 <span data-ttu-id="421ec-120">下表列出了重新编译的原因。</span><span class="sxs-lookup"><span data-stu-id="421ec-120">The following table lists the reasons for recompilation.</span></span>  
  
|<span data-ttu-id="421ec-121">原因代码</span><span class="sxs-lookup"><span data-stu-id="421ec-121">Reason code</span></span>|<span data-ttu-id="421ec-122">说明</span><span class="sxs-lookup"><span data-stu-id="421ec-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="421ec-123">1</span><span class="sxs-lookup"><span data-stu-id="421ec-123">1</span></span>|<span data-ttu-id="421ec-124">架构已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-124">Schema changed</span></span>|  
|<span data-ttu-id="421ec-125">2</span><span class="sxs-lookup"><span data-stu-id="421ec-125">2</span></span>|<span data-ttu-id="421ec-126">统计信息已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-126">Statistics changed</span></span>|  
|<span data-ttu-id="421ec-127">3</span><span class="sxs-lookup"><span data-stu-id="421ec-127">3</span></span>|<span data-ttu-id="421ec-128">编译延迟</span><span class="sxs-lookup"><span data-stu-id="421ec-128">Deferred compile</span></span>|  
|<span data-ttu-id="421ec-129">4</span><span class="sxs-lookup"><span data-stu-id="421ec-129">4</span></span>|<span data-ttu-id="421ec-130">所设置的选项已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-130">Set option changed</span></span>|  
|<span data-ttu-id="421ec-131">5</span><span class="sxs-lookup"><span data-stu-id="421ec-131">5</span></span>|<span data-ttu-id="421ec-132">临时表已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-132">Temp table changed</span></span>|  
|<span data-ttu-id="421ec-133">6</span><span class="sxs-lookup"><span data-stu-id="421ec-133">6</span></span>|<span data-ttu-id="421ec-134">远程行集已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-134">Remote rowset changed</span></span>|  
|<span data-ttu-id="421ec-135">7</span><span class="sxs-lookup"><span data-stu-id="421ec-135">7</span></span>|<span data-ttu-id="421ec-136">For Browse 权限已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-136">For Browse permissions changed</span></span>|  
|<span data-ttu-id="421ec-137">8</span><span class="sxs-lookup"><span data-stu-id="421ec-137">8</span></span>|<span data-ttu-id="421ec-138">查询通知环境已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-138">Query notification environment changed</span></span>|  
|<span data-ttu-id="421ec-139">9</span><span class="sxs-lookup"><span data-stu-id="421ec-139">9</span></span>|<span data-ttu-id="421ec-140">分区视图已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-140">Partition view changed</span></span>|  
|<span data-ttu-id="421ec-141">10</span><span class="sxs-lookup"><span data-stu-id="421ec-141">10</span></span>|<span data-ttu-id="421ec-142">游标选项已更改</span><span class="sxs-lookup"><span data-stu-id="421ec-142">Cursor options changed</span></span>|  
|<span data-ttu-id="421ec-143">11</span><span class="sxs-lookup"><span data-stu-id="421ec-143">11</span></span>|<span data-ttu-id="421ec-144">已请求选项（重新编译）</span><span class="sxs-lookup"><span data-stu-id="421ec-144">Option (recompile) requested</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="421ec-145">用户操作</span><span class="sxs-lookup"><span data-stu-id="421ec-145">User Action</span></span>  
  
1.  <span data-ttu-id="421ec-146">通过运行以下查询查看导致重新编译的语句。</span><span class="sxs-lookup"><span data-stu-id="421ec-146">View the statement causing the recompilation by running the following query.</span></span> <span data-ttu-id="421ec-147">将 *sql_handle*、*starting_offset*、*ending_offset* 和 *plan_handle* 占位符替换为错误消息中指定的值。</span><span class="sxs-lookup"><span data-stu-id="421ec-147">Replace the *sql_handle*, *starting_offset*, *ending_offset*, and *plan_handle* placeholders with the values specified in the error message.</span></span> <span data-ttu-id="421ec-148">请注意，对于临时和预定义 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，**database_name** 和 **object_name** 列将为 NULL。</span><span class="sxs-lookup"><span data-stu-id="421ec-148">Note that the **database_name** and **object_name** columns will be NULL for ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="421ec-149">SELECT DB_NAME(st.dbid) AS database_name</span><span class="sxs-lookup"><span data-stu-id="421ec-149">SELECT DB_NAME(st.dbid) AS database_name</span></span>  
  
     <span data-ttu-id="421ec-150">, OBJECT_NAME(st.objectid) AS object_name</span><span class="sxs-lookup"><span data-stu-id="421ec-150">, OBJECT_NAME(st.objectid) AS object_name</span></span>  
  
     <span data-ttu-id="421ec-151">, st.text</span><span class="sxs-lookup"><span data-stu-id="421ec-151">, st.text</span></span>  
  
     <span data-ttu-id="421ec-152">FROM sys.dm_exec_query_stats</span><span class="sxs-lookup"><span data-stu-id="421ec-152">FROM sys.dm_exec_query_stats AS qs</span></span>  
  
     <span data-ttu-id="421ec-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span><span class="sxs-lookup"><span data-stu-id="421ec-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span></span>  
  
     <span data-ttu-id="421ec-154">WHERE qs.statement_start_offset = *starting_offset*</span><span class="sxs-lookup"><span data-stu-id="421ec-154">WHERE qs.statement_start_offset = *starting_offset*</span></span>  
  
     <span data-ttu-id="421ec-155">AND qs.statement_end_offset = *ending_offset*</span><span class="sxs-lookup"><span data-stu-id="421ec-155">AND qs.statement_end_offset = *ending_offset*</span></span>  
  
     <span data-ttu-id="421ec-156">AND qs.plan_handle = *plan_handle*;</span><span class="sxs-lookup"><span data-stu-id="421ec-156">AND qs.plan_handle = *plan_handle*;</span></span>  
  
2.  <span data-ttu-id="421ec-157">根据原因代码说明，修改相应语句、批处理或过程以避免重新编译。</span><span class="sxs-lookup"><span data-stu-id="421ec-157">Based on the reason code description, modify the statement, batch, or procedure to avoid recompilations.</span></span> <span data-ttu-id="421ec-158">例如，某一存储过程可能包含一个或多个 SET 语句。</span><span class="sxs-lookup"><span data-stu-id="421ec-158">For example, a stored procedure may contain one or more SET statements.</span></span> <span data-ttu-id="421ec-159">应从此过程中删除这些语句。</span><span class="sxs-lookup"><span data-stu-id="421ec-159">These statements should be removed from the procedure.</span></span> <span data-ttu-id="421ec-160">有关重新编译原因和解决方法的其他示例，请参阅 [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10))（SQL Server 2005 中的批编译、重新编译和计划缓存问题）。</span><span class="sxs-lookup"><span data-stu-id="421ec-160">For additional examples of recompilation causes and resolutions, see [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10)).</span></span>  
  
3.  <span data-ttu-id="421ec-161">如果问题仍然存在，请与 Microsoft 客户支持服务部门联系。</span><span class="sxs-lookup"><span data-stu-id="421ec-161">If the problem persists, contact Microsoft Customer Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="421ec-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="421ec-162">See Also</span></span>  
 [<span data-ttu-id="421ec-163">SQL:StmtRecompile 事件类</span><span class="sxs-lookup"><span data-stu-id="421ec-163">SQL:StmtRecompile Event Class</span></span>](../event-classes/sql-stmtrecompile-event-class.md)  
  
  
