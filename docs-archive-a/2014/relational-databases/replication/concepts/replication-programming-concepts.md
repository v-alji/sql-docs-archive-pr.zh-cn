---
title: 复制编程概念 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- replication [SQL Server], planning
- programming [SQL Server replication], planning
- programming [SQL Server replication]
ms.assetid: 2cd846e7-5bf3-4144-8772-703c4f439a2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db4ab6196c138eaf21de08afc27731225df398e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586616"
---
# <a name="replication-programming-concepts"></a><span data-ttu-id="4fb83-102">复制编程概念</span><span class="sxs-lookup"><span data-stu-id="4fb83-102">Replication Programming Concepts</span></span>
  <span data-ttu-id="4fb83-103">在开发使用复制功能的应用程序之前，应该先完成以下常规计划步骤：</span><span class="sxs-lookup"><span data-stu-id="4fb83-103">Before developing an application that uses replication functionalities, you should follow the following general planning steps:</span></span>  
  
1.  <span data-ttu-id="4fb83-104">定义复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="4fb83-104">Define your replication topology.</span></span>  
  
2.  <span data-ttu-id="4fb83-105">定义应用程序功能。</span><span class="sxs-lookup"><span data-stu-id="4fb83-105">Define application functionality.</span></span>  
  
3.  <span data-ttu-id="4fb83-106">规划安全性。</span><span class="sxs-lookup"><span data-stu-id="4fb83-106">Plan for security.</span></span>  
  
4.  <span data-ttu-id="4fb83-107">选择开发环境。</span><span class="sxs-lookup"><span data-stu-id="4fb83-107">Choose a development environment.</span></span>  
  
5.  <span data-ttu-id="4fb83-108">选择合适的复制编程接口。</span><span class="sxs-lookup"><span data-stu-id="4fb83-108">Choose the appropriate replication programming interface.</span></span>  
  
 <span data-ttu-id="4fb83-109">下面，本主题将对这些步骤进行更为详细地说明。</span><span class="sxs-lookup"><span data-stu-id="4fb83-109">The rest of this topic describes these steps in more detail.</span></span> <span data-ttu-id="4fb83-110">为了阐明计划的过程，本主题还提供了一个示例。</span><span class="sxs-lookup"><span data-stu-id="4fb83-110">To help illustrate the planning process, an example has been included.</span></span>  
  
## <a name="defining-the-replication-topology"></a><span data-ttu-id="4fb83-111">定义复制拓扑</span><span class="sxs-lookup"><span data-stu-id="4fb83-111">Defining the Replication Topology</span></span>  
 <span data-ttu-id="4fb83-112">复制编程的第一步是为应用程序定义复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="4fb83-112">The first step in programming replication is to define the replication topology for your application.</span></span> <span data-ttu-id="4fb83-113">如果您要编写使用现有复制拓扑的应用程序，如访问现有订阅服务器上数据的客户端应用程序，则可以直接跳到下一步。</span><span class="sxs-lookup"><span data-stu-id="4fb83-113">If you are writing an application that will use an existing replication topology, such as a client application that accesses data at an existing subscriber, you should move onto the next step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fb83-114">在某些情况下，部署复制拓扑是应用程序的唯一目的。</span><span class="sxs-lookup"><span data-stu-id="4fb83-114">In some cases, deploying the replication topology will be the sole purpose of the application.</span></span>  
  
 <span data-ttu-id="4fb83-115">您要定义的复制拓扑取决于多个因素，其中包括：</span><span class="sxs-lookup"><span data-stu-id="4fb83-115">The replication topology that you define depends on many factors, including the following:</span></span>  
  
-   <span data-ttu-id="4fb83-116">复制的数据是否需要更新以及由谁更新。</span><span class="sxs-lookup"><span data-stu-id="4fb83-116">Whether or not replicated data needs to be updated, and by whom.</span></span>  
  
-   <span data-ttu-id="4fb83-117">有关一致性、自主性和延迟性的数据分布需求。</span><span class="sxs-lookup"><span data-stu-id="4fb83-117">Your data distribution needs regarding consistency, autonomy, and latency.</span></span>  
  
-   <span data-ttu-id="4fb83-118">复制环境，包括业务用户、技术基础结构、网络和安全性，以及数据特征。</span><span class="sxs-lookup"><span data-stu-id="4fb83-118">The replication environment, including business users, technical infrastructure, network and security, and data characteristics.</span></span>  
  
-   <span data-ttu-id="4fb83-119">复制类型和复制选项。</span><span class="sxs-lookup"><span data-stu-id="4fb83-119">The types of replication and replication options.</span></span>  
  
