---
title: 提取和更新 ODBC)  (的行集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: rothja
ms.author: jroth
ms.openlocfilehash: e09a3033e0883452ecd69b82c9375ed28c920da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576725"
---
# <a name="fetch-and-update-rowsets-odbc"></a><span data-ttu-id="b9e05-102">提取和更新行集 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="b9e05-102">Fetch and Update Rowsets (ODBC)</span></span>
    
### <a name="to-fetch-and-update-rowsets"></a><span data-ttu-id="b9e05-103">提取和更新行集</span><span class="sxs-lookup"><span data-stu-id="b9e05-103">To fetch and update rowsets</span></span>  
  
1.  <span data-ttu-id="b9e05-104">（可选）通过 SQL_ROW_ARRAY_SIZE 调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)来更改行集中 (R) 的行数。</span><span class="sxs-lookup"><span data-stu-id="b9e05-104">Optionally, call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) with SQL_ROW_ARRAY_SIZE to change the number of rows (R) in the rowset.</span></span>  
  
2.  <span data-ttu-id="b9e05-105">调用[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)获取行集。</span><span class="sxs-lookup"><span data-stu-id="b9e05-105">Call [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) to get a rowset.</span></span>  
  
3.  <span data-ttu-id="b9e05-106">如果使用绑定列，则在行集的绑定列缓冲区中现在可以使用数据值和数据长度。</span><span class="sxs-lookup"><span data-stu-id="b9e05-106">If bound columns are used, use the data values and data lengths now available in the bound column buffers for the rowset.</span></span>  
  
     <span data-ttu-id="b9e05-107">如果使用未绑定的列，则对于每个行调用 SQL_POSITION [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) ，以设置游标位置;然后，对于每个未绑定列：</span><span class="sxs-lookup"><span data-stu-id="b9e05-107">If unbound columns are used, for each row call [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) with SQL_POSITION to set the cursor position; then, for each unbound column:</span></span>  
  
    -   <span data-ttu-id="b9e05-108">调用[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)一次或多次，以便在行集的最后一个绑定列后获取未绑定列的数据。</span><span class="sxs-lookup"><span data-stu-id="b9e05-108">Call [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) one or more times to get the data for unbound columns after the last bound column of the rowset.</span></span> <span data-ttu-id="b9e05-109">对[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)的调用应按照递增的列号顺序排列。</span><span class="sxs-lookup"><span data-stu-id="b9e05-109">Calls to [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) should be in order of increasing column number.</span></span>  
  
    -   <span data-ttu-id="b9e05-110">多次调用 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 以从 text 或 image 列获取数据。</span><span class="sxs-lookup"><span data-stu-id="b9e05-110">Call [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) multiple times to get data from a text or image column.</span></span>  
  
4.  <span data-ttu-id="b9e05-111">设置任意执行时数据 text 或 image 列。</span><span class="sxs-lookup"><span data-stu-id="b9e05-111">Set up any data-at-execution text or image columns.</span></span>  
  
5.  <span data-ttu-id="b9e05-112">调用[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)或[SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398)以设置游标位置、刷新、更新、删除或添加行集内)  (s。</span><span class="sxs-lookup"><span data-stu-id="b9e05-112">Call [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) or [SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398) to set the cursor position, refresh, update, delete, or add row(s) within the rowset.</span></span>  
  
     <span data-ttu-id="b9e05-113">如果执行时数据 text 或 image 列用于某个更新或添加操作，则处理它们。</span><span class="sxs-lookup"><span data-stu-id="b9e05-113">If data-at-execution text or image columns are used for an update or add operation, handle them.</span></span>  
  
6.  <span data-ttu-id="b9e05-114">（可选）执行定位的 UPDATE 或 DELETE 语句，指定 (在[SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)中可用的游标名) 并在同一连接上使用不同的语句句柄。</span><span class="sxs-lookup"><span data-stu-id="b9e05-114">Optionally, execute a positioned UPDATE or DELETE statement, specifying the cursor name (available from [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)) and using a different statement handle on the same connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e05-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9e05-115">See Also</span></span>  
 [<span data-ttu-id="b9e05-116">使用游标操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="b9e05-116">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](using-cursors-how-to-topics-odbc.md)  
  
  
