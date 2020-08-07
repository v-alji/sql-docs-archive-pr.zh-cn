---
title: 订阅服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c5281a53b755bc171cdf96e7856e38ee6a54a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580114"
---
# <a name="subscribers"></a><span data-ttu-id="23211-102">订阅服务器</span><span class="sxs-lookup"><span data-stu-id="23211-102">Subscribers</span></span>
  <span data-ttu-id="23211-103">指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将接收对所选发布的订阅的或非订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="23211-103">Specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers that will receive a subscription to the selected publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="23211-104">选项</span><span class="sxs-lookup"><span data-stu-id="23211-104">Options</span></span>  
 <span data-ttu-id="23211-105">**“发布服务器属性”**</span><span class="sxs-lookup"><span data-stu-id="23211-105">**Subscribers**</span></span>  
 <span data-ttu-id="23211-106">选中网格中的复选框可以启用相应的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源作为 **“发布”** 页上所选发布的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="23211-106">Select the check box in the grid to enable the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source as a Subscriber to the publication chosen on the **Publication** page.</span></span> <span data-ttu-id="23211-107">如果没有列出订阅服务器，请单击 **“添加订阅服务器”** 或 **“添加 SQL Server 订阅服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="23211-107">If the Subscriber is not listed, click **Add Subscriber** or **Add SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="23211-108">**订阅数据库**</span><span class="sxs-lookup"><span data-stu-id="23211-108">**Subscription database**</span></span>  
 <span data-ttu-id="23211-109">此列中显示的信息和其中可用的操作取决于 **“订阅服务器”** 列中所列的订阅服务器的类型：</span><span class="sxs-lookup"><span data-stu-id="23211-109">The information displayed in and actions available from this column depend on the type of Subscriber listed in the **Subscribers** column:</span></span>  
  
-   <span data-ttu-id="23211-110">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器，请从 **“订阅数据库”** 列表中选择订阅数据库，或从同一列表中选择 **“新建数据库”** 命令来创建新的数据库。</span><span class="sxs-lookup"><span data-stu-id="23211-110">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, select a subscription database from the **Subscription Database** list or create a new database by selecting the **New database** command from the same list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23211-111">若要启用发布服务器作为订阅服务器，则订阅数据库与发布数据库必须属于不同的数据库。</span><span class="sxs-lookup"><span data-stu-id="23211-111">If you are enabling the Publisher as a Subscriber, the subscription database must be different from the publication database.</span></span>  
  
-   <span data-ttu-id="23211-112">对于非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器，不显示订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="23211-112">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, the subscription database is not displayed.</span></span> <span data-ttu-id="23211-113">请在 **“添加非 SQL Server 订阅服务器”** 对话框的 **“数据源名称”** 字段中指定数据库以及其他连接信息。</span><span class="sxs-lookup"><span data-stu-id="23211-113">Specify the database, along with other connection information, in the **Data source name** field of the **Add Non-SQL Server** dialog box.</span></span> <span data-ttu-id="23211-114">若要显示此对话框，请单击 **“添加订阅服务器”** ，再单击 **“添加非 SQL Server 订阅服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="23211-114">This dialog box is available by clicking **Add Subscriber** and then clicking **Add Non-SQL Server Subscriber**.</span></span>  
  
 <span data-ttu-id="23211-115">**“添加订阅服务器”**</span><span class="sxs-lookup"><span data-stu-id="23211-115">**Add Subscriber**</span></span>  
 <span data-ttu-id="23211-116">向可以启用为订阅服务器的服务器列表中添加服务器。</span><span class="sxs-lookup"><span data-stu-id="23211-116">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="23211-117">如果以下条件全部为真，则显示此按钮：</span><span class="sxs-lookup"><span data-stu-id="23211-117">This button is displayed when all of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="23211-118">所选择的发布是不支持更新订阅的快照或事务发布。</span><span class="sxs-lookup"><span data-stu-id="23211-118">The publication you selected is a snapshot or transactional publication that does not support updating subscriptions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23211-119">如果正在订阅的发布有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅，并且尚未为非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器启用发布，则不能添加非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅。</span><span class="sxs-lookup"><span data-stu-id="23211-119">If the publication you are subscribing to has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscriptions and the publication is not already enabled for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, you cannot add a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] subscription.</span></span>  
  
-   <span data-ttu-id="23211-120">订阅是推送订阅。</span><span class="sxs-lookup"><span data-stu-id="23211-120">The subscription is a push subscription.</span></span>  
  
-   <span data-ttu-id="23211-121">所选发布的发布服务器是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="23211-121">The Publisher of the selected publication is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span>  
  
 <span data-ttu-id="23211-122">单击 **“添加订阅服务器”** 将显示一个菜单，其中包含两个选项： **“添加 SQL Server 订阅服务器”** 和 **“添加非 SQL Server 订阅服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="23211-122">Clicking **Add Subscriber** shows a menu with two choices: **Add SQL Server Subscriber** and **Add Non-SQL Server Subscriber**.</span></span> <span data-ttu-id="23211-123">单击 **“添加非 SQL Server 订阅服务器”** 可以添加 Oracle 或 IBM DB2 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="23211-123">Click **Add Non-SQL Server Subscriber** to add an Oracle or IBM DB2 Subscriber.</span></span>  
  
 <span data-ttu-id="23211-124">**“添加 SQL Server 订阅服务器”**</span><span class="sxs-lookup"><span data-stu-id="23211-124">**Add SQL Server Subscriber**</span></span>  
 <span data-ttu-id="23211-125">向可以启用为订阅服务器的服务器列表中添加服务器。</span><span class="sxs-lookup"><span data-stu-id="23211-125">Add a server to the list of servers that can be enabled as Subscribers.</span></span> <span data-ttu-id="23211-126">如果以下一个或多个条件为真，则显示此按钮：</span><span class="sxs-lookup"><span data-stu-id="23211-126">This button is displayed when one or more of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="23211-127">所选择的发布是合并发布，或者是支持更新订阅的快照或事务发布。</span><span class="sxs-lookup"><span data-stu-id="23211-127">The publication you selected is a merge publication, or a snapshot or transactional publication that supports updating subscriptions.</span></span>  
  
-   <span data-ttu-id="23211-128">订阅是请求订阅。</span><span class="sxs-lookup"><span data-stu-id="23211-128">The subscription is a pull subscription.</span></span>  
  
-   <span data-ttu-id="23211-129">所选发布的发布服务器的版本早于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23211-129">The Publisher of the selected publication is earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="23211-130">对于早期版本，只有当以下一个或多个条件为真时才会显示该按钮：</span><span class="sxs-lookup"><span data-stu-id="23211-130">For earlier versions, the button is displayed only if one or more of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="23211-131">您是发布服务器上 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="23211-131">You are a member of the **sysadmin** fixed server role at the Publisher.</span></span>  
  
    -   <span data-ttu-id="23211-132">已在 **“发布服务器属性”** 对话框的 **“订阅服务器”** 页上添加了该订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="23211-132">The Subscriber has been added on the **Subscribers** page of the **Publisher Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="23211-133">发布允许匿名订阅。</span><span class="sxs-lookup"><span data-stu-id="23211-133">The publication allows anonymous subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23211-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23211-134">See Also</span></span>  
 <span data-ttu-id="23211-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="23211-135">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="23211-136">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="23211-136">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="23211-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="23211-137">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="23211-138">订阅发布</span><span class="sxs-lookup"><span data-stu-id="23211-138">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
