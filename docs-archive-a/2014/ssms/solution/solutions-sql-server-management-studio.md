---
title: 解决方案 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- solutions [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d06a8a05-7201-4055-8cf3-21bcb4e82c25
author: stevestein
ms.author: sstein
ms.openlocfilehash: 836d3b3002d72541ad88ae55eac6d951530e0ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580500"
---
# <a name="solutions-sql-server-management-studio"></a><span data-ttu-id="ab3c2-102">解决方案 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ab3c2-102">Solutions (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ab3c2-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 解决方案是一个或多个相关项目的集合。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-103">A [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution is a collection of one or more related projects.</span></span> <span data-ttu-id="ab3c2-104">项目是开发人员用来组织相关文件（例如常用管理脚本集）的容器。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-104">Projects are containers that developers use to organize related files, such as sets of commonly used administration scripts.</span></span>  
  
## <a name="solution-overview"></a><span data-ttu-id="ab3c2-105">解决方案概述</span><span class="sxs-lookup"><span data-stu-id="ab3c2-105">Solution Overview</span></span>  
 <span data-ttu-id="ab3c2-106">可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 作为 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的脚本开发平台。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-106">You can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] as a script development platform for [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ab3c2-107">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 代码编辑器可为关系数据库和多维数据库开发脚本和查询，以及一起收集项目中的相关脚本和查询。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-107">Use the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] code editors to develop scripts and queries for relational and multidimensional databases, and collect related scripts and queries together in projects.</span></span>  
  
 <span data-ttu-id="ab3c2-108">项目可以包含：</span><span class="sxs-lookup"><span data-stu-id="ab3c2-108">Projects can contain:</span></span>  
  
-   <span data-ttu-id="ab3c2-109">实现生产过程的查询和脚本。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-109">Queries and scripts that implement production processes.</span></span>  
  
-   <span data-ttu-id="ab3c2-110">查询和脚本使用的连接信息和文件。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-110">Connection information and files used by the queries and scripts.</span></span>  
  
 <span data-ttu-id="ab3c2-111">可以将一个或多个相关项目合并到一个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-111">One or more related projects can be combined in a solution.</span></span> <span data-ttu-id="ab3c2-112">通过使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的“解决方案资源管理器”窗格，可以管理解决方案和项目。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-112">Solutions and projects can be managed by using the Solution Explorer pane in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="ab3c2-113">可以将解决方案和项目集成到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe (VSS) 数据库或其他第三方源代码管理提供程序中，以进行开发更改跟踪和生命周期管理。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-113">Solutions and projects can be integrated into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe (VSS) database or other third-party source control providers, for development change tracking and life-cycle management.</span></span>  
  
## <a name="solution-tasks"></a><span data-ttu-id="ab3c2-114">解决方案任务</span><span class="sxs-lookup"><span data-stu-id="ab3c2-114">Solution Tasks</span></span>  
  
|<span data-ttu-id="ab3c2-115">任务说明</span><span class="sxs-lookup"><span data-stu-id="ab3c2-115">Task Description</span></span>|<span data-ttu-id="ab3c2-116">主题</span><span class="sxs-lookup"><span data-stu-id="ab3c2-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ab3c2-117">介绍如何创建一个新的解决方案，然后使用该解决方案来包含一个或多个项目。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-117">Describes how to create a new solution that can then be used to contain one or more projects.</span></span>|[<span data-ttu-id="ab3c2-118">新建解决方案</span><span class="sxs-lookup"><span data-stu-id="ab3c2-118">Create a New Solution</span></span>](create-a-new-solution.md)|  
|<span data-ttu-id="ab3c2-119">介绍如何在解决方案资源管理器中打开现有解决方案。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-119">Describes how to open an existing solution in Solution Explorer.</span></span>|[<span data-ttu-id="ab3c2-120">打开现有解决方案</span><span class="sxs-lookup"><span data-stu-id="ab3c2-120">Open an Existing Solution</span></span>](open-an-existing-solution.md)|  
|<span data-ttu-id="ab3c2-121">介绍如何关闭解决方案。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-121">Describes how to close a solution.</span></span>|[<span data-ttu-id="ab3c2-122">关闭解决方案</span><span class="sxs-lookup"><span data-stu-id="ab3c2-122">Close a Solution</span></span>](close-a-solution.md)|  
|<span data-ttu-id="ab3c2-123">介绍如何删除解决方案。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-123">Describes how to delete a solution.</span></span>|[<span data-ttu-id="ab3c2-124">删除解决方案</span><span class="sxs-lookup"><span data-stu-id="ab3c2-124">Delete a Solution</span></span>](delete-a-solution.md)|  
|<span data-ttu-id="ab3c2-125">介绍如何在项目之间复制项。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-125">Describes how to copy items between projects.</span></span>|[<span data-ttu-id="ab3c2-126">复制解决方案中的项</span><span class="sxs-lookup"><span data-stu-id="ab3c2-126">Copy Items in a Solution</span></span>](copy-items-in-a-solution.md)|  
|<span data-ttu-id="ab3c2-127">介绍如何删除项目中的项，或者删除整个项目。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-127">Describes how to delete items in a project, or an entire project.</span></span>|[<span data-ttu-id="ab3c2-128">移除或删除项或项目</span><span class="sxs-lookup"><span data-stu-id="ab3c2-128">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)|  
|<span data-ttu-id="ab3c2-129">介绍如何在解决方案中的各项目之间移动项。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-129">Describes how to move items between projects in a solution.</span></span>|[<span data-ttu-id="ab3c2-130">在解决方案中移动项</span><span class="sxs-lookup"><span data-stu-id="ab3c2-130">Move Items in a Solution</span></span>](move-items-in-a-solution.md)|  
|<span data-ttu-id="ab3c2-131">介绍如何重命名解决方案或解决方案中的项。</span><span class="sxs-lookup"><span data-stu-id="ab3c2-131">Describes how to rename a solution or the items in the solution.</span></span>|[<span data-ttu-id="ab3c2-132">重命名解决方案和项目项</span><span class="sxs-lookup"><span data-stu-id="ab3c2-132">Rename Solutions and Project Items</span></span>](rename-solutions-and-project-items.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ab3c2-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab3c2-133">See Also</span></span>  
 <span data-ttu-id="ab3c2-134">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="ab3c2-134">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="ab3c2-135">[项目 &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ab3c2-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="ab3c2-136">解决方案资源管理器源代码管理</span><span class="sxs-lookup"><span data-stu-id="ab3c2-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
