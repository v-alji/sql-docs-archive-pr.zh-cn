---
title: 注册服务器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f4b23ba127c6b000b0abbe832c4c072ada78c5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580506"
---
# <a name="register-servers"></a><span data-ttu-id="67234-102">注册服务器</span><span class="sxs-lookup"><span data-stu-id="67234-102">Register Servers</span></span>
  <span data-ttu-id="67234-103">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中注册服务器使您可以存储服务器连接信息，以供将来连接时使用。有三种方法可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中注册服务器。</span><span class="sxs-lookup"><span data-stu-id="67234-103">Registering a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] allows you to store the server connection information for future connections.There are three ways to register a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="67234-104">在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之后首次启动它时，将自动注册 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的本地实例。</span><span class="sxs-lookup"><span data-stu-id="67234-104">Local instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are automatically registered during the first launch of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] after its installation.</span></span>  
  
2.  <span data-ttu-id="67234-105">也可以随时启动自动注册过程来还原本地服务器实例的注册。</span><span class="sxs-lookup"><span data-stu-id="67234-105">You can also initiate the automatic registration process at any time, to restore the registration of local server instances.</span></span>  
  
3.  <span data-ttu-id="67234-106">最后，还可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的“已注册的服务器”工具注册服务器。</span><span class="sxs-lookup"><span data-stu-id="67234-106">Lastly, you can register a server using the Registered Servers tool in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="benefits-of-registered-servers"></a><span data-ttu-id="67234-107">已注册服务器的优点</span><span class="sxs-lookup"><span data-stu-id="67234-107">Benefits of Registered Servers</span></span>  
 <span data-ttu-id="67234-108">使用已注册的服务器，您可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="67234-108">With Registered Servers you can:</span></span>  
  
-   <span data-ttu-id="67234-109">注册服务器以保留连接信息。</span><span class="sxs-lookup"><span data-stu-id="67234-109">Register servers to preserve the connection information.</span></span>  
  
-   <span data-ttu-id="67234-110">确定已注册的服务器是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="67234-110">Determine if a registered server is running.</span></span>  
  
-   <span data-ttu-id="67234-111">将对象资源管理器和查询编辑器轻松连接到已注册的服务器。</span><span class="sxs-lookup"><span data-stu-id="67234-111">Easily connect Object Explorer and Query Editor to a registered server.</span></span>  
  
-   <span data-ttu-id="67234-112">编辑或删除已注册服务器的注册信息。</span><span class="sxs-lookup"><span data-stu-id="67234-112">Edit or delete the registration information for a registered server.</span></span>  
  
-   <span data-ttu-id="67234-113">创建服务器组。</span><span class="sxs-lookup"><span data-stu-id="67234-113">Create groups of servers.</span></span>  
  
-   <span data-ttu-id="67234-114">通过在“已注册的服务器名称”  框中提供与“服务器名称”  列表中不同的值，为已注册的服务器提供用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="67234-114">Provide user-friendly names for registered servers by providing a value in the **Registered server name** box that is different from the **Server name** list.</span></span>  
  
-   <span data-ttu-id="67234-115">提供已注册服务器的详细说明。</span><span class="sxs-lookup"><span data-stu-id="67234-115">Provide detailed descriptions for registered servers.</span></span>  
  
-   <span data-ttu-id="67234-116">提供已注册服务器组的详细说明。</span><span class="sxs-lookup"><span data-stu-id="67234-116">Provide detailed descriptions of registered server groups.</span></span>  
  
-   <span data-ttu-id="67234-117">导出已注册的服务器组。</span><span class="sxs-lookup"><span data-stu-id="67234-117">Export registered server groups.</span></span>  
  
-   <span data-ttu-id="67234-118">导入已注册的服务器组。</span><span class="sxs-lookup"><span data-stu-id="67234-118">Import registered server groups.</span></span>  
  
-   <span data-ttu-id="67234-119">查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机或脱机实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日志文件。</span><span class="sxs-lookup"><span data-stu-id="67234-119">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files for online or offline instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="67234-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="67234-120">Related Tasks</span></span>  
 <span data-ttu-id="67234-121">参考以下主题可以开始使用注册服务器：</span><span class="sxs-lookup"><span data-stu-id="67234-121">Use the following topics to get started with registered servers:</span></span>  
  
