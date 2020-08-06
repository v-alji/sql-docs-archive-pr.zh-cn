---
title: '&lt;代理名称&gt; 代理安全性 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc72d4380b4d1980da30b8445596e1919a859e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591296"
---
# <a name="ltagentnamegt-agent-security"></a><span data-ttu-id="b4adc-102">&lt;代理名称&gt; 代理安全性</span><span class="sxs-lookup"><span data-stu-id="b4adc-102">&lt;AgentName&gt; Agent Security</span></span>
  <span data-ttu-id="b4adc-103">使用“\<AgentName> 代理安全性”页，可以指定用来运行分发代理（对于事务复制和快照复制）或合并代理（对于合并复制）的帐户，并与复制拓扑中的计算机建立连接。</span><span class="sxs-lookup"><span data-stu-id="b4adc-103">The **\<AgentName> Agent Security** page allows you to specify the accounts under which the Distribution Agent (for transactional and snapshot replication) or Merge Agent (for merge replication) run and make connections to the computers in a replication topology.</span></span> <span data-ttu-id="b4adc-104">有关代理要求的权限及复制安全的最佳做法的信息，请参阅[复制代理安全模型](security/replication-agent-security-model.md)和[复制安全最佳做法](security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="b4adc-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4adc-105">选项</span><span class="sxs-lookup"><span data-stu-id="b4adc-105">Options</span></span>  
 <span data-ttu-id="b4adc-106">单击每个订阅服务器的行中的属性按钮 ( **...** )，可以访问 **“分发代理安全性”** 或 **“合并代理安全性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b4adc-106">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** or **Merge Agent Security** dialog box.</span></span> <span data-ttu-id="b4adc-107">对于代理使用的帐户，有关其所需权限的详细信息，请在启动的对话框中单击 **“帮助”** 。</span><span class="sxs-lookup"><span data-stu-id="b4adc-107">Click **Help** on the dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="b4adc-108">在一个对话框中输入设置后，将在网格中显示订阅服务器的连接信息。</span><span class="sxs-lookup"><span data-stu-id="b4adc-108">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="b4adc-109">**订阅服务器代理**</span><span class="sxs-lookup"><span data-stu-id="b4adc-109">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="b4adc-110">每个订阅服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="b4adc-110">The name of each Subscriber.</span></span>  
  
 <span data-ttu-id="b4adc-111">**与分发服务器的连接**</span><span class="sxs-lookup"><span data-stu-id="b4adc-111">**Connection to Distributor**</span></span>  
 <span data-ttu-id="b4adc-112">为事务复制和快照复制显示。</span><span class="sxs-lookup"><span data-stu-id="b4adc-112">Displayed for transactional and snapshot replication.</span></span> <span data-ttu-id="b4adc-113">连接到分发服务器时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="b4adc-113">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="b4adc-114">本地连接始终使用运行代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户的上下文进行建立：</span><span class="sxs-lookup"><span data-stu-id="b4adc-114">Local connections are always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="b4adc-115">对于推送订阅，本地连接是指与分发服务器的连接，因此此字段将始终显示：模拟“\<Domain>\\<登录名\>”或模拟“\<Computer>\\<登录名\>”（对于推送订阅） 。</span><span class="sxs-lookup"><span data-stu-id="b4adc-115">For push subscriptions, the local connection is the connection to the Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="b4adc-116">对于请求订阅，还可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录的上下文建立连接。</span><span class="sxs-lookup"><span data-stu-id="b4adc-116">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="b4adc-117">该字段显示下列选项之一：使用登录名“\<Login>”、模拟“\<Domain>\\<登录名\>”或模拟“\<Computer>\\<登录名\>”  。</span><span class="sxs-lookup"><span data-stu-id="b4adc-117">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b4adc-118">建议使用 Windows 帐户的上下文建立所有连接。</span><span class="sxs-lookup"><span data-stu-id="b4adc-118">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="b4adc-119">**与发布服务器和分发服务器的连接**</span><span class="sxs-lookup"><span data-stu-id="b4adc-119">**Connection to Publisher & Distributor**</span></span>  
 <span data-ttu-id="b4adc-120">为合并复制显示。</span><span class="sxs-lookup"><span data-stu-id="b4adc-120">Displayed for merge replication.</span></span> <span data-ttu-id="b4adc-121">与发布服务器和分发服务器建立连接时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="b4adc-121">The context under which the connections to the Publisher and Distributor are made.</span></span> <span data-ttu-id="b4adc-122">始终使用运行代理的 Windows 帐户的上下文建立本地连接：</span><span class="sxs-lookup"><span data-stu-id="b4adc-122">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="b4adc-123">对于推送订阅，本地连接是指与发布服务器和分发服务器的连接，因此此字段将始终显示：模拟“\<Domain>\\<登录名\>”或模拟“\<Computer>\\<登录名\>”（对于推送订阅） 。</span><span class="sxs-lookup"><span data-stu-id="b4adc-123">For push subscriptions, the local connection is the connection to the Publisher and Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="b4adc-124">对于请求订阅，还可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录的上下文建立连接。</span><span class="sxs-lookup"><span data-stu-id="b4adc-124">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="b4adc-125">该字段显示下列选项之一：使用登录名“\<Login>”、模拟“\<Domain>\\<登录名\>”或模拟“\<Computer>\\<登录名\>”  。</span><span class="sxs-lookup"><span data-stu-id="b4adc-125">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b4adc-126">建议使用 Windows 帐户的上下文建立所有连接。</span><span class="sxs-lookup"><span data-stu-id="b4adc-126">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="b4adc-127">**与订阅服务器的连接**</span><span class="sxs-lookup"><span data-stu-id="b4adc-127">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="b4adc-128">与订阅服务器建立连接时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="b4adc-128">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="b4adc-129">始终使用运行代理的 Windows 帐户的上下文建立本地连接：</span><span class="sxs-lookup"><span data-stu-id="b4adc-129">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="b4adc-130">对于请求订阅，本地连接是指与订阅服务器的连接，因此此字段将始终显示：模拟“\<Domain>\\<登录名\>”或模拟“\<Computer>\\<登录名\>”（对于推送订阅） 。</span><span class="sxs-lookup"><span data-stu-id="b4adc-130">For pull subscriptions, the local connection is the connection to the Subscriber, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="b4adc-131">对于推送订阅，还可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录的上下文建立连接。</span><span class="sxs-lookup"><span data-stu-id="b4adc-131">For push subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="b4adc-132">该字段显示下列选项之一：使用登录名“\<Login>”、模拟“\<Domain>\\<登录名\>”或模拟“\<Computer>\\<登录名\>”  。</span><span class="sxs-lookup"><span data-stu-id="b4adc-132">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b4adc-133">建议使用 Windows 帐户的上下文建立所有连接。</span><span class="sxs-lookup"><span data-stu-id="b4adc-133">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4adc-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4adc-134">See Also</span></span>  
 <span data-ttu-id="b4adc-135">[查看和修改请求订阅属性](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b4adc-135">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="b4adc-136">[查看和修改推送订阅属性](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b4adc-136">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="b4adc-137">[管理复制中的登录名和密码](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="b4adc-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="b4adc-138">[复制代理安全模式](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="b4adc-138">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 [<span data-ttu-id="b4adc-139">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="b4adc-139">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
