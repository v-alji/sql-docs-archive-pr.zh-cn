---
title: 项目 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fed02e84b154a86788b350812ad8fd5137c14b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590518"
---
# <a name="projects-sql-server-management-studio"></a><span data-ttu-id="6083f-102">项目 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6083f-102">Projects (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6083f-103">一个 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 项目是一些在逻辑上相关并可保存在一起用于数据库管理和开发的脚本和文件的集合。</span><span class="sxs-lookup"><span data-stu-id="6083f-103">A [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] project is a collection of logically related scripts and files that can be saved together for database administration and development.</span></span>  
  
## <a name="script-project-overview"></a><span data-ttu-id="6083f-104">脚本项目概述</span><span class="sxs-lookup"><span data-stu-id="6083f-104">Script Project Overview</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6083f-105">脚本项目显示在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的解决方案资源管理器组件中。</span><span class="sxs-lookup"><span data-stu-id="6083f-105">script projects are displayed in the Solution Explorer component of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="6083f-106">脚本项目可以不包含项目文件，也可以包含多个项目文件。</span><span class="sxs-lookup"><span data-stu-id="6083f-106">A script project can contain zero or more project files.</span></span> <span data-ttu-id="6083f-107">可以将项目添加到解决方案中，或者将多个项目组合在一个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="6083f-107">You can add a project to a solution or combine more than one project within a solution.</span></span>  
  
 <span data-ttu-id="6083f-108">项目可以包括以下项：</span><span class="sxs-lookup"><span data-stu-id="6083f-108">Projects can include the following:</span></span>  
  
-   <span data-ttu-id="6083f-109">**连接**。</span><span class="sxs-lookup"><span data-stu-id="6083f-109">**Connections**.</span></span> <span data-ttu-id="6083f-110">连接是项目中的持久项，它将包含登录信息、服务器名称、默认数据库、首选协议、身份验证类型和连接属性。</span><span class="sxs-lookup"><span data-stu-id="6083f-110">A connection, as persisted within a project, will contain login information, server name, default database, preferred protocol, authentication type, and connection properties.</span></span> <span data-ttu-id="6083f-111">连接信息可能根据需要与脚本存储在一起（请参见下面内容）。</span><span class="sxs-lookup"><span data-stu-id="6083f-111">Connection information may optionally be stored with a script (see below).</span></span>  
  
-   <span data-ttu-id="6083f-112">**SQL 脚本**。</span><span class="sxs-lookup"><span data-stu-id="6083f-112">**SQLScripts**.</span></span> <span data-ttu-id="6083f-113">用户的常用 SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="6083f-113">Frequently used SQL scripts for the user.</span></span> <span data-ttu-id="6083f-114">双击项目中的 .sql 文件将会使 SQL 编辑器打开所选脚本。</span><span class="sxs-lookup"><span data-stu-id="6083f-114">Double-clicking a .sql file within the project will cause the SQL Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="6083f-115">**MDX、DMX 和 XMLA 脚本**。</span><span class="sxs-lookup"><span data-stu-id="6083f-115">**MDX, DMX, and XMLAScripts**.</span></span> <span data-ttu-id="6083f-116">用户的常用 MDX 脚本。</span><span class="sxs-lookup"><span data-stu-id="6083f-116">Frequently used MDX scripts for the user.</span></span> <span data-ttu-id="6083f-117">双击项目中的 .mdx 文件将会使编辑器打开所选脚本。</span><span class="sxs-lookup"><span data-stu-id="6083f-117">Double-clicking an .mdx file within the project will cause the Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="6083f-118">**杂项**。该文件夹可用于不完全适合于任何其他默认节点类型的文件，如包含项目目标的文本文件。</span><span class="sxs-lookup"><span data-stu-id="6083f-118">**Misc**. This folder can be used for files that do not neatly fit into any of the other default node types, such as a text file that contains the project objectives.</span></span>  
  
 <span data-ttu-id="6083f-119">项目还可以集成到源代码管理系统中。</span><span class="sxs-lookup"><span data-stu-id="6083f-119">Projects can also be integrated into a source code control system.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a><span data-ttu-id="6083f-120">从脚本项目连接到 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="6083f-120">Connecting to an Instance of SQL Server from a Script Project</span></span>  
 <span data-ttu-id="6083f-121">脚本项目可能包含与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。</span><span class="sxs-lookup"><span data-stu-id="6083f-121">A script project may contain connections to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6083f-122">通过单击连接，可以连接到项目中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="6083f-122">You can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a project by clicking the connection.</span></span> <span data-ttu-id="6083f-123">这将打开一个 SQL 脚本窗口，该窗口将连接到在所选连接中定义的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="6083f-123">This will open an SQL Script window that is connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defined in the connection you selected.</span></span> <span data-ttu-id="6083f-124">如果通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的连接打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 MDX 脚本，则在打开编辑器并且加载脚本之后，系统将使用“连接到 SQL Server”  对话框提示你输入密码。</span><span class="sxs-lookup"><span data-stu-id="6083f-124">If you open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or MDX script with a connection that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, you will be prompted for the password using the **Connect to SQL Server** dialog box after the Editor has been opened and the script loaded.</span></span>  
  
 <span data-ttu-id="6083f-125">相应窗口关闭后，连接也将随之关闭。</span><span class="sxs-lookup"><span data-stu-id="6083f-125">The connection will be closed after the corresponding window is closed.</span></span>  
  
 <span data-ttu-id="6083f-126">若要修改有关连接的信息，请使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的属性窗口。</span><span class="sxs-lookup"><span data-stu-id="6083f-126">To modify information about a connection, use the properties window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="project-tasks"></a><span data-ttu-id="6083f-127">项目任务</span><span class="sxs-lookup"><span data-stu-id="6083f-127">Project Tasks</span></span>  
  
