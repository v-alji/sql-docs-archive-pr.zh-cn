---
title: 保护发布服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- Publishers [SQL Server replication], security
- publications [SQL Server replication], security
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dca3f704c43a97c2c34921007341b9bd613676ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588972"
---
# <a name="secure-the-publisher"></a><span data-ttu-id="6708b-102">保护发布服务器的安全</span><span class="sxs-lookup"><span data-stu-id="6708b-102">Secure the Publisher</span></span>
  <span data-ttu-id="6708b-103">以下复制代理将连接到发布服务器：</span><span class="sxs-lookup"><span data-stu-id="6708b-103">The following replication agents connect to the Publisher:</span></span>  
  
-   <span data-ttu-id="6708b-104">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="6708b-104">Log Reader Agent</span></span>  
  
-   <span data-ttu-id="6708b-105">快照代理</span><span class="sxs-lookup"><span data-stu-id="6708b-105">Snapshot Agent</span></span>  
  
-   <span data-ttu-id="6708b-106">队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="6708b-106">Queue Reader Agent</span></span>  
  
-   <span data-ttu-id="6708b-107">合并代理</span><span class="sxs-lookup"><span data-stu-id="6708b-107">Merge Agent</span></span>  
  
 <span data-ttu-id="6708b-108">建议您为这些代理提供合适的登录名，遵循授予所需的最小权限的原则，并保护所有密码的存储。</span><span class="sxs-lookup"><span data-stu-id="6708b-108">We recommend that you provide an appropriate login for these agents, follow the principle of granting the minimal rights that are required, and protect the storage of all passwords.</span></span> <span data-ttu-id="6708b-109">有关每个代理所需权限的信息，请参阅 [Replication Agent Security Model](replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="6708b-109">For information about the permissions that are required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="6708b-110">除适当地管理登录名和密码外，还应了解发布访问列表 (PAL) 的角色。</span><span class="sxs-lookup"><span data-stu-id="6708b-110">Besides appropriately managing logins and passwords, you should understand the role of the publication access list (PAL).</span></span> <span data-ttu-id="6708b-111">PAL 用于启用登录名以访问发布数据，同时限制对发布服务器中的数据库进行即席访问。</span><span class="sxs-lookup"><span data-stu-id="6708b-111">The PAL is used to enable logins to access to publication data while restricting ad hoc access to the database at the Publisher.</span></span>  
  
## <a name="publication-access-list"></a><span data-ttu-id="6708b-112">发布访问列表</span><span class="sxs-lookup"><span data-stu-id="6708b-112">Publication Access List</span></span>  
 <span data-ttu-id="6708b-113">PAL 是用于保护发布服务器中发布的主要机制。</span><span class="sxs-lookup"><span data-stu-id="6708b-113">The PAL is the primary mechanism for securing publications at the Publisher.</span></span> <span data-ttu-id="6708b-114">PAL 的功能与 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 的访问控制列表相似。</span><span class="sxs-lookup"><span data-stu-id="6708b-114">The PAL functions similarly to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows access control list.</span></span> <span data-ttu-id="6708b-115">创建发布时，复制将为该发布创建 PAL。</span><span class="sxs-lookup"><span data-stu-id="6708b-115">When you create a publication, replication creates a PAL for the publication.</span></span> <span data-ttu-id="6708b-116">可把 PAL 配置为包含被授权访问发布的登录名和组的列表。</span><span class="sxs-lookup"><span data-stu-id="6708b-116">The PAL can be configured to contain a list of logins and groups that are granted access to the publication.</span></span> <span data-ttu-id="6708b-117">当一个代理连接到发布服务器或分发服务器并请求访问某个发布时，PAL 中的身份验证信息将与此代理提供的发布服务器登录名进行比较。</span><span class="sxs-lookup"><span data-stu-id="6708b-117">When an agent connects to the Publisher or Distributor and requests access to a publication, the authentication information in the PAL is compared to the Publisher login that the agent provides.</span></span> <span data-ttu-id="6708b-118">此过程为发布服务器提供了额外的安全性，方法是：阻止客户端工具使用发布服务器和分发服务器登录名在发布服务器中直接进行修改</span><span class="sxs-lookup"><span data-stu-id="6708b-118">This process provides additional security for the Publisher by preventing the Publisher and Distributor login from being used by a client tool to perform modifications on the Publisher directly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6708b-119">复制操作在发布服务器中为每个发布创建一个角色，强制应用 PAL 成员身份。</span><span class="sxs-lookup"><span data-stu-id="6708b-119">Replication creates a role on the Publisher for each publication to enforce PAL membership.</span></span> <span data-ttu-id="6708b-120">对于合并复制，该角色的名称采用 Msmerge_\<PublicationID> 的形式；对于事务性复制和快照复制，该角色的名称采用 MSReplPAL_\<PublicationDatabaseID>_\<PublicationID> 的形式。</span><span class="sxs-lookup"><span data-stu-id="6708b-120">The role has a name in the form **Msmerge_**_\<PublicationID>_ for merge replication and **MSReplPAL_**_\<PublicationDatabaseID>_**_**_\<PublicationID>_ for transactional and snapshot replication.</span></span>  
  
 <span data-ttu-id="6708b-121">默认情况下，PAL 中包括的登录名是： **sysadmin** 固定服务器角色在创建发布时的成员，以及用于创建发布的登录名。</span><span class="sxs-lookup"><span data-stu-id="6708b-121">By default, the following logins are included in the PAL: the members of the **sysadmin** fixed server role at the time the publication is created and the login that is used to create the publication.</span></span> <span data-ttu-id="6708b-122">默认情况下，发布数据库中属于 **sysadmin** 固定服务器角色或 **db_owner** 固定数据库角色的成员的所有登录名都可订阅发布，而不用显式添加到 PAL 中。</span><span class="sxs-lookup"><span data-stu-id="6708b-122">By default, all logins that are members of the **sysadmin** fixed server role or the **db_owner** fixed database role on the publication database can subscribe to a publication without being explicitly added to the PAL.</span></span>  
  
 <span data-ttu-id="6708b-123">使用 PAL 时，请考虑以下原则：</span><span class="sxs-lookup"><span data-stu-id="6708b-123">When you are using the PAL, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="6708b-124">在将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名添加到 PAL 前，必须将该登录名与发布数据库中的数据库用户关联。</span><span class="sxs-lookup"><span data-stu-id="6708b-124">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before adding the login to the PAL.</span></span>  
  
-   <span data-ttu-id="6708b-125">遵循最小权限原则，仅允许 PAL 中的登录名拥有执行复制任务所必需的权限。</span><span class="sxs-lookup"><span data-stu-id="6708b-125">Follow the principle of least privilege by allowing logins in the PAL only the permissions the logins must have to perform replication tasks.</span></span> <span data-ttu-id="6708b-126">不要将登录名添加给执行复制任务所不需要的任何固定数据库角色或服务器角色。</span><span class="sxs-lookup"><span data-stu-id="6708b-126">Do not add the logins to any fixed database roles or server roles that are not required for replication.</span></span> <span data-ttu-id="6708b-127">有关所需权限的详细信息，请参阅 [Replication Agent Security Model](replication-agent-security-model.md) 和 [Replication Security Best Practices](replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="6708b-127">For more information about the permissions that are required, see [Replication Agent Security Model](replication-agent-security-model.md) and [Replication Security Best Practices](replication-security-best-practices.md).</span></span>  
  
-   <span data-ttu-id="6708b-128">如果使用远程分发服务器，则 PAL 中的帐户必须在发布服务器和分发服务器中都可用。</span><span class="sxs-lookup"><span data-stu-id="6708b-128">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="6708b-129">帐户必须是在这两个服务器中定义的域帐户或本地帐户。</span><span class="sxs-lookup"><span data-stu-id="6708b-129">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="6708b-130">与这两个登录名关联的密码必须相同。</span><span class="sxs-lookup"><span data-stu-id="6708b-130">The passwords associated with both logins must be the same.</span></span>  
  
-   <span data-ttu-id="6708b-131">如果 PAL 包含 Windows 帐户并且域使用 Active Directory，则运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帐户必须具有对 Active Directory 的读取权限。</span><span class="sxs-lookup"><span data-stu-id="6708b-131">If the PAL contains Windows accounts and the domain uses Active Directory, the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs must have permissions to read from Active Directory.</span></span> <span data-ttu-id="6708b-132">如果遇到与 Windows 帐户有关的问题，请确保运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帐户具有足够的权限。</span><span class="sxs-lookup"><span data-stu-id="6708b-132">If you experience issues with Windows accounts, make sure that the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs has sufficient permissions.</span></span> <span data-ttu-id="6708b-133">有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="6708b-133">For more information, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="6708b-134">若要管理 PAL，请参阅[管理发布访问列表中的登录名](manage-logins-in-the-publication-access-list.md)。</span><span class="sxs-lookup"><span data-stu-id="6708b-134">To manage the PAL, see [Manage Logins in the Publication Access List](manage-logins-in-the-publication-access-list.md).</span></span>  
  
## <a name="snapshot-agent"></a><span data-ttu-id="6708b-135">快照代理</span><span class="sxs-lookup"><span data-stu-id="6708b-135">Snapshot Agent</span></span>  
 <span data-ttu-id="6708b-136">每个发布拥有一个快照代理。</span><span class="sxs-lookup"><span data-stu-id="6708b-136">There is one Snapshot Agent for each publication.</span></span> <span data-ttu-id="6708b-137">有关详细信息，请参阅 [Create a Publication](../publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="6708b-137">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="ftp-snapshot-delivery"></a><span data-ttu-id="6708b-138">FTP 快照传递</span><span class="sxs-lookup"><span data-stu-id="6708b-138">FTP Snapshot Delivery</span></span>  
 <span data-ttu-id="6708b-139">如果指定应通过 FTP 共享而非 UNC 共享使快照可用，则配置 FTP 访问时必须指定登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="6708b-139">If you specify that snapshots should be made available through an FTP share rather than a UNC share, you must specify a login and password when configuring FTP access.</span></span> <span data-ttu-id="6708b-140">有关详细信息，请参阅[通过 FTP 传递快照](../publish/deliver-a-snapshot-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="6708b-140">For more information, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
## <a name="log-reader-agent"></a><span data-ttu-id="6708b-141">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="6708b-141">Log Reader Agent</span></span>  
 <span data-ttu-id="6708b-142">对于使用事务复制发布的每个数据库，都有一个日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="6708b-142">There is one Log Reader Agent for each database published for transactional replication.</span></span> <span data-ttu-id="6708b-143">有关详细信息，请参阅 [Create a Publication](../publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="6708b-143">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="queue-reader-agent"></a><span data-ttu-id="6708b-144">队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="6708b-144">Queue Reader Agent</span></span>  
 <span data-ttu-id="6708b-145">与给定的分发服务器关联的所有发布服务器和发布（允许排队更新订阅）都拥有一个队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="6708b-145">There is one Queue Reader Agent for all Publishers and publications (that allow queued updating subscriptions) associated with a given Distributor.</span></span> <span data-ttu-id="6708b-146">有关详细信息，请参阅[允许更新事务发布的订阅](../publish/enable-updating-subscriptions-for-transactional-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="6708b-146">For more information, see [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6708b-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6708b-147">See Also</span></span>  
 <span data-ttu-id="6708b-148">[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="6708b-148">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="6708b-149">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="6708b-149">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="6708b-150">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="6708b-150">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
