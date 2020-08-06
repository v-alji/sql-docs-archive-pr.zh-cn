---
title: 使用游标 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 61afedab4f4a1e309a08d9c2421ca7889811da8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692908"
---
# <a name="using-cursors-odbc"></a><span data-ttu-id="d6bd9-102">使用游标 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d6bd9-102">Using Cursors (ODBC)</span></span>
  <span data-ttu-id="d6bd9-103">ODBC 支持允许以下项的游标模型：</span><span class="sxs-lookup"><span data-stu-id="d6bd9-103">ODBC supports a cursor model that allows:</span></span>  
  
-   <span data-ttu-id="d6bd9-104">多种类型的游标。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-104">Several types of cursors.</span></span>  
  
-   <span data-ttu-id="d6bd9-105">在游标中滚动和定位。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-105">Scrolling and positioning within a cursor.</span></span>  
  
-   <span data-ttu-id="d6bd9-106">多个并发选项。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-106">Several concurrency options.</span></span>  
  
-   <span data-ttu-id="d6bd9-107">定位更新。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-107">Positioned updates.</span></span>  
  
 <span data-ttu-id="d6bd9-108">ODBC 应用程序很少声明和打开游标，或使用与游标相关的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-108">ODBC applications rarely declare and open cursors or use any cursor-related [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="d6bd9-109">ODBC 自动为从 SQL 语句返回的每个结果集打开游标。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-109">ODBC automatically opens a cursor for every result set returned from an SQL statement.</span></span> <span data-ttu-id="d6bd9-110">在执行 SQL 语句之前，游标的特征由[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)设置的语句属性控制。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-110">The characteristics of the cursors are controlled by statement attributes set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) before the SQL statement is executed.</span></span> <span data-ttu-id="d6bd9-111">用于处理结果集的 ODBC API 函数支持完整范围的游标功能，包括提取、滚动和定位更新。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-111">The ODBC API functions for processing result sets support the full range of cursor functionality, including fetching, scrolling, and positioned updates.</span></span>  
  
 <span data-ttu-id="d6bd9-112">下面是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本和 ODBC 应用程序如何使用游标的比较。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-112">This is a comparison of how [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and ODBC applications work with cursors.</span></span>  
  
|<span data-ttu-id="d6bd9-113">操作</span><span class="sxs-lookup"><span data-stu-id="d6bd9-113">Action</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)]|<span data-ttu-id="d6bd9-114">ODBC</span><span class="sxs-lookup"><span data-stu-id="d6bd9-114">ODBC</span></span>|  
|------------|------------------------|----------|  
|<span data-ttu-id="d6bd9-115">定义游标行为</span><span class="sxs-lookup"><span data-stu-id="d6bd9-115">Define cursor behavior</span></span>|<span data-ttu-id="d6bd9-116">通过 DECLARE CURSOR 参数进行指定</span><span class="sxs-lookup"><span data-stu-id="d6bd9-116">Specify through DECLARE CURSOR parameters</span></span>|<span data-ttu-id="d6bd9-117">使用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)设置 cursor 特性</span><span class="sxs-lookup"><span data-stu-id="d6bd9-117">Set cursor attributes by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)</span></span>|  
|<span data-ttu-id="d6bd9-118">打开游标</span><span class="sxs-lookup"><span data-stu-id="d6bd9-118">Open a cursor</span></span>|<span data-ttu-id="d6bd9-119">声明游标打开*cursor_name*</span><span class="sxs-lookup"><span data-stu-id="d6bd9-119">DECLARE CURSOR OPEN *cursor_name*</span></span>|<span data-ttu-id="d6bd9-120">**SQLExecDirect**或**SQLExecute**</span><span class="sxs-lookup"><span data-stu-id="d6bd9-120">**SQLExecDirect** or **SQLExecute**</span></span>|  
|<span data-ttu-id="d6bd9-121">提取行</span><span class="sxs-lookup"><span data-stu-id="d6bd9-121">Fetch rows</span></span>|<span data-ttu-id="d6bd9-122">FETCH</span><span class="sxs-lookup"><span data-stu-id="d6bd9-122">FETCH</span></span>|<span data-ttu-id="d6bd9-123">**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)</span><span class="sxs-lookup"><span data-stu-id="d6bd9-123">**SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)</span></span>|  
|<span data-ttu-id="d6bd9-124">定位更新</span><span class="sxs-lookup"><span data-stu-id="d6bd9-124">Positioned update</span></span>|<span data-ttu-id="d6bd9-125">UPDATE 或 DELETE 中的 WHERE CURRENT OF 子句</span><span class="sxs-lookup"><span data-stu-id="d6bd9-125">WHERE CURRENT OF clause on UPDATE or DELETE</span></span>|<span data-ttu-id="d6bd9-126">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="d6bd9-126">**SQLSetPos**</span></span>|  
|<span data-ttu-id="d6bd9-127">关闭游标</span><span class="sxs-lookup"><span data-stu-id="d6bd9-127">Close a cursor</span></span>|<span data-ttu-id="d6bd9-128">关闭*cursor_name*解除分配</span><span class="sxs-lookup"><span data-stu-id="d6bd9-128">CLOSE *cursor_name* DEALLOCATE</span></span>|[<span data-ttu-id="d6bd9-129">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="d6bd9-129">SQLCloseCursor</span></span>](../native-client-odbc-api/sqlclosecursor.md)|  
  
 <span data-ttu-id="d6bd9-130">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中实现的服务器游标支持 ODBC 游标模型的功能。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-130">The server cursors implemented in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support the functionality of the ODBC cursor model.</span></span> <span data-ttu-id="d6bd9-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 驱动程序使用服务器游标以支持 ODBC API 的游标功能。</span><span class="sxs-lookup"><span data-stu-id="d6bd9-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client driver uses server cursors to support the cursor functionality of the ODBC API.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6bd9-132">本节内容</span><span class="sxs-lookup"><span data-stu-id="d6bd9-132">In This Section</span></span>  
  
