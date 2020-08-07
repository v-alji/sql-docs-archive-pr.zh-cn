---
title: 序列容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sequencecontainer.f1
helpviewer_keywords:
- Sequence container
- grouping control flows
- containers [Integration Services], Sequence
- subset control flow [Integration Services]
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b972f923e2134363ba1b378beebebbeb1e5d6bb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587950"
---
# <a name="sequence-container"></a><span data-ttu-id="e306e-102">序列容器</span><span class="sxs-lookup"><span data-stu-id="e306e-102">Sequence Container</span></span>
  <span data-ttu-id="e306e-103">序列容器可定义作为包控制流子集的控制流。</span><span class="sxs-lookup"><span data-stu-id="e306e-103">The Sequence container defines a control flow that is a subset of the package control flow.</span></span> <span data-ttu-id="e306e-104">序列容器将包分组到多个单独的控制流中，每个控制流包含一个或多个在整体包控制流中运行的任务和容器。</span><span class="sxs-lookup"><span data-stu-id="e306e-104">Sequence containers group the package into multiple separate control flows, each containing one or more tasks and containers that run within the overall package control flow.</span></span>  
  
 <span data-ttu-id="e306e-105">除包含其他容器外，序列容器还可以包含多个任务。</span><span class="sxs-lookup"><span data-stu-id="e306e-105">The Sequence container can include multiple tasks in addition to other containers.</span></span> <span data-ttu-id="e306e-106">将任务和容器添加到序列容器的过程与将它们添加到包的过程相似，唯一不同是把任务和容器拖动到序列容器，而不是拖动到包容器。</span><span class="sxs-lookup"><span data-stu-id="e306e-106">Adding tasks and containers to a Sequence container is similar to adding them to a package, except you drag the tasks and containers to the Sequence container instead of to the package container.</span></span> <span data-ttu-id="e306e-107">如果序列容器包含多个任务或容器，可以使用优先约束连接它们，如同在包中的操作一样。</span><span class="sxs-lookup"><span data-stu-id="e306e-107">If the Sequence container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="e306e-108">有关详细信息，请参阅 [优先约束](precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="e306e-108">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="e306e-109">使用序列容器有许多好处：</span><span class="sxs-lookup"><span data-stu-id="e306e-109">There are many benefits of using a Sequence container:</span></span>  
  
-   <span data-ttu-id="e306e-110">禁用任务组，以便将包调试主要放在包控制流的一个子集上执行。</span><span class="sxs-lookup"><span data-stu-id="e306e-110">Disabling groups of tasks to focus package debugging on one subset of the package control flow.</span></span>  
  
-   <span data-ttu-id="e306e-111">通过设置序列容器而不是各个任务的属性来管理一个位置中多个任务的属性。</span><span class="sxs-lookup"><span data-stu-id="e306e-111">Managing properties on multiple tasks in one location by setting properties on a Sequence container instead of on the individual tasks.</span></span>  
  
     <span data-ttu-id="e306e-112">例如，可以将序列容器的 `Disable` 属性设置为 `True`，以禁用序列容器中的所有任务和容器。</span><span class="sxs-lookup"><span data-stu-id="e306e-112">For example, you can set the `Disable` property of the Sequence container to `True` to disable all the tasks and containers in the Sequence container.</span></span>  
  
-   <span data-ttu-id="e306e-113">提供一组相关任务和容器所用变量的范围。</span><span class="sxs-lookup"><span data-stu-id="e306e-113">Providing scope for variables that a group of related tasks and containers use.</span></span>  
  
-   <span data-ttu-id="e306e-114">对许多任务进行分组，以便您可以通过展开和折叠序列容器，更轻松地管理这些任务。</span><span class="sxs-lookup"><span data-stu-id="e306e-114">Grouping many tasks so you can more easily managed them by collapsing and expanding the Sequence container.</span></span>  
  
     <span data-ttu-id="e306e-115">也可以创建任务组，这些任务组用 **“分组”** 框展开和折叠。</span><span class="sxs-lookup"><span data-stu-id="e306e-115">You can also create task groups, which expand and collapse using the **Group** box.</span></span> <span data-ttu-id="e306e-116">但是，“分组”  框是设计时功能，没有属性或运行时行为。</span><span class="sxs-lookup"><span data-stu-id="e306e-116">However, the **Group** box is a design-time feature that has no properties or run-time behavior.</span></span> <span data-ttu-id="e306e-117">有关详细信息，请参阅 [对组件分组或取消分组](../group-or-ungroup-components.md)</span><span class="sxs-lookup"><span data-stu-id="e306e-117">For more information, see [Group or Ungroup Components](../group-or-ungroup-components.md)</span></span>  
  
-   <span data-ttu-id="e306e-118">在序列容器上设置事务属性，以便为包控制流的子集定义事务。</span><span class="sxs-lookup"><span data-stu-id="e306e-118">Set a transaction attribute on the Sequence container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="e306e-119">采用这种方法，可以更详细地管理事务。</span><span class="sxs-lookup"><span data-stu-id="e306e-119">In this way, you can manage transactions at a more granular level.</span></span>  
  
     <span data-ttu-id="e306e-120">例如，如果序列容器包含两个相关任务（一个任务删除表中的数据，另一个将数据插入到表中），则可配置事务以确保插入操作失败时回滚删除操作。</span><span class="sxs-lookup"><span data-stu-id="e306e-120">For example, if a Sequence container includes two related tasks, one task that deletes data in a table and another task that inserts data into a table, you can configure a transaction to ensure that the delete action is rolled back if the insert action fails.</span></span> <span data-ttu-id="e306e-121">有关详细信息，请参阅 [Integration Services 事务](../integration-services-transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="e306e-121">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-sequence-container"></a><span data-ttu-id="e306e-122">序列容器的配置</span><span class="sxs-lookup"><span data-stu-id="e306e-122">Configuration of the Sequence Container</span></span>  
 <span data-ttu-id="e306e-123">序列容器没有自定义用户界面，您只能通过 **中的** “属性” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 窗口对其进行配置，或以编程方式配置。</span><span class="sxs-lookup"><span data-stu-id="e306e-123">The Sequence container has no custom user interface and you can configure it only in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>  
  
 <span data-ttu-id="e306e-124">有关以编程方式设置这些属性的详细信息，请参阅开发人员指南中针对 **T:Microsoft.SqlServer.Dts.Runtime.Sequence** 类的文档。</span><span class="sxs-lookup"><span data-stu-id="e306e-124">For information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.Sequence** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e306e-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e306e-125">Related Tasks</span></span>  
 <span data-ttu-id="e306e-126">有关如何在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中设置组件属性的信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="e306e-126">For information about how to set properties of the component in the [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e306e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e306e-127">See Also</span></span>  
 <span data-ttu-id="e306e-128">[在控制流中添加或删除任务或容器](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e306e-128">[Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="e306e-129">[使用默认优先约束来连接任务和容器](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="e306e-129">[Connect Tasks and Containers by Using a Default Precedence Constraint](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="e306e-130">Integration Services 容器</span><span class="sxs-lookup"><span data-stu-id="e306e-130">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  
