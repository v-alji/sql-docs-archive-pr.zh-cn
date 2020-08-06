---
title: 在控制流中添加或删除任务或容器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], adding
- adding tasks
- adding containers
- tasks [Integration Services], adding
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8338a4143358d732a974287e587f482dc5c36a22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587557"
---
# <a name="add-or-delete-a-task-or-a-container-in-a-control-flow"></a><span data-ttu-id="63770-102">在控制流中添加或删除任务或容器</span><span class="sxs-lookup"><span data-stu-id="63770-102">Add or Delete a Task or a Container in a Control Flow</span></span>
  <span data-ttu-id="63770-103">在控制流设计器中工作时， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中的工具箱会列出 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 为在包中生成控制流而提供的任务。</span><span class="sxs-lookup"><span data-stu-id="63770-103">When you are working in the control flow designer, the Toolbox in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists the tasks that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides for building control flow in a package.</span></span> <span data-ttu-id="63770-104">有关这些工具箱的详细信息，请参阅 [SSIS Toolbox](../ssis-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="63770-104">For more information about the Toolbox, see [SSIS Toolbox](../ssis-toolbox.md).</span></span>  
  
 <span data-ttu-id="63770-105">包可以包含同一任务的多个实例。</span><span class="sxs-lookup"><span data-stu-id="63770-105">A package can include multiple instances of the same task.</span></span> <span data-ttu-id="63770-106">任务的每个实例在包中都唯一标识，因此可以分别配置每个实例。</span><span class="sxs-lookup"><span data-stu-id="63770-106">Each instance of a task is uniquely identified in the package, and you can configure each instance differently.</span></span>  
  
 <span data-ttu-id="63770-107">如果删除任务，则将该任务连接到控制流中其他任务和容器的优先约束也将被删除。</span><span class="sxs-lookup"><span data-stu-id="63770-107">If you delete a task, the precedence constraints that connect the task to other tasks and containers in the control flow are also deleted.</span></span>  
  
 <span data-ttu-id="63770-108">下面的过程介绍如何在包的控制流中添加或删除任务或容器。</span><span class="sxs-lookup"><span data-stu-id="63770-108">The following procedures describe how to add or delete a task or container in the control flow of a package.</span></span>  
  
### <a name="to-add-a-task-or-a-container-to-a-control-flow"></a><span data-ttu-id="63770-109">将任务或容器添加到控制流</span><span class="sxs-lookup"><span data-stu-id="63770-109">To add a task or a container to a control flow</span></span>  
  
1.  <span data-ttu-id="63770-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="63770-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="63770-111">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="63770-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="63770-112">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="63770-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="63770-113">若要打开 **“工具箱”** ，请单击 **“查看”** 菜单上的 **“工具箱”** 。</span><span class="sxs-lookup"><span data-stu-id="63770-113">To open the **Toolbox**, click **Toolbox** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="63770-114">展开 **“控制流项”** 和 **“维护任务”** 。</span><span class="sxs-lookup"><span data-stu-id="63770-114">Expand **Control Flow Items** and **Maintenance Tasks**.</span></span>  
  
6.  <span data-ttu-id="63770-115">将任务和容器从 **“工具箱”** 拖动到 **“控制流”** 选项卡的设计图面。</span><span class="sxs-lookup"><span data-stu-id="63770-115">Drag tasks and containers from the **Toolbox** to the design surface of the **Control Flow** tab.</span></span>  
  
7.  <span data-ttu-id="63770-116">将任务或容器的连接线拖动到控制流中的另一组件，从而连接包控制流内的任务或容器。</span><span class="sxs-lookup"><span data-stu-id="63770-116">Connect a task or container within the package control flow by dragging its connector to another component in the control flow.</span></span>  
  
8.  <span data-ttu-id="63770-117">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="63770-117">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-task-or-a-container-from-a-control-flow"></a><span data-ttu-id="63770-118">从控制流删除任务或容器</span><span class="sxs-lookup"><span data-stu-id="63770-118">To delete a task or a container from a control flow</span></span>  
  
1.  <span data-ttu-id="63770-119">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="63770-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="63770-120">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="63770-120">In Solution Explorer, double-click the package to open it.</span></span> <span data-ttu-id="63770-121">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="63770-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="63770-122">单击“控制流”  选项卡，右键单击要删除的任务或容器，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="63770-122">Click the **Control Flow** tab, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
    -   <span data-ttu-id="63770-123">打开 **包资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="63770-123">Open **Package Explorer**.</span></span> <span data-ttu-id="63770-124">在“可执行文件”  文件夹上，右键单击要删除的任务或容器，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="63770-124">From the **Executables** folder, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="63770-125">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="63770-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63770-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63770-126">See Also</span></span>  
 <span data-ttu-id="63770-127">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="63770-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="63770-128">[Integration Services 容器](integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="63770-128">[Integration Services Containers](integration-services-containers.md) </span></span>  
 [<span data-ttu-id="63770-129">控制流</span><span class="sxs-lookup"><span data-stu-id="63770-129">Control Flow</span></span>](control-flow.md)  
  
  
