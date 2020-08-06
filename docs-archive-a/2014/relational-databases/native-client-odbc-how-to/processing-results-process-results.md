---
title: ODBC)  (处理结果 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a22e9d7280f88de7799c31d2d0611e5299043d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692377"
---
# <a name="process-results-odbc"></a><span data-ttu-id="e55ce-102">处理结果 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="e55ce-102">Process Results (ODBC)</span></span>
    
### <a name="to-process-results"></a><span data-ttu-id="e55ce-103">处理结果</span><span class="sxs-lookup"><span data-stu-id="e55ce-103">To process results</span></span>  
  
1.  <span data-ttu-id="e55ce-104">检索结果集信息。</span><span class="sxs-lookup"><span data-stu-id="e55ce-104">Retrieve result set information.</span></span>  
  
2.  <span data-ttu-id="e55ce-105">如果使用了绑定列，则对每个要绑定的列，调用 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)，以将程序缓冲区绑定到该列。</span><span class="sxs-lookup"><span data-stu-id="e55ce-105">If bound columns are used, for each column you want to bind to, call [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) to bind a program buffer to the column.</span></span>  
  
3.  <span data-ttu-id="e55ce-106">对于结果集中的每一行：</span><span class="sxs-lookup"><span data-stu-id="e55ce-106">For each row in the result set:</span></span>  
  
    -   <span data-ttu-id="e55ce-107">调用 [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 以获取下一行。</span><span class="sxs-lookup"><span data-stu-id="e55ce-107">Call [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) to get the next row.</span></span>  
  
    -   <span data-ttu-id="e55ce-108">如果使用绑定列，则在绑定列缓冲区使用现在可用的数据。</span><span class="sxs-lookup"><span data-stu-id="e55ce-108">If bound columns are used, use the data now available in the bound column buffers.</span></span>  
  
    -   <span data-ttu-id="e55ce-109">如果使用绑定列，在最后一个绑定列后一次或多次调用 [SQLGetData](../native-client-odbc-api/sqlgetdata.md) 以获取未绑定列的数据。</span><span class="sxs-lookup"><span data-stu-id="e55ce-109">If unbound columns are used, call [SQLGetData](../native-client-odbc-api/sqlgetdata.md) one or more times to get the data for unbound columns after the last bound column.</span></span> <span data-ttu-id="e55ce-110">对 `SQLGetData` 的调用应按列号递增顺序排列。</span><span class="sxs-lookup"><span data-stu-id="e55ce-110">Calls to `SQLGetData` should be in increasing order of column number.</span></span>  
  
    -   <span data-ttu-id="e55ce-111">多次调用 `SQLGetData` 以从 text 或 image 列获取数据。</span><span class="sxs-lookup"><span data-stu-id="e55ce-111">Call `SQLGetData` multiple times to get data from a text or image column.</span></span>  
  
4.  <span data-ttu-id="e55ce-112">当 [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 通过返回 SQL_NO_DATA 指示到达结果集末尾时，调用 [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) 确定是否有其他可用结果集。</span><span class="sxs-lookup"><span data-stu-id="e55ce-112">When [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) signals the end of the result set by returning SQL_NO_DATA, call [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="e55ce-113">如果返回 SQL_SUCCESS，则其他结果集可用。</span><span class="sxs-lookup"><span data-stu-id="e55ce-113">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="e55ce-114">如果返回 SQL_NO_DATA，则没有其他结果集可用。</span><span class="sxs-lookup"><span data-stu-id="e55ce-114">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="e55ce-115">如果返回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，则调用 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) 以确定来自 PRINT 或 RAISERROR 语句的输出是否可用。</span><span class="sxs-lookup"><span data-stu-id="e55ce-115">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
         <span data-ttu-id="e55ce-116">如果将绑定语句参数用于某一存储过程的输出参数或返回值，则使用在绑定参数缓冲区中当前提供的数据。</span><span class="sxs-lookup"><span data-stu-id="e55ce-116">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span> <span data-ttu-id="e55ce-117">此外，在使用绑定参数时，对 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 或 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 的每个调用都将执行 *S* 次 SQL 语句，其中，*S* 是绑定参数数组中元素的数目。</span><span class="sxs-lookup"><span data-stu-id="e55ce-117">Also, when bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement *S* times, where *S* is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="e55ce-118">这意味着，将存在 *S* 组要处理的结果，而其中每组结果都由所有结果集、输出参数以及 SQL 语句的单次执行通常返回的返回代码构成。</span><span class="sxs-lookup"><span data-stu-id="e55ce-118">This means that there will be *S* sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e55ce-119">在某一结果集包含计算行时，每个计算行都可作为单独的结果集提供。</span><span class="sxs-lookup"><span data-stu-id="e55ce-119">When a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="e55ce-120">这些计算结果集混杂在普通行内，并且将普通行分为多个结果集。</span><span class="sxs-lookup"><span data-stu-id="e55ce-120">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
5.  <span data-ttu-id="e55ce-121">或者，使用 SQL_UNBIND 调用 [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) 以释放任何绑定列缓冲区。</span><span class="sxs-lookup"><span data-stu-id="e55ce-121">Optionally, call [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
6.  <span data-ttu-id="e55ce-122">如果其他结果集可用，则转到步骤 1。</span><span class="sxs-lookup"><span data-stu-id="e55ce-122">If another result set is available, go to Step 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e55ce-123">若要在 [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 返回 SQL_NO_DATA 之前取消处理结果集，请调用 [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)。</span><span class="sxs-lookup"><span data-stu-id="e55ce-123">To cancel processing a result set before [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) returns SQL_NO_DATA, call [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55ce-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e55ce-124">See Also</span></span>  
 [<span data-ttu-id="e55ce-125">处理结果操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="e55ce-125">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
