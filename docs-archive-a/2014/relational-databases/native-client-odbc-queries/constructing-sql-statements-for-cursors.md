---
title: 为游标构造 SQL 语句 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
author: rothja
ms.author: jroth
ms.openlocfilehash: b0fe0831b97c13c5d20067386f4e9d8c97ee19ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577611"
---
# <a name="constructing-sql-statements-for-cursors"></a><span data-ttu-id="e1917-102">为游标构造 SQL 语句</span><span class="sxs-lookup"><span data-stu-id="e1917-102">Constructing SQL Statements for Cursors</span></span>
  <span data-ttu-id="e1917-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序使用服务器游标来实现 ODBC 规范中定义的游标功能。</span><span class="sxs-lookup"><span data-stu-id="e1917-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses server cursors to implement the cursor functionality defined in the ODBC specification.</span></span> <span data-ttu-id="e1917-104">ODBC 应用程序通过使用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)设置不同的语句特性来控制游标行为。</span><span class="sxs-lookup"><span data-stu-id="e1917-104">An ODBC application controls the cursor behavior by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) to set different statement attributes.</span></span> <span data-ttu-id="e1917-105">以下为属性及其默认值。</span><span class="sxs-lookup"><span data-stu-id="e1917-105">These are the attributes and their defaults.</span></span>  
  
|<span data-ttu-id="e1917-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="e1917-106">Attribute</span></span>|<span data-ttu-id="e1917-107">默认</span><span class="sxs-lookup"><span data-stu-id="e1917-107">Default</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="e1917-108">SQL_ATTR_CONCURRENCY</span><span class="sxs-lookup"><span data-stu-id="e1917-108">SQL_ATTR_CONCURRENCY</span></span>|<span data-ttu-id="e1917-109">SQL_CONCUR_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="e1917-109">SQL_CONCUR_READ_ONLY</span></span>|  
|<span data-ttu-id="e1917-110">SQL_ATTR_CURSOR_TYPE</span><span class="sxs-lookup"><span data-stu-id="e1917-110">SQL_ATTR_CURSOR_TYPE</span></span>|<span data-ttu-id="e1917-111">SQL_CURSOR_FORWARD_ONLY</span><span class="sxs-lookup"><span data-stu-id="e1917-111">SQL_CURSOR_FORWARD_ONLY</span></span>|  
|<span data-ttu-id="e1917-112">SQL_ATTR_CURSOR_SCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="e1917-112">SQL_ATTR_CURSOR_SCROLLABLE</span></span>|<span data-ttu-id="e1917-113">SQL_NONSCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="e1917-113">SQL_NONSCROLLABLE</span></span>|  
|<span data-ttu-id="e1917-114">SQL_ATTR_CURSOR_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="e1917-114">SQL_ATTR_CURSOR_SENSITIVITY</span></span>|<span data-ttu-id="e1917-115">SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="e1917-115">SQL_UNSPECIFIED</span></span>|  
|<span data-ttu-id="e1917-116">SQL_ATTR_ROW_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="e1917-116">SQL_ATTR_ROW_ARRAY_SIZE</span></span>|<span data-ttu-id="e1917-117">1</span><span class="sxs-lookup"><span data-stu-id="e1917-117">1</span></span>|  
  
 <span data-ttu-id="e1917-118">当执行 SQL 语句时，将这些选项设置为默认值时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序不使用服务器游标来实现结果集; 而是使用默认结果集。</span><span class="sxs-lookup"><span data-stu-id="e1917-118">When these options are set to their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not use a server cursor to implement the result set; instead, it uses a default result set.</span></span> <span data-ttu-id="e1917-119">如果在执行 SQL 语句时，这些选项中的任何一种都已更改为默认值，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序会尝试使用服务器游标来实现结果集。</span><span class="sxs-lookup"><span data-stu-id="e1917-119">If any of these options are changed from their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to use a server cursor to implement the result set.</span></span>  
  
 <span data-ttu-id="e1917-120">默认结果集支持所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="e1917-120">Default result sets support all of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="e1917-121">对使用默认结果集时可以执行的 SQL 语句类型没有限制。</span><span class="sxs-lookup"><span data-stu-id="e1917-121">There are no restrictions on the types of SQL statements that can be executed when using a default result set.</span></span>  
  
 <span data-ttu-id="e1917-122">服务器游标不支持所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="e1917-122">Server cursors do not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="e1917-123">服务器游标不支持生成多个结果集的任何 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="e1917-123">Server cursors do not support any SQL statement that generates multiple result sets.</span></span>  
  
 <span data-ttu-id="e1917-124">服务器游标不支持以下语句类型：</span><span class="sxs-lookup"><span data-stu-id="e1917-124">The following types of statements are not supported by server cursors:</span></span>  
  
