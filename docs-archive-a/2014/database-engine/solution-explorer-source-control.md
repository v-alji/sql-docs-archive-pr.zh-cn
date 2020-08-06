---
title: 解决方案资源管理器源代码管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual SourceSafe
- SQL Server Management Studio [SQL Server], source control services
- source-controlled files [SQL Server]
- source controls [SQL Server Management Studio], services
- version control services [SQL Server]
- file source control services [SQL Server]
- VSS [Visual SourceSafe]
ms.assetid: 6373adb8-3d81-4945-a9fc-1d0d5799d29a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 46471ba8149c26f80e78006bc3a8befc2e81b416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588684"
---
# <a name="solution-explorer-source-control"></a><span data-ttu-id="cc518-102">解决方案资源管理器源代码管理</span><span class="sxs-lookup"><span data-stu-id="cc518-102">Solution Explorer Source Control</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="cc518-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]解决方案资源管理器可以集成到单独的源代码管理系统中。</span><span class="sxs-lookup"><span data-stu-id="cc518-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Solution Explorer can be integrated into a separate source control system.</span></span> <span data-ttu-id="cc518-104">将解决方案或项目集成到源代码管理系统中后，即可控制针对项目中的脚本和查询的文件访问和版本控制。</span><span class="sxs-lookup"><span data-stu-id="cc518-104">Once a solution or project is integrated into a source control system, you can control file access and versioning for the scripts and queries in your projects.</span></span>  
  
## <a name="solution-and-project-source-control"></a><span data-ttu-id="cc518-105">解决方案和项目源代码管理</span><span class="sxs-lookup"><span data-stu-id="cc518-105">Solution and Project Source Control</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="cc518-106">源代码管理是指以下系统：在该系统中，使用中心服务器软件存储和跟踪文件版本，并控制对文件的访问。</span><span class="sxs-lookup"><span data-stu-id="cc518-106">Source control refers to a system in which a central piece of server software stores and tracks file versions, and also controls access to files.</span></span> <span data-ttu-id="cc518-107">典型的源代码管理系统包括源代码管理提供程序以及两个或多个源代码管理客户端。</span><span class="sxs-lookup"><span data-stu-id="cc518-107">A typical source control system includes a source control provider and two or more source control clients.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="cc518-108">可与源代码管理服务集成在一起。</span><span class="sxs-lookup"><span data-stu-id="cc518-108">can be integrated with a source control service.</span></span> <span data-ttu-id="cc518-109">也就是说，可将该工具用作源代码管理提供程序的客户端。</span><span class="sxs-lookup"><span data-stu-id="cc518-109">This means you can use the tool as a client for your source control provider.</span></span> <span data-ttu-id="cc518-110">您无需离开环境就可以轻松管理个人项目和团队项目。</span><span class="sxs-lookup"><span data-stu-id="cc518-110">Without leaving the environment, you can manage your individual and team projects easily.</span></span> <span data-ttu-id="cc518-111">源代码管理提供程序不包含在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="cc518-111">The source control provider is not included with [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
#### <a name="to-select-a-source-control-provider"></a><span data-ttu-id="cc518-112">选择源代码管理提供程序</span><span class="sxs-lookup"><span data-stu-id="cc518-112">To select a source control provider</span></span>  
  
1.  <span data-ttu-id="cc518-113">安装源代码管理提供程序的客户端部分。</span><span class="sxs-lookup"><span data-stu-id="cc518-113">Install the client portion of your source control provider.</span></span>  
  
2.  <span data-ttu-id="cc518-114">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]的 **“工具”** 菜单中，单击 **“选项”**。</span><span class="sxs-lookup"><span data-stu-id="cc518-114">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="cc518-115">在 "**选项**" 对话框中，展开 "**源代码管理**"，然后单击 "**插件选择**" 页。</span><span class="sxs-lookup"><span data-stu-id="cc518-115">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
4.  <span data-ttu-id="cc518-116">在 "**当前源代码管理插件**" 框中，选择源代码管理插件。</span><span class="sxs-lookup"><span data-stu-id="cc518-116">In the **Current source control plug-in** box, select the source control plug-in.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc518-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="cc518-117">In This Section</span></span>  
  
