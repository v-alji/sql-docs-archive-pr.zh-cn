---
title: 为 SQL Server 代理服务选择帐户 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, accounts
- startup accounts [SQL Server]
- SQL Server Agent service, accounts
- accounts [SQL Server], SQL Server Agent
- Windows groups [SQL Server Agent]
- SQL Server Agent, permissions
- members [SQL Server], SQL Server Agent service
- Windows domain accounts [SQL Server]
- security [SQL Server], SQL Server Agent
ms.assetid: fe658e32-9e6b-4147-a189-7adc3bd28fe7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 25e470bb8bde192d05a078a77fce71850c641854
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691491"
---
# <a name="select-an-account-for-the-sql-server-agent-service"></a><span data-ttu-id="25abe-102">为 SQL Server 代理服务选择帐户</span><span class="sxs-lookup"><span data-stu-id="25abe-102">Select an Account for the SQL Server Agent Service</span></span>
  <span data-ttu-id="25abe-103">服务启动帐户可以定义运行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 代理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 帐户及其网络权限。</span><span class="sxs-lookup"><span data-stu-id="25abe-103">The service startup account defines the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account in which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs and its network permissions.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="25abe-104">代理在指定的用户帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="25abe-104">Agent runs as a specified user account.</span></span> <span data-ttu-id="25abe-105">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务选择一个帐户，可选帐户如下：</span><span class="sxs-lookup"><span data-stu-id="25abe-105">You select an account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, where you can choose from the following options:</span></span>  
  
