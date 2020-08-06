---
title: MSSQL_ENG024070 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fcfcb96b284d46d46f63af4a650f925ef2de73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688817"
---
# <a name="mssql_eng024070"></a><span data-ttu-id="ccceb-102">MSSQL_ENG024070</span><span class="sxs-lookup"><span data-stu-id="ccceb-102">MSSQL_ENG024070</span></span>
    
## <a name="message-details"></a><span data-ttu-id="ccceb-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="ccceb-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccceb-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ccceb-104">Product Name</span></span>|<span data-ttu-id="ccceb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ccceb-105">SQL Server</span></span>|  
|<span data-ttu-id="ccceb-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ccceb-106">Event ID</span></span>|<span data-ttu-id="ccceb-107">24070</span><span class="sxs-lookup"><span data-stu-id="ccceb-107">24070</span></span>|  
|<span data-ttu-id="ccceb-108">事件源</span><span class="sxs-lookup"><span data-stu-id="ccceb-108">Event Source</span></span>|<span data-ttu-id="ccceb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ccceb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ccceb-110">组件</span><span class="sxs-lookup"><span data-stu-id="ccceb-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="ccceb-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="ccceb-111">Symbolic Name</span></span>||  
|<span data-ttu-id="ccceb-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="ccceb-112">Message Text</span></span>|<span data-ttu-id="ccceb-113">客户端没有所需的特权。</span><span class="sxs-lookup"><span data-stu-id="ccceb-113">A required privilege is not held by the client.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ccceb-114">说明</span><span class="sxs-lookup"><span data-stu-id="ccceb-114">Explanation</span></span>  
 <span data-ttu-id="ccceb-115">这是一个常规错误，不管是否进行复制，都会引发该错误。</span><span class="sxs-lookup"><span data-stu-id="ccceb-115">This is a general error that can be raised regardless of whether replication is being used.</span></span> <span data-ttu-id="ccceb-116">对于复制拓扑中的服务器，引发该错误的原因通常是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 服务控制管理器，而不是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 配置管理器来更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户。</span><span class="sxs-lookup"><span data-stu-id="ccceb-116">For a server in a replication topology, the error is typically raised because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account is changed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Service Control Manager instead of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="ccceb-117">当您在更改服务帐户后尝试运行代理作业时，作业可能会失败，并显示类似如下的错误消息：</span><span class="sxs-lookup"><span data-stu-id="ccceb-117">When you try to run an agent job after changing the service account, the job might fail with an error message that is similar to the following:</span></span>  
  
 <span data-ttu-id="ccceb-118">"作为用户执行： \<UserAccount> 。</span><span class="sxs-lookup"><span data-stu-id="ccceb-118">"Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="ccceb-119">复制-复制快照子系统：代理 \<AgentName> 失败。</span><span class="sxs-lookup"><span data-stu-id="ccceb-119">Replication-Replication Snapshot Subsystem: agent \<AgentName> failed.</span></span> <span data-ttu-id="ccceb-120">作为用户执行： \<UserAccount> 。</span><span class="sxs-lookup"><span data-stu-id="ccceb-120">Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="ccceb-121">客户端没有所需的特权。</span><span class="sxs-lookup"><span data-stu-id="ccceb-121">A required privilege is not held by the client.</span></span> <span data-ttu-id="ccceb-122">该步骤失败。</span><span class="sxs-lookup"><span data-stu-id="ccceb-122">The step failed.</span></span> <span data-ttu-id="ccceb-123">`[SQLSTATE 42000] (Error 14151)`.</span><span class="sxs-lookup"><span data-stu-id="ccceb-123">`[SQLSTATE 42000] (Error 14151)`.</span></span> <span data-ttu-id="ccceb-124">该步骤失败。”</span><span class="sxs-lookup"><span data-stu-id="ccceb-124">The step failed."</span></span>  
  
 <span data-ttu-id="ccceb-125">出现此问题的原因是 Windows 服务控制管理器无法向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的新服务帐户授予所需权限。</span><span class="sxs-lookup"><span data-stu-id="ccceb-125">This problem occurs because the Windows Service Control Manager cannot grant the required permissions to the new service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ccceb-126">用户操作</span><span class="sxs-lookup"><span data-stu-id="ccceb-126">User Action</span></span>  
 <span data-ttu-id="ccceb-127">为了避免以后再出现此问题，请始终使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器而非 Windows 服务控制管理器来更改服务帐户和密码。</span><span class="sxs-lookup"><span data-stu-id="ccceb-127">To avoid this problem in the future, always use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager instead of the Windows Service Control Manager to change service accounts and passwords.</span></span>  
  
 <span data-ttu-id="ccceb-128">若要解决此问题，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器将服务帐户更改为原始帐户。</span><span class="sxs-lookup"><span data-stu-id="ccceb-128">To resolve this problem, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change the service account back to the original account.</span></span> <span data-ttu-id="ccceb-129">然后，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器更改为新帐户。</span><span class="sxs-lookup"><span data-stu-id="ccceb-129">Then, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change to the new account.</span></span> <span data-ttu-id="ccceb-130">执行此操作时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器会将新帐户添加到以下安全组中：</span><span class="sxs-lookup"><span data-stu-id="ccceb-130">When you do this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager adds the new account to the following security group:</span></span>  
  
 <span data-ttu-id="ccceb-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span><span class="sxs-lookup"><span data-stu-id="ccceb-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span></span>  
  
 <span data-ttu-id="ccceb-132">成为此安全组的成员，便可以向新帐户授予运行复制代理作业所需的权限。</span><span class="sxs-lookup"><span data-stu-id="ccceb-132">Being a member of this security group grants to the new account the required permissions to run the replication agent job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccceb-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ccceb-133">See Also</span></span>  
 <span data-ttu-id="ccceb-134">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ccceb-134">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="ccceb-135">[管理复制中的登录名和密码](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="ccceb-135">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 [<span data-ttu-id="ccceb-136">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="ccceb-136">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
