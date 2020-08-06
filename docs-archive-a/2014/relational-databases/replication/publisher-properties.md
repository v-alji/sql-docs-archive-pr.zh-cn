---
title: SQL Server 复制发布服务器属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
- sql12.rep.configdistwizard.pubproperties.general.f1
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
- sql12.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e14f82e855cc29f83859d85dfdaaf85a1bda37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689860"
---
# <a name="sql-server-replication-publisher-properties"></a><span data-ttu-id="94fa0-102">SQL Server 复制发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="94fa0-102">SQL Server Replication Publisher Properties</span></span>
  <span data-ttu-id="94fa0-103">本部分包含有关分发服务器和发布服务器上可用的发布服务器属性的信息。</span><span class="sxs-lookup"><span data-stu-id="94fa0-103">This section contains information on Publisher properties available at the Distributor and the Publisher.</span></span> 

## <a name="general"></a><span data-ttu-id="94fa0-104">常规</span><span class="sxs-lookup"><span data-stu-id="94fa0-104">General</span></span>  
  <span data-ttu-id="94fa0-105">**“发布服务器属性”** 对话框的 **“常规”** 页显示有关发布服务器使用的分发服务器和分发数据库的只读信息。</span><span class="sxs-lookup"><span data-stu-id="94fa0-105">The **General** page of the **Publisher Properties** dialog box displays read-only information on the Distributor and distribution database that the Publisher uses.</span></span> <span data-ttu-id="94fa0-106">若要更改发布服务器的分发服务器或分发数据库，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="94fa0-106">To change the Distributor or distribution database for a Publisher:</span></span>  
  
