---
title: Integration Services 项目的开发 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 6e90b016-36a5-415e-9440-a20199fffff0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da648b3b09b25fa2a7b1cf886ad1bf770296f5ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590304"
---
# <a name="development-of-an-integration-services-project"></a><span data-ttu-id="cea99-102">Integration Services 项目的开发</span><span class="sxs-lookup"><span data-stu-id="cea99-102">Development of an Integration Services Project</span></span>
  <span data-ttu-id="cea99-103">您将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包添加到项目。</span><span class="sxs-lookup"><span data-stu-id="cea99-103">You add [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to projects.</span></span> <span data-ttu-id="cea99-104">若要创建和使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，必须安装 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 环境。</span><span class="sxs-lookup"><span data-stu-id="cea99-104">To create and work with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, you must install the [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] environment.</span></span> <span data-ttu-id="cea99-105">有关详细信息，请参阅 [安装 Integration Services](install-windows/install-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cea99-105">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
 <span data-ttu-id="cea99-106">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中创建新的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]项目时， **“新建项目”** 对话框包含一个 **“Integration Services 项目”** 模板。</span><span class="sxs-lookup"><span data-stu-id="cea99-106">When you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the **New Project** dialog box includes an **Integration Services Project** template.</span></span> <span data-ttu-id="cea99-107">此项目模板创建包含一个包的新项目。</span><span class="sxs-lookup"><span data-stu-id="cea99-107">This project template creates a new project that contains a single package.</span></span>  
  
## <a name="projects-and-solutions"></a><span data-ttu-id="cea99-108">项目和解决方案</span><span class="sxs-lookup"><span data-stu-id="cea99-108">Projects and Solutions</span></span>  
 <span data-ttu-id="cea99-109">项目存储在解决方案中。</span><span class="sxs-lookup"><span data-stu-id="cea99-109">Projects are stored in solutions.</span></span> <span data-ttu-id="cea99-110">可以先创建解决方案，然后向该解决方案添加 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="cea99-110">You can create a solution first and then add an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the solution.</span></span> <span data-ttu-id="cea99-111">如果不存在解决方案， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 将在您首次创建项目时自动创建解决方案。</span><span class="sxs-lookup"><span data-stu-id="cea99-111">If no solution exists, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates one for you when you first create the project.</span></span> <span data-ttu-id="cea99-112">解决方案可以包含多个不同类型的项目。</span><span class="sxs-lookup"><span data-stu-id="cea99-112">A solution can contain multiple projects of different types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea99-113">默认情况下，在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中创建新的 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]项目时， **“解决方案资源管理器”** 窗格不会显示该解决方案。</span><span class="sxs-lookup"><span data-stu-id="cea99-113">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the solution is not shown in the **Solution Explorer** pane.</span></span> <span data-ttu-id="cea99-114">若要更改此默认行为，请在 **“工具”** 菜单上单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="cea99-114">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="cea99-115">在 **“选项”** 对话框中，展开 **“项目和解决方案”**，然后单击 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="cea99-115">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="cea99-116">在 **“常规”** 页上，选择 **“总是显示解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="cea99-116">On the **General** page, select **Always show solution**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="cea99-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cea99-117">Related Tasks</span></span>  
  
-   [<span data-ttu-id="cea99-118">创建新的 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="cea99-118">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="cea99-119">向 Integration Services 项目添加项</span><span class="sxs-lookup"><span data-stu-id="cea99-119">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)  
  
-   [<span data-ttu-id="cea99-120">在解决方案中添加或删除 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="cea99-120">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
