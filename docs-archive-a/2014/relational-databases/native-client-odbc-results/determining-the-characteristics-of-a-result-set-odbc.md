---
title: " (ODBC) 确定结果集的特征 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], characteristics
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLDescribeCol function
- metadata [ODBC]
- SQLColAttribute function
- SQLNumResultCols function
ms.assetid: 90be414c-04b3-46c0-906b-ae7537989b7d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5957092cdddfbcbce904d9a6483914672565d337
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580235"
---
# <a name="determining-the-characteristics-of-a-result-set-odbc"></a><span data-ttu-id="52122-102">确定结果集的特征 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="52122-102">Determining the Characteristics of a Result Set (ODBC)</span></span>
  <span data-ttu-id="52122-103">元数据是描述其他数据的数据。</span><span class="sxs-lookup"><span data-stu-id="52122-103">Metadata is data that describes other data.</span></span> <span data-ttu-id="52122-104">例如，结果集元数据描述结果集的特征，比如结果集中的列数、这些列的数据类型、其名称、精度和可为 Null 性。</span><span class="sxs-lookup"><span data-stu-id="52122-104">For example, result set metadata describes the characteristics of a result set, such as the number of columns in the result set, the data types of those columns, their names, precision, and nullability.</span></span>  
  
 <span data-ttu-id="52122-105">ODBC 通过其目录 API 函数向应用程序提供元数据。</span><span class="sxs-lookup"><span data-stu-id="52122-105">ODBC supplies metadata to applications through its catalog API functions.</span></span> <span data-ttu-id="52122-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc 驱动程序将许多 ODBC API 目录函数实现为对相应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目录过程的调用。</span><span class="sxs-lookup"><span data-stu-id="52122-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver implements many of the ODBC API catalog functions as calls to a corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] catalog procedure.</span></span>  
  
 <span data-ttu-id="52122-107">应用程序需要大多数结果集操作的元数据。</span><span class="sxs-lookup"><span data-stu-id="52122-107">Applications require metadata for most result set operations.</span></span> <span data-ttu-id="52122-108">例如，应用程序使用某列的数据类型来确定要将哪一种变量绑定到该列；</span><span class="sxs-lookup"><span data-stu-id="52122-108">For example, the application uses the data type of a column to determine what kind of variable to bind to that column.</span></span> <span data-ttu-id="52122-109">使用某字符列的字节长度来确定必须有多少空间才能显示该列的数据。</span><span class="sxs-lookup"><span data-stu-id="52122-109">It uses the byte length of a character column to determine how much space it must have to display data from that column.</span></span> <span data-ttu-id="52122-110">应用程序确定列的元数据的方式取决于应用程序的类型。</span><span class="sxs-lookup"><span data-stu-id="52122-110">How an application determines the metadata for a column depends on the type of the application.</span></span>  
  
 <span data-ttu-id="52122-111">垂直应用程序通常使用预定义的表，并对这些表执行预定义的操作。</span><span class="sxs-lookup"><span data-stu-id="52122-111">Vertical applications typically work with predefined tables and perform predefined operations on those tables.</span></span> <span data-ttu-id="52122-112">由于此类应用程序的结果集元数据甚至是在编写应用程序之前定义的，并且由开发人员控制，因此可以将它硬编码到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="52122-112">Because the result set metadata for such applications is defined before the application is even written and is controlled by the developer, it can be hard-coded into the application.</span></span> <span data-ttu-id="52122-113">例如，如果在数据源中将顺序 ID 列定义为 4 字节整数，则应用程序可以始终将 4 字节整数绑定到该列。</span><span class="sxs-lookup"><span data-stu-id="52122-113">For example, if an order ID column is defined as a 4-byte integer in the data source, the application can always bind a 4-byte integer to that column.</span></span> <span data-ttu-id="52122-114">如果元数据在应用程序中为硬编码，则对应用程序所用的表进行更改通常意味着要对应用程序代码进行更改。</span><span class="sxs-lookup"><span data-stu-id="52122-114">When metadata is hard-coded in the application, a change to the tables used by the application generally implies a change to the application code.</span></span>  
  
 <span data-ttu-id="52122-115">在一般应用程序中，尤其是支持即席查询的应用程序中，通常直到运行时才知道应用程序所创建的结果集的元数据。</span><span class="sxs-lookup"><span data-stu-id="52122-115">In generic applications, especially applications that support ad hoc queries, the metadata of the result sets they create is typically unknown until run time.</span></span>  
  
 <span data-ttu-id="52122-116">若要确定结果集的特征，应用程序可以调用：</span><span class="sxs-lookup"><span data-stu-id="52122-116">To determine the characteristics of a result set, an application can call:</span></span>  
  
