---
title: Integration Services (SSIS) 事件处理程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, events
- run-time [Integration Services]
- SQL Server Integration Services packages, events
- event handlers [Integration Services], about event handlers
- events [Integration Services]
- packages [Integration Services], events
- event handlers [Integration Services]
- SSIS packages, events
- containers [Integration Services], events
- events [Integration Services], about events
ms.assetid: 6f60cf93-35dc-431c-908d-2049c4ab66ba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78bcd6579aa8306c89fd9530fad3557ac57f102a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586866"
---
# <a name="integration-services-ssis-event-handlers"></a><span data-ttu-id="185c6-102">Integration Services (SSIS) 事件处理程序</span><span class="sxs-lookup"><span data-stu-id="185c6-102">Integration Services (SSIS) Event Handlers</span></span>
  <span data-ttu-id="185c6-103">在运行时，可执行文件（包以及 Foreach 循环容器、For 循环容器、序列容器和任务宿主容器）会引发事件。</span><span class="sxs-lookup"><span data-stu-id="185c6-103">At run time, executables (packages and Foreach Loop, For Loop, Sequence, and task host containers) raise events.</span></span> <span data-ttu-id="185c6-104">例如，错误发生时会引发 OnError 事件。</span><span class="sxs-lookup"><span data-stu-id="185c6-104">For example, an OnError event is raised when an error occurs.</span></span> <span data-ttu-id="185c6-105">可以为这些事件创建自定义事件处理程序，以扩展包的功能并使包在运行时更容易管理。</span><span class="sxs-lookup"><span data-stu-id="185c6-105">You can create custom event handlers for these events to extend package functionality and make packages easier to manage at run time.</span></span> <span data-ttu-id="185c6-106">事件处理程序可以执行诸如下列任务：</span><span class="sxs-lookup"><span data-stu-id="185c6-106">Event handlers can perform tasks such as the following:</span></span>

-   <span data-ttu-id="185c6-107">当包或任务运行完成时清除临时数据存储。</span><span class="sxs-lookup"><span data-stu-id="185c6-107">Clean up temporary data storage when a package or task finishes running.</span></span>

-   <span data-ttu-id="185c6-108">在包运行前检索系统信息，以便评估资源可用性。</span><span class="sxs-lookup"><span data-stu-id="185c6-108">Retrieve system information to assess resource availability before a package runs.</span></span>

-   <span data-ttu-id="185c6-109">在引用表中的查找失败时刷新表中的数据。</span><span class="sxs-lookup"><span data-stu-id="185c6-109">Refresh data in a table when a lookup in a reference table fails.</span></span>

