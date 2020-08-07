---
title: Transact-SQL 代码
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, debugging code
- Transact-SQL debugger, step over
- Transact-SQL debugger, step out
- Transact-SQL debugger, step into
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
author: rothja
ms.author: jroth
ms.openlocfilehash: 48cb307130c65729640864a26bdf1dfaf344b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589501"
---
# <a name="step-through-transact-sql-code"></a><span data-ttu-id="b57fb-102">Transact-SQL 代码</span><span class="sxs-lookup"><span data-stu-id="b57fb-102">Step Through Transact-SQL Code</span></span>
  <span data-ttu-id="b57fb-103">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器，您可以控制在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询编辑器窗口中运行哪些 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="b57fb-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger enables you to control which [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run in a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span> <span data-ttu-id="b57fb-104">可在各个语句上暂停调试器，然后查看该位置的代码元素的状态。</span><span class="sxs-lookup"><span data-stu-id="b57fb-104">You can pause the debugger on individual statements and then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="b57fb-105">断点</span><span class="sxs-lookup"><span data-stu-id="b57fb-105">Breakpoints</span></span>  
 <span data-ttu-id="b57fb-106">断点表示调试器对特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句暂停执行。</span><span class="sxs-lookup"><span data-stu-id="b57fb-106">A breakpoint signals the debugger to pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="b57fb-107">有关断点的详细信息，请参阅“使用 Transact-SQL 断点”。</span><span class="sxs-lookup"><span data-stu-id="b57fb-107">For more information about breakpoints, see Using Transact-SQL Breakpoints.</span></span>  
  