-   <span data-ttu-id="52122-117">[SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md)确定请求返回的列数。</span><span class="sxs-lookup"><span data-stu-id="52122-117">[SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) to determine how many columns a request returned.</span></span>  
  
-   <span data-ttu-id="52122-118">用于描述结果集中的列的[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md)或[SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) 。</span><span class="sxs-lookup"><span data-stu-id="52122-118">[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) or [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) to describe a column in the result set.</span></span>  
  
 <span data-ttu-id="52122-119">设计得很好的应用程序在编写时会假定结果集是未知的，并使用这些函数返回的信息来绑定结果集中的列。</span><span class="sxs-lookup"><span data-stu-id="52122-119">A well-designed application is written with the assumption that the result set is unknown and uses the information returned by these functions to bind the columns in the result set.</span></span> <span data-ttu-id="52122-120">在准备或执行语句之后，应用程序可以在任何时候调用这些函数。</span><span class="sxs-lookup"><span data-stu-id="52122-120">An application can call these functions at any time after a statement is prepared or executed.</span></span> <span data-ttu-id="52122-121">但是，为了获得最佳性能，应用程序应在执行语句后调用**SQLColAttribute**、 **SQLDescribeCol**和**SQLNumResultCols** 。</span><span class="sxs-lookup"><span data-stu-id="52122-121">However, for optimal performance, an application should call **SQLColAttribute**, **SQLDescribeCol**, and **SQLNumResultCols** after a statement is executed.</span></span>  
  
 <span data-ttu-id="52122-122">可以对元数据进行多个并发调用。</span><span class="sxs-lookup"><span data-stu-id="52122-122">You can have multiple concurrent calls for metadata.</span></span> <span data-ttu-id="52122-123">ODBC 驱动程序可以在使用静态服务器游标时调用作为 ODBC 目录 API 实现基础的系统目录过程。</span><span class="sxs-lookup"><span data-stu-id="52122-123">The system catalog procedures underlying the ODBC catalog API implementations can be called by the ODBC driver while it is using static server cursors.</span></span> <span data-ttu-id="52122-124">这使得应用程序可以同时处理对 ODBC 目录函数的多个调用。</span><span class="sxs-lookup"><span data-stu-id="52122-124">This lets applications concurrently process multiple calls to ODBC catalog functions.</span></span>  
  
 <span data-ttu-id="52122-125">如果某个应用程序多次使用一组特定的元数据，则该应用程序很有可能得益于以下操作：首次获得专用变量中的信息时就进行信息缓存。</span><span class="sxs-lookup"><span data-stu-id="52122-125">If an application uses a particular set of metadata more than one time, it will probably benefit from caching the information in private variables when it is first obtained.</span></span> <span data-ttu-id="52122-126">这样可以防止以后为获取相同信息而调用 ODBC 目录函数，这种调用会强制驱动程序执行到服务器的往返操作。</span><span class="sxs-lookup"><span data-stu-id="52122-126">This prevents later calls to the ODBC catalog functions for the same information, which force the driver to make round trips to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52122-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52122-127">See Also</span></span>  
 [<span data-ttu-id="52122-128">&#40;ODBC&#41;处理结果</span><span class="sxs-lookup"><span data-stu-id="52122-128">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
