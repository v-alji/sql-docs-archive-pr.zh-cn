---
title: Transact-SQL 调试器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, introduction
ms.assetid: 6e914699-0d85-46c2-aa2d-3e339ac2c4ce
author: rothja
ms.author: jroth
ms.openlocfilehash: a4312e8ac0989664e447a6ebe1cd3f05ce750f23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688801"
---
# <a name="transact-sql-debugger"></a><span data-ttu-id="44ef2-102">Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="44ef2-102">Transact-SQL Debugger</span></span>
  <span data-ttu-id="44ef2-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器通过调查代码的运行时行为可以帮助您查找 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码中的错误。</span><span class="sxs-lookup"><span data-stu-id="44ef2-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger helps you find errors in [!INCLUDE[tsql](../../includes/tsql-md.md)] code by investigating the run-time behavior of the code.</span></span> <span data-ttu-id="44ef2-104">将 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口设置为调试模式后，可在特定的代码行上暂停执行，并检查那些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句使用和返回的信息和数据。</span><span class="sxs-lookup"><span data-stu-id="44ef2-104">After you set the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window to debug mode, you can pause execution on specific lines of code and inspect information and data that is used by or returned by those [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="stepping-through-transact-sql-code"></a><span data-ttu-id="44ef2-105">单步执行 Transact-SQL 代码</span><span class="sxs-lookup"><span data-stu-id="44ef2-105">Stepping Through Transact-SQL Code</span></span>  
 <span data-ttu-id="44ef2-106">当 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询编辑器窗口处于调试模式时，可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器提供的以下选项逐个导航 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 代码：</span><span class="sxs-lookup"><span data-stu-id="44ef2-106">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger provides the following options that you can use to navigate through [!INCLUDE[tsql](../../includes/tsql-md.md)] code when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window is in debug mode:</span></span>  
  
-   <span data-ttu-id="44ef2-107">在各个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句上设置断点。</span><span class="sxs-lookup"><span data-stu-id="44ef2-107">Set breakpoints on individual [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="44ef2-108">断点指定一个点，您希望在到该点时暂停执行以便您检查数据。</span><span class="sxs-lookup"><span data-stu-id="44ef2-108">A breakpoint specifies a point at which you want execution to pause so you can examine data.</span></span> <span data-ttu-id="44ef2-109">在启动调试器时，调试器会在查询编辑器窗口中的第一个代码行上暂停。</span><span class="sxs-lookup"><span data-stu-id="44ef2-109">When you start the debugger, it pauses on the first line of code in the Query Editor window.</span></span> <span data-ttu-id="44ef2-110">若要运行到您设置的第一个断点，可以使用 **“继续”** 功能。</span><span class="sxs-lookup"><span data-stu-id="44ef2-110">To run to the first breakpoint that you have set, you can use the **Continue** feature.</span></span> <span data-ttu-id="44ef2-111">也可以使用 **“继续”** 功能从窗口当前暂停的任何位置运行到下一个断点。</span><span class="sxs-lookup"><span data-stu-id="44ef2-111">You can also use the **Continue** feature to run to the next breakpoint from any location at which the window is currently paused.</span></span> <span data-ttu-id="44ef2-112">您可以编辑断点，以便指定一些操作（诸如在哪些条件下断点应暂停执行），指定要输出到 **“输出”** 窗口中的信息，以及更改断点的位置。</span><span class="sxs-lookup"><span data-stu-id="44ef2-112">You can edit breakpoints to specify actions such as the conditions under which the breakpoint should pause execution, information to print to the **output** window, and change the location of the breakpoint.</span></span>  
  
-   <span data-ttu-id="44ef2-113">单步执行下一个语句。</span><span class="sxs-lookup"><span data-stu-id="44ef2-113">Step into the next statement.</span></span>  
  
     <span data-ttu-id="44ef2-114">使用此选项可以在一组语句中逐个导航，并在导航时观察它们的行为。</span><span class="sxs-lookup"><span data-stu-id="44ef2-114">This option enables you to navigate through a set of statements one by one, and to observe their behavior as you go.</span></span>  
  
-   <span data-ttu-id="44ef2-115">单步或逐过程对存储过程或函数执行调用。</span><span class="sxs-lookup"><span data-stu-id="44ef2-115">Step either into or over a call to a stored procedure or function.</span></span>  
  
     <span data-ttu-id="44ef2-116">如果确认存储过程中没有错误，可以逐过程执行。</span><span class="sxs-lookup"><span data-stu-id="44ef2-116">If you are sure there are no errors in a stored procedure, you can step over it.</span></span> <span data-ttu-id="44ef2-117">这样可以完整执行该过程，并将结果返回到代码。</span><span class="sxs-lookup"><span data-stu-id="44ef2-117">The procedure is executed in full, and the results are returned to the code.</span></span>  
  
     <span data-ttu-id="44ef2-118">如果要调试一个存储过程或函数，则可单步执行模块。</span><span class="sxs-lookup"><span data-stu-id="44ef2-118">If you want to debug a stored procedure or function, you can step into the module.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="44ef2-119">会打开一个由模块源代码填充的新 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口，将该窗口置于调试模式，并暂停对模块中第一个语句的执行。</span><span class="sxs-lookup"><span data-stu-id="44ef2-119">opens a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window that is populated with the source code for the module, places the window into debug mode, and then pauses execution on the first statement in the module.</span></span> <span data-ttu-id="44ef2-120">然后，您就可以在模块代码中导航，例如通过设置断点或逐句通过代码。</span><span class="sxs-lookup"><span data-stu-id="44ef2-120">You can then navigate through the module code, for example, by setting breakpoints or stepping through the code.</span></span>  
  
 <span data-ttu-id="44ef2-121">有关如何通过调试器浏览代码的详细信息，请参阅 [Transact-SQL 代码](step-through-transact-sql-code.md)。</span><span class="sxs-lookup"><span data-stu-id="44ef2-121">For more information about how the debugger enables you to navigate code, see [Step Through Transact-SQL Code](step-through-transact-sql-code.md).</span></span>  
  
## <a name="viewing-debugger-information"></a><span data-ttu-id="44ef2-122">查看调试器信息</span><span class="sxs-lookup"><span data-stu-id="44ef2-122">Viewing Debugger Information</span></span>  
 <span data-ttu-id="44ef2-123">每当调试器对特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句暂停执行时，您可以都使用以下调试器窗口来查看当前执行状态：</span><span class="sxs-lookup"><span data-stu-id="44ef2-123">Each time the debugger pauses execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can use the following debugger windows to view the current execution state:</span></span>  
  
-   <span data-ttu-id="44ef2-124">**局部变量** 和 **监视**</span><span class="sxs-lookup"><span data-stu-id="44ef2-124">**Locals** and **Watch.**</span></span> <span data-ttu-id="44ef2-125">这些窗口显示当前分配的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式。</span><span class="sxs-lookup"><span data-stu-id="44ef2-125">These windows display currently allocated [!INCLUDE[tsql](../../includes/tsql-md.md)] expressions.</span></span> <span data-ttu-id="44ef2-126">表达式是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 子句，其计算结果为单个标量表达式。</span><span class="sxs-lookup"><span data-stu-id="44ef2-126">Expressions are [!INCLUDE[tsql](../../includes/tsql-md.md)] clauses that evaluate to a single, scalar expression.</span></span> <span data-ttu-id="44ef2-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器支持查看引用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 变量、参数或名称以 @@ 开头的内置函数的表达式。</span><span class="sxs-lookup"><span data-stu-id="44ef2-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports viewing expressions that reference [!INCLUDE[tsql](../../includes/tsql-md.md)] variables, parameters, or the built-in functions that have names that start with @@.</span></span> <span data-ttu-id="44ef2-128">这些窗口还显示当前分配给表达式的数据值。</span><span class="sxs-lookup"><span data-stu-id="44ef2-128">These windows also display the data values that are currently assigned to the expressions.</span></span>  
  
-   <span data-ttu-id="44ef2-129">**快速监视。**</span><span class="sxs-lookup"><span data-stu-id="44ef2-129">**QuickWatch.**</span></span> <span data-ttu-id="44ef2-130">此窗口显示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式的值，还可将该表达式保存到 **监视** 窗口。</span><span class="sxs-lookup"><span data-stu-id="44ef2-130">This window displays the value of a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, and enables saving that expression to a **Watch** window.</span></span>  
  
-   <span data-ttu-id="44ef2-131">**断点。**</span><span class="sxs-lookup"><span data-stu-id="44ef2-131">**Breakpoints.**</span></span> <span data-ttu-id="44ef2-132">此窗口显示当前设置的断点，通过此窗口可对断点进行管理。</span><span class="sxs-lookup"><span data-stu-id="44ef2-132">This window displays the currently set breakpoints and enables you to manage them.</span></span>  
  
-   <span data-ttu-id="44ef2-133">**调用堆栈。**</span><span class="sxs-lookup"><span data-stu-id="44ef2-133">**Call Stack.**</span></span> <span data-ttu-id="44ef2-134">此窗口显示当前执行位置。</span><span class="sxs-lookup"><span data-stu-id="44ef2-134">This window displays the current execution location.</span></span> <span data-ttu-id="44ef2-135">它还提供关于执行如何从原始查询编辑器窗口开始，通过所有函数、存储过程或触发器，最后到达当前执行位置的信息。</span><span class="sxs-lookup"><span data-stu-id="44ef2-135">And also provides information about how execution passed from the original Query Editor window through any functions, stored procedures, or triggers to reach the current execution location.</span></span>  
  
-   <span data-ttu-id="44ef2-136">**输出。**</span><span class="sxs-lookup"><span data-stu-id="44ef2-136">**Output.**</span></span> <span data-ttu-id="44ef2-137">此窗口显示各种消息和程序数据，如来自调试器的系统消息。</span><span class="sxs-lookup"><span data-stu-id="44ef2-137">This window displays various messages and program data, such as system messages from the debugger.</span></span>  
  
-   <span data-ttu-id="44ef2-138">**结果** 和 **消息**</span><span class="sxs-lookup"><span data-stu-id="44ef2-138">**Results** and **Messages.**</span></span> <span data-ttu-id="44ef2-139">“查询编辑器”窗口上的这些选项卡显示以前执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的结果。</span><span class="sxs-lookup"><span data-stu-id="44ef2-139">These tabs on the Query Editor window display the results of previously executed [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="transact-sql-debugger-tasks"></a><span data-ttu-id="44ef2-140">Transact-SQL 调试器任务</span><span class="sxs-lookup"><span data-stu-id="44ef2-140">Transact-SQL Debugger Tasks</span></span>  
  
|<span data-ttu-id="44ef2-141">任务说明</span><span class="sxs-lookup"><span data-stu-id="44ef2-141">Task Description</span></span>|<span data-ttu-id="44ef2-142">主题</span><span class="sxs-lookup"><span data-stu-id="44ef2-142">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="44ef2-143">介绍如何配置 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器以用于远程调试。</span><span class="sxs-lookup"><span data-stu-id="44ef2-143">Describes how to configure the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger for remote debugging.</span></span>|[<span data-ttu-id="44ef2-144">配置 Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="44ef2-144">Configure the Transact-SQL Debugger</span></span>](configure-firewall-rules-before-running-the-tsql-debugger.md)|  
|<span data-ttu-id="44ef2-145">介绍如何启动、停止和控制调试器的操作。</span><span class="sxs-lookup"><span data-stu-id="44ef2-145">Describes how to start, stop, and control the operation of the debugger.</span></span>|[<span data-ttu-id="44ef2-146">运行 Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="44ef2-146">Run the Transact-SQL Debugger</span></span>](transact-sql-debugger.md)|  
|<span data-ttu-id="44ef2-147">介绍如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器逐句通过代码。</span><span class="sxs-lookup"><span data-stu-id="44ef2-147">Describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger to step through code.</span></span>|[<span data-ttu-id="44ef2-148">逐句通过 Transact-SQL 代码</span><span class="sxs-lookup"><span data-stu-id="44ef2-148">Step Through Transact-SQL Code</span></span>](step-through-transact-sql-code.md)|  
|<span data-ttu-id="44ef2-149">介绍如何使用调试器查看 [!INCLUDE[tsql](../../includes/tsql-md.md)] 数据，例如参数、变量和系统信息。</span><span class="sxs-lookup"><span data-stu-id="44ef2-149">Describes how to use the debugger to view [!INCLUDE[tsql](../../includes/tsql-md.md)] data, such as parameters and variables, and system information.</span></span>|[<span data-ttu-id="44ef2-150">Transact-SQL 调试器信息</span><span class="sxs-lookup"><span data-stu-id="44ef2-150">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)|  
  
## <a name="see-also"></a><span data-ttu-id="44ef2-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44ef2-151">See Also</span></span>  
 [<span data-ttu-id="44ef2-152">查询和文本编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="44ef2-152">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