## <a name="controlling-statement-execution"></a><span data-ttu-id="b57fb-108">控制语句执行</span><span class="sxs-lookup"><span data-stu-id="b57fb-108">Controlling Statement Execution</span></span>  
 <span data-ttu-id="b57fb-109">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器中，可以指定从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码中的当前语句开始执行的以下选项：</span><span class="sxs-lookup"><span data-stu-id="b57fb-109">In the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can specify the following options for executing from the current statement in [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
-   <span data-ttu-id="b57fb-110">运行到下一个断点。</span><span class="sxs-lookup"><span data-stu-id="b57fb-110">Run to the next breakpoint.</span></span>  
  
-   <span data-ttu-id="b57fb-111">单步执行下一个语句。</span><span class="sxs-lookup"><span data-stu-id="b57fb-111">Step into the next statement.</span></span>  
  
     <span data-ttu-id="b57fb-112">如果下一个语句调用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程、函数或触发器，则调试器会显示一个包含该模块的代码的新查询编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="b57fb-112">If the next statement invokes a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, function, or trigger, the debugger displays a new Query Editor window that contains the code of the module.</span></span> <span data-ttu-id="b57fb-113">该窗口处于调试模式，并在模块中的第一个语句上暂停执行。</span><span class="sxs-lookup"><span data-stu-id="b57fb-113">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="b57fb-114">然后，您可以在模块代码中移动，例如，设置断点或逐句通过代码。</span><span class="sxs-lookup"><span data-stu-id="b57fb-114">You can then move through the module code, for example, by setting breakpoints or stepping through the code.</span></span>  
  
-   <span data-ttu-id="b57fb-115">逐过程执行下一个语句。</span><span class="sxs-lookup"><span data-stu-id="b57fb-115">Step over the next statement.</span></span>  
  
     <span data-ttu-id="b57fb-116">执行下一个语句。</span><span class="sxs-lookup"><span data-stu-id="b57fb-116">The next statement is executed.</span></span> <span data-ttu-id="b57fb-117">但是，如果该语句调用了存储过程、函数或触发器，则模块代码会运行，直到完成执行，并将结果返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="b57fb-117">However, if the statement invokes a stored procedure, function, or trigger, the module code runs until it finishes, and the results are returned to the calling code.</span></span> <span data-ttu-id="b57fb-118">如果确认存储过程中没有错误，可以逐过程执行。</span><span class="sxs-lookup"><span data-stu-id="b57fb-118">If you are sure there are no errors in a stored procedure, you can step over it.</span></span> <span data-ttu-id="b57fb-119">在调用存储过程、函数或触发器的后面的语句上暂停执行。</span><span class="sxs-lookup"><span data-stu-id="b57fb-119">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="b57fb-120">跳出存储过程、函数或触发器。</span><span class="sxs-lookup"><span data-stu-id="b57fb-120">Step out of a stored procedure, function, or trigger.</span></span>  
  
     <span data-ttu-id="b57fb-121">在调用存储过程、函数或触发器的后面的语句上暂停执行。</span><span class="sxs-lookup"><span data-stu-id="b57fb-121">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="b57fb-122">从当前位置运行到指针的当前位置，并忽略所有断点。</span><span class="sxs-lookup"><span data-stu-id="b57fb-122">Run from the current location to the current location of the pointer, and ignore all breakpoints.</span></span>  
  
 <span data-ttu-id="b57fb-123">下表列出了用于控制在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器中执行语句的各种方法。</span><span class="sxs-lookup"><span data-stu-id="b57fb-123">The following table lists the various ways in which you can control how statements execute in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
|<span data-ttu-id="b57fb-124">操作</span><span class="sxs-lookup"><span data-stu-id="b57fb-124">Action</span></span>|<span data-ttu-id="b57fb-125">过程</span><span class="sxs-lookup"><span data-stu-id="b57fb-125">Procedure</span></span>|  
|------------|---------------|  
|<span data-ttu-id="b57fb-126">运行当前语句到下一个断点之间的所有语句</span><span class="sxs-lookup"><span data-stu-id="b57fb-126">Run all statements from the current statement to the next breakpoint</span></span>|<span data-ttu-id="b57fb-127">在“调试”菜单上，单击“继续” 。</span><span class="sxs-lookup"><span data-stu-id="b57fb-127">On the **Debug** menu, click **Continue**.</span></span><br /><br /> <span data-ttu-id="b57fb-128">在 "**调试**" 工具栏上，单击 "**继续**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b57fb-128">On the **Debug** toolbar, click the **Continue** button.</span></span>|  
|<span data-ttu-id="b57fb-129">单步执行下一个语句或模块</span><span class="sxs-lookup"><span data-stu-id="b57fb-129">Step into the next statement or module</span></span>|<span data-ttu-id="b57fb-130">在 "**调试**" 菜单上单击 "**单步**执行"。</span><span class="sxs-lookup"><span data-stu-id="b57fb-130">On the **Debug** menu, click **Step Into**.</span></span><br /><br /> <span data-ttu-id="b57fb-131">在 "**调试**" 工具栏上，单击 "**单步**执行" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b57fb-131">On the **Debug** toolbar, click the **Step Into** button.</span></span><br /><br /> <span data-ttu-id="b57fb-132">按 F11。</span><span class="sxs-lookup"><span data-stu-id="b57fb-132">Press F11.</span></span>|  
|<span data-ttu-id="b57fb-133">逐过程执行下一个语句或模块</span><span class="sxs-lookup"><span data-stu-id="b57fb-133">Step over the next statement or module</span></span>|<span data-ttu-id="b57fb-134">在“调试”菜单上，单击“逐过程” 。</span><span class="sxs-lookup"><span data-stu-id="b57fb-134">On the **Debug** menu, click **Step Over**.</span></span><br /><br /> <span data-ttu-id="b57fb-135">在 "**调试**" 工具栏上，单击 "**单步执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b57fb-135">On the **Debug** toolbar, click the **Step Over** button.</span></span><br /><br /> <span data-ttu-id="b57fb-136">按 F10。</span><span class="sxs-lookup"><span data-stu-id="b57fb-136">Press F10.</span></span>|  
|<span data-ttu-id="b57fb-137">跳出模块</span><span class="sxs-lookup"><span data-stu-id="b57fb-137">Step out of a module</span></span>|<span data-ttu-id="b57fb-138">在 "**调试**" 菜单上，单击 "**跳出**"。</span><span class="sxs-lookup"><span data-stu-id="b57fb-138">On the **Debug** menu, click **Step Out**.</span></span><br /><br /> <span data-ttu-id="b57fb-139">在 "**调试**" 工具栏上，单击 "**跳出**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b57fb-139">On the **Debug** toolbar, click the **Step Out** button.</span></span><br /><br /> <span data-ttu-id="b57fb-140">按 Shift+F11。</span><span class="sxs-lookup"><span data-stu-id="b57fb-140">Press SHIFT+F11.</span></span>|  
|<span data-ttu-id="b57fb-141">运行到当前光标位置</span><span class="sxs-lookup"><span data-stu-id="b57fb-141">Run to the current cursor location</span></span>|<span data-ttu-id="b57fb-142">右键单击查询编辑器窗口，然后单击“运行至光标处”  。</span><span class="sxs-lookup"><span data-stu-id="b57fb-142">Right-click in the Query Editor window, and then click **Run To Cursor**.</span></span><br /><br /> <span data-ttu-id="b57fb-143">按 Ctrl+F10。</span><span class="sxs-lookup"><span data-stu-id="b57fb-143">Press CTRL+F10.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b57fb-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b57fb-144">See Also</span></span>  
 [<span data-ttu-id="b57fb-145">Transact-SQL 调试器信息</span><span class="sxs-lookup"><span data-stu-id="b57fb-145">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
