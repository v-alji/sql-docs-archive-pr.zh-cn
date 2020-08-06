---
title: 向控制流添加枚举 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59b8569880fdf1a49f5f2ca1f6841841f9790af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585946"
---
# <a name="add-enumeration-to-a-control-flow"></a><span data-ttu-id="9534f-102">将枚举添加到控制流</span><span class="sxs-lookup"><span data-stu-id="9534f-102">Add Enumeration to a Control Flow</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="9534f-103">包含 Foreach 循环容器，此容器是一个控制流元素，利用它可以轻松地将枚举文件和对象的循环构造包括到包的控制流中。</span><span class="sxs-lookup"><span data-stu-id="9534f-103">includes the Foreach Loop container, a control flow element that makes it simple to include a looping construct that enumerates files and objects in the control flow of a package.</span></span> <span data-ttu-id="9534f-104">有关详细信息，请参阅 [Foreach 循环容器](control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="9534f-104">For more information, see [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="9534f-105">Foreach 循环容器不提供任何功能，只提供用以生成可重复的控制流、指定枚举器类型以及配置枚举器的结构。</span><span class="sxs-lookup"><span data-stu-id="9534f-105">The Foreach Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow, specify an enumerator type, and configure the enumerator.</span></span> <span data-ttu-id="9534f-106">若要提供容器功能，Foreach Loop 循环容器中必须包含至少一个任务。</span><span class="sxs-lookup"><span data-stu-id="9534f-106">To provide container functionality, you must include at least one task in the Foreach Loop container.</span></span> <span data-ttu-id="9534f-107">有关详细信息，请参阅 [Integration Services Tasks](control-flow/integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="9534f-107">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="9534f-108">Foreach 循环容器可包含具有多个任务和其他容器的控制流。</span><span class="sxs-lookup"><span data-stu-id="9534f-108">The Foreach Loop container can include a control flow with multiple tasks and other containers.</span></span> <span data-ttu-id="9534f-109">除了要将任务和容器拖动到 Foreach 循环容器而不是拖放到包以外，将任务和容器添加到 Foreach 循环容器的过程与将其添加到包的过程相似。</span><span class="sxs-lookup"><span data-stu-id="9534f-109">Adding tasks and containers to a Foreach Loop container is similar to adding them to a package, except you drag the tasks and containers to the Foreach Loop container instead of to the package.</span></span> <span data-ttu-id="9534f-110">如果 Foreach 循环容器包含多个任务或容器，可以使用优先约束连接它们，这与在包中的操作一样。</span><span class="sxs-lookup"><span data-stu-id="9534f-110">If the Foreach Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="9534f-111">有关详细信息，请参阅 [优先约束](control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="9534f-111">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a><span data-ttu-id="9534f-112">在控制流中实现 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="9534f-112">To implement a Foreach Loop container in a control flow</span></span>  
  
1.  <span data-ttu-id="9534f-113">将 Foreach 循环容器添加到包。</span><span class="sxs-lookup"><span data-stu-id="9534f-113">Add the Foreach Loop container to the package.</span></span> <span data-ttu-id="9534f-114">有关详细信息，请参阅[在控制流中添加或删除任务或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="9534f-114">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="9534f-115">.</span><span class="sxs-lookup"><span data-stu-id="9534f-115">.</span></span>  
  
2.  <span data-ttu-id="9534f-116">将任务和容器添加到 Foreach 循环容器。</span><span class="sxs-lookup"><span data-stu-id="9534f-116">Add tasks and containers to the Foreach Loop container.</span></span> <span data-ttu-id="9534f-117">有关详细信息，请参阅[在控制流中添加或删除任务或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="9534f-117">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="9534f-118">.</span><span class="sxs-lookup"><span data-stu-id="9534f-118">.</span></span>  
  
3.  <span data-ttu-id="9534f-119">使用优先约束连接 Foreach 循环容器中的任务和容器。</span><span class="sxs-lookup"><span data-stu-id="9534f-119">Connect tasks and containers in the Foreach Loop container using precedence constraints.</span></span> <span data-ttu-id="9534f-120">有关详细信息，请参阅 [使用默认优先约束来连接任务和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="9534f-120">For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).</span></span>  
  
4.  <span data-ttu-id="9534f-121">配置 Foreach 循环容器。</span><span class="sxs-lookup"><span data-stu-id="9534f-121">Configure the Foreach Loop container.</span></span> <span data-ttu-id="9534f-122">有关详细信息，请参阅 [配置 Foreach 循环容器](../../2014/integration-services/configure-a-foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="9534f-122">For more information, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9534f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9534f-123">See Also</span></span>  
 <span data-ttu-id="9534f-124">[在控制流中添加或删除任务或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="9534f-124">[Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="9534f-125">[对组件进行分组或取消分组](group-or-ungroup-components.md) </span><span class="sxs-lookup"><span data-stu-id="9534f-125">[Group or Ungroup Components](group-or-ungroup-components.md) </span></span>  
 <span data-ttu-id="9534f-126">[优先约束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="9534f-126">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="9534f-127">[向控制流添加迭代](add-iteration-to-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="9534f-127">[Add Iteration to a Control Flow](add-iteration-to-a-control-flow.md) </span></span>  
 [<span data-ttu-id="9534f-128">控制流</span><span class="sxs-lookup"><span data-stu-id="9534f-128">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