|<span data-ttu-id="67234-122">**说明**</span><span class="sxs-lookup"><span data-stu-id="67234-122">**Description**</span></span>|<span data-ttu-id="67234-123">**主题**</span><span class="sxs-lookup"><span data-stu-id="67234-123">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="67234-124">注册本地服务器实例</span><span class="sxs-lookup"><span data-stu-id="67234-124">Register local server instances</span></span>|[<span data-ttu-id="67234-125">注册连接的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-125">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](register-a-connected-server-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-126">注册服务器</span><span class="sxs-lookup"><span data-stu-id="67234-126">Register a server</span></span>|[<span data-ttu-id="67234-127">创建新的已注册的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-127">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-128">查看已注册的服务器</span><span class="sxs-lookup"><span data-stu-id="67234-128">View registered servers</span></span>|[<span data-ttu-id="67234-129">查看 SQL Server Management Studio 中已注册的服务器</span><span class="sxs-lookup"><span data-stu-id="67234-129">View Registered Servers in SQL Server Management Studio</span></span>](view-registered-servers-in-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-130">删除注册服务器</span><span class="sxs-lookup"><span data-stu-id="67234-130">Remove a registered server</span></span>|[<span data-ttu-id="67234-131">删除已注册的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-131">Remove a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](remove-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-132">更改服务器注册</span><span class="sxs-lookup"><span data-stu-id="67234-132">Change a server's registration</span></span>|[<span data-ttu-id="67234-133">更改服务器的注册信息 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-133">Change a Server's Registration &#40;SQL Server Management Studio&#41;</span></span>](change-a-server-s-registration-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-134">连接到注册服务器</span><span class="sxs-lookup"><span data-stu-id="67234-134">Connect to a registered server</span></span>|[<span data-ttu-id="67234-135">连接到已注册的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-135">Connect to a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](connect-to-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-136">从已注册的服务器断开连接</span><span class="sxs-lookup"><span data-stu-id="67234-136">Disconnect from a registered server</span></span>|[<span data-ttu-id="67234-137">断开与已注册服务器的连接 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-137">Disconnect from a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-138">移动已注册的服务器或服务器组</span><span class="sxs-lookup"><span data-stu-id="67234-138">Move a registered server or server group</span></span>|[<span data-ttu-id="67234-139">移动已注册的服务器或已注册的服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-139">Move a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](move-a-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="67234-140">更改已注册的服务器或服务器组的名称</span><span class="sxs-lookup"><span data-stu-id="67234-140">Change the name of a registered server or server group</span></span>|[<span data-ttu-id="67234-141">更改已注册的服务器或已注册的服务器组的名称 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-141">Change the Name of a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](change-the-name-of-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="67234-142">创建或编辑服务器组</span><span class="sxs-lookup"><span data-stu-id="67234-142">Create or edit a server group</span></span>|[<span data-ttu-id="67234-143">创建或编辑服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-143">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-144">删除服务器组</span><span class="sxs-lookup"><span data-stu-id="67234-144">Remove a server group</span></span>|[<span data-ttu-id="67234-145">删除服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-145">Remove a Server Group &#40;SQL Server Management Studio&#41;</span></span>](remove-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-146">导出已注册的服务器信息</span><span class="sxs-lookup"><span data-stu-id="67234-146">Export registered server information</span></span>|[<span data-ttu-id="67234-147">导出已注册服务器信息 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-147">Export Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](export-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-148">导入已注册的服务器信息</span><span class="sxs-lookup"><span data-stu-id="67234-148">Import registered server information</span></span>|[<span data-ttu-id="67234-149">导入已注册的服务器信息 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-149">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="67234-150">创建中央管理服务器和服务器组</span><span class="sxs-lookup"><span data-stu-id="67234-150">Create a Central Management Server and Server Group</span></span>|[<span data-ttu-id="67234-151">创建中央管理服务器和服务器组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-151">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-a-central-management-server-and-server-group.md)|  
|<span data-ttu-id="67234-152">同时对多个服务器执行语句</span><span class="sxs-lookup"><span data-stu-id="67234-152">Execute statements against multiple servers simultaneously</span></span>|[<span data-ttu-id="67234-153">同时对多个服务器执行语句 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="67234-153">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="67234-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67234-154">See Also</span></span>  
 [<span data-ttu-id="67234-155">远程服务器</span><span class="sxs-lookup"><span data-stu-id="67234-155">Remote Servers</span></span>](../../database-engine/configure-windows/remote-servers.md)  
  
  