-   <span data-ttu-id="25abe-106">**内置帐户**。</span><span class="sxs-lookup"><span data-stu-id="25abe-106">**Built-in account**.</span></span> <span data-ttu-id="25abe-107">可以从下列内置 Windows 服务帐户的列表中选择：</span><span class="sxs-lookup"><span data-stu-id="25abe-107">You can choose from a list of the following built-in Windows service accounts:</span></span>  
  
    -   <span data-ttu-id="25abe-108">**本地系统**帐户。</span><span class="sxs-lookup"><span data-stu-id="25abe-108">**Local System** account.</span></span> <span data-ttu-id="25abe-109">此帐户的名称是 NT AUTHORITY\System。</span><span class="sxs-lookup"><span data-stu-id="25abe-109">The name of this account is NT AUTHORITY\System.</span></span> <span data-ttu-id="25abe-110">它是一个功能强大的帐户，可以不受限制地访问所有本地系统资源。</span><span class="sxs-lookup"><span data-stu-id="25abe-110">It is a powerful account that has unrestricted access to all local system resources.</span></span> <span data-ttu-id="25abe-111">它是本地计算机上 Windows“管理员”\*\*\*\* 组的成员，因此也是  sysadmin[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \*\*\*\* 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="25abe-111">It is a member of the Windows **Administrators** group on the local computer, and is therefore a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin** fixed server role</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="25abe-112">提供“Local System 帐户”\*\*\*\* 选项只是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="25abe-112">The **Local System account** option is provided for backward compatibility only.</span></span> <span data-ttu-id="25abe-113">本地系统帐户具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理不需要的权限。</span><span class="sxs-lookup"><span data-stu-id="25abe-113">The Local System account has permissions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not require.</span></span> <span data-ttu-id="25abe-114">避免使用本地系统帐户运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="25abe-114">Avoid running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent as the Local System account.</span></span> <span data-ttu-id="25abe-115">为了提高安全性，请使用具有下面部分“Windows 域帐户权限”中所列出权限的 Windows 域帐户。</span><span class="sxs-lookup"><span data-stu-id="25abe-115">For improved security, use a Windows domain account with the permissions listed in the following section, "Windows Domain Account Permissions."</span></span>  
  
-   <span data-ttu-id="25abe-116">**此帐户**。</span><span class="sxs-lookup"><span data-stu-id="25abe-116">**This account**.</span></span> <span data-ttu-id="25abe-117">使您可以指定运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的 Windows 域帐户。</span><span class="sxs-lookup"><span data-stu-id="25abe-117">Lets you specify the Windows domain account in which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs.</span></span> <span data-ttu-id="25abe-118">建议选择非 Windows **管理员** 组成员的 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="25abe-118">We recommend choosing a Windows user account that is not a member of the Windows **Administrators** group.</span></span> <span data-ttu-id="25abe-119">但是，当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户不是本地 **管理员** 组的成员时，在使用多服务器管理时存在限制。</span><span class="sxs-lookup"><span data-stu-id="25abe-119">However, there are limitations for using multiserver administration when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account is not a member of the local **Administrators** group.</span></span> <span data-ttu-id="25abe-120">有关详细信息，请参阅本主题后面的“支持的服务帐户类型”。</span><span class="sxs-lookup"><span data-stu-id="25abe-120">For more information, see 'Supported Service Account Types' that follows in this topic.</span></span>  
  
## <a name="windows-domain-account-permissions"></a><span data-ttu-id="25abe-121">Windows 域帐户权限</span><span class="sxs-lookup"><span data-stu-id="25abe-121">Windows Domain Account Permissions</span></span>  
 <span data-ttu-id="25abe-122">为了提高安全性，可以选择“本帐户”\*\*\*\* 来指定 Windows 域帐户。</span><span class="sxs-lookup"><span data-stu-id="25abe-122">For improved security, select **This account**, which specifies a Windows domain account.</span></span> <span data-ttu-id="25abe-123">指定的 Windows 域帐户必须具有下列权限：</span><span class="sxs-lookup"><span data-stu-id="25abe-123">The Windows domain account that you specify must have the following permissions:</span></span>  
  
-   <span data-ttu-id="25abe-124">在所有 Windows 版本中，作为服务登录的权限 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="25abe-124">In all Windows versions, permission to log on as a service (SeServiceLogonRight)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25abe-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户必须是域控制器上 Pre-Windows 2000 Compatible Access 组的一部分，否则，非 Windows Administrators 组成员的域用户拥有的作业将失败。</span><span class="sxs-lookup"><span data-stu-id="25abe-125">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account must be part of the Pre-Windows 2000 Compatible Access group on the domain controller, or jobs that are owned by domain users who are not members of the Windows Administrators group will fail.</span></span>  
  
-   <span data-ttu-id="25abe-126">在 Windows 服务器中，运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的帐户需要具有下列权限才能支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="25abe-126">In Windows servers, the account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service runs as requires the following permissions to be able to support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxies.</span></span>  
  
    -   <span data-ttu-id="25abe-127">跳过遍历检查的权限 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="25abe-127">Permission to bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
    -   <span data-ttu-id="25abe-128">替换进程级别标记的权限 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="25abe-128">Permission to replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
    -   <span data-ttu-id="25abe-129">调整进程的内存配额的权限 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="25abe-129">Permission to adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
    -   <span data-ttu-id="25abe-130">使用批登录类型登录的权限 (SeBatchLogonRight)</span><span class="sxs-lookup"><span data-stu-id="25abe-130">Permission to log on using the batch logon type (SeBatchLogonRight)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25abe-131">如果帐户不具有支持代理帐户所需的权限，则只有 **sysadmin** 固定服务器角色的成员才可创建作业。</span><span class="sxs-lookup"><span data-stu-id="25abe-131">If the account does not have the permissions required to support proxies, only members of the **sysadmin** fixed server role can create jobs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25abe-132">必须为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的服务帐户授予包含 WMI 事件的命名空间的权限以及 ALTER ANY EVENT NOTIFICATION 权限，才能接收 WMI 警报通知。</span><span class="sxs-lookup"><span data-stu-id="25abe-132">To receive WMI alert notification, the service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must have been granted permission to the namespace that contains the WMI events, and ALTER ANY EVENT NOTIFICATION.</span></span>  
  
## <a name="sql-server-role-membership"></a><span data-ttu-id="25abe-133">SQL Server 角色成员身份</span><span class="sxs-lookup"><span data-stu-id="25abe-133">SQL Server Role Membership</span></span>  
 <span data-ttu-id="25abe-134">运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务时使用的帐户必须是下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 角色的成员：</span><span class="sxs-lookup"><span data-stu-id="25abe-134">The account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs as must be a member of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] roles:</span></span>  
  
-   <span data-ttu-id="25abe-135">该帐户必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="25abe-135">The account must be a member of the **sysadmin** fixed server role.</span></span>  
  
