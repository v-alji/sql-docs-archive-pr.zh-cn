---
title: " (ODBC) 执行语句 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
ms.openlocfilehash: 3066a09cb1f5e63105ca3ffe2441f19e4bbe0101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577603"
---
# <a name="executing-statements-odbc"></a><span data-ttu-id="f3e8e-102">执行语句 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="f3e8e-102">Executing Statements (ODBC)</span></span>
  <span data-ttu-id="f3e8e-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序提供了在数据库中执行 SQL 语句的多种方法 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="f3e8e-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers a variety ways to execute SQL statements in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="f3e8e-104">直接执行</span><span class="sxs-lookup"><span data-stu-id="f3e8e-104">Direct execution</span></span>  
  
-   <span data-ttu-id="f3e8e-105">准备好的执行</span><span class="sxs-lookup"><span data-stu-id="f3e8e-105">Prepared execution</span></span>  
  
 <span data-ttu-id="f3e8e-106">直接执行涉及构建包含语句的字符串 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ，并使用**SQLExecDirect**函数提交它以执行执行。</span><span class="sxs-lookup"><span data-stu-id="f3e8e-106">Direct execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submitting it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="f3e8e-107">准备好的执行即生成一个包含 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句的字符串，然后分两个阶段执行。</span><span class="sxs-lookup"><span data-stu-id="f3e8e-107">Prepared execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and then executing it in two stages.</span></span> <span data-ttu-id="f3e8e-108">第一个阶段使用[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)函数分析和编译中的语句的执行计划 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f3e8e-108">The first stage uses the [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) function to parse and compile the execution plan for the statement in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="f3e8e-109">第二个阶段使用**SQLExecute**函数执行之前准备好的执行计划。</span><span class="sxs-lookup"><span data-stu-id="f3e8e-109">The second stage uses the **SQLExecute** function to execute the previously prepared execution plan.</span></span> <span data-ttu-id="f3e8e-110">这节省了每次执行的分析和编译开销。</span><span class="sxs-lookup"><span data-stu-id="f3e8e-110">This saves the parsing and compiling overhead on each execution.</span></span> <span data-ttu-id="f3e8e-111">应用程序通常使用准备好的执行来重复执行相同的参数化 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="f3e8e-111">Prepared execution is commonly used by applications to repeatedly execute the same, parameterized SQL statement.</span></span>  
  
 <span data-ttu-id="f3e8e-112">直接执行和准备好的执行都可以执行单个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句或批处理 SQL 语句，也可以调用存储过程。</span><span class="sxs-lookup"><span data-stu-id="f3e8e-112">Both direct and prepared execution can execute a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement or a batch of SQL statements, or they can call a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3e8e-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="f3e8e-113">In This Section</span></span>  
  
-   [<span data-ttu-id="f3e8e-114">直接执行</span><span class="sxs-lookup"><span data-stu-id="f3e8e-114">Direct Execution</span></span>](direct-execution.md)  
  
-   [<span data-ttu-id="f3e8e-115">准备好的执行</span><span class="sxs-lookup"><span data-stu-id="f3e8e-115">Prepared Execution</span></span>](prepared-execution.md)  
  
-   [<span data-ttu-id="f3e8e-116">过程</span><span class="sxs-lookup"><span data-stu-id="f3e8e-116">Procedures</span></span>](procedures.md)  
  
-   [<span data-ttu-id="f3e8e-117">语句的批处理</span><span class="sxs-lookup"><span data-stu-id="f3e8e-117">Batches of Statements</span></span>](batches-of-statements.md)  
  
-   [<span data-ttu-id="f3e8e-118">ISO 选项的作用</span><span class="sxs-lookup"><span data-stu-id="f3e8e-118">Effects of ISO Options</span></span>](effects-of-iso-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="f3e8e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3e8e-119">See Also</span></span>  
 [<span data-ttu-id="f3e8e-120">&#40;ODBC&#41;执行查询</span><span class="sxs-lookup"><span data-stu-id="f3e8e-120">Executing Queries &#40;ODBC&#41;</span></span>](../executing-queries-odbc.md)  
  
  