-   [<span data-ttu-id="d6bd9-133">如何实现游标</span><span class="sxs-lookup"><span data-stu-id="d6bd9-133">How Cursors Are Implemented</span></span>](implementation/how-cursors-are-implemented.md)  
  
-   [<span data-ttu-id="d6bd9-134">游标类型</span><span class="sxs-lookup"><span data-stu-id="d6bd9-134">Cursor Types</span></span>](cursor-types.md)  
  
-   [<span data-ttu-id="d6bd9-135">游标行为</span><span class="sxs-lookup"><span data-stu-id="d6bd9-135">Cursor Behaviors</span></span>](cursor-behaviors.md)  
  
-   [<span data-ttu-id="d6bd9-136">游标属性</span><span class="sxs-lookup"><span data-stu-id="d6bd9-136">Cursor Properties</span></span>](properties/cursor-properties.md)  
  
-   [<span data-ttu-id="d6bd9-137">ODBC&#41;的游标编程详细信息 &#40;</span><span class="sxs-lookup"><span data-stu-id="d6bd9-137">Cursor Programming Details &#40;ODBC&#41;</span></span>](programming/cursor-programming-details-odbc.md)  
  
-   [<span data-ttu-id="d6bd9-138">滚动和提取行</span><span class="sxs-lookup"><span data-stu-id="d6bd9-138">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [<span data-ttu-id="d6bd9-139">ODBC&#41;的定位更新 &#40;</span><span class="sxs-lookup"><span data-stu-id="d6bd9-139">Positioned Updates &#40;ODBC&#41;</span></span>](positioned-updates-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="d6bd9-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6bd9-140">See Also</span></span>  
 <span data-ttu-id="d6bd9-141">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="d6bd9-141">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="d6bd9-142">[CLOSE &#40;Transact-sql&#41;](/sql/t-sql/language-elements/close-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6bd9-142">[CLOSE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/close-transact-sql) </span></span>  
 <span data-ttu-id="d6bd9-143">[游标](../../relational-databases/cursors.md) </span><span class="sxs-lookup"><span data-stu-id="d6bd9-143">[Cursors](../../relational-databases/cursors.md) </span></span>  
 <span data-ttu-id="d6bd9-144">[释放 &#40;Transact-sql&#41;](/sql/t-sql/language-elements/deallocate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6bd9-144">[DEALLOCATE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/deallocate-transact-sql) </span></span>  
 <span data-ttu-id="d6bd9-145">[&#40;Transact-sql 声明游标&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6bd9-145">[DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span></span>  
 <span data-ttu-id="d6bd9-146">[FETCH (Transact-SQL)](/sql/t-sql/language-elements/fetch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d6bd9-146">[FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql) </span></span>  
 [<span data-ttu-id="d6bd9-147">OPEN (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d6bd9-147">OPEN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/open-transact-sql)  
  
  