-   <span data-ttu-id="4fb83-120">复制拓扑及其如何与复制类型相符。</span><span class="sxs-lookup"><span data-stu-id="4fb83-120">The replication topologies and how they align with the types of replication.</span></span>  
  
 <span data-ttu-id="4fb83-121">如果不熟悉 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制，请参阅[复制类型](../types-of-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="4fb83-121">If you are new to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication, see [Types of Replication](../types-of-replication.md).</span></span>  
  
## <a name="defining-application-functionality"></a><span data-ttu-id="4fb83-122">定义应用程序功能</span><span class="sxs-lookup"><span data-stu-id="4fb83-122">Defining Application Functionality</span></span>  
 <span data-ttu-id="4fb83-123">定义完复制拓扑后，应确定应用程序提供的功能。</span><span class="sxs-lookup"><span data-stu-id="4fb83-123">Once the replication topology has been defined, you should decide on the functionalities that your application will offer.</span></span> <span data-ttu-id="4fb83-124">应用程序的功能范围广泛，既可以是对订阅进行同步的脚本，也可以是具有用于配置复制的用户界面的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4fb83-124">These functionalities can range from a script that synchronizes a subscription to an application with a user interface to configure replication.</span></span> <span data-ttu-id="4fb83-125">复制支持下列常规编程任务：</span><span class="sxs-lookup"><span data-stu-id="4fb83-125">Replication supports the following general programming tasks:</span></span>  
  
-   <span data-ttu-id="4fb83-126">设置复制。</span><span class="sxs-lookup"><span data-stu-id="4fb83-126">Setting up replication.</span></span>  
  
-   <span data-ttu-id="4fb83-127">同步订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="4fb83-127">Synchronizing Subscribers.</span></span>  
  
-   <span data-ttu-id="4fb83-128">维护复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="4fb83-128">Maintaining a replication topology.</span></span>  
  
-   <span data-ttu-id="4fb83-129">监视复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="4fb83-129">Monitoring a replication topology.</span></span>  
  
-   <span data-ttu-id="4fb83-130">排除复制故障。</span><span class="sxs-lookup"><span data-stu-id="4fb83-130">Troubleshooting replication.</span></span>  
  
 <span data-ttu-id="4fb83-131">将复制功能与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 提供的其他功能相结合来扩展应用程序也是很常见的。</span><span class="sxs-lookup"><span data-stu-id="4fb83-131">It is also common extend your application by combining replication functionalities with other functionalities provided by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4fb83-132">下表列出了一些您可以在您的复制应用程序中提供的扩展功能。</span><span class="sxs-lookup"><span data-stu-id="4fb83-132">The following table highlights some extended functionalities that you might provide in your replication application.</span></span>  
  
|<span data-ttu-id="4fb83-133">功能</span><span class="sxs-lookup"><span data-stu-id="4fb83-133">Functionality</span></span>|<span data-ttu-id="4fb83-134">示例</span><span class="sxs-lookup"><span data-stu-id="4fb83-134">Example</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="4fb83-135">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 进行服务器管理</span><span class="sxs-lookup"><span data-stu-id="4fb83-135">Server administration using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)</span></span>|<span data-ttu-id="4fb83-136">允许管理员在复制拓扑中附加一个数据库并将其配置为发布服务器的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4fb83-136">An application that enables an administrator to attach and configure a database as a Publisher in a replication topology.</span></span>|  
|<span data-ttu-id="4fb83-137">使用 ADO.NET 进行数据访问</span><span class="sxs-lookup"><span data-stu-id="4fb83-137">Data access using ADO.NET</span></span>|<span data-ttu-id="4fb83-138">用户能够以编程方式脱机访问并更改本地订阅服务器数据库中的复制的销售数据且随后单击按钮即可连接并同步请求订阅的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4fb83-138">An application that enables users to programmatically access and change replicated sales data in a local Subscriber database while offline and then connect and synchronize the pull subscription by clicking a button.</span></span>|  
  
