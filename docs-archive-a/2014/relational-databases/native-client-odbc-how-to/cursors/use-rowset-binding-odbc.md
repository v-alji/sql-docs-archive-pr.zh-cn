---
title: " (ODBC) 使用行集绑定 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: rothja
ms.author: jroth
ms.openlocfilehash: e2e0671fd1140e72005cd1a7532ea581f077382f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576718"
---
# <a name="use-rowset-binding-odbc"></a><span data-ttu-id="1a511-102">使用行集绑定 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="1a511-102">Use Rowset Binding (ODBC)</span></span>
    
### <a name="to-use-column-wise-binding"></a><span data-ttu-id="1a511-103">使用按列绑定</span><span class="sxs-lookup"><span data-stu-id="1a511-103">To use column-wise binding</span></span>  
  
1.  <span data-ttu-id="1a511-104">对于每个绑定列，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1a511-104">For each bound column, do the following:</span></span>  
  
    -   <span data-ttu-id="1a511-105">分配一个包含 R（或更多）个列缓冲区的数组以存储数据值，其中，R 是行集中的行数。</span><span class="sxs-lookup"><span data-stu-id="1a511-105">Allocate an array of R (or more) column buffers to store data values, where R is number of rows in the rowset.</span></span>  
  
    -   <span data-ttu-id="1a511-106">此外，可以选择分配一个包含 R（或更多）个列缓冲区的数组以存储数据长度。</span><span class="sxs-lookup"><span data-stu-id="1a511-106">Optionally, allocate an array of R (or more) column buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="1a511-107">调用[SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) ，将列的数据值和数据长度数组绑定到行集的列。</span><span class="sxs-lookup"><span data-stu-id="1a511-107">Call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to bind the column's data value and data length arrays to the column of the rowset.</span></span>  
  
2.  <span data-ttu-id="1a511-108">调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="1a511-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="1a511-109">将 SQL_ATTR_ROW_ARRAY_SIZE 设置为行集中的行数 (R)。</span><span class="sxs-lookup"><span data-stu-id="1a511-109">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="1a511-110">将 SQL_ATTR_ROW_BIND_TYPE 设置为 SQL_BIND_BY_COLUMN。</span><span class="sxs-lookup"><span data-stu-id="1a511-110">Set SQL_ATTR_ROW_BIND_TYPE to SQL_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="1a511-111">将 SQL_ATTR_ROWS FETCHED_PTR 属性设置为指向 SQLUINTEGER 变量，以包含所提取的行数。</span><span class="sxs-lookup"><span data-stu-id="1a511-111">Set the SQL_ATTR_ROWS FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="1a511-112">将 SQL_ATTR_ROW_STATUS_PTR 设置为指向 SQLUSSMALLINT 变量的数组 [R]，以包含行状态指示器。</span><span class="sxs-lookup"><span data-stu-id="1a511-112">Set SQL_ATTR_ROW_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="1a511-113">执行语句。</span><span class="sxs-lookup"><span data-stu-id="1a511-113">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="1a511-114">对[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)的每个调用都将检索 R 行并将数据传输到绑定列。</span><span class="sxs-lookup"><span data-stu-id="1a511-114">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
### <a name="to-use-row-wise-binding"></a><span data-ttu-id="1a511-115">使用按行绑定</span><span class="sxs-lookup"><span data-stu-id="1a511-115">To use row-wise binding</span></span>  
  
1.  <span data-ttu-id="1a511-116">分配结构数组 [R]，其中，R 是行集中的行数。</span><span class="sxs-lookup"><span data-stu-id="1a511-116">Allocate an array[R] of structures, where R is the number of rows in the rowset.</span></span> <span data-ttu-id="1a511-117">该结构对于每列都有一个元素，并且每个元素有两部分：</span><span class="sxs-lookup"><span data-stu-id="1a511-117">The structure has one element for each column, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="1a511-118">第一部分是适当的数据类型的变量，用于包含列数据。</span><span class="sxs-lookup"><span data-stu-id="1a511-118">The first part is a variable of the appropriate data type to hold the column data.</span></span>  
  
    -   <span data-ttu-id="1a511-119">第二部分是 SQLINTEGER 变量，用于包含列状态指示器。</span><span class="sxs-lookup"><span data-stu-id="1a511-119">The second part is a SQLINTEGER variable to hold the column status indicator.</span></span>  
  
2.  <span data-ttu-id="1a511-120">调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="1a511-120">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="1a511-121">将 SQL_ATTR_ROW_ARRAY_SIZE 设置为行集中的行数 (R)。</span><span class="sxs-lookup"><span data-stu-id="1a511-121">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="1a511-122">将 SQL_ATTR_ROW_BIND_TYPE 设置为在步骤 1 中分配的结构的大小。</span><span class="sxs-lookup"><span data-stu-id="1a511-122">Set SQL_ATTR_ROW_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="1a511-123">将 SQL_ATTR_ROWS_FETCHED_PTR 属性设置为指向 SQLUINTEGER 变量，以包含所提取的行数。</span><span class="sxs-lookup"><span data-stu-id="1a511-123">Set the SQL_ATTR_ROWS_FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="1a511-124">将 SQL_ATTR_PARAMS_STATUS_PTR 设置为指向 SQLUSSMALLINT 变量的数组 [R]，以包含行状态指示器。</span><span class="sxs-lookup"><span data-stu-id="1a511-124">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="1a511-125">对于结果集中的每个列，调用[SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) ，将列的数据值和数据长度指针指向其在步骤1中分配的结构数组的第一个元素中的变量。</span><span class="sxs-lookup"><span data-stu-id="1a511-125">For each column in the result set, call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to point the data value and data length pointer of the column to their variables in the first element of the array of structures allocated in Step 1.</span></span>  
  
4.  <span data-ttu-id="1a511-126">执行语句。</span><span class="sxs-lookup"><span data-stu-id="1a511-126">Execute the statement.</span></span>  
  
5.  <span data-ttu-id="1a511-127">对[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)的每个调用都将检索 R 行并将数据传输到绑定列。</span><span class="sxs-lookup"><span data-stu-id="1a511-127">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a511-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a511-128">See Also</span></span>  
 <span data-ttu-id="1a511-129">[使用游标操作指南主题 &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="1a511-129">[Using Cursors How-to Topics &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md) </span></span>  
 <span data-ttu-id="1a511-130">[如何实现游标](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span><span class="sxs-lookup"><span data-stu-id="1a511-130">[How Cursors Are Implemented](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span></span>  
 [<span data-ttu-id="1a511-131">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="1a511-131">Use Cursors &#40;ODBC&#41;</span></span>](use-cursors-odbc.md)  
  
  