-   <span data-ttu-id="185c6-110">当发生错误或警告时，或者当任务失败时，发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="185c6-110">Send an e-mail message when an error or a warning occurs or when a task fails.</span></span>

 <span data-ttu-id="185c6-111">如果事件没有事件处理程序，则将该事件提升到包中容器层次结构中的上一级容器。</span><span class="sxs-lookup"><span data-stu-id="185c6-111">If an event has no event handler, the event is raised to the next container up the container hierarchy in a package.</span></span> <span data-ttu-id="185c6-112">如果此容器具有事件处理程序，则该事件处理程序当事件发生时运行。</span><span class="sxs-lookup"><span data-stu-id="185c6-112">If this container has an event handler, the event handler runs in response to the event.</span></span> <span data-ttu-id="185c6-113">如果没有，则将该事件提升到容器层次结构中的上一级容器。</span><span class="sxs-lookup"><span data-stu-id="185c6-113">If not, the event is raised to the next container up the container hierarchy.</span></span>

 <span data-ttu-id="185c6-114">以下关系图显示具有 For 循环容器的简单包，该容器包含一个执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="185c6-114">The following diagram shows a simple package that has a For Loop container that contains one Execute SQL task.</span></span>

 <span data-ttu-id="185c6-115">![包、For 循环、任务宿主和执行 SQL 任务](media/mw-dts-eventhandlerpkg.gif "包、For 循环、任务宿主和执行 SQL 任务")</span><span class="sxs-lookup"><span data-stu-id="185c6-115">![Package, For Loop, task host, and Execute SQL task](media/mw-dts-eventhandlerpkg.gif "Package, For Loop, task host, and Execute SQL task")</span></span>

 <span data-ttu-id="185c6-116">只有包具有事件处理程序，用于处理其 `OnError` 事件。</span><span class="sxs-lookup"><span data-stu-id="185c6-116">Only the package has an event handler, for its `OnError` event.</span></span> <span data-ttu-id="185c6-117">如果执行 SQL 任务运行时发生错误，包的 `OnError` 事件处理程序就会运行。</span><span class="sxs-lookup"><span data-stu-id="185c6-117">If an error occurs when the Execute SQL task runs, the `OnError` event handler for the package runs.</span></span> <span data-ttu-id="185c6-118">以下关系图显示导致包的 `OnError` 事件处理程序执行的调用序列。</span><span class="sxs-lookup"><span data-stu-id="185c6-118">The following diagram shows the sequence of calls that causes the `OnError` event handler for the package to execute.</span></span>

 <span data-ttu-id="185c6-119">![事件处理程序流](media/mw-dts-eventhandlers.gif "事件处理程序流")</span><span class="sxs-lookup"><span data-stu-id="185c6-119">![Event handler flow](media/mw-dts-eventhandlers.gif "Event handler flow")</span></span>

 <span data-ttu-id="185c6-120">事件处理程序是事件处理程序集的成员，所有容器都包含此事件处理程序集。</span><span class="sxs-lookup"><span data-stu-id="185c6-120">Event handlers are members of an event handler collection, and all containers include this collection.</span></span> <span data-ttu-id="185c6-121">如果使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器创建包，就可以在 **设计器的** “包资源管理器” **选项卡上的** “事件处理程序” [!INCLUDE[ssIS](../includes/ssis-md.md)] 文件夹中看到事件处理程序集的成员。</span><span class="sxs-lookup"><span data-stu-id="185c6-121">If you create the package using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, you can see the members of the event handler collections in the **Event Handlers** folders on the **Package Explorer** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="185c6-122">可以采用下列方法配置事件处理程序容器：</span><span class="sxs-lookup"><span data-stu-id="185c6-122">You can configure the event handler container in the following ways:</span></span>

-   <span data-ttu-id="185c6-123">指定事件处理程序的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="185c6-123">Specify a name and description for the event handler.</span></span>

-   <span data-ttu-id="185c6-124">指示事件处理程序是否运行，事件处理程序失败时包是否失败，以及事件处理程序失败前可发生的错误数。</span><span class="sxs-lookup"><span data-stu-id="185c6-124">Indicate whether the event handler runs, whether the package fails if the event handler fails, and the number of errors that can occur before the event handler fails.</span></span>

-   <span data-ttu-id="185c6-125">指定返回执行结果，而不是事件处理程序在运行时返回的实际执行结果。</span><span class="sxs-lookup"><span data-stu-id="185c6-125">Specify an execution result to return instead of the actual execution result that the event handler returns at run time.</span></span>

-   <span data-ttu-id="185c6-126">指定事件处理程序的事务选项。</span><span class="sxs-lookup"><span data-stu-id="185c6-126">Specify the transaction option for the event handler.</span></span>

-   <span data-ttu-id="185c6-127">指定事件处理程序使用的日志记录模式。</span><span class="sxs-lookup"><span data-stu-id="185c6-127">Specify the logging mode that the event handler uses.</span></span>

