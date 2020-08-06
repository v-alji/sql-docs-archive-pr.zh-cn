---
title: 对组件分组或取消分组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6811dffca41a12fe0afeeeb334e0107ac127c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578320"
---
# <a name="group-or-ungroup-components"></a><span data-ttu-id="12dbf-102">对组件分组或取消分组</span><span class="sxs-lookup"><span data-stu-id="12dbf-102">Group or Ungroup Components</span></span>
  <span data-ttu-id="12dbf-103">**设计器中的**“控制流” **、** “数据流” **和** “事件处理程序” [!INCLUDE[ssIS](../includes/ssis-md.md)] 选项卡支持可折叠的分组。</span><span class="sxs-lookup"><span data-stu-id="12dbf-103">The **Control Flow**, **Data Flow**, and **Event Handlers** tabs in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer supports collapsible grouping.</span></span> <span data-ttu-id="12dbf-104">如果包包含许多组件，这些选项卡可能变得很拥挤，使您很难一次查看所有组件并找到要使用的项。</span><span class="sxs-lookup"><span data-stu-id="12dbf-104">If a package has many components, the tabs can become crowded, making it difficult to view all the components at one time and to locate the item with which you want to work.</span></span> <span data-ttu-id="12dbf-105">可折叠的分组功能可节省工作图面空间，从而简化大型包的处理。</span><span class="sxs-lookup"><span data-stu-id="12dbf-105">The collapsible grouping feature can conserve space on the work surface and make it easier to work with large packages.</span></span>  
  
 <span data-ttu-id="12dbf-106">您可以选择要分组的组件，对其进行分组，然后根据工作需要展开或折叠这些组。</span><span class="sxs-lookup"><span data-stu-id="12dbf-106">You select the components that you want to group, group them, and then expand or collapse the groups to suit your work.</span></span> <span data-ttu-id="12dbf-107">将组展开后，将能够访问组中组件的属性。</span><span class="sxs-lookup"><span data-stu-id="12dbf-107">Expanding a group provides access to the properties of the components in the group.</span></span> <span data-ttu-id="12dbf-108">连接任务和容器的优先约束会自动包含在组中。</span><span class="sxs-lookup"><span data-stu-id="12dbf-108">The precedence constraints that connect tasks and containers are automatically included in the group.</span></span>  
  
 <span data-ttu-id="12dbf-109">以下是对组件进行分组需注意的事项。</span><span class="sxs-lookup"><span data-stu-id="12dbf-109">The following are considerations for grouping components.</span></span>  
  
-   <span data-ttu-id="12dbf-110">若要对组件分组，控制流、数据流或事件处理程序必须包含多个组件。</span><span class="sxs-lookup"><span data-stu-id="12dbf-110">To group components, the control flow, data flow, or event handler must contain more than one component.</span></span>  
  
-   <span data-ttu-id="12dbf-111">组还可以嵌套，因此可以在组内创建组。</span><span class="sxs-lookup"><span data-stu-id="12dbf-111">Groups can also be nested, making it possible to create groups within groups.</span></span> <span data-ttu-id="12dbf-112">设计图面可以实现多个非嵌套组，但除非组是嵌套的，否则组件只能属于一个组。</span><span class="sxs-lookup"><span data-stu-id="12dbf-112">The design surface can implement multiple un-nested groups, but a component can belong to only one group, unless the groups are nested.</span></span>  
  
-   <span data-ttu-id="12dbf-113">保存包时， [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器也保存分组，但是分组对包的执行没有影响。</span><span class="sxs-lookup"><span data-stu-id="12dbf-113">When a package is saved, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the grouping, but the grouping has no effect on package execution.</span></span> <span data-ttu-id="12dbf-114">对组件分组的能力是一项设计时功能；它不影响包的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="12dbf-114">The ability to group components is a design-time feature; it does not affect the run-time behavior of the package.</span></span>  
  
### <a name="to-group-components"></a><span data-ttu-id="12dbf-115">对组件分组</span><span class="sxs-lookup"><span data-stu-id="12dbf-115">To group components</span></span>  
  
1.  <span data-ttu-id="12dbf-116">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="12dbf-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="12dbf-117">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="12dbf-117">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="12dbf-118">单击 **“控制流”** 、 **“数据流”** 或 **“事件处理程序”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="12dbf-118">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="12dbf-119">在该选项卡的设计图面上，选择要分组的组件，右键单击所选组件，然后单击“分组”  。</span><span class="sxs-lookup"><span data-stu-id="12dbf-119">On the design surface of the tab, select the components you want to group, right-click a selected component, and then click **Group**.</span></span>  
  
5.  <span data-ttu-id="12dbf-120">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="12dbf-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-ungroup-components"></a><span data-ttu-id="12dbf-121">对组件取消分组</span><span class="sxs-lookup"><span data-stu-id="12dbf-121">To ungroup components</span></span>  
  
1.  <span data-ttu-id="12dbf-122">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="12dbf-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="12dbf-123">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="12dbf-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="12dbf-124">单击 **“控制流”** 、 **“数据流”** 或 **“事件处理程序”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="12dbf-124">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="12dbf-125">在该选项卡的设计图面上，选择要取消分组的组件所在的组，单击右键，然后单击“取消分组”  。</span><span class="sxs-lookup"><span data-stu-id="12dbf-125">On the design surface of the tab, select the group that contains the component you want to ungroup, right-click, and then click **Ungroup**.</span></span>  
  
5.  <span data-ttu-id="12dbf-126">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="12dbf-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dbf-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12dbf-127">See Also</span></span>  
 [<span data-ttu-id="12dbf-128">在控制流中添加或删除任务或容器</span><span class="sxs-lookup"><span data-stu-id="12dbf-128">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
     
 [<span data-ttu-id="12dbf-129">使用默认优先约束来连接任务和容器</span><span class="sxs-lookup"><span data-stu-id="12dbf-129">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)  
  
  
