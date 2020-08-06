---
title: 用于管理解决方案和项目的文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c94f1f853263c3969961de91ec95b921f5d78ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689698"
---
# <a name="files-that-manage-solutions-and-projects"></a><span data-ttu-id="531bf-102">用于管理解决方案和项目的文件</span><span class="sxs-lookup"><span data-stu-id="531bf-102">Files That Manage Solutions and Projects</span></span>
  <span data-ttu-id="531bf-103">本主题介绍了 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 专用文件类型。</span><span class="sxs-lookup"><span data-stu-id="531bf-103">This topic describes the file types that are specific to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="531bf-104">默认情况下，所有的解决方案及其项目均创建于 \My Documents\SQL Server Management Studio Projects 中。</span><span class="sxs-lookup"><span data-stu-id="531bf-104">By default, all solutions and their projects are created in \My Documents\SQL Server Management Studio Projects.</span></span>  
  
## <a name="management-studio-solution-files"></a><span data-ttu-id="531bf-105">Management Studio 解决方案文件</span><span class="sxs-lookup"><span data-stu-id="531bf-105">Management Studio Solution Files</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="531bf-106">使用的文件类型不同于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="531bf-106">uses different file types than [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="531bf-107">这意味着无法在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Visual Studio 中打开 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="531bf-107">This means you cannot open a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in Visual Studio.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="531bf-108">解决方案文件使解决方案资源管理器可以显示一个图形界面，以便管理文件。</span><span class="sxs-lookup"><span data-stu-id="531bf-108">solution files allow Solution Explorer to display a graphical interface for managing your files.</span></span>  
  
|<span data-ttu-id="531bf-109">分机</span><span class="sxs-lookup"><span data-stu-id="531bf-109">Extension</span></span>|<span data-ttu-id="531bf-110">文件类型</span><span class="sxs-lookup"><span data-stu-id="531bf-110">File type</span></span>|<span data-ttu-id="531bf-111">说明</span><span class="sxs-lookup"><span data-stu-id="531bf-111">Description</span></span>|<span data-ttu-id="531bf-112">创建者</span><span class="sxs-lookup"><span data-stu-id="531bf-112">Created by</span></span>|  
|---------------|---------------|-----------------|----------------|  
|<span data-ttu-id="531bf-113">.ssmssln</span><span class="sxs-lookup"><span data-stu-id="531bf-113">.ssmssln</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="531bf-114">解决方案对象</span><span class="sxs-lookup"><span data-stu-id="531bf-114">Solution Object</span></span>|<span data-ttu-id="531bf-115">为环境提供对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 项目、项目项和解决方案在磁盘上的位置的引用</span><span class="sxs-lookup"><span data-stu-id="531bf-115">Provides the environment with references to the location on disk of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] projects, project items, and solution</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a><span data-ttu-id="531bf-116">Management Studio 项目文件</span><span class="sxs-lookup"><span data-stu-id="531bf-116">Management Studio Project Files</span></span>  
 <span data-ttu-id="531bf-117">解决方案包含用于管理解决方案中对象的解决方案文件，同样，项目包含项目文件。</span><span class="sxs-lookup"><span data-stu-id="531bf-117">In the same way that solutions contain solution files that manage objects in a solution, projects contain project files.</span></span> <span data-ttu-id="531bf-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 为项目所创建的项目文件类型取决于创建项目时使用的模板。</span><span class="sxs-lookup"><span data-stu-id="531bf-118">The type of project file that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates for a project depends on the template used to create the project.</span></span> <span data-ttu-id="531bf-119">下表介绍了为每个项目所创建的文件类型。</span><span class="sxs-lookup"><span data-stu-id="531bf-119">The following table describes the type of file created for each project.</span></span>  
  
|<span data-ttu-id="531bf-120">分机</span><span class="sxs-lookup"><span data-stu-id="531bf-120">Extension</span></span>|<span data-ttu-id="531bf-121">项目模板</span><span class="sxs-lookup"><span data-stu-id="531bf-121">Project template</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="531bf-122">.ssmssqlproj</span><span class="sxs-lookup"><span data-stu-id="531bf-122">.ssmssqlproj</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="531bf-123">脚本项目</span><span class="sxs-lookup"><span data-stu-id="531bf-123">Scripts Project</span></span>|  
|<span data-ttu-id="531bf-124">.ssmsasproj</span><span class="sxs-lookup"><span data-stu-id="531bf-124">.ssmsasproj</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="531bf-125">脚本项目</span><span class="sxs-lookup"><span data-stu-id="531bf-125">Scripts Project</span></span>|  
  
## <a name="location-of-solution-level-files"></a><span data-ttu-id="531bf-126">解决方案级文件的位置</span><span class="sxs-lookup"><span data-stu-id="531bf-126">Location of Solution-Level Files</span></span>  
 <span data-ttu-id="531bf-127">默认情况下，解决方案级文件创建于使用该解决方案创建的第一个项目的物理目录中。</span><span class="sxs-lookup"><span data-stu-id="531bf-127">By default, solution-level files are created in the physical directory of the first project that is created with the solution.</span></span> <span data-ttu-id="531bf-128">可以通过创建解决方案指定解决方案的目录，也可以在创建新项目时指定该目录。</span><span class="sxs-lookup"><span data-stu-id="531bf-128">You can specify a directory for the solution by creating a solution, or you can specify the directory when you create a new project.</span></span>  
  
 <span data-ttu-id="531bf-129">如果目录结构与解决方案资源管理器中显示的逻辑结构相似，则更容易找到项目文件和解决方案文件并与工作组中的其他开发人员共享。</span><span class="sxs-lookup"><span data-stu-id="531bf-129">If you have a directory structure similar to the logical structure shown in Solution Explorer, project and solution files are easier to locate and share with other developers on a team.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531bf-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="531bf-130">See Also</span></span>  
 <span data-ttu-id="531bf-131">[用编码管理文件](manage-files-with-encoding.md) </span><span class="sxs-lookup"><span data-stu-id="531bf-131">[Manage Files with Encoding](manage-files-with-encoding.md) </span></span>  
 <span data-ttu-id="531bf-132">[杂项文件](miscellaneous-files.md) </span><span class="sxs-lookup"><span data-stu-id="531bf-132">[Miscellaneous Files](miscellaneous-files.md) </span></span>  
 <span data-ttu-id="531bf-133">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="531bf-133">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="531bf-134">[SQL Server Management Studio 的解决方案 &#40;&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="531bf-134">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="531bf-135">[项目 &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="531bf-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="531bf-136">解决方案资源管理器源代码管理</span><span class="sxs-lookup"><span data-stu-id="531bf-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
