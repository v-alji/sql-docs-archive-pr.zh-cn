---
title: 本机编译的存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8fb7a379c0c08ca357baa1042ebcf51c512c9ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692405"
---
# <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="d89f9-102">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="d89f9-102">Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="d89f9-103">本机编译的存储过程是编译为访问内存优化表的本机代码的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程。</span><span class="sxs-lookup"><span data-stu-id="d89f9-103">Natively compiled stored procedures are [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures compiled to native code that access memory-optimized tables.</span></span> <span data-ttu-id="d89f9-104">利用本机编译的存储过程，可在存储过程中高效执行查询和业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="d89f9-104">Natively compiled stored procedures allow for efficient execution of queries and business logic in the stored procedure.</span></span> <span data-ttu-id="d89f9-105">有关本机编译过程的更详细信息，请参阅 [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d89f9-105">For more details about the native compilation process, see [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md).</span></span> <span data-ttu-id="d89f9-106">有关将基于磁盘的存储过程迁移到本机编译的存储过程的详细信息，请参阅 [本机编译的存储过程的迁移问题](migration-issues-for-natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d89f9-106">For more information about migrating disk-based stored procedures to natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d89f9-107">解释型（基于磁盘的）存储过程与本机编译的存储过程之间的一个区别在于解释型存储过程是在首次执行时编译的，而本机编译的存储过程是在创建时编译的。</span><span class="sxs-lookup"><span data-stu-id="d89f9-107">One difference between interpreted (disk-based) stored procedures and natively compiled stored procedures is that an interpreted stored procedure is compiled at first execution whereas a natively compiled stored procedure is compiled when it is created.</span></span> <span data-ttu-id="d89f9-108">对于本机编译的存储过程，可在创建时检测到许多错误情况（算术溢出、类型转换和一些被零除情况），并且将导致本机编译的存储过程的创建失败。</span><span class="sxs-lookup"><span data-stu-id="d89f9-108">With natively compiled stored procedures, many error conditions (arithmetic overflow, type conversion, and some divide-by-zero conditions) can be detected at create time and will cause creation of the natively compiled stored procedure to fail.</span></span> <span data-ttu-id="d89f9-109">对于解释型存储过程，在创建存储过程时这些错误情况通常将不会导致失败，但所有执行都将失败。</span><span class="sxs-lookup"><span data-stu-id="d89f9-109">With interpreted stored procedures, these error conditions will typically not cause a failure when the stored procedure is created, but all executions will fail.</span></span>  
  
 <span data-ttu-id="d89f9-110">本节主题：</span><span class="sxs-lookup"><span data-stu-id="d89f9-110">Topics in this section:</span></span>  
  
-   [<span data-ttu-id="d89f9-111">创建本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="d89f9-111">Creating Natively Compiled Stored Procedures</span></span>](creating-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="d89f9-112">原子块</span><span class="sxs-lookup"><span data-stu-id="d89f9-112">Atomic Blocks</span></span>](atomic-blocks-in-native-procedures.md)  
  
-   [<span data-ttu-id="d89f9-113">本机编译的存储过程中支持的构造</span><span class="sxs-lookup"><span data-stu-id="d89f9-113">Supported Constructs in Natively Compiled Stored Procedures</span></span>](supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="d89f9-114">在本机编译的存储过程中使用 Try..Catch</span><span class="sxs-lookup"><span data-stu-id="d89f9-114">Using Try..Catch in Natively Compiled Stored Procedures</span></span>](../../database-engine/using-try-catch-in-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="d89f9-115">本机编译的存储过程支持的构造</span><span class="sxs-lookup"><span data-stu-id="d89f9-115">Supported Constructs on Natively Compiled Stored Procedures</span></span>](supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="d89f9-116">本机编译存储过程和执行的 Set 选项</span><span class="sxs-lookup"><span data-stu-id="d89f9-116">Natively Compiled Stored Procedures and Execution Set Options</span></span>](natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [<span data-ttu-id="d89f9-117">调用本机编译存储过程的最佳做法</span><span class="sxs-lookup"><span data-stu-id="d89f9-117">Best Practices for Calling Natively Compiled Stored Procedures</span></span>](best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="d89f9-118">监视本机编译的存储过程的执行</span><span class="sxs-lookup"><span data-stu-id="d89f9-118">Monitoring Performance of Natively Compiled Stored Procedures</span></span>](monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="d89f9-119">从数据访问应用程序调用本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="d89f9-119">Calling Natively Compiled Stored Procedures from Data Access Applications</span></span>](calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="d89f9-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d89f9-120">See Also</span></span>  
 [<span data-ttu-id="d89f9-121">Memory-Optimized Tables</span><span class="sxs-lookup"><span data-stu-id="d89f9-121">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
