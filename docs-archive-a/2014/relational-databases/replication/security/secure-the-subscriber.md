---
title: 保护订阅服务器的安全 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], security
- Subscribers [SQL Server replication], security
- security [SQL Server replication], Subscribers
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f03b9a202c3c49f147368460518a579f28dc850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588968"
---
# <a name="secure-the-subscriber"></a><span data-ttu-id="0864f-102">保护订阅服务器的安全</span><span class="sxs-lookup"><span data-stu-id="0864f-102">Secure the Subscriber</span></span>
  <span data-ttu-id="0864f-103">合并代理和分发代理连接到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0864f-103">Merge Agents and Distribution Agents connect to the Subscriber.</span></span> <span data-ttu-id="0864f-104">这些连接可在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录或 Windows 登录上下文环境中建立。</span><span class="sxs-lookup"><span data-stu-id="0864f-104">These connections can be made under the context of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login or a Windows login.</span></span> <span data-ttu-id="0864f-105">在遵循授予必要的最小权限并且保护所有密码的存储的原则下，为这些代理提供合适的登录名十分重要。</span><span class="sxs-lookup"><span data-stu-id="0864f-105">It is important to provide an appropriate login for these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords.</span></span> <span data-ttu-id="0864f-106">有关每个代理所需权限的信息，请参阅 [Replication Agent Security Model](replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="0864f-106">For information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
## <a name="distribution-agent"></a><span data-ttu-id="0864f-107">分发代理</span><span class="sxs-lookup"><span data-stu-id="0864f-107">Distribution Agent</span></span>  
 <span data-ttu-id="0864f-108">可以是每个订阅一个分发代理（独立代理，对于新建发布向导中创建的发布是默认设置），也可以是每个发布数据库和订阅数据库对一个分发代理（共享代理）。</span><span class="sxs-lookup"><span data-stu-id="0864f-108">There is either one Distribution Agent per subscription (an independent agent, the default for publications created in the New Publication Wizard) or one Distribution Agent per publication database and subscription database pair (a shared agent).</span></span> <span data-ttu-id="0864f-109">T</span><span class="sxs-lookup"><span data-stu-id="0864f-109">T</span></span>  
  
 <span data-ttu-id="0864f-110">若要为推送订阅指定连接信息，请参阅[创建推送订阅](../create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0864f-110">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="0864f-111">若要为请求订阅指定连接信息，请参阅[创建请求订阅](../create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0864f-111">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md)</span></span>  
  
## <a name="merge-agent"></a><span data-ttu-id="0864f-112">合并代理</span><span class="sxs-lookup"><span data-stu-id="0864f-112">Merge Agent</span></span>  
 <span data-ttu-id="0864f-113">每个合并订阅都有自己的合并代理，此合并代理同时连接发布服务器和订阅服务器并对它们进行更新。</span><span class="sxs-lookup"><span data-stu-id="0864f-113">Each merge subscription has its own Merge Agent that connects to and updates both the Publisher and the Subscriber.</span></span>  
  
 <span data-ttu-id="0864f-114">若要为推送订阅指定连接信息，请参阅[创建推送订阅](../create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0864f-114">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="0864f-115">若要为请求订阅指定连接信息，请参阅[创建请求订阅](../create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0864f-115">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md).</span></span>  
  
## <a name="immediate-updating-subscriptions"></a><span data-ttu-id="0864f-116">立即更新订阅</span><span class="sxs-lookup"><span data-stu-id="0864f-116">Immediate Updating Subscriptions</span></span>  
 <span data-ttu-id="0864f-117">当配置立即更新订阅时，需要在与发布服务器建立连接的订阅服务器上指定一个帐户。</span><span class="sxs-lookup"><span data-stu-id="0864f-117">When you configure an immediate updating subscription, you specify an account at the Subscriber under which connections to the Publisher are made.</span></span> <span data-ttu-id="0864f-118">连接用于在订阅服务器上激发的触发器，这些触发器用于将更改传播到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="0864f-118">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="0864f-119">有三种连接类型可以选择：</span><span class="sxs-lookup"><span data-stu-id="0864f-119">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="0864f-120">复制创建的链接服务器；此连接是用配置时所指定的凭据建立的。</span><span class="sxs-lookup"><span data-stu-id="0864f-120">A linked server that replication creates; the connection is made with the credentials you specify at configuration time.</span></span>  
  
