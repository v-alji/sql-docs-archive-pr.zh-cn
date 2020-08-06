---
title: 调试控制流 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- breakpoints [Integration Services]
- debugging [Integration Services], control flow
- control flow [Integration Services], debugging
- color-coded progress reporting [Integration Services]
- Set Breakpoints dialog box
ms.assetid: 54a458cc-9f4f-4b48-8cf2-db2e0fa7756c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f2e2feff6723a510cb773131cb6452bdc7a77cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690710"
---
# <a name="debugging-control-flow"></a><span data-ttu-id="534ca-102">调试控制流</span><span class="sxs-lookup"><span data-stu-id="534ca-102">Debugging Control Flow</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="534ca-103">和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包含一些功能和工具，你可以使用这些功能和工具对 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包中的控制流进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="534ca-103">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] include features and tools that you can use to troubleshoot the control flow in an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package.</span></span>

-   [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="534ca-104">支持容器和任务上的断点。</span><span class="sxs-lookup"><span data-stu-id="534ca-104">supports breakpoints on containers and tasks.</span></span>

-   [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="534ca-105">设计器在运行时提供进度报告。</span><span class="sxs-lookup"><span data-stu-id="534ca-105">Designer provides progress reporting at run time.</span></span>

-   [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="534ca-106">提供了调试窗口。</span><span class="sxs-lookup"><span data-stu-id="534ca-106">provides debug windows.</span></span>

## <a name="breakpoints"></a><span data-ttu-id="534ca-107">断点</span><span class="sxs-lookup"><span data-stu-id="534ca-107">Breakpoints</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="534ca-108">设计器提供了 **“设置断点”** 对话框，您可以在其中对断点进行设置：启用中断条件，指定发生多少次断点后就将包的执行挂起。</span><span class="sxs-lookup"><span data-stu-id="534ca-108">Designer provides the **Set Breakpoints** dialog box, in which you can set breakpoints by enabling break conditions and specifying the number of times a breakpoint can occur before the execution of the package is suspended.</span></span> <span data-ttu-id="534ca-109">断点可在包级或单个组件级启用。</span><span class="sxs-lookup"><span data-stu-id="534ca-109">Breakpoints can be enabled at the package level, or at the level of the individual component.</span></span> <span data-ttu-id="534ca-110">如果在任务或容器级上启用中断条件，则在 **“控制流”** 选项卡的设计图面上，相应的任务或容器旁边会显示断点图标。如果在包一级启用中断条件，则在 **“控制流”** 选项卡的标签上显示断点图标。</span><span class="sxs-lookup"><span data-stu-id="534ca-110">If break conditions are enabled at the task or container level, the breakpoint icon appears next to the task or container on the design surface of the **Control Flow** tab. If the break conditions are enabled on the package, the breakpoint icon appears on the label of the **Control Flow** tab.</span></span>

 <span data-ttu-id="534ca-111">在命中断点时，断点图标将会发生改变以帮助识别断点源。</span><span class="sxs-lookup"><span data-stu-id="534ca-111">When a breakpoint is hit, the breakpoint icon changes to help you identify the source of the breakpoint.</span></span> <span data-ttu-id="534ca-112">包运行时，可以添加、删除和更改断点。</span><span class="sxs-lookup"><span data-stu-id="534ca-112">You can add, delete, and change breakpoints when the package is running.</span></span>

 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="534ca-113">提供了十个可以在所有任务和容器上启用的中断条件。</span><span class="sxs-lookup"><span data-stu-id="534ca-113">provides ten break conditions that you can enable on all tasks and containers.</span></span> <span data-ttu-id="534ca-114">在 **“设置断点”** 对话框中，可根据下列条件启用断点：</span><span class="sxs-lookup"><span data-stu-id="534ca-114">In the **Set Breakpoints** dialog box, you can enable breakpoints on the following conditions:</span></span>

|<span data-ttu-id="534ca-115">中断条件</span><span class="sxs-lookup"><span data-stu-id="534ca-115">Break condition</span></span>|<span data-ttu-id="534ca-116">说明</span><span class="sxs-lookup"><span data-stu-id="534ca-116">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="534ca-117">当任务或容器收到 `OnPreExecute` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-117">When the task or container receives the `OnPreExecute` event.</span></span>|<span data-ttu-id="534ca-118">任务将要执行时调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-118">Called when a task is about to execute.</span></span> <span data-ttu-id="534ca-119">此事件由任务或容器在其运行前一刻引发。</span><span class="sxs-lookup"><span data-stu-id="534ca-119">This event is raised by a task or a container immediately before it runs.</span></span>|
|<span data-ttu-id="534ca-120">当任务或容器收到 `OnPostExecute` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-120">When the task or container receives the `OnPostExecute` event.</span></span>|<span data-ttu-id="534ca-121">任务的执行逻辑完成后立即调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-121">Called immediately after the execution logic of the task finishes.</span></span> <span data-ttu-id="534ca-122">此事件由任务或容器在其运行后引发。</span><span class="sxs-lookup"><span data-stu-id="534ca-122">This event is raised by a task or container immediately after it runs.</span></span>|
|<span data-ttu-id="534ca-123">当任务或容器收到 `OnError` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-123">When the task or container receives the `OnError` event.</span></span>|<span data-ttu-id="534ca-124">出现错误时由任务或容器调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-124">Called by a task or container when an error occurs.</span></span>|
|<span data-ttu-id="534ca-125">当任务或容器收到 `OnWarning` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-125">When the task or container receives the `OnWarning` event.</span></span>|<span data-ttu-id="534ca-126">当任务处于不能证明出错但有必要发出警告的状态时调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-126">Called when the task is in a state that does not justify an error, but does warrant a warning.</span></span>|
|<span data-ttu-id="534ca-127">当任务或容器收到 `OnInformation` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-127">When the task or container receives the `OnInformation` event.</span></span>|<span data-ttu-id="534ca-128">需要任务提供信息时调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-128">Called when the task is required to provide information.</span></span>|
|<span data-ttu-id="534ca-129">当任务或容器收到 `OnTaskFailed` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-129">When the task or container receives the `OnTaskFailed` event.</span></span>|<span data-ttu-id="534ca-130">任务宿主失败时由其调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-130">Called by the task host when it fails.</span></span>|
|<span data-ttu-id="534ca-131">当任务或容器收到 `OnProgress` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-131">When the task or container receives the `OnProgress` event.</span></span>|<span data-ttu-id="534ca-132">要更新任务执行的进度时调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-132">Called to update progress about task execution.</span></span>|
|<span data-ttu-id="534ca-133">当任务或容器收到 `OnQueryCancel` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-133">When the task or container receives the `OnQueryCancel` event.</span></span>|<span data-ttu-id="534ca-134">在可以取消执行的任务处理中，随时可以调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-134">Called at any time in task processing when you can cancel execution.</span></span>|
|<span data-ttu-id="534ca-135">当任务或容器收到 `OnVariableValueChanged` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-135">When the task or container receives the `OnVariableValueChanged` event.</span></span>|<span data-ttu-id="534ca-136">变量值更改时，由 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行时调用。</span><span class="sxs-lookup"><span data-stu-id="534ca-136">Called by the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime when the value of a variable changes.</span></span> <span data-ttu-id="534ca-137">必须将该变量的 RaiseChangeEvent 设置为 `true` 才能引发此事件。</span><span class="sxs-lookup"><span data-stu-id="534ca-137">The RaiseChangeEvent of the variable must be set to `true` to raise this event.</span></span><br /><br /> <span data-ttu-id="534ca-138">&#42;&#42; 警告 &#42;&#42; 必须在容器范围定义与此断点关联的变量   。</span><span class="sxs-lookup"><span data-stu-id="534ca-138">**&#42;&#42; Warning &#42;&#42;** The variable associated with this breakpoint must be defined at the **container** scope.</span></span> <span data-ttu-id="534ca-139">如果在包作用域定义变量，则不会命中断点。</span><span class="sxs-lookup"><span data-stu-id="534ca-139">If the variable is defined at the package scope, the breakpoint does not get hit.</span></span>|
|<span data-ttu-id="534ca-140">当任务或容器收到 `OnCustomEvent` 事件时。</span><span class="sxs-lookup"><span data-stu-id="534ca-140">When the task or container receives the `OnCustomEvent` event.</span></span>|<span data-ttu-id="534ca-141">由任务调用，用于引发自定义的任务定义事件。</span><span class="sxs-lookup"><span data-stu-id="534ca-141">Called by tasks to raise custom task-defined events.</span></span>|

 <span data-ttu-id="534ca-142">除了对所有任务和容器可用的中断条件外，有些任务和容器还包含用来设置断点的特殊中断条件。</span><span class="sxs-lookup"><span data-stu-id="534ca-142">In addition to the break conditions available to all tasks and containers, some tasks and containers include special break conditions for setting breakpoints.</span></span> <span data-ttu-id="534ca-143">例如，可以在 For 循环容器上启用中断条件，设置一个在循环的每个迭代开始时挂起执行的断点。</span><span class="sxs-lookup"><span data-stu-id="534ca-143">For example, you can enable a break condition on the For Loop container that sets a breakpoint that suspends execution at the start of each iteration of the loop.</span></span>

 <span data-ttu-id="534ca-144">若要增加断点的灵活性和能力，可通过指定下列选项来修改断点的行为：</span><span class="sxs-lookup"><span data-stu-id="534ca-144">To add flexibility and power to a breakpoint, you can modify the behavior of a breakpoint by specifying the following options:</span></span>

-   <span data-ttu-id="534ca-145">命中计数，即执行挂起之前中断条件出现的最大次数。</span><span class="sxs-lookup"><span data-stu-id="534ca-145">The hit count, or the maximum number of times that a break condition occurs before the execution is suspended.</span></span>

-   <span data-ttu-id="534ca-146">命中计数类型，或指定中断条件何时触发断点的规则。</span><span class="sxs-lookup"><span data-stu-id="534ca-146">The hit count type, or the rule that specifies when the break condition triggers the breakpoint.</span></span>

 <span data-ttu-id="534ca-147">命中计数类型（除“始终”类型以外）由命中计数进行进一步限定。</span><span class="sxs-lookup"><span data-stu-id="534ca-147">The hit count types, except for the Always type, are further qualified by the hit count.</span></span> <span data-ttu-id="534ca-148">例如，如果类型是“命中计数等于”并且命中计数是 5，则在中断条件第六次出现时挂起执行。</span><span class="sxs-lookup"><span data-stu-id="534ca-148">For example, if the type is "Hit count equals" and the hit count is 5, execution is suspended on the sixth occurrence of the break condition.</span></span>

 <span data-ttu-id="534ca-149">下表介绍命中计数类型。</span><span class="sxs-lookup"><span data-stu-id="534ca-149">The following table describes the hit count types.</span></span>

|<span data-ttu-id="534ca-150">命中计数类型</span><span class="sxs-lookup"><span data-stu-id="534ca-150">Hit count type</span></span>|<span data-ttu-id="534ca-151">说明</span><span class="sxs-lookup"><span data-stu-id="534ca-151">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="534ca-152">始终</span><span class="sxs-lookup"><span data-stu-id="534ca-152">Always</span></span>|<span data-ttu-id="534ca-153">断点命中时始终挂起执行。</span><span class="sxs-lookup"><span data-stu-id="534ca-153">Execution is always suspended when the breakpoint is hit.</span></span>|
|<span data-ttu-id="534ca-154">命中计数等于</span><span class="sxs-lookup"><span data-stu-id="534ca-154">Hit count equals</span></span>|<span data-ttu-id="534ca-155">断点发生的次数等于命中计数时挂起执行。</span><span class="sxs-lookup"><span data-stu-id="534ca-155">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|
|<span data-ttu-id="534ca-156">命中计数大于或等于</span><span class="sxs-lookup"><span data-stu-id="534ca-156">Hit count greater than or equal to</span></span>|<span data-ttu-id="534ca-157">断点发生的次数等于或大于命中计数时挂起执行。</span><span class="sxs-lookup"><span data-stu-id="534ca-157">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|
|<span data-ttu-id="534ca-158">命中计数倍增基数</span><span class="sxs-lookup"><span data-stu-id="534ca-158">Hit count multiple</span></span>|<span data-ttu-id="534ca-159">断点发生的次数为命中计数的倍数时挂起执行。</span><span class="sxs-lookup"><span data-stu-id="534ca-159">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="534ca-160">例如，如果将此选项设置为 5，则每命中五次就挂起执行。</span><span class="sxs-lookup"><span data-stu-id="534ca-160">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|

#### <a name="to-set-breakpoints"></a><span data-ttu-id="534ca-161">设置断点</span><span class="sxs-lookup"><span data-stu-id="534ca-161">To set breakpoints</span></span>

-   [<span data-ttu-id="534ca-162">通过在任务或容器上设置断点调试包</span><span class="sxs-lookup"><span data-stu-id="534ca-162">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>](../debug-a-package-by-setting-breakpoints-on-a-task-or-a-container.md)

## <a name="progress-reporting"></a><span data-ttu-id="534ca-163">进度报告</span><span class="sxs-lookup"><span data-stu-id="534ca-163">Progress Reporting</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="534ca-164">设计器包含两种类型进度报告：“控制流”选项卡设计图面上的颜色编码和“进度”选项卡上的进度消息   。</span><span class="sxs-lookup"><span data-stu-id="534ca-164">Designer includes two types of progress reporting: color-coding on the design surface of the **Control Flow** tab, and progress messages on the **Progress** tab.</span></span>

 <span data-ttu-id="534ca-165">运行包时， [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器使用可指示执行状态的颜色显示每个任务或容器，以此来描绘执行进度。</span><span class="sxs-lookup"><span data-stu-id="534ca-165">When you run a package, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer depicts execution progress by displaying each task or container using a color that indicates execution status.</span></span> <span data-ttu-id="534ca-166">可根据颜色判断元素是否正在等待运行、是否当前正在运行、是否已成功完成或者已经以失败结束。</span><span class="sxs-lookup"><span data-stu-id="534ca-166">You can tell by its color whether the element is waiting to run, currently running, has completed successfully, or has ended unsuccessfully.</span></span> <span data-ttu-id="534ca-167">停止包执行后，颜色编码将消失。</span><span class="sxs-lookup"><span data-stu-id="534ca-167">After you stop package execution, the color-coding disappears.</span></span>

 <span data-ttu-id="534ca-168">下表介绍用于描绘执行状态的各种颜色。</span><span class="sxs-lookup"><span data-stu-id="534ca-168">The following table describes the colors that are used to depict execution status.</span></span>

|<span data-ttu-id="534ca-169">Color</span><span class="sxs-lookup"><span data-stu-id="534ca-169">Color</span></span>|<span data-ttu-id="534ca-170">执行状态</span><span class="sxs-lookup"><span data-stu-id="534ca-170">Execution status</span></span>|
|-----------|----------------------|
|<span data-ttu-id="534ca-171">灰色</span><span class="sxs-lookup"><span data-stu-id="534ca-171">Gray</span></span>|<span data-ttu-id="534ca-172">等待运行</span><span class="sxs-lookup"><span data-stu-id="534ca-172">Waiting to run</span></span>|
|<span data-ttu-id="534ca-173">Yellow</span><span class="sxs-lookup"><span data-stu-id="534ca-173">Yellow</span></span>|<span data-ttu-id="534ca-174">正在运行</span><span class="sxs-lookup"><span data-stu-id="534ca-174">Running</span></span>|
|<span data-ttu-id="534ca-175">绿色</span><span class="sxs-lookup"><span data-stu-id="534ca-175">Green</span></span>|<span data-ttu-id="534ca-176">成功运行</span><span class="sxs-lookup"><span data-stu-id="534ca-176">Ran successfully</span></span>|
|<span data-ttu-id="534ca-177">已突出显示</span><span class="sxs-lookup"><span data-stu-id="534ca-177">highlighted</span></span>|<span data-ttu-id="534ca-178">运行，但有错误</span><span class="sxs-lookup"><span data-stu-id="534ca-178">Ran with errors</span></span>|

 <span data-ttu-id="534ca-179">**“进度”** 选项卡上按执行顺序列出了任务和容器，并包含了开始时间和结束时间、警告以及错误信息。</span><span class="sxs-lookup"><span data-stu-id="534ca-179">The **Progress** tab lists tasks and containers in execution order and includes the start and finish times, warnings, and error messages.</span></span> <span data-ttu-id="534ca-180">停止包执行后，在 **“执行结果”** 选项卡上的进度信息仍然可用。</span><span class="sxs-lookup"><span data-stu-id="534ca-180">After you stop package execution, the progress information remains available on the **Execution Results** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="534ca-181">若要允许或禁止在 **“进度”** 选项卡上显示消息，请在 **SSIS** 菜单上切换 **“调试进度报告”** 选项。</span><span class="sxs-lookup"><span data-stu-id="534ca-181">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

 <span data-ttu-id="534ca-182">下面的关系图显示 **“进度”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="534ca-182">The following diagram shows the **Progress** tab.</span></span>

 <span data-ttu-id="534ca-183">![SSIS 设计器的“进度”选项卡](../media/mw-dtsflow04.gif "SSIS 设计器的“进度”选项卡")</span><span class="sxs-lookup"><span data-stu-id="534ca-183">![Progress tab of SSIS Designer](../media/mw-dtsflow04.gif "Progress tab of SSIS Designer")</span></span>

## <a name="debug-windows"></a><span data-ttu-id="534ca-184">调试窗口</span><span class="sxs-lookup"><span data-stu-id="534ca-184">Debug Windows</span></span>
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="534ca-185">包含多个窗口，可以用来处理断点，以及用来调试包含断点的包。</span><span class="sxs-lookup"><span data-stu-id="534ca-185">includes many windows that you can use to work with breakpoints, and to debug packages that contain breakpoints.</span></span> <span data-ttu-id="534ca-186">若要了解每个窗口的更多信息，请打开该窗口，然后按 F1 显示该窗口的帮助。</span><span class="sxs-lookup"><span data-stu-id="534ca-186">To learn more about each window, open the window, and then press F1 to display Help for the window.</span></span>

 <span data-ttu-id="534ca-187">若要在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中打开这些窗口，请单击 **“调试”** 菜单，指向 **“窗口”** ，然后单击 **“断点”** 、 **“输出”** 或 **“即时”** 。</span><span class="sxs-lookup"><span data-stu-id="534ca-187">To open these windows in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], click the **Debug** menu, point to **Windows**, and then click **Breakpoints**, **Output**, or **Immediate**.</span></span>

 <span data-ttu-id="534ca-188">下表介绍这些窗口。</span><span class="sxs-lookup"><span data-stu-id="534ca-188">The following table describes the windows.</span></span>

|<span data-ttu-id="534ca-189">窗口</span><span class="sxs-lookup"><span data-stu-id="534ca-189">Window</span></span>|<span data-ttu-id="534ca-190">说明</span><span class="sxs-lookup"><span data-stu-id="534ca-190">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="534ca-191">断点</span><span class="sxs-lookup"><span data-stu-id="534ca-191">Breakpoints</span></span>|<span data-ttu-id="534ca-192">列出包中的断点并提供启用和删除断点的选项。</span><span class="sxs-lookup"><span data-stu-id="534ca-192">Lists the breakpoints in a package and provides options to enable and delete breakpoints.</span></span>|
|<span data-ttu-id="534ca-193">输出</span><span class="sxs-lookup"><span data-stu-id="534ca-193">Output</span></span>|<span data-ttu-id="534ca-194">显示 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中各功能的状态消息。</span><span class="sxs-lookup"><span data-stu-id="534ca-194">Displays status messages for features in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>|
|<span data-ttu-id="534ca-195">即时</span><span class="sxs-lookup"><span data-stu-id="534ca-195">Immediate</span></span>|<span data-ttu-id="534ca-196">用于调试和评估表达式，并打印变量值。</span><span class="sxs-lookup"><span data-stu-id="534ca-196">Used to debug and evaluate expressions and print variable values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="534ca-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="534ca-197">See Also</span></span>
 [<span data-ttu-id="534ca-198">包开发的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="534ca-198">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)


