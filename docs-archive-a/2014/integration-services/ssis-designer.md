---
title: SSIS 设计器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services, SSIS Designer
- Business Intelligence Development Studio, Integration Services in
- tools [Integration Services], SSIS Designer
- SSIS, SSIS Designer
- SSIS Designer, about SSIS Designer
- Integration Services, SSIS Designer
ms.assetid: 006d68ea-1b5c-4c1e-8079-3910288e012c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a54a3b445317c59582b8dedcb162e244fda1b58d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690736"
---
# <a name="ssis-designer"></a><span data-ttu-id="ec611-102">SSIS 设计器</span><span class="sxs-lookup"><span data-stu-id="ec611-102">SSIS Designer</span></span>
  [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="ec611-103">设计器是用于创建和维护 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的图形工具。</span><span class="sxs-lookup"><span data-stu-id="ec611-103">Designer is a graphical tool that you can use to create and maintain [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="ec611-104">设计器作为 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 项目的一部分，位于 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="ec611-104">Designer is available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] as part of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

 <span data-ttu-id="ec611-105">可以使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="ec611-105">You can use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to perform the following tasks:</span></span>

-   <span data-ttu-id="ec611-106">在包中构造控制流。</span><span class="sxs-lookup"><span data-stu-id="ec611-106">Constructing the control flow in a package.</span></span>

-   <span data-ttu-id="ec611-107">在包中构造数据流。</span><span class="sxs-lookup"><span data-stu-id="ec611-107">Constructing the data flows in a package.</span></span>

-   <span data-ttu-id="ec611-108">将事件处理程序添加到包和包对象。</span><span class="sxs-lookup"><span data-stu-id="ec611-108">Adding event handlers to the package and package objects.</span></span>

-   <span data-ttu-id="ec611-109">查看包内容。</span><span class="sxs-lookup"><span data-stu-id="ec611-109">Viewing the package content.</span></span>

-   <span data-ttu-id="ec611-110">在运行时查看包的执行进度。</span><span class="sxs-lookup"><span data-stu-id="ec611-110">At run time, viewing the execution progress of the package.</span></span>

 <span data-ttu-id="ec611-111">下面的关系图显示 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器和 **“工具箱”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="ec611-111">The following diagram shows [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and the **Toolbox** window.</span></span>

 <span data-ttu-id="ec611-112">![SSIS 设计器和工具箱的屏幕快照](media/denali-designerandtoolbox.gif "SSIS 设计器和工具箱的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="ec611-112">![Screenshot of SSIS Designer and Toolbox](media/denali-designerandtoolbox.gif "Screenshot of SSIS Designer and Toolbox")</span></span>

 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="ec611-113">还有其他一些用于将功能添加到包的对话框和窗口，而 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 提供用于配置开发环境及对包进行操作的窗口和对话框。</span><span class="sxs-lookup"><span data-stu-id="ec611-113">includes additional dialog boxes and windows for adding functionality to packages, and [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] provides windows and dialog boxes for configuring the development environment and working with packages.</span></span> <span data-ttu-id="ec611-114">有关详细信息，请参阅 [Integration Services 用户界面](integration-services-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="ec611-114">For more information, see [Integration Services User Interface](integration-services-user-interface.md).</span></span>

 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="ec611-115">设计器不依赖于 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务（即管理和监视包的服务），而且在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中创建或修改包也不需要该服务处于运行状态。</span><span class="sxs-lookup"><span data-stu-id="ec611-115">Designer has no dependency on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, the service that manages and monitors packages, and it is not required that the service be running to create or modify packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ec611-116">但是，如果在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器打开的情况下停止该服务，则您无法再打开 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器提供的对话框，并且可能收到“RPC 服务器不可用”的错误消息。</span><span class="sxs-lookup"><span data-stu-id="ec611-116">However, if you stop the service while [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer is open, you can no longer open the dialog boxes that [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides and you may receive the error message "RPC server is unavailable."</span></span> <span data-ttu-id="ec611-117">若要重置 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器并继续对包进行操作，就必须关闭设计器，退出 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]，然后重新打开 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目和包。</span><span class="sxs-lookup"><span data-stu-id="ec611-117">To reset [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and continue working with the package, you must close the designer, exit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], and then reopen [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and the package.</span></span>

## <a name="undo-and-redo"></a><span data-ttu-id="ec611-118">撤消和重做</span><span class="sxs-lookup"><span data-stu-id="ec611-118">Undo and Redo</span></span>
 <span data-ttu-id="ec611-119">您可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中撤消或重做最多 20 个操作。</span><span class="sxs-lookup"><span data-stu-id="ec611-119">You can undo and redo up to 20 actions in the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ec611-120">对于包，可以在“控制流”  、“数据流”  、“事件处理程序”  和“参数”  选项卡以及“变量”  窗口中进行撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="ec611-120">For a package, undo /redo is available in the **Control Flow**, **Data Flow**, **Event Handlers**, and **Parameters** tabs, and in the **Variables** window.</span></span> <span data-ttu-id="ec611-121">对于项目，可以在“项目参数”  窗口中进行撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="ec611-121">For a project, undo/redo is available in the **Project Parameters** window.</span></span>

 <span data-ttu-id="ec611-122">不能撤消/重做对新的“SSIS 工具箱”所做的更改  。</span><span class="sxs-lookup"><span data-stu-id="ec611-122">You can't undo/redo changes to the new **SSIS Toolbox**.</span></span>

 <span data-ttu-id="ec611-123">使用组件编辑器更改组件时，可以将更改作为一个组来撤消和重做，而不是撤消和重做单个更改。</span><span class="sxs-lookup"><span data-stu-id="ec611-123">When you make changes to a component using the component editor, you undo and redo the changes as a set rather than undoing and redoing individual changes.</span></span> <span data-ttu-id="ec611-124">更改组在撤消和重做下拉列表中显示为单个操作。</span><span class="sxs-lookup"><span data-stu-id="ec611-124">The set of changes appears as a single action in the undo and redo drop-down list.</span></span>

 <span data-ttu-id="ec611-125">若要撤消操作，请单击撤消工具栏按钮、“编辑/撤消”  菜单项，或按 Ctrl+Z。</span><span class="sxs-lookup"><span data-stu-id="ec611-125">To undo an action, click the undo toolbar button, **Edit/Undo** menu item, or press CTRL+Z.</span></span> <span data-ttu-id="ec611-126">若要恢复操作，请单击恢复工具栏按钮、“编辑/恢复”  菜单项或按 CTRL + Y。若要撤消和恢复多项操作，可以单击相应工具栏按钮旁边的箭头，在下拉列表中选中多项操作，然后在该列表中单击。</span><span class="sxs-lookup"><span data-stu-id="ec611-126">To redo an action, click the redo toolbar button, **Edit/Redo** menu item or press CTRL + Y. You can undo and redo multiple actions, by clicking the arrow next to the toolbar button, highlighting multiple actions in the drop-down list, and then clicking in the list.</span></span>

## <a name="parts-of-the-ssis-designer"></a><span data-ttu-id="ec611-127">SSIS 设计器的部件</span><span class="sxs-lookup"><span data-stu-id="ec611-127">Parts of the SSIS Designer</span></span>
 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="ec611-128">设计器有五个永久选项卡：其中四个选项卡分别用于生成包控制流、数据流、参数和事件处理程序，另外一个选项卡用于查看包的内容。</span><span class="sxs-lookup"><span data-stu-id="ec611-128">Designer has five permanent tabs: one each for building package control flow, data flows, parameters, and event handlers, and one tab for viewing the contents of a package.</span></span> <span data-ttu-id="ec611-129">运行时将出现第六个选项卡，显示包在运行时的执行进度以及完成后的执行结果。</span><span class="sxs-lookup"><span data-stu-id="ec611-129">At run time a sixth tab appears that shows the execution progress of a package while it is running and the execution results after it finishes.</span></span>

 <span data-ttu-id="ec611-130">此外， [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器还包括连接管理器区域，用于添加和配置包连接到数据所使用的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ec611-130">In addition, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer includes the Connection Managers area for adding and configuring the connection managers that a package uses to connect to data.</span></span>

### <a name="control-flow-tab"></a><span data-ttu-id="ec611-131">“控制流”选项卡</span><span class="sxs-lookup"><span data-stu-id="ec611-131">Control Flow Tab</span></span>
 <span data-ttu-id="ec611-132">若要构造包中的控制流，即可在 **“控制流”** 选项卡的设计图面进行。先将所需项从 **“工具箱”** 逐个拖动到设计图面上，然后单击项的图标，将箭头从一项拖动到另一项，如此反复，将这些项连成一个控制流。</span><span class="sxs-lookup"><span data-stu-id="ec611-132">You construct the control flow in a package on the design surface of the **Control Flow** tab. Drag items from **Toolbox** to the design surface and connect them into a control flow by clicking the icon for the item, and then dragging the arrow from one item to another.</span></span>

 <span data-ttu-id="ec611-133">有关详细信息，请参阅 [Control Flow](control-flow/control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="ec611-133">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>

### <a name="data-flow-tab"></a><span data-ttu-id="ec611-134">“数据流”选项卡</span><span class="sxs-lookup"><span data-stu-id="ec611-134">Data Flow Tab</span></span>
 <span data-ttu-id="ec611-135">如果包中包含数据流任务，则可以将数据流添加到包。</span><span class="sxs-lookup"><span data-stu-id="ec611-135">If a package contains a Data flow task, you can add data flows to the package.</span></span> <span data-ttu-id="ec611-136">在 **“数据流”** 选项卡设计图面上的包中构造数据流。先将所需项从 **“工具箱”** 逐个拖动到设计图面上，然后单击项的图标，将一项的箭头拖动到另一项，如此反复，将这些项连成一个数据流。</span><span class="sxs-lookup"><span data-stu-id="ec611-136">You construct the data flows in a package on the design surface of the **Data Flow** tab. Drag items from **Toolbox** to the design surface and connect them into a data flow by clicking the icon for the item, and then dragging the arrow from one item to another.</span></span>

 <span data-ttu-id="ec611-137">有关详细信息，请参阅 [Data Flow](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="ec611-137">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>

### <a name="parameters-tab"></a><span data-ttu-id="ec611-138">“参数”选项卡</span><span class="sxs-lookup"><span data-stu-id="ec611-138">Parameters Tab</span></span>
 <span data-ttu-id="ec611-139">Integration Services (SSIS) 参数可用于在包执行时向包内的属性赋值。</span><span class="sxs-lookup"><span data-stu-id="ec611-139">Integration Services (SSIS) parameters allow you to assign values to properties within packages at the time of package execution.</span></span> <span data-ttu-id="ec611-140">您可以在项目级别创建项目参数，在包级别创建包参数。</span><span class="sxs-lookup"><span data-stu-id="ec611-140">You can create project parameters at the project level and package parameters at the package level.</span></span> <span data-ttu-id="ec611-141">项目参数可用于向项目中的一个或多个包提供项目接收的任何外部输入。</span><span class="sxs-lookup"><span data-stu-id="ec611-141">Project parameters are used to supply any external input the project receives to one or more packages in the project.</span></span> <span data-ttu-id="ec611-142">利用包参数，您不必编辑和重新部署包就可以修改包执行。</span><span class="sxs-lookup"><span data-stu-id="ec611-142">Package parameters allow you to modify package execution without having to edit and redeploy the package.</span></span> <span data-ttu-id="ec611-143">您可以利用此选项卡来管理包参数。</span><span class="sxs-lookup"><span data-stu-id="ec611-143">This tab allows you to manage package parameters.</span></span>

 <span data-ttu-id="ec611-144">有关参数的详细信息，请参阅 [Integration Services (SSIS) 参数](integration-services-ssis-package-and-project-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ec611-144">For more information about parameters, see [Integration Services &#40;SSIS&#41; Parameters](integration-services-ssis-package-and-project-parameters.md).</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ec611-145">参数仅可用于为项目部署模型开发的项目。</span><span class="sxs-lookup"><span data-stu-id="ec611-145">Parameters are available only to projects developed for the project deployment model.</span></span> <span data-ttu-id="ec611-146">因此，仅对于属于配置为使用项目部署模型的项目一部分的包，您才会看到“参数”选项卡。</span><span class="sxs-lookup"><span data-stu-id="ec611-146">Therefore, you will see the Parameters tab only for packages that are part of a project configured to use the project deployment model.</span></span>

### <a name="event-handlers-tab"></a><span data-ttu-id="ec611-147">“事件处理程序”选项卡</span><span class="sxs-lookup"><span data-stu-id="ec611-147">Event Handlers Tab</span></span>
 <span data-ttu-id="ec611-148">在 **“事件处理程序”** 选项卡设计图面上构造包中的事件。在 **“事件处理程序”** 选项卡上选择要为之创建事件处理程序的包或包对象，再选择要与事件处理程序相关联的事件。</span><span class="sxs-lookup"><span data-stu-id="ec611-148">You construct the events in a package on the design surface of the **Event Handlers** tab. On the **Event Handlers** tab, you select the package or package object that you want to create an event handler for, and then select the event to associate with the event handler.</span></span> <span data-ttu-id="ec611-149">一个事件处理程序有一个控制流，如果需要，还可以有多个可选的数据流。</span><span class="sxs-lookup"><span data-stu-id="ec611-149">An event handler has a control flow and optional data flows.</span></span>

 <span data-ttu-id="ec611-150">有关详细信息，请参阅 [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="ec611-150">For more information, see [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md).</span></span>

### <a name="package-explorer-tab"></a><span data-ttu-id="ec611-151">“包资源管理器”选项卡</span><span class="sxs-lookup"><span data-stu-id="ec611-151">Package Explorer Tab</span></span>
 <span data-ttu-id="ec611-152">包可以很复杂，包括多项任务、连接管理器、变量和其他元素。</span><span class="sxs-lookup"><span data-stu-id="ec611-152">Packages can be complex, including many tasks, connection managers, variables, and other elements.</span></span> <span data-ttu-id="ec611-153">在包的资源管理器视图中，可以查看完整的包元素列表。</span><span class="sxs-lookup"><span data-stu-id="ec611-153">The explorer view of the package lets you see a complete list of package elements.</span></span>

 <span data-ttu-id="ec611-154">有关详细信息，请参阅 [查看包对象](view-package-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="ec611-154">For more information, see [View Package Objects](view-package-objects.md).</span></span>

#### <a name="progressexecution-result-tab"></a><span data-ttu-id="ec611-155">“进度/执行结果”选项卡</span><span class="sxs-lookup"><span data-stu-id="ec611-155">Progress/Execution Result Tab</span></span>
 <span data-ttu-id="ec611-156">在包运行过程中， **“进度”** 选项卡显示包的执行进度。</span><span class="sxs-lookup"><span data-stu-id="ec611-156">While a package is running, the **Progress** tab shows the execution progress of the package.</span></span> <span data-ttu-id="ec611-157">在包运行完毕后， **“执行结果”** 选项卡上就一直显示执行结果。</span><span class="sxs-lookup"><span data-stu-id="ec611-157">After the package has finished running, the execution results remain available on the **Execution Result** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="ec611-158">若要允许或禁止在 **“进度”** 选项卡上显示消息，请在 **SSIS** 菜单上切换 **“调试进度报告”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ec611-158">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

##### <a name="connection-managers-area"></a><span data-ttu-id="ec611-159">连接管理器区域</span><span class="sxs-lookup"><span data-stu-id="ec611-159">Connection Managers Area</span></span>
 <span data-ttu-id="ec611-160">**“连接管理器”** 区域用于添加和修改包使用的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ec611-160">You add and modify the connection managers that a package uses in the **Connection Managers** area.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="ec611-161">包括连接到多种数据源（如文本文件、OLE DB 数据库和 .Net 提供程序）的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ec611-161">includes connection managers to connect to a variety of data sources, such as text files, OLE DB databases, and .NET providers.</span></span>

 <span data-ttu-id="ec611-162">有关详细信息，请参阅 [Integration Services (SSIS) 连接](connection-manager/integration-services-ssis-connections.md)和[创建连接管理器](../../2014/integration-services/create-connection-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="ec611-162">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md) and [Create Connection Managers](../../2014/integration-services/create-connection-managers.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="ec611-163">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ec611-163">Related Tasks</span></span>

-   [<span data-ttu-id="ec611-164">在 SQL Server Data Tools 中创建包</span><span class="sxs-lookup"><span data-stu-id="ec611-164">Create Packages in SQL Server Data Tools</span></span>](create-packages-in-sql-server-data-tools.md)

## <a name="see-also"></a><span data-ttu-id="ec611-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec611-165">See Also</span></span>
 [<span data-ttu-id="ec611-166">Integration Services 用户界面</span><span class="sxs-lookup"><span data-stu-id="ec611-166">Integration Services User Interface</span></span>](integration-services-user-interface.md)


