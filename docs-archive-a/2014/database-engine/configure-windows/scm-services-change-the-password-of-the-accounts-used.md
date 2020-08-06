---
title: 将 SQL Server (使用的帐户的密码更改 SQL Server 配置管理器) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7da2b5f60187d7e3060dc6616686c493c893c21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694126"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="24d11-102">更改 SQL Server 使用的帐户的密码（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="24d11-102">Change the Password of the Accounts Used by SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="24d11-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 代理使用的帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="24d11-103">This topic describes how to change the password of the accounts used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="24d11-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作为服务在计算机上运行，并使用最初在设置期间提供的凭据。</span><span class="sxs-lookup"><span data-stu-id="24d11-104">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent run on a computer as a service using credentials that are initially provided during setup.</span></span> <span data-ttu-id="24d11-105">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例使用域帐户运行但此帐户的密码已更改，则必须将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所用的密码更新为新密码。</span><span class="sxs-lookup"><span data-stu-id="24d11-105">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running under a domain account and the password for that account is changed, the password used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be updated to the new password.</span></span> <span data-ttu-id="24d11-106">如果不更新密码， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能无法访问某些域资源；如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 停止，则在更新密码后才能重新启动该服务。</span><span class="sxs-lookup"><span data-stu-id="24d11-106">If the password is not updated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may lose access to some domain resources and if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops, the service will not restart until the password is updated.</span></span>  
  
 <span data-ttu-id="24d11-107">若要更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证密码，请参阅 [密码已过期](../password-expired.md)。</span><span class="sxs-lookup"><span data-stu-id="24d11-107">To change [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication passwords, see [Password Expired](../password-expired.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="24d11-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="24d11-108">Before You Begin</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="24d11-109">配置管理器是为更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务设置而设计和授权使用的工具。</span><span class="sxs-lookup"><span data-stu-id="24d11-109">Configuration Manager is the tool designed and authorized to change the settings of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="24d11-110">使用 Windows 服务控制管理器 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.msc **) 应用程序更改**服务不总是更改所有必要设置，并且可能会阻止服务正常运行。</span><span class="sxs-lookup"><span data-stu-id="24d11-110">Changing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service by using the Windows Service Control Manager (**services.msc**) application does not always change all of the necessary settings and might prevent the service from functioning properly.</span></span> <span data-ttu-id="24d11-111">但是在群集环境中，在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器更改活动节点上的密码之后，您必须使用服务控制管理器来更改被动节点上的密码。</span><span class="sxs-lookup"><span data-stu-id="24d11-111">However, in a clustered environment, after changing the password on the active node by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, you must change the password on the passive node by using the Service Control Manager.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="24d11-112">Security</span><span class="sxs-lookup"><span data-stu-id="24d11-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="24d11-113">权限</span><span class="sxs-lookup"><span data-stu-id="24d11-113">Permissions</span></span>  
 <span data-ttu-id="24d11-114">您必须是计算机管理员才能更改服务所用的密码。</span><span class="sxs-lookup"><span data-stu-id="24d11-114">You must be an administrator of the computer to change the password used by a service.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="24d11-115">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="24d11-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a><span data-ttu-id="24d11-116">更改 SQL Server（数据库引擎）服务所用的密码</span><span class="sxs-lookup"><span data-stu-id="24d11-116">To change the password used by the SQL Server (Database Engine) service</span></span>  
  
1.  <span data-ttu-id="24d11-117">单击 **“开始”** 按钮，依次指向 **“所有程序”** 、“ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]”和 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="24d11-117">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="24d11-118">因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理控制台程序的一个管理单元而不是单独的程序，所以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器在新版本的 Windows 中不显示为一个应用程序。</span><span class="sxs-lookup"><span data-stu-id="24d11-118">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="24d11-119">**Windows 10**：</span><span class="sxs-lookup"><span data-stu-id="24d11-119">**Windows 10**:</span></span>  
    >          <span data-ttu-id="24d11-120">若要打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，请在 "**开始" 页**上，键入) 的 sqlservermanager12.msc ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="24d11-120">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="24d11-121">对于早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请将 12 替换为较小的数字。</span><span class="sxs-lookup"><span data-stu-id="24d11-121">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="24d11-122">单击 SQLServerManager12.msc 可打开“配置管理器”。</span><span class="sxs-lookup"><span data-stu-id="24d11-122">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="24d11-123">若要将 Configuration Manager 固定到 "起始页" 或 "任务栏"，请右键单击 "Sqlservermanager12.msc"，然后单击 "**打开文件位置**"。</span><span class="sxs-lookup"><span data-stu-id="24d11-123">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="24d11-124">在 Windows 文件资源管理器中，右键单击 "Sqlservermanager12.msc"，然后单击 "**固定到\*\*\*\*任务栏**"。</span><span class="sxs-lookup"><span data-stu-id="24d11-124">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="24d11-125">**Windows 8**：</span><span class="sxs-lookup"><span data-stu-id="24d11-125">**Windows 8**:</span></span>  
    >          <span data-ttu-id="24d11-126">若要打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager，请在 "**搜索**" 超级按钮中的 "**应用**" 下，键入**sqlservermanager version>.msc （ \<version> **如 `SQLServerManager12.msc` ），然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="24d11-126">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="24d11-127">在 SQL Server 配置管理器中，单击 **“SQL Server 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="24d11-127">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="24d11-128">在“详细信息”窗格中，右键单击“SQL Server (\<instancename> )”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="24d11-128">In the details pane, right-click **SQL Server (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="24d11-129">在“SQL Server (\<instancename>) 属性” 对话框中的“登录”选项卡上，对于“帐户名”框中列出的帐户，在“密码”框和“确认密码”框中键入新密码，然后单击“确定”   。</span><span class="sxs-lookup"><span data-stu-id="24d11-129">In the **SQL Server (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="24d11-130">密码会立即生效，而不需要重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24d11-130">The password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a><span data-ttu-id="24d11-131">更改 SQL Server 代理服务所用的密码</span><span class="sxs-lookup"><span data-stu-id="24d11-131">To change the password used by the SQL Server Agent service</span></span>  
  
1.  <span data-ttu-id="24d11-132">单击 **“开始”** 按钮，依次指向 **“所有程序”** 、“ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]”和 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="24d11-132">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="24d11-133">在 SQL Server 配置管理器中，单击 **“SQL Server 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="24d11-133">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="24d11-134">在“详细信息”窗格中，右键单击“SQL Server 代理(\<instancename> )”，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="24d11-134">In the details pane, right-click **SQL Server Agent (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="24d11-135">在“SQL Server 代理(\<instancename>)属性”对话框中的“登录”选项卡上，对于“帐户名”框中列出的帐户，在“密码”框和“确认密码”框中键入新密码，然后单击“确定”     。</span><span class="sxs-lookup"><span data-stu-id="24d11-135">In the **SQL Server Agent (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="24d11-136">在独立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上，密码会立即生效，无需重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24d11-136">On a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="24d11-137">在群集实例上， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能会使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源脱机，并需要重新启动。</span><span class="sxs-lookup"><span data-stu-id="24d11-137">On a clustered instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might take the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource offline, and require a restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d11-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24d11-138">See Also</span></span>  
 [<span data-ttu-id="24d11-139">管理服务操作指南主题（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="24d11-139">Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;</span></span>](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
