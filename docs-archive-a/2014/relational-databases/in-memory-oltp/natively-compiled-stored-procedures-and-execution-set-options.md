---
title: 本机编译存储过程和执行的 Set 选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 264a2b3ab1e6f3f0bda97bfe89a4438aa641577d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693873"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a><span data-ttu-id="b06b1-102">本机编译存储过程和执行的 Set 选项</span><span class="sxs-lookup"><span data-stu-id="b06b1-102">Natively Compiled Stored Procedures and Execution Set Options</span></span>
  <span data-ttu-id="b06b1-103">会话选项在原子块中是固定的。</span><span class="sxs-lookup"><span data-stu-id="b06b1-103">Session options are fixed in atomic blocks.</span></span> <span data-ttu-id="b06b1-104">存储过程的执行不会受到会话的 SET 选项的影响。</span><span class="sxs-lookup"><span data-stu-id="b06b1-104">A stored procedure's execution is not affected by a session's SET options.</span></span> <span data-ttu-id="b06b1-105">但是，某些 SET 选项（例如 SET NOEXEC 和 SET SHOWPLAN_XML）会导致存储过程（包括本机编译存储过程）不执行。</span><span class="sxs-lookup"><span data-stu-id="b06b1-105">However, certain SET options, such as SET NOEXEC and SET SHOWPLAN_XML, cause stored procedures (including natively compiled stored procedures) to not execute.</span></span>  
  
 <span data-ttu-id="b06b1-106">在任意 STATISTICS 选项开启的情况下执行本机编译的存储过程时，系统将该过程作为整体（而非针对每条语句）收集统计数据。</span><span class="sxs-lookup"><span data-stu-id="b06b1-106">When a natively compiled stored procedure is executed with any STATISTICS option turned on, statistics are gathered for the procedure as a whole and not per statement.</span></span> <span data-ttu-id="b06b1-107">有关详细信息，请参阅 [SET STATISTICS IO (Transact-SQL)](/sql/t-sql/statements/set-statistics-io-transact-sql)、[SET STATISTICS PROFILE (Transact-SQL)](/sql/t-sql/statements/set-statistics-profile-transact-sql)、[SET STATISTICS TIME (Transact-SQL)](/sql/t-sql/statements/set-statistics-time-transact-sql) 和 [SET STATISTICS XML (Transact-SQL)](/sql/t-sql/statements/set-statistics-xml-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b06b1-107">For more information, see [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql), and [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql).</span></span> <span data-ttu-id="b06b1-108">若要在本机编译的存储过程中获取针对每条语句的执行统计信息，请使用 sp_statement_completed 事件上的扩展事件会话，该会话将会在某一存储过程执行中的每个单独查询完成时启动。</span><span class="sxs-lookup"><span data-stu-id="b06b1-108">To obtain execution statistics on a per-statement level in natively compiled stored procedures, use an Extended Event session on the sp_statement_completed event, which starts when each individual query in a stored procedures execution completes.</span></span> <span data-ttu-id="b06b1-109">有关创建扩展事件会话的详细信息，请参阅 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b06b1-109">For more information on creating Extended Event sessions, see [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).</span></span>  
  
 <span data-ttu-id="b06b1-110">本机编译存储过程支持 `SHOWPLAN_XML`。</span><span class="sxs-lookup"><span data-stu-id="b06b1-110">`SHOWPLAN_XML` is supported for natively compiled stored procedures.</span></span> <span data-ttu-id="b06b1-111">本机编译的存储过程不支持 `SHOWPLAN_ALL` 和 `SHOWPLAN_TEXT`。</span><span class="sxs-lookup"><span data-stu-id="b06b1-111">`SHOWPLAN_ALL` and `SHOWPLAN_TEXT` are not supported with natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="b06b1-112">本机编译的存储过程不支持 `SET FMTONLY`。</span><span class="sxs-lookup"><span data-stu-id="b06b1-112">`SET FMTONLY` in not supported with natively compiled stored procedures.</span></span> <span data-ttu-id="b06b1-113">请改为使用 [sp_describe_first_result_set (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b06b1-113">Use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06b1-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b06b1-114">See Also</span></span>  
 [<span data-ttu-id="b06b1-115">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="b06b1-115">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