-   <span data-ttu-id="0864f-121">复制创建的链接服务器；用在订阅服务器上做更改的用户的凭据建立连接。</span><span class="sxs-lookup"><span data-stu-id="0864f-121">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
-   <span data-ttu-id="0864f-122">已定义的链接服务器或远程服务器。</span><span class="sxs-lookup"><span data-stu-id="0864f-122">A linked server or remote server that you have already defined.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0864f-123">若要指定连接信息，请使用存储过程 [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0864f-123">To specify connection information, use the stored procedure [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="0864f-124">还可以使用新订阅向导的 **“用于可更新订阅的登录名”** 页，该页可调用 **sp_link_publication**。</span><span class="sxs-lookup"><span data-stu-id="0864f-124">You can also use the **Login for Updatable Subscriptions** page of the New Subscription Wizard, which calls **sp_link_publication**.</span></span> <span data-ttu-id="0864f-125">在某些情况下，如果订阅服务器运行的是 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 或更高版本，而发布服务器运行的是早期版本，则该存储过程可能会失败。</span><span class="sxs-lookup"><span data-stu-id="0864f-125">Under certain conditions, this stored procedure can fail if the Subscriber is running [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) or later, and the Publisher is running an earlier version.</span></span> <span data-ttu-id="0864f-126">如果在这种情形下存储过程失败，请将发布服务器升级到 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="0864f-126">If the stored procedure fails in this scenario, upgrade the Publisher to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 or later.</span></span>  
  
 <span data-ttu-id="0864f-127">有关详细信息，请参阅[创建事务发布的可更新订阅](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)和[查看和修改复制安全性设置](view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="0864f-127">For more information, see [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0864f-128">对于指定的连接帐户，只能授予对复制功能在发布数据库中创建的视图插入、更新和删除数据的权限，而不应授予任何其他权限。</span><span class="sxs-lookup"><span data-stu-id="0864f-128">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="0864f-129">对于发布数据库（名称格式为 syncobj_\<HexadecimalNumber>）中的视图，请将其权限授予在每个订阅服务器上配置的帐户。</span><span class="sxs-lookup"><span data-stu-id="0864f-129">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
## <a name="queued-updating-subscriptions"></a><span data-ttu-id="0864f-130">排队更新订阅</span><span class="sxs-lookup"><span data-stu-id="0864f-130">Queued Updating Subscriptions</span></span>  
 <span data-ttu-id="0864f-131">当配置排队更新订阅时，请谨记以下两个与安全性相关的方面：</span><span class="sxs-lookup"><span data-stu-id="0864f-131">When you configure queued updating subscriptions, there are two areas to keep in mind that relate to security:</span></span>  
  
-   <span data-ttu-id="0864f-132">每个分发服务器只有一个队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="0864f-132">There is only one Queue Reader Agent for each Distributor.</span></span> <span data-ttu-id="0864f-133">建议最多为每个分发服务器配置一个为排队更新订阅而启用的发布。</span><span class="sxs-lookup"><span data-stu-id="0864f-133">It is recommended that for each Distributor, you configure at most one publication that is enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="0864f-134">队列读取器代理建立与分发服务器、发布服务器和每个订阅服务器的连接：</span><span class="sxs-lookup"><span data-stu-id="0864f-134">The Queue Reader agent makes connections to the Distributor, Publisher, and each Subscriber:</span></span>  
  
    -   <span data-ttu-id="0864f-135">运行代理并与分发服务器建立连接的账户将在创建代理时指定（如果使用新建发布向导，则代理将在创建为更新订阅而启用的发布时创建）。</span><span class="sxs-lookup"><span data-stu-id="0864f-135">The account under which the agent runs and makes connections to the Distributor is specified when you create the agent (if you use the New Publication Wizard, the agent is created when you create a publication that is enabled for updating subscriptions).</span></span>  
  
    -   <span data-ttu-id="0864f-136">代理与发布服务器建立连接的帐户将在配置发布服务器的分发时指定。</span><span class="sxs-lookup"><span data-stu-id="0864f-136">The account under which the agent makes connections to the Publisher is specified when you configure distribution for a Publisher.</span></span> <span data-ttu-id="0864f-137">指定运行代理的 Windows 帐户，或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帐户。</span><span class="sxs-lookup"><span data-stu-id="0864f-137">Specify the Windows account under which the agent runs or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account.</span></span>  
  
    -   <span data-ttu-id="0864f-138">代理与订阅服务器建立连接的帐户将在创建订阅时指定。</span><span class="sxs-lookup"><span data-stu-id="0864f-138">The account under which the agent makes connections to the Subscriber is specified when you create the subscription.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0864f-139">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到订阅服务器，并指定一个不同帐户连接到每个订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0864f-139">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication for connections to Subscribers, and specify a different account for the connection to each Subscriber.</span></span> <span data-ttu-id="0864f-140">如果使用请求订阅，复制始终将连接设置为使用 Windows 身份验证（对于请求订阅，复制无法访问需要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证的订阅服务器上的元数据）。</span><span class="sxs-lookup"><span data-stu-id="0864f-140">If you use a pull subscription, replication always sets the connection to use Windows Authentication (for pull subscriptions, replication cannot access metadata at the Subscriber required to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication).</span></span> <span data-ttu-id="0864f-141">这种情况下，请在配置订阅后对连接进行更改，以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="0864f-141">In this case, change the connection to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication after the subscription is configured.</span></span>  
  
     <span data-ttu-id="0864f-142">有关详细信息，请参阅如何：创建事务发布的更新订阅 (SQL Server Management Studio) 和[查看和修改复制安全设置](view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="0864f-142">For more information, see How to: Create an Updating Subscription to a Transactional Publication (SQL Server Management Studio) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0864f-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0864f-143">See Also</span></span>  
 <span data-ttu-id="0864f-144">[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="0864f-144">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="0864f-145">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="0864f-145">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="0864f-146">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="0864f-146">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
