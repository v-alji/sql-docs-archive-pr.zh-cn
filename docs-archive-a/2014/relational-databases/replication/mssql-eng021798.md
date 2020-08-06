---
title: MSSQL_ENG021798 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 327b4a373c28376701ea12400215ab00367df66a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688819"
---
# <a name="mssql_eng021798"></a><span data-ttu-id="cc810-102">MSSQL_ENG021798</span><span class="sxs-lookup"><span data-stu-id="cc810-102">MSSQL_ENG021798</span></span>
    
## <a name="message-details"></a><span data-ttu-id="cc810-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="cc810-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc810-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cc810-104">Product Name</span></span>|<span data-ttu-id="cc810-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cc810-105">SQL Server</span></span>|  
|<span data-ttu-id="cc810-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cc810-106">Event ID</span></span>|<span data-ttu-id="cc810-107">21798</span><span class="sxs-lookup"><span data-stu-id="cc810-107">21798</span></span>|  
|<span data-ttu-id="cc810-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cc810-108">Event Source</span></span>|<span data-ttu-id="cc810-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cc810-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cc810-110">组件</span><span class="sxs-lookup"><span data-stu-id="cc810-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="cc810-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="cc810-111">Symbolic Name</span></span>||  
|<span data-ttu-id="cc810-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="cc810-112">Message Text</span></span>|<span data-ttu-id="cc810-113">在继续操作之前，必须通过 '%s' 添加 '%s' 代理作业。</span><span class="sxs-lookup"><span data-stu-id="cc810-113">The '%s' agent job must be added through '%s' before continuing.</span></span> <span data-ttu-id="cc810-114">请参阅 '%s' 的文档。</span><span class="sxs-lookup"><span data-stu-id="cc810-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cc810-115">说明</span><span class="sxs-lookup"><span data-stu-id="cc810-115">Explanation</span></span>  
 <span data-ttu-id="cc810-116">要创建发布，您必须是发布服务器上的 **sysadmin** 固定服务器角色的成员或者发布数据库中的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="cc810-116">To create a publication, you must be a member of the **sysadmin** fixed server role on the Publisher or a member of the **db_owner** fixed database role in the publication database.</span></span> <span data-ttu-id="cc810-117">如果您是 **db_owner** 角色的成员，则发生以下情况将会引发此错误：</span><span class="sxs-lookup"><span data-stu-id="cc810-117">If you are a member of the **db_owner** role, this error is raised if:</span></span>  
  
-   <span data-ttu-id="cc810-118">从 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]运行脚本。</span><span class="sxs-lookup"><span data-stu-id="cc810-118">You run scripts from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="cc810-119">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中的安全模式已更改，因此必须更新这些脚本。</span><span class="sxs-lookup"><span data-stu-id="cc810-119">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   <span data-ttu-id="cc810-120">存储过程 **sp_addpublication** 在执行 [sp_addlogreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) 之前执行。</span><span class="sxs-lookup"><span data-stu-id="cc810-120">The stored procedure **sp_addpublication** is executed before executing [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql).</span></span> <span data-ttu-id="cc810-121">这适用于所有的事务发布。</span><span class="sxs-lookup"><span data-stu-id="cc810-121">This applies to all transactional publications.</span></span>  
  
-   <span data-ttu-id="cc810-122">存储过程 **sp_addpublication** 在执行 [sp_addqreader_agent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) 之前执行。</span><span class="sxs-lookup"><span data-stu-id="cc810-122">The stored procedure **sp_addpublication** is executed before executing [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql).</span></span> <span data-ttu-id="cc810-123">这适用于为排队更新订阅启用的事务发布， (sp_addpublication) 的参数的值为 TRUE **@allow_queued_tran** 。 **sp_addpublication**</span><span class="sxs-lookup"><span data-stu-id="cc810-123">This applies to transactional publications that are enabled for queued updating subscriptions (a value of TRUE for the **@allow_queued_tran** parameter of **sp_addpublication**).</span></span>  
  
 <span data-ttu-id="cc810-124">存储过程 **sp_addlogreader_agent** 和 **sp_addqreader_agent** 各创建一个代理作业并允许您指定运行代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="cc810-124">The stored procedures **sp_addlogreader_agent** and **sp_addqreader_agent** each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="cc810-125">对于 **sysadmin** 角色中的用户，如果未执行 **sp_addlogreader_agent** 和 **sp_addqreader_agent** ，则将隐式创建代理作业；代理在分发服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="cc810-125">For users in the **sysadmin** role, agent jobs are created implicitly if **sp_addlogreader_agent** and **sp_addqreader_agent** are not executed; agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the Distributor.</span></span> <span data-ttu-id="cc810-126">尽管 **sp_addlogreader_agent** 和 **sp_addqreader_agent** 对于 **sysadmin** 角色中的用户不是必须的，但是为了安全起见，最好为代理指定单独的帐户。</span><span class="sxs-lookup"><span data-stu-id="cc810-126">Although **sp_addlogreader_agent** and **sp_addqreader_agent** are not required for users in the **sysadmin** role, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="cc810-127">有关详细信息，请参阅 [复制代理安全模式](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="cc810-127">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cc810-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="cc810-128">User Action</span></span>  
 <span data-ttu-id="cc810-129">请确保按正确的顺序执行过程。</span><span class="sxs-lookup"><span data-stu-id="cc810-129">Ensure you execute procedures in the correct order.</span></span> <span data-ttu-id="cc810-130">有关详细信息，请参阅[创建发布](publish/create-a-publication.md)，更新这些脚本以包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本所需的存储过程和参数。</span><span class="sxs-lookup"><span data-stu-id="cc810-130">For more information, see [Create a Publication](publish/create-a-publication.md), update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="cc810-131">有关详细信息，请参阅[升级复制脚本（复制 Transact-SQL 编程）](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="cc810-131">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc810-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc810-132">See Also</span></span>  
 [<span data-ttu-id="cc810-133">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="cc810-133">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
