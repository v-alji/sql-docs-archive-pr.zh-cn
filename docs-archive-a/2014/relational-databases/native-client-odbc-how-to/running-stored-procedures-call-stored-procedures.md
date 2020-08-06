---
title: " (ODBC) 调用存储过程 |Microsoft Docs"
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: rothja
ms.author: jroth
ms.openlocfilehash: d98d623dbbb4701bb59c95df502d0063d528d0d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586635"
---
# <a name="call-stored-procedures-odbc"></a><span data-ttu-id="1c17b-102">调用存储过程 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="1c17b-102">Call Stored Procedures (ODBC)</span></span>
  <span data-ttu-id="1c17b-103">当 SQL 语句使用 ODBC CALL 转义子句调用存储过程时，Microsoft SQL Server 驱动程序使用远程存储过程调用 (RPC) 机制将该过程发送到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="1c17b-103">When a SQL statement calls a stored procedure using the ODBC CALL escape clause, the Microsoft SQL Server driver sends the procedure to SQL Server using the remote stored procedure call (RPC) mechanism.</span></span> <span data-ttu-id="1c17b-104">RPC 请求在 SQL Server 中跳过大多数语句分析和参数处理，因此，其速度快于使用 Transact-SQL EXECUTE 语句。</span><span class="sxs-lookup"><span data-stu-id="1c17b-104">RPC requests bypass much of the statement parsing and parameter processing in SQL Server and are faster than using the Transact-SQL EXECUTE statement.</span></span>  
  
 <span data-ttu-id="1c17b-105">有关演示此功能的示例应用程序，请参阅使用[ODBC&#41;&#40;处理返回代码和输出参数](running-stored-procedures-process-return-codes-and-output-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1c17b-105">For a sample application that demonstrates this feature, see [Process Return Codes and Output Parameters &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).</span></span>  
  
### <a name="to-run-a-procedure-as-an-rpc"></a><span data-ttu-id="1c17b-106">将过程作为 RPC 运行</span><span class="sxs-lookup"><span data-stu-id="1c17b-106">To run a procedure as an RPC</span></span>  
  
1.  <span data-ttu-id="1c17b-107">构造使用 ODBC CALL 转义序列的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="1c17b-107">Construct a SQL statement that uses the ODBC CALL escape sequence.</span></span> <span data-ttu-id="1c17b-108">该语句对每个输入、输入/输出和输出参数以及过程返回值（如果有）使用参数标记：</span><span class="sxs-lookup"><span data-stu-id="1c17b-108">The statement uses parameter markers for each input, input/output, and output parameter, and for the procedure return value (if any):</span></span>  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  <span data-ttu-id="1c17b-109">为每个输入、输入/输出和输出参数调用[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) ，并为过程返回值调用，如果有任何)  (。</span><span class="sxs-lookup"><span data-stu-id="1c17b-109">Call [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
3.  <span data-ttu-id="1c17b-110">用[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)执行语句。</span><span class="sxs-lookup"><span data-stu-id="1c17b-110">Execute the statement with [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c17b-111">如果应用程序使用 Transact-SQL EXECUTE 语法提交过程（这与 ODBC CALL 转义序列相反），SQL Server ODBC 驱动程序会将过程调用作为 SQL 语句（而非 RPC）传递给 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="1c17b-111">If an application submits a procedure using the Transact-SQL EXECUTE syntax (as opposed to the ODBC CALL escape sequence), the SQL Server ODBC driver passes the procedure call to SQL Server as a SQL statement rather than as an RPC.</span></span> <span data-ttu-id="1c17b-112">此外，如果未使用 Transact-SQL EXECUTE 语句，则不会返回输出参数。</span><span class="sxs-lookup"><span data-stu-id="1c17b-112">Also, output parameters are not returned if the Transact-SQL EXECUTE statement is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c17b-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c17b-113">See Also</span></span>  
 <span data-ttu-id="1c17b-114">[运行存储过程操作指南主题 &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="1c17b-114">[Running Stored Procedures How-to Topics &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md) </span></span>  
 <span data-ttu-id="1c17b-115">[批处理存储过程调用](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md) </span><span class="sxs-lookup"><span data-stu-id="1c17b-115">[Batching Stored Procedure Calls](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md) </span></span>  
 <span data-ttu-id="1c17b-116">[运行存储过程](../native-client-odbc-stored-procedures/running-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="1c17b-116">[Running Stored Procedures](../native-client-odbc-stored-procedures/running-stored-procedures.md) </span></span>  
 <span data-ttu-id="1c17b-117">[调用存储过程](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="1c17b-117">[Calling a Stored Procedure](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="1c17b-118">过程</span><span class="sxs-lookup"><span data-stu-id="1c17b-118">Procedures</span></span>](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
