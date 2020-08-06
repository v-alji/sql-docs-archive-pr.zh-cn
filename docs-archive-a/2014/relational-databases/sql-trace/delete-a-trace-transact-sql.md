---
title: 删除跟踪 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b3551cff36ef6e2c2e9cc6a4d9b7056ae44cb950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587304"
---
# <a name="delete-a-trace-transact-sql"></a><span data-ttu-id="ee799-102">删除跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ee799-102">Delete a Trace (Transact-SQL)</span></span>
  <span data-ttu-id="ee799-103">本主题说明如何使用存储过程删除跟踪。</span><span class="sxs-lookup"><span data-stu-id="ee799-103">This topic describes how to use stored procedures to delete a trace.</span></span>  
  
 <span data-ttu-id="ee799-104">有关使用跟踪存储过程的示例，请参阅[创建跟踪 (Transact-SQL)](create-a-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ee799-104">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md).</span></span>  
  
### <a name="to-delete-a-trace"></a><span data-ttu-id="ee799-105">删除跟踪</span><span class="sxs-lookup"><span data-stu-id="ee799-105">To delete a trace</span></span>  
  
1.  <span data-ttu-id="ee799-106">执行 **sp_trace_setstatus** 时通过指定 **@status = 0** 停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="ee799-106">Execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="ee799-107">执行 **sp_trace_setstatus** 时通过指定 **@status = 2** 关闭跟踪并从服务器删除其信息。</span><span class="sxs-lookup"><span data-stu-id="ee799-107">Execute **sp_trace_setstatus** by specifying **@status = 2** to close the trace and delete its information from the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee799-108">在关闭跟踪前首先必须先停止它。</span><span class="sxs-lookup"><span data-stu-id="ee799-108">A trace must be stopped first before it can be closed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee799-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee799-109">See Also</span></span>  
 <span data-ttu-id="ee799-110">[sp_trace_setstatus (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ee799-110">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="ee799-111">[系统存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ee799-111">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="ee799-112">SQL Server Profiler 存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ee799-112">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