1.  <span data-ttu-id="94fa0-107">禁用发布服务器上的发布。</span><span class="sxs-lookup"><span data-stu-id="94fa0-107">Disable publishing on the Publisher.</span></span> <span data-ttu-id="94fa0-108">有关详细信息，请参阅[禁用发布和分发](disable-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="94fa0-108">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>    
2.  <span data-ttu-id="94fa0-109">重新配置发布和分发。</span><span class="sxs-lookup"><span data-stu-id="94fa0-109">Reconfigure publishing and distribution.</span></span> <span data-ttu-id="94fa0-110">有关详细信息，请参阅 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="94fa0-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  

## <a name="distributor"></a><span data-ttu-id="94fa0-111">分发服务器</span><span class="sxs-lookup"><span data-stu-id="94fa0-111">Distributor</span></span>
  <span data-ttu-id="94fa0-112">使用“发布服务器属性”\*\*\*\* 对话框，可以查看和修改与发布服务器和其分发服务器之间的关系相关联的属性。</span><span class="sxs-lookup"><span data-stu-id="94fa0-112">The **Publisher Properties** dialog box allows you to view and modify properties associated with the relationship between the Publisher and its Distributor.</span></span>  
  
### <a name="options"></a><span data-ttu-id="94fa0-113">选项</span><span class="sxs-lookup"><span data-stu-id="94fa0-113">Options</span></span>  
 <span data-ttu-id="94fa0-114">**到发布服务器的代理连接**</span><span class="sxs-lookup"><span data-stu-id="94fa0-114">**Agent Connection to the Publisher**</span></span>  
 <span data-ttu-id="94fa0-115">指定以下代理从分发服务器连接到发布服务器时所处的上下文：</span><span class="sxs-lookup"><span data-stu-id="94fa0-115">Specify the context under which the following agents make connections from the Distributor to the Publisher:</span></span>  
  
-   <span data-ttu-id="94fa0-116">允许排队更新订阅的事务发布的队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="94fa0-116">The Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="94fa0-117">用于 Oracle 发布的快照代理和日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="94fa0-117">The Snapshot Agent and Log Reader Agent for Oracle publications.</span></span>  
  
 <span data-ttu-id="94fa0-118">选择 **“模拟代理进程帐户”** 以使用运行这些代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户的上下文连接到发布服务器，或指定 **“SQL Server 身份验证”**，然后为 **“登录名”** 和 **“密码”** 输入值。</span><span class="sxs-lookup"><span data-stu-id="94fa0-118">Select **Impersonate agent process account** to make connections to the Publisher using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which these agents run, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> <span data-ttu-id="94fa0-119">建议选择 **“模拟代理进程帐户”**。</span><span class="sxs-lookup"><span data-stu-id="94fa0-119">It is recommended that you select **Impersonate agent process account**.</span></span> <span data-ttu-id="94fa0-120">有关代理安全性的详细信息，请参阅[复制代理安全模式](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="94fa0-120">For more information on agent security, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="94fa0-121">在新建发布向导中可以指定运行这些代理的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="94fa0-121">The Windows accounts under which these agents run are specified in the New Publication Wizard.</span></span> <span data-ttu-id="94fa0-122">您可以在如下位置更改这些帐户：</span><span class="sxs-lookup"><span data-stu-id="94fa0-122">These accounts can be changed:</span></span>  
  
-   <span data-ttu-id="94fa0-123">队列读取器代理的 **“分发服务器属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="94fa0-123">In the **Distributor Properties** dialog box for the Queue Reader Agent.</span></span>  
  
-   <span data-ttu-id="94fa0-124">快照代理和日志读取器代理的 **“发布属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="94fa0-124">In the **Publication Properties** dialog box for the Snapshot Agent and Log Reader Agent.</span></span>  
  
 <span data-ttu-id="94fa0-125">**其他**</span><span class="sxs-lookup"><span data-stu-id="94fa0-125">**Miscellaneous**</span></span>  
 <span data-ttu-id="94fa0-126">**“发布服务器类型”** 和 **“分发数据库名称”** 都是只读属性。</span><span class="sxs-lookup"><span data-stu-id="94fa0-126">The properties **Publisher Type** and **Distribution Database Name** are read-only.</span></span> <span data-ttu-id="94fa0-127">可以更改 **“默认快照文件夹”** 属性。</span><span class="sxs-lookup"><span data-stu-id="94fa0-127">The property **Default Snapshot Folder** can be changed.</span></span> <span data-ttu-id="94fa0-128">有关快照文件夹的详细信息，请参阅[保护快照文件夹](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="94fa0-128">For more information about the snapshot folder, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  

## <a name="publication-databases"></a><span data-ttu-id="94fa0-129">发布数据库</span><span class="sxs-lookup"><span data-stu-id="94fa0-129">Publication Databases</span></span>
  <span data-ttu-id="94fa0-130">通过使用 **“发布服务器属性”** 对话框的 **“发布数据库”** 页， **sysadmin** 固定服务器角色中的用户可以启用数据库以进行复制。</span><span class="sxs-lookup"><span data-stu-id="94fa0-130">The **Publication Databases** page of the **Publisher Properties** dialog box allows a user in the **sysadmin** fixed server role to enable databases for replication.</span></span> <span data-ttu-id="94fa0-131">启用数据库并不会发布相应的数据库；不过，该数据库的 **db_owner** 固定数据库角色中的所有用户都可以对该数据库创建一个或多个发布。</span><span class="sxs-lookup"><span data-stu-id="94fa0-131">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications on the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="94fa0-132">选项</span><span class="sxs-lookup"><span data-stu-id="94fa0-132">Options</span></span>  
 <span data-ttu-id="94fa0-133">**事务性**</span><span class="sxs-lookup"><span data-stu-id="94fa0-133">**Transactional**</span></span>  
 <span data-ttu-id="94fa0-134">选中此复选框后， **db_owner** 固定数据库角色中的用户将可以在数据库中创建快照发布或事务发布。</span><span class="sxs-lookup"><span data-stu-id="94fa0-134">Select this check box to allow users in the **db_owner** fixed database role to create snapshot publications or transactional publications in the database.</span></span> 
  
 <span data-ttu-id="94fa0-135">**合并**</span><span class="sxs-lookup"><span data-stu-id="94fa0-135">**Merge**</span></span>  
 <span data-ttu-id="94fa0-136">选中此复选框后， **db_owner** 固定数据库角色中的用户将可以在数据库中创建合并发布。</span><span class="sxs-lookup"><span data-stu-id="94fa0-136">Select this check box to allow users in the **db_owner** fixed database role to create merge publications in the database.</span></span>  

## <a name="subscribers"></a><span data-ttu-id="94fa0-137">订阅服务器</span><span class="sxs-lookup"><span data-stu-id="94fa0-137">Subscribers</span></span>

  <span data-ttu-id="94fa0-138">“发布服务器属性”对话框的“订阅服务器”页面用于运行版本低于  的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94fa0-138">The **Subscribers** page of the **Publisher Properties** dialog box is used for Publishers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="94fa0-139">使用此页，可以启用订阅服务器以接收此发布服务器上发布的数据。</span><span class="sxs-lookup"><span data-stu-id="94fa0-139">The page allows you to enable Subscribers to receive data from publications on this Publisher.</span></span> <span data-ttu-id="94fa0-140">启用订阅服务器接收此发布服务器的数据，并不会创建对此发布服务器上的发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="94fa0-140">Enabling a Subscriber to receive data from this Publisher does not create subscriptions to publications on this Publisher.</span></span> <span data-ttu-id="94fa0-141">若要创建订阅，必须使用新建订阅向导。</span><span class="sxs-lookup"><span data-stu-id="94fa0-141">To create a subscription, you must use the New Subscription Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="94fa0-142">选项</span><span class="sxs-lookup"><span data-stu-id="94fa0-142">Options</span></span>  
 <span data-ttu-id="94fa0-143">**订阅服务器**</span><span class="sxs-lookup"><span data-stu-id="94fa0-143">**Subscribers**</span></span>  
 <span data-ttu-id="94fa0-144">**“订阅服务器”** 属性网格显示了已启用的从此发布服务器上发布接收数据的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="94fa0-144">The **Subscribers** property grid shows Subscribers that are enabled to receive data from publications on this Publisher.</span></span> <span data-ttu-id="94fa0-145">单击订阅服务器旁边的属性按钮 (**...**) 可以查看和设置其他属性。</span><span class="sxs-lookup"><span data-stu-id="94fa0-145">Click the properties button (**...**) next to a Subscriber to view and set additional properties.</span></span>  
  
 <span data-ttu-id="94fa0-146">**添加**</span><span class="sxs-lookup"><span data-stu-id="94fa0-146">**Add**</span></span>  
 <span data-ttu-id="94fa0-147">单击 **“添加”** 以添加订阅服务器，然后可单击 **“添加 SQL Server 订阅服务器”** 或 **“添加非 SQL Server 订阅服务器”**。</span><span class="sxs-lookup"><span data-stu-id="94fa0-147">Click **Add** to add a Subscriber, and then click **Add SQL Server Subscriber** or **Add Non-SQL Server Subscriber**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="94fa0-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94fa0-148">See Also</span></span>  
 [<span data-ttu-id="94fa0-149">查看和修改分发服务器和发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="94fa0-149">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
