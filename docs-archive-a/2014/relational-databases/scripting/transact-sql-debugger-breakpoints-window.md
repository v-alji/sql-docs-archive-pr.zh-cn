---
title: “断点”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Breakpoints Window [Transact-SQL]
ms.assetid: bad88d10-fdd5-4d3d-b5ea-a4f063847485
author: rothja
ms.author: jroth
ms.openlocfilehash: 077d501e581ed5baaac45cc6bbbb34e0040730e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589492"
---
# <a name="breakpoints-window"></a><span data-ttu-id="aefeb-102">“断点”窗口</span><span class="sxs-lookup"><span data-stu-id="aefeb-102">Breakpoints Window</span></span>
  <span data-ttu-id="aefeb-103">**“断点”** 窗口列出在当前 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中设置的所有断点。</span><span class="sxs-lookup"><span data-stu-id="aefeb-103">The **Breakpoints** window lists all the breakpoints that are set in the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="aefeb-104">若要管理断点，请使用“断点”窗口中的工具栏。 </span><span class="sxs-lookup"><span data-stu-id="aefeb-104">To manage the breakpoints, use the toolbar in the **Breakpoints** window.</span></span> <span data-ttu-id="aefeb-105">断点是代码中的某些位置，在调试模式下执行在这些位置暂停，以便您可以查看调试数据。</span><span class="sxs-lookup"><span data-stu-id="aefeb-105">Breakpoints are locations in the code where execution pauses in debug mode so that you can view debugging data.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="aefeb-106">任务列表</span><span class="sxs-lookup"><span data-stu-id="aefeb-106">Task List</span></span>  
 <span data-ttu-id="aefeb-107">**访问“断点”窗口**</span><span class="sxs-lookup"><span data-stu-id="aefeb-107">**To access the Breakpoints window**</span></span>  
  
