---
title: 维护计划（“设计”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.planeditor.f1
- sql12.swb.maint.subplaneditor.f1
- sql12.swb.maint.maintplanproperties.optimizations.f1
ms.assetid: 6d20d4d4-5b3f-454a-8a05-f0aac803c5ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e18b1c3901b37dfe44ad94c8e7a390801ae2f1d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580724"
---
# <a name="maintenance-plan-design-tab"></a><span data-ttu-id="b8a72-102">维护计划（“设计”选项卡）</span><span class="sxs-lookup"><span data-stu-id="b8a72-102">Maintenance Plan (Design Tab)</span></span>
  <span data-ttu-id="b8a72-103">使用 **维护计划（“设计”选项卡）** 可以指定维护计划及其子计划的属性。</span><span class="sxs-lookup"><span data-stu-id="b8a72-103">Use the **Maintenance Plan (Design Tab)** to specify the properties of a maintenance plan and its subplans.</span></span> <span data-ttu-id="b8a72-104">将任务从工具箱拖到计划设计器中。</span><span class="sxs-lookup"><span data-stu-id="b8a72-104">Drag tasks from the Toolbox to the plan designer.</span></span> <span data-ttu-id="b8a72-105">右键单击任务组以创建分支执行路径。</span><span class="sxs-lookup"><span data-stu-id="b8a72-105">Right-click groups of tasks to create branching execution paths.</span></span> <span data-ttu-id="b8a72-106">维护计划将另存为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，它们由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业执行。</span><span class="sxs-lookup"><span data-stu-id="b8a72-106">Maintenance plans are saved as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that are run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b8a72-107">选项</span><span class="sxs-lookup"><span data-stu-id="b8a72-107">Options</span></span>  
 <span data-ttu-id="b8a72-108">**添加子计划**</span><span class="sxs-lookup"><span data-stu-id="b8a72-108">**Add Subplan**</span></span>  
 <span data-ttu-id="b8a72-109">添加可以配置的子计划。</span><span class="sxs-lookup"><span data-stu-id="b8a72-109">Add a subplan that you can configure.</span></span>  
  
 <span data-ttu-id="b8a72-110">**子计划属性**</span><span class="sxs-lookup"><span data-stu-id="b8a72-110">**Subplan Properties**</span></span>  
 <span data-ttu-id="b8a72-111">显示“子计划属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b8a72-111">Display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="b8a72-112">在网格中选择子计划，单击此图标为该子计划输入名称、说明和计划。</span><span class="sxs-lookup"><span data-stu-id="b8a72-112">Select a subplan in the grid and click this icon to enter a name, description, and schedule for the subplan.</span></span> <span data-ttu-id="b8a72-113">还可以在网格中双击该子计划，以显示“子计划属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b8a72-113">You can also double-click the subplan in the grid to display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="b8a72-114">子计划的名称限制在 128 个字符以内，子计划的说明限制在 512 个字符以内。</span><span class="sxs-lookup"><span data-stu-id="b8a72-114">Subplan names are limited to 128 characters and subplan descriptions are limited to 512 characters.</span></span>  
  
 <span data-ttu-id="b8a72-115">**删除所选子计划**</span><span class="sxs-lookup"><span data-stu-id="b8a72-115">**Delete Selected Subplan**</span></span>  
 <span data-ttu-id="b8a72-116">删除所选子计划。</span><span class="sxs-lookup"><span data-stu-id="b8a72-116">Delete the selected subplan.</span></span>  
  
 <span data-ttu-id="b8a72-117">**子计划的计划**</span><span class="sxs-lookup"><span data-stu-id="b8a72-117">**Subplan Schedule**</span></span>  
 <span data-ttu-id="b8a72-118">显示“作业计划属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b8a72-118">Display the **Job Schedule Properties** dialog box.</span></span> <span data-ttu-id="b8a72-119">在网格中选择子计划，单击此图标可配置该子计划的计划。</span><span class="sxs-lookup"><span data-stu-id="b8a72-119">Select a subplan in the grid and click this icon to configure a schedule for the subplan.</span></span>  
  
 <span data-ttu-id="b8a72-120">**删除计划**</span><span class="sxs-lookup"><span data-stu-id="b8a72-120">**Remove Schedule**</span></span>  
 <span data-ttu-id="b8a72-121">从所选子计划中删除计划。</span><span class="sxs-lookup"><span data-stu-id="b8a72-121">Remove a schedule from the selected subplan.</span></span>  
  
 <span data-ttu-id="b8a72-122">**管理连接**</span><span class="sxs-lookup"><span data-stu-id="b8a72-122">**Manage Connections**</span></span>  
 <span data-ttu-id="b8a72-123">显示“管理连接”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b8a72-123">Display the **Manage Connections** dialog box.</span></span> <span data-ttu-id="b8a72-124">用于向维护计划添加其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例连接。</span><span class="sxs-lookup"><span data-stu-id="b8a72-124">Used to add additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance connections to the maintenance plan.</span></span> <span data-ttu-id="b8a72-125">子计划编辑器中的每一个维护任务都可以使用其中的任何连接。</span><span class="sxs-lookup"><span data-stu-id="b8a72-125">Each maintenance task in the subplan editor can use any of these connections.</span></span> <span data-ttu-id="b8a72-126">在执行时，维护计划会使用连接凭据，建立从维护计划服务器到指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="b8a72-126">When executing, the maintenance plan makes a connection from the maintenance plan server to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers specified, using the connection credentials.</span></span>  
  
 <span data-ttu-id="b8a72-127">**报告和记录**</span><span class="sxs-lookup"><span data-stu-id="b8a72-127">**Reporting and Logging**</span></span>  
 <span data-ttu-id="b8a72-128">显示“报告和记录”  对话框，用于管理关于维护计划活动的报告，并配置是在本地服务器还是在远程服务器上进行日志记录。</span><span class="sxs-lookup"><span data-stu-id="b8a72-128">Display the **Reporting and Logging** dialog box, used to manage reports concerning maintenance plan activity, and to configure logging to the local or a remote server.</span></span>  
  
 <span data-ttu-id="b8a72-129">**服务器**</span><span class="sxs-lookup"><span data-stu-id="b8a72-129">**Servers**</span></span>  
 <span data-ttu-id="b8a72-130">显示“服务器”  对话框，用于选择要运行子计划中的任务的服务器。</span><span class="sxs-lookup"><span data-stu-id="b8a72-130">Display the **Servers** dialog box, which is used to select the servers where the subplan tasks will be run.</span></span> <span data-ttu-id="b8a72-131">此选项仅在多服务器环境中的主服务器上启用。</span><span class="sxs-lookup"><span data-stu-id="b8a72-131">This option is enabled only on master servers in multiserver environments.</span></span> <span data-ttu-id="b8a72-132">有关详细信息，请参阅 [创建多服务器环境](../../ssms/agent/create-a-multiserver-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a72-132">For more information, see [Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md).</span></span>  
  
 <span data-ttu-id="b8a72-133">**名称**</span><span class="sxs-lookup"><span data-stu-id="b8a72-133">**Name**</span></span>  
 <span data-ttu-id="b8a72-134">显示维护计划的名称。</span><span class="sxs-lookup"><span data-stu-id="b8a72-134">Display the maintenance plan name.</span></span> <span data-ttu-id="b8a72-135">对于新建的维护计划，该名称是在打开维护计划设计器之前在一个对话框中指定的。</span><span class="sxs-lookup"><span data-stu-id="b8a72-135">For new maintenance plans, the name is specified in a dialog box before the maintenance plan designer opens.</span></span> <span data-ttu-id="b8a72-136">若要重命名维护计划，请在对象资源管理器中右键单击该计划，再单击“重命名”  。</span><span class="sxs-lookup"><span data-stu-id="b8a72-136">To rename a maintenance plan, right-click the plan in Object Explorer, and then click **Rename**.</span></span>  
  
 <span data-ttu-id="b8a72-137">**说明**</span><span class="sxs-lookup"><span data-stu-id="b8a72-137">**Description**</span></span>  
 <span data-ttu-id="b8a72-138">查看或指定维护计划的说明。</span><span class="sxs-lookup"><span data-stu-id="b8a72-138">View or specify a description for the maintenance plan.</span></span> <span data-ttu-id="b8a72-139">说明的最大长度为 512 个字符。</span><span class="sxs-lookup"><span data-stu-id="b8a72-139">The maximum length for a description is 512 characters.</span></span>  
  
 <span data-ttu-id="b8a72-140">**设计器图面**</span><span class="sxs-lookup"><span data-stu-id="b8a72-140">**Designer Surface**</span></span>  
 <span data-ttu-id="b8a72-141">设计和维护维护计划。</span><span class="sxs-lookup"><span data-stu-id="b8a72-141">Design and maintain maintenance plans.</span></span> <span data-ttu-id="b8a72-142">使用设计器图面，可以向计划中添加维护任务、从计划中删除任务、指定任务之间的优先链接以及指示任务分支和并行情况。</span><span class="sxs-lookup"><span data-stu-id="b8a72-142">Use the designer surface to add maintenance tasks to a plan, remove tasks from a plan, specify precedence links between the tasks, and indicate task branching and parallelism.</span></span>  
  
 <span data-ttu-id="b8a72-143">两个任务之间的优先链接会在任务之间建立关系。</span><span class="sxs-lookup"><span data-stu-id="b8a72-143">A precedence link between two tasks establishes a relationship between the tasks.</span></span> <span data-ttu-id="b8a72-144">只有当第一项任务（前置任务  ）的执行结果与指定的条件相匹配时，才执行第二项任务（依赖任务  ）。</span><span class="sxs-lookup"><span data-stu-id="b8a72-144">The second task (the *dependent task*) executes only if the execution result of the first task (the *precedent task*) matches specified criteria.</span></span> <span data-ttu-id="b8a72-145">通常，指定的执行结果为 **“成功”** 、 **“失败”** 或 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="b8a72-145">Typically the execution result specified is **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="b8a72-146">维护计划设计器图面基于 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器图面。</span><span class="sxs-lookup"><span data-stu-id="b8a72-146">The maintenance plan designer surface is based on the [!INCLUDE[ssIS](../../includes/ssis-md.md)] designer surface.</span></span> <span data-ttu-id="b8a72-147">有关详细信息，请参阅 [优先约束](../../integration-services/control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a72-147">For more information, see [Precedence Constraints](../../integration-services/control-flow/precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="b8a72-148">例如，可以将“索引碎片整理”任务指定为只在上一个“检查数据库完整性”任务成功完成之后才能执行。</span><span class="sxs-lookup"><span data-stu-id="b8a72-148">As an example, a Defragment Index Task could be specified to execute only if a previous Check Database Integrity task completed successfully.</span></span> <span data-ttu-id="b8a72-149">使用任务优先关联功能，您还可以在计划中处理错误或失败条件。</span><span class="sxs-lookup"><span data-stu-id="b8a72-149">The task precedence linkage feature also allows for error or failure conditions to be handled in a plan.</span></span> <span data-ttu-id="b8a72-150">例如，如果“检查数据库完整性”任务失败，则“通知操作员”任务可以通知用户或操作员有关失败的消息。</span><span class="sxs-lookup"><span data-stu-id="b8a72-150">For example, if the Check Database Integrity task failed, a Notify Operator task could notify a user or operator about the failure.</span></span>  
  
 <span data-ttu-id="b8a72-151">“任务分支”  示例：指定任务在前置任务失败后执行。</span><span class="sxs-lookup"><span data-stu-id="b8a72-151">Specifying tasks to execute after the failure of a predecessor task is an example of *task branching*.</span></span>  
  
 <span data-ttu-id="b8a72-152">“任务并行”  示例：指定两项或多项任务在前置任务成功完成后同时开始执行。</span><span class="sxs-lookup"><span data-stu-id="b8a72-152">Indicating that two or more tasks begin simultaneously, for example upon the successful completion of a predecessor task, is an example of specifying *task parallelism*.</span></span> <span data-ttu-id="b8a72-153">没有约束的所有任务将并行开始和运行。</span><span class="sxs-lookup"><span data-stu-id="b8a72-153">All tasks with no constraints will start and run in parallel.</span></span> <span data-ttu-id="b8a72-154">使用约束可以延迟任务，以便让较早的任务首先完成。</span><span class="sxs-lookup"><span data-stu-id="b8a72-154">Use constraints to delay  tasks so earlier tasks complete first.</span></span>  
  
 <span data-ttu-id="b8a72-155">在将维护任务放在设计图面上之后，可以根据需要编辑其属性。</span><span class="sxs-lookup"><span data-stu-id="b8a72-155">After a maintenance task is placed on the design surface, its properties can be edited as needed.</span></span> <span data-ttu-id="b8a72-156">例如，在将“备份数据库”任务添加到计划中之后，可以指定要在该任务中备份的特定数据库。</span><span class="sxs-lookup"><span data-stu-id="b8a72-156">For example, the specific database to back up in a Back Up Database Task is specified after the task is added the plan.</span></span> <span data-ttu-id="b8a72-157">设计图面上未正确配置的任务包含一个带有白色 x 的红色图标。</span><span class="sxs-lookup"><span data-stu-id="b8a72-157">Tasks on the design surface that are not properly configured contain a red icon with a white x.</span></span>  
  
 <span data-ttu-id="b8a72-158">若要将维护任务添加到计划中，请从“维护计划任务”  工具箱中将该任务的图标拖到计划设计图面上，或者在该工具箱中双击该任务，从而将该任务添加到当前活动的设计器图面上。</span><span class="sxs-lookup"><span data-stu-id="b8a72-158">To add a maintenance task to a plan, drag the task's icon from the **Maintenance Plan Tasks** toolbox to the plan design surface, or double-click the task in the toolbox, which adds that task to the currently active designer surface.</span></span> <span data-ttu-id="b8a72-159">如果“维护计划中的任务”工具箱不可见，请在 **“视图”菜单中选择“工具箱”**  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  。</span><span class="sxs-lookup"><span data-stu-id="b8a72-159">If the **Maintenance Plan Tasks** toolbox is not visible, choose **Toolbox** from the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **View** menu.</span></span> <span data-ttu-id="b8a72-160">在 **“工具箱”** 窗格中展开 **“维护计划中的任务”** 节点。</span><span class="sxs-lookup"><span data-stu-id="b8a72-160">Expand the **Maintenance Plan Tasks** node in the **Toolbox** pane.</span></span>  
  
 <span data-ttu-id="b8a72-161">若要从计划中删除某项任务，请在设计器图面中选择该任务，按“DELETE”  键，或者右键单击该任务，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="b8a72-161">To remove a task from a plan, select the task in the designer surface and press the **DELETE** key, or right-click the task and then click **Delete**.</span></span>  
  
 <span data-ttu-id="b8a72-162">若要在两项任务之间指定优先链接，请首先将这两项任务拖到设计图面上，然后单击首先出现的任务（前置任务），再将箭头拖到依赖任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-162">To specify precedence links between two tasks, first drag the tasks to the design surface, and then click the task that occurs first (the precedent task), and drag the arrow to the dependent task.</span></span> <span data-ttu-id="b8a72-163">在建立了优先链接之后，设计器会显示一个链接这两个任务的箭头（从前置任务指向依赖任务）。</span><span class="sxs-lookup"><span data-stu-id="b8a72-163">When a precedence link has been established, the designer displays an arrow linking the two tasks, with the precedent task pointing to the dependent task.</span></span> <span data-ttu-id="b8a72-164">默认情况下，在建立链接后，将设置对该链接的约束，以保证只有在前置任务的执行结果为 **“成功”** 时才会执行依赖任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-164">By default, when a link is first established, the link's constraint is set such that the dependent task only executes if the execution result of the precedent task is **Success**.</span></span>  
  
 <span data-ttu-id="b8a72-165">若要更改优先链接的属性，请双击该链接以启动“优先约束编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="b8a72-165">To change the properties of a precedence link, double-click the link to launch the **Precedence Constraint Editor**.</span></span> <span data-ttu-id="b8a72-166">此编辑器提供了多种选项，用来指定逻辑条件以确定是否执行依赖任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-166">This provides many options for specifying the logical conditions which determine whether the dependent task executes.</span></span> <span data-ttu-id="b8a72-167">例如，可以将 **“执行结果”** 设置为 **“失败”** ，在此情况下，只有当前置任务失败时才会执行依赖任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-167">For example, the **Execution result** can be set to **Failure**, in which case the dependent task only executes if the precedent task fails.</span></span> <span data-ttu-id="b8a72-168">通过右键单击链接，然后从上下文菜单上选择“成功”  、“失败”  或“完成”  ，还可以修改该链接的执行结果属性。</span><span class="sxs-lookup"><span data-stu-id="b8a72-168">Modifying the execution result property of a link to **Success**, **Failure**, or **Completion**, can also be accomplished by right-clicking the link and then selecting from the context menu.</span></span>  
  
 <span data-ttu-id="b8a72-169">若要指定任务分支，请首先在两个任务之间创建优先链接。</span><span class="sxs-lookup"><span data-stu-id="b8a72-169">To specify task branching, first create precedence links between two tasks.</span></span> <span data-ttu-id="b8a72-170">然后，将另外一个依赖任务放到设计图面上，针对与第一个依赖任务不同的结果执行该任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-170">Then, put another dependent task on the design surface that executes on a different outcome than the first dependent task.</span></span> <span data-ttu-id="b8a72-171">单击前置任务，然后将第二个箭头从前置任务拖到该依赖任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-171">Click the predecessor task, and drag the second arrow from the precedent task to the dependent task.</span></span> <span data-ttu-id="b8a72-172">若要更改触发依赖任务开始执行的执行结果（“成功”  、“失败”  或“完成”  ），请双击链接箭头，然后修改“执行结果”  字段。</span><span class="sxs-lookup"><span data-stu-id="b8a72-172">To change the execution result (**Success**, **Failure**, **Completion**) that causes a dependent task to execute, double-click the link arrow and modify the **Execution result** field.</span></span> <span data-ttu-id="b8a72-173">或者，右键单击链接，然后从快捷菜单上选择所需的执行结果值。</span><span class="sxs-lookup"><span data-stu-id="b8a72-173">Alternatively, right-click the link and select the desired execution result value from the shortcut menu.</span></span>  
  
 <span data-ttu-id="b8a72-174">若要指定任务并行，请将两个或多个依赖任务链接到单个前置任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-174">To specify task parallelism, link two or more dependent tasks to a single precedent task.</span></span> <span data-ttu-id="b8a72-175">修改优先链接的属性，对于指向并行运行的依赖任务的链接，执行结果字段具有相同的值。</span><span class="sxs-lookup"><span data-stu-id="b8a72-175">Modify the properties of the precedence links so that the links pointing to the dependent tasks that run in parallel have the same value for their execution result fields.</span></span>  
  
## <a name="additional-features-available-from-the-shortcut-menu"></a><span data-ttu-id="b8a72-176">快捷菜单上可用的其他功能</span><span class="sxs-lookup"><span data-stu-id="b8a72-176">Additional Features Available from the Shortcut Menu</span></span>  
 <span data-ttu-id="b8a72-177">若要查看其他选项，请在设计图面上选择一个或多个任务，再单击右键打开快捷菜单。</span><span class="sxs-lookup"><span data-stu-id="b8a72-177">To see additional options, select one or more tasks on the design surface, and then right-click, to open the shortcut menu.</span></span> <span data-ttu-id="b8a72-178">除了常用的 **“剪切”** 、 **“复制”** 、 **“粘贴”** 、 **“删除”** 和 **“全选”** 之外，对于某些任务，还可以使用以下特殊选项：</span><span class="sxs-lookup"><span data-stu-id="b8a72-178">In addition to typical **Cut**, **Copy**, **Paste**, **Delete**, and **Select All**, the following special options are available for some tasks.</span></span>  
  
 <span data-ttu-id="b8a72-179">**添加批注**</span><span class="sxs-lookup"><span data-stu-id="b8a72-179">**Add Annotation**</span></span>  
 <span data-ttu-id="b8a72-180">向设计图面上添加说明性注释。</span><span class="sxs-lookup"><span data-stu-id="b8a72-180">Adds a descriptive note to the design surface.</span></span>  
  
 <span data-ttu-id="b8a72-181">**编辑**</span><span class="sxs-lookup"><span data-stu-id="b8a72-181">**Edit**</span></span>  
 <span data-ttu-id="b8a72-182">打开任务的属性对话框。</span><span class="sxs-lookup"><span data-stu-id="b8a72-182">Opens the property dialog box for the task.</span></span>  
  
 <span data-ttu-id="b8a72-183">**Disable**</span><span class="sxs-lookup"><span data-stu-id="b8a72-183">**Disable**</span></span>  
 <span data-ttu-id="b8a72-184">使任务暂时不可用。</span><span class="sxs-lookup"><span data-stu-id="b8a72-184">Makes the task temporarily unavailable.</span></span>  
  
 <span data-ttu-id="b8a72-185">**启用**</span><span class="sxs-lookup"><span data-stu-id="b8a72-185">**Enable**</span></span>  
 <span data-ttu-id="b8a72-186">恢复禁用的任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-186">Restores a disabled task.</span></span>  
  
 <span data-ttu-id="b8a72-187">**分组**</span><span class="sxs-lookup"><span data-stu-id="b8a72-187">**Group**</span></span>  
 <span data-ttu-id="b8a72-188">创建包含一项或多项任务的组。</span><span class="sxs-lookup"><span data-stu-id="b8a72-188">Creates a group that contains one or more tasks.</span></span>  
  
 <span data-ttu-id="b8a72-189">**取消分组**</span><span class="sxs-lookup"><span data-stu-id="b8a72-189">**Ungroup**</span></span>  
 <span data-ttu-id="b8a72-190">从组中删除任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-190">Removes tasks from a group.</span></span>  
  
 <span data-ttu-id="b8a72-191">**自动调整大小**</span><span class="sxs-lookup"><span data-stu-id="b8a72-191">**Autosize**</span></span>  
 <span data-ttu-id="b8a72-192">将每项任务的大小设置为该任务的最佳大小。</span><span class="sxs-lookup"><span data-stu-id="b8a72-192">Sets the size of each task to the optimal size for that task.</span></span>  
  
 <span data-ttu-id="b8a72-193">**折叠**</span><span class="sxs-lookup"><span data-stu-id="b8a72-193">**Collapse**</span></span>  
 <span data-ttu-id="b8a72-194">隐藏组中的任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-194">Hides tasks within a group.</span></span>  
  
 <span data-ttu-id="b8a72-195">**展开**</span><span class="sxs-lookup"><span data-stu-id="b8a72-195">**Expand**</span></span>  
 <span data-ttu-id="b8a72-196">显示组中以前使用“折叠”  隐藏的任务。</span><span class="sxs-lookup"><span data-stu-id="b8a72-196">Shows the tasks in a group that were previously hidden using **Collapse**.</span></span>  
  
 <span data-ttu-id="b8a72-197">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="b8a72-197">**Zoom**</span></span>  
 <span data-ttu-id="b8a72-198">更改设计图面上任务的大小。</span><span class="sxs-lookup"><span data-stu-id="b8a72-198">Changes the size of the tasks on the design surface</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a72-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8a72-199">See Also</span></span>  
 <span data-ttu-id="b8a72-200">[维护计划](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="b8a72-200">[Maintenance Plans](maintenance-plans.md) </span></span>  
 [<span data-ttu-id="b8a72-201">创建维护计划</span><span class="sxs-lookup"><span data-stu-id="b8a72-201">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)  
  
  
