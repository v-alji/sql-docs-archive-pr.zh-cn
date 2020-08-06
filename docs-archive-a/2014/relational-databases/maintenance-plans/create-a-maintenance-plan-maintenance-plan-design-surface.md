---
title: 创建维护计划（维护计划设计图面）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77e347720824198ba7d6abaddedd7a581ace98a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589058"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a><span data-ttu-id="167b5-102">创建维护计划（维护计划设计图面）</span><span class="sxs-lookup"><span data-stu-id="167b5-102">Create a Maintenance Plan (Maintenance Plan Design Surface)</span></span>
  <span data-ttu-id="167b5-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中使用维护计划设计图面创建单个服务器或多服务器维护计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Design Surface in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="167b5-104">尽管 **“维护计划向导”** 是创建基本维护计划的最佳方法，但使用设计图面创建计划允许您使用增强的工作流。</span><span class="sxs-lookup"><span data-stu-id="167b5-104">While the **Maintenance Plan Wizard** is best for creating basic maintenance plans, creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="167b5-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="167b5-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="167b5-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="167b5-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="167b5-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="167b5-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="167b5-108">安全性</span><span class="sxs-lookup"><span data-stu-id="167b5-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="167b5-109">使用维护计划设计图面创建维护计划</span><span class="sxs-lookup"><span data-stu-id="167b5-109">Creating a maintenance plan using the Maintenance Plan Design Surface</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="167b5-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="167b5-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="167b5-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="167b5-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="167b5-112">若要创建多服务器维护计划，必须配置包含一个主服务器和一个（或多个）目标服务器的多服务器环境。</span><span class="sxs-lookup"><span data-stu-id="167b5-112">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="167b5-113">必须在主服务器上创建和维护多服务器维护计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-113">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="167b5-114">在目标服务器上可以查看这些计划，但不能进行维护。</span><span class="sxs-lookup"><span data-stu-id="167b5-114">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="167b5-115">**db_ssisadmin** 和 **dc_admin** 角色的成员可以将其特权提升为 **sysadmin**。</span><span class="sxs-lookup"><span data-stu-id="167b5-115">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="167b5-116">因为这些角色可以修改 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 **代理的** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全上下文可以执行这些包，所以可以实现特权提升。</span><span class="sxs-lookup"><span data-stu-id="167b5-116">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="167b5-117">若要防止在运行维护计划、数据收集组和其它 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时提升特权，请将运行包的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业配置为具有有限特权的代理帐户，或仅将 **sysadmin** 成员添加到 **db_ssisadmin** 和 **dc_admin** 角色。</span><span class="sxs-lookup"><span data-stu-id="167b5-117">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="167b5-118">Security</span><span class="sxs-lookup"><span data-stu-id="167b5-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="167b5-119">权限</span><span class="sxs-lookup"><span data-stu-id="167b5-119">Permissions</span></span>  
 <span data-ttu-id="167b5-120">若要创建或管理维护计划，您必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="167b5-120">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="167b5-121">对象资源管理器只为属于 **sysadmin** 固定服务器角色成员的用户显示 **“维护计划”** 节点。</span><span class="sxs-lookup"><span data-stu-id="167b5-121">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-design-surface"></a><a name="SSMSProcedure"></a> <span data-ttu-id="167b5-122">使用维护计划设计图面</span><span class="sxs-lookup"><span data-stu-id="167b5-122">Using Maintenance Plan Design Surface</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="167b5-123">创建维护计划</span><span class="sxs-lookup"><span data-stu-id="167b5-123">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="167b5-124">在对象资源管理器中，单击加号以便展开您要创建维护计划的服务器。</span><span class="sxs-lookup"><span data-stu-id="167b5-124">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="167b5-125">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="167b5-125">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="167b5-126">右键单击“维护计划”  文件夹，然后选择“新建维护计划” 。</span><span class="sxs-lookup"><span data-stu-id="167b5-126">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="167b5-127">在 **“新建维护计划”** 对话框的 **“名称”** 框中，为该计划键入一个名称，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-127">In the **New Maintenance Plan** dialog box, in the **Name** box, type a name for the plan and click **OK**.</span></span> <span data-ttu-id="167b5-128">这将打开工具箱和 maintenance_plan_name [设计] 图面，其中包含在主网格中创建的 Subplan_1 子计划 。</span><span class="sxs-lookup"><span data-stu-id="167b5-128">This opens the  Toolbox and the _maintenance_plan_name_ **[Design]** surface with the **Subplan_1** subplan created in the main grid.</span></span>  
  
     <span data-ttu-id="167b5-129">在设计空间的标头中提供以下选项。</span><span class="sxs-lookup"><span data-stu-id="167b5-129">The following options are available in the design space's header.</span></span>  
  
     <span data-ttu-id="167b5-130">**添加子计划**</span><span class="sxs-lookup"><span data-stu-id="167b5-130">**Add Subplan**</span></span>  
     <span data-ttu-id="167b5-131">添加可以配置的子计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-131">Adds a subplan that you can configure.</span></span>  
  
     <span data-ttu-id="167b5-132">**子计划属性**</span><span class="sxs-lookup"><span data-stu-id="167b5-132">**Subplan Properties**</span></span>  
     <span data-ttu-id="167b5-133">为在主网格中选择的子计划显示“子计划属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-133">Displays the **Subplan Properties** dialog box for the selected subplan in the main grid.</span></span> <span data-ttu-id="167b5-134">或者，还可以在网格中双击某一子计划，以显示“子计划属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-134">Alternately, double-click a subplan in the grid to display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="167b5-135">下面提供了有关此对话框的详细信息。</span><span class="sxs-lookup"><span data-stu-id="167b5-135">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="167b5-136">**删除所选子计划**</span><span class="sxs-lookup"><span data-stu-id="167b5-136">**Delete Selected Subplan**</span></span>  
     <span data-ttu-id="167b5-137">删除所选子计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-137">Deletes the selected subplan.</span></span>  
  
     <span data-ttu-id="167b5-138">**子计划的计划**</span><span class="sxs-lookup"><span data-stu-id="167b5-138">**Subplan Schedule**</span></span>  
     <span data-ttu-id="167b5-139">为选择的子计划显示“新建作业计划”  对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-139">Displays the **New Job Schedule** dialog box for the selected subplan.</span></span>  
  
     <span data-ttu-id="167b5-140">**删除计划**</span><span class="sxs-lookup"><span data-stu-id="167b5-140">**Remove Schedule**</span></span>  
     <span data-ttu-id="167b5-141">从所选子计划中删除计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-141">Removes a schedule from the selected subplan.</span></span>  
  
     <span data-ttu-id="167b5-142">**管理连接**</span><span class="sxs-lookup"><span data-stu-id="167b5-142">**Manage Connections**</span></span>  
     <span data-ttu-id="167b5-143">显示“管理连接”  对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-143">Displays the **Manage Connections** dialog box.</span></span> <span data-ttu-id="167b5-144">用于向维护计划添加其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例连接。</span><span class="sxs-lookup"><span data-stu-id="167b5-144">Used to add additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance connections to the maintenance plan.</span></span> <span data-ttu-id="167b5-145">下面提供了有关此对话框的详细信息。</span><span class="sxs-lookup"><span data-stu-id="167b5-145">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="167b5-146">**报告和记录**</span><span class="sxs-lookup"><span data-stu-id="167b5-146">**Reporting and Logging**</span></span>  
     <span data-ttu-id="167b5-147">显示“报告和记录”  对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-147">Displays the **Reporting and Logging** dialog box.</span></span> <span data-ttu-id="167b5-148">下面提供了有关此对话框的详细信息。</span><span class="sxs-lookup"><span data-stu-id="167b5-148">See below for more information on this dialog box.</span></span>  
  
     <span data-ttu-id="167b5-149">**服务器**</span><span class="sxs-lookup"><span data-stu-id="167b5-149">**Servers**</span></span>  
     <span data-ttu-id="167b5-150">显示“服务器”  对话框，用于选择要运行子计划中的任务的服务器。</span><span class="sxs-lookup"><span data-stu-id="167b5-150">Display the **Servers** dialog box, which is used to select the servers where the subplan tasks will be run.</span></span> <span data-ttu-id="167b5-151">此选项仅在多服务器环境中的主服务器上启用。</span><span class="sxs-lookup"><span data-stu-id="167b5-151">This option is enabled only on master servers in multiserver environments.</span></span> <span data-ttu-id="167b5-152">有关详细信息，请参阅[创建多服务器环境](../../ssms/agent/create-a-multiserver-environment.md)和[维护计划（服务器）](maintenance-plan-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="167b5-152">For more information, see [Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) and [Maintenance Plan &#40;Servers&#41;](maintenance-plan-servers.md).</span></span>  
  
     <span data-ttu-id="167b5-153">**名称**</span><span class="sxs-lookup"><span data-stu-id="167b5-153">**Name**</span></span>  
     <span data-ttu-id="167b5-154">显示维护计划的名称。</span><span class="sxs-lookup"><span data-stu-id="167b5-154">Display the maintenance plan name.</span></span> <span data-ttu-id="167b5-155">对于新建的维护计划，该名称是在打开维护计划设计器之前在一个对话框中指定的。</span><span class="sxs-lookup"><span data-stu-id="167b5-155">For new maintenance plans, the name is specified in a dialog box before the maintenance plan designer opens.</span></span> <span data-ttu-id="167b5-156">若要重命名维护计划，请在对象资源管理器中右键单击该计划，再单击“重命名” 。</span><span class="sxs-lookup"><span data-stu-id="167b5-156">To rename a maintenance plan, right-click the plan in Object Explorer, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="167b5-157">**说明**</span><span class="sxs-lookup"><span data-stu-id="167b5-157">**Description**</span></span>  
     <span data-ttu-id="167b5-158">查看或指定维护计划的说明。</span><span class="sxs-lookup"><span data-stu-id="167b5-158">View or specify a description for the maintenance plan.</span></span> <span data-ttu-id="167b5-159">说明的最大长度为 512 个字符。</span><span class="sxs-lookup"><span data-stu-id="167b5-159">The maximum length for a description is 512 characters.</span></span>  
  
     <span data-ttu-id="167b5-160">**设计器图面**</span><span class="sxs-lookup"><span data-stu-id="167b5-160">**Designer Surface**</span></span>  
     <span data-ttu-id="167b5-161">设计和维护维护计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-161">Design and maintain maintenance plans.</span></span> <span data-ttu-id="167b5-162">使用设计器图面，可以向计划中添加维护任务、从计划中删除任务、指定任务之间的优先链接以及指示任务分支和并行情况。</span><span class="sxs-lookup"><span data-stu-id="167b5-162">Use the designer surface to add maintenance tasks to a plan, remove tasks from a plan, specify precedence links between the tasks, and indicate task branching and parallelism.</span></span>  
  
     <span data-ttu-id="167b5-163">两个任务之间的优先链接会在任务之间建立关系。</span><span class="sxs-lookup"><span data-stu-id="167b5-163">A precedence link between two tasks establishes a relationship between the tasks.</span></span> <span data-ttu-id="167b5-164">只有当第一项任务（前置任务 ）的执行结果与指定的条件相匹配时，才执行第二项任务（依赖任务 ）。</span><span class="sxs-lookup"><span data-stu-id="167b5-164">The second task (the *dependent task*) executes only if the execution result of the first task (the *precedent task*) matches specified criteria.</span></span> <span data-ttu-id="167b5-165">通常，指定的执行结果为 **“成功”** 、 **“失败”** 或 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-165">Typically the execution result specified is **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="167b5-166">有关详细信息，请参阅下面的步骤 **8** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-166">For more information, see step **8** below.</span></span>  
  
5.  <span data-ttu-id="167b5-167">在设计图面的标头中，双击 **Subplan_1** ，然后在“子计划属性”  对话框中输入子计划的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="167b5-167">In the design space's header, double-click **Subplan_1** and enter a name and description for the subplan in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="167b5-168">在 **“子计划属性”** 对话框中提供以下选项。</span><span class="sxs-lookup"><span data-stu-id="167b5-168">The following options are available in the **Subplan Properties** dialog box.</span></span>  
  
     <span data-ttu-id="167b5-169">**名称**</span><span class="sxs-lookup"><span data-stu-id="167b5-169">**Name**</span></span>  
     <span data-ttu-id="167b5-170">子计划的名称。</span><span class="sxs-lookup"><span data-stu-id="167b5-170">The name of the subplan.</span></span>  
  
     <span data-ttu-id="167b5-171">**说明**</span><span class="sxs-lookup"><span data-stu-id="167b5-171">**Description**</span></span>  
     <span data-ttu-id="167b5-172">子计划的简短说明。</span><span class="sxs-lookup"><span data-stu-id="167b5-172">A brief description of the subplan.</span></span>  
  
     <span data-ttu-id="167b5-173">**“计划”**</span><span class="sxs-lookup"><span data-stu-id="167b5-173">**Schedule**</span></span>  
     <span data-ttu-id="167b5-174">指示子计划将会运行的计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-174">Indicates on what schedule the subplan will be run.</span></span> <span data-ttu-id="167b5-175">单击 **“子计划的计划”** 以便打开 **“新建作业计划”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-175">Click **Subplan Schedule** to open the **New Job Schedule** dialog box.</span></span> <span data-ttu-id="167b5-176">单击 **“删除计划”** 可从子计划中删除计划。</span><span class="sxs-lookup"><span data-stu-id="167b5-176">Click **Remove Schedule** to delete the schedule from the subplan.</span></span>  
  
     <span data-ttu-id="167b5-177"> “运行身份”列表</span><span class="sxs-lookup"><span data-stu-id="167b5-177">**Run as** list</span></span>  
     <span data-ttu-id="167b5-178">选择要用于运行此子任务的帐户。</span><span class="sxs-lookup"><span data-stu-id="167b5-178">Select the account to use to run this subtask.</span></span>  
  
6.  <span data-ttu-id="167b5-179">单击 **“子计划的计划”** 以便在 **“新建作业计划”** 对话框中输入计划详细信息。</span><span class="sxs-lookup"><span data-stu-id="167b5-179">Click **Subplan Schedule** to enter schedule details in the **New Job Schedule** dialog box.</span></span>  
  
7.  <span data-ttu-id="167b5-180">若要生成子计划，请将 **“工具箱”** 中的任务流元素拖放到计划设计图面。</span><span class="sxs-lookup"><span data-stu-id="167b5-180">To build the subplan, drag and drop task flow elements from the **Toolbox** to the plan design surface.</span></span> <span data-ttu-id="167b5-181">双击任务打开对话框来配置任务选项。</span><span class="sxs-lookup"><span data-stu-id="167b5-181">Double-click tasks to open dialog boxes to configure the task options.</span></span>  
  
     <span data-ttu-id="167b5-182">在 **“工具箱”** 中提供以下维护计划任务：</span><span class="sxs-lookup"><span data-stu-id="167b5-182">The following maintenance plan tasks are available in the **Toolbox**:</span></span>  
  
    -   <span data-ttu-id="167b5-183">**“备份数据库”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-183">**Back up Database Task**</span></span>  
  
    -   <span data-ttu-id="167b5-184">**“检查数据库完整性”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-184">**Check Database Integrity Task**</span></span>  
  
    -   <span data-ttu-id="167b5-185">**“执行 SQL Server 代理作业”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-185">**Execute SQL Server Agent Job Task**</span></span>  
  
    -   <span data-ttu-id="167b5-186">**执行 T-SQL 语句任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-186">**Execute T-SQL Statement Task**</span></span>  
  
    -   <span data-ttu-id="167b5-187">**“清除历史记录”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-187">**History Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="167b5-188">**“清除维护”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-188">**Maintenance Cleanup Task**</span></span>  
  
    -   <span data-ttu-id="167b5-189">**“通知操作员”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-189">**Notify Operator Task**</span></span>  
  
    -   <span data-ttu-id="167b5-190">**“重新生成索引”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-190">**Rebuild Index Task**</span></span>  
  
    -   <span data-ttu-id="167b5-191">**“重新组织索引”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-191">**Reorganize Index Task**</span></span>  
  
    -   <span data-ttu-id="167b5-192">**收缩数据库任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-192">**Shrink Database Task**</span></span>  
  
    -   <span data-ttu-id="167b5-193">**“更新统计信息”任务**</span><span class="sxs-lookup"><span data-stu-id="167b5-193">**Update Statistics Task**</span></span>  
  
     <span data-ttu-id="167b5-194">向 **“工具箱”** 中添加任务：</span><span class="sxs-lookup"><span data-stu-id="167b5-194">To add tasks to the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="167b5-195">在 **“工具”** 菜单上，单击 **“选择工具箱项”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-195">On the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="167b5-196">选择想要显示在 **“工具箱”** 中的工具，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-196">Select the tools you want to appear in the **Toolbox**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="167b5-197">向 **“工具箱”** 中添加维护计划任务也会使这些任务可用于 **“维护计划向导”** 中。</span><span class="sxs-lookup"><span data-stu-id="167b5-197">Adding maintenance plan tasks to the **Toolbox** also makes them available in the **Maintenance Plan Wizard**.</span></span> <span data-ttu-id="167b5-198">有关上述各个任务的详细信息，请参阅“启动维护计划向导”下的 [使用维护计划向导](use-the-maintenance-plan-wizard.md#SSMSProcedure)。</span><span class="sxs-lookup"><span data-stu-id="167b5-198">For more information on the individual tasks above, see [Using Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md#SSMSProcedure) under **Start the Maintenance Plan Wizard**.</span></span>  
  
8.  <span data-ttu-id="167b5-199">定义各任务之间的工作流：</span><span class="sxs-lookup"><span data-stu-id="167b5-199">To define a workflow between tasks:</span></span>  
  
    1.  <span data-ttu-id="167b5-200">右键单击前置任务，然后选择“添加优先约束” 。</span><span class="sxs-lookup"><span data-stu-id="167b5-200">Right-click the precedent task and select **Add Precedence Constraint**.</span></span>  
  
    2.  <span data-ttu-id="167b5-201">在 **“控制流”** 对话框的 **“到”** 列表中，选择依赖任务，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-201">In the **Control Flow** dialog box, in the **To** list, select the dependent task and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="167b5-202">双击两个任务之间的连接器以便打开 **“优先约束编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-202">Double click the connector between the two tasks to open the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="167b5-203">在 **“优先约束编辑器”** 对话框中提供以下选项。</span><span class="sxs-lookup"><span data-stu-id="167b5-203">The following options are available in the **Precedence Constraint Editor** dialog box.</span></span>  
  
         <span data-ttu-id="167b5-204">**约束选项**</span><span class="sxs-lookup"><span data-stu-id="167b5-204">**Constraint option**</span></span>  
         <span data-ttu-id="167b5-205">定义约束在两个任务之间的工作方式。</span><span class="sxs-lookup"><span data-stu-id="167b5-205">Defines how a constraint works between two tasks.</span></span>  
  
         <span data-ttu-id="167b5-206">  “求值运算”列表</span><span class="sxs-lookup"><span data-stu-id="167b5-206">**Evaluation operation**  list</span></span>  
         <span data-ttu-id="167b5-207">指定优先约束使用的求值运算。</span><span class="sxs-lookup"><span data-stu-id="167b5-207">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="167b5-208">运算包括：“约束”、“表达式”、“表达式和约束”和“表达式或约束”。</span><span class="sxs-lookup"><span data-stu-id="167b5-208">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
         <span data-ttu-id="167b5-209"> “值”列表</span><span class="sxs-lookup"><span data-stu-id="167b5-209">**Value** list</span></span>  
         <span data-ttu-id="167b5-210">指定约束值：“成功”、“失败”或“完成”。</span><span class="sxs-lookup"><span data-stu-id="167b5-210">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="167b5-211">**“成功”** 的默认值。</span><span class="sxs-lookup"><span data-stu-id="167b5-211">**Success** is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="167b5-212">优先约束线的含义：绿色表示“成功” ，红色表示“失败” ，蓝色表示“完成” 。</span><span class="sxs-lookup"><span data-stu-id="167b5-212">The precedence constraint line is green for **Success**, red for **Failure**, and blue for **Completion**.</span></span>  
  
         <span data-ttu-id="167b5-213">**表达式**</span><span class="sxs-lookup"><span data-stu-id="167b5-213">**Expression**</span></span>  
         <span data-ttu-id="167b5-214">若要使用“表达式” 、“表达式和约束” 或“表达式或约束” 运算，请键入表达式。</span><span class="sxs-lookup"><span data-stu-id="167b5-214">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression.</span></span> <span data-ttu-id="167b5-215">表达式的计算结果必须为布尔值。</span><span class="sxs-lookup"><span data-stu-id="167b5-215">The expression must evaluate to a Boolean.</span></span>  
  
         <span data-ttu-id="167b5-216">**Test**</span><span class="sxs-lookup"><span data-stu-id="167b5-216">**Test**</span></span>  
         <span data-ttu-id="167b5-217">验证表达式。</span><span class="sxs-lookup"><span data-stu-id="167b5-217">Validate the expression.</span></span>  
  
         <span data-ttu-id="167b5-218">**多个约束**</span><span class="sxs-lookup"><span data-stu-id="167b5-218">**Multiple constraints**</span></span>  
         <span data-ttu-id="167b5-219">定义多个约束如何交互操作以便控制约束任务的执行。</span><span class="sxs-lookup"><span data-stu-id="167b5-219">Define how multiple constraints interoperate to control the execution of the constrained task.</span></span>  
  
         <span data-ttu-id="167b5-220">**逻辑与**</span><span class="sxs-lookup"><span data-stu-id="167b5-220">**Logical AND**</span></span>  
         <span data-ttu-id="167b5-221">选择此选项可以指定：同一个可执行文件的多个优先约束必须一起计算。</span><span class="sxs-lookup"><span data-stu-id="167b5-221">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="167b5-222">所有约束的计算结果都必须为 True。</span><span class="sxs-lookup"><span data-stu-id="167b5-222">All constraints must evaluate to True.</span></span> <span data-ttu-id="167b5-223">此选项为默认值。</span><span class="sxs-lookup"><span data-stu-id="167b5-223">This option is the default.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="167b5-224">这种类型的优先约束显示为绿色、红色或蓝色实线。</span><span class="sxs-lookup"><span data-stu-id="167b5-224">This type of precedence constraint appears as a solid green, red, or blue line.</span></span>  
  
         <span data-ttu-id="167b5-225">**逻辑或**</span><span class="sxs-lookup"><span data-stu-id="167b5-225">**Logical OR**</span></span>  
         <span data-ttu-id="167b5-226">选择此选项可以指定：同一个可执行文件的多个优先约束必须一起计算。</span><span class="sxs-lookup"><span data-stu-id="167b5-226">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="167b5-227">至少必须有一个约束的计算结果为 True。</span><span class="sxs-lookup"><span data-stu-id="167b5-227">At least one constraint must evaluate to True.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="167b5-228">这种类型的优先约束显示为绿色、红色或蓝色点线。</span><span class="sxs-lookup"><span data-stu-id="167b5-228">This type of precedence constraint appears as a dotted green, red, or blue line.</span></span>  
  
9. <span data-ttu-id="167b5-229">若要添加包含在其他计划中运行的任务的另一个子计划，请单击工具栏上的 **“添加子计划”** 以便打开 **“子计划属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="167b5-229">To add another subplan that contains tasks run on a different schedule, click **Add Subplan** on the toolbar to open the **Subplan Properties** dialog box.</span></span>  
  
10. <span data-ttu-id="167b5-230">添加与其他服务器的连接：</span><span class="sxs-lookup"><span data-stu-id="167b5-230">To add connections to different servers:</span></span>  
  
    1.  <span data-ttu-id="167b5-231">在设计空间的工具栏中，单击 **“管理连接”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-231">In the design space's toolbar, click **Manage Connections**.</span></span>  
  
    2.  <span data-ttu-id="167b5-232">在 **“管理连接”** 对话框中，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-232">In the **Manage Connections** dialog box, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="167b5-233">在 **“连接属性”** 对话框的 **“连接名称”** 框中，输入要创建的连接的名称。</span><span class="sxs-lookup"><span data-stu-id="167b5-233">In the **Connection Properties** dialog box, in the **Connection name** box, enter the name of the connection you are creating.</span></span>  
  
    4.  <span data-ttu-id="167b5-234">在“指定下列选项以连接到 SQL Server 数据”下的“选择或输入服务器名称”框中，输入要使用的 SQL Server 的名称，或者单击省略号 (…) 并在 SQL Server 对话框中选择某一服务器   。</span><span class="sxs-lookup"><span data-stu-id="167b5-234">Under **Specify the following to connect to SQL Server data**, in the **Select or enter a server name** box, either enter the name of the SQL server you want to use or click the ellipsis **(...)** and select a server in the **SQL Server** dialog box.</span></span> <span data-ttu-id="167b5-235">如果您从 **SQL Server** 对话框中选择某一服务器，则单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-235">If you select a server from the **SQL Server** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="167b5-236">在 **“输入登录服务器所需的信息”** 下，选择 **“使用 Windows NT 集成安全性”** 或 **“使用特定用户名和密码”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-236">Under **Enter information to log on to the server**, select either **Use Windows NT Integrated security** or **Use a specific user name and password**.</span></span> <span data-ttu-id="167b5-237">如果您选择使用特定的用户名和密码，则分别在 **“用户名”** 和 **“密码”** 框中输入该信息。</span><span class="sxs-lookup"><span data-stu-id="167b5-237">If you elect to use a specific user name and password, enter that information in the **User name** and **Password** boxes, respectively.</span></span>  
  
    6.  <span data-ttu-id="167b5-238">单击 **“连接属性”** 对话框中的 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-238">In the **Connection Properties** dialog box, click **OK**.</span></span>  
  
    7.  <span data-ttu-id="167b5-239">在 **“管理连接”** 对话框中，单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-239">In the **Manage Connections** dialog box, click **Close**.</span></span>  
  
11. <span data-ttu-id="167b5-240">指定报告选项：</span><span class="sxs-lookup"><span data-stu-id="167b5-240">To specify reporting options:</span></span>  
  
    1.  <span data-ttu-id="167b5-241">在设计空间的工具栏中，单击 **“报告和记录”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-241">In the design space's toolbar, click **Reporting and Logging**.</span></span>  
  
    2.  <span data-ttu-id="167b5-242">在 **“报告和记录”** 对话框的 **“报告”** 下，选择 **“生成文本文件报告”** 和/或 **“将报告发送给电子邮件收件人”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-242">In the **Reporting and Logging** dialog box, under **Reporting**, select **Generate a text file report** or **Send report to an email recipient** or both.</span></span>  
  
        1.  <span data-ttu-id="167b5-243">如果您选择了 **“生成文本文件报告”** ，则选择 **“创建新文件”** 或 **“追加到文件”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-243">If you select **Generate a text file report**, select either **Create a new file** or **Append to file**.</span></span>  
  
        2.  <span data-ttu-id="167b5-244">根据上面选择的选项，通过在 **“文件夹”** 或 **“文件名”** 框中输入信息，输入新文件或要追加的文件的名称和完整路径。</span><span class="sxs-lookup"><span data-stu-id="167b5-244">Depending on the selection above, enter the name and full path of the new file or file to be appended by entering the information in the **Folder** or **File name** boxes.</span></span> <span data-ttu-id="167b5-245">或者，单击省略号\*\* ( ... ) **然后从 "**定位文件夹-**_Server_name_ " 或 "**定位数据库文件-\*\*_server_name_ " 对话框中选择文件夹或文件名的路径。</span><span class="sxs-lookup"><span data-stu-id="167b5-245">Alternately, click on the ellipsis **(...)** and select the path to the folder or file name from the **Locate Folder -**_server_name_ or **Locate Database Files -**_server_name_ dialog boxes.</span></span>  
  
        3.  <span data-ttu-id="167b5-246">如果您选择 **“将报告发送给电子邮件收件人”** ，则在 **“代理操作员”** 列表上，选择以电子邮件形式发送的报告的收件人。</span><span class="sxs-lookup"><span data-stu-id="167b5-246">If you select **Send report to an email recipient**, on the **Agent operator** list, select the recipient of the emailed report.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="167b5-247">为发送电子邮件，SQL Server 代理必须配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="167b5-247">SQL Server Agent must be configured to use Database Mail in order to send mail.</span></span> <span data-ttu-id="167b5-248">有关详细信息，请参阅 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)</span><span class="sxs-lookup"><span data-stu-id="167b5-248">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)</span></span>  
  
    3.  <span data-ttu-id="167b5-249">若要保存更详细的信息，请在 **“记录”** 下选择 **“记录扩展信息”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-249">To save more detailed information, under **Logging**, select **Log extended information**.</span></span>  
  
    4.  <span data-ttu-id="167b5-250">若要将维护计划结果信息写入其他服务器，请选择 **“在远程服务器上进行日志记录”** ，并且或者从 **“连接”** 列表中选择某一服务器连接，或者单击 **“新建”** 并在 **“连接属性”** 对话框中输入连接信息。</span><span class="sxs-lookup"><span data-stu-id="167b5-250">To write maintenance plan results information to another server, select **Log to remote server** and either select a server connection from the **Connection** list or click **New** and enter the connection information in the **Connection Properties** dialog box.</span></span>  
  
    5.  <span data-ttu-id="167b5-251">在 **“报告和记录”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-251">In the **Reporting and Logging** dialog box, click **OK**.</span></span>  
  
12. <span data-ttu-id="167b5-252">若要在日志文件查看器中查看结果，请在“对象资源管理器” 中右键单击“维护计划”  文件夹或特定维护计划，然后选择“查看历史记录” 。</span><span class="sxs-lookup"><span data-stu-id="167b5-252">To view the results in the log file viewer, in **Object Explorer**, right-click either the **Maintenance Plans** folder or the specific maintenance plan and select **View History**.</span></span>  
  
     <span data-ttu-id="167b5-253">"**日志文件查看器-**_server_name_ " 对话框中提供了以下选项。</span><span class="sxs-lookup"><span data-stu-id="167b5-253">The following options are available on the **Log File Viewer -**_server_name_ dialog box.</span></span>  
  
     <span data-ttu-id="167b5-254">**加载日志**</span><span class="sxs-lookup"><span data-stu-id="167b5-254">**Load Log**</span></span>  
     <span data-ttu-id="167b5-255">打开一个对话框，您可以在其中指定要加载的日志文件。</span><span class="sxs-lookup"><span data-stu-id="167b5-255">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="167b5-256">**导出**</span><span class="sxs-lookup"><span data-stu-id="167b5-256">**Export**</span></span>  
     <span data-ttu-id="167b5-257">打开一个对话框，你可以使用该对话框将“日志文件摘要”  网格中显示的信息导入到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="167b5-257">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="167b5-258">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="167b5-258">**Refresh**</span></span>  
     <span data-ttu-id="167b5-259">刷新选定日志的视图。</span><span class="sxs-lookup"><span data-stu-id="167b5-259">Refresh the view of the selected logs.</span></span> <span data-ttu-id="167b5-260">在应用任何筛选器设置时， **“刷新”** 按钮重新从目标服务器中读取选定的日志。</span><span class="sxs-lookup"><span data-stu-id="167b5-260">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="167b5-261">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="167b5-261">**Filter**</span></span>  
     <span data-ttu-id="167b5-262">打开一个对话框，你可以使用该对话框指定用于筛选日志文件的设置，例如“连接” 、“日期” 或其他“常规”  筛选条件。</span><span class="sxs-lookup"><span data-stu-id="167b5-262">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="167b5-263">**搜索**</span><span class="sxs-lookup"><span data-stu-id="167b5-263">**Search**</span></span>  
     <span data-ttu-id="167b5-264">在日志文件中搜索特定文本。</span><span class="sxs-lookup"><span data-stu-id="167b5-264">Search the log file for specific text.</span></span> <span data-ttu-id="167b5-265">不支持在搜索中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="167b5-265">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="167b5-266">**Stop**</span><span class="sxs-lookup"><span data-stu-id="167b5-266">**Stop**</span></span>  
     <span data-ttu-id="167b5-267">停止加载日志文件条目。</span><span class="sxs-lookup"><span data-stu-id="167b5-267">Stops loading the log file entries.</span></span> <span data-ttu-id="167b5-268">例如，如果远程或脱机日志文件需要较长时间才能加载，并且您只想查看最新的条目，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="167b5-268">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="167b5-269">**日志文件摘要**</span><span class="sxs-lookup"><span data-stu-id="167b5-269">**Log file summary**</span></span>  
     <span data-ttu-id="167b5-270">此信息窗格显示日志文件筛选摘要。</span><span class="sxs-lookup"><span data-stu-id="167b5-270">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="167b5-271">如果未对文件进行筛选，您将看到以下文本： **“未应用任何筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="167b5-271">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="167b5-272">如果对日志应用了筛选器，将看到以下文本：基于以下条件筛选日志项：\<filter criteria>。</span><span class="sxs-lookup"><span data-stu-id="167b5-272">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="167b5-273">**Date**</span><span class="sxs-lookup"><span data-stu-id="167b5-273">**Date**</span></span>  
     <span data-ttu-id="167b5-274">显示事件的日期。</span><span class="sxs-lookup"><span data-stu-id="167b5-274">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="167b5-275">**数据源**</span><span class="sxs-lookup"><span data-stu-id="167b5-275">**Source**</span></span>  
     <span data-ttu-id="167b5-276">显示从其创建事件的源功能，例如服务的名称（如 MSSQLSERVER）。</span><span class="sxs-lookup"><span data-stu-id="167b5-276">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="167b5-277">并非对所有日志类型都显示此项。</span><span class="sxs-lookup"><span data-stu-id="167b5-277">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="167b5-278">**消息**</span><span class="sxs-lookup"><span data-stu-id="167b5-278">**Message**</span></span>  
     <span data-ttu-id="167b5-279">显示与事件相关联的任何消息。</span><span class="sxs-lookup"><span data-stu-id="167b5-279">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="167b5-280">**日志类型**</span><span class="sxs-lookup"><span data-stu-id="167b5-280">**Log Type**</span></span>  
     <span data-ttu-id="167b5-281">显示事件所属的日志类型。</span><span class="sxs-lookup"><span data-stu-id="167b5-281">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="167b5-282">所有选定的日志都显示在日志文件摘要窗口中。</span><span class="sxs-lookup"><span data-stu-id="167b5-282">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="167b5-283">**日志源**</span><span class="sxs-lookup"><span data-stu-id="167b5-283">**Log Source**</span></span>  
     <span data-ttu-id="167b5-284">显示在其中捕获事件的源日志的说明。</span><span class="sxs-lookup"><span data-stu-id="167b5-284">Displays a description of the source log in which the event is captured.</span></span>  
  
     <span data-ttu-id="167b5-285">**所选行详细信息**</span><span class="sxs-lookup"><span data-stu-id="167b5-285">**Selected row details**</span></span>  
     <span data-ttu-id="167b5-286">选择一行可以在页面底部显示有关所选事件行的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="167b5-286">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="167b5-287">在网格中，通过将列拖动到的新位置可以重新排列各列的顺序。</span><span class="sxs-lookup"><span data-stu-id="167b5-287">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="167b5-288">通过将网格标题中的列分隔条向左或向右拖动，可以调列的大小。</span><span class="sxs-lookup"><span data-stu-id="167b5-288">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="167b5-289">双击网格标题中的列分隔条，可以按内容宽度自动调整列的大小。</span><span class="sxs-lookup"><span data-stu-id="167b5-289">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="167b5-290">**实例**</span><span class="sxs-lookup"><span data-stu-id="167b5-290">**Instance**</span></span>  
     <span data-ttu-id="167b5-291">发生事件的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="167b5-291">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="167b5-292">这显示为：计算机名称\\实例名称 。</span><span class="sxs-lookup"><span data-stu-id="167b5-292">This is displayed as *computer name*\\*instance name*.</span></span>  
  
  
