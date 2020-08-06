---
title: MSSQLSERVER_21879 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21879 (Database Engine error)
ms.assetid: fcfab735-05ca-423a-89f1-fdee7e2ed8c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 08c5d4f45faf94d555ed7acedd90cc55ec4791ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690626"
---
# <a name="mssqlserver_21879"></a><span data-ttu-id="79bc7-102">MSSQLSERVER_21879</span><span class="sxs-lookup"><span data-stu-id="79bc7-102">MSSQLSERVER_21879</span></span>
    
## <a name="details"></a><span data-ttu-id="79bc7-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="79bc7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79bc7-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="79bc7-104">Product Name</span></span>|<span data-ttu-id="79bc7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="79bc7-105">SQL Server</span></span>|  
|<span data-ttu-id="79bc7-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="79bc7-106">Event ID</span></span>|<span data-ttu-id="79bc7-107">21879</span><span class="sxs-lookup"><span data-stu-id="79bc7-107">21879</span></span>|  
|<span data-ttu-id="79bc7-108">事件源</span><span class="sxs-lookup"><span data-stu-id="79bc7-108">Event Source</span></span>|<span data-ttu-id="79bc7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="79bc7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="79bc7-110">组件</span><span class="sxs-lookup"><span data-stu-id="79bc7-110">Component</span></span>|<span data-ttu-id="79bc7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="79bc7-111">SQLEngine</span></span>|  
|<span data-ttu-id="79bc7-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="79bc7-112">Symbolic Name</span></span>|<span data-ttu-id="79bc7-113">SQLErrorNum21879</span><span class="sxs-lookup"><span data-stu-id="79bc7-113">SQLErrorNum21879</span></span>|  
|<span data-ttu-id="79bc7-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="79bc7-114">Message Text</span></span>|<span data-ttu-id="79bc7-115">无法查询重定向服务器“%s”以找到原始发布服务器“%s”和发布服务器数据库“%s”来确定远程服务器的名称；错误 %d，错误消息“%s”。</span><span class="sxs-lookup"><span data-stu-id="79bc7-115">Unable to query the redirected server '%s' for original publisher '%s' and publisher database '%s' to determine the name of the remote server; Error %d, Error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="79bc7-116">说明</span><span class="sxs-lookup"><span data-stu-id="79bc7-116">Explanation</span></span>  
 <span data-ttu-id="79bc7-117">`sp_validate_redirected_publisher` 使用其创建的临时链接服务器连接到重定向发布服务器，以便发现远程服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="79bc7-117">`sp_validate_redirected_publisher` uses a temporary linked server that it creates to connect to the redirected publisher in order to discover the name of the remote server.</span></span> <span data-ttu-id="79bc7-118">在链接服务器查询失败时，将返回错误 21879。</span><span class="sxs-lookup"><span data-stu-id="79bc7-118">Error 21879 is returned when the linked server query fails.</span></span> <span data-ttu-id="79bc7-119">对请求远程服务器名称的调用通常是首次使用临时链接服务器，因此如果存在连接问题，则这些问题可能首先会与此调用一起出现。</span><span class="sxs-lookup"><span data-stu-id="79bc7-119">The call to request the remote server name is typically the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with this call.</span></span> <span data-ttu-id="79bc7-120">在远程服务器上，此远程调用只执行选择 `@@servername`。</span><span class="sxs-lookup"><span data-stu-id="79bc7-120">This remote call simply executes select `@@servername` at the remote server.</span></span>  
  
 <span data-ttu-id="79bc7-121">用于查询重定向发布服务器的链接服务器使用在为原始发布服务器调用 `sp_adddistpublisher` 时提供的安全模式、登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="79bc7-121">The linked server used to query the redirected publisher uses the security mode, login, and password supplied when `sp_adddistpublisher` was called for the original publisher.</span></span>  
  
-   <span data-ttu-id="79bc7-122">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证（安全模式 0），则使用指定的登录名和密码连接到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="79bc7-122">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication was used (security mode 0) then the login and password specified are used to connect to the remote server.</span></span>  
  
