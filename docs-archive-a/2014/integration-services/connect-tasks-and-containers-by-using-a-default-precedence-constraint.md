---
title: 使用默认优先约束来连接任务和容器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 00207172babdb41b1030e77e71a2c8bc3b99799d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692483"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a><span data-ttu-id="4ddde-102">使用默认优先约束来连接任务和容器</span><span class="sxs-lookup"><span data-stu-id="4ddde-102">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>
  <span data-ttu-id="4ddde-103">优先约束连接两个可执行文件。</span><span class="sxs-lookup"><span data-stu-id="4ddde-103">Precedence constraints connect two executables.</span></span> <span data-ttu-id="4ddde-104">可执行文件可以是任何任务，也可以是 For 循环容器、Foreach 循环容器或序列容器。</span><span class="sxs-lookup"><span data-stu-id="4ddde-104">An executable can be any task or a For Loop, Foreach Loop, or Sequence container.</span></span> <span data-ttu-id="4ddde-105">此过程介绍如何设置优先约束的默认行为，以及如何用默认优先约束来连接可执行文件。</span><span class="sxs-lookup"><span data-stu-id="4ddde-105">This procedure describes how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints.</span></span>  
  
## <a name="creating-default-precedence-constraints"></a><span data-ttu-id="4ddde-106">创建默认优先约束</span><span class="sxs-lookup"><span data-stu-id="4ddde-106">Creating Default Precedence Constraints</span></span>  
 <span data-ttu-id="4ddde-107">首次使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器时，优先约束的默认值为 `Success`。</span><span class="sxs-lookup"><span data-stu-id="4ddde-107">When you first use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the default value of a precedence constraint is `Success`.</span></span> <span data-ttu-id="4ddde-108">按照下列步骤将 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器配置为使用不同的优先约束默认值。</span><span class="sxs-lookup"><span data-stu-id="4ddde-108">Follow these steps to configure [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to use a different default value for precedence constraints.</span></span>  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a><span data-ttu-id="4ddde-109">设置优先约束的默认值</span><span class="sxs-lookup"><span data-stu-id="4ddde-109">To set the default value for precedence constraints</span></span>  
  
1.  <span data-ttu-id="4ddde-110">打开 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4ddde-110">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4ddde-111">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="4ddde-111">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="4ddde-112">在 **“选项”** 对话框中，展开 **“商业智能设计器”** ，再展开 **“Integration Services 设计器”**。</span><span class="sxs-lookup"><span data-stu-id="4ddde-112">In the **Options** dialog box, expand **Business Intelligence Designers,** and then expand **Integration Services Designers**.</span></span>  
  
4.  <span data-ttu-id="4ddde-113">单击 **“控制流自动连接”** ，并选择 **“将新形状连接到默认选中的形状”**。</span><span class="sxs-lookup"><span data-stu-id="4ddde-113">Click **Control Flow Auto Connect** and select **Connect a new shape to the selected shape by default**.</span></span>  
  
5.  <span data-ttu-id="4ddde-114">在下拉列表中，选择“对新形状使用‘失败’约束”或“对新形状使用‘完成’约束”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4ddde-114">In the drop-down list, choose either **Use a Failure constraint for the new shape** or **Use a Completion constraint for the new shape**.</span></span>  
  
6.  <span data-ttu-id="4ddde-115">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="4ddde-115">Click **OK**.</span></span>  
  
#### <a name="to-create-a-default-precedence-constraint"></a><span data-ttu-id="4ddde-116">创建默认优先约束</span><span class="sxs-lookup"><span data-stu-id="4ddde-116">To create a default precedence constraint</span></span>  
  
1.  <span data-ttu-id="4ddde-117">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="4ddde-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="4ddde-118">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="4ddde-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4ddde-119">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4ddde-119">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="4ddde-120">在 **“控制流”** 选项卡的设计图面上，单击任务或容器，并将其连接线拖动到要将优先约束应用到其上的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="4ddde-120">On the design surface of the **Control Flow** tab, click the task or container and drag its connector to the executable to which you want the precedence constraint to apply.</span></span>  
  
5.  <span data-ttu-id="4ddde-121">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="4ddde-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddde-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ddde-122">See Also</span></span>  
 <span data-ttu-id="4ddde-123">[优先约束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="4ddde-123">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="4ddde-124">[使用快捷菜单设置优先约束的值](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="4ddde-124">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="4ddde-125">[设置优先约束的属性](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="4ddde-125">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="4ddde-126">在优先约束中使用表达式</span><span class="sxs-lookup"><span data-stu-id="4ddde-126">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
