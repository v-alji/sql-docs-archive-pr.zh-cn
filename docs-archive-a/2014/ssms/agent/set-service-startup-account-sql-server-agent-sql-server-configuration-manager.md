---
title: 将 SQL Server 代理 (SQL Server 配置管理器的服务启动帐户设置) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: stevestein
ms.author: sstein
ms.openlocfilehash: 63e5ba7c24f1aa1a3f79f80e5ca28c02a0cd5812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689235"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a><span data-ttu-id="4a51b-102">为 SQL Server 代理设置服务启动帐户（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="4a51b-102">Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="4a51b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务启动帐户定义了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在运行时所用的 Windows 帐户及其网络权限。</span><span class="sxs-lookup"><span data-stu-id="4a51b-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account defines the Windows account that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs as, as well as its network permissions.</span></span> <span data-ttu-id="4a51b-104">本主题说明了如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中通过 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 配置管理器设置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]代理服务帐户。</span><span class="sxs-lookup"><span data-stu-id="4a51b-104">This topic describes how to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4a51b-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4a51b-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4a51b-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4a51b-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4a51b-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="4a51b-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4a51b-108">安全性</span><span class="sxs-lookup"><span data-stu-id="4a51b-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="4a51b-109">使用 SQL Server Management Studio 为 SQL Server 代理设置服务启动帐户</span><span class="sxs-lookup"><span data-stu-id="4a51b-109">To set the Service Startup Account for SQL Server Agent using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4a51b-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="4a51b-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4a51b-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="4a51b-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4a51b-112">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]开始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理不再要求服务启动帐户为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="4a51b-112">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer requires that the service startup account be a member of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators group.</span></span> <span data-ttu-id="4a51b-113">但是， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务启动帐户必须是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="4a51b-113">However, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service startup account must be a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin fixed server role.</span></span> <span data-ttu-id="4a51b-114">如果使用多服务器作业处理，帐户还必须是主服务器上 msdb 数据库角色 TargetServersRole 的成员。</span><span class="sxs-lookup"><span data-stu-id="4a51b-114">The account must also be a member of the msdb database role TargetServersRole on the master server if multiserver job processing is used.</span></span>  
  
-   <span data-ttu-id="4a51b-115">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="4a51b-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4a51b-116">Security</span><span class="sxs-lookup"><span data-stu-id="4a51b-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4a51b-117">权限</span><span class="sxs-lookup"><span data-stu-id="4a51b-117">Permissions</span></span>  
 <span data-ttu-id="4a51b-118">若要执行其功能， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必须将代理配置为使用作为 `sysadmin` 中固定服务器角色的成员的帐户的凭据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4a51b-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the `sysadmin` fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4a51b-119">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="4a51b-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="4a51b-120">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="4a51b-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="4a51b-121">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4a51b-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="4a51b-122">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4a51b-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="4a51b-123">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4a51b-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="4a51b-124">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="4a51b-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4a51b-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4a51b-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a><span data-ttu-id="4a51b-126">为 SQL Server 代理设置服务启动帐户</span><span class="sxs-lookup"><span data-stu-id="4a51b-126">To set the Service Startup Account for SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="4a51b-127">在 **“已注册的服务器”** 中，单击加号以便展开 **“数据库引擎”**。</span><span class="sxs-lookup"><span data-stu-id="4a51b-127">In **Registered Servers**, click the plus sign to expand **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="4a51b-128">单击加号以便展开 **“本地服务器组”** 文件集。</span><span class="sxs-lookup"><span data-stu-id="4a51b-128">Click the plus sign to expand the **Local Server Groups** folder.</span></span>  
  
3.  <span data-ttu-id="4a51b-129">右键单击要设置服务启动帐户的服务器实例，然后选择“SQL Server 配置管理器…”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a51b-129">Right-click the server instance where you want set up the Service Startup Account, and select **SQL Server Configuration Manager...**.</span></span>  
  
4.  <span data-ttu-id="4a51b-130">在“用户帐户控制”对话框中，单击“是”。</span><span class="sxs-lookup"><span data-stu-id="4a51b-130">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="4a51b-131">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器的控制台窗格中，选择 **“SQL Server 服务”**。</span><span class="sxs-lookup"><span data-stu-id="4a51b-131">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, select **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="4a51b-132">在详细信息窗格中，右键单击 " **SQL Server 代理**_ (server_name") _"，其中*server_name*是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要更改其服务启动帐户的代理实例的名称，然后选择"**属性**"。</span><span class="sxs-lookup"><span data-stu-id="4a51b-132">In the details pane, right-click **SQL Server Agent**_(server_name)_, where *server_name* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance for which you want to change the service startup account, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="4a51b-133">在 " **SQL Server 代理**_ (server_name) _ **属性**" 对话框的 "**登录**" 选项卡中，选择 "**登录身份**" 下的以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="4a51b-133">In the **SQL Server Agent**_(server_name)_ **Properties** dialog box, in the **Log On** tab, select one of the following options under **Log on as**:</span></span>  
  
    -   <span data-ttu-id="4a51b-134">**内置帐户**：如果你的作业仅需要本地服务器中的资源，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="4a51b-134">**Built-in account**: select this option if your jobs require resources from the local server only.</span></span> <span data-ttu-id="4a51b-135">有关如何选择 Windows 内置帐户类型的信息，请参阅 [为 SQL Server 代理服务选择帐户](https://msdn.microsoft.com/library/ms191543.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4a51b-135">For information about how to choose a Windows built-in account type, see [Selecting an Account for SQL Server Agent Service.](https://msdn.microsoft.com/library/ms191543.aspx)</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="4a51b-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务不支持 \*\*\*\* 中的 Local Service [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]帐户。</span><span class="sxs-lookup"><span data-stu-id="4a51b-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service does not support the **Local Service** account in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="4a51b-137">**本帐户**：如果作业需要网络上的资源（包括应用程序资源），如果要将事件转发到其他 Windows 应用程序日志，或者如果要通过电子邮件或寻呼程序来通知操作员，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="4a51b-137">**This account**: select this option if your jobs require resources across the network, including application resources; if you want to forward events to other Windows application logs; or if you want to notify operators through e-mail or pagers.</span></span>  
  
         <span data-ttu-id="4a51b-138">如果您选择此选项：</span><span class="sxs-lookup"><span data-stu-id="4a51b-138">If you select this option:</span></span>  
  
        1.  <span data-ttu-id="4a51b-139">在 **“帐户名称”** 框中，输入将用来运行 SQL Server 代理的帐户。</span><span class="sxs-lookup"><span data-stu-id="4a51b-139">In the **Account Name** box, enter the account that will be used to run SQL Server Agent.</span></span> <span data-ttu-id="4a51b-140">或者，单击 **“浏览”** 打开 **“选择用户或组”** 对话框并选择要使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="4a51b-140">Alternately, click **Browse** to open the **Select User or Group** dialog box and select the account to use.</span></span>  
  
        2.  <span data-ttu-id="4a51b-141">在 **“密码”** 框中，输入帐户密码。</span><span class="sxs-lookup"><span data-stu-id="4a51b-141">In the **Password** box, enter the password for the account.</span></span> <span data-ttu-id="4a51b-142">在“确认密码”\*\*\*\* 框中重新输入密码。</span><span class="sxs-lookup"><span data-stu-id="4a51b-142">Re-enter the password in the **Confirm password** box.</span></span>  
  
8.  <span data-ttu-id="4a51b-143">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="4a51b-143">Click **OK**.</span></span>  
  
9. <span data-ttu-id="4a51b-144">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，单击 **“关闭”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4a51b-144">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click the **Close** button.</span></span>  
  
  