|<span data-ttu-id="cc518-118">主题</span><span class="sxs-lookup"><span data-stu-id="cc518-118">Topic</span></span>|<span data-ttu-id="cc518-119">说明</span><span class="sxs-lookup"><span data-stu-id="cc518-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cc518-120">源代码管理基础</span><span class="sxs-lookup"><span data-stu-id="cc518-120">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)|<span data-ttu-id="cc518-121">定义基本源代码管理术语，并说明使用源代码管理服务，项目将如何从中受益。</span><span class="sxs-lookup"><span data-stu-id="cc518-121">Defines basic source control terminology, and explains how your project can benefit from using source control services.</span></span>|  
|[<span data-ttu-id="cc518-122">将解决方案和项目添加到源代码管理</span><span class="sxs-lookup"><span data-stu-id="cc518-122">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)|<span data-ttu-id="cc518-123">说明如何使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 环境，将解决方案和项目添加到源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="cc518-123">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to add solutions and projects to source control.</span></span>|  
|[<span data-ttu-id="cc518-124">从源代码管理打开解决方案和项目</span><span class="sxs-lookup"><span data-stu-id="cc518-124">Open Solutions and Projects from Source Control</span></span>](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)|<span data-ttu-id="cc518-125">说明如何使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 环境打开源代码管理的解决方案和项目。</span><span class="sxs-lookup"><span data-stu-id="cc518-125">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to open source-controlled solutions and projects.</span></span>|  
|[<span data-ttu-id="cc518-126">管理签出</span><span class="sxs-lookup"><span data-stu-id="cc518-126">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)|<span data-ttu-id="cc518-127">说明如何从源代码管理中签出解决方案和文件。</span><span class="sxs-lookup"><span data-stu-id="cc518-127">Explains how to check out solutions and files from source control.</span></span>|  
|[<span data-ttu-id="cc518-128">管理签入</span><span class="sxs-lookup"><span data-stu-id="cc518-128">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)|<span data-ttu-id="cc518-129">说明如何将解决方案和文件签入源代码管理。</span><span class="sxs-lookup"><span data-stu-id="cc518-129">Explains how to check solutions and files into source control.</span></span>|  
|[<span data-ttu-id="cc518-130">设置和检索版本信息</span><span class="sxs-lookup"><span data-stu-id="cc518-130">Set and Retrieve Version Information</span></span>](../../2014/database-engine/set-and-retrieve-version-information.md)|<span data-ttu-id="cc518-131">说明如何检索项目或项的历史记录、检索项的本地副本或比较项的两个版本。</span><span class="sxs-lookup"><span data-stu-id="cc518-131">Explains how to retrieve the history of a project or item, retrieve a local copy of an item, or compare two item versions.</span></span>|  
|||  
  
## <a name="see-also"></a><span data-ttu-id="cc518-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc518-132">See Also</span></span>  
 <span data-ttu-id="cc518-133">[解决方案资源管理器](../ssms/solution/solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="cc518-133">[Solution Explorer](../ssms/solution/solution-explorer.md) </span></span>  
 <span data-ttu-id="cc518-134">[SQL Server Management Studio 的解决方案 &#40;&#41;](../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="cc518-134">[Solutions &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md) </span></span>  
 <span data-ttu-id="cc518-135">[项目 &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="cc518-135">[Projects &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="cc518-136">用于管理解决方案和项目的文件</span><span class="sxs-lookup"><span data-stu-id="cc518-136">Files That Manage Solutions and Projects</span></span>](../ssms/solution/files-that-manage-solutions-and-projects.md)  
  
  
