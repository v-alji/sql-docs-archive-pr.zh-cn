---
title: 设置用于全文筛选器后台程序启动器的服务帐户 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], FDHOST Launcher (MSSQLFDLauncher) service account
- FDHOST Launcher (MSSQLFDLauncher) [SQL Server]
ms.assetid: 3ab1d101-7ae0-488f-9b57-468e2517b737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d69e68f0b00e760c4b11d1f842f22911ac8dd2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578772"
---
# <a name="set-the-service-account-for-the-full-text-filter-daemon-launcher"></a><span data-ttu-id="1c995-102">设置用于全文筛选器后台程序启动器的服务帐户</span><span class="sxs-lookup"><span data-stu-id="1c995-102">Set the Service Account for the Full-text Filter Daemon Launcher</span></span>
  <span data-ttu-id="1c995-103">本主题介绍如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器为 SQL 全文筛选器后台程序启动器服务 (MSSQLFDLauncher) 设置服务帐户。</span><span class="sxs-lookup"><span data-stu-id="1c995-103">This topic describes how to set the service account for the SQL Full-text Filter Daemon Launcher service (MSSQLFDLauncher) by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="1c995-104">全文搜索 ssNoVersionto 将使用 SQL 全文筛选器后台程序启动器服务来启动筛选器后台程序主机进程，此进程用于处理全文搜索筛选和断字。</span><span class="sxs-lookup"><span data-stu-id="1c995-104">The SQL Full-text Filter Daemon Launcher service is used by full-text search ssNoVersionto start the filter daemon host process, which handles full-text search filtering and word breaking.</span></span> <span data-ttu-id="1c995-105">必须运行此服务才能使用全文搜索。</span><span class="sxs-lookup"><span data-stu-id="1c995-105">This service must be running to use full-text search.</span></span>  
  
 <span data-ttu-id="1c995-106">SQL 全文筛选器后台程序启动器服务是可识别实例的服务，它与特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例相关联。</span><span class="sxs-lookup"><span data-stu-id="1c995-106">The SQL Full-text Filter Daemon Launcher service is an instance-aware service that is associated with a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1c995-107">SQL 全文筛选器后台程序启动器服务将服务帐户信息传播到每个筛选器后台程序主机进程。</span><span class="sxs-lookup"><span data-stu-id="1c995-107">The SQL Full-text Filter Daemon Launcher service propagates the service account information to each filter daemon host process.</span></span>  
  
  
##  <a name="setting-the-service-account"></a><a name="setting"></a><span data-ttu-id="1c995-108">设置服务帐户</span><span class="sxs-lookup"><span data-stu-id="1c995-108">Setting the Service Account</span></span>  
  
#### <a name="to-set-the-sql-full-text-filter-daemon-launcher-service-account-for-full-text-search"></a><span data-ttu-id="1c995-109">为全文搜索设置 SQL 全文筛选器后台程序启动器服务帐户</span><span class="sxs-lookup"><span data-stu-id="1c995-109">To set the SQL Full-text Filter Daemon Launcher service account for full-text search</span></span>  
  
1.  <span data-ttu-id="1c995-110">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="1c995-110">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="1c995-111">在**SQL Server 配置管理器**中，单击 " **SQL Server 服务**"，右键单击 " **SQL 全文筛选器守护程序启动器 (" *`instance name`*) **，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="1c995-111">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click **SQL Full-text Filter Daemon Launcher (*`instance name`*)**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="1c995-112">单击此对话框的“登录”\*\*\*\* 选项卡，选择或输入用于运行由 SQL 全文筛选器后台程序启动器服务创建的每个进程的帐户。</span><span class="sxs-lookup"><span data-stu-id="1c995-112">Click the **Log On** tab of the dialog box, and then select or enter the account under which to run each process created by the SQL Full-text Filter Daemon Launcher service.</span></span>  
  
4.  <span data-ttu-id="1c995-113">关闭此对话框之后，单击“重新启动”\*\*\*\* 以重新启动 SQL 全文筛选器后台程序启动器服务。</span><span class="sxs-lookup"><span data-stu-id="1c995-113">After you close the dialog box, click **Restart** to restart the SQL Full-text Filter Daemon Launcher service.</span></span>  
  
  
##  <a name="if-the-sql-full-text-filter-daemon-launcher-service-does-not-start"></a><a name="error"></a><span data-ttu-id="1c995-114">如果 SQL 全文筛选器守护程序启动器服务未启动</span><span class="sxs-lookup"><span data-stu-id="1c995-114">If the SQL Full-text Filter Daemon Launcher Service Does Not Start</span></span>  
 <span data-ttu-id="1c995-115">如果 SQL 全文筛选器后台程序启动器服务未启动，可能是由以下一种或多种情况引起的：</span><span class="sxs-lookup"><span data-stu-id="1c995-115">If the SQL Full-text Filter Daemon Launcher service does not start, one or more of the following might be the cause:</span></span>  
  
-   <span data-ttu-id="1c995-116">与 SQL 全文筛选器后台程序启动器服务帐户关联的密码已过期。</span><span class="sxs-lookup"><span data-stu-id="1c995-116">The password associated with the SQL Full-text Filter Daemon Launcher service account has expired.</span></span>  
  
     <span data-ttu-id="1c995-117">如果对 SQL 全文筛选器后台程序启动器服务使用本地用户帐户并且您的密码已过期，您需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1c995-117">If you use a local user account for the SQL Full-text Filter Daemon Launcher service and your password expires, you need to:</span></span>  
  
    1.  <span data-ttu-id="1c995-118">为此帐户设置一个新的 Windows 密码。</span><span class="sxs-lookup"><span data-stu-id="1c995-118">Set a new Windows password for the account.</span></span>  
  
    2.  <span data-ttu-id="1c995-119">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，更新 SQL 全文筛选器后台程序启动器服务以便使用新密码。</span><span class="sxs-lookup"><span data-stu-id="1c995-119">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, update the SQL Full-text Filter Daemon Launcher service to use the new password.</span></span>  
  
