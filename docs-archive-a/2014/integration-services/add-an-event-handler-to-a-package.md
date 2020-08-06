---
title: 向包中添加事件处理程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- event handlers [Integration Services], creating
ms.assetid: 5e56885d-8658-480a-bed9-3f2f8003fd78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 007d81a395e06ac5a97210cd3e3ed6eea91aee57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585958"
---
# <a name="add-an-event-handler-to-a-package"></a><span data-ttu-id="ac180-102">在包中添加事件处理程序</span><span class="sxs-lookup"><span data-stu-id="ac180-102">Add an Event Handler to a Package</span></span>
  <span data-ttu-id="ac180-103">在运行时，容器和任务引发事件。</span><span class="sxs-lookup"><span data-stu-id="ac180-103">At run time, containers and tasks raise events.</span></span> <span data-ttu-id="ac180-104">您可以创建自定义事件处理程序，这些程序在事件被引发时运行工作流，以对事件做出响应。</span><span class="sxs-lookup"><span data-stu-id="ac180-104">You can create custom event handlers that respond to these events by running a workflow when the event is raised.</span></span> <span data-ttu-id="ac180-105">例如，您可创建一个事件处理程序，在任务失败时发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="ac180-105">For example, you can create an event handler that sends an e-mail message when a task fails.</span></span>  
  
 <span data-ttu-id="ac180-106">事件处理程序与包类似。</span><span class="sxs-lookup"><span data-stu-id="ac180-106">An event handler is similar to a package.</span></span> <span data-ttu-id="ac180-107">事件处理程序可以像包一样为变量提供作用域，并且包含控制流和可选数据流。</span><span class="sxs-lookup"><span data-stu-id="ac180-107">Like a package, an event handler can provide scope for variables, and includes a control flow and optional data flows.</span></span> <span data-ttu-id="ac180-108">您可以为包、Foreach 循环容器、For 循环容器和序列容器以及所有的任务生成事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="ac180-108">You can build event handlers for packages, the Foreach Loop container, the For Loop container, the Sequence container, and all tasks.</span></span>  
  
 <span data-ttu-id="ac180-109">您可以使用 **设计器中的** “事件处理程序” [!INCLUDE[ssIS](../includes/ssis-md.md)] 选项卡的设计图面来创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="ac180-109">You create event handlers by using the design surface of the **Event Handlers** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="ac180-110">当 **“事件处理程序”** 选项卡活动时， **设计器中的工具箱的** “控制流项” **和** “维护计划中的任务” [!INCLUDE[ssIS](../includes/ssis-md.md)] 节点包含用于生成事件处理程序中控制流的任务和容器。</span><span class="sxs-lookup"><span data-stu-id="ac180-110">When the **Event Handlers** tab is active, the **Control Flow Items** and **Maintenance Plan Tasks** nodes of the Toolbox in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer contain the task and containers for building the control flow in the event handler.</span></span> <span data-ttu-id="ac180-111">**“数据流源”**、 **“转换”** 和 **“数据流目标”** 节点包含用于生成事件处理程序中数据流的数据源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="ac180-111">The **Data Flow Sources**, **Transformations**, **and Data Flow Destinations** nodes contain the data sources, transformations, and destinations for building the data flows in the event handler.</span></span> <span data-ttu-id="ac180-112">有关详细信息，请参阅 [Control Flow](control-flow/control-flow.md) 和 [Data Flow](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="ac180-112">For more information, see [Control Flow](control-flow/control-flow.md) and [Data Flow](data-flow/data-flow.md).</span></span>  
  
 <span data-ttu-id="ac180-113">**“事件处理程序”** 选项卡也包含 **“连接管理器”** 区域，在这里可创建并修改事件处理程序用来连接到服务器和数据源的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ac180-113">The **Event Handlers** tab also includes the **Connections** Managers area where you can create and modify the connection managers that event handlers use to connect to servers and data sources.</span></span> <span data-ttu-id="ac180-114">有关详细信息，请参阅 [创建连接管理器](../../2014/integration-services/create-connection-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="ac180-114">For more information, see [Create Connection Managers](../../2014/integration-services/create-connection-managers.md).</span></span>  
  
### <a name="to-create-an-event-handler"></a><span data-ttu-id="ac180-115">创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="ac180-115">To create an event handler</span></span>  
  
1.  <span data-ttu-id="ac180-116">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="ac180-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="ac180-117">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="ac180-117">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="ac180-118">单击 **“事件处理程序”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ac180-118">Click the **Event Handlers** tab.</span></span>  
  
     <span data-ttu-id="ac180-119">![带有事件处理程序的设计图面的屏幕快照](media/eventhandlers.gif "带有事件处理程序的设计图面的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="ac180-119">![Screenshot of design surface with event handler](media/eventhandlers.gif "Screenshot of design surface with event handler")</span></span>  
  
     <span data-ttu-id="ac180-120">在事件处理程序中创建控制流和数据流类似于在包中创建控制流和数据流。</span><span class="sxs-lookup"><span data-stu-id="ac180-120">Creating the control flow and data flows in an event handler is similar to creating the control flow and data flows in a package.</span></span> <span data-ttu-id="ac180-121">有关详细信息，请参阅 [Control Flow](control-flow/control-flow.md) 和 [Data Flow](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="ac180-121">For more information, see [Control Flow](control-flow/control-flow.md) and [Data Flow](data-flow/data-flow.md).</span></span>  
  
4.  <span data-ttu-id="ac180-122">在 **“可执行文件”** 列表中，选择要为其创建事件处理程序的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="ac180-122">In the **Executable** list, select the executable for which you want to create an event handler.</span></span>  
  
5.  <span data-ttu-id="ac180-123">在 **“事件处理程序”** 列表中，选择要生成的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="ac180-123">In the **Event handler** list, select the event handler you want to build.</span></span>  
  
6.  <span data-ttu-id="ac180-124">单击 **“事件处理程序”** 选项卡的设计图面上的链接。</span><span class="sxs-lookup"><span data-stu-id="ac180-124">Click the link on the design surface of the **Event Handler** tab.</span></span>  
  
7.  <span data-ttu-id="ac180-125">将控制流项添加到事件处理程序，并且通过将优先约束从一个控制流项拖到另一控制流项，使用该约束来连接这些控制流项。</span><span class="sxs-lookup"><span data-stu-id="ac180-125">Add control flow items to the event handler, and connect items using a precedence constraint by dragging the constraint from one control flow item to another.</span></span> <span data-ttu-id="ac180-126">有关详细信息，请参阅 [Control Flow](control-flow/control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="ac180-126">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>  
  
8.  <span data-ttu-id="ac180-127">还可以根据需要添加数据流任务，并且在 **“数据流”** 选项卡的设计图面上，为事件处理程序创建数据流。</span><span class="sxs-lookup"><span data-stu-id="ac180-127">Optionally, add a Data Flow task, and on the design surface of the **Data Flow** tab, create a data flow for the event handler.</span></span> <span data-ttu-id="ac180-128">有关详细信息，请参阅 [Data Flow](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="ac180-128">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>  
  
9. <span data-ttu-id="ac180-129">在 **“文件”** 菜单上，单击 **“保存选定项”** 以保存包。</span><span class="sxs-lookup"><span data-stu-id="ac180-129">On the **File** menu, click **Save Selected Items** to save the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac180-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac180-130">See Also</span></span>  
 <span data-ttu-id="ac180-131">[SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="ac180-131">[SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md) </span></span>  
 [<span data-ttu-id="ac180-132">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="ac180-132">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
