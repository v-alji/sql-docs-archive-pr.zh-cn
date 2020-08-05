---
title: 使用 SQL Server 默认结果集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 18cd10dd95329f68a42497d2bea5ce63f345ceff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580257"
---
# <a name="using-sql-server-default-result-sets"></a><span data-ttu-id="aa3a8-102">使用 SQL Server 默认结果集</span><span class="sxs-lookup"><span data-stu-id="aa3a8-102">Using SQL Server Default Result Sets</span></span>
  <span data-ttu-id="aa3a8-103">默认的 ODBC 游标属性包括：</span><span class="sxs-lookup"><span data-stu-id="aa3a8-103">The default ODBC cursor attributes are:</span></span>  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="aa3a8-104">当这些属性设置为默认值时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序将使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认结果集。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-104">Whenever these attributes are set to their defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set.</span></span> <span data-ttu-id="aa3a8-105">默认结果集可用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支持的任意 SQL 语句，并且是将整个结果集传输到客户端的最有效的方法。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-105">Default result sets can be used for any SQL statement supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and are the most efficient method of transferring an entire result set to the client.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]<span data-ttu-id="aa3a8-106">引入了对 (MARS) 的多个活动结果集的支持;应用程序现在可以为每个连接设置多个活动的默认结果集。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-106">introduced support for multiple active result sets (MARS); applications can now have more than one active default result set per connection.</span></span> <span data-ttu-id="aa3a8-107">默认情况下未启用 MARS。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-107">MARS is not enabled by default.</span></span>  
  
 <span data-ttu-id="aa3a8-108">在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 之前，默认结果集不支持同一连接上具有多个活动语句。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-108">Before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], default result sets did not support multiple active statements on the same connection.</span></span> <span data-ttu-id="aa3a8-109">对连接执行 SQL 语句后，服务器不接受来自该连接上的客户端的命令（取消结果集剩余内容的请求除外），直到结果集中的所有行均处理完毕。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-109">After an SQL statement is executed on a connection, the server does not accept commands (except a request to cancel the rest of the result set) from the client on that connection until all the rows in the result set have been processed.</span></span> <span data-ttu-id="aa3a8-110">若要取消部分处理的结果集的剩余部分，请调用[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)或[SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) ，并将*fOption*参数设置为 SQL_CLOSE。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-110">To cancel the remainder of a partially processed result set, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with the *fOption* parameter set to SQL_CLOSE.</span></span> <span data-ttu-id="aa3a8-111">若要完成部分处理的结果集并测试是否存在另一个结果集，请调用[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)。</span><span class="sxs-lookup"><span data-stu-id="aa3a8-111">To finish a partially processed result set and test for the presence of another result set, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md).</span></span> <span data-ttu-id="aa3a8-112">如果在完全处理默认结果集之前，ODBC 应用程序在连接句柄上尝试命令，则调用将生成 SQL_ERROR 并返回对**SQLGetDiagRec**的调用：</span><span class="sxs-lookup"><span data-stu-id="aa3a8-112">If an ODBC application attempts a command on a connection handle before a default result set has been completely processed, the call generates SQL_ERROR and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa3a8-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa3a8-113">See Also</span></span>  
 [<span data-ttu-id="aa3a8-114">如何实现游标</span><span class="sxs-lookup"><span data-stu-id="aa3a8-114">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  
