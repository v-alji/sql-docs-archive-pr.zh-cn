---
title: 使用 SQL Server Management Studio 生成数据库项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], database projects
- database projects [SQL Server]
- projects [SQL Server Management Studio], about projects
- projects [SQL Server Management Studio]
ms.assetid: c2e80045-894d-44cf-b65c-e547ed738947
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ddf3f61e69623716b2987c5c4d849398e822d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576526"
---
# <a name="build-database-projects-by-using-sql-server-management-studio"></a><span data-ttu-id="5e9ad-102">使用 SQL Server Management Studio 生成数据库项目</span><span class="sxs-lookup"><span data-stu-id="5e9ad-102">Build Database Projects by Using SQL Server Management Studio</span></span>
  <span data-ttu-id="5e9ad-103">数据库脚本项目是与数据库或数据库的某一部分关联的一组经过整理的脚本、连接信息和模板。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-103">A database script project is an organized set of scripts, connection information, and templates that are all associated with a database or one part of a database.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="5e9ad-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供了 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，用于在脚本项目上下文中管理和设计 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for administering and designing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databases within the context of a script project.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5e9ad-105">包含设计器、编辑器、指南和向导，可帮助用户开发、部署和维护数据库。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-105">includes designers, editors, guides and wizards to assist users in developing, deploying and maintaining databases.</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="5e9ad-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5e9ad-106">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5e9ad-107">是一套管理工具，用于管理从属于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的组件。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-107">is a suite of administrative tools for managing the components belonging to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5e9ad-108">此集成环境使用户可以在一个界面内执行各种任务，例如，备份数据、编辑查询和自动执行常见函数。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-108">This integrated environment allows users to perform a variety of tasks, such as backing up data, editing queries, and automating common functions within a single interface.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5e9ad-109">包含以下工具：</span><span class="sxs-lookup"><span data-stu-id="5e9ad-109">includes the following tools:</span></span>  
  
-   <span data-ttu-id="5e9ad-110">代码编辑器，用于编写和编辑脚本，是一种功能丰富的脚本编辑器。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-110">Code Editor is a rich script editor for writing and editing scripts.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5e9ad-111">提供了四种版本的代码编辑器：针对 [!INCLUDE[ssDE](../includes/ssde-md.md)] 脚本的 [!INCLUDE[tsql](../includes/tsql-md.md)] 查询编辑器、DMX 查询编辑器、MDX 查询编辑器和 XML/A 查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-111">provides four versions of the Code Editor; the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor for [!INCLUDE[tsql](../includes/tsql-md.md)] scripts, the DMX Query Editor, the MDX Query Editor, and the XML/A Query Editor.</span></span>  
  
-   <span data-ttu-id="5e9ad-112">对象资源管理器，用于查找、修改、编写脚本或运行从属于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的对象。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-112">Object Explorer for locating, modifying, scripting or running objects belonging to instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5e9ad-113">模板资源管理器，用于查找模板以及为模板编写脚本。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-113">Template Explorer for locating and scripting templates.</span></span>  
  
-   <span data-ttu-id="5e9ad-114">解决方案资源管理器，用于将相关脚本组织并存储为项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-114">Solution Explorer for organizing and storing related scripts as parts of a project.</span></span>  
  
-   <span data-ttu-id="5e9ad-115">属性窗口，用于显示当前选定对象的属性。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-115">Properties Window for displaying the current properties of selected objects.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5e9ad-116">通过提供下列项目支持有效的工作过程：</span><span class="sxs-lookup"><span data-stu-id="5e9ad-116">supports efficient work processes by providing:</span></span>  
  
