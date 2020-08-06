---
title: SQLProcedures |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: rothja
ms.author: jroth
ms.openlocfilehash: e37f15841a36eb95c1e9263d137ba2734d622367
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590758"
---
# <a name="sqlprocedures"></a><span data-ttu-id="ac508-102">SQLProcedures</span><span class="sxs-lookup"><span data-stu-id="ac508-102">SQLProcedures</span></span>
  <span data-ttu-id="ac508-103">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储过程都返回值。</span><span class="sxs-lookup"><span data-stu-id="ac508-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return a value.</span></span> <span data-ttu-id="ac508-104">**SQLProcedures**报告结果集列 SQL_PT_FUNCTION PROCEDURE_TYPE。</span><span class="sxs-lookup"><span data-stu-id="ac508-104">**SQLProcedures** reports SQL_PT_FUNCTION for the result set column PROCEDURE_TYPE.</span></span>  
  
 <span data-ttu-id="ac508-105">**SQLProcedures**返回 SQL_SUCCESS *CatalogName、SchemaName*或*ProcName*参数是否存在值。</span><span class="sxs-lookup"><span data-stu-id="ac508-105">**SQLProcedures** returns SQL_SUCCESS whether or not values exist for *CatalogName, SchemaName,* or *ProcName* parameters.</span></span> <span data-ttu-id="ac508-106">当在这些参数中使用了无效值时， **SQLFetch**将返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="ac508-106">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="ac508-107">可以对静态服务器游标执行**SQLProcedures** 。</span><span class="sxs-lookup"><span data-stu-id="ac508-107">**SQLProcedures** can be executed on a static server cursor.</span></span> <span data-ttu-id="ac508-108">尝试对可更新的 (动态或键集) 游标执行**SQLProcedures**将返回 SQL_SUCCESS_WITH_INFO，指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="ac508-108">An attempt to execute **SQLProcedures** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO, indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="ac508-109">**SQLProcedures**返回有关其名称与*ProcName*匹配并且可以由当前用户执行的任何过程的信息，或者当前用户已被授予 VIEW DEFINITION 权限的任何过程的相关信息。</span><span class="sxs-lookup"><span data-stu-id="ac508-109">**SQLProcedures** returns information about any procedures whose names match *ProcName* and can be executed by the current user, or for which the current user has been granted VIEW DEFINITION permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac508-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac508-110">See Also</span></span>  
 <span data-ttu-id="ac508-111">[SQLProcedures 函数](https://go.microsoft.com/fwlink/?LinkId=59364) </span><span class="sxs-lookup"><span data-stu-id="ac508-111">[SQLProcedures Function](https://go.microsoft.com/fwlink/?LinkId=59364) </span></span>  
 [<span data-ttu-id="ac508-112">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="ac508-112">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
