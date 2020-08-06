---
title: 直接执行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: rothja
ms.author: jroth
ms.openlocfilehash: 29153f3e4e9265e87feb0e23ba9ae97118691e95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577605"
---
# <a name="direct-execution"></a><span data-ttu-id="232f3-102">直接执行</span><span class="sxs-lookup"><span data-stu-id="232f3-102">Direct Execution</span></span>
  <span data-ttu-id="232f3-103">直接执行是最基本的语句执行方式。</span><span class="sxs-lookup"><span data-stu-id="232f3-103">Direct execution is the most basic way to execute a statement.</span></span> <span data-ttu-id="232f3-104">应用程序将生成一个包含语句的字符串 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ，然后使用**SQLExecDirect**函数提交它以执行执行。</span><span class="sxs-lookup"><span data-stu-id="232f3-104">An application builds a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submits it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="232f3-105">当该语句到达服务器时，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将其编译为执行计划，然后立即运行该执行计划。</span><span class="sxs-lookup"><span data-stu-id="232f3-105">When the statement reaches the server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compiles it into an execution plan and then immediately runs the execution plan.</span></span>  
  
 <span data-ttu-id="232f3-106">直接执行是在运行时生成和执行语句的应用程序的常用执行方式，它也是只需执行一次的语句的最有效方法。</span><span class="sxs-lookup"><span data-stu-id="232f3-106">Direct execution is commonly used by applications that build and execute statements at run time and is the most efficient method for statements that will be executed a single time.</span></span> <span data-ttu-id="232f3-107">对于许多数据库而言，它的缺点就是每次执行 SQL 语句都必须对该语句进行分析和编译，如果该语句多次执行，就会增加开销。</span><span class="sxs-lookup"><span data-stu-id="232f3-107">Its drawback with many databases is that the SQL statement must be parsed and compiled each time it is executed, which adds overhead if the statement is executed multiple times.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="232f3-108">显著提高了在多用户环境中直接执行通常执行的语句的性能；如果将 SQLExecDirect 与参数标记配合用于通常执行的 SQL 语句，其效率可接近准备好的执行。</span><span class="sxs-lookup"><span data-stu-id="232f3-108">significantly improves the performance of direct execution of commonly executed statements in multiuser environments and using SQLExecDirect with parameter markers for commonly executed SQL statements can approach the efficiency of prepared execution.</span></span>  
  
 <span data-ttu-id="232f3-109">当连接到实例时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序使用[sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql)传输**SQLExecDirect**上指定的 SQL 语句或批处理。</span><span class="sxs-lookup"><span data-stu-id="232f3-109">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) to transmit the SQL statement or batch specified on **SQLExecDirect**.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="232f3-110">具有逻辑来快速确定使用**sp_executesql**执行的 SQL 语句或批处理是否与生成执行计划（已存在于内存中）的语句或批处理相匹配。</span><span class="sxs-lookup"><span data-stu-id="232f3-110">has logic to quickly determine if an SQL statement or batch executed with **sp_executesql** matches the statement or batch that generated an execution plan that already exists in memory.</span></span> <span data-ttu-id="232f3-111">如果匹配，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 只需重用现有计划，而无需编译新计划。</span><span class="sxs-lookup"><span data-stu-id="232f3-111">If a match is made, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] simply reuses the existing plan rather than compile a new plan.</span></span> <span data-ttu-id="232f3-112">这意味着，在包含多个用户的系统中，使用**SQLExecDirect**执行的常见 SQL 语句将受益于较早版本的中的存储过程所使用的许多计划重用权益 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="232f3-112">This means that commonly executed SQL statements executed with **SQLExecDirect** in a system with many users will benefit from many of the plan-reuse benefits that were only available to stored procedures in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="232f3-113">仅当多个用户执行同一 SQL 语句或批处理时，才会从重用执行计划中受益。</span><span class="sxs-lookup"><span data-stu-id="232f3-113">This benefit of reusing execution plans only works when several users are executing the same SQL statement or batch.</span></span> <span data-ttu-id="232f3-114">请遵照以下编码约定，提高不同客户端执行的 SQL 语句的相似性，以便能够重用执行计划：</span><span class="sxs-lookup"><span data-stu-id="232f3-114">Follow these coding conventions to increase the probability that the SQL statements executed by different clients are similar enough to be able to reuse execution plans:</span></span>  
  
-   <span data-ttu-id="232f3-115">不要在 SQL 语句中包括数据常量；改用绑定到程序变量的参数标记。</span><span class="sxs-lookup"><span data-stu-id="232f3-115">Do not include data constants in the SQL statements; instead use parameter markers bound to program variables.</span></span> <span data-ttu-id="232f3-116">有关详细信息，请参阅[Using 语句参数](../using-statement-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="232f3-116">For more information, see [Using Statement Parameters](../using-statement-parameters.md).</span></span>  
  
-   <span data-ttu-id="232f3-117">使用完全限定对象名。</span><span class="sxs-lookup"><span data-stu-id="232f3-117">Use fully qualified object names.</span></span> <span data-ttu-id="232f3-118">如果未限定对象名，则不重用执行计划。</span><span class="sxs-lookup"><span data-stu-id="232f3-118">Execution plans are not reused if object names are not qualified.</span></span>  
  
-   <span data-ttu-id="232f3-119">令应用程序连接尽量使用常用的一组连接和语句选项。</span><span class="sxs-lookup"><span data-stu-id="232f3-119">Have application connections as possible use a common set of connection and statement options.</span></span> <span data-ttu-id="232f3-120">从具有某一组选项（如 ANSI_NULLS）的连接生成的执行计划不会重复用于具有另一组选项的连接。</span><span class="sxs-lookup"><span data-stu-id="232f3-120">Execution plans generated for a connection with one set of options (such as ANSI_NULLS) are not reused for a connection having another set of options.</span></span> <span data-ttu-id="232f3-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口的这些选项都具有相同的默认设置。</span><span class="sxs-lookup"><span data-stu-id="232f3-121">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider both have the same default settings for these options.</span></span>  
  
 <span data-ttu-id="232f3-122">如果使用这些约定对使用**SQLExecDirect**执行的所有语句进行编码，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可能会在出现机会时重新使用执行计划。</span><span class="sxs-lookup"><span data-stu-id="232f3-122">If all statements executed with **SQLExecDirect** are coded using these conventions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can reuse execution plans when the opportunity arises.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232f3-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="232f3-123">See Also</span></span>  
 [<span data-ttu-id="232f3-124">&#40;ODBC&#41;执行语句</span><span class="sxs-lookup"><span data-stu-id="232f3-124">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