-   <span data-ttu-id="1c995-120">此服务帐户的用户帐户或密码不正确。</span><span class="sxs-lookup"><span data-stu-id="1c995-120">The user account or password of the service account is incorrect.</span></span>  
  
     <span data-ttu-id="1c995-121">SQL 全文筛选器后台程序启动器服务可能试图以错误的用户帐户和密码登录。</span><span class="sxs-lookup"><span data-stu-id="1c995-121">The SQL Full-text Filter Daemon Launcher service might attempt to log in with an incorrect user account and password.</span></span> <span data-ttu-id="1c995-122">按照上述过程，验证该服务的用户帐户是否发生了更改。</span><span class="sxs-lookup"><span data-stu-id="1c995-122">Follow the procedures above to verify that the user account for the service has not been changed.</span></span>  
  
-   <span data-ttu-id="1c995-123">用来登录到该服务的帐户没有相应的特权。</span><span class="sxs-lookup"><span data-stu-id="1c995-123">The account used to log in to the service does not have privileges.</span></span>  
  
     <span data-ttu-id="1c995-124">您使用的帐户可能对安装该服务器实例的计算机不具有登录特权。</span><span class="sxs-lookup"><span data-stu-id="1c995-124">You might be using an account that does not have login privileges on the computer where the server instance is installed.</span></span> <span data-ttu-id="1c995-125">请验证您用于登录的帐户是否对相应本地计算机具有用户权限。</span><span class="sxs-lookup"><span data-stu-id="1c995-125">Verify that you are logging in with an account that has User rights and permissions on the local computer.</span></span>  
  
-   <span data-ttu-id="1c995-126">相同命名管道的另一个实例已在运行。</span><span class="sxs-lookup"><span data-stu-id="1c995-126">Another instance of the same named pipe is already running.</span></span>  
  
     <span data-ttu-id="1c995-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务充当 SQL 全文筛选器后台程序启动器服务客户端的命名管道服务器。</span><span class="sxs-lookup"><span data-stu-id="1c995-127">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service acts as a named pipe server for the SQL Full-text Filter Daemon Launcher service client.</span></span> <span data-ttu-id="1c995-128">如果在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动之前另一进程便已创建该命名管道，则将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和 Windows 事件日志中记录一条错误，并且将无法使用全文搜索。</span><span class="sxs-lookup"><span data-stu-id="1c995-128">If the named pipe was already created by another process before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts, an error will be logged in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the Windows Event Log, and full-text search will not be available.</span></span>  <span data-ttu-id="1c995-129">确定哪个进程或应用程序在试图使用该命名管道并停止相应的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1c995-129">Determine what process or application is attempting to use the same named pipe and stop the application.</span></span>  
  
-   <span data-ttu-id="1c995-130">未正确地配置 SQL 全文筛选器后台程序启动器服务。</span><span class="sxs-lookup"><span data-stu-id="1c995-130">The SQL Full-text Filter Daemon Launcher service is not configured correctly.</span></span>  
  
     <span data-ttu-id="1c995-131">该服务在本地计算机上的配置可能不正确。</span><span class="sxs-lookup"><span data-stu-id="1c995-131">The service may not be configured correctly on the local computer.</span></span>  
  
     <span data-ttu-id="1c995-132">如果本地计算机已禁用命名管道功能，或者已将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用非默认命名管道，则 SQL 全文筛选器后台程序启动器服务可能无法启动。</span><span class="sxs-lookup"><span data-stu-id="1c995-132">If named pipes functionality has been disabled on the local computer, or if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been configured to use a named pipe other than the default named pipe, the SQL Full-text Filter Daemon Launcher service might not start.</span></span>  
  
-   <span data-ttu-id="1c995-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务组没有启动 SQL 全文筛选器后台程序启动器服务的权限。</span><span class="sxs-lookup"><span data-stu-id="1c995-133">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group does not have permission to start SQL Full-text Filter Daemon Launcher service.</span></span>  
  
     <span data-ttu-id="1c995-134">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的安装过程中，向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务组授予了管理、查询和启动 SQL 全文筛选器后台程序启动器服务的默认权限。</span><span class="sxs-lookup"><span data-stu-id="1c995-134">During the installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group is granted default permission to manage, query, and start the SQL Full-text Filter Daemon Launcher service.</span></span> <span data-ttu-id="1c995-135">如果在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 后删除了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务组对 SQL 全文筛选器后台程序启动器服务帐户的权限，则 SQL 全文筛选器后台程序启动器服务将无法启动，并且全文搜索也将被禁用。</span><span class="sxs-lookup"><span data-stu-id="1c995-135">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group permissions to the SQL Full-text Filter Daemon Launcher service account have been removed after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, the SQL Full-text Filter Daemon Launcher service will not start, and full-text search will be disabled.</span></span> <span data-ttu-id="1c995-136">请确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务组拥有对 SQL 全文筛选器后台程序启动器服务帐户的权限。</span><span class="sxs-lookup"><span data-stu-id="1c995-136">Make certain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group has permissions to the SQL Full-text Filter Daemon Launcher service account.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="1c995-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c995-137">See Also</span></span>  
 [<span data-ttu-id="1c995-138">管理服务操作指南主题（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="1c995-138">Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;</span></span>](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)  
 [<span data-ttu-id="1c995-139">升级全文搜索</span><span class="sxs-lookup"><span data-stu-id="1c995-139">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)  
  
  
