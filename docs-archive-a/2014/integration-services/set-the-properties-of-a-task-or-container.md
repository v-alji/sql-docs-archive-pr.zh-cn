---
title: 设置任务或容器的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], properties
ms.assetid: 52d47ca4-fb8c-493d-8b2b-48bb269f859b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0a4c556b94af02c2f874f2740a70b1294c35e653
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694024"
---
# <a name="set-the-properties-of-a-task-or-container"></a><span data-ttu-id="f6b5a-102">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="f6b5a-102">Set the Properties of a Task or Container</span></span>
  <span data-ttu-id="f6b5a-103">可以使用 **“属性”** 窗口设置任务和容器的大多数属性。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-103">You can set most properties of tasks and containers by using the **Properties** window.</span></span> <span data-ttu-id="f6b5a-104">但任务集合的属性以及因过于复杂而无法使用 **“属性”** 窗口设置的属性不在此列。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-104">The exceptions are properties of task collections and properties that are too complex to set by using the **Properties** window.</span></span> <span data-ttu-id="f6b5a-105">例如，不能在 **“属性”** 窗口中配置 Foreach 循环容器使用的枚举器。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-105">For example, you cannot configure the enumerator that the Foreach Loop container uses in the **Properties** window.</span></span> <span data-ttu-id="f6b5a-106">您必须使用任务或容器编辑器来设置这些复杂的属性。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-106">You must use a task or container editor to set these complex properties.</span></span> <span data-ttu-id="f6b5a-107">大多数任务和容器编辑器都有多个节点，而每个节点都包含相关属性。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-107">Most task and container editors have multiple nodes and each node contains related properties.</span></span> <span data-ttu-id="f6b5a-108">节点的名称指出了节点所包含属性的主题。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-108">The name of the node indicates the subject of the properties that the node contains.</span></span>  
  
 <span data-ttu-id="f6b5a-109">下面的过程介绍如何使用 **“属性”** 窗口或者任务或容器编辑器来设置相应任务或容器的属性。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-109">The following procedures describe how to set the properties of a task or container by using either the **Properties** windows, or the corresponding task or container editor.</span></span>  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-the-properties-window"></a><span data-ttu-id="f6b5a-110">使用“属性”窗口设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="f6b5a-110">To set the properties of a task or container by using the Properties window</span></span>  
  
1.  <span data-ttu-id="f6b5a-111">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f6b5a-112">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-112">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f6b5a-113">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-113">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="f6b5a-114">在“控制流”选项卡的设计图面上，右键单击任务或容器，然后单击“属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-114">On the design surface of the **Control Flow** tab, right-click the task or container, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="f6b5a-115">在 **“属性”** 窗口中，更新属性值。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-115">In the **Properties** window, update the property value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f6b5a-116">大部分属性可以通过直接在文本框中键入值或者从列表中选择值的方式进行设置。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-116">Most properties can be set by typing a value directly in the text box, or by selecting a value from a list.</span></span> <span data-ttu-id="f6b5a-117">但是，某些属性比较复杂，并且具有自定义的属性编辑器。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-117">However, some properties are more complex and have a custom property editor.</span></span> <span data-ttu-id="f6b5a-118">若要设置属性，请在文本框中单击，然后单击生成按钮 (…) 打开自定义编辑器\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-118">To set the property, click in the text box, and then click the build **(...)** button to open the custom editor.</span></span>  
  
6.  <span data-ttu-id="f6b5a-119">也可以创建属性表达式来动态更新任务或容器的属性。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-119">Optionally, create property expressions to dynamically update the properties of the task or container.</span></span> <span data-ttu-id="f6b5a-120">有关详细信息，请参阅 [添加或更改属性表达式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-120">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="f6b5a-121">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-a-task-or-container-editor"></a><span data-ttu-id="f6b5a-122">使用任务或容器编辑器设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="f6b5a-122">To set the properties of a task or container by using a task or container editor</span></span>  
  
1.  <span data-ttu-id="f6b5a-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f6b5a-124">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-124">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f6b5a-125">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-125">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="f6b5a-126">在“控制流”选项卡的设计图面上，右键单击任务或容器，然后单击“编辑”以打开相应的任务或容器编辑器\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-126">On the design surface of the **Control Flow** tab, right-click the task or container, and then click **Edit** to open the corresponding task or container editor.</span></span>  
  
     <span data-ttu-id="f6b5a-127">有关如何配置 For 循环容器的信息，请参阅[配置 For 循环容器](control-flow/for-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-127">For information about how to configure the For Loop container, see [Configure a For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
     <span data-ttu-id="f6b5a-128">有关如何配置 Foreach 循环容器的信息，请参阅 [配置 Foreach 循环容器](control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-128">For information about how to configure the Foreach Loop container, see [Configure a Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f6b5a-129">序列容器没有自定义编辑器。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-129">The Sequence container has no custom editor.</span></span>  
  
5.  <span data-ttu-id="f6b5a-130">如果任务或容器编辑器具有多个节点，单击包含要设置的属性的节点。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-130">If the task or container editor has multiple nodes, click the node that contains the property that you want to set.</span></span>  
  
6.  <span data-ttu-id="f6b5a-131">根据需要，也可以单击 **“表达式”** ，并在 **“表达式”** 页上创建属性表达式，以动态更新任务或容器的属性。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-131">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions to dynamically update the properties of the task or container.</span></span> <span data-ttu-id="f6b5a-132">有关详细信息，请参阅 [添加或更改属性表达式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-132">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="f6b5a-133">更新属性值。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-133">Update the property value.</span></span>  
  
8.  <span data-ttu-id="f6b5a-134">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="f6b5a-134">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b5a-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6b5a-135">See Also</span></span>  
 <span data-ttu-id="f6b5a-136">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="f6b5a-136">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="f6b5a-137">Integration Services 容器</span><span class="sxs-lookup"><span data-stu-id="f6b5a-137">Integration Services Containers</span></span>](control-flow/integration-services-containers.md)  
  
  
