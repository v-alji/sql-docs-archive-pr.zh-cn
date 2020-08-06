---
title: MSSQL_ENG021797 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021797 error
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d33ade7e7eea9fa9e95453a5b232447f7b222b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688821"
---
# <a name="mssql_eng021797"></a><span data-ttu-id="b5a91-102">MSSQL_ENG021797</span><span class="sxs-lookup"><span data-stu-id="b5a91-102">MSSQL_ENG021797</span></span>
    
## <a name="message-details"></a><span data-ttu-id="b5a91-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="b5a91-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5a91-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b5a91-104">Product Name</span></span>|<span data-ttu-id="b5a91-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b5a91-105">SQL Server</span></span>|  
|<span data-ttu-id="b5a91-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b5a91-106">Event ID</span></span>|<span data-ttu-id="b5a91-107">21797</span><span class="sxs-lookup"><span data-stu-id="b5a91-107">21797</span></span>|  
|<span data-ttu-id="b5a91-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b5a91-108">Event Source</span></span>|<span data-ttu-id="b5a91-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b5a91-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b5a91-110">组件</span><span class="sxs-lookup"><span data-stu-id="b5a91-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="b5a91-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="b5a91-111">Symbolic Name</span></span>||  
|<span data-ttu-id="b5a91-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="b5a91-112">Message Text</span></span>|<span data-ttu-id="b5a91-113">%s 必须是以下格式的有效 Windows 登录信息:'MACHINE\Login' 或 'DOMAIN\Login'。</span><span class="sxs-lookup"><span data-stu-id="b5a91-113">'%s' must be a valid Windows Login in the form: 'MACHINE\Login' or 'DOMAIN\Login'.</span></span> <span data-ttu-id="b5a91-114">请参阅 '%s' 的文档。</span><span class="sxs-lookup"><span data-stu-id="b5a91-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b5a91-115">说明</span><span class="sxs-lookup"><span data-stu-id="b5a91-115">Explanation</span></span>  
 <span data-ttu-id="b5a91-116">如果为参数指定的值 **@job_login** 为 null 或无效，则下列复制存储过程将引发此错误。</span><span class="sxs-lookup"><span data-stu-id="b5a91-116">This error is raised by the following replication stored procedures if the value specified for the **@job_login** parameter is null or not valid.</span></span> <span data-ttu-id="b5a91-117">如果 **db_owner** 固定数据库角色的成员从早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中运行脚本时，将发生此错误。</span><span class="sxs-lookup"><span data-stu-id="b5a91-117">This error can occur if a member of the **db_owner** fixed database role runs scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5a91-118">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中的安全模式已更改，因此必须更新这些脚本。</span><span class="sxs-lookup"><span data-stu-id="b5a91-118">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   [<span data-ttu-id="b5a91-119">sp_addlogreader_agent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5a91-119">sp_addlogreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)  
  
-   [<span data-ttu-id="b5a91-120">sp_addqreader_agent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5a91-120">sp_addqreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql)  
  
-   [<span data-ttu-id="b5a91-121">sp_addpublication_snapshot (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5a91-121">sp_addpublication_snapshot &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)  
  
-   [<span data-ttu-id="b5a91-122">sp_addpushsubscription_agent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5a91-122">sp_addpushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="b5a91-123">sp_addpullsubscription_agent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5a91-123">sp_addpullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="b5a91-124">sp_addmergepushsubscription_agent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5a91-124">sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="b5a91-125">sp_addmergepullsubscription_agent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5a91-125">sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)  
  
 <span data-ttu-id="b5a91-126">这些存储过程可由相应服务器上 **sysadmin** 固定服务器角色的成员执行，或者相应数据库中 **db_owner** 固定数据库角色的成员执行。</span><span class="sxs-lookup"><span data-stu-id="b5a91-126">These stored procedures can be executed by a member of the **sysadmin** fixed server role on the appropriate server or a member of the **db_owner** fixed database role in the appropriate database.</span></span> <span data-ttu-id="b5a91-127">每个存储过程都创建代理作业，并允许指定用于运行代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="b5a91-127">The stored procedures each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="b5a91-128">对于 **sysadmin** 角色中的用户，即便未指定 Windows 帐户（如果指定帐户，则帐户必须有效），代理作业仍将隐式创建；代理运行于相应服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户的上下文中。</span><span class="sxs-lookup"><span data-stu-id="b5a91-128">For users in the **sysadmin** role, agent jobs are created implicitly even if a Windows account is not specified (if an account is specified, it must be valid); agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the appropriate server.</span></span> <span data-ttu-id="b5a91-129">虽然帐户不是必需的，但为代理指定单独的帐户却是最佳安全方法。</span><span class="sxs-lookup"><span data-stu-id="b5a91-129">Although the account is not required, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="b5a91-130">有关详细信息，请参阅 [复制代理安全模式](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b5a91-130">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b5a91-131">用户操作</span><span class="sxs-lookup"><span data-stu-id="b5a91-131">User Action</span></span>  
 <span data-ttu-id="b5a91-132">确保为每个过程的参数指定一个有效的 Windows 帐户 **@job_login** 。</span><span class="sxs-lookup"><span data-stu-id="b5a91-132">Ensure you specify a valid Windows account for the **@job_login** parameter of each procedure.</span></span> <span data-ttu-id="b5a91-133">如果您具有早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的复制脚本，请更新这些脚本以包括 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]所需的存储过程和参数。</span><span class="sxs-lookup"><span data-stu-id="b5a91-133">If you have replication scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="b5a91-134">有关详细信息，请参阅[升级复制脚本（复制 Transact-SQL 编程）](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="b5a91-134">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a91-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5a91-135">See Also</span></span>  
 [<span data-ttu-id="b5a91-136">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="b5a91-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
