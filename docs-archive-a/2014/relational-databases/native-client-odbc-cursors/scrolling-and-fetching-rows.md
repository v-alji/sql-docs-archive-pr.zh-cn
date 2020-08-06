---
title: 滚动和提取行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 97586f82ddddb79581b0f9c027aa60d7822b472c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692912"
---
# <a name="scrolling-and-fetching-rows"></a><span data-ttu-id="8f4a2-102">滚动和提取行</span><span class="sxs-lookup"><span data-stu-id="8f4a2-102">Scrolling and Fetching Rows</span></span>
  <span data-ttu-id="8f4a2-103">若要使用可滚动游标，ODBC 应用程序必须：</span><span class="sxs-lookup"><span data-stu-id="8f4a2-103">To use a scrollable cursor, an ODBC application must:</span></span>  
  
-   <span data-ttu-id="8f4a2-104">使用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)设置光标功能。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-104">Set the cursor capabilities using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
-   <span data-ttu-id="8f4a2-105">使用**SQLExecute**或**SQLExecDirect**打开游标。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-105">Open the cursor using **SQLExecute** or **SQLExecDirect**.</span></span>  
  
-   <span data-ttu-id="8f4a2-106">使用**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)滚动和提取行。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-106">Scroll and fetch rows using **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="8f4a2-107">**SQLFetch**和**SQLFetchSroll**一次可以提取行块。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-107">Both **SQLFetch** and **SQLFetchSroll** can fetch blocks of rows at a time.</span></span> <span data-ttu-id="8f4a2-108">返回的行数是通过使用**SQLSetStmtAttr**设置 SQL_ATTR_ROW_ARRAY_SIZE 参数指定的。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-108">The number of rows returned is specified by using **SQLSetStmtAttr** to set the SQL_ATTR_ROW_ARRAY_SIZE parameter.</span></span>  
  
 <span data-ttu-id="8f4a2-109">ODBC 应用程序可以使用**SQLFetch**来提取只进游标。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-109">ODBC applications can use **SQLFetch** to fetch through a forward-only cursor.</span></span>  
  
 <span data-ttu-id="8f4a2-110">**SQLFetchScroll**用于在游标周围滚动。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-110">**SQLFetchScroll** is used to scroll around a cursor.</span></span> <span data-ttu-id="8f4a2-111">**SQLFetchScroll**支持提取下一个、以前的、第一个和最后一个行集， (提取从当前行集开头开始的行集*n*行) 和绝对提取 (从第*n*行开始) 提取行集。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-111">**SQLFetchScroll** supports fetching the next, prior, first, and last rowsets in addition to relative fetching (fetch the rowset *n* rows from the start of the current rowset) and absolute fetching (fetch the rowset starting at row *n*).</span></span> <span data-ttu-id="8f4a2-112">如果在绝对提取中*n*为负，则从结果集的末尾开始对行进行计数。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-112">If *n* is negative in an absolute fetch, rows are counted from the end of the result set.</span></span> <span data-ttu-id="8f4a2-113">绝对提取行 -1 表示提取从结果集中最后一行开始的行集。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-113">An absolute fetch of row -1 means to fetch the rowset that starts with the last row in the result set.</span></span>  
  
 <span data-ttu-id="8f4a2-114">仅对其块游标功能（如报表）使用**SQLFetchScroll**的应用程序可能只使用用于提取下一个行集的选项传递结果集。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-114">Applications that use **SQLFetchScroll** only for its block cursor capabilities, such as reports, are likely to pass through the result set a single time, using only the option to fetch the next rowset.</span></span> <span data-ttu-id="8f4a2-115">另一方面，基于屏幕的应用程序可以利用**SQLFetchScroll**的所有功能。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-115">Screen-based applications, on the other hand, can take advantage of all the capabilities of **SQLFetchScroll**.</span></span> <span data-ttu-id="8f4a2-116">如果应用程序将行集大小设置为屏幕上显示的行数，并将屏幕缓冲区绑定到结果集，则可以直接将滚动条操作转换为对**SQLFetchScroll**的调用。</span><span class="sxs-lookup"><span data-stu-id="8f4a2-116">If the application sets the rowset size to the number of rows displayed on the screen and binds the screen buffers to the result set, it can translate scroll bar operations directly to calls to **SQLFetchScroll**.</span></span>  
  
