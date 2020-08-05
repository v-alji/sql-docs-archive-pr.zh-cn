---
title: 代理安全性（新建发布向导）| Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a0da30cb49a73024ca83d8587a4f6477d21c49c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580156"
---
# <a name="agent-security-new-publication-wizard"></a><span data-ttu-id="df853-102">代理安全性（新建发布向导）</span><span class="sxs-lookup"><span data-stu-id="df853-102">Agent Security (New Publication Wizard)</span></span>
  <span data-ttu-id="df853-103">可以使用 **“代理安全性”** 页指定运行以下代理的帐户，以及连接到复制拓扑中的计算机：</span><span class="sxs-lookup"><span data-stu-id="df853-103">The **Agent Security** page allows you to specify the accounts under which the following agents run and make connections to the computers in a replication topology:</span></span>  
  
-   <span data-ttu-id="df853-104">所有发布的快照代理。</span><span class="sxs-lookup"><span data-stu-id="df853-104">The Snapshot Agent for all publications.</span></span>  
  
-   <span data-ttu-id="df853-105">所有事务发布的日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="df853-105">The Log Reader Agent for all transactional publications.</span></span>  
  
-   <span data-ttu-id="df853-106">允许可更新订阅的事务发布的队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="df853-106">The Queue Reader Agent for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="df853-107">如果你在“发布类型”页上指定了“具有可更新订阅的事务发布”，那么不管使用何种类型的可更新订阅，都将为此代理创建 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业 。</span><span class="sxs-lookup"><span data-stu-id="df853-107">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job for this agent is created if you specified **Transactional publication with updatable subscriptions** on the **Publication Type** page, regardless of the type of updatable subscriptions you use.</span></span> <span data-ttu-id="df853-108">有关可更新订阅的详细信息，请参阅 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="df853-108">For more information about updatable subscriptions, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="df853-109">有关代理要求的权限及复制安全的最佳实践的信息，请参阅 [Replication Agent Security Model](security/replication-agent-security-model.md) 和 [Replication Security Best Practices](security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="df853-109">For information about permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="df853-110">选项</span><span class="sxs-lookup"><span data-stu-id="df853-110">Options</span></span>  
 <span data-ttu-id="df853-111">**快照代理**</span><span class="sxs-lookup"><span data-stu-id="df853-111">**Snapshot Agent**</span></span>  
 <span data-ttu-id="df853-112">所有发布都将显示此选项。</span><span class="sxs-lookup"><span data-stu-id="df853-112">Displayed for all publications.</span></span> <span data-ttu-id="df853-113">单击 **“安全设置”** ，可以指定 **“快照代理安全性”** 对话框中的安全设置。</span><span class="sxs-lookup"><span data-stu-id="df853-113">Click **Security Settings** to specify security settings in the **Snapshot Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="df853-114">单击 **“快照代理安全性”** 对话框中的 **“帮助”** ，可以获得快照代理使用的帐户所需权限的详细信息。</span><span class="sxs-lookup"><span data-stu-id="df853-114">Click **Help** on the **Snapshot Agent Security** dialog box for more information about the permissions required for accounts used by the Snapshot Agent.</span></span>  
  
 <span data-ttu-id="df853-115">**日志读取器代理**</span><span class="sxs-lookup"><span data-stu-id="df853-115">**Log Reader Agent**</span></span>  
 <span data-ttu-id="df853-116">所有事务发布都将显示此选项。</span><span class="sxs-lookup"><span data-stu-id="df853-116">Displayed for all transactional publications.</span></span> <span data-ttu-id="df853-117">单击 **“安全设置”** ，可以指定 **“日志读取器代理安全性”** 对话框中的安全设置。</span><span class="sxs-lookup"><span data-stu-id="df853-117">Click **Security Settings** to specify security settings in the **Log Reader Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="df853-118">单击 **“日志读取器代理安全性”** 对话框中的 **“帮助”** ，可以获得日志读取器代理使用的帐户所需权限的详细信息。</span><span class="sxs-lookup"><span data-stu-id="df853-118">Click **Help** on the **Log Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Log Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df853-119">对于使用事务复制发布的每个数据库，都有一个日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="df853-119">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="df853-120">如果数据库中已经存在事务发布，则安全设置是只读的。</span><span class="sxs-lookup"><span data-stu-id="df853-120">If a transactional publication already exists in the database, the security settings are read-only.</span></span> <span data-ttu-id="df853-121">您可以更改 **“发布属性”** 对话框中的设置，但是此更改会影响数据库中的所有事务发布。</span><span class="sxs-lookup"><span data-stu-id="df853-121">You can change the settings in the **Publication Properties** dialog box, but changes affect all transactional publications in the database.</span></span>  
  
 <span data-ttu-id="df853-122">**队列读取器代理**</span><span class="sxs-lookup"><span data-stu-id="df853-122">**Queue Reader Agent**</span></span>  
 <span data-ttu-id="df853-123">允许可更新订阅的事务发布都将显示此选项。</span><span class="sxs-lookup"><span data-stu-id="df853-123">Displayed for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="df853-124">单击 **“安全设置”** ，可以指定 **“队列读取器代理安全性”** 对话框中的安全设置。</span><span class="sxs-lookup"><span data-stu-id="df853-124">Click **Security Settings** to specify security settings in the **Queue Reader Agent Security** dialog box.</span></span> <span data-ttu-id="df853-125">此向导完成时将创建队列读取器代理作业；而不会取决于您创建的任意排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="df853-125">A Queue Reader Agent job is created when this wizard completes; it does not depend on you creating any queued updating subscriptions.</span></span> <span data-ttu-id="df853-126">如果您不打算创建任何排队更新订阅，那么可以禁用该作业。</span><span class="sxs-lookup"><span data-stu-id="df853-126">If you do not plan to create any queued updating subscriptions, you can disable the job.</span></span> <span data-ttu-id="df853-127">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的“作业”文件夹中右键单击该作业（命名格式为 [\<Publisher>].\<integer>），然后单击“禁用” 。</span><span class="sxs-lookup"><span data-stu-id="df853-127">Right-click the job (named in the form: *[\<Publisher>].\<integer>*.) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **Jobs** folder, and then click **Disable**.</span></span>  
  
 <span data-ttu-id="df853-128">单击 **“队列读取器代理安全性”** 对话框中的 **“帮助”** ，可以获得队列读取器代理使用的帐户所需权限的详细信息。</span><span class="sxs-lookup"><span data-stu-id="df853-128">Click **Help** on the **Queue Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Queue Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df853-129">每个分发数据库（及其所有发布服务器）都具有一个队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="df853-129">There is one Queue Reader Agent for each distribution database (and all Publishers that it serves).</span></span> <span data-ttu-id="df853-130">如果使用给定分发数据库的任意发布服务器中已存在允许排队更新订阅的事务发布，则安全设置是只读的。</span><span class="sxs-lookup"><span data-stu-id="df853-130">If a transactional publication that allows queued updating subscriptions already exists on any of the Publishers that use a given distribution database, the security settings are read-only.</span></span> <span data-ttu-id="df853-131">可以在 **“分发服务器属性”** 对话框中更改运行队列读取器代理并建立连接的帐户，但是此更改会影响使用分发数据库的所有发布服务器中的发布。</span><span class="sxs-lookup"><span data-stu-id="df853-131">You can change the account under which the Queue Reader Agent runs and makes connections in the **Distributor Properties** dialog box, but changes affect publications at all Publishers that use the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df853-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df853-132">See Also</span></span>  
 <span data-ttu-id="df853-133">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="df853-133">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="df853-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="df853-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="df853-135">[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="df853-135">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 <span data-ttu-id="df853-136">[查看和修改发布属性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="df853-136">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="df853-137">[管理复制中的登录名和密码](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="df853-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="df853-138">[发布数据和数据库对象](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="df853-138">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="df853-139">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="df853-139">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
