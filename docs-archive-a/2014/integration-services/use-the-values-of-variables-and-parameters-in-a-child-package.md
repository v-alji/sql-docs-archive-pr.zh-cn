---
title: 在子包中使用变量和参数的值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- configurations [Integration Services]
- packages [Integration Services], configurations
- variables [Integration Services], adding
ms.assetid: 9b939edb-4e17-48e5-8428-855beb10049c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 28561db91e5e924d8b25f9c7be7a4a51c6c315ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588602"
---
# <a name="use-the-values-of-variables-and-parameters-in-a-child-package"></a><span data-ttu-id="25995-102">在子包中使用变量和参数的值</span><span class="sxs-lookup"><span data-stu-id="25995-102">Use the Values of Variables and Parameters in a Child Package</span></span>
  <span data-ttu-id="25995-103">此过程介绍如何创建使用父变量配置类型的包配置。</span><span class="sxs-lookup"><span data-stu-id="25995-103">This procedure describes how to create a package configuration that uses the parent variable configuration type.</span></span> <span data-ttu-id="25995-104">通过此配置类型，从父包运行的子包可以访问父包中的变量。</span><span class="sxs-lookup"><span data-stu-id="25995-104">This configuration type enables a child package that is run from a parent package to access a variable in the parent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25995-105">您还可以通过配置执行包任务将值传递给子包，以将父包变量或参数（或项目参数）映射到子包参数。</span><span class="sxs-lookup"><span data-stu-id="25995-105">You can also pass values to a child package by configuring the Execute Package Task to map parent package variables or parameters, or project parameters, to child package parameters.</span></span> <span data-ttu-id="25995-106">有关详细信息，请参阅 [Execute Package Task](control-flow/execute-package-task.md)。</span><span class="sxs-lookup"><span data-stu-id="25995-106">For more information, see [Execute Package Task](control-flow/execute-package-task.md).</span></span>  
  
 <span data-ttu-id="25995-107">在子包中创建包配置之前，不必在父包中创建变量。</span><span class="sxs-lookup"><span data-stu-id="25995-107">It is not necessary to create the variable in the parent package before you create the package configuration in the child package.</span></span> <span data-ttu-id="25995-108">可以随时在父包中添加变量，但必须在包配置中使用准确的父变量名称。</span><span class="sxs-lookup"><span data-stu-id="25995-108">You can add the variable to the parent package at any time, but you must use the exact name of the parent variable in the package configuration.</span></span> <span data-ttu-id="25995-109">但是，在配置可以更新的子包中必须有现成的变量，然后才能创建父变量配置。</span><span class="sxs-lookup"><span data-stu-id="25995-109">However, before you can create a parent variable configuration, there must be an existing variable in the child package that the configuration can update.</span></span> <span data-ttu-id="25995-110">有关添加和配置变量的详细信息，请参阅 [添加、删除、更改包中用户定义变量的作用域](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="25995-110">For more information about adding and configuring variables, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
 <span data-ttu-id="25995-111">父包中用于父变量配置的变量的作用域可以设置为“执行包”任务、包含任务的容器或包。</span><span class="sxs-lookup"><span data-stu-id="25995-111">The scope of the variable in the parent package that is used in a parent variable configuration can be set to the Execute Package task, to the container that has the task, or to the package.</span></span> <span data-ttu-id="25995-112">如果在包中定义了多个同名的变量，则使用在作用域中最接近“执行包”任务的变量。</span><span class="sxs-lookup"><span data-stu-id="25995-112">If multiple variables with the same name are defined in a package, the variable that is closest in scope to the Execute Package task is used.</span></span> <span data-ttu-id="25995-113">最接近“执行包”任务的作用域是该任务本身。</span><span class="sxs-lookup"><span data-stu-id="25995-113">The closest scope to the Execute Package task is the task itself.</span></span>  
  
### <a name="to-add-a-variable-to-a-parent-package"></a><span data-ttu-id="25995-114">向父包中添加变量</span><span class="sxs-lookup"><span data-stu-id="25995-114">To add a variable to a parent package</span></span>  
  
1.  <span data-ttu-id="25995-115">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含目标包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，所谓目标包是指您想将要传递给子包的变量添加到其中的包。</span><span class="sxs-lookup"><span data-stu-id="25995-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a variable to pass to a child package.</span></span>  
  
2.  <span data-ttu-id="25995-116">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="25995-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="25995-117">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，若要定义变量的作用域，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="25995-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="25995-118">若要设置包的范围，请单击 **“控制流”** 选项卡设计图面上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="25995-118">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="25995-119">若要将作用域设置为“执行包”任务的父容器，请单击该容器。</span><span class="sxs-lookup"><span data-stu-id="25995-119">To set the scope to a parent container of the Execute Package task, click the container.</span></span>  
  
    -   <span data-ttu-id="25995-120">若要将作用域设置为“执行包”任务，请单击该任务。</span><span class="sxs-lookup"><span data-stu-id="25995-120">To set the scope to the Execute Package task, click the task.</span></span>  
  
4.  <span data-ttu-id="25995-121">添加并配置变量。</span><span class="sxs-lookup"><span data-stu-id="25995-121">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25995-122">选择与变量将要存储的数据兼容的数据类型。</span><span class="sxs-lookup"><span data-stu-id="25995-122">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="25995-123">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="25995-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-variable-to-a-child-package"></a><span data-ttu-id="25995-124">向子包中添加变量</span><span class="sxs-lookup"><span data-stu-id="25995-124">To add a variable to a child package</span></span>  
  
1.  <span data-ttu-id="25995-125">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，有一个 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目应当包含您要向其中添加父变量配置的包，请将该项目打开。</span><span class="sxs-lookup"><span data-stu-id="25995-125">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a parent variable configuration.</span></span>  
  
2.  <span data-ttu-id="25995-126">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="25995-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="25995-127">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，若要设置包的作用域，请在 **“控制流”** 选项卡的设计图面上单击任何位置。</span><span class="sxs-lookup"><span data-stu-id="25995-127">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="25995-128">添加并配置变量。</span><span class="sxs-lookup"><span data-stu-id="25995-128">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25995-129">选择与变量将要存储的数据兼容的数据类型。</span><span class="sxs-lookup"><span data-stu-id="25995-129">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="25995-130">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="25995-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-parent-package-configuration-to-a-child-package"></a><span data-ttu-id="25995-131">向子包添加父包配置</span><span class="sxs-lookup"><span data-stu-id="25995-131">To add a parent package configuration to a child package</span></span>  
  
1.  <span data-ttu-id="25995-132">如果尚未打开它，请在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中打开子包。</span><span class="sxs-lookup"><span data-stu-id="25995-132">If it is not already open, open the child package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="25995-133">在 **“控制流”** 选项卡的设计图面上单击任何位置。</span><span class="sxs-lookup"><span data-stu-id="25995-133">Click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="25995-134">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="25995-134">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="25995-135">在 **“包配置组织程序”** 对话框中，选择 **“启用包配置”**，再单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="25995-135">In the **Package Configuration Organizer** dialog box, select **Enable package configuration**, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="25995-136">在包配置向导的 "欢迎" 页上，单击 "**下一步"。**</span><span class="sxs-lookup"><span data-stu-id="25995-136">On the welcome page of the Package Configuration Wizard, click **Next.**</span></span>  
  
6.  <span data-ttu-id="25995-137">在“选择配置类型”页上的 **“配置类型”** 列表中，选择 **“父包变量”** ，并执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="25995-137">On the Select Configuration Type page, in the **Configuration type** list, select **Parent package variable** and do one of the following:</span></span>  
  
    -   <span data-ttu-id="25995-138">选择 **“直接指定配置设置”**，然后在 **“父变量”** 框中提供要在配置中使用的父包中的变量的名称。</span><span class="sxs-lookup"><span data-stu-id="25995-138">Select **Specify configuration settings directly**, and then in the **Parent variable** box, provide the name of the variable in the parent package to use in the configuration.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="25995-139">变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="25995-139">Variable names are case sensitive.</span></span>  
  
    -   <span data-ttu-id="25995-140">选择“配置位置存储在一个环境变量中”\*\*\*\*，然后在“环境变量列表”\*\*\*\* 中选择包含变量名称的环境变量。</span><span class="sxs-lookup"><span data-stu-id="25995-140">Select or **Configuration location is stored in an environment variable,** and then in the **Environment variable list**, select the environmentvariable that contains the name of the variable.</span></span>  
  
7.  <span data-ttu-id="25995-141">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="25995-141">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="25995-142">在“选择目标属性”页上，展开 **“变量”** 节点，并展开要配置的变量的 **“属性”** 节点，然后单击要由配置设置的属性。</span><span class="sxs-lookup"><span data-stu-id="25995-142">On the Select Target Property page, expand the **Variable** node, and expand the **Properties** node of the variable to configure, and then click the property to be set by the configuration.</span></span>  
  
9. <span data-ttu-id="25995-143">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="25995-143">Click **Next**.</span></span>  
  
10. <span data-ttu-id="25995-144">（可选）在“完成向导”页上，修改配置的默认名称，并检查配置信息。</span><span class="sxs-lookup"><span data-stu-id="25995-144">On the Completing the Wizard page, optionally, modify the default name of the configuration and review the configuration information.</span></span>  
  
11. <span data-ttu-id="25995-145">单击 **“完成”** 以完成向导并返回 **“包配置组织程序”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="25995-145">Click **Finish** to complete the wizard and return to the **Package Configuration Organizer** dialog box.</span></span>  
  
12. <span data-ttu-id="25995-146">在 **“包配置组织程序”** 对话框中， **“配置”** 框将列出新配置。</span><span class="sxs-lookup"><span data-stu-id="25995-146">In the **Package Configuration Organizer** dialog box, the **Configuration** box lists the new configuration.</span></span>  
  
13. <span data-ttu-id="25995-147">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="25995-147">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25995-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25995-148">See Also</span></span>  
 <span data-ttu-id="25995-149">[包配置](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="25995-149">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="25995-150">[创建包配置](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="25995-150">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="25995-151">[Integration Services (SSIS) 变量](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="25995-151">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="25995-152">使用包中的变量</span><span class="sxs-lookup"><span data-stu-id="25995-152">Use Variables in Packages</span></span>](../../2014/integration-services/use-variables-in-packages.md)  
  
  
