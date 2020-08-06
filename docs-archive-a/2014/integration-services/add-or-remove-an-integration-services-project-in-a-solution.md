---
title: 在解决方案中添加或删除 Integration Services 项目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49984c61047a6b716015bd72e518b73cb08b3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576951"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a><span data-ttu-id="14ffc-102">在解决方案中添加或删除 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="14ffc-102">Add or Remove an Integration Services Project in a Solution</span></span>
  <span data-ttu-id="14ffc-103">下列过程介绍如何在解决方案中添加或删除 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-103">The following procedures descibe how to add or remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution.</span></span>  
  
 <span data-ttu-id="14ffc-104">仅当解决方案在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中可见时，才能向现有解决方案中添加项目或从解决方案中删除项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-104">You can only add a project to an existing solution, or remove a project from a solution, when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="14ffc-105">如果在中选择了 "**始终显示解决方案**" 选项 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 则即使该解决方案只包含一个项目，也会显示该解决方案。</span><span class="sxs-lookup"><span data-stu-id="14ffc-105">If you have selected the **Always show solution** option in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution even when that solution contains only one project.</span></span> <span data-ttu-id="14ffc-106">否则， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 将只显示包含多个项目的解决方案。</span><span class="sxs-lookup"><span data-stu-id="14ffc-106">Otherwise, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution only when that solution contains more than one project.</span></span> <span data-ttu-id="14ffc-107">其他项目可以是 [!INCLUDE[ssIS](../includes/ssis-md.md)] 项目或其他类型的项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-107">The additional projects can be either [!INCLUDE[ssIS](../includes/ssis-md.md)] projects or projects of other types.</span></span>  
  
## <a name="adding-an-integration-services-project"></a><span data-ttu-id="14ffc-108">添加 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="14ffc-108">Adding an Integration Services Project</span></span>  
 <span data-ttu-id="14ffc-109">在添加项目时，可以让 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 创建新的空白项目，或者你可以添加已为其他解决方案创建的项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-109">When you add a project, you can have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] create a new, blank project, or you can add a project that you have already created for a different solution.</span></span> <span data-ttu-id="14ffc-110">仅当现有解决方案在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中可见时，才能向该解决方案中添加项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-110">You can only add a project to an existing solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a><span data-ttu-id="14ffc-111">将新 Integration Services 项目添加到解决方案</span><span class="sxs-lookup"><span data-stu-id="14ffc-111">To add a new Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="14ffc-112">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要添加新 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的解决方案，然后进行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="14ffc-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="14ffc-113">右键单击该解决方案，单击“添加”，再单击“新建项目”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="14ffc-113">Right-click the solution, click **Add**, and then click **New Project**.</span></span>  
  
    -   <span data-ttu-id="14ffc-114">在 **“文件”** 菜单上，指向 **“添加”**，再单击 **“新建项目”**。</span><span class="sxs-lookup"><span data-stu-id="14ffc-114">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="14ffc-115">在 **“添加新项目”** 对话框中，单击 **“模板”** 窗格中的 **“Integration Services 项目”** 。</span><span class="sxs-lookup"><span data-stu-id="14ffc-115">In the **Add New Project** dialog box, click **Integration Services Project** in the **Templates** pane.</span></span>  
  
3.  <span data-ttu-id="14ffc-116">或者，编辑项目的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="14ffc-116">Optionally, edit the project name and location.</span></span>  
  
4.  <span data-ttu-id="14ffc-117">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="14ffc-117">Click **OK**.</span></span>  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a><span data-ttu-id="14ffc-118">将现有 Integration Services 项目添加到解决方案中</span><span class="sxs-lookup"><span data-stu-id="14ffc-118">To add an existing Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="14ffc-119">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中打开要把现有 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目添加到其中的解决方案，并且执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="14ffc-119">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="14ffc-120">右键单击该解决方案，指向“添加”，然后单击“现有项目”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="14ffc-120">Right-click the solution, point to **Add**, and then click **Existing Project**.</span></span>  
  
    -   <span data-ttu-id="14ffc-121">在 **“文件”** 菜单上，单击 **“添加”**，然后单击 **“现有项目”**。</span><span class="sxs-lookup"><span data-stu-id="14ffc-121">On the **File** menu, click **Add**, and then click **Existing Project**.</span></span>  
  
2.  <span data-ttu-id="14ffc-122">在 **“添加现有项目”** 对话框中，浏览并找到要添加的项目，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="14ffc-122">In the **Add Existing Project** dialog box, browse to locate the project you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="14ffc-123">此项目即添加到 **解决方案资源管理器**中的解决方案文件夹中。</span><span class="sxs-lookup"><span data-stu-id="14ffc-123">The project is added to the solution folder in **Solution Explorer**.</span></span>  
  
## <a name="removing-an-integration-services-project"></a><span data-ttu-id="14ffc-124">删除 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="14ffc-124">Removing an Integration Services Project</span></span>  
 <span data-ttu-id="14ffc-125">仅当解决方案在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中可见时，才能从解决方案中删除项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-125">You can only remove a project from a solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="14ffc-126">解决方案可见后，则可以保留一个项目而删除其余所有项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-126">After the solution is visible, you can remove all except one project.</span></span> <span data-ttu-id="14ffc-127">只要仅剩余一个项目， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 就不再显示解决方案文件夹，并且您无法删除最后一个项目。</span><span class="sxs-lookup"><span data-stu-id="14ffc-127">As soon as only one project remains, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] no longer displays the solution folder and you cannot remove the last project.</span></span>  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a><span data-ttu-id="14ffc-128">从解决方案中删除 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="14ffc-128">To remove an Integration Services project from a solution</span></span>  
  
1.  <span data-ttu-id="14ffc-129">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要删除 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的解决方案。</span><span class="sxs-lookup"><span data-stu-id="14ffc-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution from which you want to remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="14ffc-130">在解决方案资源管理器中，右键单击该项目，然后单击“卸载项目”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="14ffc-130">In Solution Explorer, right-click the project, and then click **Unload Project**.</span></span>  
  
3.  <span data-ttu-id="14ffc-131">单击“确定”以确认删除。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="14ffc-131">Click **OK** to confirm the removal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ffc-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14ffc-132">See Also</span></span>  
 <span data-ttu-id="14ffc-133">[Integration Services &#40;SSIS&#41; 项目](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="14ffc-133">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="14ffc-134">创建新的 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="14ffc-134">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