|<span data-ttu-id="6083f-128">任务说明</span><span class="sxs-lookup"><span data-stu-id="6083f-128">Task Description</span></span>|<span data-ttu-id="6083f-129">主题</span><span class="sxs-lookup"><span data-stu-id="6083f-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="6083f-130">说明如何在解决方案中创建新项目。</span><span class="sxs-lookup"><span data-stu-id="6083f-130">Describes how to create a new project in a solution.</span></span>|[<span data-ttu-id="6083f-131">创建项目</span><span class="sxs-lookup"><span data-stu-id="6083f-131">Create a Project</span></span>](create-a-project.md)|  
|<span data-ttu-id="6083f-132">说明如何向解决方案中添加现有项目。</span><span class="sxs-lookup"><span data-stu-id="6083f-132">Describes how to add an existing project to a solution.</span></span>|[<span data-ttu-id="6083f-133">在解决方案中添加现有项目</span><span class="sxs-lookup"><span data-stu-id="6083f-133">Add an Existing Project to a Solution</span></span>](add-an-existing-project-to-a-solution.md)|  
|<span data-ttu-id="6083f-134">说明如何更改保存项目文件的默认位置。</span><span class="sxs-lookup"><span data-stu-id="6083f-134">Describes how to change the default location at which project files are saved.</span></span>|[<span data-ttu-id="6083f-135">更改项目的默认位置</span><span class="sxs-lookup"><span data-stu-id="6083f-135">Change the Default Location for Projects</span></span>](change-the-default-location-for-projects.md)|  
|<span data-ttu-id="6083f-136">说明如何查看项目的当前属性。</span><span class="sxs-lookup"><span data-stu-id="6083f-136">Describes how to view the current properties for a project.</span></span>|[<span data-ttu-id="6083f-137">视图项目属性</span><span class="sxs-lookup"><span data-stu-id="6083f-137">View Project Properties</span></span>](view-project-properties.md)|  
|<span data-ttu-id="6083f-138">说明如何将新项（例如连接或脚本文件）添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="6083f-138">Describes how to add new items, such as connections or script files, to a project.</span></span>|[<span data-ttu-id="6083f-139">向项目添加新项</span><span class="sxs-lookup"><span data-stu-id="6083f-139">Add New Items to a Project</span></span>](add-new-items-to-a-project.md)|  
|<span data-ttu-id="6083f-140">说明如何建立查询的连接信息。</span><span class="sxs-lookup"><span data-stu-id="6083f-140">Describes how to establish the connection information for a query.</span></span>|[<span data-ttu-id="6083f-141">将查询与项目中的连接关联</span><span class="sxs-lookup"><span data-stu-id="6083f-141">Associate a Query with a Connection in a Project</span></span>](associate-a-query-with-a-connection-in-a-project.md)|  
|<span data-ttu-id="6083f-142">说明如何更改查询的连接信息。</span><span class="sxs-lookup"><span data-stu-id="6083f-142">Describes how to change the connection information for a query.</span></span>|[<span data-ttu-id="6083f-143">更改与查询关联的连接</span><span class="sxs-lookup"><span data-stu-id="6083f-143">Change the Connection Associated with a Query</span></span>](change-the-connection-associated-with-a-query.md)|  
|<span data-ttu-id="6083f-144">说明如何更改连接属性。</span><span class="sxs-lookup"><span data-stu-id="6083f-144">Describes how to change connection properties.</span></span>|[<span data-ttu-id="6083f-145">查看或更改项目中的连接属性</span><span class="sxs-lookup"><span data-stu-id="6083f-145">View or Change the Properties of a Connection in a Project</span></span>](view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a><span data-ttu-id="6083f-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6083f-146">See Also</span></span>  
 <span data-ttu-id="6083f-147">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="6083f-147">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="6083f-148">[SQL Server Management Studio 的解决方案 &#40;&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6083f-148">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="6083f-149">解决方案资源管理器源代码管理</span><span class="sxs-lookup"><span data-stu-id="6083f-149">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
