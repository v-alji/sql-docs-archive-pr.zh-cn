---
title: SQLFreeStmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: rothja
ms.author: jroth
ms.openlocfilehash: d38237b53ed994fd3272f9e129564320f88c6e37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580708"
---
# <a name="sqlfreestmt"></a><span data-ttu-id="a61ad-102">SQLFreeStmt</span><span class="sxs-lookup"><span data-stu-id="a61ad-102">SQLFreeStmt</span></span>
  <span data-ttu-id="a61ad-103">不建议在 ODBC 3.0 和更高版本中使用**SQLFreeStmt** 。</span><span class="sxs-lookup"><span data-stu-id="a61ad-103">**SQLFreeStmt** is not recommended in ODBC 3.0 and later.</span></span> <span data-ttu-id="a61ad-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序支持**SQLFreeStmt**的所有已定义的*选项*值。</span><span class="sxs-lookup"><span data-stu-id="a61ad-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports all defined *Option* values for **SQLFreeStmt**.</span></span> <span data-ttu-id="a61ad-105">但是， [SQLCloseCursor](sqlclosecursor.md)、 [SQLBindParameter](sqlbindparameter.md)、 [SQLBindCol](sqlbindcol.md)、 **SQLSetDescField**和[SQLFreeHandle](sqlfreehandle.md)将替换或复制**SQLFreeStmt**的功能，而应该改用。</span><span class="sxs-lookup"><span data-stu-id="a61ad-105">However, [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**, and [SQLFreeHandle](sqlfreehandle.md) replace or duplicate the function of **SQLFreeStmt** and should be used instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61ad-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a61ad-106">See Also</span></span>  
 <span data-ttu-id="a61ad-107">[SQLFreeStmt 函数](https://go.microsoft.com/fwlink/?LinkId=59346) </span><span class="sxs-lookup"><span data-stu-id="a61ad-107">[SQLFreeStmt Function](https://go.microsoft.com/fwlink/?LinkId=59346) </span></span>  
 [<span data-ttu-id="a61ad-108">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="a61ad-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
