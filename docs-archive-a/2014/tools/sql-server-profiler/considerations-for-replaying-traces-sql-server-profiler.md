---
title: 重播跟踪的注意事项 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c2f030a0191596e40ef1ee9e2b0b2d4da34c773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682511"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a><span data-ttu-id="07fcd-102">重播跟踪的注意事项 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="07fcd-102">Considerations for Replaying Traces (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="07fcd-103">无法重播下列类型的跟踪：</span><span class="sxs-lookup"><span data-stu-id="07fcd-103">cannot replay the following kinds of traces:</span></span>  
  
-   <span data-ttu-id="07fcd-104">包含事务复制和其他事务日志活动的跟踪。</span><span class="sxs-lookup"><span data-stu-id="07fcd-104">Traces that contain transactional replication and other transaction log activity.</span></span> <span data-ttu-id="07fcd-105">将跳过这些事件。</span><span class="sxs-lookup"><span data-stu-id="07fcd-105">These events are skipped.</span></span> <span data-ttu-id="07fcd-106">其他类型的复制不标记事务日志，因此它们不会受到影响。</span><span class="sxs-lookup"><span data-stu-id="07fcd-106">Other types of replication do not mark the transaction log so they are not affected.</span></span>  
  
-   <span data-ttu-id="07fcd-107">包含涉及全局唯一标识符 (GUID) 的操作的跟踪。</span><span class="sxs-lookup"><span data-stu-id="07fcd-107">Traces that contain operations that involve globally unique identifiers (GUID).</span></span> <span data-ttu-id="07fcd-108">这些事件将被跳过。</span><span class="sxs-lookup"><span data-stu-id="07fcd-108">These events will be skipped.</span></span>  
  
-   <span data-ttu-id="07fcd-109">包含对 **text**、 **ntext**和 **image** 列的操作、涉及 **bcp** 实用工具、BULK INSERT、READTEXT、WRITETEXT 和 UPDATETEXT 语句以及全文操作的跟踪。</span><span class="sxs-lookup"><span data-stu-id="07fcd-109">Traces that contain operations on **text**, **ntext**, and **image** columns involving the **bcp** utility, the BULK INSERT, READTEXT, WRITETEXT, and UPDATETEXT statements, and full-text operations.</span></span> <span data-ttu-id="07fcd-110">将跳过这些事件。</span><span class="sxs-lookup"><span data-stu-id="07fcd-110">These events are skipped.</span></span>  
  
-   <span data-ttu-id="07fcd-111">包含会话绑定（ **sp_getbindtoken** 和 **sp_bindsession** 系统存储过程）的跟踪。</span><span class="sxs-lookup"><span data-stu-id="07fcd-111">Traces that contain session binding: **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span> <span data-ttu-id="07fcd-112">将跳过这些事件。</span><span class="sxs-lookup"><span data-stu-id="07fcd-112">These events are skipped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07fcd-113">如果不使用预先配置的重播模版 (**TSQL_Replay**)，也不捕获所有必需的数据，则 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 将不重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="07fcd-113">If you do not use the preconfigured replay template (**TSQL_Replay**), and do not capture all required data, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] does not replay the trace.</span></span> <span data-ttu-id="07fcd-114">有关详细信息，请参阅 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07fcd-114">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
 <span data-ttu-id="07fcd-115">有关重播跟踪需要哪些权限的信息，请参阅 [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="07fcd-115">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07fcd-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07fcd-116">See Also</span></span>  
 <span data-ttu-id="07fcd-117">[bcp 实用工具](../bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="07fcd-117">[bcp Utility](../bcp-utility.md) </span></span>  
 <span data-ttu-id="07fcd-118">[SQL Server 事件类参考](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="07fcd-118">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="07fcd-119">[sp_getbindtoken (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07fcd-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span></span>  
 <span data-ttu-id="07fcd-120">[sp_bindsession (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07fcd-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 <span data-ttu-id="07fcd-121">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07fcd-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="07fcd-122">[READTEXT (Transact-SQL)](/sql/t-sql/queries/readtext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07fcd-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span></span>  
 <span data-ttu-id="07fcd-123">[WRITETEXT (Transact-SQL)](/sql/t-sql/queries/writetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07fcd-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span></span>  
 [<span data-ttu-id="07fcd-124">UPDATETEXT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="07fcd-124">UPDATETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/updatetext-transact-sql)  
  
  
