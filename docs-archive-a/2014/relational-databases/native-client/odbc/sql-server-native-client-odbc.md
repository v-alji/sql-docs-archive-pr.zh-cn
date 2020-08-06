---
title: SQL Server Native Client (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: rothja
ms.author: jroth
ms.openlocfilehash: 16c73966e318ed1e7d326fa77f56195ebbd830df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690587"
---
# <a name="sql-server-native-client-odbc"></a><span data-ttu-id="466fd-102">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="466fd-102">SQL Server Native Client (ODBC)</span></span>
  <span data-ttu-id="466fd-103">ODBC 是应用程序编程接口 (API) 的标准定义，可用于访问关系型数据库或索引的顺序访问方法 (ISAM) 数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="466fd-103">ODBC is a standard definition of an application programming interface (API) used to access data in relational or indexed sequential access method (ISAM) databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="466fd-104">通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序支持 ODBC，并将其作为可用于编写与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通信的 C 和 C++ 应用程序的本机 API 之一。</span><span class="sxs-lookup"><span data-stu-id="466fd-104">supports ODBC, via the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, as one of the native APIs for writing C and C++ applications that communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="466fd-105">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序编写的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 程序通过 C 函数调用与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进行通信。</span><span class="sxs-lookup"><span data-stu-id="466fd-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] programs that are written using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through C function calls.</span></span> <span data-ttu-id="466fd-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序中实现了特定于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 ODBC 函数版本。</span><span class="sxs-lookup"><span data-stu-id="466fd-106">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific versions of the ODBC functions are implemented in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="466fd-107">驱动程序将 SQL 语句传递给 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 并将语句的结果返回给应用程序。</span><span class="sxs-lookup"><span data-stu-id="466fd-107">The driver passes SQL statements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and returns the results of the statements to the application.</span></span>  
  
 <span data-ttu-id="466fd-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序符合 Microsoft Win32 ODBC 3.51 规范。</span><span class="sxs-lookup"><span data-stu-id="466fd-108">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with the Microsoft Win32 ODBC 3.51 specification.</span></span> <span data-ttu-id="466fd-109">驱动程序按照 ODBC 3.51 规范中定义的方式支持使用 ODBC 早期版本编写的应用程序。</span><span class="sxs-lookup"><span data-stu-id="466fd-109">The driver supports applications written using earlier versions of ODBC in the manner defined in the ODBC 3.51 specification.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="466fd-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="466fd-110">In This Section</span></span>  
  
-   [<span data-ttu-id="466fd-111">数据源名称和 64 位操作系统</span><span class="sxs-lookup"><span data-stu-id="466fd-111">Data Source Names and 64-Bit Operating Systems</span></span>](data-source-names-and-64-bit-operating-systems.md)  
  
-   [<span data-ttu-id="466fd-112">创建 SQL Server Native Client ODBC 驱动程序应用程序</span><span class="sxs-lookup"><span data-stu-id="466fd-112">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
-   [<span data-ttu-id="466fd-113">与 SQL Server &#40;ODBC&#41;通信</span><span class="sxs-lookup"><span data-stu-id="466fd-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](../../native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [<span data-ttu-id="466fd-114">&#40;ODBC&#41;执行查询</span><span class="sxs-lookup"><span data-stu-id="466fd-114">Executing Queries &#40;ODBC&#41;</span></span>](../../native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [<span data-ttu-id="466fd-115">&#40;ODBC&#41;处理结果</span><span class="sxs-lookup"><span data-stu-id="466fd-115">Processing Results &#40;ODBC&#41;</span></span>](../../native-client-odbc-results/processing-results-odbc.md)  
  
-   [<span data-ttu-id="466fd-116">使用游标 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="466fd-116">Using Cursors &#40;ODBC&#41;</span></span>](../../native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [<span data-ttu-id="466fd-117">&#40;ODBC&#41;执行事务</span><span class="sxs-lookup"><span data-stu-id="466fd-117">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
-   [<span data-ttu-id="466fd-118">处理错误和消息</span><span class="sxs-lookup"><span data-stu-id="466fd-118">Handling Errors and Messages</span></span>](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [<span data-ttu-id="466fd-119">运行存储过程</span><span class="sxs-lookup"><span data-stu-id="466fd-119">Running Stored Procedures</span></span>](../../native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [<span data-ttu-id="466fd-120">使用目录函数</span><span class="sxs-lookup"><span data-stu-id="466fd-120">Using Catalog Functions</span></span>](using-catalog-functions.md)  
  
-   [<span data-ttu-id="466fd-121">&#40;ODBC&#41;执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="466fd-121">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [<span data-ttu-id="466fd-122">管理 Text 和 Image 列</span><span class="sxs-lookup"><span data-stu-id="466fd-122">Managing Text and Image Columns</span></span>](../../native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [<span data-ttu-id="466fd-123">ODBC 驱动程序性能事件探查</span><span class="sxs-lookup"><span data-stu-id="466fd-123">Profiling ODBC Driver Performance</span></span>](profiling-odbc-driver-performance.md)  
  
-   [<span data-ttu-id="466fd-124">ODBC&#41;&#40;表值参数</span><span class="sxs-lookup"><span data-stu-id="466fd-124">Table-Valued Parameters &#40;ODBC&#41;</span></span>](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [<span data-ttu-id="466fd-125">ODBC&#41;&#40;的日期和时间改进</span><span class="sxs-lookup"><span data-stu-id="466fd-125">Date and Time Improvements &#40;ODBC&#41;</span></span>](../../native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [<span data-ttu-id="466fd-126">&#40;ODBC&#41;的大型 CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="466fd-126">Large CLR User-Defined Types &#40;ODBC&#41;</span></span>](large-clr-user-defined-types-odbc.md)  
  
-   [<span data-ttu-id="466fd-127">FILESTREAM 支持 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="466fd-127">FILESTREAM Support &#40;ODBC&#41;</span></span>](filestream-support-odbc.md)  
  
-   [<span data-ttu-id="466fd-128">客户端连接中的服务主体名称 (SPN) (ODBC)</span><span class="sxs-lookup"><span data-stu-id="466fd-128">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;</span></span>](service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [<span data-ttu-id="466fd-129">稀疏列支持 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="466fd-129">Sparse Columns Support &#40;ODBC&#41;</span></span>](sparse-columns-support-odbc.md)  
  
-   [<span data-ttu-id="466fd-130">SQL Server Native Client &#40;ODBC&#41; 引用</span><span class="sxs-lookup"><span data-stu-id="466fd-130">SQL Server Native Client &#40;ODBC&#41; Reference</span></span>](../../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)  
  
-   [<span data-ttu-id="466fd-131">ODBC 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="466fd-131">ODBC How-to Topics</span></span>](../../native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="466fd-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="466fd-132">See Also</span></span>  
 <span data-ttu-id="466fd-133">[SQL Server Native Client 编程](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="466fd-133">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 [<span data-ttu-id="466fd-134">安装 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="466fd-134">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  
