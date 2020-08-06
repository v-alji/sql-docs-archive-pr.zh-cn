---
title: 管理服务的安全要求 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a777858c01bf3057093d34b29b9a2093668e97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692529"
---
# <a name="security-requirements-for-managing-services"></a><span data-ttu-id="ec336-102">管理服务的安全要求</span><span class="sxs-lookup"><span data-stu-id="ec336-102">Security Requirements for Managing Services</span></span>
  <span data-ttu-id="ec336-103">要管理[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务，请使用 SQL Server 配置管理器或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ec336-103">To manage the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Services, use either SQL Server Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ec336-104">使用群集管理器管理群集服务器上的服务。</span><span class="sxs-lookup"><span data-stu-id="ec336-104">Manage the services on clustered servers with the Cluster Administrator.</span></span>  
  
 <span data-ttu-id="ec336-105">若要管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务并设置服务器配置选项，您必须是 **serveradmin** 固定服务器角色或 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="ec336-105">To manage the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service and set the server configuration options, you must be a member of the **serveradmin** fixed server role or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="ec336-106">Windows 管理员  组的成员可以启动和停止服务，配置 Windows 提供的服务器选项。</span><span class="sxs-lookup"><span data-stu-id="ec336-106">Members of the Windows **Administrators** group can start and stop services and configure the server options that Windows provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec336-107">必须使用正确的域、文件系统和注册表权限配置服务使用的帐户，才能正确操作。</span><span class="sxs-lookup"><span data-stu-id="ec336-107">To operate properly, the accounts used for the services must be configured with the correct domain, file system, and registry permissions.</span></span> <span data-ttu-id="ec336-108">有关所需权限的信息，请参阅 [配置 Windows 服务帐户和权限](configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="ec336-108">For information about the required permissions, see [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md).</span></span>  
  
## <a name="windows-management-instrumentation"></a><span data-ttu-id="ec336-109">Windows Management Instrumentation</span><span class="sxs-lookup"><span data-stu-id="ec336-109">Windows Management Instrumentation</span></span>  
 <span data-ttu-id="ec336-110">SQL Server 配置管理器和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 使用 Windows Management Instrumentation (WMI) 显示和修改某些服务器属性。</span><span class="sxs-lookup"><span data-stu-id="ec336-110">SQL Server Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] use Windows Management Instrumentation (WMI) to display and modify some of the server properties.</span></span> <span data-ttu-id="ec336-111">若要管理服务并获取服务状态，用户必须具有访问 WMI 对象的权限。</span><span class="sxs-lookup"><span data-stu-id="ec336-111">To manage services and obtain the status of the services, the user must have rights to access the WMI object.</span></span> <span data-ttu-id="ec336-112">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，下列服务器属性页使用 WMI：</span><span class="sxs-lookup"><span data-stu-id="ec336-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the following server property pages use WMI:</span></span>  
  
-   <span data-ttu-id="ec336-113">自动启动服务</span><span class="sxs-lookup"><span data-stu-id="ec336-113">Autostart Services</span></span>  
  
-   <span data-ttu-id="ec336-114">引导参数</span><span class="sxs-lookup"><span data-stu-id="ec336-114">Startup Parameters</span></span>  
  
-   <span data-ttu-id="ec336-115">安全性</span><span class="sxs-lookup"><span data-stu-id="ec336-115">Security</span></span>  
  
-   <span data-ttu-id="ec336-116">杂项服务器设置</span><span class="sxs-lookup"><span data-stu-id="ec336-116">Misc Server Settings</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ec336-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ec336-117">Related Tasks</span></span>  
 [<span data-ttu-id="ec336-118">在 SQL Server 工具中将 WMI 配置为显示服务器状态</span><span class="sxs-lookup"><span data-stu-id="ec336-118">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="ec336-119">相关内容</span><span class="sxs-lookup"><span data-stu-id="ec336-119">Related Content</span></span>  
 [<span data-ttu-id="ec336-120">用于配置管理的 WMI 提供程序的概念</span><span class="sxs-lookup"><span data-stu-id="ec336-120">WMI Provider for Configuration Management Concepts</span></span>](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
