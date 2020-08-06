---
title: 语句的批处理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: rothja
ms.author: jroth
ms.openlocfilehash: 4818b67766dafe851035041c8fd5137a0dfade73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577608"
---
# <a name="batches-of-statements"></a><span data-ttu-id="93657-102">语句的批处理</span><span class="sxs-lookup"><span data-stu-id="93657-102">Batches of Statements</span></span>
  <span data-ttu-id="93657-103">一批 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句包含两个或多个语句，这些语句由分号分隔 (; ) ，内置于传递到**SQLExecDirect**或[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)的单个字符串。</span><span class="sxs-lookup"><span data-stu-id="93657-103">A batch of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements contains two or more statements, separated by a semicolon (;), built into a single string passed to **SQLExecDirect** or [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span> <span data-ttu-id="93657-104">例如：</span><span class="sxs-lookup"><span data-stu-id="93657-104">For example:</span></span>  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 <span data-ttu-id="93657-105">批处理通常可减少网络流量，因而比单个提交语句效率更高。</span><span class="sxs-lookup"><span data-stu-id="93657-105">Batches can be more efficient than submitting statements separately because network traffic is often reduced.</span></span> <span data-ttu-id="93657-106">完成当前结果集后，使用[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)定位到下一个结果集。</span><span class="sxs-lookup"><span data-stu-id="93657-106">Use [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to get positioned on the next result set when finished with the current result set.</span></span>  
  
 <span data-ttu-id="93657-107">当 ODBC 游标属性设置为行集大小为 1 的只进只读游标的默认值时，始终可以使用批处理。</span><span class="sxs-lookup"><span data-stu-id="93657-107">Batches can always be used when the ODBC cursor attributes are set to the defaults of a forward-only, read-only cursor with a rowset size of 1.</span></span>  
  
 <span data-ttu-id="93657-108">如果在针对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用服务器游标时执行批处理，则服务器游标会隐式转换为默认结果集。</span><span class="sxs-lookup"><span data-stu-id="93657-108">If a batch is executed when using server cursors against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="93657-109">**SQLExecDirect**或**SQLExecute**返回 SQL_SUCCESS_WITH_INFO，对**SQLGetDiagRec**的调用返回：</span><span class="sxs-lookup"><span data-stu-id="93657-109">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a><span data-ttu-id="93657-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93657-110">See Also</span></span>  
 [<span data-ttu-id="93657-111">&#40;ODBC&#41;执行语句</span><span class="sxs-lookup"><span data-stu-id="93657-111">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
