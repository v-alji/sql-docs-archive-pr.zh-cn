---
title: 在 ODBC 中为行加书签 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: rothja
ms.author: jroth
ms.openlocfilehash: def05f478c16dcbcdc91771925a11b0b91da2e9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692920"
---
# <a name="bookmarking-rows-in-odbc"></a><span data-ttu-id="465f3-102">在 ODBC 中为行加书签</span><span class="sxs-lookup"><span data-stu-id="465f3-102">Bookmarking Rows in ODBC</span></span>
  <span data-ttu-id="465f3-103">书签是用于标识数据行的值。</span><span class="sxs-lookup"><span data-stu-id="465f3-103">A bookmark is a value used to identify a row of data.</span></span> <span data-ttu-id="465f3-104">只有驱动程序或数据源才知道书签值的含义。</span><span class="sxs-lookup"><span data-stu-id="465f3-104">The meaning of the bookmark value is known only to the driver or data source.</span></span> <span data-ttu-id="465f3-105">例如，书签可能与行号一样简单，也可能与磁盘地址一样复杂。</span><span class="sxs-lookup"><span data-stu-id="465f3-105">For example, it might be as simple as a row number or as complex as a disk address.</span></span> <span data-ttu-id="465f3-106">在 ODBC 中，应用程序为特定行请求书签，存储该书签，并将其传回到游标以返回到该行。</span><span class="sxs-lookup"><span data-stu-id="465f3-106">In ODBC, the application requests a bookmark for a particular row, stores it, and passes it back to the cursor to return to the row.</span></span>  
  
 <span data-ttu-id="465f3-107">使用[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)提取行时，应用程序可以使用书签作为选择起始行的基础。</span><span class="sxs-lookup"><span data-stu-id="465f3-107">When fetching rows with [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md), an application can use a bookmark as a basis for selecting the starting row.</span></span> <span data-ttu-id="465f3-108">这是一种绝对寻址的格式，因为它不依赖于当前游标位置。</span><span class="sxs-lookup"><span data-stu-id="465f3-108">This is a form of absolute addressing because it does not depend on the current cursor position.</span></span> <span data-ttu-id="465f3-109">若要滚动到带有书签的行，应用程序将调用**SQLFetchScroll** ，并将*FetchOrientation* SQL_FETCH_BOOKMARK。</span><span class="sxs-lookup"><span data-stu-id="465f3-109">To scroll to a bookmarked row, the application calls **SQLFetchScroll** with a *FetchOrientation* of SQL_FETCH_BOOKMARK.</span></span> <span data-ttu-id="465f3-110">此操作使用 SQL_ATTR_FETCH_BOOKMARK_PTR 选项属性所指向的书签。</span><span class="sxs-lookup"><span data-stu-id="465f3-110">This operation uses the bookmark pointed to by the SQL_ATTR_FETCH_BOOKMARK_PTR option attribute.</span></span> <span data-ttu-id="465f3-111">它将返回以该书签标识的行开始的行集。</span><span class="sxs-lookup"><span data-stu-id="465f3-111">It returns the rowset starting with the row identified by that bookmark.</span></span> <span data-ttu-id="465f3-112">应用程序可以在调用**SQLFetchScroll**的*FetchOffset*参数中指定此操作的偏移量。</span><span class="sxs-lookup"><span data-stu-id="465f3-112">An application can specify an offset for this operation in the *FetchOffset* argument of the call to **SQLFetchScroll**.</span></span> <span data-ttu-id="465f3-113">指定偏移量后，会通过将 FetchOffset 参数中的数字与由书签标识的这一行的编号相加来确定所返回行集的第一行。</span><span class="sxs-lookup"><span data-stu-id="465f3-113">When an offset is specified, the first row of the returned rowset is determined by adding the number in the FetchOffset argument to the number of the row identified by the bookmark.</span></span> <span data-ttu-id="465f3-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序只对于静态游标和键集游标支持书签。</span><span class="sxs-lookup"><span data-stu-id="465f3-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver only supports bookmarks on static and keyset cursors.</span></span> <span data-ttu-id="465f3-115">如果在设置书签时要求动态游标，则转而打开键集游标。</span><span class="sxs-lookup"><span data-stu-id="465f3-115">If a dynamic cursor is requested when bookmarks are set on, a keyset cursor is opened instead.</span></span>  
  
 <span data-ttu-id="465f3-116">书签还可与**SQLBulkOperations**函数一起使用，以便对一组从书签开始的行执行操作。</span><span class="sxs-lookup"><span data-stu-id="465f3-116">Bookmarks can also be used with the **SQLBulkOperations** function to perform operations on a set of rows starting at the bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465f3-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="465f3-117">See Also</span></span>  
 [<span data-ttu-id="465f3-118">滚动和提取行</span><span class="sxs-lookup"><span data-stu-id="465f3-118">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
  
