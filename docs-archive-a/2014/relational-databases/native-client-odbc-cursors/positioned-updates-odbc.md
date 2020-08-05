---
title: ODBC) 的定位更新 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
author: rothja
ms.author: jroth
ms.openlocfilehash: 20272014e32632117e6282e5929d1d21789852df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580256"
---
# <a name="positioned-updates-odbc"></a><span data-ttu-id="db049-102">定位更新 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="db049-102">Positioned Updates (ODBC)</span></span>
  <span data-ttu-id="db049-103">ODBC 支持通过两种方法在游标中执行定位更新：</span><span class="sxs-lookup"><span data-stu-id="db049-103">ODBC supports two methods for performing positioned updates in a cursor:</span></span>  
  
-   <span data-ttu-id="db049-104">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="db049-104">**SQLSetPos**</span></span>  
  
-   <span data-ttu-id="db049-105">WHERE CURRENT OF 子句</span><span class="sxs-lookup"><span data-stu-id="db049-105">WHERE CURRENT OF clause</span></span>  
  
 <span data-ttu-id="db049-106">更常见的方法是使用**SQLSetPos**。</span><span class="sxs-lookup"><span data-stu-id="db049-106">The more common approach is to use **SQLSetPos**.</span></span> <span data-ttu-id="db049-107">它具有以下选项。</span><span class="sxs-lookup"><span data-stu-id="db049-107">It has the following options.</span></span>  
  
 <span data-ttu-id="db049-108">SQL_POSITION</span><span class="sxs-lookup"><span data-stu-id="db049-108">SQL_POSITION</span></span>  
 <span data-ttu-id="db049-109">将游标定位到当前行集中的特定行。</span><span class="sxs-lookup"><span data-stu-id="db049-109">Positions the cursor on a specific row in the current rowset.</span></span>  
  
 <span data-ttu-id="db049-110">SQL_REFRESH</span><span class="sxs-lookup"><span data-stu-id="db049-110">SQL_REFRESH</span></span>  
 <span data-ttu-id="db049-111">使用游标当前所定位行的值刷新被绑定到结果集列上的程序变量。</span><span class="sxs-lookup"><span data-stu-id="db049-111">Refreshes program variables bound to the result set columns with the values from the row the cursor is currently positioned on.</span></span>  
  
 <span data-ttu-id="db049-112">SQL_UPDATE</span><span class="sxs-lookup"><span data-stu-id="db049-112">SQL_UPDATE</span></span>  
 <span data-ttu-id="db049-113">使用绑定到结果集列上的程序变量中所存储的值来更新游标中的当前行。</span><span class="sxs-lookup"><span data-stu-id="db049-113">Updates the current row in the cursor with the values stored in the program variables bound to the result set columns.</span></span>  
  
 <span data-ttu-id="db049-114">SQL_DELETE</span><span class="sxs-lookup"><span data-stu-id="db049-114">SQL_DELETE</span></span>  
 <span data-ttu-id="db049-115">删除游标中的当前行。</span><span class="sxs-lookup"><span data-stu-id="db049-115">Deletes the current row in the cursor.</span></span>  
  
 <span data-ttu-id="db049-116">当语句句柄游标属性设置为使用服务器游标时，可以将**SQLSetPos**与任何语句结果集一起使用。</span><span class="sxs-lookup"><span data-stu-id="db049-116">**SQLSetPos** can be used with any statement result set when the statement handle cursor attributes are set to use server cursors.</span></span> <span data-ttu-id="db049-117">结果集列必须绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="db049-117">The result set columns must be bound to program variables.</span></span> <span data-ttu-id="db049-118">应用程序提取行后，会立即调用**SQLSetPos** (SQL_POSTION) 将游标定位在该行上。</span><span class="sxs-lookup"><span data-stu-id="db049-118">As soon as the application has fetched a row it calls **SQLSetPos**(SQL_POSTION) to position the cursor on the row.</span></span> <span data-ttu-id="db049-119">随后应用程序可以调用 SQLSetPos(SQL_DELETE) 删除当前行，或者可以将新数据值移入绑定程序变量并调用 SQLSetPos(SQL_UPDATE) 更新当前行。</span><span class="sxs-lookup"><span data-stu-id="db049-119">The application could then call SQLSetPos(SQL_DELETE) to delete the current row, or it can move new data values into the bound program variables and call SQLSetPos(SQL_UPDATE) to update the current row.</span></span>  
  
 <span data-ttu-id="db049-120">应用程序可以通过**SQLSetPos**更新或删除行集中的任何行。</span><span class="sxs-lookup"><span data-stu-id="db049-120">Applications can update or delete any row in the rowset with **SQLSetPos**.</span></span> <span data-ttu-id="db049-121">调用**SQLSetPos**是构造和执行 SQL 语句的一种简便方法。</span><span class="sxs-lookup"><span data-stu-id="db049-121">Calling **SQLSetPos** is a convenient alternative to constructing and executing an SQL statement.</span></span> <span data-ttu-id="db049-122">**SQLSetPos**对当前行集进行操作，并且只能在调用[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)后使用。</span><span class="sxs-lookup"><span data-stu-id="db049-122">**SQLSetPos** operates on the current rowset and can be used only after a call to [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="db049-123">行集大小通过使用 SQL_ATTR_ROW_ARRAY_SIZE 的属性参数对[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)的调用设置。</span><span class="sxs-lookup"><span data-stu-id="db049-123">Rowset size is set by a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with an attribute argument of SQL_ATTR_ROW_ARRAY_SIZE.</span></span> <span data-ttu-id="db049-124">**SQLSetPos**仅在调用**SQLFetch**或**SQLFetchScroll**后使用新的行集大小。</span><span class="sxs-lookup"><span data-stu-id="db049-124">**SQLSetPos** uses a new rowset size, but only after a call to **SQLFetch** or **SQLFetchScroll**.</span></span> <span data-ttu-id="db049-125">例如，如果行集大小发生更改，则会调用**SQLSetPos** ，然后调用**SQLFetch**或**SQLFetchScroll** 。</span><span class="sxs-lookup"><span data-stu-id="db049-125">For example, if the rowset size is changed, **SQLSetPos** is called and then **SQLFetch** or **SQLFetchScroll** is called.</span></span> <span data-ttu-id="db049-126">对**SQLSetPos**的调用使用旧的行集大小，但**SQLFetch**或**SQLFetchScroll**使用新的行集大小。</span><span class="sxs-lookup"><span data-stu-id="db049-126">The call to **SQLSetPos** uses the old rowset size, but **SQLFetch** or **SQLFetchScroll** uses the new rowset size.</span></span>  
  
 <span data-ttu-id="db049-127">行集中的第一行的行编号为 1。</span><span class="sxs-lookup"><span data-stu-id="db049-127">The first row in the rowset is row number 1.</span></span> <span data-ttu-id="db049-128">**SQLSetPos**中的 RowNumber 参数必须标识行集中的行;也就是说，其值必须介于1和最近提取的行数之间。</span><span class="sxs-lookup"><span data-stu-id="db049-128">The RowNumber argument in **SQLSetPos** must identify a row in the rowset; that is, its value must be in the range between 1 and the number of rows that were most recently fetched.</span></span> <span data-ttu-id="db049-129">这可能小于行集大小。</span><span class="sxs-lookup"><span data-stu-id="db049-129">This may be less than the rowset size.</span></span> <span data-ttu-id="db049-130">如果 RowNumber 为 0，将对行集中的所有行应用操作。</span><span class="sxs-lookup"><span data-stu-id="db049-130">If RowNumber is 0, the operation applies to every row in the rowset.</span></span>  
  
 <span data-ttu-id="db049-131">**SQLSetPos**的 delete 操作使数据源删除表中的一个或多个选定行。</span><span class="sxs-lookup"><span data-stu-id="db049-131">The delete operation of **SQLSetPos** makes the data source delete one or more selected rows of a table.</span></span> <span data-ttu-id="db049-132">若要删除**SQLSetPos**的行，应用程序将调用**SQLSetPos** ，并将操作设置 SQL_DELETE 为，并将 RowNumber 设置为要删除的行号。</span><span class="sxs-lookup"><span data-stu-id="db049-132">To delete rows with **SQLSetPos**, the application calls **SQLSetPos** with Operation set to SQL_DELETE and RowNumber set to the number of the row to delete.</span></span> <span data-ttu-id="db049-133">如果 RowNumber 为 0，将删除行集中的所有行。</span><span class="sxs-lookup"><span data-stu-id="db049-133">If RowNumber is 0, all rows in the rowset are deleted.</span></span>  
  
 <span data-ttu-id="db049-134">**SQLSetPos**返回后，删除的行是当前行，其状态为 SQL_ROW_DELETED。</span><span class="sxs-lookup"><span data-stu-id="db049-134">After **SQLSetPos** returns, the deleted row is the current row and its status is SQL_ROW_DELETED.</span></span> <span data-ttu-id="db049-135">该行不能用于任何其他定位操作，例如对[SQLGetData](../native-client-odbc-api/sqlgetdata.md)或**SQLSetPos**的调用。</span><span class="sxs-lookup"><span data-stu-id="db049-135">The row cannot be used in any additional positioned operations, such as calls to [SQLGetData](../native-client-odbc-api/sqlgetdata.md) or **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="db049-136">删除行集的所有行时 (RowNumber 等于 0) 时，应用程序可以通过使用行操作数组来阻止该驱动程序删除某些行，这与**SQLSetPos**的更新操作类似。</span><span class="sxs-lookup"><span data-stu-id="db049-136">When you delete all rows of the rowset (RowNumber is equal to 0), the application can prevent the driver from deleting certain rows by using the row operation array just like for the update operation of **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="db049-137">每个删除的行都应该是结果集中存在的行。</span><span class="sxs-lookup"><span data-stu-id="db049-137">Every row that is deleted should be a row that exists in the result set.</span></span> <span data-ttu-id="db049-138">如果应用程序缓冲区已被提取操作填充，并且保持了行状态数组，则所有这些行位置处的行值都不应为 SQL_ROW_DELETED、SQL_ROW_ERROR 或 SQL_ROW_NOROW。</span><span class="sxs-lookup"><span data-stu-id="db049-138">If the application buffers were filled by fetching, and if a row status array has been maintained, its values at each of these row positions should not be SQL_ROW_DELETED, SQL_ROW_ERROR, or SQL_ROW_NOROW.</span></span>  
  
 <span data-ttu-id="db049-139">通过在 UPDATE、DELETE 和 INSERT 语句中使用 WHERE CURRENT OF 子句，也可以执行定位更新。</span><span class="sxs-lookup"><span data-stu-id="db049-139">Positioned updates can also be performed using the WHERE CURRENT OF clause on UPDATE, DELETE, and INSERT statements.</span></span> <span data-ttu-id="db049-140">其中，CURRENT of 需要在调用[SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md)函数时 ODBC 将生成的游标名称，或者通过调用**SQLSetCursorName**来指定。</span><span class="sxs-lookup"><span data-stu-id="db049-140">WHERE CURRENT OF requires a cursor name that ODBC will generate when the [SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md) function is called, or which you can specify by calling **SQLSetCursorName**.</span></span> <span data-ttu-id="db049-141">以下是用于在 ODBC 应用程序中执行 WHERE CURRENT OF 更新的一般步骤：</span><span class="sxs-lookup"><span data-stu-id="db049-141">The following are general steps used to perform a WHERE CURRENT OF update in an ODBC application:</span></span>  
  
-   <span data-ttu-id="db049-142">调用**SQLSetCursorName**为语句句柄建立游标名称。</span><span class="sxs-lookup"><span data-stu-id="db049-142">Call **SQLSetCursorName** to establish a cursor name for the statement handle.</span></span>  
  
-   <span data-ttu-id="db049-143">生成包含 FOR UPDATE OF 子句的 SELECT 语句，并执行该语句。</span><span class="sxs-lookup"><span data-stu-id="db049-143">Build a SELECT statement with a FOR UPDATE OF clause and execute it.</span></span>  
  
-   <span data-ttu-id="db049-144">调用**SQLFetchScroll**可检索行集或**SQLFetch**以检索行。</span><span class="sxs-lookup"><span data-stu-id="db049-144">Call **SQLFetchScroll** to retrieve a rowset or **SQLFetch** to retrieve a row.</span></span>  
  
-   <span data-ttu-id="db049-145">调用**SQLSetPos** (SQL_POSITION) 将游标定位在该行上。</span><span class="sxs-lookup"><span data-stu-id="db049-145">Call **SQLSetPos** (SQL_POSITION) to position the cursor on the row.</span></span>  
  
-   <span data-ttu-id="db049-146">使用**SQLSetCursorName**设置的游标名称，生成和执行包含 WHERE CURRENT of 子句的 UPDATE 语句。</span><span class="sxs-lookup"><span data-stu-id="db049-146">Build and execute an UPDATE statement with a WHERE CURRENT OF clause using the cursor name set with **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="db049-147">或者，在执行 select 语句后（而不是在执行 SELECT 语句之前调用**SQLSetCursorName** ），可以调用**SQLGetCursorName** 。</span><span class="sxs-lookup"><span data-stu-id="db049-147">Alternatively, you could call **SQLGetCursorName** after you execute the SELECT statement instead of calling **SQLSetCursorName** before executing the SELECT statement.</span></span> <span data-ttu-id="db049-148">如果未使用**SQLSetCursorName**设置游标名称， **SQLGETCURSORNAME**将返回 ODBC 分配的默认游标名称。</span><span class="sxs-lookup"><span data-stu-id="db049-148">**SQLGetCursorName** returns a default cursor name assigned by ODBC if you do not set a cursor name using **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="db049-149">使用服务器游标时， **SQLSetPos**的优先级高于当前的。</span><span class="sxs-lookup"><span data-stu-id="db049-149">**SQLSetPos** is preferred over WHERE CURRENT OF when you are using server cursors.</span></span> <span data-ttu-id="db049-150">如果使用 ODBC 游标库中的静态、可更新游标，该游标库通过添加一个 WHERE 子句（带有基础表的键值）实现 WHERE CURRENT OF 更新。</span><span class="sxs-lookup"><span data-stu-id="db049-150">If you are using a static, updatable cursor with the ODBC cursor library, the cursor library implements WHERE CURRENT OF updates by adding a WHERE clause with the key values for the underlying table.</span></span> <span data-ttu-id="db049-151">如果表中的键不唯一，这可能导致意外更新。</span><span class="sxs-lookup"><span data-stu-id="db049-151">This can cause unintended updates if the keys in the table are not unique.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db049-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db049-152">See Also</span></span>  
 [<span data-ttu-id="db049-153">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="db049-153">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
