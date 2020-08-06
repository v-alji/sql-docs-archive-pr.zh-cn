---
title: 添加、删除、更改包中用户定义变量的作用域 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], adding
ms.assetid: cbf40c7f-3c8a-48cd-aefa-8b37faf8b40e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7e5980fc7f730c69ef886e4e80760cfbdc9e4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585951"
---
# <a name="add-delete-change-scope-of-user-defined-variable-in-a-package"></a><span data-ttu-id="cd5f2-102">添加、删除、更改包中用户定义变量的作用域</span><span class="sxs-lookup"><span data-stu-id="cd5f2-102">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>
  <span data-ttu-id="cd5f2-103">这些过程介绍如何使用“变量”窗口来添加、删除和更改包中用户定义变量的作用域。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="cd5f2-103">These procedures describe how to add, delete, and change the scope of a user-defined variable in a package by using the **Variables** window.</span></span>  
  
 <span data-ttu-id="cd5f2-104">有关变量作用域的详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)区域之下。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-104">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="cd5f2-105">还提供了可在运行时提供系统信息的系统变量，这些系统变量可在包和事件处理程序等容器中使用。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-105">also provides system variables that make system information available at run time and can be used in containers such as packages and event handlers.</span></span> <span data-ttu-id="cd5f2-106">您无法删除系统变量。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-106">You cannot delete system variables.</span></span>  
  
### <a name="to-add-a-variable"></a><span data-ttu-id="cd5f2-107">添加变量</span><span class="sxs-lookup"><span data-stu-id="cd5f2-107">To add a variable</span></span>  
  
1.  <span data-ttu-id="cd5f2-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要使用的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="cd5f2-109">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-109">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cd5f2-110">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，若要定义变量的作用域，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="cd5f2-110">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="cd5f2-111">若要设置包的范围，请单击 **“控制流”** 选项卡设计图面上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-111">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="cd5f2-112">若要设置事件处理程序的作用域，请在 **“事件处理程序”** 选项卡的设计图面上，选择一个可执行文件和一个事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-112">To set the scope to an event handler, select an executable and an event handler on the design surface of the **Event Handler** tab.</span></span>  
  
    -   <span data-ttu-id="cd5f2-113">若要设置任务或容器的范围，请在 **“控制流”** 选项卡或 **“事件处理程序”** 选项卡的设计图面上，单击一个任务或容器。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-113">To set the scope to a task or container, on the design surface of the **Control Flow** tab or the **Event Handler** tab, click a task or container.</span></span>  
  
4.  <span data-ttu-id="cd5f2-114">在 **SSIS** 菜单上单击 **“变量”** 。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-114">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="cd5f2-115">您可以通过将 View.Variables 命令映射到在 **“选项”** 对话框的 **“键盘”** 页上选择的组合键来显示 **“变量”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-115">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
5.  <span data-ttu-id="cd5f2-116">在 **“变量”** 窗口中，单击 **“添加变量”** 图标。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-116">In the **Variables** window, click the **Add Variable** icon.</span></span> <span data-ttu-id="cd5f2-117">新的变量将添加到该列表中。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-117">The new variable is added to the list.</span></span>  
  
6.  <span data-ttu-id="cd5f2-118">也可以单击 **“网格选项”** 图标，选择要在 **“变量网格选项”** 对话框中显示的其他列，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-118">Optionally, click the **Grid Options** icon, select additional columns to show in the **Variables Grid Options** dialog box, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="cd5f2-119">或者，设置变量属性。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-119">Optionally, set the variable properties.</span></span> <span data-ttu-id="cd5f2-120">有关详细信息，请参阅 [设置用户定义变量的属性](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)定义。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-120">For more information, see [Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md).</span></span>  
  
8.  <span data-ttu-id="cd5f2-121">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-variable"></a><span data-ttu-id="cd5f2-122">删除变量</span><span class="sxs-lookup"><span data-stu-id="cd5f2-122">To delete a variable</span></span>  
  
1.  <span data-ttu-id="cd5f2-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="cd5f2-124">在解决方案资源管理器中，右键单击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-124">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cd5f2-125">在 **SSIS** 菜单上单击 **“变量”** 。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-125">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="cd5f2-126">您可以通过将 View.Variables 命令映射到在 **“选项”** 对话框的 **“键盘”** 页上选择的组合键来显示 **“变量”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-126">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="cd5f2-127">选择要删除的变量，然后单击 **“删除变量”**。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-127">Select the variable to delete, and then click **Delete Variable**.</span></span>  
  
     <span data-ttu-id="cd5f2-128">如果在 "变量" 窗口中没有看到该变量，请单击 "**网格选项**"，然后选择 "**显示所有作用域的变量**"。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-128">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="cd5f2-129">如果 **“确认删除变量”** 对话框打开，请单击 **“是”** 确认删除。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-129">If the **Confirm Deletion of Variables** dialog box opens, click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="cd5f2-130">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-change-the-scope-of-a-variable"></a><span data-ttu-id="cd5f2-131">更改变量的作用域</span><span class="sxs-lookup"><span data-stu-id="cd5f2-131">To change the scope of a variable</span></span>  
  
1.  <span data-ttu-id="cd5f2-132">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-132">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="cd5f2-133">在解决方案资源管理器中，右键单击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-133">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cd5f2-134">在 **SSIS** 菜单上单击 **“变量”** 。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-134">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="cd5f2-135">您可以通过将 View.Variables 命令映射到在 **“选项”** 对话框的 **“键盘”** 页上选择的组合键来显示 **“变量”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-135">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="cd5f2-136">选择该变量，然后单击 **“移动变量”**。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-136">Select the variable and then click **Move Variable**.</span></span>  
  
     <span data-ttu-id="cd5f2-137">如果在 "变量" 窗口中没有看到该变量，请单击 "**网格选项**"，然后选择 "**显示所有作用域的变量**"。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-137">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="cd5f2-138">在 **“选择新作用域”** 对话框中，选择包或包中的容器、任务或事件处理程序，以更改变量作用域。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-138">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
6.  <span data-ttu-id="cd5f2-139">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="cd5f2-139">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd5f2-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd5f2-140">See Also</span></span>  
 <span data-ttu-id="cd5f2-141">[Integration Services (SSIS) 变量](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="cd5f2-141">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="cd5f2-142">[使用包中的变量](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="cd5f2-142">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="cd5f2-143">[设置用户定义变量的属性](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span><span class="sxs-lookup"><span data-stu-id="cd5f2-143">[Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span></span>  
 [<span data-ttu-id="cd5f2-144">在子包中使用变量和参数的值</span><span class="sxs-lookup"><span data-stu-id="cd5f2-144">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
  
