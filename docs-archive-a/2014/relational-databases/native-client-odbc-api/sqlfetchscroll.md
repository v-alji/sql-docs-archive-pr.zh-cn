---
title: SQLFetchScroll |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: rothja
ms.author: jroth
ms.openlocfilehash: eecf9714a97577ff490b642cee5b9c380333e40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580271"
---
# <a name="sqlfetchscroll"></a><span data-ttu-id="5f99b-102">SQLFetchScroll</span><span class="sxs-lookup"><span data-stu-id="5f99b-102">SQLFetchScroll</span></span>
  <span data-ttu-id="5f99b-103">**SQLFetchScroll**将向应用程序返回一行数据。</span><span class="sxs-lookup"><span data-stu-id="5f99b-103">**SQLFetchScroll** returns one row set of data to the application.</span></span> <span data-ttu-id="5f99b-104">使用[SQLSetStmtAttr](sqlsetstmtattr.md)设置行集的大小。</span><span class="sxs-lookup"><span data-stu-id="5f99b-104">The size of the row set is set using [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span> <span data-ttu-id="5f99b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序支持所有定义的提取说明 (例如 SQL_FETCH_RELATIVE) ，但具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="5f99b-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports all defined fetch instructions (for example, SQL_FETCH_RELATIVE) with the following limitations:</span></span>  
  
-   <span data-ttu-id="5f99b-106">如果为语句定义了只进游标，则必须使用 SQL_FETCH_NEXT，尝试以任何其他方式执行提取都将导致返回错误。</span><span class="sxs-lookup"><span data-stu-id="5f99b-106">If a forward-only cursor is defined for the statement, SQL_FETCH_NEXT is required and attempts to fetch in any other fashion will result in an error return.</span></span>  
  
-   <span data-ttu-id="5f99b-107">仅静态和键集驱动游标支持 SQL_FETCH_BOOKMARK。</span><span class="sxs-lookup"><span data-stu-id="5f99b-107">SQL_FETCH_BOOKMARK is supported for static and keyset-driven cursors only.</span></span>  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="5f99b-108">SQLFetchScroll 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="5f99b-108">SQLFetchScroll Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="5f99b-109">日期/时间类型的结果列值按[从 SQL 到 C 的转换](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)中所述进行转换。</span><span class="sxs-lookup"><span data-stu-id="5f99b-109">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="5f99b-110">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="5f99b-110">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a><span data-ttu-id="5f99b-111">SQLFetchScroll 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="5f99b-111">SQLFetchScroll Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="5f99b-112">**SQLFetchScroll**支持 (udt) 的大型 CLR 用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="5f99b-112">**SQLFetchScroll** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="5f99b-113">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="5f99b-113">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f99b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f99b-114">See Also</span></span>  
 <span data-ttu-id="5f99b-115">[SQLFetchScroll 函数](https://go.microsoft.com/fwlink/?LinkId=59343) </span><span class="sxs-lookup"><span data-stu-id="5f99b-115">[SQLFetchScroll Function](https://go.microsoft.com/fwlink/?LinkId=59343) </span></span>  
 [<span data-ttu-id="5f99b-116">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="5f99b-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