-   <span data-ttu-id="25abe-136">若要使用多服务器作业处理，帐户必须是主服务器上 **msdb** 数据库角色 **TargetServersRole** 的成员。</span><span class="sxs-lookup"><span data-stu-id="25abe-136">To use multiserver job processing, the account must be a member of the **msdb** database role **TargetServersRole** on the master server.</span></span>  
  
## <a name="supported-service-account-types"></a><span data-ttu-id="25abe-137">支持的服务帐户类型</span><span class="sxs-lookup"><span data-stu-id="25abe-137">Supported Service Account Types</span></span>  
 <span data-ttu-id="25abe-138">下表列出了可用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的 Windows 帐户类型。</span><span class="sxs-lookup"><span data-stu-id="25abe-138">The following table lists the Windows account types that can be used for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
|<span data-ttu-id="25abe-139">服务帐户类型</span><span class="sxs-lookup"><span data-stu-id="25abe-139">Service account type</span></span>|<span data-ttu-id="25abe-140">非聚集服务器</span><span class="sxs-lookup"><span data-stu-id="25abe-140">Nonclustered Server</span></span>|<span data-ttu-id="25abe-141">群集服务器</span><span class="sxs-lookup"><span data-stu-id="25abe-141">Clustered server</span></span>|<span data-ttu-id="25abe-142">域控制器（非聚集）</span><span class="sxs-lookup"><span data-stu-id="25abe-142">Domain controller (nonclustered)</span></span>|  
|--------------------------|---------------------------|----------------------|------------------------------------------|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="25abe-143">Windows 域帐户（Windows 管理员组的成员）</span><span class="sxs-lookup"><span data-stu-id="25abe-143">Windows domain account (member of Windows Administrators group)</span></span>|<span data-ttu-id="25abe-144">支持</span><span class="sxs-lookup"><span data-stu-id="25abe-144">Supported</span></span>|<span data-ttu-id="25abe-145">支持</span><span class="sxs-lookup"><span data-stu-id="25abe-145">Supported</span></span>|<span data-ttu-id="25abe-146">支持</span><span class="sxs-lookup"><span data-stu-id="25abe-146">Supported</span></span>|  
|<span data-ttu-id="25abe-147">Windows 域帐户（非管理）</span><span class="sxs-lookup"><span data-stu-id="25abe-147">Windows domain account (non-administrative)</span></span>|<span data-ttu-id="25abe-148">支持<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="25abe-148">Supported<sup>1</sup></span></span>|<span data-ttu-id="25abe-149">支持<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="25abe-149">Supported<sup>1</sup></span></span>|<span data-ttu-id="25abe-150">支持<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="25abe-150">Supported<sup>1</sup></span></span>|  
|<span data-ttu-id="25abe-151">网络服务帐户 (NT AUTHORITY\NetworkService)</span><span class="sxs-lookup"><span data-stu-id="25abe-151">Network Service account (NT AUTHORITY\NetworkService)</span></span>|<span data-ttu-id="25abe-152">支持<sup>1、3、4</sup></span><span class="sxs-lookup"><span data-stu-id="25abe-152">Supported<sup>1, 3, 4</sup></span></span>|<span data-ttu-id="25abe-153">不支持</span><span class="sxs-lookup"><span data-stu-id="25abe-153">Not supported</span></span>|<span data-ttu-id="25abe-154">不支持</span><span class="sxs-lookup"><span data-stu-id="25abe-154">Not supported</span></span>|  
|<span data-ttu-id="25abe-155">本地用户帐户（非管理）</span><span class="sxs-lookup"><span data-stu-id="25abe-155">Local user account (non-administrative)</span></span>|<span data-ttu-id="25abe-156">支持<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="25abe-156">Supported<sup>1</sup></span></span>|<span data-ttu-id="25abe-157">不支持</span><span class="sxs-lookup"><span data-stu-id="25abe-157">Not supported</span></span>|<span data-ttu-id="25abe-158">不适用</span><span class="sxs-lookup"><span data-stu-id="25abe-158">Not applicable</span></span>|  
|<span data-ttu-id="25abe-159">本地系统帐户 (NT AUTHORITY\System)</span><span class="sxs-lookup"><span data-stu-id="25abe-159">Local System account (NT AUTHORITY\System)</span></span>|<span data-ttu-id="25abe-160">支持<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="25abe-160">Supported<sup>2</sup></span></span>|<span data-ttu-id="25abe-161">不支持</span><span class="sxs-lookup"><span data-stu-id="25abe-161">Not supported</span></span>|<span data-ttu-id="25abe-162">支持<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="25abe-162">Supported<sup>2</sup></span></span>|  
|<span data-ttu-id="25abe-163">本地服务帐户 (NT AUTHORITY\LocalService)</span><span class="sxs-lookup"><span data-stu-id="25abe-163">Local Service account (NT AUTHORITY\LocalService)</span></span>|<span data-ttu-id="25abe-164">不支持</span><span class="sxs-lookup"><span data-stu-id="25abe-164">Not supported</span></span>|<span data-ttu-id="25abe-165">不支持</span><span class="sxs-lookup"><span data-stu-id="25abe-165">Not supported</span></span>|<span data-ttu-id="25abe-166">不支持</span><span class="sxs-lookup"><span data-stu-id="25abe-166">Not supported</span></span>|  
  
 <span data-ttu-id="25abe-167"><sup>1</sup>请参阅下面的限制1。</span><span class="sxs-lookup"><span data-stu-id="25abe-167"><sup>1</sup> See Limitation 1 below.</span></span>  
  
 <span data-ttu-id="25abe-168"><sup>2</sup>请参阅下面的限制2。</span><span class="sxs-lookup"><span data-stu-id="25abe-168"><sup>2</sup> See Limitation 2 below.</span></span>  
  
 <span data-ttu-id="25abe-169"><sup>3</sup>参阅下面的限制3。</span><span class="sxs-lookup"><span data-stu-id="25abe-169"><sup>3</sup> See Limitation 3 below.</span></span>  
  
 <span data-ttu-id="25abe-170"><sup>4</sup>请参阅下面的限制4。</span><span class="sxs-lookup"><span data-stu-id="25abe-170"><sup>4</sup> See Limitation 4 below.</span></span>  
  