-   <span data-ttu-id="aefeb-108">在 **“调试”** 菜单上单击 **“窗口”**，然后单击 **“断点”**。</span><span class="sxs-lookup"><span data-stu-id="aefeb-108">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
## <a name="breakpoints-window-columns"></a><span data-ttu-id="aefeb-109">“断点”窗口中包含的列</span><span class="sxs-lookup"><span data-stu-id="aefeb-109">Breakpoints Window Columns</span></span>  
 <span data-ttu-id="aefeb-110">默认情况下， **“断点”** 窗口列出以下列。</span><span class="sxs-lookup"><span data-stu-id="aefeb-110">By default, the **Breakpoints** window lists the following columns.</span></span>  
  
 <span data-ttu-id="aefeb-111">**名称**</span><span class="sxs-lookup"><span data-stu-id="aefeb-111">**Name**</span></span>  
 <span data-ttu-id="aefeb-112">显示断点名称。</span><span class="sxs-lookup"><span data-stu-id="aefeb-112">Displays the name of the breakpoint.</span></span> <span data-ttu-id="aefeb-113">断点名称是由调试器提供的。</span><span class="sxs-lookup"><span data-stu-id="aefeb-113">Breakpoint names are provided by the debugger.</span></span> <span data-ttu-id="aefeb-114">该名称含有包含此断点的数据库引擎查询编辑器窗口的名称和查询编辑器中设有此断点的行的行号。</span><span class="sxs-lookup"><span data-stu-id="aefeb-114">This name includes the name of Database Engine Query Editor window that contains the breakpoint, and the line number in the Query Editor on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="aefeb-115">**条件**</span><span class="sxs-lookup"><span data-stu-id="aefeb-115">**Condition**</span></span>  
 <span data-ttu-id="aefeb-116">显示“(无条件)”  。</span><span class="sxs-lookup"><span data-stu-id="aefeb-116">Displays **(no condition)**.</span></span> <span data-ttu-id="aefeb-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器不支持设置断点条件。</span><span class="sxs-lookup"><span data-stu-id="aefeb-117">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint conditions.</span></span>  
  
 <span data-ttu-id="aefeb-118">**命中计数**</span><span class="sxs-lookup"><span data-stu-id="aefeb-118">**Hit Count**</span></span>  
 <span data-ttu-id="aefeb-119">显示“始终中断”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aefeb-119">Displays**breaks always**.</span></span>  
  
 <span data-ttu-id="aefeb-120">在 **“列”** 列表中选择以下列后，可以添加或删除这些列。</span><span class="sxs-lookup"><span data-stu-id="aefeb-120">You can add and remove the following columns by selecting them on the **Columns** list.</span></span>  
  
 <span data-ttu-id="aefeb-121">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="aefeb-121">**Filter**</span></span>  
 <span data-ttu-id="aefeb-122">显示“(无)”  。</span><span class="sxs-lookup"><span data-stu-id="aefeb-122">Displays **(none)**.</span></span> <span data-ttu-id="aefeb-123">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器不支持设置断点筛选器。</span><span class="sxs-lookup"><span data-stu-id="aefeb-123">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint filters.</span></span>  
  
 <span data-ttu-id="aefeb-124">**命中条件**</span><span class="sxs-lookup"><span data-stu-id="aefeb-124">**When Hit**</span></span>  
 <span data-ttu-id="aefeb-125">显示“中断”  。</span><span class="sxs-lookup"><span data-stu-id="aefeb-125">Displays **Break**.</span></span>  
  
 <span data-ttu-id="aefeb-126">**语言**</span><span class="sxs-lookup"><span data-stu-id="aefeb-126">**Language**</span></span>  
 <span data-ttu-id="aefeb-127">如果是 **，则显示** Transact-SQL [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aefeb-127">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="aefeb-128">**Function**</span><span class="sxs-lookup"><span data-stu-id="aefeb-128">**Function**</span></span>  
 <span data-ttu-id="aefeb-129">显示设有断点的行的行号。</span><span class="sxs-lookup"><span data-stu-id="aefeb-129">Displays the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="aefeb-130">**File**</span><span class="sxs-lookup"><span data-stu-id="aefeb-130">**File**</span></span>  
 <span data-ttu-id="aefeb-131">显示包含断点的源文件的名称和设有此断点的行的行号。</span><span class="sxs-lookup"><span data-stu-id="aefeb-131">Displays the name of the source file that contains the breakpoint, and the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="aefeb-132">**Address**</span><span class="sxs-lookup"><span data-stu-id="aefeb-132">**Address**</span></span>  
 <span data-ttu-id="aefeb-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="aefeb-133">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="aefeb-134">**处理**</span><span class="sxs-lookup"><span data-stu-id="aefeb-134">**Process**</span></span>  
 <span data-ttu-id="aefeb-135">显示“[SQL]”  ，则表明这是一个 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 进程。</span><span class="sxs-lookup"><span data-stu-id="aefeb-135">Displays **[SQL]** to indicate that this is a [!INCLUDE[ssDE](../../includes/ssde-md.md)] process.</span></span> <span data-ttu-id="aefeb-136">后面跟随代码在其中执行的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="aefeb-136">This is followed by the name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the code executes.</span></span>  
  
## <a name="breakpoints-window-toolbar"></a><span data-ttu-id="aefeb-137">“断点”窗口工具栏</span><span class="sxs-lookup"><span data-stu-id="aefeb-137">Breakpoints Window Toolbar</span></span>  
 <span data-ttu-id="aefeb-138">如果当前 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口具有活动断点，则 **“断点”** 窗口将显示一个可用于管理这些断点的工具栏。</span><span class="sxs-lookup"><span data-stu-id="aefeb-138">When the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window has active breakpoints, the **Breakpoints** window displays a toolbar that can be used to manage the breakpoints.</span></span>  
  
 <span data-ttu-id="aefeb-139">**删除**</span><span class="sxs-lookup"><span data-stu-id="aefeb-139">**Delete**</span></span>  
 <span data-ttu-id="aefeb-140">删除所选断点。</span><span class="sxs-lookup"><span data-stu-id="aefeb-140">Deletes the selected breakpoint.</span></span>  
  
 <span data-ttu-id="aefeb-141">**删除全部断点**</span><span class="sxs-lookup"><span data-stu-id="aefeb-141">**Delete All Breakpoints**</span></span>  
 <span data-ttu-id="aefeb-142">删除“断点”  窗口中显示的全部断点。</span><span class="sxs-lookup"><span data-stu-id="aefeb-142">Deletes all breakpoints that are displayed in the **Breakpoints** window.</span></span>  
  
 <span data-ttu-id="aefeb-143">**禁用所有断点**</span><span class="sxs-lookup"><span data-stu-id="aefeb-143">**Disable All Breakpoints**</span></span>  
 <span data-ttu-id="aefeb-144">禁用所有断点，以使其不再中断代码执行，但保留断点。</span><span class="sxs-lookup"><span data-stu-id="aefeb-144">Disables all breakpoints so that they no longer stop code execution; however, the breakpoints remain.</span></span> <span data-ttu-id="aefeb-145">禁用所有断点后，该按钮即变为 **“启用所有断点”** 。</span><span class="sxs-lookup"><span data-stu-id="aefeb-145">When all the breakpoints are disabled, this button becomes **Enable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="aefeb-146">**“启用所有断点”**</span><span class="sxs-lookup"><span data-stu-id="aefeb-146">**Enable All Breakpoints**</span></span>  
 <span data-ttu-id="aefeb-147">启用所有断点，以使它们中断代码执行。</span><span class="sxs-lookup"><span data-stu-id="aefeb-147">Enables all breakpoints so that they stop code execution.</span></span> <span data-ttu-id="aefeb-148">启用所有断点后，该按钮即变为 **“禁用所有断点”** 。</span><span class="sxs-lookup"><span data-stu-id="aefeb-148">When all breakpoints are enabled, this button becomes **Disable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="aefeb-149">**转到源代码**</span><span class="sxs-lookup"><span data-stu-id="aefeb-149">**Go To Source Code**</span></span>  
 <span data-ttu-id="aefeb-150">将光标定位在查询编辑器中包含所选断点的行。</span><span class="sxs-lookup"><span data-stu-id="aefeb-150">Positions the cursor on the line in the Query Editor that contains the selected breakpoint.</span></span>  
  
 <span data-ttu-id="aefeb-151">**“列”**</span><span class="sxs-lookup"><span data-stu-id="aefeb-151">**Columns**</span></span>  
 <span data-ttu-id="aefeb-152">列出所有可以在“断点”  窗口中显示的列。</span><span class="sxs-lookup"><span data-stu-id="aefeb-152">Lists all the columns that can be displayed in the **Breakpoints** window.</span></span> <span data-ttu-id="aefeb-153">复选框指示所显示的列。</span><span class="sxs-lookup"><span data-stu-id="aefeb-153">A check box indicates the columns that are displayed.</span></span> <span data-ttu-id="aefeb-154">若要在 **“断点”** 窗口中添加或删除某一列，请在此列表中选择该列。</span><span class="sxs-lookup"><span data-stu-id="aefeb-154">To add or remove a column in the **Breakpoints** window, select the column on the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefeb-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aefeb-155">See Also</span></span>  
 [<span data-ttu-id="aefeb-156">Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="aefeb-156">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
