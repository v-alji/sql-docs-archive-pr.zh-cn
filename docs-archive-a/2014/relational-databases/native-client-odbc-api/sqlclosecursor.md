---
title: SQLCloseCursor |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: rothja
ms.author: jroth
ms.openlocfilehash: 770a67432868516e5023d1cf0ff819501b4c130e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693849"
---
# <a name="sqlclosecursor"></a><span data-ttu-id="1f2f3-102">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="1f2f3-102">SQLCloseCursor</span></span>
  <span data-ttu-id="1f2f3-103">**SQLCloseCursor**使用*选项*值 SQL_CLOSE 来替换[SQLFreeStmt](sqlfreestmt.md) 。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-103">**SQLCloseCursor** replaces [SQLFreeStmt](sqlfreestmt.md) with an *Option* value of SQL_CLOSE.</span></span> <span data-ttu-id="1f2f3-104">收到**SQLCloseCursor**后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序将放弃挂起的结果集行。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-104">On receipt of **SQLCloseCursor**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver discards pending result set rows.</span></span> <span data-ttu-id="1f2f3-105">请注意，如果**SQLCloseCursor**不改变任何存在) ，语句的列和参数绑定 (。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-105">Note that the statement's column and parameter bindings (if any exist) are left unaltered by **SQLCloseCursor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2f3-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f2f3-106">See Also</span></span>  
 <span data-ttu-id="1f2f3-107">[SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331) </span><span class="sxs-lookup"><span data-stu-id="1f2f3-107">[SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331) </span></span>  
 [<span data-ttu-id="1f2f3-108">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="1f2f3-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
