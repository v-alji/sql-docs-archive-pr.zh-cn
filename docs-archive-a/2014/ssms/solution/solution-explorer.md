---
title: 解决方案资源管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- solutions [SQL Server Management Studio], about solutions
- SQL Server Management Studio [SQL Server], items
- items [SQL Server]
ms.assetid: 0df09843-0d4f-4925-bc6c-99265035a0c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa312f5e097fa1c59b9ba545709dc964a184c3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580502"
---
# <a name="solution-explorer"></a><span data-ttu-id="5c276-102">解决方案资源管理器</span><span class="sxs-lookup"><span data-stu-id="5c276-102">Solution Explorer</span></span>
  <span data-ttu-id="5c276-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的“解决方案资源管理器”窗格提供了称为“项目”的容器，用于管理数据库脚本、查询、数据连接和文件等项。</span><span class="sxs-lookup"><span data-stu-id="5c276-103">The Solution Explorer pane in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides containers called projects for managing items such as database scripts, queries, data connections, and files.</span></span> <span data-ttu-id="5c276-104">一个或多个彼此相关联的项目可以组合在一个容器中（称为解决方案）。</span><span class="sxs-lookup"><span data-stu-id="5c276-104">One or more projects that are related to each other can be combined in a container called a solution.</span></span>  
  
 <span data-ttu-id="5c276-105">“解决方案”包含一个或多个项目，以及定义整个解决方案所需的文件和元数据。</span><span class="sxs-lookup"><span data-stu-id="5c276-105">A solution includes one or more projects, plus files and metadata that help define the solution as a whole.</span></span> <span data-ttu-id="5c276-106">“项目”是一组文件和相关的元数据（如连接信息）。</span><span class="sxs-lookup"><span data-stu-id="5c276-106">A project is a set of files, plus related metadata such as connection information.</span></span> <span data-ttu-id="5c276-107">解决方案和项目所包含的“项”表示创建数据库解决方案所需的脚本、查询、连接信息和文件。</span><span class="sxs-lookup"><span data-stu-id="5c276-107">Solutions and projects contain items that represent the scripts, queries, connection information and files that you need to create your database solution.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="benefits-of-using-solutions"></a><span data-ttu-id="5c276-108">使用解决方案的好处</span><span class="sxs-lookup"><span data-stu-id="5c276-108">Benefits of Using Solutions</span></span>  
 <span data-ttu-id="5c276-109">使用这些容器可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c276-109">Use these containers to:</span></span>  
  
-   <span data-ttu-id="5c276-110">对查询和脚本实施源代码管理。</span><span class="sxs-lookup"><span data-stu-id="5c276-110">Implement source control on queries and scripts.</span></span>  
  
-   <span data-ttu-id="5c276-111">管理整个解决方案的设置或管理各个项目的设置。</span><span class="sxs-lookup"><span data-stu-id="5c276-111">Manage settings for your solution as a whole or for individual projects.</span></span>  
  
-   <span data-ttu-id="5c276-112">在您集中精力管理构成数据库解决方案的项的同时，处理文件管理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5c276-112">Handle the details of file management while you focus on items that make up your database solution.</span></span>  
  
-   <span data-ttu-id="5c276-113">向解决方案中的多个项目或向解决方案添加有用项，而不必在每个项目中都引用该项。</span><span class="sxs-lookup"><span data-stu-id="5c276-113">Add items that are useful to multiple projects in the solution or to the solution without referencing the item in each project.</span></span>  
  
-   <span data-ttu-id="5c276-114">对独立于解决方案或项目的杂项文件进行操作。</span><span class="sxs-lookup"><span data-stu-id="5c276-114">Work on miscellaneous files that are independent from solutions or projects.</span></span>  
  
 <span data-ttu-id="5c276-115">项目中包含的项取决于项目类型以及您是否使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5c276-115">The items contained in projects depend on the project type and whether you are using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5c276-116">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="5c276-116">Related Tasks</span></span>  
 <span data-ttu-id="5c276-117">使用以下主题开始使用 SQL Server 解决方案：</span><span class="sxs-lookup"><span data-stu-id="5c276-117">Use the following topics to get started with SQL Server Solutions:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c276-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="5c276-118">**Description**</span></span>|<span data-ttu-id="5c276-119">**主题**</span><span class="sxs-lookup"><span data-stu-id="5c276-119">**Topic**</span></span>|  
|<span data-ttu-id="5c276-120">介绍如何在解决方案中收集一个或多个项目。</span><span class="sxs-lookup"><span data-stu-id="5c276-120">Describes how to collect one or more projects in a solution.</span></span>|[<span data-ttu-id="5c276-121">解决方案 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5c276-121">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solutions-sql-server-management-studio.md)|  
|<span data-ttu-id="5c276-122">介绍如何创建项目并添加项（如脚本和连接）。</span><span class="sxs-lookup"><span data-stu-id="5c276-122">Describes how to create a project and add items like scripts and connections.</span></span>|[<span data-ttu-id="5c276-123">项目 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5c276-123">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)|  
|<span data-ttu-id="5c276-124">介绍如何将解决方案或单独的项目集成到源代码管理系统。</span><span class="sxs-lookup"><span data-stu-id="5c276-124">Describes how to integrate solutions or individual projects into a source code control system.</span></span>|[<span data-ttu-id="5c276-125">解决方案资源管理器源代码管理</span><span class="sxs-lookup"><span data-stu-id="5c276-125">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)|  
|<span data-ttu-id="5c276-126">提供有关 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 管理解决方案和文件所使用的文件的信息。</span><span class="sxs-lookup"><span data-stu-id="5c276-126">Provides information about the files used by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage solutions and files.</span></span>|[<span data-ttu-id="5c276-127">用于管理解决方案和项目的文件</span><span class="sxs-lookup"><span data-stu-id="5c276-127">Files That Manage Solutions and Projects</span></span>](files-that-manage-solutions-and-projects.md)|  
  
  
