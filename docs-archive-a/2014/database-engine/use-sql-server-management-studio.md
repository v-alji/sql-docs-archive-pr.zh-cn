---
title: 使用 SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Management Studio [SQL Server]
- Enterprise Manager (See SQL Server Management Studio [Analysis Services])
- SQL Server Management Studio [SQL Server], about SQL Server Management Studio
ms.assetid: f289e978-14ca-46ef-9e61-e1fe5fd593be
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fed75ae8d4a1cfba7fb890a5b0b9c159c13366f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577790"
---
# <a name="use-sql-server-management-studio"></a><span data-ttu-id="f063d-102">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f063d-102">Use SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f063d-103">(SSMS) 是一个集成环境，用于访问、配置、管理和开发的所有组件 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f063d-103">(SSMS) is an integrated environment for accessing, configuring, managing, administering, and developing all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f063d-104">SSMS 将大量图形工具与丰富的脚本编辑器相结合，使各种技术水平的开发人员和管理员都能访问 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f063d-104">SSMS combines a broad group of graphical tools with a number of rich script editors to provide access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to developers and administrators of all skill levels.</span></span>  
  
 <span data-ttu-id="f063d-105">SSMS 将早期版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中所包含的企业管理器、查询分析器和 Analysis Manager 结合到单一的环境中。</span><span class="sxs-lookup"><span data-stu-id="f063d-105">SSMS combines the features of Enterprise Manager, Query Analyzer, and Analysis Manager, included in previous releases of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], into a single environment.</span></span> <span data-ttu-id="f063d-106">此外，SSMS 还可以与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的所有组件（例如 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 和 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]）协同工作。</span><span class="sxs-lookup"><span data-stu-id="f063d-106">In addition, SSMS works with all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] such as [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="f063d-107">开发人员可以获得熟悉的体验，而数据库管理员可获得功能齐全的单一实用工具，其中包含易于使用的图形工具和丰富的脚本撰写功能。</span><span class="sxs-lookup"><span data-stu-id="f063d-107">Developers get a familiar experience, and database administrators get a single comprehensive utility that combines easy-to-use graphical tools with rich scripting capabilities.</span></span>  
  
 <span data-ttu-id="f063d-108">从[Microsoft 开发人员网络](https://msdn.microsoft.com/library/dn434042.aspx)下载和安装 SSMS。</span><span class="sxs-lookup"><span data-stu-id="f063d-108">Download and install SSMS from the [Microsoft Developer Network](https://msdn.microsoft.com/library/dn434042.aspx).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f063d-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="f063d-109">In This Section</span></span>  
 [<span data-ttu-id="f063d-110">SQL Server Management Studio 中的功能</span><span class="sxs-lookup"><span data-stu-id="f063d-110">Features in SQL Server Management Studio</span></span>](features-in-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-111">列出 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]所包括的丰富功能集。</span><span class="sxs-lookup"><span data-stu-id="f063d-111">Lists the rich feature set included in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="f063d-112">SQL Server Management Studio 中的工具窗口</span><span class="sxs-lookup"><span data-stu-id="f063d-112">Tool Windows in SQL Server Management Studio</span></span>](../ssms/tool-windows-in-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-113">介绍属于 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]组件的工具。</span><span class="sxs-lookup"><span data-stu-id="f063d-113">Describes the tools that are components of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="f063d-114">了解 SQL Server Management Studio Windows 管理</span><span class="sxs-lookup"><span data-stu-id="f063d-114">Understand SQL Server Management Studio Windows Management</span></span>](../ssms/understand-sql-server-management-studio-windows-management.md)  
 <span data-ttu-id="f063d-115">介绍如何管理 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中显示的窗口。</span><span class="sxs-lookup"><span data-stu-id="f063d-115">Describes how to manage the windows displayed in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="f063d-116">使用 SQL Server Management Studio 管理服务器</span><span class="sxs-lookup"><span data-stu-id="f063d-116">Administer Servers with SQL Server Management Studio</span></span>](../ssms/administer-servers-with-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-117">介绍如何管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="f063d-117">Describes how to administer instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="f063d-118">从 SQL Server Management Studio 连接到任何 SQL Server 组件</span><span class="sxs-lookup"><span data-stu-id="f063d-118">Connect to Any SQL Server Component from SQL Server Management Studio</span></span>](../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-119">介绍如何连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例以及如何在没有连接的情况下执行某些任务。</span><span class="sxs-lookup"><span data-stu-id="f063d-119">Describes how to connect to instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and how to perform certain tasks without a connection.</span></span>  
  
 [<span data-ttu-id="f063d-120">对象资源管理器</span><span class="sxs-lookup"><span data-stu-id="f063d-120">Object Explorer</span></span>](../ssms/object/object-explorer.md)  
 <span data-ttu-id="f063d-121">介绍对象资源管理器的功能。</span><span class="sxs-lookup"><span data-stu-id="f063d-121">Describes the features of the Object Explorer.</span></span>  
  
 [<span data-ttu-id="f063d-122">SQL Server Management Studio 中的用户帮助</span><span class="sxs-lookup"><span data-stu-id="f063d-122">User Assistance in SQL Server Management Studio</span></span>](../ssms/user-assistance-in-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-123">介绍如何在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中配置用户帮助（例如“帮助”）。</span><span class="sxs-lookup"><span data-stu-id="f063d-123">Describes how to configure user assistance, such as Help, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="f063d-124">查询和文本编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f063d-124">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-125">介绍如何使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中丰富的编辑环境来编辑 [!INCLUDE[tsql](../includes/tsql-md.md)]、MDX、DMX 和 XML/A 脚本。</span><span class="sxs-lookup"><span data-stu-id="f063d-125">Describes how to use the rich editing environment in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to edit [!INCLUDE[tsql](../includes/tsql-md.md)], MDX, DMX and XML/A scripts.</span></span>  
  
 [<span data-ttu-id="f063d-126">使用查询编辑器编辑 SQLCMD 脚本</span><span class="sxs-lookup"><span data-stu-id="f063d-126">Edit SQLCMD Scripts with Query Editor</span></span>](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)  
 <span data-ttu-id="f063d-127">介绍在 SQLCMD 模式下使用查询编辑器的功能和限制。</span><span class="sxs-lookup"><span data-stu-id="f063d-127">Describes the capabilities and limitations of using Query Editor in SQLCMD mode.</span></span>  
  
 [<span data-ttu-id="f063d-128">查询编辑器中的颜色编码</span><span class="sxs-lookup"><span data-stu-id="f063d-128">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
 <span data-ttu-id="f063d-129">介绍代码编辑器窗口中颜色编码的含义。</span><span class="sxs-lookup"><span data-stu-id="f063d-129">Describes the meaning of the color coding in Code Editor windows.</span></span>  
  
 [<span data-ttu-id="f063d-130">SQL Server Management Studio 键盘快捷键</span><span class="sxs-lookup"><span data-stu-id="f063d-130">SQL Server Management Studio Keyboard Shortcuts</span></span>](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
 <span data-ttu-id="f063d-131">列出 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中可用的键盘快捷键。</span><span class="sxs-lookup"><span data-stu-id="f063d-131">Lists the keyboard shortcuts available in the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="f063d-132">自定义菜单和快捷键</span><span class="sxs-lookup"><span data-stu-id="f063d-132">Customize Menus and Shortcut Keys</span></span>](../ssms/customize-menus-and-shortcut-keys.md)  
 <span data-ttu-id="f063d-133">介绍如何创建自定义菜单和快捷方式。</span><span class="sxs-lookup"><span data-stu-id="f063d-133">Describes how to create custom menus and shortcuts.</span></span>  
  
 [<span data-ttu-id="f063d-134">解决方案 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f063d-134">Solutions &#40;SQL Server Management Studio&#41;</span></span>](../ssms/solution/solutions-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-135">介绍如何开发脚本项目和解决方案。</span><span class="sxs-lookup"><span data-stu-id="f063d-135">Describes how to develop script projects and solutions.</span></span>  
  
 [<span data-ttu-id="f063d-136">模板资源管理器</span><span class="sxs-lookup"><span data-stu-id="f063d-136">Template Explorer</span></span>](../ssms/template/template-explorer.md)  
 <span data-ttu-id="f063d-137">介绍如何使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 模板以及如何创建自定义模板。</span><span class="sxs-lookup"><span data-stu-id="f063d-137">Describes how to use the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] templates and how to create custom templates.</span></span>  
  
 [<span data-ttu-id="f063d-138">SQL Server Management Studio 中的属性页</span><span class="sxs-lookup"><span data-stu-id="f063d-138">Property Pages in SQL Server Management Studio</span></span>](../ssms/property-pages-in-sql-server-management-studio.md)  
 <span data-ttu-id="f063d-139">介绍 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的新属性窗口布局。</span><span class="sxs-lookup"><span data-stu-id="f063d-139">Describes the new property window layout in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="f063d-140">Visual Database Tool 设计器</span><span class="sxs-lookup"><span data-stu-id="f063d-140">Visual Database Tool Designers</span></span>](../ssms/visual-db-tools/visual-database-tool-designers.md)  
 <span data-ttu-id="f063d-141">介绍了 Visual Database Tools，您可以使用它来创建查询，设计或修改数据库结构或更新数据。</span><span class="sxs-lookup"><span data-stu-id="f063d-141">Describes the Visual Database Tools that you can use to create queries, design or modify a database structure, or update data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f063d-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f063d-142">See Also</span></span>  
 [<span data-ttu-id="f063d-143">查看或更改服务器属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f063d-143">View or Change Server Properties &#40;SQL Server&#41;</span></span>](configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
