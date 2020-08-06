---
title: 释放语句句柄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d7a1e93d222e2b87058bc878f7eca85313b4108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577594"
---
# <a name="freeing-a-statement-handle"></a><span data-ttu-id="5ac2c-102">释放语句句柄</span><span class="sxs-lookup"><span data-stu-id="5ac2c-102">Freeing a Statement Handle</span></span>
  <span data-ttu-id="5ac2c-103">重用语句句柄比删除它们后再分配新句柄更高效。</span><span class="sxs-lookup"><span data-stu-id="5ac2c-103">It is more efficient to reuse statement handles than to drop them and allocate new ones.</span></span> <span data-ttu-id="5ac2c-104">对语句句柄执行新 SQL 语句之前，应用程序应当验证当前语句设置是否正确。</span><span class="sxs-lookup"><span data-stu-id="5ac2c-104">Before executing a new SQL statement on a statement handle, applications should verify that the current statement settings are appropriate.</span></span> <span data-ttu-id="5ac2c-105">这些设置包括语句属性、参数绑定和结果集绑定。</span><span class="sxs-lookup"><span data-stu-id="5ac2c-105">These include statement attributes, parameter bindings, and result set bindings.</span></span> <span data-ttu-id="5ac2c-106">通常，旧 SQL 语句的参数和结果集必须通过使用 SQL_RESET_PARAMS 和 SQL_UNBIND 选项调用[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)进行取消绑定，然后再为新的 sql 语句重新绑定。</span><span class="sxs-lookup"><span data-stu-id="5ac2c-106">Generally, parameters and result sets for the old SQL statement must be unbound by calling [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with the SQL_RESET_PARAMS and SQL_UNBIND options and then re-bound for the new SQL statement.</span></span>  
  
 <span data-ttu-id="5ac2c-107">当应用程序使用完该语句后，它将调用[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md)来释放该语句。</span><span class="sxs-lookup"><span data-stu-id="5ac2c-107">When the application has finished using the statement, it calls [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) to free the statement.</span></span> <span data-ttu-id="5ac2c-108">请注意， **SQLDisconnect**会自动释放连接上的所有语句。</span><span class="sxs-lookup"><span data-stu-id="5ac2c-108">Note that **SQLDisconnect** automatically frees all statements on a connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac2c-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ac2c-109">See Also</span></span>  
 [<span data-ttu-id="5ac2c-110">&#40;ODBC&#41;执行查询</span><span class="sxs-lookup"><span data-stu-id="5ac2c-110">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
