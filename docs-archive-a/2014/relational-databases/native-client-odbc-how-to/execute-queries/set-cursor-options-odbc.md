---
title: " (ODBC) 设置游标选项 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: rothja
ms.author: jroth
ms.openlocfilehash: 877c2596c87ce50295a15912493661c6dd4e0305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692901"
---
# <a name="set-cursor-options-odbc"></a><span data-ttu-id="4989c-102">设置游标选项 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="4989c-102">Set Cursor Options (ODBC)</span></span>
  <span data-ttu-id="4989c-103">若要设置游标选项，请调用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)设置或[SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md)以获取控制游标行为的语句选项。</span><span class="sxs-lookup"><span data-stu-id="4989c-103">To set cursor options, Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set or [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) to get the statement options that control cursor behavior.</span></span>  
  
|<span data-ttu-id="4989c-104">*特性*</span><span class="sxs-lookup"><span data-stu-id="4989c-104">*Attribute*</span></span>|<span data-ttu-id="4989c-105">指定</span><span class="sxs-lookup"><span data-stu-id="4989c-105">Specifies</span></span>|  
|-----------------|---------------|  
|<span data-ttu-id="4989c-106">SQL_ATTR_CURSOR_TYPE</span><span class="sxs-lookup"><span data-stu-id="4989c-106">SQL_ATTR_CURSOR_TYPE</span></span>|<span data-ttu-id="4989c-107">只进、静态、动态或由键集驱动的游标类型</span><span class="sxs-lookup"><span data-stu-id="4989c-107">Cursor type of forward-only, static, dynamic, or keyset-driven</span></span>|  
|<span data-ttu-id="4989c-108">SQL_ATTR_CONCURRENCY</span><span class="sxs-lookup"><span data-stu-id="4989c-108">SQL_ATTR_CONCURRENCY</span></span>|<span data-ttu-id="4989c-109">只读、锁定、乐观使用时间戳或乐观使用值的并发控制选项</span><span class="sxs-lookup"><span data-stu-id="4989c-109">Concurrency control option of read-only, locking, optimistic using timestamps, or optimistic using values</span></span>|  
|<span data-ttu-id="4989c-110">SQL_ATTR_ROW_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="4989c-110">SQL_ATTR_ROW_ARRAY_SIZE</span></span>|<span data-ttu-id="4989c-111">在每个提取中检索的行数</span><span class="sxs-lookup"><span data-stu-id="4989c-111">Number of rows retrieved in each fetch</span></span>|  
|<span data-ttu-id="4989c-112">SQL_ATTR_CURSOR_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="4989c-112">SQL_ATTR_CURSOR_SENSITIVITY</span></span>|<span data-ttu-id="4989c-113">显示或不显示由其他连接对游标行进行的更新的游标</span><span class="sxs-lookup"><span data-stu-id="4989c-113">Cursor that does or does not show updates to cursor rows made by other connections</span></span>|  
|<span data-ttu-id="4989c-114">SQL_ATTR_CURSOR_SCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="4989c-114">SQL_ATTR_CURSOR_SCROLLABLE</span></span>|<span data-ttu-id="4989c-115">可以向前和向后滚动的游标</span><span class="sxs-lookup"><span data-stu-id="4989c-115">Cursor that can be scrolled forward and backward</span></span>|  
  
 <span data-ttu-id="4989c-116">这些属性（只进、只读、行集大小为 1）的默认值不使用服务器游标。</span><span class="sxs-lookup"><span data-stu-id="4989c-116">The default values for these attributes (forward-only, read-only, rowset size of 1) do not use server cursors.</span></span> <span data-ttu-id="4989c-117">若要使用服务器游标，必须将这些属性中的至少一个属性设置为非默认值，并且所执行的语句必须是包含单个 SELECT 语句的单个 SELECT 语句或存储过程。</span><span class="sxs-lookup"><span data-stu-id="4989c-117">To use server cursors, at least one of these attributes must be set to a value other than the default, and the statement being executed must be a single SELECT statement or a stored procedure that contains a single SELECT statement.</span></span> <span data-ttu-id="4989c-118">使用服务器游标时，SELECT 语句无法使用服务器游标不支持的子句：COMPUTE、COMPUTE BY、FOR BROWSE 和 INTO。</span><span class="sxs-lookup"><span data-stu-id="4989c-118">When using server cursors, SELECT statements cannot use clauses not supported by server cursors: COMPUTE, COMPUTE BY, FOR BROWSE, and INTO.</span></span>  
  
 <span data-ttu-id="4989c-119">您可以通过设置 SQL_ATTR_CURSOR_TYPE 和 SQL_ATTR_CONCURRENCY 或设置 SQL_ATTR_CURSOR_SENSITIVITY 和 SQL_ATTR_CURSOR_SCROLLABLE 来控制使用的游标类型。</span><span class="sxs-lookup"><span data-stu-id="4989c-119">You can control the type of cursor used either by setting SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY, or by setting SQL_ATTR_CURSOR_SENSITIVITY and SQL_ATTR_CURSOR_SCROLLABLE.</span></span> <span data-ttu-id="4989c-120">不应将指定游标行为的两种方法混用。</span><span class="sxs-lookup"><span data-stu-id="4989c-120">You should not mix the two methods of specifying cursor behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4989c-121">示例</span><span class="sxs-lookup"><span data-stu-id="4989c-121">Example</span></span>  
 <span data-ttu-id="4989c-122">以下示例分配一个语句句柄，之后以行版本控制乐观并发方式设置动态游标类型，然后执行 SELECT。</span><span class="sxs-lookup"><span data-stu-id="4989c-122">The following sample allocates a statement handle, sets a dynamic cursor type with row versioning optimistic concurrency, and then executes a SELECT.</span></span>  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a><span data-ttu-id="4989c-123">示例</span><span class="sxs-lookup"><span data-stu-id="4989c-123">Example</span></span>  
 <span data-ttu-id="4989c-124">以下示例分配一个语句句柄，之后设置可滚动、敏感游标，然后执行 SELECT</span><span class="sxs-lookup"><span data-stu-id="4989c-124">The following sample allocates a statement handle, sets a scrollable, sensitive cursor, and then executes a SELECT</span></span>  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4989c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4989c-125">See Also</span></span>  
 [<span data-ttu-id="4989c-126">&#40;ODBC&#41;执行查询操作指南主题</span><span class="sxs-lookup"><span data-stu-id="4989c-126">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