## <a name="event-handler-content"></a><span data-ttu-id="185c6-128">事件处理程序内容</span><span class="sxs-lookup"><span data-stu-id="185c6-128">Event Handler Content</span></span>
 <span data-ttu-id="185c6-129">创建事件处理程序与生成包类似；事件处理程序具有多个任务和容器，这些任务和容器按照一定顺序组织成控制流，事件处理程序也可以包含多个数据流。</span><span class="sxs-lookup"><span data-stu-id="185c6-129">Creating an event handler is similar to building a package; an event handler has tasks and containers, which are sequenced into a control flow, and an event handler can also include data flows.</span></span> <span data-ttu-id="185c6-130">[!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器包含 **“事件处理程序”** 选项卡，用于创建自定义事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-130">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer includes the **Event Handlers** tab for creating custom event handlers.</span></span> <span data-ttu-id="185c6-131">有关详细信息，请参阅[SSIS 包事件处理程序](integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="185c6-131">For more information, see [SSIS Package Event Handlers](integration-services-ssis-event-handlers.md).</span></span>

 <span data-ttu-id="185c6-132">还可以采用编程方式创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-132">You can also create event handlers programmatically.</span></span> <span data-ttu-id="185c6-133">有关详细信息，请参阅 [以编程方式处理事件](building-packages-programmatically/handling-events-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="185c6-133">For more information, see [Handling Events Programmatically](building-packages-programmatically/handling-events-programmatically.md).</span></span>

## <a name="run-time-events"></a><span data-ttu-id="185c6-134">运行时事件</span><span class="sxs-lookup"><span data-stu-id="185c6-134">Run-Time Events</span></span>
 <span data-ttu-id="185c6-135">下表列出 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供的事件处理程序，并介绍导致事件处理程序运行的运行时事件。</span><span class="sxs-lookup"><span data-stu-id="185c6-135">The following table lists the event handlers that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides, and describes the run-time events that cause the event handler to run.</span></span>

|<span data-ttu-id="185c6-136">事件处理程序</span><span class="sxs-lookup"><span data-stu-id="185c6-136">Event handler</span></span>|<span data-ttu-id="185c6-137">事件</span><span class="sxs-lookup"><span data-stu-id="185c6-137">Event</span></span>|
|-------------------|-----------|
|`OnError`|<span data-ttu-id="185c6-138">`OnError` 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-138">The event handler for the `OnError` event.</span></span> <span data-ttu-id="185c6-139">此事件在发生错误时由可执行文件引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-139">This event is raised by an executable when an error occurs.</span></span>|
|<span data-ttu-id="185c6-140">**OnExecStatusChanged**</span><span class="sxs-lookup"><span data-stu-id="185c6-140">**OnExecStatusChanged**</span></span>|<span data-ttu-id="185c6-141">**OnExecStatusChanged** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-141">The event handler for the **OnExecStatusChanged** event.</span></span> <span data-ttu-id="185c6-142">此事件在其执行状态更改时由可执行文件引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-142">This event is raised by an executable when its execution status changes.</span></span>|
|<span data-ttu-id="185c6-143">**OnInformation**</span><span class="sxs-lookup"><span data-stu-id="185c6-143">**OnInformation**</span></span>|<span data-ttu-id="185c6-144">**OnInformation** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-144">The event handler for the **OnInformation** event.</span></span> <span data-ttu-id="185c6-145">此事件在可执行文件的验证和执行期间引发以报告信息。</span><span class="sxs-lookup"><span data-stu-id="185c6-145">This event is raised during the validation and execution of an executable to report information.</span></span> <span data-ttu-id="185c6-146">此事件仅传递信息，不传递错误或警告。</span><span class="sxs-lookup"><span data-stu-id="185c6-146">This event conveys information only, no errors or warnings.</span></span>|
|<span data-ttu-id="185c6-147">**OnPostExecute**</span><span class="sxs-lookup"><span data-stu-id="185c6-147">**OnPostExecute**</span></span>|<span data-ttu-id="185c6-148">**OnPostExecute** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-148">The event handler for the **OnPostExecute** event.</span></span> <span data-ttu-id="185c6-149">此事件由可执行文件在其运行完成后立即引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-149">This event is raised by an executable immediately after it has finished running.</span></span>|
|<span data-ttu-id="185c6-150">**OnPostValidate**</span><span class="sxs-lookup"><span data-stu-id="185c6-150">**OnPostValidate**</span></span>|<span data-ttu-id="185c6-151">**OnPostValidate** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-151">The event handler for the **OnPostValidate** event.</span></span> <span data-ttu-id="185c6-152">此事件由可执行文件在其验证完成时引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-152">This event is raised by an executable when its validation is finished.</span></span>|
|<span data-ttu-id="185c6-153">**OnPreExecute**</span><span class="sxs-lookup"><span data-stu-id="185c6-153">**OnPreExecute**</span></span>|<span data-ttu-id="185c6-154">**OnPreExecute** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-154">The event handler for the **OnPreExecute** event.</span></span> <span data-ttu-id="185c6-155">此事件由可执行文件在其运行前引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-155">This event is raised by an executable immediately before it runs.</span></span>|
|<span data-ttu-id="185c6-156">**OnPreValidate**</span><span class="sxs-lookup"><span data-stu-id="185c6-156">**OnPreValidate**</span></span>|<span data-ttu-id="185c6-157">**OnPreValidate** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-157">The event handler for the **OnPreValidate** event.</span></span> <span data-ttu-id="185c6-158">此事件由可执行文件在其验证开始时引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-158">This event is raised by an executable when its validation starts.</span></span>|
|<span data-ttu-id="185c6-159">**OnProgress**</span><span class="sxs-lookup"><span data-stu-id="185c6-159">**OnProgress**</span></span>|<span data-ttu-id="185c6-160">**OnProgress** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-160">The event handler for the **OnProgress** event.</span></span> <span data-ttu-id="185c6-161">此事件由可执行文件在其完成可度量的进度时引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-161">This event is raised by an executable when measurable progress is made by the executable.</span></span>|
|<span data-ttu-id="185c6-162">**OnQueryCancel**</span><span class="sxs-lookup"><span data-stu-id="185c6-162">**OnQueryCancel**</span></span>|<span data-ttu-id="185c6-163">**OnQueryCancel** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-163">The event handler for the **OnQueryCancel** event.</span></span> <span data-ttu-id="185c6-164">此事件由可执行文件引发，以确定它是否应停止运行。</span><span class="sxs-lookup"><span data-stu-id="185c6-164">This event is raised by an executable to determine whether it should stop running.</span></span>|
|<span data-ttu-id="185c6-165">**OnTaskFailed**</span><span class="sxs-lookup"><span data-stu-id="185c6-165">**OnTaskFailed**</span></span>|<span data-ttu-id="185c6-166">**OnTaskFailed** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-166">The event handler for the **OnTaskFailed** event.</span></span> <span data-ttu-id="185c6-167">此事件由任务在其失败时引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-167">This event is raised by a task when it fails.</span></span>|
|<span data-ttu-id="185c6-168">**OnVariableValueChanged**</span><span class="sxs-lookup"><span data-stu-id="185c6-168">**OnVariableValueChanged**</span></span>|<span data-ttu-id="185c6-169">**OnVariableValueChanged** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-169">The event handler for the **OnVariableValueChanged** event.</span></span> <span data-ttu-id="185c6-170">此事件在变量值更改时由可执行文件引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-170">This event is raised by an executable when the value of a variable changes.</span></span> <span data-ttu-id="185c6-171">此事件由此变量的可执行文件引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-171">The event is raised by the executable on which the variable is defined.</span></span> <span data-ttu-id="185c6-172">如果将变量的**RaiseChangeEvent**属性设置为，则不会引发此事件 `False` 。</span><span class="sxs-lookup"><span data-stu-id="185c6-172">This event is not raised if you set the **RaiseChangeEvent** property for the variable to `False`.</span></span> <span data-ttu-id="185c6-173">有关详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="185c6-173">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>|
|<span data-ttu-id="185c6-174">**OnWarning**</span><span class="sxs-lookup"><span data-stu-id="185c6-174">**OnWarning**</span></span>|<span data-ttu-id="185c6-175">**OnWarning** 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="185c6-175">The event handler for the **OnWarning** event.</span></span> <span data-ttu-id="185c6-176">此事件在发生警告时由可执行文件引发。</span><span class="sxs-lookup"><span data-stu-id="185c6-176">This event is raised by an executable when a warning occurs.</span></span>|

## <a name="configuration-of-an-event-handler"></a><span data-ttu-id="185c6-177">事件处理程序的配置</span><span class="sxs-lookup"><span data-stu-id="185c6-177">Configuration of an Event Handler</span></span>
 <span data-ttu-id="185c6-178">可以在 **的** “属性” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 窗口中设置属性，或以编程方式设置属性。</span><span class="sxs-lookup"><span data-stu-id="185c6-178">You can set properties in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>

 <span data-ttu-id="185c6-179">有关如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中设置这些属性的信息，请参阅 [设置任务或容器的属性](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="185c6-179">For information about how to set these properties in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../../2014/integration-services/set-the-properties-of-a-task-or-container.md).</span></span>

 <span data-ttu-id="185c6-180">有关如何以编程方式设置这些属性的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="185c6-180">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="185c6-181">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="185c6-181">Related Tasks</span></span>
 <span data-ttu-id="185c6-182">有关如何向包中添加事件处理程序的信息，请参阅 [在包中添加事件处理程序](../../2014/integration-services/add-an-event-handler-to-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="185c6-182">For information about how to add an event handler to a package, see [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md).</span></span>