### <a name="limitation-1-using-non-administrative-accounts-for-multiserver-administration"></a><span data-ttu-id="25abe-171">限制 1：针对多服务器管理使用非管理帐户</span><span class="sxs-lookup"><span data-stu-id="25abe-171">Limitation 1: Using Non-administrative Accounts for Multiserver Administration</span></span>  
 <span data-ttu-id="25abe-172">目标服务器可能无法登记到主服务器，并出现以下错误信息：“登记操作失败”。</span><span class="sxs-lookup"><span data-stu-id="25abe-172">Enlisting target servers to a master server may fail with the following error message: "The enlist operation failed."</span></span>  
  
 <span data-ttu-id="25abe-173">若要解决该错误，请重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="25abe-173">To resolve this error, restart both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="25abe-174">有关详细信息，请参阅 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="25abe-174">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
### <a name="limitation-2-using-the-local-system-account-for-multiserver-administration"></a><span data-ttu-id="25abe-175">限制 2：针对多服务器管理使用本地系统帐户</span><span class="sxs-lookup"><span data-stu-id="25abe-175">Limitation 2: Using the Local System Account for Multiserver Administration</span></span>  
 <span data-ttu-id="25abe-176">仅当主服务器和目标服务器位于同一台计算机中，并在本地系统帐户下运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务时，才支持多服务器管理。</span><span class="sxs-lookup"><span data-stu-id="25abe-176">Multiserver administration is supported when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is run under the Local System account only when both the master server and the target server reside on the same computer.</span></span> <span data-ttu-id="25abe-177">如果使用此配置，则在将目标服务器登记到主服务器时返回以下消息：</span><span class="sxs-lookup"><span data-stu-id="25abe-177">If you use this configuration, the following message is returned when you enlist target servers to the master server:</span></span>  
  
 <span data-ttu-id="25abe-178">“请确保 <target_server_computer_name>\*\* 的代理启动帐户拥有以 targetServer 身份登录的权限”。</span><span class="sxs-lookup"><span data-stu-id="25abe-178">"Ensure the agent start-up account for *<target_server_computer_name>* has rights to log on as targetServer."</span></span>  
  
 <span data-ttu-id="25abe-179">您可以忽略此信息性消息。</span><span class="sxs-lookup"><span data-stu-id="25abe-179">You can ignore this informational message.</span></span> <span data-ttu-id="25abe-180">登记操作将成功完成。</span><span class="sxs-lookup"><span data-stu-id="25abe-180">The enlistment operation should complete successfully.</span></span> <span data-ttu-id="25abe-181">有关详细信息，请参阅 [创建多服务器环境](create-a-multiserver-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="25abe-181">For more information, see [Create a Multiserver Environment](create-a-multiserver-environment.md).</span></span>  
  
### <a name="limitation-3-using-the-network-service-account-when-it-is-a-sql-server-user"></a><span data-ttu-id="25abe-182">限制 3：在网络服务帐户为 SQL Server 用户时使用该帐户</span><span class="sxs-lookup"><span data-stu-id="25abe-182">Limitation 3: Using the Network Service Account When It Is a SQL Server User</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="25abe-183">如果在网络服务帐户下运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务，并显式授予网络服务帐户以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户身份登录到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的访问权限，则可能无法启动代理。</span><span class="sxs-lookup"><span data-stu-id="25abe-183">Agent may fail to start if you run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under the Network Service account, and the Network Service account has been explicitly granted access to log into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="25abe-184">为了解决此问题，请重新启动运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机。</span><span class="sxs-lookup"><span data-stu-id="25abe-184">To resolve this, reboot the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="25abe-185">此操作仅需执行一次。</span><span class="sxs-lookup"><span data-stu-id="25abe-185">This only needs to be done once.</span></span>  
  
### <a name="limitation-4-using-the-network-service-account-when-sql-server-reporting-services-is-running-on-the-same-computer"></a><span data-ttu-id="25abe-186">限制 4：当同一台计算机中还运行有 SQL Server Reporting Services 时使用网络服务帐户</span><span class="sxs-lookup"><span data-stu-id="25abe-186">Limitation 4: Using the Network Service Account When SQL Server Reporting Services Is Running on the Same Computer</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="25abe-187">如果在网络服务帐户下运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务并且在同一台计算机中还运行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，则可能无法启动代理。</span><span class="sxs-lookup"><span data-stu-id="25abe-187">Agent may fail to start if you run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under the Network Service account and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is also running on the same computer.</span></span>  
  
 <span data-ttu-id="25abe-188">为了解决此问题，请重新引导运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机，然后重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="25abe-188">To resolve this, reboot the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running, and then restart both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="25abe-189">此操作仅需执行一次。</span><span class="sxs-lookup"><span data-stu-id="25abe-189">This only needs to be done once.</span></span>  
  
## <a name="common-tasks"></a><span data-ttu-id="25abe-190">常见任务</span><span class="sxs-lookup"><span data-stu-id="25abe-190">Common Tasks</span></span>  
 <span data-ttu-id="25abe-191">**指定 SQL Server 代理服务的启动帐户**</span><span class="sxs-lookup"><span data-stu-id="25abe-191">**To specify the startup account for the SQL Server Agent service**</span></span>  
  
-   [<span data-ttu-id="25abe-192">为 SQL Server 代理设置服务启动帐户&#40;SQL Server 配置管理器&#41;</span><span class="sxs-lookup"><span data-stu-id="25abe-192">Set the Service Startup Account for SQL Server Agent &#40;SQL Server Configuration Manager&#41;</span></span>](set-service-startup-account-sql-server-agent-sql-server-configuration-manager.md)  
  
 <span data-ttu-id="25abe-193">**指定 SQL Server 代理的邮件配置文件**</span><span class="sxs-lookup"><span data-stu-id="25abe-193">**To specify the mail profile for SQL Server Agent**</span></span>  
  
-   [<span data-ttu-id="25abe-194">配置 SQL Server 代理邮件以使用数据库邮件</span><span class="sxs-lookup"><span data-stu-id="25abe-194">Configure SQL Server Agent Mail to Use Database Mail</span></span>](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
> [!NOTE]  
>  <span data-ttu-id="25abe-195">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器可以指定启动操作系统时必须启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="25abe-195">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to specify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must start up when the operating system starts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25abe-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25abe-196">See Also</span></span>  
 <span data-ttu-id="25abe-197">[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="25abe-197">[Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) </span></span>  
 <span data-ttu-id="25abe-198">[管理服务操作指南主题 &#40;SQL Server 配置管理器&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="25abe-198">[Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md) </span></span>  
 [<span data-ttu-id="25abe-199">实现 SQL Server 代理安全性</span><span class="sxs-lookup"><span data-stu-id="25abe-199">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