-   <span data-ttu-id="79bc7-123">如果使用 Windows 身份验证（安全模式 1），则对此连接使用可信连接。</span><span class="sxs-lookup"><span data-stu-id="79bc7-123">If Windows authentication was used (security mode 1) a trusted connection is used for the connection.</span></span>  
  
    -   <span data-ttu-id="79bc7-124">如果 `sp_validate_redirected_publisher` 被用户显式调用，则用户运行时所使用的 Windows 登录名将用于该连接。</span><span class="sxs-lookup"><span data-stu-id="79bc7-124">If `sp_validate_redirected_publisher` is called explicitly by a user, the Windows login that the user is running under is used for the connection.</span></span>  
  
    -   <span data-ttu-id="79bc7-125">如果复制代理从 `sp_validate_redirected_` 中调用 `sp_get_redirected_publisher` 发布服务器，则将使用与该代理关联的 Windows 登录名。</span><span class="sxs-lookup"><span data-stu-id="79bc7-125">If `sp_validate_redirected_`publisher is called by a replication agent from `sp_get_redirected_publisher`, the Windows login associated with the agent is used.</span></span>  
  
 <span data-ttu-id="79bc7-126">错误 21879 可能指示在重定向目标发布服务器上使用未知的登录名调用了 `sp_validate_redirected_publisher`。</span><span class="sxs-lookup"><span data-stu-id="79bc7-126">Error 21879 can indicate that `sp_validate_redirected_publisher` was called using a login that is not known at the redirected target publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="79bc7-127">用户操作</span><span class="sxs-lookup"><span data-stu-id="79bc7-127">User Action</span></span>  
 <span data-ttu-id="79bc7-128">请确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录名或 Windows 身份验证登录名对所有可用性组副本都有效，并具有足够的权限，可访问发布服务器数据库中的订阅元数据表（syssubscriptions 和 sysmergesubscriptions）。</span><span class="sxs-lookup"><span data-stu-id="79bc7-128">Make certain that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication login or the Windows authentication login is valid at all of the availability group replicas and has sufficient authorization to access the subscription metadata tables (syssubscriptions and sysmergesubscriptions) in the publisher database.</span></span>  
  
 <span data-ttu-id="79bc7-129">如果由非分发服务器的其他节点上运行的复制代理（如在订阅服务器上运行的合并代理）启动的 `sp_get_redirected_publisher` 调用返回了错误 21879，则应注意一些特殊事项。</span><span class="sxs-lookup"><span data-stu-id="79bc7-129">There are special considerations when error 21879 is returned from a call to `sp_get_redirected_publisher` that is initiated by a replication agent running on a node other that the distributor; such as a merge agent running at a subscriber.</span></span> <span data-ttu-id="79bc7-130">如果使用 Windows 身份验证连接到重定向发布服务器，则必须将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用 Kerberos 身份验证以便成功建立连接。</span><span class="sxs-lookup"><span data-stu-id="79bc7-130">If Windows authentication is used for the connection to the redirected publisher, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured for Kerberos authentication for the connection to be successfully established.</span></span> <span data-ttu-id="79bc7-131">当使用 Windows 身份验证且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未配置为使用 Kerberos 身份验证时，在订阅服务器上运行的合并代理将收到错误 18456，指示“NT AUTHORITY\ANONYMOUS LOGON”登录名失败。</span><span class="sxs-lookup"><span data-stu-id="79bc7-131">When Windows authentication is used and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not configured for Kerberos authentication, error 18456 indicating that the 'NT AUTHORITY\ANONYMOUS LOGON' login failed, is received by a merge agent running at a subscriber.</span></span> <span data-ttu-id="79bc7-132">可以通过三种方式解决此问题：</span><span class="sxs-lookup"><span data-stu-id="79bc7-132">There are three possible ways to address this issue:</span></span>  
  
-   <span data-ttu-id="79bc7-133">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="79bc7-133">Configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Kerberos authentication.</span></span> <span data-ttu-id="79bc7-134">请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的 **Kerberos 身份验证和 SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="79bc7-134">See **Kerberos Authentication and SQL Server** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="79bc7-135">使用 `sp_changedistpublisher` 更改与 MSdistpublishers 中的原始发布服务器相关联的安全模式，以及指定用于连接的登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="79bc7-135">Use `sp_changedistpublisher` to change the security mode associated with the original publisher in MSdistpublishers, as well as to specify a login and password to use for the connection.</span></span>  
  
-   <span data-ttu-id="79bc7-136">指定在合并代理命令行上的命令行参数*BypassPublisherValidation*在分发服务器上调用时绕过验证 `sp_get_redirected_publisher` 。</span><span class="sxs-lookup"><span data-stu-id="79bc7-136">Specify the command line parameter *BypassPublisherValidation* on the merge agent command line to bypass validation when `sp_get_redirected_publisher` is called at the distributor.</span></span>  
  
  
