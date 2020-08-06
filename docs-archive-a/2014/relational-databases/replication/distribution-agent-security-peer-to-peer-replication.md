---
title: 分发代理的安全性（对等复制）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72b5a52fbb3ddc11d0ea6f2c0b26786463e08eaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578119"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a><span data-ttu-id="3aed7-102">分发代理的安全性（对等复制）</span><span class="sxs-lookup"><span data-stu-id="3aed7-102">Distribution Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="3aed7-103">使用 **“分发代理安全性”** 页，可以指定运行分发代理以及与对等拓扑中的计算机建立连接时所使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="3aed7-103">The **Distribution Agent Security** page allows you to specify the accounts under which the Distribution Agent runs and makes connections to the computers in a peer-to-peer topology.</span></span> <span data-ttu-id="3aed7-104">有关代理要求的权限及复制安全的最佳做法的信息，请参阅[复制代理安全模型](security/replication-agent-security-model.md)和[复制安全最佳做法](security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="3aed7-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3aed7-105">如果在上次运行此向导时已经对订阅的分发代理进行了配置，则无法更改分发代理在此向导中所使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="3aed7-105">If the Distribution Agent for a subscription has already been configured in a previous run of this wizard, you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="3aed7-106">如果指定新凭据，它们将被忽略。</span><span class="sxs-lookup"><span data-stu-id="3aed7-106">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="3aed7-107">若要更改凭据，请使用 **“订阅属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3aed7-107">To change credentials, use the **Subscription Properties** dialog box.</span></span> <span data-ttu-id="3aed7-108">有关详细信息，请参阅 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="3aed7-108">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3aed7-109">选项</span><span class="sxs-lookup"><span data-stu-id="3aed7-109">Options</span></span>  
 <span data-ttu-id="3aed7-110">单击每个订阅服务器的行中的属性按钮 ( **...** )，可以访问 **“分发代理安全性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3aed7-110">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** dialog box.</span></span> <span data-ttu-id="3aed7-111">对于代理使用的帐户，有关其所需权限的详细信息，请在启动的 **“分发代理安全性”** 对话框中单击 **“帮助”** 。</span><span class="sxs-lookup"><span data-stu-id="3aed7-111">Click **Help** on the **Distribution Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="3aed7-112">在一个对话框中输入设置后，将在网格中显示订阅服务器的连接信息。</span><span class="sxs-lookup"><span data-stu-id="3aed7-112">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="3aed7-113">**订阅服务器代理**</span><span class="sxs-lookup"><span data-stu-id="3aed7-113">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="3aed7-114">每个对等方的名称。</span><span class="sxs-lookup"><span data-stu-id="3aed7-114">The name of each peer.</span></span>  
  
 <span data-ttu-id="3aed7-115">**对等数据库**</span><span class="sxs-lookup"><span data-stu-id="3aed7-115">**Peer Database**</span></span>  
 <span data-ttu-id="3aed7-116">对等方上同时用作发布数据库和订阅数据库的数据库。</span><span class="sxs-lookup"><span data-stu-id="3aed7-116">The database at the peer that will serve as both a publication database and subscription database.</span></span>  
  
 <span data-ttu-id="3aed7-117">**与分发服务器的连接**</span><span class="sxs-lookup"><span data-stu-id="3aed7-117">**Connection to Distributor**</span></span>  
 <span data-ttu-id="3aed7-118">连接到分发服务器时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="3aed7-118">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="3aed7-119">始终使用运行代理的 Windows 帐户的上下文建立本地连接：</span><span class="sxs-lookup"><span data-stu-id="3aed7-119">Local connections are always made using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="3aed7-120">由于此向导将创建推送订阅（本地连接为与分发服务器的连接），因此此字段将始终显示：模拟“\<Domain>\\<登录名\>”或模拟“\<Computer>\\<登录名\>” 。</span><span class="sxs-lookup"><span data-stu-id="3aed7-120">This wizard creates push subscriptions (the local connection is the connection to the Distributor), so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="3aed7-121">**与订阅服务器的连接**</span><span class="sxs-lookup"><span data-stu-id="3aed7-121">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="3aed7-122">与订阅服务器建立连接时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="3aed7-122">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="3aed7-123">可以使用运行代理的 Windows 帐户的上下文或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录的上下文建立连接。</span><span class="sxs-lookup"><span data-stu-id="3aed7-123">The connection can be made using the context of the Windows account under which the agent runs or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="3aed7-124">该字段显示下列选项之一：使用登录名“\<Login>”、模拟“\<Domain><登录名\>”或模拟“\<Computer>\\<登录名\>” **\\** 。</span><span class="sxs-lookup"><span data-stu-id="3aed7-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="3aed7-125">建议使用 Windows 帐户的上下文建立所有连接。</span><span class="sxs-lookup"><span data-stu-id="3aed7-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aed7-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3aed7-126">See Also</span></span>  
 <span data-ttu-id="3aed7-127">[管理对等拓扑（复制 Transact-SQL 编程）](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="3aed7-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="3aed7-128">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="3aed7-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
