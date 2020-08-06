---
title: 控制流 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], elements
- SSIS control flow elements
- SQL Server Integration Services control flow elements
ms.assetid: 0cc042a9-1a7f-49ed-9f47-091653d5ef6e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81ace5d285a67c6fee8a3a568ed89bc564193c42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585921"
---
# <a name="control-flow"></a><span data-ttu-id="c8c54-102">控制流</span><span class="sxs-lookup"><span data-stu-id="c8c54-102">Control Flow</span></span>
  <span data-ttu-id="c8c54-103">包由一个控制流以及一个或多个数据流（可选）组成。</span><span class="sxs-lookup"><span data-stu-id="c8c54-103">A package consists of a control flow and, optionally, one or more data flows.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c8c54-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 提供了三种不同类型的控制流元素：提供包中结构的容器、提供功能的任务以及将可执行文件、容器和任务连接为已排序控制流的优先约束。</span><span class="sxs-lookup"><span data-stu-id="c8c54-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides three different types of control flow elements: containers that provide structures in packages, tasks that provide functionality, and precedence constraints that connect the executables, containers, and tasks into an ordered control flow.</span></span>

 <span data-ttu-id="c8c54-105">有关详细信息，请参阅 [Precedence Constraints](precedence-constraints.md)、 [Integration Services Containers](integration-services-containers.md)和 [Integration Services Tasks](integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c54-105">For more information, see [Precedence Constraints](precedence-constraints.md), [Integration Services Containers](integration-services-containers.md), and [Integration Services Tasks](integration-services-tasks.md).</span></span>

 <span data-ttu-id="c8c54-106">下面的关系图显示具有一个容器和六项任务的控制流。</span><span class="sxs-lookup"><span data-stu-id="c8c54-106">The following diagram shows a control flow that has one container and six tasks.</span></span> <span data-ttu-id="c8c54-107">这些任务中有五项定义于包级别，还有一项定义于容器级别。</span><span class="sxs-lookup"><span data-stu-id="c8c54-107">Five of the tasks are defined at the package level, and one task is defined at the container level.</span></span> <span data-ttu-id="c8c54-108">任务位于容器内。</span><span class="sxs-lookup"><span data-stu-id="c8c54-108">The task is inside a container.</span></span>

 <span data-ttu-id="c8c54-109">![具有六个任务和一个容器的控制流](../media/ssis-controlflowelmt.gif "具有六个任务和一个容器的控制流")</span><span class="sxs-lookup"><span data-stu-id="c8c54-109">![Control flow with six tasks and a container](../media/ssis-controlflowelmt.gif "Control flow with six tasks and a container")</span></span>

 <span data-ttu-id="c8c54-110">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 体系结构支持容器的嵌套，且一个控制流可以包含多级嵌套容器。</span><span class="sxs-lookup"><span data-stu-id="c8c54-110">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] architecture supports the nesting of containers, and a control flow can include multiple levels of nested containers.</span></span> <span data-ttu-id="c8c54-111">例如，一个包可以包含一个容器（如 Foreach 循环容器），此容器转而又能包含另一个 Foreach 循环容器，如此逐层嵌套。</span><span class="sxs-lookup"><span data-stu-id="c8c54-111">For example, a package could contain a container such as a Foreach Loop container, which in turn could contain another Foreach Loop container and so on.</span></span>

 <span data-ttu-id="c8c54-112">事件处理程序也具有控制流，而这些控制流是使用同类控制流元素生成的。</span><span class="sxs-lookup"><span data-stu-id="c8c54-112">Event handlers also have control flows, which are built using the same kinds of control flow elements.</span></span>

