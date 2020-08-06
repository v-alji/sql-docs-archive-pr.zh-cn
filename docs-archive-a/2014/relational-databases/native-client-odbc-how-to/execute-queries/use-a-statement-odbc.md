---
title: 使用 (ODBC) 的语句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ff3bc8c545cc9b55f0da3bb31d68d1ecbb5b547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692904"
---
# <a name="use-a-statement-odbc"></a><span data-ttu-id="c6082-102">使用语句 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="c6082-102">Use a Statement (ODBC)</span></span>
    
### <a name="to-use-a-statement"></a><span data-ttu-id="c6082-103">使用语句</span><span class="sxs-lookup"><span data-stu-id="c6082-103">To use a statement</span></span>  
  
1.  <span data-ttu-id="c6082-104">调用 [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)，同时将 *HandleType* 设置为 SQL_HANDLE_STMT，以分配语句句柄。</span><span class="sxs-lookup"><span data-stu-id="c6082-104">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a *HandleType* of SQL_HANDLE_STMT to allocate a statement handle.</span></span>  
  
2.  <span data-ttu-id="c6082-105">（可选）调用 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 以设置语句选项，或调用 [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) 以获取语句属性。</span><span class="sxs-lookup"><span data-stu-id="c6082-105">Optionally, call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set statement options or [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) to get statement attributes.</span></span>  
  
     <span data-ttu-id="c6082-106">若要使用服务器游标，必须将游标属性设置为其默认值之外的值。</span><span class="sxs-lookup"><span data-stu-id="c6082-106">To use server cursors, you must set cursor attributes to values other than their defaults.</span></span>  
  
3.  <span data-ttu-id="c6082-107">（可选）如果要多次执行此语句，可以使用 [SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)准备要执行的语句。</span><span class="sxs-lookup"><span data-stu-id="c6082-107">Optionally, if the statement will be executed several times, prepare the statement for execution with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span>  
  
4.  <span data-ttu-id="c6082-108">（可选）如果语句具有绑定参数标记，通过使用 [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) 将参数标记绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="c6082-108">Optionally, if the statement has bound parameter markers, bind the parameter markers to program variables by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="c6082-109">如果是准备的语句，则可以调用 [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) 和 [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) 以查找参数的数目和特征。</span><span class="sxs-lookup"><span data-stu-id="c6082-109">If the statement was prepared, you can call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) and [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to find the number and characteristics of the parameters.</span></span>  
  
5.  <span data-ttu-id="c6082-110">使用 SQLExecDirect 直接执行语句。</span><span class="sxs-lookup"><span data-stu-id="c6082-110">Execute a statement directly by using SQLExecDirect.</span></span>  
  
     <span data-ttu-id="c6082-111">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="c6082-111">\- or -</span></span>  
  
     <span data-ttu-id="c6082-112">如果是准备的语句，则可以使用 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 多次执行该语句。</span><span class="sxs-lookup"><span data-stu-id="c6082-112">If the statement was prepared, execute it multiple times by using [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400).</span></span>  
  
     <span data-ttu-id="c6082-113">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="c6082-113">\- or -</span></span>  
  
     <span data-ttu-id="c6082-114">调用可返回结果的目录函数。</span><span class="sxs-lookup"><span data-stu-id="c6082-114">Call a catalog function, which returns results.</span></span>  
  
6.  <span data-ttu-id="c6082-115">采用以下方法处理结果：将结果集列绑定到程序变量、通过使用 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 将数据从结果集列移至程序变量，或是结合使用这两种方法。</span><span class="sxs-lookup"><span data-stu-id="c6082-115">Process the results by binding the result set columns to program variables, by moving data from the result set columns to program variables by using [SQLGetData](../../native-client-odbc-api/sqlgetdata.md), or a combination of the two methods.</span></span>  
  
     <span data-ttu-id="c6082-116">从语句的结果集中提取，每次提取一行。</span><span class="sxs-lookup"><span data-stu-id="c6082-116">Fetch through the result set of a statement one row at a time.</span></span>  
  
     <span data-ttu-id="c6082-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="c6082-117">\- or -</span></span>  
  
     <span data-ttu-id="c6082-118">通过使用块游标从结果集中提取，每次提取多个行。</span><span class="sxs-lookup"><span data-stu-id="c6082-118">Fetch through the result set several rows at a time by using a block cursor.</span></span>  
  
     <span data-ttu-id="c6082-119">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="c6082-119">\- or -</span></span>  
  
     <span data-ttu-id="c6082-120">调用 [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) 以确定 INSERT、UPDATE 或 DELETE 语句影响的行数。</span><span class="sxs-lookup"><span data-stu-id="c6082-120">Call [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) to determine the number of rows affected by an INSERT, UPDATE, or DELETE statement.</span></span>  
  
     <span data-ttu-id="c6082-121">如果 SQL 语句可以有多个结果集，在每个结果集的末尾调用 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 以查看是否还有更多待处理的结果集。</span><span class="sxs-lookup"><span data-stu-id="c6082-121">If the SQL statement can have multiple result sets, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) at the end of each result set to see if there are additional result sets to process.</span></span>  
  
7.  <span data-ttu-id="c6082-122">处理完结果后，可能需要执行以下操作，令语句句柄可用于执行新语句：</span><span class="sxs-lookup"><span data-stu-id="c6082-122">After results are processed, the following actions may be necessary to make the statement handle available to execute a new statement:</span></span>  
  
    -   <span data-ttu-id="c6082-123">如果未调用 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)，直到它返回 SQL_NO_DATA，则调用 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) 以关闭游标。</span><span class="sxs-lookup"><span data-stu-id="c6082-123">If you did not call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) until it returned SQL_NO_DATA, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) to close the cursor.</span></span>  
  
    -   <span data-ttu-id="c6082-124">如果将参数标记绑定到程序变量，则调用 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)（同时将 *Option* 设置为 SQL_RESET_PARAMS）以释放绑定参数。</span><span class="sxs-lookup"><span data-stu-id="c6082-124">If you bound parameter markers to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_RESET_PARAMS to free the bound parameters.</span></span>  
  
    -   <span data-ttu-id="c6082-125">如果将结果集列绑定到程序变量，则调用 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)（同时将 *Option* 设置为 SQL_UNBIND）以释放绑定列。</span><span class="sxs-lookup"><span data-stu-id="c6082-125">If you bound result set columns to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_UNBIND to free the bound columns.</span></span>  
  
    -   <span data-ttu-id="c6082-126">若要重用语句句柄，请转至步骤 2。</span><span class="sxs-lookup"><span data-stu-id="c6082-126">To reuse the statement handle, go to Step 2.</span></span>  
  
8.  <span data-ttu-id="c6082-127">调用 [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md)，同时将 *HandleType* 设置为 SQL_HANDLE_STMT，以释放语句句柄。</span><span class="sxs-lookup"><span data-stu-id="c6082-127">Call [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) with a *HandleType* of SQL_HANDLE_STMT to free the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6082-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6082-128">See Also</span></span>  
 [<span data-ttu-id="c6082-129">&#40;ODBC&#41;执行查询操作指南主题</span><span class="sxs-lookup"><span data-stu-id="c6082-129">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
