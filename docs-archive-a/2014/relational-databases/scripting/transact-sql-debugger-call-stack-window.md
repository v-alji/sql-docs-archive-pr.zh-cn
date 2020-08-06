---
title: “调用堆栈”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Call Stack Window [Transact-SQL]
ms.assetid: ddb0b19c-87cd-4883-bcb8-ec09ffb30369
author: rothja
ms.author: jroth
ms.openlocfilehash: b4b72e484ade696be81ebac8ea4eed9be295edf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590153"
---
# <a name="call-stack-window"></a><span data-ttu-id="22adf-102">“调用堆栈”窗口</span><span class="sxs-lookup"><span data-stu-id="22adf-102">Call Stack Window</span></span>
  <span data-ttu-id="22adf-103">**“调用堆栈”** 窗口显示调用堆栈中的模块以及传递给这些模块的任意参数的数据类型和值。</span><span class="sxs-lookup"><span data-stu-id="22adf-103">The **Call Stack** window displays the modules on the call stack, and the data types and values of any parameters that are passed to the modules.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="22adf-104">模块包括存储过程、函数和触发器。</span><span class="sxs-lookup"><span data-stu-id="22adf-104">modules include stored procedures, functions, and triggers.</span></span> <span data-ttu-id="22adf-105">只有在调试模式下才可以显示调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="22adf-105">To display the call stack, you must be in debug mode.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="22adf-106">任务列表</span><span class="sxs-lookup"><span data-stu-id="22adf-106">Task List</span></span>  
 <span data-ttu-id="22adf-107">**访问“调用堆栈”窗口**</span><span class="sxs-lookup"><span data-stu-id="22adf-107">**To access the Call Stack window**</span></span>  
  
-   <span data-ttu-id="22adf-108">在 **“调试”** 菜单上单击 **“窗口”** ，再单击 **“调用堆栈”** 。</span><span class="sxs-lookup"><span data-stu-id="22adf-108">On the **Debug** menu, click **Windows**, and then click **Call Stack**.</span></span>  
  
 <span data-ttu-id="22adf-109">**更改当前调用堆栈帧**</span><span class="sxs-lookup"><span data-stu-id="22adf-109">**To change the current Call Stack frame**</span></span>  
  
 <span data-ttu-id="22adf-110">可以使用以下任一过程使某个堆栈帧成为当前帧：</span><span class="sxs-lookup"><span data-stu-id="22adf-110">You can use either of the following procedures to make a stack frame the current frame:</span></span>  
  
-   <span data-ttu-id="22adf-111">右键单击该堆栈帧，然后单击“切换到帧”  。</span><span class="sxs-lookup"><span data-stu-id="22adf-111">Right-click the stack frame, and then click **Switch To Frame**.</span></span>  
  
-   <span data-ttu-id="22adf-112">双击该堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="22adf-112">Double-click the stack frame.</span></span>  
  
 <span data-ttu-id="22adf-113">**查看当前帧以外的帧的源**</span><span class="sxs-lookup"><span data-stu-id="22adf-113">**To view the source of a frame other than the current frame**</span></span>  
  
-   <span data-ttu-id="22adf-114">右键单击该堆栈帧，然后单击“转到源代码”  。</span><span class="sxs-lookup"><span data-stu-id="22adf-114">Right-click the stack frame, and then click **Go To Source Code**.</span></span>  
  
