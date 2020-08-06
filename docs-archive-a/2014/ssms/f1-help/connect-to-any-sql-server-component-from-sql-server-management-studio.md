---
title: 从 SQL Server Management Studio 连接到任何 SQL Server 组件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9cd3e185ea6f289a2a6db46cdca2cb310fefbcf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690313"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a><span data-ttu-id="e3e84-102">从 SQL Server Management Studio 连接到任何 SQL Server 组件</span><span class="sxs-lookup"><span data-stu-id="e3e84-102">Connect to Any SQL Server Component from SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="e3e84-103">提供了管理每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]组件的功能。</span><span class="sxs-lookup"><span data-stu-id="e3e84-103">provides functionality for managing every component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e3e84-104">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 可以连接到：</span><span class="sxs-lookup"><span data-stu-id="e3e84-104">Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to connect to:</span></span>  
  
-   <span data-ttu-id="e3e84-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="e3e84-105">An instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e3e84-106">列中的一个值匹配。</span><span class="sxs-lookup"><span data-stu-id="e3e84-106">.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="e3e84-107">列中的一个值匹配。</span><span class="sxs-lookup"><span data-stu-id="e3e84-107">.</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e3e84-108">列中的一个值匹配。</span><span class="sxs-lookup"><span data-stu-id="e3e84-108">.</span></span>  
  
 <span data-ttu-id="e3e84-109">虽然 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 允许您在使用查询时无需先建立与数据源的连接，但其他多数任务需要一个连接。</span><span class="sxs-lookup"><span data-stu-id="e3e84-109">Although [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] allows you to work with queries without first establishing a connection to a data source, most other tasks require a connection.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="e3e84-110">提供了“连接到服务器”  对话框，可用于配置到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件的连接属性。</span><span class="sxs-lookup"><span data-stu-id="e3e84-110">provides the **Connect to Server** dialog box to configure connection properties to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="e3e84-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 启动时，将打开“连接到服务器”  对话框，并提示你连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="e3e84-111">When [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] starts, it opens the **Connect to Server** dialog box and prompts you to connect to a server.</span></span> <span data-ttu-id="e3e84-112">“连接到服务器”  对话框会保留上次使用的连接设置。</span><span class="sxs-lookup"><span data-stu-id="e3e84-112">The **Connect to Server** dialog box retains the connection settings from the last time it was used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3e84-113">可以关闭此功能，以免自动启动某个连接。</span><span class="sxs-lookup"><span data-stu-id="e3e84-113">This feature can be turned off so no connection is automatically initiated.</span></span> <span data-ttu-id="e3e84-114">有关详细信息，请参阅 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e84-114">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).</span></span>  
  
## <a name="saving-connections"></a><span data-ttu-id="e3e84-115">保存连接</span><span class="sxs-lookup"><span data-stu-id="e3e84-115">Saving Connections</span></span>  
 <span data-ttu-id="e3e84-116">可以在已注册的服务器中将连接保存到特定服务器，也可以在解决方案资源管理器中将连接保存到项目中。</span><span class="sxs-lookup"><span data-stu-id="e3e84-116">You can save connections to specific servers in Registered Servers, or you can save connections in projects with Solution Explorer.</span></span>  
  
### <a name="saving-connections-in-registered-servers"></a><span data-ttu-id="e3e84-117">在已注册的服务器中保存连接</span><span class="sxs-lookup"><span data-stu-id="e3e84-117">Saving Connections in Registered Servers</span></span>  
 <span data-ttu-id="e3e84-118">注册服务器时， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 会在已注册的服务器中保存连接信息。</span><span class="sxs-lookup"><span data-stu-id="e3e84-118">When you register a server, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] saves the connection information in Registered Servers.</span></span> <span data-ttu-id="e3e84-119">若要连接到某个已注册的服务器，可在已注册的服务器中双击该服务器名称。</span><span class="sxs-lookup"><span data-stu-id="e3e84-119">To connect to a registered server, double-click the server name in Registered Servers.</span></span> <span data-ttu-id="e3e84-120">对象资源管理器随即会打开一个到该服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="e3e84-120">Object Explorer then opens a connection to the server.</span></span>  
  
### <a name="saving-connections-in-solution-explorer"></a><span data-ttu-id="e3e84-121">在解决方案资源管理器中保存连接</span><span class="sxs-lookup"><span data-stu-id="e3e84-121">Saving Connections in Solution Explorer</span></span>  
 <span data-ttu-id="e3e84-122">使用解决方案资源管理器，可以在项目中存储相关的查询、脚本、连接和其他关联的信息。</span><span class="sxs-lookup"><span data-stu-id="e3e84-122">Solution Explorer allows you to store related queries, scripts, connections, and other associated information in a project.</span></span> <span data-ttu-id="e3e84-123">每个脚本项目都包含一个名为“连接”  的节点，可以在其中保存一个或多个连接。</span><span class="sxs-lookup"><span data-stu-id="e3e84-123">Each script project contains a node called **Connections**, where you can save one or more connections.</span></span> <span data-ttu-id="e3e84-124">若要添加连接，可右键单击“连接”  ，再单击“新建连接”  。</span><span class="sxs-lookup"><span data-stu-id="e3e84-124">To add a connection, right-click **Connections**, and then click **New Connection**.</span></span> <span data-ttu-id="e3e84-125">若要访问已保存的连接，可展开“连接”  ，然后双击该连接。</span><span class="sxs-lookup"><span data-stu-id="e3e84-125">To access a saved connection, expand **Connections** and double-click the connection.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="e3e84-126">随即会打开一个与该连接关联的查询窗口。</span><span class="sxs-lookup"><span data-stu-id="e3e84-126">opens a query window associated with that connection.</span></span> <span data-ttu-id="e3e84-127">保存后，脚本会保留其与特定连接的关联。</span><span class="sxs-lookup"><span data-stu-id="e3e84-127">When saved, scripts retain their association to a specific connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e84-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3e84-128">See Also</span></span>  
 <span data-ttu-id="e3e84-129">[使用 SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="e3e84-129">[Use SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="e3e84-130">对象资源管理器</span><span class="sxs-lookup"><span data-stu-id="e3e84-130">Object Explorer</span></span>](../object/object-explorer.md)  
  
  
