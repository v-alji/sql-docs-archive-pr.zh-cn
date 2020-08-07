---
title: ODBC)  (游标并发 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: rothja
ms.author: jroth
ms.openlocfilehash: c47f24152978fedf8f2c3d49ec3b721969712814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589041"
---
# <a name="cursor-concurrency-odbc"></a><span data-ttu-id="de7a6-102">游标并发 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="de7a6-102">Cursor Concurrency (ODBC)</span></span>
  <span data-ttu-id="de7a6-103">和游标类型一样，游标操作也受应用程序设置的并发选项的影响。</span><span class="sxs-lookup"><span data-stu-id="de7a6-103">Cursor operations, like cursor types, are affected by the concurrency options set by the application.</span></span> <span data-ttu-id="de7a6-104">并发选项是使用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_CONCURRENCY 选项设置的。</span><span class="sxs-lookup"><span data-stu-id="de7a6-104">Concurrency options are set using the SQL_ATTR_CONCURRENCY option of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="de7a6-105">并发类型包括：</span><span class="sxs-lookup"><span data-stu-id="de7a6-105">The concurrency types are:</span></span>  
  
-   <span data-ttu-id="de7a6-106">只读 (SQL_CONCUR_READONLY)</span><span class="sxs-lookup"><span data-stu-id="de7a6-106">Read-only (SQL_CONCUR_READONLY)</span></span>  
  
-   <span data-ttu-id="de7a6-107">值 (SQL_CONCUR_VALUES)</span><span class="sxs-lookup"><span data-stu-id="de7a6-107">Values (SQL_CONCUR_VALUES)</span></span>  
  
-   <span data-ttu-id="de7a6-108">行版本 (SQL_CONCUR_ROWVER)</span><span class="sxs-lookup"><span data-stu-id="de7a6-108">Row version (SQL_CONCUR_ROWVER)</span></span>  
  
-   <span data-ttu-id="de7a6-109">锁 (SQL_CONCUR_LOCK)</span><span class="sxs-lookup"><span data-stu-id="de7a6-109">Lock (SQL_CONCUR_LOCK)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7a6-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de7a6-110">See Also</span></span>  
 [<span data-ttu-id="de7a6-111">游标属性</span><span class="sxs-lookup"><span data-stu-id="de7a6-111">Cursor Properties</span></span>](cursor-properties.md)  
  
  
