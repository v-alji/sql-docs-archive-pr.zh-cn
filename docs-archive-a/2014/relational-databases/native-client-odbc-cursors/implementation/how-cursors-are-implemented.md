---
title: 如何实现游标 |Microsoft Docs
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
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
author: rothja
ms.author: jroth
ms.openlocfilehash: 18995355b825d9cb1e62b4794429b5e98ef2b472
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580268"
---
# <a name="how-cursors-are-implemented"></a><span data-ttu-id="e31ea-102">如何实现游标</span><span class="sxs-lookup"><span data-stu-id="e31ea-102">How Cursors Are Implemented</span></span>
  <span data-ttu-id="e31ea-103">ODBC 应用程序通过在执行 SQL 语句之前设置一个或多个语句属性来控制游标的行为。</span><span class="sxs-lookup"><span data-stu-id="e31ea-103">ODBC applications control the behavior of a cursor by setting one or more statement attributes before executing an SQL statement.</span></span> <span data-ttu-id="e31ea-104">ODBC 采用以下两种不同方式来指定游标的特征：</span><span class="sxs-lookup"><span data-stu-id="e31ea-104">ODBC has two different ways to specify the characteristics of a cursor:</span></span>  
  
-   <span data-ttu-id="e31ea-105">游标类型</span><span class="sxs-lookup"><span data-stu-id="e31ea-105">Cursor type</span></span>  
  
     <span data-ttu-id="e31ea-106">游标类型使用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_CURSOR_TYPE 属性进行设置。</span><span class="sxs-lookup"><span data-stu-id="e31ea-106">Cursor types are set using the SQL_ATTR_CURSOR_TYPE attribute of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="e31ea-107">ODBC 游标类型包括只进、静态、由键集驱动、混合和动态。</span><span class="sxs-lookup"><span data-stu-id="e31ea-107">The ODBC cursor types are forward-only, static, keyset-driven, mixed, and dynamic.</span></span> <span data-ttu-id="e31ea-108">设置游标类型是在 ODBC 中指定游标的原始方法。</span><span class="sxs-lookup"><span data-stu-id="e31ea-108">Setting the cursor type was the original method of specifying cursors in ODBC.</span></span>  
  
-   <span data-ttu-id="e31ea-109">游标行为</span><span class="sxs-lookup"><span data-stu-id="e31ea-109">Cursor behavior</span></span>  
  
     <span data-ttu-id="e31ea-110">游标行为是使用**SQLSetStmtAttr**的 SQL_ATTR_CURSOR_SCROLLABLE 和 SQL_ATTR_CURSOR_SENSITIVITY 属性设置的。</span><span class="sxs-lookup"><span data-stu-id="e31ea-110">Cursor behavior is set using the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY attributes of **SQLSetStmtAttr**.</span></span> <span data-ttu-id="e31ea-111">这些属性根据在 ISO 标准中为 DECLARE CURSOR 语句定义的 SCROLL 和 SENSITIVE 关键字建模。</span><span class="sxs-lookup"><span data-stu-id="e31ea-111">These attributes are modeled on the SCROLL and SENSITIVE keywords defined for the DECLARE CURSOR statement in ISO standards.</span></span> <span data-ttu-id="e31ea-112">这两个 ISO 选项是在 ODBC 版本 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e31ea-112">These two ISO options were introduced in ODBC version 3.0.</span></span>  
  
 <span data-ttu-id="e31ea-113">应使用上述两种方法之一指定 ODBC 游标的特征，首选方法为使用 ODBC 游标类型。</span><span class="sxs-lookup"><span data-stu-id="e31ea-113">The characteristics of an ODBC cursor should be specified using either one or the other of these two methods, with the preference being to use the ODBC cursor types.</span></span>  
  
 <span data-ttu-id="e31ea-114">除设置游标类型以外，ODBC 应用程序还会设置其他选项，例如每次提取返回的行数、并发选项和事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="e31ea-114">In addition to setting the type of a cursor, ODBC applications also set other options, such as the number of rows returned on each fetch, concurrency options, and transaction isolation levels.</span></span> <span data-ttu-id="e31ea-115">可以针对 ODBC 样式的游标（只进、静态、由键集驱动、混合和动态）或 ISO 样式的游标（可滚动性和敏感性）设置这些选项。</span><span class="sxs-lookup"><span data-stu-id="e31ea-115">These options can be set for either ODBC-style cursors (forward-only, static, keyset-driven, mixed, and dynamic) or ISO style cursors (scrollability and sensitivity).</span></span>  
  
 <span data-ttu-id="e31ea-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序支持多种方法以物理方式实现各种类型的游标。</span><span class="sxs-lookup"><span data-stu-id="e31ea-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports several ways to physically implement the various types of cursors.</span></span> <span data-ttu-id="e31ea-117">该驱动程序使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认结果集实现某些类型的游标，并将其他类型的游标作为服务器游标或使用 ODBC 游标库实现。</span><span class="sxs-lookup"><span data-stu-id="e31ea-117">The driver implements some types of cursors using a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set; it implements others as server cursors or by using the ODBC Cursor Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e31ea-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="e31ea-118">In This Section</span></span>  
  
-   [<span data-ttu-id="e31ea-119">使用 SQL Server 默认结果集</span><span class="sxs-lookup"><span data-stu-id="e31ea-119">Using SQL Server Default Result Sets</span></span>](using-sql-server-default-result-sets.md)  
  
-   [<span data-ttu-id="e31ea-120">使用服务器游标</span><span class="sxs-lookup"><span data-stu-id="e31ea-120">Using Server Cursors</span></span>](using-server-cursors.md)  
  
-   [<span data-ttu-id="e31ea-121">ODBC 游标库</span><span class="sxs-lookup"><span data-stu-id="e31ea-121">ODBC Cursor Library</span></span>](odbc-cursor-library.md)  
  
## <a name="see-also"></a><span data-ttu-id="e31ea-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e31ea-122">See Also</span></span>  
 [<span data-ttu-id="e31ea-123">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="e31ea-123">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
