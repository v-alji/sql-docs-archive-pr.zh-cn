---
title: 分发服务器属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
- sql12.rep.configdistwizard.distproperties.general.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
ms.assetid: f643c7c3-f238-4835-b81e-2c2b3b53b23f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 501c7931d651498fea49749be38af374c02424ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578109"
---
# <a name="sql-server-replication-distributor-properties"></a><span data-ttu-id="a2090-102">SQL Server 复制分发服务器属性</span><span class="sxs-lookup"><span data-stu-id="a2090-102">SQL Server Replication Distributor Properties</span></span>
<span data-ttu-id="a2090-103">本主题讨论 "**分发服务器属性**" 窗口中的 "**常规**"、"**发布服务器**" 和 "**分发数据库**" 页上的属性。</span><span class="sxs-lookup"><span data-stu-id="a2090-103">This topic discusses the properties found on the **General**, **Publishers**, and **Distribution Database** pages within the **Distributor Properties** window.</span></span> 

## <a name="general"></a><span data-ttu-id="a2090-104">常规</span><span class="sxs-lookup"><span data-stu-id="a2090-104">General</span></span>
  <span data-ttu-id="a2090-105">使用“分发服务器属性”\*\*\*\* 对话框的“常规”\*\*\*\* 页，可以添加和删除分发数据库，以及设置分发数据库属性。</span><span class="sxs-lookup"><span data-stu-id="a2090-105">The **General** page of the **Distributor Properties** dialog box allows you to add and delete distribution databases and set distribution database properties.</span></span>  
  
 <span data-ttu-id="a2090-106">分发数据库用于存储所有类型复制的元数据和历史记录数据，并存储事务复制的事务。</span><span class="sxs-lookup"><span data-stu-id="a2090-106">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span> <span data-ttu-id="a2090-107">在许多情况下，单个分发数据库就能够满足需要。</span><span class="sxs-lookup"><span data-stu-id="a2090-107">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="a2090-108">不过，如果多个发布服务器使用单个分发服务器，则应考虑为每个发布服务器都创建一个分发数据库。</span><span class="sxs-lookup"><span data-stu-id="a2090-108">But if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="a2090-109">这样可确保通过每个分发数据库的数据流是不同的。</span><span class="sxs-lookup"><span data-stu-id="a2090-109">Doing so ensures that the data flowing through each distribution database is distinct.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a2090-110">选项</span><span class="sxs-lookup"><span data-stu-id="a2090-110">Options</span></span>  
 <span data-ttu-id="a2090-111">**数据库**</span><span class="sxs-lookup"><span data-stu-id="a2090-111">**Databases**</span></span>  
 <span data-ttu-id="a2090-112">**“数据库”** 属性网格显示了分发服务器上分发数据库的名称和保持期属性。</span><span class="sxs-lookup"><span data-stu-id="a2090-112">The **Databases** property grid shows the name and retention properties of the distribution databases on the Distributor.</span></span> <span data-ttu-id="a2090-113">**“事务保持期”** 是指为事务复制存储事务的时间长度（事务保持期也称为分发保持期）。</span><span class="sxs-lookup"><span data-stu-id="a2090-113">**Transaction Retention** is the length of time transactions are stored for transactional replication (transaction retention is also known as distribution retention).</span></span> <span data-ttu-id="a2090-114">**“历史记录保持期”** 是指为所有类型的复制存储历史记录元数据的时间长度。</span><span class="sxs-lookup"><span data-stu-id="a2090-114">**History Retention** is the length of time history metadata is stored for all types of replication.</span></span> <span data-ttu-id="a2090-115">有关分发保持期的详细信息，请参阅[订阅过期和停用](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="a2090-115">For more information about distribution retention, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="a2090-116">单击 **“数据库”** 属性网格中的属性按钮 ( **...** ) 可启动 **“分发数据库属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a2090-116">Click the properties button (**...**) in the **Databases** property grid to launch the **Distribution Database Properties** dialog box.</span></span>  
  
 <span data-ttu-id="a2090-117">**新建**</span><span class="sxs-lookup"><span data-stu-id="a2090-117">**New**</span></span>  
 <span data-ttu-id="a2090-118">单击此项可创建一个新的分发数据库。</span><span class="sxs-lookup"><span data-stu-id="a2090-118">Click to create a new distribution database.</span></span>  
  
 <span data-ttu-id="a2090-119">**删除**</span><span class="sxs-lookup"><span data-stu-id="a2090-119">**Delete**</span></span>  
 <span data-ttu-id="a2090-120">选择 **“数据库”** 属性网格中的一个现有分发数据库，再单击 **“删除”** ，即可删除该数据库。</span><span class="sxs-lookup"><span data-stu-id="a2090-120">Select an existing distribution database in the **Databases** property grid, and click **Delete** to delete the database.</span></span> <span data-ttu-id="a2090-121">如果只有一个这样的分发数据库，则无法删除；每个分发服务器必须至少有一个分发数据库。</span><span class="sxs-lookup"><span data-stu-id="a2090-121">You cannot delete the distribution database if there is only one such database; each Distributor must have at least one distribution database.</span></span> <span data-ttu-id="a2090-122">若要删除所有分发数据库，则必须在该计算机上禁用分发功能。</span><span class="sxs-lookup"><span data-stu-id="a2090-122">To delete all distribution databases, you must disable distribution on the computer.</span></span> <span data-ttu-id="a2090-123">有关详细信息，请参阅[禁用发布和分发](disable-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="a2090-123">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="a2090-124">**默认配置文件**</span><span class="sxs-lookup"><span data-stu-id="a2090-124">**Profile Defaults**</span></span>  
 <span data-ttu-id="a2090-125">单击此项可访问 **“代理配置文件”** 对话框中的复制代理配置文件。</span><span class="sxs-lookup"><span data-stu-id="a2090-125">Click to access replication agent profiles in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="a2090-126">有关配置文件的详细信息，请参阅 [Replication Agent Profiles](agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a2090-126">For more information about profiles, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  

## <a name="publishers"></a><span data-ttu-id="a2090-127">发布者</span><span class="sxs-lookup"><span data-stu-id="a2090-127">Publishers</span></span>

  <span data-ttu-id="a2090-128">可以使用 **“分发服务器属性”** 对话框的 **“发布服务器”** 页，允许发布服务器使用此分发服务器。</span><span class="sxs-lookup"><span data-stu-id="a2090-128">The **Publishers** page of the **Distributor Properties** dialog box allows you to enable Publishers to use this Distributor.</span></span> <span data-ttu-id="a2090-129">还可以设置与这些发布服务器关联的属性。</span><span class="sxs-lookup"><span data-stu-id="a2090-129">You can also set properties associated with those Publishers.</span></span> <span data-ttu-id="a2090-130">请注意，允许发布服务器将此服务器用作其远程分发服务器的同时，并不会使该服务器成为发布服务器。</span><span class="sxs-lookup"><span data-stu-id="a2090-130">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="a2090-131">必须连接到发布服务器，对其进行配置以用于发布，并选择此服务器作为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="a2090-131">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="a2090-132">您可以通过新建发布向导配置发布服务器并选择分发服务器。</span><span class="sxs-lookup"><span data-stu-id="a2090-132">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a2090-133">选项</span><span class="sxs-lookup"><span data-stu-id="a2090-133">Options</span></span>  
 <span data-ttu-id="a2090-134">**发布服务器**</span><span class="sxs-lookup"><span data-stu-id="a2090-134">**Publishers**</span></span>  
 <span data-ttu-id="a2090-135">选择允许使用此分发服务器的服务器。</span><span class="sxs-lookup"><span data-stu-id="a2090-135">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="a2090-136">单击发布服务器旁边的属性按钮 **(...)** 可以查看和设置其他属性。</span><span class="sxs-lookup"><span data-stu-id="a2090-136">Click the Properties button **(...)** next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="a2090-137">**添加**</span><span class="sxs-lookup"><span data-stu-id="a2090-137">**Add**</span></span>  
 <span data-ttu-id="a2090-138">如果希望允许的服务器没有列出，请单击“添加”向可用发布服务器列表中添加 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器或 Oracle 发布服务器\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a2090-138">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span> <span data-ttu-id="a2090-139">如果添加的服务器是使用此分发服务器作为远程分发服务器的第一个服务器，则系统将会提示您提供管理链接密码。</span><span class="sxs-lookup"><span data-stu-id="a2090-139">If the server you add is the first server to use this Distributor as a remote Distributor, you are prompted to provide an administrative link password.</span></span>  
  
 <span data-ttu-id="a2090-140">**管理链接密码**</span><span class="sxs-lookup"><span data-stu-id="a2090-140">**Administrative link password**</span></span>  
 <span data-ttu-id="a2090-141">对于使用 **distributor_admin** 登录名在发布服务器和远程分发服务器之间进行的连接复制，使用此选项可以为其指定或更新密码：</span><span class="sxs-lookup"><span data-stu-id="a2090-141">Use to specify or update the password for the connection replication makes between the Publisher and the remote Distributor using the **distributor_admin** login:</span></span>  
  
-   <span data-ttu-id="a2090-142">如果分发服务器仅用作本地分发服务器，则会随机生成并自动配置此密码。</span><span class="sxs-lookup"><span data-stu-id="a2090-142">If the Distributor serves only as a local Distributor, this password is randomly generated and automatically configured.</span></span>  
-   <span data-ttu-id="a2090-143">如果分发服务器已具有远程发布服务器，则密码已在此页上或配置分发向导的 **“分发服务器密码”** 页上提供。</span><span class="sxs-lookup"><span data-stu-id="a2090-143">If the Distributor already has a remote Publisher, a password was initially supplied on this page or the **Distributor Password** page of the Configure Distribution Wizard.</span></span>    
-   <span data-ttu-id="a2090-144">如果为此分发服务器启用第一个远程发布服务器，则系统将会提示您输入密码。</span><span class="sxs-lookup"><span data-stu-id="a2090-144">If you enable the first remote Publisher for this Distributor, you are prompted to enter a password.</span></span>  
  
 <span data-ttu-id="a2090-145">有关分发服务器的安全性的详细信息，请参阅[保护分发服务器](security/secure-the-distributor.md)。</span><span class="sxs-lookup"><span data-stu-id="a2090-145">For more information on security for Distributors, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  

## <a name="distribution-database"></a><span data-ttu-id="a2090-146">分发数据库</span><span class="sxs-lookup"><span data-stu-id="a2090-146">Distribution Database</span></span>
 <span data-ttu-id="a2090-147">可使用“分发数据库属性”对话框查看数据库的多个属性，以及为数据库设置事务保持期和历史记录保持期\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a2090-147">The **Distribution Database Properties** dialog box allows you to view a number of properties and to set the transaction retention period and history retention period for the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a2090-148">选项</span><span class="sxs-lookup"><span data-stu-id="a2090-148">Options</span></span>  
 <span data-ttu-id="a2090-149">**名称**</span><span class="sxs-lookup"><span data-stu-id="a2090-149">**Name**</span></span>  
 <span data-ttu-id="a2090-150">分发数据库的名称，默认值为“distribution”（只读）。</span><span class="sxs-lookup"><span data-stu-id="a2090-150">The name of the distribution database, which defaults to 'distribution' (read-only).</span></span>  
  
 <span data-ttu-id="a2090-151">**文件位置**</span><span class="sxs-lookup"><span data-stu-id="a2090-151">**File locations**</span></span>  
 <span data-ttu-id="a2090-152">数据库文件和日志文件的位置（只读）。</span><span class="sxs-lookup"><span data-stu-id="a2090-152">The location of the database file and the log file (read-only).</span></span>  
  
 <span data-ttu-id="a2090-153">**事务保持期**</span><span class="sxs-lookup"><span data-stu-id="a2090-153">**Transaction retention period**</span></span>  
 <span data-ttu-id="a2090-154">也称为分发保持期。</span><span class="sxs-lookup"><span data-stu-id="a2090-154">Also known as the distribution retention period.</span></span> <span data-ttu-id="a2090-155">为事务复制存储的事务时间长度。</span><span class="sxs-lookup"><span data-stu-id="a2090-155">The length of time transactions are stored for transactional replication.</span></span> <span data-ttu-id="a2090-156">有关详细信息，请参阅 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="a2090-156">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="a2090-157">**历史记录保持期**</span><span class="sxs-lookup"><span data-stu-id="a2090-157">**History retention period**</span></span>  
 <span data-ttu-id="a2090-158">为所有类型的复制存储的历史记录元数据的时间长度。</span><span class="sxs-lookup"><span data-stu-id="a2090-158">The length of time history metadata is stored for all types of replication.</span></span>  
  
 <span data-ttu-id="a2090-159">**队列读取器代理安全性**</span><span class="sxs-lookup"><span data-stu-id="a2090-159">**Queue Reader Agent security**</span></span>  
 <span data-ttu-id="a2090-160">队列读取器代理由带有排队更新订阅的事务复制使用。</span><span class="sxs-lookup"><span data-stu-id="a2090-160">The Queue Reader Agent is used by transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="a2090-161">如果在新建发布向导的 **“发布类型”** 页上选择 **“带有更新订阅的事务发布”** ，将自动创建队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="a2090-161">A Queue Reader Agent is created automatically if you select **Transactional publication with updating subscriptions** on the **Publication Type** page of the New Publication Wizard.</span></span> <span data-ttu-id="a2090-162">单击“安全设置…”可以更改运行代理并连接到分发服务器时所使用的帐户\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a2090-162">Click **Security Settings...** to change the account under which the agent runs and makes connections to the Distributor.</span></span>  
  
 <span data-ttu-id="a2090-163">还可以在此页上选择 **“创建队列读取器代理”** （如果已创建该代理，此选项将被禁用），来创建队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="a2090-163">A Queue Reader Agent can also be created by selecting **Create Queue Reader Agent** on this page (this option is disabled if the agent has already been created).</span></span>  
  
 <span data-ttu-id="a2090-164">下面两点说明了队列读取器代理的其他连接信息：</span><span class="sxs-lookup"><span data-stu-id="a2090-164">Additional connection information for the Queue Reader Agent is specified in two places:</span></span>    
-   <span data-ttu-id="a2090-165">使用 **“发布服务器属性”** 对话框中指定的凭据，该代理可以连接到发布服务器。该对话框可以在 **“分发服务器属性”** 对话框的 **“发布服务器”** 页中找到。</span><span class="sxs-lookup"><span data-stu-id="a2090-165">The agent connects to the Publisher using the credentials specified in the **Publisher Properties** dialog box, which is available from the **Publishers** page of the **Distributor Properties** dialog box.</span></span>    
-   <span data-ttu-id="a2090-166">使用在新建订阅向导中为分发代理指定的凭据，该代理可以连接到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="a2090-166">The agent connects to the Subscriber using the credentials specified for the Distribution Agent in the New Subscription Wizard.</span></span>  
  
 <span data-ttu-id="a2090-167">有关详细信息，请参阅 \\ [复制代理安全模式](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a2090-167">For more information, see  \\[Replication Agent Security Model](security/replication-agent-security-model.md).</span></span> 

  
## <a name="see-also"></a><span data-ttu-id="a2090-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2090-168">See Also</span></span>  
 <span data-ttu-id="a2090-169">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="a2090-169">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="a2090-170">查看和修改分发服务器和发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="a2090-170">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
