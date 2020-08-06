---
title: 使用 SQL Server Management Studio 管理服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb2a6b9afba7d838cf71144f88ed7866c54ad796
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692119"
---
# <a name="administer-servers-with-sql-server-management-studio"></a><span data-ttu-id="61e95-102">使用 SQL Server Management Studio 管理服务器</span><span class="sxs-lookup"><span data-stu-id="61e95-102">Administer Servers with SQL Server Management Studio</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="61e95-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]是一个丰富的集成管理客户端，旨在满足 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理员的服务器管理要求。</span><span class="sxs-lookup"><span data-stu-id="61e95-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is a rich, integrated administrative client designed to meet the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] administrator's server management requirements.</span></span> <span data-ttu-id="61e95-104">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中，管理任务是使用对象资源管理器来完成的，使用对象资源管理器，您可以连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 系列中的任何服务器，并以图形方式浏览其内容。</span><span class="sxs-lookup"><span data-stu-id="61e95-104">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], administrative tasks are accomplished using Object Explorer, which allows you to connect to any server in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] family and graphically browse its contents.</span></span> <span data-ttu-id="61e95-105">服务器可以是[!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="61e95-105">A server can be an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="61e95-106">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的工具组件包括已注册的服务器、对象资源管理器、解决方案资源管理器、模板资源管理器、对象资源管理器详细信息页和文档窗口。</span><span class="sxs-lookup"><span data-stu-id="61e95-106">The tool components of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] include Registered Servers, Object Explorer, Solution Explorer, Template Explorer, the Object Explorer Details page, and the document window.</span></span> <span data-ttu-id="61e95-107">若要显示某个工具，请在“视图”  菜单上单击该工具的名称。</span><span class="sxs-lookup"><span data-stu-id="61e95-107">To display a tool, on the **View** menu, click the tool name.</span></span> <span data-ttu-id="61e95-108">若要显示查询编辑器工具，请单击工具栏上的“新建查询”  按钮。</span><span class="sxs-lookup"><span data-stu-id="61e95-108">To display the Query Editor tool, click the **New Query** button on the toolbar.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61e95-109">默认情况下，不对 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之间的网络通信进行加密。</span><span class="sxs-lookup"><span data-stu-id="61e95-109">Network traffic between [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is unencrypted by default.</span></span> <span data-ttu-id="61e95-110">除非建立了加密连接，否则不要在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 中使用敏感数据（包括密码）。</span><span class="sxs-lookup"><span data-stu-id="61e95-110">Do not work with sensitive data (including passwords) in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] unless you have established an encrypted connection.</span></span> <span data-ttu-id="61e95-111">有关详细信息，请参阅[启用数据库引擎的加密连接（SQL Server 配置管理器）](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="61e95-111">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>  
  
 <span data-ttu-id="61e95-112">使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 可以：</span><span class="sxs-lookup"><span data-stu-id="61e95-112">Use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="61e95-113">注册服务器。</span><span class="sxs-lookup"><span data-stu-id="61e95-113">Register servers.</span></span>  
  
-   <span data-ttu-id="61e95-114">连接到[!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssAS](../includes/ssas-md.md)]、[!INCLUDE[ssRS](../includes/ssrs.md)] 或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 的一个实例。</span><span class="sxs-lookup"><span data-stu-id="61e95-114">Connect to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssAS](../includes/ssas-md.md)], [!INCLUDE[ssRS](../includes/ssrs.md)], or [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
-   <span data-ttu-id="61e95-115">配置服务器属性。</span><span class="sxs-lookup"><span data-stu-id="61e95-115">Configure server properties.</span></span>  
  
-   <span data-ttu-id="61e95-116">管理数据库和 [!INCLUDE[ssAS](../includes/ssas-md.md)] 对象（如多维数据集、维度和程序集等）。</span><span class="sxs-lookup"><span data-stu-id="61e95-116">Manage database and [!INCLUDE[ssAS](../includes/ssas-md.md)] objects such as cubes, dimensions, and assemblies.</span></span>  
  
-   <span data-ttu-id="61e95-117">创建对象，如数据库、表、多维数据集、数据库用户和登录名等。</span><span class="sxs-lookup"><span data-stu-id="61e95-117">Create objects, such as databases, tables, cubes, database users, and logins.</span></span>  
  
-   <span data-ttu-id="61e95-118">管理文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="61e95-118">Manage files and filegroups.</span></span>  
  
-   <span data-ttu-id="61e95-119">附加或分离数据库。</span><span class="sxs-lookup"><span data-stu-id="61e95-119">Attach or detach databases.</span></span>  
  
-   <span data-ttu-id="61e95-120">启动脚本编写工具。</span><span class="sxs-lookup"><span data-stu-id="61e95-120">Launch scripting tools.</span></span>  
  
-   <span data-ttu-id="61e95-121">管理安全性。</span><span class="sxs-lookup"><span data-stu-id="61e95-121">Manage security.</span></span>  
  
-   <span data-ttu-id="61e95-122">查看系统日志。</span><span class="sxs-lookup"><span data-stu-id="61e95-122">View system logs.</span></span>  
  
-   <span data-ttu-id="61e95-123">监视当前活动。</span><span class="sxs-lookup"><span data-stu-id="61e95-123">Monitor current activity.</span></span>  
  
-   <span data-ttu-id="61e95-124">配置复制。</span><span class="sxs-lookup"><span data-stu-id="61e95-124">Configure replication.</span></span>  
  
-   <span data-ttu-id="61e95-125">管理全文索引。</span><span class="sxs-lookup"><span data-stu-id="61e95-125">Manage full-text indexes.</span></span>  
  
 <span data-ttu-id="61e95-126">若要启动和停止 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理，请使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="61e95-126">To start and stop [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e95-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61e95-127">See Also</span></span>  
 <span data-ttu-id="61e95-128">[使用 SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="61e95-128">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="61e95-129">查看或更改服务器属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="61e95-129">View or Change Server Properties &#40;SQL Server&#41;</span></span>](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
