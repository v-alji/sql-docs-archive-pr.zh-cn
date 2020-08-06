---
title: 直接 (ODBC) 执行语句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: rothja
ms.author: jroth
ms.openlocfilehash: 2aeada906a925cff93455ffd92e7c17822a80124
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576714"
---
# <a name="execute-a-statement-directly-odbc"></a><span data-ttu-id="0245c-102">直接执行语句 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="0245c-102">Execute a Statement Directly (ODBC)</span></span>
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a><span data-ttu-id="0245c-103">直接执行语句并且只执行一次</span><span class="sxs-lookup"><span data-stu-id="0245c-103">To execute a statement directly and one time only</span></span>  
  
1.  <span data-ttu-id="0245c-104">如果语句具有参数标记，请使用[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)将每个参数绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="0245c-104">If the statement has parameter markers, use [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind each parameter to a program variable.</span></span> <span data-ttu-id="0245c-105">使用数据值填充程序变量，然后设置任何执行时数据参数。</span><span class="sxs-lookup"><span data-stu-id="0245c-105">Fill the program variables with data values, and then set up any data-at-execution parameters.</span></span>  
  
2.  <span data-ttu-id="0245c-106">调用[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)以执行该语句。</span><span class="sxs-lookup"><span data-stu-id="0245c-106">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span>  
  
3.  <span data-ttu-id="0245c-107">如果使用执行时数据输入参数，则[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)将返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="0245c-107">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="0245c-108">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以区块形式发送数据。</span><span class="sxs-lookup"><span data-stu-id="0245c-108">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a><span data-ttu-id="0245c-109">通过使用按列参数绑定多次执行语句</span><span class="sxs-lookup"><span data-stu-id="0245c-109">To execute a statement multiple times by using column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="0245c-110">调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="0245c-110">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="0245c-111">将 SQL_ATTR_PARAMSET_SIZE 设置为参数集 (S) 的数目。</span><span class="sxs-lookup"><span data-stu-id="0245c-111">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="0245c-112">将 SQL_ATTR_PARAM_BIND_TYPE 设置为 SQL_PARAMETER_BIND_BY_COLUMN。</span><span class="sxs-lookup"><span data-stu-id="0245c-112">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
     <span data-ttu-id="0245c-113">将 SQL_ATTR_PARAMS_PROCESSED_PTR 属性设置为指向 SQLUINTEGER 变量，以包含所处理的参数个数。</span><span class="sxs-lookup"><span data-stu-id="0245c-113">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="0245c-114">将 SQL_ATTR_PARAMS_STATUS_PTR 设置为指向 SQLUSSMALLINT 变量的数组 [S]，以包含参数状态指示器。</span><span class="sxs-lookup"><span data-stu-id="0245c-114">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="0245c-115">对于每个参数标记：</span><span class="sxs-lookup"><span data-stu-id="0245c-115">For each parameter marker:</span></span>  
  
     <span data-ttu-id="0245c-116">分配 S 参数缓冲区的数组以存储数据值。</span><span class="sxs-lookup"><span data-stu-id="0245c-116">Allocate an array of S parameter buffers to store data values.</span></span>  
  
     <span data-ttu-id="0245c-117">分配 S 参数缓冲区的数组以存储数据长度。</span><span class="sxs-lookup"><span data-stu-id="0245c-117">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
     <span data-ttu-id="0245c-118">调用[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) ，将参数数据值和数据长度数组绑定到语句参数。</span><span class="sxs-lookup"><span data-stu-id="0245c-118">Call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
     <span data-ttu-id="0245c-119">设置任意执行时数据 text 或 image 参数。</span><span class="sxs-lookup"><span data-stu-id="0245c-119">Set up any data-at-execution text or image parameters.</span></span>  
  
     <span data-ttu-id="0245c-120">将 S 数据值和 S 数据长度放到绑定参数数组中。</span><span class="sxs-lookup"><span data-stu-id="0245c-120">Put S data values and S data lengths into the bound parameter arrays.</span></span>  
  
3.  <span data-ttu-id="0245c-121">调用[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)以执行该语句。</span><span class="sxs-lookup"><span data-stu-id="0245c-121">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="0245c-122">驱动程序将有效地执行该语句 S 次，每组参数一次。</span><span class="sxs-lookup"><span data-stu-id="0245c-122">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
4.  <span data-ttu-id="0245c-123">如果使用执行时数据输入参数，则[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)将返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="0245c-123">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="0245c-124">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以区块形式发送数据。</span><span class="sxs-lookup"><span data-stu-id="0245c-124">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a><span data-ttu-id="0245c-125">通过使用按行参数绑定多次执行语句</span><span class="sxs-lookup"><span data-stu-id="0245c-125">To execute a statement multiple times by using row-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="0245c-126">分配结构数组 [S]，其中，S 是参数的集合数。</span><span class="sxs-lookup"><span data-stu-id="0245c-126">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="0245c-127">该结构对于每个参数有一个元素，并且每个元素有两部分：</span><span class="sxs-lookup"><span data-stu-id="0245c-127">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
     <span data-ttu-id="0245c-128">第一部分是合适的数据类型的变量，以包含参数数据。</span><span class="sxs-lookup"><span data-stu-id="0245c-128">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
     <span data-ttu-id="0245c-129">第二部分是 SQLINTEGER 变量，以包含状态指示器。</span><span class="sxs-lookup"><span data-stu-id="0245c-129">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="0245c-130">调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="0245c-130">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="0245c-131">将 SQL_ATTR_PARAMSET_SIZE 设置为参数集 (S) 的数目。</span><span class="sxs-lookup"><span data-stu-id="0245c-131">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="0245c-132">将 SQL_ATTR_PARAM_BIND_TYPE 设置为在步骤 1 中分配的结构的大小。</span><span class="sxs-lookup"><span data-stu-id="0245c-132">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
     <span data-ttu-id="0245c-133">将 SQL_ATTR_PARAMS_PROCESSED_PTR 属性设置为指向 SQLUINTEGER 变量，以包含所处理的参数个数。</span><span class="sxs-lookup"><span data-stu-id="0245c-133">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="0245c-134">将 SQL_ATTR_PARAMS_STATUS_PTR 设置为指向 SQLUSSMALLINT 变量的数组 [S]，以包含参数状态指示器。</span><span class="sxs-lookup"><span data-stu-id="0245c-134">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="0245c-135">对于每个参数标记，调用[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) ，将参数的数据值和数据长度指针指向其在步骤1中分配的结构数组的第一个元素中的变量。</span><span class="sxs-lookup"><span data-stu-id="0245c-135">For each parameter marker, call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to point the parameter's data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="0245c-136">如果参数是执行时数据参数，则设置它。</span><span class="sxs-lookup"><span data-stu-id="0245c-136">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
4.  <span data-ttu-id="0245c-137">用数据值填充绑定参数缓冲区数组。</span><span class="sxs-lookup"><span data-stu-id="0245c-137">Fill the bound parameter buffer array with data values.</span></span>  
  
5.  <span data-ttu-id="0245c-138">调用[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)以执行该语句。</span><span class="sxs-lookup"><span data-stu-id="0245c-138">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="0245c-139">驱动程序将有效地执行该语句 S 次，每组参数一次。</span><span class="sxs-lookup"><span data-stu-id="0245c-139">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
6.  <span data-ttu-id="0245c-140">如果使用执行时数据输入参数，则[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)将返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="0245c-140">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="0245c-141">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以区块形式发送数据。</span><span class="sxs-lookup"><span data-stu-id="0245c-141">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
 <span data-ttu-id="0245c-142">**注意**与[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)和[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)相比，与[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)一起使用时，对列和按行绑定更常见。</span><span class="sxs-lookup"><span data-stu-id="0245c-142">**Note** Column-wise and row-wise binding are more typically used in conjunction with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) and [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) than with [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0245c-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0245c-143">See Also</span></span>  
 [<span data-ttu-id="0245c-144">&#40;ODBC&#41;执行查询操作指南主题</span><span class="sxs-lookup"><span data-stu-id="0245c-144">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
