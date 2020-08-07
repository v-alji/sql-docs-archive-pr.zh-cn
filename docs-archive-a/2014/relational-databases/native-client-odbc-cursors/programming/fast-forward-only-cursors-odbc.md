---
title: ODBC)  (快速只进游标 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: rothja
ms.author: jroth
ms.openlocfilehash: de8d82a0c72ad51741a3785fba2910f691028cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589046"
---
# <a name="fast-forward-only-cursors-odbc"></a><span data-ttu-id="d736d-102">快速只进游标 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d736d-102">Fast Forward-Only Cursors (ODBC)</span></span>
  <span data-ttu-id="d736d-103">当连接到实例时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序支持只进、只读游标的性能优化。</span><span class="sxs-lookup"><span data-stu-id="d736d-103">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports performance optimizations for forward-only, read-only cursors.</span></span> <span data-ttu-id="d736d-104">快速只进游标由驱动程序和服务器采用近似于默认结果集的方式在内部实现。</span><span class="sxs-lookup"><span data-stu-id="d736d-104">Fast forward-only cursors are implemented internally by the driver and server in a manner very similar to default result sets.</span></span> <span data-ttu-id="d736d-105">除高性能之外，快速只进游标还具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="d736d-105">Besides having high performance, fast forward-only cursors also have these characteristics:</span></span>  
  
-   <span data-ttu-id="d736d-106">不支持[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 。</span><span class="sxs-lookup"><span data-stu-id="d736d-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) is not supported.</span></span> <span data-ttu-id="d736d-107">结果集列必须绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="d736d-107">The result set columns must be bound to program variables.</span></span>  
  
-   <span data-ttu-id="d736d-108">当检测到达游标末尾时，服务器自动关闭游标。</span><span class="sxs-lookup"><span data-stu-id="d736d-108">The server automatically closes the cursor when the end of the cursor is detected.</span></span> <span data-ttu-id="d736d-109">应用程序仍必须 SQL_CLOSE) 调用[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)或[SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) (，但驱动程序不必向服务器发送关闭请求。</span><span class="sxs-lookup"><span data-stu-id="d736d-109">The application must still call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), but the driver does not have to send the close request to the server.</span></span> <span data-ttu-id="d736d-110">这就省去了通过网络往返服务器。</span><span class="sxs-lookup"><span data-stu-id="d736d-110">This saves a roundtrip across the network to the server.</span></span>  
  
 <span data-ttu-id="d736d-111">应用程序使用驱动程序特定的语句属性 SQL_SOPT_SS_CURSOR_OPTIONS 请求快速只进游标。</span><span class="sxs-lookup"><span data-stu-id="d736d-111">The application requests fast forward-only cursors using the driver-specific statement attribute SQL_SOPT_SS_CURSOR_OPTIONS.</span></span> <span data-ttu-id="d736d-112">如果设置为 SQL_CO_FFO，则启用快速只进游标，不启用自动提取。</span><span class="sxs-lookup"><span data-stu-id="d736d-112">When set to SQL_CO_FFO, fast forward-only cursors are enabled without autofetch.</span></span> <span data-ttu-id="d736d-113">如果设置为 SQL_CO_FFO_AF，则同时启用自动提取选项。</span><span class="sxs-lookup"><span data-stu-id="d736d-113">When set to SQL_CO_FFO_AF, the autofetch option is also enabled.</span></span> <span data-ttu-id="d736d-114">有关自动提取的详细信息，请参阅将[自动提取与 ODBC 游标一起使用](using-autofetch-with-odbc-cursors.md)。</span><span class="sxs-lookup"><span data-stu-id="d736d-114">For more information about autofetch, see [Using Autofetch with ODBC Cursors](using-autofetch-with-odbc-cursors.md).</span></span>  
  
 <span data-ttu-id="d736d-115">启用了自动提取的快速只进游标可用于检索较小的结果集，只需进行一次服务器往返。</span><span class="sxs-lookup"><span data-stu-id="d736d-115">Fast forward-only cursors with autofetch can be used to retrieve a small result set with only one roundtrip to the server.</span></span> <span data-ttu-id="d736d-116">在这些步骤中， *n*是要返回的行数：</span><span class="sxs-lookup"><span data-stu-id="d736d-116">In these steps, *n* is the number of rows to be returned:</span></span>  
  
1.  <span data-ttu-id="d736d-117">将 SQL_SOPT_SS_CURSOR_OPTIONS 设置为 SQL_CO_FFO_AF。</span><span class="sxs-lookup"><span data-stu-id="d736d-117">Set SQL_SOPT_SS_CURSOR_OPTIONS to SQL_CO_FFO_AF.</span></span>  
  
2.  <span data-ttu-id="d736d-118">将 SQL_ATTR_ROW_ARRAY_SIZE 设置为*n* + 1。</span><span class="sxs-lookup"><span data-stu-id="d736d-118">Set SQL_ATTR_ROW_ARRAY_SIZE to *n* + 1.</span></span>  
  
3.  <span data-ttu-id="d736d-119">如果在实际) *n* + 1 行时，将结果列绑定到*n* + 1 个元素的数组 (为 safe。</span><span class="sxs-lookup"><span data-stu-id="d736d-119">Bind the result columns to arrays of *n* + 1 elements (to be safe if *n* + 1 rows are actually fetched).</span></span>  
  
4.  <span data-ttu-id="d736d-120">用**SQLExecDirect**或**SQLExecute**打开游标。</span><span class="sxs-lookup"><span data-stu-id="d736d-120">Open the cursor with either **SQLExecDirect** or **SQLExecute**.</span></span>  
  
5.  <span data-ttu-id="d736d-121">如果返回状态为 SQL_SUCCESS，则调用**SQLFreeStmt**或**SQLCloseCursor**以关闭游标。</span><span class="sxs-lookup"><span data-stu-id="d736d-121">If the return status is SQL_SUCCESS, then call **SQLFreeStmt** or **SQLCloseCursor** to close the cursor.</span></span> <span data-ttu-id="d736d-122">所有行数据将位于绑定程序变量中。</span><span class="sxs-lookup"><span data-stu-id="d736d-122">All data for the rows will be in the bound program variables.</span></span>  
  
 <span data-ttu-id="d736d-123">执行这些步骤后， **SQLExecDirect**或**SQLExecute**将发送一个已启用自动提取选项的游标打开请求。</span><span class="sxs-lookup"><span data-stu-id="d736d-123">With these steps, the **SQLExecDirect** or **SQLExecute** sends a cursor open request with the autofetch option enabled.</span></span> <span data-ttu-id="d736d-124">对于来自客户端的单个请求，服务器执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d736d-124">On that single request from the client, the server:</span></span>  
  
-   <span data-ttu-id="d736d-125">打开游标。</span><span class="sxs-lookup"><span data-stu-id="d736d-125">Opens the cursor.</span></span>  
  
-   <span data-ttu-id="d736d-126">生成结果集并将行发送给客户端。</span><span class="sxs-lookup"><span data-stu-id="d736d-126">Builds the result set and sends the rows to the client.</span></span>  
  
-   <span data-ttu-id="d736d-127">由于行集大小设置为比结果集中的行数大 1，因此服务器检测到游标末尾并关闭游标。</span><span class="sxs-lookup"><span data-stu-id="d736d-127">Because the rowset size was set to 1 more than the number of rows in the result set, the server detects the end of the cursor and closes the cursor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d736d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d736d-128">See Also</span></span>  
 [<span data-ttu-id="d736d-129">ODBC&#41;的游标编程详细信息 &#40;</span><span class="sxs-lookup"><span data-stu-id="d736d-129">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