## <a name="planning-for-security"></a><span data-ttu-id="4fb83-139">规划安全性</span><span class="sxs-lookup"><span data-stu-id="4fb83-139">Planning for Security</span></span>  
 <span data-ttu-id="4fb83-140">对于任何应用程序，安全性都是非常重要的，应当在编写代码前，就完成安全性规划。</span><span class="sxs-lookup"><span data-stu-id="4fb83-140">Security is important in any application, and planning for security should be completed before writing any code.</span></span> <span data-ttu-id="4fb83-141">应用程序安全性可划分为三个主要部分：保护数据库、保护复制和编写安全的代码。</span><span class="sxs-lookup"><span data-stu-id="4fb83-141">Application security can be divided into three main parts: securing the database, securing replication, and writing secure code.</span></span>  
  
 <span data-ttu-id="4fb83-142">以下主题提供安全性方面的信息：</span><span class="sxs-lookup"><span data-stu-id="4fb83-142">The following topics provide information on security:</span></span>  
  
-   [<span data-ttu-id="4fb83-143">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="4fb83-143">SQL Server Replication Security</span></span>](../security/view-and-modify-replication-security-settings.md)  
  
-   [<span data-ttu-id="4fb83-144">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="4fb83-144">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
## <a name="choosing-a-development-environment"></a><span data-ttu-id="4fb83-145">选择开发环境</span><span class="sxs-lookup"><span data-stu-id="4fb83-145">Choosing a Development Environment</span></span>  
 <span data-ttu-id="4fb83-146">开发复制应用程序时，有三种基本开发环境可供选择。</span><span class="sxs-lookup"><span data-stu-id="4fb83-146">When developing a replication application, there are three basic development environments to consider.</span></span> <span data-ttu-id="4fb83-147">除了一些例外情况，每种开发环境都可以开发相同的功能。</span><span class="sxs-lookup"><span data-stu-id="4fb83-147">Each development environment has access to the same replication functionalities with some exceptions.</span></span> <span data-ttu-id="4fb83-148">复制应用程序可在以下任一环境中开发：</span><span class="sxs-lookup"><span data-stu-id="4fb83-148">Replication applications can be developed in each of the following environments.</span></span>  
  
-   <span data-ttu-id="4fb83-149">**托管代码**</span><span class="sxs-lookup"><span data-stu-id="4fb83-149">**Managed code**</span></span>  
  
     <span data-ttu-id="4fb83-150">利用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 编程和 .NET 公共语言运行时 (CLR) 的优点的面向对象开发环境。</span><span class="sxs-lookup"><span data-stu-id="4fb83-150">Object oriented development environment that leverages the benefits of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programming and the .NET common language runtime (CLR).</span></span> <span data-ttu-id="4fb83-151">对于 .NET 开发和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 应用程序，编程环境推荐使用托管代码。</span><span class="sxs-lookup"><span data-stu-id="4fb83-151">Managed code is the recommended programming environment for both .NET development and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applications.</span></span> <span data-ttu-id="4fb83-152">使用托管复制接口可以在无须了解 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 的情况下以面向对象的方式进行复制管理编程，而且它还可在运行复制代理时提供某些脚本所不具备的回调功能。</span><span class="sxs-lookup"><span data-stu-id="4fb83-152">Managed replication interfaces enable the programming of replication administration in an object-oriented manner without having to know [!INCLUDE[tsql](../../../includes/tsql-md.md)], and it also provides some callback functionalities when running replication agents that are not available from scripts.</span></span> <span data-ttu-id="4fb83-153">托管代码是开发可重用组件和用户界面应用程序的最佳环境。</span><span class="sxs-lookup"><span data-stu-id="4fb83-153">Managed code is the best environment for developing reusable components and user interface applications.</span></span>  
  
-   <span data-ttu-id="4fb83-154">**脚本**</span><span class="sxs-lookup"><span data-stu-id="4fb83-154">**Scripting**</span></span>  
  
     <span data-ttu-id="4fb83-155">简单应用程序，执行一系列命令，如 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本中的复制系统存储过程或批处理文件中的命令。</span><span class="sxs-lookup"><span data-stu-id="4fb83-155">Simple applications that execute a series of commands as either replication system stored procedures in [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts or commands in batch files.</span></span> <span data-ttu-id="4fb83-156">您可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进程内托管提供程序在托管环境中执行脚本，使用托管复制接口可以实现同样的功能，而且该接口还提供回调功能。</span><span class="sxs-lookup"><span data-stu-id="4fb83-156">While you can execute scripts in a managed environment using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in-process managed provider, the same functionality can obtained by using managed replication interfaces, which also provide callback functionalities.</span></span> <span data-ttu-id="4fb83-157">脚本是执行运行次数少且无需回调功能的任务的最佳环境，如安装复制服务器。</span><span class="sxs-lookup"><span data-stu-id="4fb83-157">Scripting is the best environment for executing tasks that will run only a few times and where callback functionalities are not required, such as installing a replication server.</span></span>  
  
-   <span data-ttu-id="4fb83-158">**本机代码**</span><span class="sxs-lookup"><span data-stu-id="4fb83-158">**Native code**</span></span>  
  
     <span data-ttu-id="4fb83-159">面向对象的开发环境，直接访问系统或 COM 对象，因而不由 CLR 托管代码。</span><span class="sxs-lookup"><span data-stu-id="4fb83-159">Object-oriented development environment that utilizes direct access to the system or COM objects such that code is not managed by the CLR.</span></span> <span data-ttu-id="4fb83-160">本机代码复制接口是不推荐使用或已停止使用的。</span><span class="sxs-lookup"><span data-stu-id="4fb83-160">Native code replication interfaces are deprecated or discontinued.</span></span> <span data-ttu-id="4fb83-161">有关详细信息，请参阅 [SQL Server 复制中不推荐使用的功能](../deprecated-features-in-sql-server-replication.md)或[复制的向后兼容性](../replication-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="4fb83-161">For more information, see [Deprecated Features in SQL Server Replication](../deprecated-features-in-sql-server-replication.md) or [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
## <a name="choose-the-appropriate-replication-programming-interface"></a><span data-ttu-id="4fb83-162">选择合适的复制编程接口</span><span class="sxs-lookup"><span data-stu-id="4fb83-162">Choose the Appropriate Replication Programming Interface</span></span>  
 <span data-ttu-id="4fb83-163">计划步骤的最后一步是为所选开发环境选择可实现所需复制功能的合适复制编程接口。</span><span class="sxs-lookup"><span data-stu-id="4fb83-163">The final planning step is choosing the appropriate replication programming interface that implements the desired replication functionality for the chosen development environment.</span></span> <span data-ttu-id="4fb83-164">下表显示了可用的复制编程接口。</span><span class="sxs-lookup"><span data-stu-id="4fb83-164">The following table shows the replication programming interfaces available.</span></span>  
  
|<span data-ttu-id="4fb83-165">接口</span><span class="sxs-lookup"><span data-stu-id="4fb83-165">Interface</span></span>|<span data-ttu-id="4fb83-166">环境</span><span class="sxs-lookup"><span data-stu-id="4fb83-166">Environment</span></span>|<span data-ttu-id="4fb83-167">使用</span><span class="sxs-lookup"><span data-stu-id="4fb83-167">Uses</span></span>|  
|---------------|-----------------|----------|  
|[<span data-ttu-id="4fb83-168">复制管理对象概念</span><span class="sxs-lookup"><span data-stu-id="4fb83-168">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)|<span data-ttu-id="4fb83-169">托管代码</span><span class="sxs-lookup"><span data-stu-id="4fb83-169">Managed code</span></span>|<span data-ttu-id="4fb83-170">管理、监视和同步。</span><span class="sxs-lookup"><span data-stu-id="4fb83-170">Administration, monitoring, and synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication>|<span data-ttu-id="4fb83-171">托管代码</span><span class="sxs-lookup"><span data-stu-id="4fb83-171">Managed code</span></span>|<span data-ttu-id="4fb83-172">同步。</span><span class="sxs-lookup"><span data-stu-id="4fb83-172">Synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|<span data-ttu-id="4fb83-173">托管代码</span><span class="sxs-lookup"><span data-stu-id="4fb83-173">Managed code</span></span>|<span data-ttu-id="4fb83-174">创建业务逻辑处理程序，以集成自定义逻辑与合并同步进程。</span><span class="sxs-lookup"><span data-stu-id="4fb83-174">Creation of business logic handlers to integrate custom logic with the merge synchronization process.</span></span>|  
|[<span data-ttu-id="4fb83-175">复制存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4fb83-175">Replication Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)|<span data-ttu-id="4fb83-176">脚本编写</span><span class="sxs-lookup"><span data-stu-id="4fb83-176">Scripting</span></span>|<span data-ttu-id="4fb83-177">管理和监视。</span><span class="sxs-lookup"><span data-stu-id="4fb83-177">Administration and monitoring.</span></span>|  
|[<span data-ttu-id="4fb83-178">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="4fb83-178">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)|<span data-ttu-id="4fb83-179">脚本编写</span><span class="sxs-lookup"><span data-stu-id="4fb83-179">Scripting</span></span>|<span data-ttu-id="4fb83-180">同步。</span><span class="sxs-lookup"><span data-stu-id="4fb83-180">Synchronization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4fb83-181">示例</span><span class="sxs-lookup"><span data-stu-id="4fb83-181">Example</span></span>  
 <span data-ttu-id="4fb83-182">在 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] 中，需要为全球 200 位销售代表发布数据。</span><span class="sxs-lookup"><span data-stu-id="4fb83-182">At [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)], data needs to be published for 200 sales representatives around the world.</span></span> <span data-ttu-id="4fb83-183">销售代表经常出差，需要使用便携式计算机或个人数字助理 (PDA) 更改客户数据以及添加新订单。</span><span class="sxs-lookup"><span data-stu-id="4fb83-183">The sales representatives travel often and will need to use laptop computers or personal digital assistants (PDAs) to change customer data and add new orders.</span></span> <span data-ttu-id="4fb83-184">这些更改需要在销售代表将便携式计算机连接到网络时，与发布服务器进行同步。</span><span class="sxs-lookup"><span data-stu-id="4fb83-184">The changes will then need to be synchronized with the Publisher when the sales representative connects the laptop to the network.</span></span>  
  
 <span data-ttu-id="4fb83-185">对于此应用程序，计划步骤可如下：</span><span class="sxs-lookup"><span data-stu-id="4fb83-185">For this application, the planning steps might look like the following:</span></span>  
  
1.  <span data-ttu-id="4fb83-186">此应用程序的复制拓扑已经存在。</span><span class="sxs-lookup"><span data-stu-id="4fb83-186">The replication topology for this application already exists.</span></span> <span data-ttu-id="4fb83-187">但必须在客户端创建一个新的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="4fb83-187">However, a new pull subscription must be created at the client.</span></span> <span data-ttu-id="4fb83-188">应使用参数化的筛选器进行发布，以便为每位销售代表复制一组唯一数据。</span><span class="sxs-lookup"><span data-stu-id="4fb83-188">The publication should use parameterized filters to replicate a unique set of data to each sales representative.</span></span>  
  
2.  <span data-ttu-id="4fb83-189">除了销售应用程序所需的典型数据访问外，此应用程序还应允许销售人员通过单击按钮来按需同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="4fb83-189">In addition to the typical data access required for a sales application, this application should enable a salesperson to synchronize the pull subscription on demand by clicking a button.</span></span> <span data-ttu-id="4fb83-190">由于销售代表要安装并运行该应用程序，因此该应用程序还要能在客户端配置订阅并应用初始快照。</span><span class="sxs-lookup"><span data-stu-id="4fb83-190">Since a sales representative will install and run the application, it also needs to be able to configure a subscription and apply the initial snapshot at the client.</span></span> <span data-ttu-id="4fb83-191">作为可选功能，该应用程序还可以使用 Windows 提供的用于检测无线网络连接的基础结构，在检测到无线连接时自动同步订阅。</span><span class="sxs-lookup"><span data-stu-id="4fb83-191">Optionally, the application will use the infrastructure provided by Windows for sensing wireless connectivity to automatically synchronize the subscription when a connection is detected.</span></span>  
  
3.  <span data-ttu-id="4fb83-192">遵守所有复制安全指南，包括连接发布服务器时使用 Windows 身份验证和虚拟专用网 (VPN)。</span><span class="sxs-lookup"><span data-stu-id="4fb83-192">Follow all of the security guidelines for replication, including using Windows Authentication and a virtual private network (VPN) when connecting to the publisher.</span></span> <span data-ttu-id="4fb83-193">如果需要实现 Web 同步，请使用安全套接字层 (SSL) 连接。</span><span class="sxs-lookup"><span data-stu-id="4fb83-193">If implementing Web synchronization, use a secure sockets layer (SSL) connection.</span></span> <span data-ttu-id="4fb83-194">有关详细信息，请参阅 [Configure Web Synchronization](../configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="4fb83-194">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md).</span></span>  
  
4.  <span data-ttu-id="4fb83-195">为了利用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的功能，应使用托管代码语言开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="4fb83-195">In order to take advantage of the features of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], the application is developed using a managed code language.</span></span>  
  
5.  <span data-ttu-id="4fb83-196">对于这些要求，复制管理对象 (RMO) 托管接口可提供此应用程序所需的所有复制功能。</span><span class="sxs-lookup"><span data-stu-id="4fb83-196">Based on these requirements, the Replication Management Objects (RMO) managed interface can provide all of the needed replication functionality for this application.</span></span>  
  
 <span data-ttu-id="4fb83-197">随 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 提供的一个示例应用程序已实现了此示例应用场景。</span><span class="sxs-lookup"><span data-stu-id="4fb83-197">This example scenario has been implemented in a sample application that ships with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  