|<span data-ttu-id="8f4a2-117">滚动条操作</span><span class="sxs-lookup"><span data-stu-id="8f4a2-117">Scroll bar operation</span></span>|<span data-ttu-id="8f4a2-118">SQLFetchScroll 滚动选项</span><span class="sxs-lookup"><span data-stu-id="8f4a2-118">SQLFetchScroll scrolling option</span></span>|  
|--------------------------|-------------------------------------|  
|<span data-ttu-id="8f4a2-119">向上翻页</span><span class="sxs-lookup"><span data-stu-id="8f4a2-119">Page up</span></span>|<span data-ttu-id="8f4a2-120">SQL_FETCH_PRIOR</span><span class="sxs-lookup"><span data-stu-id="8f4a2-120">SQL_FETCH_PRIOR</span></span>|  
|<span data-ttu-id="8f4a2-121">向下翻页</span><span class="sxs-lookup"><span data-stu-id="8f4a2-121">Page down</span></span>|<span data-ttu-id="8f4a2-122">SQL_FETCH_NEXT</span><span class="sxs-lookup"><span data-stu-id="8f4a2-122">SQL_FETCH_NEXT</span></span>|  
|<span data-ttu-id="8f4a2-123">向上移动一行</span><span class="sxs-lookup"><span data-stu-id="8f4a2-123">Line up</span></span>|<span data-ttu-id="8f4a2-124">FetchOffset 等于-1 的 SQL_FETCH_RELATIVE</span><span class="sxs-lookup"><span data-stu-id="8f4a2-124">SQL_FETCH_RELATIVE with FetchOffset equal to -1</span></span>|  
|<span data-ttu-id="8f4a2-125">向下移动一行</span><span class="sxs-lookup"><span data-stu-id="8f4a2-125">Line down</span></span>|<span data-ttu-id="8f4a2-126">SQL_FETCH_RELATIVE，FetchOffset 等于 1</span><span class="sxs-lookup"><span data-stu-id="8f4a2-126">SQL_FETCH_RELATIVE with FetchOffset equal to 1</span></span>|  
|<span data-ttu-id="8f4a2-127">滚动框移到顶部</span><span class="sxs-lookup"><span data-stu-id="8f4a2-127">Scroll box to top</span></span>|<span data-ttu-id="8f4a2-128">SQL_FETCH_FIRST</span><span class="sxs-lookup"><span data-stu-id="8f4a2-128">SQL_FETCH_FIRST</span></span>|  
|<span data-ttu-id="8f4a2-129">滚动框移到底部</span><span class="sxs-lookup"><span data-stu-id="8f4a2-129">Scroll box to bottom</span></span>|<span data-ttu-id="8f4a2-130">SQL_FETCH_LAST</span><span class="sxs-lookup"><span data-stu-id="8f4a2-130">SQL_FETCH_LAST</span></span>|  
|<span data-ttu-id="8f4a2-131">滚动框位于随机位置</span><span class="sxs-lookup"><span data-stu-id="8f4a2-131">Random scroll box position</span></span>|<span data-ttu-id="8f4a2-132">SQL_FETCH_ABSOLUTE</span><span class="sxs-lookup"><span data-stu-id="8f4a2-132">SQL_FETCH_ABSOLUTE</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="8f4a2-133">本节内容</span><span class="sxs-lookup"><span data-stu-id="8f4a2-133">In This Section</span></span>  
  
-   [<span data-ttu-id="8f4a2-134">在 ODBC 中为行加书签</span><span class="sxs-lookup"><span data-stu-id="8f4a2-134">Bookmarking Rows in ODBC</span></span>](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f4a2-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f4a2-135">See Also</span></span>  
 [<span data-ttu-id="8f4a2-136">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="8f4a2-136">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