-   <span data-ttu-id="e1917-125">批处理</span><span class="sxs-lookup"><span data-stu-id="e1917-125">Batches</span></span>  
  
     <span data-ttu-id="e1917-126">SQL 语句从两个或多个单独的 SQL SELECT 语句中生成，例如：</span><span class="sxs-lookup"><span data-stu-id="e1917-126">SQL statements built from two or more individual SQL SELECT statements, for example:</span></span>  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   <span data-ttu-id="e1917-127">带有多个 SELECT 语句的存储过程</span><span class="sxs-lookup"><span data-stu-id="e1917-127">Stored procedures with multiple SELECT statements</span></span>  
  
     <span data-ttu-id="e1917-128">执行包含多个 SELECT 语句的存储过程的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="e1917-128">SQL statements that execute a stored procedure containing more than one SELECT statement.</span></span> <span data-ttu-id="e1917-129">这包括填充参数或变量的 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="e1917-129">This includes SELECT statements that fill parameters or variables.</span></span>  
  
-   <span data-ttu-id="e1917-130">关键字</span><span class="sxs-lookup"><span data-stu-id="e1917-130">Keywords</span></span>  
  
     <span data-ttu-id="e1917-131">包含关键字 FOR BROWSE 或 INTO 的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="e1917-131">SQL statements containing the keywords FOR BROWSE, or INTO.</span></span>  
  
 <span data-ttu-id="e1917-132">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，如果使用服务器游标执行符合这些条件中任意一条的 SQL 语句，则服务器游标将隐式转换为默认结果集。</span><span class="sxs-lookup"><span data-stu-id="e1917-132">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if an SQL statement that matches any of these conditions is executed with a server cursor, the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="e1917-133">**SQLExecDirect**或**SQLExecute**返回 SQL_SUCCESS_WITH_INFO 后，游标属性将设置回其默认设置。</span><span class="sxs-lookup"><span data-stu-id="e1917-133">After **SQLExecDirect** or **SQLExecute** returns SQL_SUCCESS_WITH_INFO, the cursor attributes will be set back to their default settings.</span></span>  
  
 <span data-ttu-id="e1917-134">不适合以上类别的 SQL 语句可以通过任何语句属性设置执行，它们通过默认结果集或服务器游标均可正常执行。</span><span class="sxs-lookup"><span data-stu-id="e1917-134">SQL statements that do not fit the categories above can be executed with any statement attribute settings; they work equally well with either a default result set or a server cursor.</span></span>  
  
## <a name="errors"></a><span data-ttu-id="e1917-135">错误</span><span class="sxs-lookup"><span data-stu-id="e1917-135">Errors</span></span>  
 <span data-ttu-id="e1917-136">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 和更高版本中，尝试执行生成多个结果集的语句将生成 SQL_SUCCESS_WITH INFO 和下列消息：</span><span class="sxs-lookup"><span data-stu-id="e1917-136">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 and later, an attempt to execute a statement that produces multiple result sets generates SQL_SUCCESS_WITH INFO and the following message:</span></span>  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 <span data-ttu-id="e1917-137">接收此消息的 ODBC 应用程序可以调用[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)来确定当前游标设置。</span><span class="sxs-lookup"><span data-stu-id="e1917-137">ODBC applications receiving this message can call [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) to determine the current cursor settings.</span></span>  
  
 <span data-ttu-id="e1917-138">使用服务器游标时尝试执行带有多个 SELECT 语句的过程将产生下列错误：</span><span class="sxs-lookup"><span data-stu-id="e1917-138">An attempt to execute a procedure with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 <span data-ttu-id="e1917-139">使用服务器游标时尝试执行带有多个 SELECT 语句的批处理将产生下列错误：</span><span class="sxs-lookup"><span data-stu-id="e1917-139">An attempt to execute a batch with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 <span data-ttu-id="e1917-140">ODBC 应用程序收到这些错误后，在尝试执行该语句前必须将所有游标语句属性重置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="e1917-140">ODBC applications receiving these errors must reset all the cursor statement attributes to their defaults before attempting to execute the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1917-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1917-141">See Also</span></span>  
 [<span data-ttu-id="e1917-142">&#40;ODBC&#41;执行查询</span><span class="sxs-lookup"><span data-stu-id="e1917-142">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