## <a name="control-flow-implementation"></a><span data-ttu-id="c8c54-113">控制流实现</span><span class="sxs-lookup"><span data-stu-id="c8c54-113">Control Flow Implementation</span></span>
 <span data-ttu-id="c8c54-114">通过使用 **设计器中的** “控制流” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 选项卡，在包中创建控制流。</span><span class="sxs-lookup"><span data-stu-id="c8c54-114">You create the control flow in a package by using the **Control Flow** tab in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="c8c54-115">在 **“控制流”** 选项卡处于活动状态时，工具箱将列出您可以添加到控制流的任务和容器。</span><span class="sxs-lookup"><span data-stu-id="c8c54-115">When the **Control Flow** tab is active, the Toolbox lists the tasks and containers that you can add to the control flow.</span></span>

 <span data-ttu-id="c8c54-116">下面的关系图显示了控制流设计器中简单包的控制流。</span><span class="sxs-lookup"><span data-stu-id="c8c54-116">The following diagram shows the control flow of a simple package in the control flow designer.</span></span> <span data-ttu-id="c8c54-117">此关系图中显示的控制流由三个包级任务和一个包含三个任务的包级容器组成。</span><span class="sxs-lookup"><span data-stu-id="c8c54-117">The control flow shown in the diagram is made up of three package-level tasks and one package-level container that contains three tasks.</span></span> <span data-ttu-id="c8c54-118">通过使用优先约束将任务和容器连接起来。</span><span class="sxs-lookup"><span data-stu-id="c8c54-118">The tasks and container are connected by using precedence constraints.</span></span>

 <span data-ttu-id="c8c54-119">![具有包的控制流设计器的屏幕快照](../media/samplecontrolflow.gif "具有包的控制流设计器的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="c8c54-119">![Screenshot of control flow designer with package](../media/samplecontrolflow.gif "Screenshot of control flow designer with package")</span></span>

 <span data-ttu-id="c8c54-120">创建控制流包含下列任务：</span><span class="sxs-lookup"><span data-stu-id="c8c54-120">Creating a control flow includes the following tasks:</span></span>

-   <span data-ttu-id="c8c54-121">添加在包中实现重复的工作流或将控制流划分为子集的容器。</span><span class="sxs-lookup"><span data-stu-id="c8c54-121">Adding containers that implement repeating workflows in a package or divide a control flow into subsets.</span></span>

-   <span data-ttu-id="c8c54-122">添加支持数据流、准备数据、执行工作流和商业智能功能以及实现脚本的任务。</span><span class="sxs-lookup"><span data-stu-id="c8c54-122">Adding tasks that support data flow, prepare data, perform workflow and business intelligence functions, and implement script.</span></span>

     [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="c8c54-123">包含了多种任务，可以用其创建满足包的业务要求的控制流。</span><span class="sxs-lookup"><span data-stu-id="c8c54-123">includes a variety of tasks that you can use to create control flow that meets the business requirements of the package.</span></span> <span data-ttu-id="c8c54-124">如果包必须使用数据，则控制流必须包含至少一个数据流任务。</span><span class="sxs-lookup"><span data-stu-id="c8c54-124">If the package has to work with data, the control flow must include at least one Data Flow task.</span></span> <span data-ttu-id="c8c54-125">例如，包可能必须提取数据、聚合数据值，然后将结果写入到数据源。</span><span class="sxs-lookup"><span data-stu-id="c8c54-125">For example, a package might have to extract data, aggregate data values, and then write the results to a data source.</span></span>  <span data-ttu-id="c8c54-126">有关详细信息，请参阅 [Integration Services 任务](integration-services-tasks.md) 和 [在控制流中添加或删除任务或容器](add-or-delete-a-task-or-a-container-in-a-control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c54-126">For more information, see [Integration Services Tasks](integration-services-tasks.md) and [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>

-   <span data-ttu-id="c8c54-127">使用优先约束把容器和任务连接为有序控制流。</span><span class="sxs-lookup"><span data-stu-id="c8c54-127">Connecting containers and tasks into an ordered control flow by using precedence constraints.</span></span>

     <span data-ttu-id="c8c54-128">将任务或容器添加到 **“控制流”** 选项卡的设计图面后， [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器自动将连接线添加到项。</span><span class="sxs-lookup"><span data-stu-id="c8c54-128">After you add a task or container to the design surface of the **Control Flow** tab, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically adds a connector to the item.</span></span> <span data-ttu-id="c8c54-129">如果包中包含两个或更多项、任务或容器，则可以通过将它们的连接线从一项拖动到其他项而将它们联接成控制流。</span><span class="sxs-lookup"><span data-stu-id="c8c54-129">If a package includes two or more items, tasks or containers, you can join them into a control flow by dragging their connectors from one item to another.</span></span>

     <span data-ttu-id="c8c54-130">两个项之间的连接器表示优先约束。</span><span class="sxs-lookup"><span data-stu-id="c8c54-130">The connector between two items represents a precedence constraint.</span></span> <span data-ttu-id="c8c54-131">优先约束定义了两个连接项之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c8c54-131">A precedence constraint defines the relationship between the two connected items.</span></span> <span data-ttu-id="c8c54-132">它指定了运行时任务和容器的执行顺序以及任务和容器的运行条件。</span><span class="sxs-lookup"><span data-stu-id="c8c54-132">It specifies the order in which tasks and containers are executed at run time and the conditions under which tasks and containers run.</span></span> <span data-ttu-id="c8c54-133">例如，优先约束可以指定某任务必须成功，才能运行控制流中的下一个任务。</span><span class="sxs-lookup"><span data-stu-id="c8c54-133">For example, a precedence constraint can specify that a task must succeed for the next task in the control flow to run.</span></span> <span data-ttu-id="c8c54-134">有关详细信息，请参阅 [优先约束](precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c54-134">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>

-   <span data-ttu-id="c8c54-135">添加连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c8c54-135">Adding connection managers.</span></span>

     <span data-ttu-id="c8c54-136">多个任务需要连接到数据源，因此必须将任务需要的连接管理器添加到包。</span><span class="sxs-lookup"><span data-stu-id="c8c54-136">Many tasks require a connection to a data source, and you have to add the connection managers that the task requires to the package.</span></span> <span data-ttu-id="c8c54-137">根据所使用的枚举器类型，Foreach 循环容器可能也需要连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c8c54-137">Depending on the enumerator type it uses, the Foreach Loop container may also require a connection manager.</span></span> <span data-ttu-id="c8c54-138">可以在逐项构造控制流时或开始构造控制流前添加连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c8c54-138">You can add the connection managers as you construct the control flow item by item or before you start to construct the control flow.</span></span> <span data-ttu-id="c8c54-139">有关详细信息，请参阅 [Integration Services (SSIS) 连接](../connection-manager/integration-services-ssis-connections.md)和[创建连接管理器](../create-connection-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c54-139">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) and [Create Connection Managers](../create-connection-managers.md).</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="c8c54-140">设计器也包含多个设计时功能，这些功能可用于管理设计图面以及使控制流自文档化。</span><span class="sxs-lookup"><span data-stu-id="c8c54-140">Designer also includes many design-time features that you can use to manage the design surface and make the control flow self-documenting.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="c8c54-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c8c54-141">Related Tasks</span></span>

-   [<span data-ttu-id="c8c54-142">在控制流中添加或删除任务或容器</span><span class="sxs-lookup"><span data-stu-id="c8c54-142">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)

-   [<span data-ttu-id="c8c54-143">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="c8c54-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)

-   [<span data-ttu-id="c8c54-144">对组件分组或取消分组</span><span class="sxs-lookup"><span data-stu-id="c8c54-144">Group or Ungroup Components</span></span>](../group-or-ungroup-components.md)


