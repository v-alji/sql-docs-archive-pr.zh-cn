---
title: " (ODBC) 准备和执行语句 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: rothja
ms.author: jroth
ms.openlocfilehash: 607d8ad1509eca1204f6d029842b04120d3f5d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692903"
---
# <a name="prepare-and-execute-a-statement-odbc"></a><span data-ttu-id="484ff-102">准备和执行语句 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="484ff-102">Prepare and Execute a Statement (ODBC)</span></span>
    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a><span data-ttu-id="484ff-103">准备一次语句，然后多次执行它</span><span class="sxs-lookup"><span data-stu-id="484ff-103">To prepare a statement once, and then execute it multiple times</span></span>  
  
1.  <span data-ttu-id="484ff-104">调用[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)可准备语句。</span><span class="sxs-lookup"><span data-stu-id="484ff-104">Call [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) to prepare the statement.</span></span>  
  
2.  <span data-ttu-id="484ff-105">也可以调用[SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)来确定预定义语句中的参数数量。</span><span class="sxs-lookup"><span data-stu-id="484ff-105">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
3.  <span data-ttu-id="484ff-106">（可选）对于预定义语句中的每个参数：</span><span class="sxs-lookup"><span data-stu-id="484ff-106">Optionally, for each parameter in the prepared statement:</span></span>  
  
    -   <span data-ttu-id="484ff-107">调用[SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)以获取参数信息。</span><span class="sxs-lookup"><span data-stu-id="484ff-107">Call [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to get parameter information.</span></span>  
  
    -   <span data-ttu-id="484ff-108">使用[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)将每个参数绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="484ff-108">Bind each parameter to a program variable by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="484ff-109">设置任何执行时数据参数。</span><span class="sxs-lookup"><span data-stu-id="484ff-109">Set up any data-at-execution parameters.</span></span>  
  
4.  <span data-ttu-id="484ff-110">对于每次执行预定义语句：</span><span class="sxs-lookup"><span data-stu-id="484ff-110">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="484ff-111">如果语句有参数标记，请将数据值放到绑定参数缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="484ff-111">If the statement has parameter markers, put the data values into the bound parameter buffer.</span></span>  
  
    -   <span data-ttu-id="484ff-112">调用[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)以执行预定义语句。</span><span class="sxs-lookup"><span data-stu-id="484ff-112">Call [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="484ff-113">如果使用执行时数据输入参数，则[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)将返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="484ff-113">If data-at-execution input parameters are used, [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="484ff-114">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以区块形式发送数据。</span><span class="sxs-lookup"><span data-stu-id="484ff-114">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a><span data-ttu-id="484ff-115">用按列参数绑定预定义语句</span><span class="sxs-lookup"><span data-stu-id="484ff-115">To prepare a statement with column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="484ff-116">调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="484ff-116">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="484ff-117">将 SQL_ATTR_PARAMSET_SIZE 设置为参数集 (S) 的数目。</span><span class="sxs-lookup"><span data-stu-id="484ff-117">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="484ff-118">将 SQL_ATTR_PARAM_BIND_TYPE 设置为 SQL_PARAMETER_BIND_BY_COLUMN。</span><span class="sxs-lookup"><span data-stu-id="484ff-118">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="484ff-119">将 SQL_ATTR_PARAMS_PROCESSED_PTR 属性设置为指向 SQLUINTEGER 变量，以包含所处理的参数个数。</span><span class="sxs-lookup"><span data-stu-id="484ff-119">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="484ff-120">将 SQL_ATTR_PARAMS_STATUS_PTR 设置为指向 SQLUSSMALLINT 变量的数组 array[S]，以包含参数状态指示器。</span><span class="sxs-lookup"><span data-stu-id="484ff-120">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="484ff-121">调用 SQLPrepare 以准备语句。</span><span class="sxs-lookup"><span data-stu-id="484ff-121">Call SQLPrepare to prepare the statement.</span></span>  
  
3.  <span data-ttu-id="484ff-122">也可以调用[SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)来确定预定义语句中的参数数量。</span><span class="sxs-lookup"><span data-stu-id="484ff-122">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
4.  <span data-ttu-id="484ff-123">（可选）对于预定义语句中的每个参数，调用 SQLDescribeParam 以获取参数信息。</span><span class="sxs-lookup"><span data-stu-id="484ff-123">Optionally, for each parameter in the prepared statement, call SQLDescribeParam to get parameter information.</span></span>  
  
5.  <span data-ttu-id="484ff-124">对于每个参数标记：</span><span class="sxs-lookup"><span data-stu-id="484ff-124">For each parameter marker:</span></span>  
  
    -   <span data-ttu-id="484ff-125">分配 S 参数缓冲区的数组以存储数据值。</span><span class="sxs-lookup"><span data-stu-id="484ff-125">Allocate an array of S parameter buffers to store data values.</span></span>  
  
    -   <span data-ttu-id="484ff-126">分配 S 参数缓冲区的数组以存储数据长度。</span><span class="sxs-lookup"><span data-stu-id="484ff-126">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="484ff-127">调用 SQLBindParameter，将参数数据值和数据长度数组绑定到语句参数。</span><span class="sxs-lookup"><span data-stu-id="484ff-127">Call SQLBindParameter to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
    -   <span data-ttu-id="484ff-128">如果参数是执行时数据文本或映像参数，则设置它。</span><span class="sxs-lookup"><span data-stu-id="484ff-128">If the parameter is a data-at-execution text or image parameter, set it up.</span></span>  
  
    -   <span data-ttu-id="484ff-129">如果使用任何执行时数据参数，则设置它们。</span><span class="sxs-lookup"><span data-stu-id="484ff-129">If any data-at-execution parameters are used, set them up.</span></span>  
  
6.  <span data-ttu-id="484ff-130">对于每次执行预定义语句：</span><span class="sxs-lookup"><span data-stu-id="484ff-130">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="484ff-131">将 S 个数据值和 S 个数据长度放到绑定参数数组中。</span><span class="sxs-lookup"><span data-stu-id="484ff-131">Put the S data values and S data lengths into the bound parameter arrays.</span></span>  
  
    -   <span data-ttu-id="484ff-132">调用 SQLExecute 以执行预定义语句。</span><span class="sxs-lookup"><span data-stu-id="484ff-132">Call SQLExecute to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="484ff-133">如果使用执行时数据输入参数，则 SQLExecute 返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="484ff-133">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="484ff-134">使用 SQLParamData 和 SQLPutData 以区块形式发送数据。</span><span class="sxs-lookup"><span data-stu-id="484ff-134">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a><span data-ttu-id="484ff-135">用按行绑定参数预定义语句</span><span class="sxs-lookup"><span data-stu-id="484ff-135">To prepare a statement with row-wise bound parameters</span></span>  
  
1.  <span data-ttu-id="484ff-136">分配结构数组 [S]，其中，S 是参数的集合数。</span><span class="sxs-lookup"><span data-stu-id="484ff-136">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="484ff-137">该结构对于每个参数有一个元素，并且每个元素有两部分：</span><span class="sxs-lookup"><span data-stu-id="484ff-137">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="484ff-138">第一部分是合适的数据类型的变量，以包含参数数据。</span><span class="sxs-lookup"><span data-stu-id="484ff-138">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
    -   <span data-ttu-id="484ff-139">第二部分是 SQLINTEGER 变量，以包含状态指示器。</span><span class="sxs-lookup"><span data-stu-id="484ff-139">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="484ff-140">调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="484ff-140">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="484ff-141">将 SQL_ATTR_PARAMSET_SIZE 设置为参数集 (S) 的数目。</span><span class="sxs-lookup"><span data-stu-id="484ff-141">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="484ff-142">将 SQL_ATTR_PARAM_BIND_TYPE 设置为在步骤 1 中分配的结构的大小。</span><span class="sxs-lookup"><span data-stu-id="484ff-142">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="484ff-143">将 SQL_ATTR_PARAMS_PROCESSED_PTR 属性设置为指向 SQLUINTEGER 变量，以包含所处理的参数个数。</span><span class="sxs-lookup"><span data-stu-id="484ff-143">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="484ff-144">将 SQL_ATTR_PARAMS_STATUS_PTR 设置为指向 SQLUSSMALLINT 变量的数组 array[S]，以包含参数状态指示器。</span><span class="sxs-lookup"><span data-stu-id="484ff-144">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="484ff-145">调用 SQLPrepare 以准备语句。</span><span class="sxs-lookup"><span data-stu-id="484ff-145">Call SQLPrepare to prepare the statement.</span></span>  
  
4.  <span data-ttu-id="484ff-146">对于每个参数标记，调用 SQLBindParameter，将参数数据值和数据长度指针指向其在步骤1中分配的结构数组的第一个元素中的变量。</span><span class="sxs-lookup"><span data-stu-id="484ff-146">For each parameter marker, call SQLBindParameter to point the parameter data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="484ff-147">如果参数是执行时数据参数，则设置它。</span><span class="sxs-lookup"><span data-stu-id="484ff-147">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
5.  <span data-ttu-id="484ff-148">对于每次执行预定义语句：</span><span class="sxs-lookup"><span data-stu-id="484ff-148">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="484ff-149">用数据值填充绑定参数缓冲区数组。</span><span class="sxs-lookup"><span data-stu-id="484ff-149">Fill the bound parameter buffer array with data values.</span></span>  
  
    -   <span data-ttu-id="484ff-150">调用 SQLExecute 以执行预定义语句。</span><span class="sxs-lookup"><span data-stu-id="484ff-150">Call SQLExecute to execute the prepared statement.</span></span> <span data-ttu-id="484ff-151">驱动程序将有效地执行 SQL 语句 S 次，每组参数一次。</span><span class="sxs-lookup"><span data-stu-id="484ff-151">The driver efficiently executes the SQL statement S times, once for each set of parameters.</span></span>  
  
    -   <span data-ttu-id="484ff-152">如果使用执行时数据输入参数，则 SQLExecute 返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="484ff-152">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="484ff-153">使用 SQLParamData 和 SQLPutData 以区块形式发送数据。</span><span class="sxs-lookup"><span data-stu-id="484ff-153">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="484ff-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="484ff-154">See Also</span></span>  
 [<span data-ttu-id="484ff-155">&#40;ODBC&#41;执行查询操作指南主题</span><span class="sxs-lookup"><span data-stu-id="484ff-155">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
