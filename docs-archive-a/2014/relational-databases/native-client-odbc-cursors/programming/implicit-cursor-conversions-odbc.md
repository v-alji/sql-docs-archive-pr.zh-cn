---
title: ODBC)  (的隐式游标转换 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: rothja
ms.author: jroth
ms.openlocfilehash: ff8350c71a853e39ff1d35a1f3fba6e8e1944934
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589039"
---
# <a name="implicit-cursor-conversions-odbc"></a><span data-ttu-id="1b9de-102">隐式游标转换 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="1b9de-102">Implicit Cursor Conversions (ODBC)</span></span>
  <span data-ttu-id="1b9de-103">应用程序可以通过[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)请求游标类型，然后执行所请求类型的服务器游标不支持的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="1b9de-103">Applications can request a cursor type through [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) and then execute an SQL statement that is not supported by server cursors of the type requested.</span></span> <span data-ttu-id="1b9de-104">对**SQLExecute**或**SQLExecDirect**的调用将返回 SQL_SUCCESS_WITH_INFO 和**SQLGetDiagRec**返回：</span><span class="sxs-lookup"><span data-stu-id="1b9de-104">A call to **SQLExecute** or **SQLExecDirect** returns SQL_SUCCESS_WITH_INFO and **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 <span data-ttu-id="1b9de-105">应用程序可以通过调用**SQLGetStmtOption**设置为 SQL_CURSOR_TYPE 来确定目前正在使用的游标类型。</span><span class="sxs-lookup"><span data-stu-id="1b9de-105">The application can determine what type of cursor is now being used by calling **SQLGetStmtOption** set to SQL_CURSOR_TYPE.</span></span> <span data-ttu-id="1b9de-106">游标类型转换仅适用于一个语句。</span><span class="sxs-lookup"><span data-stu-id="1b9de-106">The cursor type conversion applies to only one statement.</span></span> <span data-ttu-id="1b9de-107">下一个**SQLExecDirect**或**SQLExecute**将使用原始语句游标设置完成。</span><span class="sxs-lookup"><span data-stu-id="1b9de-107">The next **SQLExecDirect** or **SQLExecute** will be done using the original statement cursor settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9de-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b9de-108">See Also</span></span>  
 [<span data-ttu-id="1b9de-109">ODBC&#41;的游标编程详细信息 &#40;</span><span class="sxs-lookup"><span data-stu-id="1b9de-109">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
