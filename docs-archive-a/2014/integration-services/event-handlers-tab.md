---
title: "\"事件处理程序\" 选项卡 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5f25a9b0d602a3189feab797b7ef9c333decabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587508"
---
# <a name="event-handlers-tab"></a><span data-ttu-id="82200-102">“事件处理程序”选项卡</span><span class="sxs-lookup"><span data-stu-id="82200-102">Event Handlers Tab</span></span>
  <span data-ttu-id="82200-103">可以使用 **设计器的** “事件处理程序” [!INCLUDE[ssIS](../includes/ssis-md.md)] 选项卡在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包中生成控制流。</span><span class="sxs-lookup"><span data-stu-id="82200-103">Use the **Event Handlers** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to build a control flow in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="82200-104">事件处理程序可因响应由包、包中的任务或容器所引发的事件而运行。</span><span class="sxs-lookup"><span data-stu-id="82200-104">An event handler runs in response to an event raised by the package or by a task or container in the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="82200-105">选项</span><span class="sxs-lookup"><span data-stu-id="82200-105">Options</span></span>  
 <span data-ttu-id="82200-106">**可执行文件**</span><span class="sxs-lookup"><span data-stu-id="82200-106">**Executable**</span></span>  
 <span data-ttu-id="82200-107">选择要为其生成事件处理程序的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="82200-107">Select the executable for which you want to build an event handler.</span></span> <span data-ttu-id="82200-108">可执行文件可以是包、包中的任务或容器。</span><span class="sxs-lookup"><span data-stu-id="82200-108">The executable can be the package, or a task or containers in the package.</span></span>  
  
 <span data-ttu-id="82200-109">**事件处理程序**</span><span class="sxs-lookup"><span data-stu-id="82200-109">**Event handler**</span></span>  
 <span data-ttu-id="82200-110">选择事件处理程序的类型。</span><span class="sxs-lookup"><span data-stu-id="82200-110">Select a type of event handler.</span></span> <span data-ttu-id="82200-111">通过从 **“工具箱”** 中拖动相应项即可创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="82200-111">Create the event handler by dragging items from the **Toolbox**.</span></span>  
  
 <span data-ttu-id="82200-112">**删除**</span><span class="sxs-lookup"><span data-stu-id="82200-112">**Delete**</span></span>  
 <span data-ttu-id="82200-113">选择一个事件处理程序，再通过单击“删除”  将其从包中删除。</span><span class="sxs-lookup"><span data-stu-id="82200-113">Select an event handler, and remove it from the package by clicking **Delete**.</span></span>  
  
 <span data-ttu-id="82200-114">单击此处为可执行文件 \<executable name> 创建一个 \<event handler name></span><span class="sxs-lookup"><span data-stu-id="82200-114">**Click here to create an \<event handler name> for the executable \<executable name>**</span></span>  
 <span data-ttu-id="82200-115">单击此项可创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="82200-115">Click to create the event handler.</span></span>  
  
 <span data-ttu-id="82200-116">通过将代表 [!INCLUDE[ssIS](../includes/ssis-md.md)] 任务和容器的图形对象从 **“工具箱”** 拖至 **“事件处理程序”** 选项卡的设计图面，再通过使用优先约束定义其运行顺序来连接这些对象，即可创建控制流。</span><span class="sxs-lookup"><span data-stu-id="82200-116">Create the control flow by dragging graphical objects that represent [!INCLUDE[ssIS](../includes/ssis-md.md)] tasks and containers from the **Toolbox** to the design surface of the **Event Handlers** tab, and then connecting the objects by using precedence constraints to define the sequence in which they run.</span></span>  
  
 <span data-ttu-id="82200-117">此外，通过右键单击设计图面，然后在菜单上单击“添加批注”  ，以添加批注。</span><span class="sxs-lookup"><span data-stu-id="82200-117">Additionally, to add annotations, right-click the design surface, and then on the menu, click **Add Annotation**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82200-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82200-118">See Also</span></span>  
 <span data-ttu-id="82200-119">[Integration Services (SSIS) 事件处理程序](integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="82200-119">[Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="82200-120">[控制流](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="82200-120">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="82200-121">[SSIS 设计器](ssis-designer.md) </span><span class="sxs-lookup"><span data-stu-id="82200-121">[SSIS Designer](ssis-designer.md) </span></span>  
 [<span data-ttu-id="82200-122">Integration Services (SSIS) 事件处理程序</span><span class="sxs-lookup"><span data-stu-id="82200-122">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
