---
title: 游标行集大小 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 83c4e55025e6e3724f354f022760b7ba1e2f10e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589033"
---
# <a name="cursor-rowset-size"></a><span data-ttu-id="64b55-102">游标行集大小</span><span class="sxs-lookup"><span data-stu-id="64b55-102">Cursor Rowset Size</span></span>
  <span data-ttu-id="64b55-103">ODBC 游标并不仅限于一次提取一行。</span><span class="sxs-lookup"><span data-stu-id="64b55-103">ODBC cursors are not limited to fetching one row at a time.</span></span> <span data-ttu-id="64b55-104">它们可以在对**SQLFetch**或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)的每次调用中检索多个行。</span><span class="sxs-lookup"><span data-stu-id="64b55-104">They can retrieve multiple rows in each call to **SQLFetch** or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="64b55-105">当与客户端/服务器数据库（例如 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]）一起使用时，可以更有效地一次提取多行。</span><span class="sxs-lookup"><span data-stu-id="64b55-105">When you are working with a client/server database such as Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it is more efficient to fetch several rows at a time.</span></span> <span data-ttu-id="64b55-106">提取时返回的行数称为行集大小，并使用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_ROW_ARRAY_SIZE 来指定。</span><span class="sxs-lookup"><span data-stu-id="64b55-106">The number of rows returned on a fetch is called the rowset size and is specified by using the SQL_ATTR_ROW_ARRAY_SIZE of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 <span data-ttu-id="64b55-107">行集大小大于 1 的游标称为块状游标。</span><span class="sxs-lookup"><span data-stu-id="64b55-107">Cursors with a rowset size greater than 1 are called block cursors.</span></span>  
  
 <span data-ttu-id="64b55-108">有两种方法可用于绑定块状游标的结果集列：</span><span class="sxs-lookup"><span data-stu-id="64b55-108">There are two options for binding result set columns for block cursors:</span></span>  
  
-   <span data-ttu-id="64b55-109">按列绑定</span><span class="sxs-lookup"><span data-stu-id="64b55-109">Column-wise binding</span></span>  
  
     <span data-ttu-id="64b55-110">每个列绑定到一个变量数组。</span><span class="sxs-lookup"><span data-stu-id="64b55-110">Each column is bound to an array of variables.</span></span> <span data-ttu-id="64b55-111">每个数组所具有的元素数目等于行集大小。</span><span class="sxs-lookup"><span data-stu-id="64b55-111">Each array has the same number of elements as the rowset size.</span></span>  
  
-   <span data-ttu-id="64b55-112">按行绑定</span><span class="sxs-lookup"><span data-stu-id="64b55-112">Row-wise binding</span></span>  
  
     <span data-ttu-id="64b55-113">使用将所有列的数据和指示符保存在一个行中的结构来构建数组。</span><span class="sxs-lookup"><span data-stu-id="64b55-113">An array is built using structures that hold the data and indicators for all the columns in a row.</span></span> <span data-ttu-id="64b55-114">数组所具有的结构数目等于行集大小。</span><span class="sxs-lookup"><span data-stu-id="64b55-114">The array has the same number of structures as the rowset size.</span></span>  
  
 <span data-ttu-id="64b55-115">使用按列绑定或按行绑定时，对**SQLFetch**或**SQLFetchScroll**的每个调用都将使用检索到的行集中的数据填充绑定数组。</span><span class="sxs-lookup"><span data-stu-id="64b55-115">When either column-wise or row-wise binding is used, each call to **SQLFetch** or **SQLFetchScroll** fills the bound arrays with data from the rowset retrieved.</span></span>  
  
 <span data-ttu-id="64b55-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)也可用于从块游标中检索列数据。</span><span class="sxs-lookup"><span data-stu-id="64b55-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) can also be used to retrieve column data from a block cursor.</span></span> <span data-ttu-id="64b55-117">由于**SQLGetData**一次只处理一行，因此在调用**SQLGetData**之前，必须调用**SQLSetPos**将行集中的特定行设置为当前行。</span><span class="sxs-lookup"><span data-stu-id="64b55-117">Because **SQLGetData** works one row at a time, **SQLSetPos** must be called to set a specific row in the rowset as the current row before calling **SQLGetData**.</span></span>  
  
 <span data-ttu-id="64b55-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序通过使用行集快速检索整个结果集提供优化。</span><span class="sxs-lookup"><span data-stu-id="64b55-118">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers an optimization using rowsets to retrieve a whole result set quickly.</span></span> <span data-ttu-id="64b55-119">若要使用此优化，请在调用**SQLExecDirect**或**SQLExecute**时，将游标属性设置为默认 (只进、只读、行集大小 = 1) 。</span><span class="sxs-lookup"><span data-stu-id="64b55-119">To use this optimization, set the cursor attributes to their defaults (forward-only, read-only, rowset size = 1) at the time **SQLExecDirect** or **SQLExecute** is called.</span></span> <span data-ttu-id="64b55-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序设置默认的结果集。</span><span class="sxs-lookup"><span data-stu-id="64b55-120">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver sets up a default result set.</span></span> <span data-ttu-id="64b55-121">在不需要滚动的情况下将结果传输到客户端时，该优化功能比服务器游标更有效。</span><span class="sxs-lookup"><span data-stu-id="64b55-121">This is more efficient than server cursors when transferring results to the client without scrolling.</span></span> <span data-ttu-id="64b55-122">执行语句后，请增加行集大小并使用按列绑定或按行绑定。</span><span class="sxs-lookup"><span data-stu-id="64b55-122">After the statement has been executed, increase the rowset size and use either column-wise or row-wise binding.</span></span> <span data-ttu-id="64b55-123">这允许 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用默认结果集将结果行高效地发送到客户端，而 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE client ODBC 驱动程序会持续从客户端上的网络缓冲区中提取行。</span><span class="sxs-lookup"><span data-stu-id="64b55-123">This lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] use a default result set to send result rows efficiently to the client, while the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver continuously pulls rows from the network buffers on the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b55-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64b55-124">See Also</span></span>  
 [<span data-ttu-id="64b55-125">游标属性</span><span class="sxs-lookup"><span data-stu-id="64b55-125">Cursor Properties</span></span>](cursor-properties.md)  
  
  
