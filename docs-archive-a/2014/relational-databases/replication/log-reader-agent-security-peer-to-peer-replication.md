---
title: 日志读取器代理安全性（对等复制）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dfef98adb622f9da922af0c1cdbb1cf8b7a07da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588991"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a><span data-ttu-id="6277e-102">日志读取器代理的安全性（对等复制）</span><span class="sxs-lookup"><span data-stu-id="6277e-102">Log Reader Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="6277e-103">可以使用 **“日志读取器代理安全性”** 页，指定日志读取器代理在各对等方运行和建立连接时使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="6277e-103">The **Log Reader Agent Security** page allows you to specify the accounts under which the Log Reader Agent at each peer runs and makes connections.</span></span> <span data-ttu-id="6277e-104">有关代理要求的权限及复制安全的最佳做法的信息，请参阅[复制代理安全模型](security/replication-agent-security-model.md)和[复制安全最佳做法](security/replication-security-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="6277e-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6277e-105">对于使用事务复制发布的每个数据库，都有一个日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="6277e-105">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="6277e-106">如果已经配置数据库的日志读取器代理（不管是在上一次运行此向导时针对发布配置的，还是针对同一数据库中另一个事务发布配置的），则不能在此向导中更改该代理使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="6277e-106">If the Log Reader Agent for a database has already been configured (either for a publication in a previous run of this wizard or for another transactional publication in the same database), you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="6277e-107">如果指定新凭据，它们将被忽略。</span><span class="sxs-lookup"><span data-stu-id="6277e-107">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="6277e-108">若要更改凭据，请使用 **“发布属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="6277e-108">To change credentials, use the **Publication Properties** dialog box.</span></span> <span data-ttu-id="6277e-109">有关详细信息，请参阅 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="6277e-109">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6277e-110">选项</span><span class="sxs-lookup"><span data-stu-id="6277e-110">Options</span></span>  
 <span data-ttu-id="6277e-111">在各对等方的行中单击属性按钮 ( **...** )，可以访问 **“日志读取器代理安全性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="6277e-111">Click the properties button (**...**) in the row for each peer to access the **Log Reader Agent Security** dialog box.</span></span> <span data-ttu-id="6277e-112">若要了解有关代理所使用帐户需要的权限的详细信息，请在 **“日志读取器代理安全性”** 对话框启动后单击其中的 **“帮助”** 。</span><span class="sxs-lookup"><span data-stu-id="6277e-112">Click **Help** on the **Log Reader Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="6277e-113">在对话框中输入设置之后，网格中将显示订阅服务器的连接信息。</span><span class="sxs-lookup"><span data-stu-id="6277e-113">After settings have been entered in the dialog box, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="6277e-114">**发布服务器的代理**</span><span class="sxs-lookup"><span data-stu-id="6277e-114">**Agents for Publisher**</span></span>  
 <span data-ttu-id="6277e-115">每个对等服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="6277e-115">The name of each peer server instance.</span></span>  
  
 <span data-ttu-id="6277e-116">**对等数据库**</span><span class="sxs-lookup"><span data-stu-id="6277e-116">**Peer Database**</span></span>  
 <span data-ttu-id="6277e-117">各对等方上用作发布数据库和订阅数据库的数据库。</span><span class="sxs-lookup"><span data-stu-id="6277e-117">The database that serves as the publication database and subscription database at each peer.</span></span>  
  
 <span data-ttu-id="6277e-118">**与分发服务器的连接**</span><span class="sxs-lookup"><span data-stu-id="6277e-118">**Connection to Distributor**</span></span>  
 <span data-ttu-id="6277e-119">连接到分发服务器时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="6277e-119">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="6277e-120">与分发服务器的本地连接始终是使用运行代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户的上下文建立的，因此，此字段将始终显示“模拟‘\<Domain>\\<登录名\>’”或“模拟‘\<Computer>\\<登录名\>’”。</span><span class="sxs-lookup"><span data-stu-id="6277e-120">The local connection to the Distributor is always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs, so this field will always display **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="6277e-121">**与发布服务器的连接**</span><span class="sxs-lookup"><span data-stu-id="6277e-121">**Connection to Publisher**</span></span>  
 <span data-ttu-id="6277e-122">与发布服务器建立连接时所处的上下文。</span><span class="sxs-lookup"><span data-stu-id="6277e-122">The context under which the connection to the Publisher is made.</span></span> <span data-ttu-id="6277e-123">通过使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名，或使用运行代理的 Windows 帐户的上下文，可以与发布服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="6277e-123">The connection to the Publisher can be made using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="6277e-124">该字段显示下列选项之一：使用登录名“\<Login>”、模拟“\<Domain><登录名\>”或模拟“\<Computer>\\<登录名\>” **\\** 。</span><span class="sxs-lookup"><span data-stu-id="6277e-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6277e-125">建议使用 Windows 帐户的上下文建立所有连接。</span><span class="sxs-lookup"><span data-stu-id="6277e-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6277e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6277e-126">See Also</span></span>  
 <span data-ttu-id="6277e-127">[管理对等拓扑（复制 Transact-SQL 编程）](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="6277e-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="6277e-128">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="6277e-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