-   <span data-ttu-id="5e9ad-117">断开连接的访问。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-117">Disconnected access.</span></span> <span data-ttu-id="5e9ad-118">可以编写和编辑脚本，而不用与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例连接。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-118">You can write and edit scripts without connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5e9ad-119">在任意对话框中编写脚本。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-119">Scripting from any dialog box.</span></span> <span data-ttu-id="5e9ad-120">可以在任意对话框中创建脚本，以便在创建脚本之后读取、修改、存储和重用脚本。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-120">You can create a script from any dialog box so that you can read, modify, store and reuse the scripts after you create them.</span></span>  
  
-   <span data-ttu-id="5e9ad-121">无模式对话框。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-121">Nonmodal dialog boxes.</span></span> <span data-ttu-id="5e9ad-122">在访问某个 UI 对话框时，可以浏览 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的其他资源而不用关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-122">When you access a UI dialog box you can browse other resources in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] without closing the dialog box.</span></span>  
  
## <a name="solutions-and-script-projects"></a><span data-ttu-id="5e9ad-123">解决方案和脚本项目</span><span class="sxs-lookup"><span data-stu-id="5e9ad-123">Solutions and Script Projects</span></span>  
 <span data-ttu-id="5e9ad-124">解决方案资源管理器是用来存储和重新打开数据库解决方案的实用工具。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-124">Solution Explorer is a utility to store and reopen database solutions.</span></span> <span data-ttu-id="5e9ad-125">解决方案将相关的脚本项目和文件组织在一起。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-125">Solutions organize related script projects and files.</span></span> <span data-ttu-id="5e9ad-126">脚本项目用于存储 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 脚本文件、SQL 模板、连接信息和其他杂项文件。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-126">Script projects store [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] script files, SQL templates, connection information and other miscellaneous files.</span></span> <span data-ttu-id="5e9ad-127">将脚本保存到脚本项目中后，用户能够：</span><span class="sxs-lookup"><span data-stu-id="5e9ad-127">When a script is saved in a script project, users are able to:</span></span>  
  
-   <span data-ttu-id="5e9ad-128">维护脚本的版本控制。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-128">Maintain version control on scripts.</span></span>  
  
-   <span data-ttu-id="5e9ad-129">用脚本存储结果选项。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-129">Store results options with a script.</span></span>  
  
-   <span data-ttu-id="5e9ad-130">在单个脚本项目中组织相关脚本。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-130">Organize related scripts in a single script project.</span></span>  
  
-   <span data-ttu-id="5e9ad-131">用脚本保存连接信息。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-131">Save connection information with scripts.</span></span>  
  
 <span data-ttu-id="5e9ad-132">解决方案资源管理器是开发人员用来创建和重用与同一项目相关的脚本的一种工具。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-132">Solution Explorer is a tool for developers who are creating and reusing scripts that are related to the same project.</span></span> <span data-ttu-id="5e9ad-133">如果以后需要类似的任务，就可以使用项目中存储的脚本组。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-133">If a similar task is required later, you can use group of scripts that were stored in a project.</span></span> <span data-ttu-id="5e9ad-134">如果你曾经使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]创建过应用程序，就会发现解决方案资源管理器非常熟悉。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-134">If you have created applications by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], you will find Solution Explorer very familiar.</span></span>  
  
 <span data-ttu-id="5e9ad-135">解决方案由一个或多个脚本项目组成。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-135">A solution consists of one or more script projects.</span></span> <span data-ttu-id="5e9ad-136">项目则由一个或多个脚本或连接组成。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-136">A project consists of one or more scripts or connections.</span></span> <span data-ttu-id="5e9ad-137">项目中可能还包括非脚本文件。</span><span class="sxs-lookup"><span data-stu-id="5e9ad-137">A project may also include nonscript files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9ad-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e9ad-138">See Also</span></span>  
 <span data-ttu-id="5e9ad-139">[使用 SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5e9ad-139">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="5e9ad-140">[查询和文本编辑器 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5e9ad-140">[Query and Text Editors &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="5e9ad-141">解决方案 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5e9ad-141">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solution/solutions-sql-server-management-studio.md)  
  
  
