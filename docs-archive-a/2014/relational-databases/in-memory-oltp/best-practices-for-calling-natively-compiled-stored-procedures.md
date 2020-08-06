---
title: 调用本机编译存储过程的最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d07d0e290d1fbd9b324235e64734a399bf7801d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578197"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a><span data-ttu-id="2445c-102">调用本机编译存储过程的最佳做法</span><span class="sxs-lookup"><span data-stu-id="2445c-102">Best Practices for Calling Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="2445c-103">本机编译存储过程：</span><span class="sxs-lookup"><span data-stu-id="2445c-103">Natively compiled stored procedures are:</span></span>  
  
-   <span data-ttu-id="2445c-104">通常用于应用程序中性能至关重要的部分。</span><span class="sxs-lookup"><span data-stu-id="2445c-104">Used typically in performance-critical parts of an application.</span></span>  
  
-   <span data-ttu-id="2445c-105">频繁执行。</span><span class="sxs-lookup"><span data-stu-id="2445c-105">Frequently executed.</span></span>  
  
-   <span data-ttu-id="2445c-106">操作速度快。</span><span class="sxs-lookup"><span data-stu-id="2445c-106">Expected to be very fast.</span></span>  
  
 <span data-ttu-id="2445c-107">使用本机编译存储过程所得的性能优势随行数和该过程所处理的逻辑数的上升而增加。</span><span class="sxs-lookup"><span data-stu-id="2445c-107">The performance benefit of using a natively compiled stored procedure increases with the number of rows and the amount of logic that is processed by the procedure.</span></span> <span data-ttu-id="2445c-108">例如，如果本机编译存储过程使用以下一项或多项操作，将获得更好的性能：</span><span class="sxs-lookup"><span data-stu-id="2445c-108">For example, a natively compiled stored procedure will exhibit better performance if it uses one or more of the following:</span></span>  
  
-   <span data-ttu-id="2445c-109">聚合。</span><span class="sxs-lookup"><span data-stu-id="2445c-109">Aggregation.</span></span>  
  
-   <span data-ttu-id="2445c-110">嵌套循环联接。</span><span class="sxs-lookup"><span data-stu-id="2445c-110">Nested-loops joins.</span></span>  
  
-   <span data-ttu-id="2445c-111">多语句选择、插入、更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="2445c-111">Multi-statement select, insert, update, and delete operations.</span></span>  
  
-   <span data-ttu-id="2445c-112">复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="2445c-112">Complex expressions.</span></span>  
  
-   <span data-ttu-id="2445c-113">程序逻辑，如条件语句和循环。</span><span class="sxs-lookup"><span data-stu-id="2445c-113">Procedural logic, such as conditional statements and loops.</span></span>  
  
 <span data-ttu-id="2445c-114">如果只需处理一行，则使用本机编译存储过程可能没有任何性能优势。</span><span class="sxs-lookup"><span data-stu-id="2445c-114">If you need to process only a single row, using a natively compiled stored procedure may not provide a performance benefit.</span></span>  
  
 <span data-ttu-id="2445c-115">避免服务器映射参数名称和转换类型：</span><span class="sxs-lookup"><span data-stu-id="2445c-115">To avoid the server having to map parameter names and convert types:</span></span>  
  
-   <span data-ttu-id="2445c-116">使传递给过程的参数类型与过程定义中的类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="2445c-116">Match the types of the parameters passed to the procedure with the types in the procedure definition.</span></span>  
  
-   <span data-ttu-id="2445c-117">在调用本机编译的存储过程时使用序数（无名称）参数。</span><span class="sxs-lookup"><span data-stu-id="2445c-117">Use ordinal (nameless) parameters when calling natively compiled stored procedures.</span></span> <span data-ttu-id="2445c-118">要实现最高效的执行，请勿使用命名参数。</span><span class="sxs-lookup"><span data-stu-id="2445c-118">For the most efficient execution, do not use named parameters.</span></span>  
  
 <span data-ttu-id="2445c-119">可通过 XEvent `hekaton_slow_parameter_passing` 及 `reason=named_parameters` 检测使用了（低效）命名参数的本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="2445c-119">Use of (inefficient) named parameters with natively compiled stored procedures can be detected through the XEvent `hekaton_slow_parameter_passing`, with `reason=named_parameters`.</span></span>  
  
 <span data-ttu-id="2445c-120">类似地，可通过 XEvent `hekaton_slow_parameter_passing` 及 `reason=parameter_conversion` 检测类型不匹配。</span><span class="sxs-lookup"><span data-stu-id="2445c-120">Similarly, you can detect use of mismatched types through the same XEvent `hekaton_slow_parameter_passing`, with `reason=parameter_conversion`.</span></span>  
  
 <span data-ttu-id="2445c-121">因为在使用内存优化表时需要实现重试逻辑（在许多情况下），并且，因为需要解决某些功能限制，所以，您可能需要创建包装解释的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程。</span><span class="sxs-lookup"><span data-stu-id="2445c-121">Because you will need to implement retry logic when using memory-optimized tables (in many scenarios), and because you will need to work around certain feature limitations, you may want to create a wrapper interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure.</span></span> <span data-ttu-id="2445c-122">有关示例，请参阅[内存优化表上的事务重试逻辑指南](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="2445c-122">For an example, see [Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2445c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2445c-123">See Also</span></span>  
 [<span data-ttu-id="2445c-124">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="2445c-124">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
