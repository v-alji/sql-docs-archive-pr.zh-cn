---
title: 使用游标 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
author: rothja
ms.author: jroth
ms.openlocfilehash: e08156b03407c7a05d86278c11482a568d651f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576721"
---
# <a name="use-cursors-odbc"></a><span data-ttu-id="9350b-102">使用游标 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="9350b-102">Use Cursors (ODBC)</span></span>
    
### <a name="to-use-cursors"></a><span data-ttu-id="9350b-103">使用游标</span><span class="sxs-lookup"><span data-stu-id="9350b-103">To use cursors</span></span>  
  
1.  <span data-ttu-id="9350b-104">调用 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 以设置所需的游标属性：</span><span class="sxs-lookup"><span data-stu-id="9350b-104">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the desired cursor attributes:</span></span>  
  
     <span data-ttu-id="9350b-105">设置 SQL_ATTR_CURSOR_TYPE 和 SQL_ATTR_CONCURRENCY 属性（这是首选选项）。</span><span class="sxs-lookup"><span data-stu-id="9350b-105">Set the SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY attributes (this is the preferred option).</span></span>  
  
     <span data-ttu-id="9350b-106">或</span><span class="sxs-lookup"><span data-stu-id="9350b-106">Or</span></span>  
  
     <span data-ttu-id="9350b-107">设置 SQL_CURSOR_SCROLLABLE 和 SQL_CURSOR_SENSITIVITY 属性。</span><span class="sxs-lookup"><span data-stu-id="9350b-107">Set the SQL_CURSOR_SCROLLABLE and SQL_CURSOR_SENSITIVITY attributes.</span></span>  
  
2.  <span data-ttu-id="9350b-108">调用 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 以便通过使用 SQL_ATTR_ROW_ARRAY_SIZE 属性设置行集大小。</span><span class="sxs-lookup"><span data-stu-id="9350b-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the rowset size by using the SQL_ATTR_ROW_ARRAY_SIZE attribute.</span></span>  
  
3.  <span data-ttu-id="9350b-109">或者，如果将通过使用 WHERE CURRENT OF 子句完成定位更新，则调用 [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) 以便设置游标名称。</span><span class="sxs-lookup"><span data-stu-id="9350b-109">Optionally, call [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) to set a cursor name if positioned updates will be done by using the WHERE CURRENT OF clause.</span></span>  
  
4.  <span data-ttu-id="9350b-110">执行 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="9350b-110">Execute the SQL statement.</span></span>  
  
5.  <span data-ttu-id="9350b-111">或者，如果将通过使用 WHERE CURRENT OF 子句完成定位更新并且游标名称没有在第 3 步中随 [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) 提供，则调用 [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) 以获取游标名称。</span><span class="sxs-lookup"><span data-stu-id="9350b-111">Optionally, call [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) to get the cursor name if positioned updates will be done by using the WHERE CURRENT OF clause and a cursor name was not supplied with [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) in Step 3.</span></span>  
  
6.  <span data-ttu-id="9350b-112">调用 [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) 以获取行集中的列数 (C)。</span><span class="sxs-lookup"><span data-stu-id="9350b-112">Call [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns (C) in the rowset.</span></span>  
  
     <span data-ttu-id="9350b-113">使用按列绑定。</span><span class="sxs-lookup"><span data-stu-id="9350b-113">Use column-wise binding.</span></span>  
  
     <span data-ttu-id="9350b-114">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="9350b-114">\- or -</span></span>  
  
     <span data-ttu-id="9350b-115">使用按行绑定。</span><span class="sxs-lookup"><span data-stu-id="9350b-115">Use row-wise binding.</span></span>  
  
7.  <span data-ttu-id="9350b-116">根据需要从游标提取行集。</span><span class="sxs-lookup"><span data-stu-id="9350b-116">Fetch rowsets from the cursor as desired.</span></span>  
  
8.  <span data-ttu-id="9350b-117">调用 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 以确定其他结果集是否可用。</span><span class="sxs-lookup"><span data-stu-id="9350b-117">Call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="9350b-118">如果返回 SQL_SUCCESS，则其他结果集可用。</span><span class="sxs-lookup"><span data-stu-id="9350b-118">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="9350b-119">如果返回 SQL_NO_DATA，则没有其他结果集可用。</span><span class="sxs-lookup"><span data-stu-id="9350b-119">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="9350b-120">如果返回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，则调用 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) 以确定来自 PRINT 或 RAISERROR 语句的输出是否可用。</span><span class="sxs-lookup"><span data-stu-id="9350b-120">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
     <span data-ttu-id="9350b-121">如果将绑定语句参数用于某一存储过程的输出参数或返回值，则使用在绑定参数缓冲区中当前提供的数据。</span><span class="sxs-lookup"><span data-stu-id="9350b-121">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span>  
  
     <span data-ttu-id="9350b-122">在使用绑定参数时，对 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 或 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 的每个调用都将执行 SQL 语句 S 次，其中，S 是绑定参数数组中元素的数目。</span><span class="sxs-lookup"><span data-stu-id="9350b-122">When bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement S times, where S is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="9350b-123">这意味着，将存在 S 组要处理的结果，而其中每组结果都由所有结果集、输出参数以及 SQL 语句的单次执行通常返回的返回代码构成。</span><span class="sxs-lookup"><span data-stu-id="9350b-123">This means that there will be S sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
     <span data-ttu-id="9350b-124">请注意，在某一结果集包含计算行时，每个计算行都可作为单独的结果集生成。</span><span class="sxs-lookup"><span data-stu-id="9350b-124">Note that when a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="9350b-125">这些计算结果集混杂在普通行内，并且将普通行分为多个结果集。</span><span class="sxs-lookup"><span data-stu-id="9350b-125">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
9. <span data-ttu-id="9350b-126">或者，使用 SQL_UNBIND 调用 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) 以释放任何绑定列缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9350b-126">Optionally, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
10. <span data-ttu-id="9350b-127">如果其他结果集可用，则转到步骤 6。</span><span class="sxs-lookup"><span data-stu-id="9350b-127">If another result set is available, go to Step 6.</span></span>  
  
     <span data-ttu-id="9350b-128">在步骤 9 中，对部分处理的结果集调用 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 将清除其余的结果集。</span><span class="sxs-lookup"><span data-stu-id="9350b-128">In Step 9, calling [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) on a partially processed result set clears the remainder of the result set.</span></span> <span data-ttu-id="9350b-129">清除部分处理的结果集的另一个方法是调用 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)。</span><span class="sxs-lookup"><span data-stu-id="9350b-129">Another way to clear a partially processed result set is to call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
     <span data-ttu-id="9350b-130">通过设置 SQL_ATTR_CURSOR_TYPE 和 SQL_ATTR_CONCURRENCY，或通过设置 SQL_ATTR_CURSOR_SENSITIVITY 和 SQL_ATTR_CURSOR_SCROLLABLE，可以控制所使用的游标类型。</span><span class="sxs-lookup"><span data-stu-id="9350b-130">You can control the type of cursor used by setting either SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY, or by setting SQL_ATTR_CURSOR_SENSITIVITY and SQL_ATTR_CURSOR_SCROLLABLE.</span></span> <span data-ttu-id="9350b-131">不应将指定游标行为的两种方法混用。</span><span class="sxs-lookup"><span data-stu-id="9350b-131">You should not mix the two methods of specifying cursor behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9350b-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9350b-132">See Also</span></span>  
 [<span data-ttu-id="9350b-133">使用游标操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="9350b-133">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](using-cursors-how-to-topics-odbc.md)  
  
  
