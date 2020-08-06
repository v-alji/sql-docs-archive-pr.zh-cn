---
title: 运行存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e5de6a9a13c95b417657a1d108403fa27abe34b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693811"
---
# <a name="running-stored-procedures"></a><span data-ttu-id="184d5-102">运行存储过程</span><span class="sxs-lookup"><span data-stu-id="184d5-102">Running Stored Procedures</span></span>
  <span data-ttu-id="184d5-103">存储过程是存储在数据库中的可执行对象。</span><span class="sxs-lookup"><span data-stu-id="184d5-103">A stored procedure is an executable object stored in a database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="184d5-104">支持：</span><span class="sxs-lookup"><span data-stu-id="184d5-104">supports:</span></span>  
  
-   <span data-ttu-id="184d5-105">存储过程：</span><span class="sxs-lookup"><span data-stu-id="184d5-105">Stored procedures:</span></span>  
  
     <span data-ttu-id="184d5-106">预编译为单个可执行过程的一条或多条 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="184d5-106">One or more SQL statements precompiled into a single executable procedure.</span></span>  
  
-   <span data-ttu-id="184d5-107">扩展存储过程：</span><span class="sxs-lookup"><span data-stu-id="184d5-107">Extended stored procedures:</span></span>  
  
     <span data-ttu-id="184d5-108">编写为扩展存储过程的 SQL Server 开放式数据服务 API 的 C 或 C++ 动态链接库 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="184d5-108">C or C++ dynamic-link libraries (DLL) written to the SQL Server Open Data Services API for extended stored procedures.</span></span> <span data-ttu-id="184d5-109">开放式数据服务 API 扩展了存储过程的功能，以包括 C 或 C++ 代码。</span><span class="sxs-lookup"><span data-stu-id="184d5-109">The Open Data Services API extends the capabilities of stored procedures to include C or C++ code.</span></span>  
  
 <span data-ttu-id="184d5-110">执行语句时，对数据源调用存储过程（而不是直接在客户端应用程序中执行或准备语句）可以：</span><span class="sxs-lookup"><span data-stu-id="184d5-110">When executing statements, calling a stored procedure on the data source (instead of directly executing or preparing a statement in the client application) can provide:</span></span>  
  
-   <span data-ttu-id="184d5-111">提高性能</span><span class="sxs-lookup"><span data-stu-id="184d5-111">Higher performance</span></span>  
  
     <span data-ttu-id="184d5-112">SQL 语句在创建过程时进行分析和编译。</span><span class="sxs-lookup"><span data-stu-id="184d5-112">SQL statements are parsed and compiled when procedures are created.</span></span> <span data-ttu-id="184d5-113">这样，在执行过程时便可节省此开销。</span><span class="sxs-lookup"><span data-stu-id="184d5-113">This overhead is then saved when the procedures are executed.</span></span>  
  
-   <span data-ttu-id="184d5-114">降低网络开销</span><span class="sxs-lookup"><span data-stu-id="184d5-114">Reduced network overhead</span></span>  
  
     <span data-ttu-id="184d5-115">执行过程而不是通过网络发送复杂的查询，从而可降低网络的流量。</span><span class="sxs-lookup"><span data-stu-id="184d5-115">Executing a procedure instead of sending complex queries across the network can reduce network traffic.</span></span> <span data-ttu-id="184d5-116">如果 ODBC 应用程序使用 ODBC { CALL } 语法执行存储过程，ODBC 还可以进行额外的优化，使得无需对参数数据进行转换。</span><span class="sxs-lookup"><span data-stu-id="184d5-116">If an ODBC application uses the ODBC { CALL } syntax to execute a stored procedure, the ODBC driver makes additional optimizations that eliminate the need to convert parameter data.</span></span>  
  
-   <span data-ttu-id="184d5-117">提供更好的一致性</span><span class="sxs-lookup"><span data-stu-id="184d5-117">Greater consistency</span></span>  
  
     <span data-ttu-id="184d5-118">如果组织的规则是在一个中央资源（如存储过程）中实现的，则只需对它们进行一次编码、测试和调试即可。</span><span class="sxs-lookup"><span data-stu-id="184d5-118">If an organization's rules are implemented in a central resource, such as a stored procedure, they can be coded, tested, and debugged once.</span></span> <span data-ttu-id="184d5-119">然后，各个编程人员可以使用经过测试的存储过程，而不是开发他们自己的实现。</span><span class="sxs-lookup"><span data-stu-id="184d5-119">Individual programmers can then use the tested stored procedures instead of developing their own implementations.</span></span>  
  
-   <span data-ttu-id="184d5-120">提高准确性</span><span class="sxs-lookup"><span data-stu-id="184d5-120">Greater accuracy</span></span>  
  
     <span data-ttu-id="184d5-121">由于存储过程通常由有经验的编程人员开发，因此与由不同技术水平的编程人员多次开发而成的代码相比，这些存储过程通常具有更高的效率和更少的错误。</span><span class="sxs-lookup"><span data-stu-id="184d5-121">Because stored procedures are usually developed by experienced programmers, they tend to be more efficient and have fewer errors than code developed multiple times by programmers of varying skill levels.</span></span>  
  
-   <span data-ttu-id="184d5-122">增加功能</span><span class="sxs-lookup"><span data-stu-id="184d5-122">Added functionality</span></span>  
  
     <span data-ttu-id="184d5-123">扩展存储过程可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句所不具备的 C 和 C++ 功能。</span><span class="sxs-lookup"><span data-stu-id="184d5-123">Extended stored procedures can use C and C++ features not available in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="184d5-124">有关如何调用存储过程的示例，请参阅使用[ODBC&#41;&#40;处理返回代码和输出参数](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="184d5-124">For an example of how to call a stored procedure, see [Process Return Codes and Output Parameters &#40;ODBC&#41;](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="184d5-125">本节内容</span><span class="sxs-lookup"><span data-stu-id="184d5-125">In This Section</span></span>  
  
-   [<span data-ttu-id="184d5-126">调用存储过程</span><span class="sxs-lookup"><span data-stu-id="184d5-126">Calling a Stored Procedure</span></span>](calling-a-stored-procedure.md)  
  
-   [<span data-ttu-id="184d5-127">批处理存储过程调用</span><span class="sxs-lookup"><span data-stu-id="184d5-127">Batching Stored Procedure Calls</span></span>](batching-stored-procedure-calls.md)  
  
-   [<span data-ttu-id="184d5-128">处理存储过程结果</span><span class="sxs-lookup"><span data-stu-id="184d5-128">Processing Stored Procedure Results</span></span>](processing-stored-procedure-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="184d5-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="184d5-129">See Also</span></span>  
 <span data-ttu-id="184d5-130">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="184d5-130">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="184d5-131">运行存储过程操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="184d5-131">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
