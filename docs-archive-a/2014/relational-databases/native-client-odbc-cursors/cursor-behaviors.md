---
title: 游标行为 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
author: rothja
ms.author: jroth
ms.openlocfilehash: 89c7c4e9a8dcffe03dd12f8013d5ed43810547f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586640"
---
# <a name="cursor-behaviors"></a><span data-ttu-id="4728f-102">游标行为</span><span class="sxs-lookup"><span data-stu-id="4728f-102">Cursor Behaviors</span></span>
  <span data-ttu-id="4728f-103">ODBC 支持通过指定游标的可滚动性和敏感性来指定其行为的 ISO 选项。</span><span class="sxs-lookup"><span data-stu-id="4728f-103">ODBC supports the ISO options for specifying the behavior of cursors by specifying their scrollability and sensitivity.</span></span> <span data-ttu-id="4728f-104">这些行为是通过在对[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)的调用上设置 SQL_ATTR_CURSOR_SCROLLABLE 和 SQL_ATTR_CURSOR_SENSITIVITY 选项来指定的。</span><span class="sxs-lookup"><span data-stu-id="4728f-104">These behaviors are specified by setting the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY options on a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="4728f-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序通过请求具有以下特征的服务器游标来实现这些选项。</span><span class="sxs-lookup"><span data-stu-id="4728f-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver implements these options by requesting server cursors with the following characteristics.</span></span>  
  
|<span data-ttu-id="4728f-106">游标行为设置</span><span class="sxs-lookup"><span data-stu-id="4728f-106">Cursor behavior settings</span></span>|<span data-ttu-id="4728f-107">请求的服务器游标的特征</span><span class="sxs-lookup"><span data-stu-id="4728f-107">Server cursor characteristics requested</span></span>|  
|------------------------------|---------------------------------------------|  
|<span data-ttu-id="4728f-108">SQL_SCROLLABLE 和 SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="4728f-108">SQL_SCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="4728f-109">由键集驱动的游标和基于版本的乐观并发</span><span class="sxs-lookup"><span data-stu-id="4728f-109">Keyset-driven cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="4728f-110">SQL_SCROLLABLE 和 SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="4728f-110">SQL_SCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="4728f-111">静态游标和只读并发</span><span class="sxs-lookup"><span data-stu-id="4728f-111">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="4728f-112">SQL_SCROLLABLE 和 SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="4728f-112">SQL_SCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="4728f-113">静态游标和只读并发</span><span class="sxs-lookup"><span data-stu-id="4728f-113">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="4728f-114">SQL_NONSCROLLABLE 和 SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="4728f-114">SQL_NONSCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="4728f-115">只进游标和基于版本的乐观并发</span><span class="sxs-lookup"><span data-stu-id="4728f-115">Forward-only cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="4728f-116">SQL_NONSCROLLABLE 和 SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="4728f-116">SQL_NONSCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="4728f-117">默认结果集（只进，只读）</span><span class="sxs-lookup"><span data-stu-id="4728f-117">Default result set (forward-only, read-only)</span></span>|  
|<span data-ttu-id="4728f-118">SQL_NONSCROLLABLE 和 SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="4728f-118">SQL_NONSCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="4728f-119">默认结果集（只进，只读）</span><span class="sxs-lookup"><span data-stu-id="4728f-119">Default result set (forward-only, read-only)</span></span>|  
  
 <span data-ttu-id="4728f-120">基于版本的乐观并发要求基础表中有一个**时间戳**列。</span><span class="sxs-lookup"><span data-stu-id="4728f-120">Version-based optimistic concurrency requires a **timestamp** column in the underlying table.</span></span> <span data-ttu-id="4728f-121">如果对没有**时间戳**列的表请求基于版本的乐观并发控制，则服务器将使用基于值的乐观并发。</span><span class="sxs-lookup"><span data-stu-id="4728f-121">If version-based optimistic concurrency control is requested on a table that does not have a **timestamp** column, the server uses values-based optimistic concurrency.</span></span>  
  
## <a name="scrollability"></a><span data-ttu-id="4728f-122">可滚动性</span><span class="sxs-lookup"><span data-stu-id="4728f-122">Scrollability</span></span>  
 <span data-ttu-id="4728f-123">当 SQL_ATTR_CURSOR_SCROLLABLE 设置为 SQL_SCROLLABLE 时，游标支持[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)的*FetchOrientation*参数的所有不同值。</span><span class="sxs-lookup"><span data-stu-id="4728f-123">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_SCROLLABLE, the cursor supports all the different values for the *FetchOrientation* parameter of [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="4728f-124">当 SQL_ATTR_CURSOR_SCROLLABLE 设置为 SQL_NONSCROLLABLE 时，游标仅支持 SQL_FETCH_NEXT 的*FetchOrientation*值。</span><span class="sxs-lookup"><span data-stu-id="4728f-124">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_NONSCROLLABLE, the cursor only supports a *FetchOrientation* value of SQL_FETCH_NEXT.</span></span>  
  
## <a name="sensitivity"></a><span data-ttu-id="4728f-125">敏感性</span><span class="sxs-lookup"><span data-stu-id="4728f-125">Sensitivity</span></span>  
 <span data-ttu-id="4728f-126">将 SQL_ATTR_CURSOR_SENSITIVITY 设置为 SQL_SENSITIVE 时，游标可以反映由当前用户所做的或由其他用户提交的数据修改。</span><span class="sxs-lookup"><span data-stu-id="4728f-126">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_SENSITIVE, the cursor reflects data modifications made by the current user or committed by other users.</span></span> <span data-ttu-id="4728f-127">将 SQL_ATTR_CURSOR_SENSITIVITY 设置为 SQL_INSENSITIVE 时，游标不能反映数据修改。</span><span class="sxs-lookup"><span data-stu-id="4728f-127">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_INSENSITIVE, the cursor does not reflect data modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4728f-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4728f-128">See Also</span></span>  
 [<span data-ttu-id="4728f-129">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="4728f-129">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