## <a name="stack-frames"></a><span data-ttu-id="22adf-115">堆栈帧</span><span class="sxs-lookup"><span data-stu-id="22adf-115">Stack Frames</span></span>  
 <span data-ttu-id="22adf-116">**“调用堆栈”** 窗口中的每一行称为一个堆栈帧，表示一个从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件到模块的调用或从一个模块到另一个模块的调用。</span><span class="sxs-lookup"><span data-stu-id="22adf-116">Each row in the **Call Stack** window is called a stack frame and represents either a call from a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file to a module or a call from one module to another.</span></span> <span data-ttu-id="22adf-117">所显示的最下面的堆栈帧指示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口中最先调用此堆栈的行。</span><span class="sxs-lookup"><span data-stu-id="22adf-117">The bottom stack frame in the display indicates the line in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window that made the first call into the stack.</span></span> <span data-ttu-id="22adf-118">最上面一行指示调试器暂停执行时所在的行，由该窗口左边距中的黄色箭头标出。</span><span class="sxs-lookup"><span data-stu-id="22adf-118">The top row indicates the line on which the debugger paused execution, and is identified by a yellow arrow in the left margin of the window.</span></span> <span data-ttu-id="22adf-119">中间的每一行指示调用下一个更高堆栈帧的模块和源代码的行号。</span><span class="sxs-lookup"><span data-stu-id="22adf-119">Each intermediate row indicates the module and the line number of the source code that called the next higher stack frame.</span></span>  
  
 <span data-ttu-id="22adf-120">**“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的所有表达式都是基于当前堆栈帧求值的。</span><span class="sxs-lookup"><span data-stu-id="22adf-120">All expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated based on the current stack frame.</span></span> <span data-ttu-id="22adf-121">查询编辑器窗口显示当前帧的代码。</span><span class="sxs-lookup"><span data-stu-id="22adf-121">The Query Editor window displays the code for the current frame.</span></span> <span data-ttu-id="22adf-122">默认情况下，当前堆栈帧是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器暂停执行时所在的帧。</span><span class="sxs-lookup"><span data-stu-id="22adf-122">By default, the current stack frame is the frame in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger paused execution.</span></span> <span data-ttu-id="22adf-123">如果使另一个帧成为当前堆栈帧，则 **“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的表达式将在新帧环境下重新求值，且查询编辑器窗口中显示此新帧的源代码。</span><span class="sxs-lookup"><span data-stu-id="22adf-123">When you change the current stack frame to another frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated in the context of the new frame, and the source code of the new frame is displayed in the Query Editor window.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="22adf-124">列</span><span class="sxs-lookup"><span data-stu-id="22adf-124">Columns</span></span>  
 <span data-ttu-id="22adf-125">**名称**</span><span class="sxs-lookup"><span data-stu-id="22adf-125">**Name**</span></span>  
 <span data-ttu-id="22adf-126">显示有关调用堆栈中某个模块的信息。</span><span class="sxs-lookup"><span data-stu-id="22adf-126">Displays information about a module on the call stack.</span></span>  
  
 <span data-ttu-id="22adf-127">对于调用堆栈中最下面的一行， **“名称”** 列出查询编辑器源窗口和最先调用此堆栈的行的行号。</span><span class="sxs-lookup"><span data-stu-id="22adf-127">For the bottom row in the call stack, **Name** lists the Query Editor source window and line number of the first call into the stack.</span></span> <span data-ttu-id="22adf-128">对于其他行，“名称”  具有 **Module(Instance.Database)(ParmList) LineNumber** 格式。</span><span class="sxs-lookup"><span data-stu-id="22adf-128">For the other rows, **Name** has the format **Module(Instance.Database)(ParmList) LineNumber**.</span></span>  
  
 <span data-ttu-id="22adf-129">**模块**</span><span class="sxs-lookup"><span data-stu-id="22adf-129">**Module**</span></span>  
 <span data-ttu-id="22adf-130">存储过程、函数或调用下一个帧的存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="22adf-130">Is the name of the stored procedure, function, or stored procedure that called to the next frame.</span></span>  
  
 <span data-ttu-id="22adf-131">**实例.数据库**</span><span class="sxs-lookup"><span data-stu-id="22adf-131">**Instance.Database**</span></span>  
 <span data-ttu-id="22adf-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例和保存模块的数据库。</span><span class="sxs-lookup"><span data-stu-id="22adf-132">Is the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the database that is holding the module.</span></span>  
  
 <span data-ttu-id="22adf-133">**参数列表**</span><span class="sxs-lookup"><span data-stu-id="22adf-133">**ParmList**</span></span>  
 <span data-ttu-id="22adf-134">指示调用模块过程中传递给该模块的各个参数的数据类型、名称和值。</span><span class="sxs-lookup"><span data-stu-id="22adf-134">Indicates the data type, name, and value for each parameter that is passed in during the call to the module.</span></span>  
  
 <span data-ttu-id="22adf-135">**LineNumber**</span><span class="sxs-lookup"><span data-stu-id="22adf-135">**LineNumber**</span></span>  
 <span data-ttu-id="22adf-136">对于除最上面一行以外的所有行， **LineNumber** 指示模块中调用帧的是哪一行。</span><span class="sxs-lookup"><span data-stu-id="22adf-136">For all rows except the top row, **LineNumber** indicates which line in the module called to the frame.</span></span> <span data-ttu-id="22adf-137">对于最上面一行， **“行号”** 指示调试器当前聚焦的行。</span><span class="sxs-lookup"><span data-stu-id="22adf-137">For the top row, **LineNumber** indicates the line on which the debugger is currently focused.</span></span>  
  
 <span data-ttu-id="22adf-138">**语言**</span><span class="sxs-lookup"><span data-stu-id="22adf-138">**Language**</span></span>  
 <span data-ttu-id="22adf-139">如果是 **，则显示** Transact-SQL [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="22adf-139">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22adf-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22adf-140">See Also</span></span>  
 <span data-ttu-id="22adf-141">[Transact-sql 调试器](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="22adf-141">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="22adf-142">[Transact-sql 调试器信息](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="22adf-142">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="22adf-143">逐句通过 Transact-SQL 代码</span><span class="sxs-lookup"><span data-stu-id="22adf-143">Step Through Transact-SQL Code</span></span>](step-through-transact-sql-code.md)  
