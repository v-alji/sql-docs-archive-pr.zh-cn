---
title: 高级合并复制冲突的检测和解决 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- column-level conflict tracking
- row-level conflict tracking
- viewing merge replication conflicts
- resolving merge replication conflicts
- logical record-level conflict tracking [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9122f0d704db948a0a8134da2b86e34ea6426dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576712"
---
# <a name="advanced-merge-replication-conflict-detection-and-resolution"></a><span data-ttu-id="d9978-102">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="d9978-102">Advanced Merge Replication Conflict Detection and Resolution</span></span>
  <span data-ttu-id="d9978-103">当发布服务器与订阅服务器连接并进行同步时，合并代理将检测是否存在任何冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-103">When a Publisher and a Subscriber are connected and synchronization occurs, the Merge Agent detects if there are any conflicts.</span></span> <span data-ttu-id="d9978-104">如果检测到冲突，合并代理将使用冲突解决程序（将项目添加到发布时指定的）来确定接受哪些数据并将其传播到其他站点。</span><span class="sxs-lookup"><span data-stu-id="d9978-104">If conflicts are detected, the Merge Agent uses a conflict resolver (which is specified when an article is added to a publication) to determine which data is accepted and propagated to other sites.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9978-105">由于订阅服务器与发布服务器同步，因此冲突通常发生在不同订阅服务器上进行的更新之间，而不是发生在订阅服务器和发布服务器上进行的更新之间。</span><span class="sxs-lookup"><span data-stu-id="d9978-105">Although a Subscriber synchronizes with the Publisher, conflicts typically occur between updates that are made at different Subscribers, instead of updates being made at a Subscriber and at the Publisher.</span></span>  
  
 <span data-ttu-id="d9978-106">冲突的检测和解决行为取决于下列选项，本主题对这些选项进行了说明：</span><span class="sxs-lookup"><span data-stu-id="d9978-106">The behavior of conflict detection and resolution depends on the following options, which are described in this topic:</span></span>  
  
-   <span data-ttu-id="d9978-107">指定列级跟踪、行级跟踪还是逻辑记录级跟踪。</span><span class="sxs-lookup"><span data-stu-id="d9978-107">Whether you specify column-level tracking, row-level tracking, or logical record-level tracking.</span></span>  
  
-   <span data-ttu-id="d9978-108">指定默认的基于优先级的解决机制，还是指定项目冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="d9978-108">Whether you specify the default priority-based resolution mechanism or specify an article resolver.</span></span> <span data-ttu-id="d9978-109">项目冲突解决程序可以是：</span><span class="sxs-lookup"><span data-stu-id="d9978-109">An article resolver can be:</span></span>  
  
    -   <span data-ttu-id="d9978-110">以托管代码编写的  业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="d9978-110">A *business logic handler* written in managed code.</span></span>  
  
    -   <span data-ttu-id="d9978-111">基于 COM 的自定义冲突解决程序 。</span><span class="sxs-lookup"><span data-stu-id="d9978-111">A COM-based *custom resolver*.</span></span>  
  
    -   <span data-ttu-id="d9978-112">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]提供的基于 COM 的冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="d9978-112">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)].</span></span>  
  
     <span data-ttu-id="d9978-113">如果使用的是默认解决机制，则冲突的检测和解决行为还取决于所用的订阅类型：客户端或服务器。</span><span class="sxs-lookup"><span data-stu-id="d9978-113">If the default resolution mechanism is used, behavior is further determined by the type of subscription used: client or server.</span></span>  
  
## <a name="conflict-detection"></a><span data-ttu-id="d9978-114">冲突检测</span><span class="sxs-lookup"><span data-stu-id="d9978-114">Conflict Detection</span></span>  
 <span data-ttu-id="d9978-115">数据更改是否可视为冲突取决于为项目设置的冲突跟踪类型：</span><span class="sxs-lookup"><span data-stu-id="d9978-115">Whether a data change qualifies as a conflict or not depends on the type of conflict tracking you set for an article:</span></span>  
  
-   <span data-ttu-id="d9978-116">选择列级冲突跟踪时，如果对多个复制节点的同一行中的同一列进行更改，则此更改视为冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-116">If you select column-level conflict tracking, it is considered a conflict if changes are made to the same column in the same row at more than one replication node.</span></span>  
  
-   <span data-ttu-id="d9978-117">选择行级跟踪时，如果对多个复制节点的同一行中的任意列进行更改（相应行中受影响的列不必相同），则此更改视为冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-117">If you select row-level tracking, it is considered a conflict if changes are made to any columns in the same row at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
-   <span data-ttu-id="d9978-118">选择逻辑记录级跟踪时，如果对多个复制节点的同一逻辑记录中的任意行进行更改（相应行中受影响的列不必相同），则此更改视为冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-118">If you select logical record-level tracking, it is considered a conflict if changes are made to any row in the same logical record at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
 <span data-ttu-id="d9978-119">有关详细信息，请参阅 [检测并解决逻辑记录中的冲突](advanced-merge-replication-conflict-resolving-in-logical-record.md)。</span><span class="sxs-lookup"><span data-stu-id="d9978-119">For more information, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
 <span data-ttu-id="d9978-120">若要指定项目的冲突跟踪和解决方法级别，请参阅 [为合并项目指定冲突跟踪和解决方法级别](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)。</span><span class="sxs-lookup"><span data-stu-id="d9978-120">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>  
  
## <a name="conflict-resolution"></a><span data-ttu-id="d9978-121">冲突解决</span><span class="sxs-lookup"><span data-stu-id="d9978-121">Conflict Resolution</span></span>  
 <span data-ttu-id="d9978-122">检测到冲突后，合并代理将启动选定的冲突解决程序，并使用该冲突解决程序来确定冲突解决入选方。</span><span class="sxs-lookup"><span data-stu-id="d9978-122">After a conflict is detected, the Merge Agent launches the selected conflict resolver and uses the resolver to determine the conflict winner.</span></span> <span data-ttu-id="d9978-123">入选行将应用到发布服务器和订阅服务器，而落选行中的数据将写入冲突表。</span><span class="sxs-lookup"><span data-stu-id="d9978-123">The winning row is applied at the Publisher and Subscriber, and the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="d9978-124">除非选择交互解决冲突，否则冲突解决程序一经执行就会立即解决冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-124">Conflicts are resolved immediately after the resolver executes, unless you select to resolve conflicts interactively.</span></span>  
  
### <a name="resolver-types"></a><span data-ttu-id="d9978-125">冲突解决程序类型</span><span class="sxs-lookup"><span data-stu-id="d9978-125">Resolver Types</span></span>  
 <span data-ttu-id="d9978-126">在合并复制中，冲突解决发生在项目级别。</span><span class="sxs-lookup"><span data-stu-id="d9978-126">In merge replication, conflict resolution takes place at the article level.</span></span> <span data-ttu-id="d9978-127">对于由多个项目组成的发布，可以用不同的冲突解决程序解决不同项目的冲突，也可以用同一个冲突解决程序解决一个项目、多个项目或者组成发布的所有项目的冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-127">For publications composed of several articles, you can have different conflict resolvers serving different articles, or the same conflict resolver serving one article, several articles, or all the articles comprising a publication.</span></span>  
  
 <span data-ttu-id="d9978-128">如果计划使用默认的基于优先级的冲突解决程序，则不必设置项目的冲突解决程序属性。</span><span class="sxs-lookup"><span data-stu-id="d9978-128">If you plan to use the default priority-based conflict resolver, you do not have to set the resolver property of an article.</span></span> <span data-ttu-id="d9978-129">如果想使用项目冲突解决程序（而不是默认冲突解决程序），则必须为要使用该程序的项目设置冲突解决程序属性，可以通过在发布服务器上选择一个可用的冲突解决程序来进行设置。</span><span class="sxs-lookup"><span data-stu-id="d9978-129">If you want to use an article resolver instead of the default resolver, you must set the resolver property for the article that will use it by selecting an available resolver on the Publisher.</span></span> <span data-ttu-id="d9978-130">任何需要传递到冲突解决程序的特定信息也可以在冲突解决程序信息属性中指定。</span><span class="sxs-lookup"><span data-stu-id="d9978-130">Any specific information that needs to be passed to the resolver can also be specified in the resolver information property.</span></span>  
  
 <span data-ttu-id="d9978-131">合并复制提供了四种的冲突解决程序：</span><span class="sxs-lookup"><span data-stu-id="d9978-131">Merge replication offers four types of conflict resolvers:</span></span>  
  
-   <span data-ttu-id="d9978-132">默认的基于优先级的冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="d9978-132">The default priority-based conflict resolver</span></span>  
  
     <span data-ttu-id="d9978-133">默认解决机制的行为不同，具体取决于订阅是客户端订阅还是服务器订阅。</span><span class="sxs-lookup"><span data-stu-id="d9978-133">The default resolution mechanism behaves differently, depending on whether a subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="d9978-134">为使用服务器订阅的各个订阅服务器指定优先级值；当出现任何冲突时，在具有最高优先级的节点上发生的更改将会入选。</span><span class="sxs-lookup"><span data-stu-id="d9978-134">You assign priority values to individual Subscribers that use server subscriptions; changes made at the node with the highest priority win any conflicts.</span></span> <span data-ttu-id="d9978-135">对于客户端订阅，发生冲突时，第一个写入发布服务器的更改将会入选。</span><span class="sxs-lookup"><span data-stu-id="d9978-135">For client subscriptions, the first change written to the Publisher wins the conflict.</span></span>  
  
     <span data-ttu-id="d9978-136">创建订阅后，将无法更改其类型。</span><span class="sxs-lookup"><span data-stu-id="d9978-136">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
-   <span data-ttu-id="d9978-137">业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="d9978-137">A business logic handler</span></span>  
  
     <span data-ttu-id="d9978-138">通过使用业务逻辑处理程序框架，您可以编写合并同步过程中调用的托管代码程序集。</span><span class="sxs-lookup"><span data-stu-id="d9978-138">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="d9978-139">程序集包括可以响应同步期间的冲突和多种其他情况的业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="d9978-139">The assembly includes business logic that can respond to conflicts and a number of other conditions during synchronization.</span></span> <span data-ttu-id="d9978-140">有关详细信息，请参阅[合并同步期间执行业务逻辑](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="d9978-140">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
-   <span data-ttu-id="d9978-141">基于 COM 的自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="d9978-141">A COM-based custom resolver</span></span>  
  
     <span data-ttu-id="d9978-142">合并复制提供了 API，通过该 API 可以用各种语言（如 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]）将冲突解决程序编写为 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="d9978-142">Merge replication provides an API for writing resolvers as COM objects in languages such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="d9978-143">有关详细信息，请参阅 [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="d9978-143">For more information, see [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
-   <span data-ttu-id="d9978-144">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9978-144">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)]</span></span>  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="d9978-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 包括许多基于 COM 的解决程序。</span><span class="sxs-lookup"><span data-stu-id="d9978-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] includes a number of COM-based resolvers.</span></span> <span data-ttu-id="d9978-146">有关详细信息，请参阅 [Microsoft 基于 COM 的冲突解决程序](advanced-merge-replication-conflict-com-based-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="d9978-146">For more information, see [Microsoft COM-Based Resolvers](advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
 <span data-ttu-id="d9978-147">有关如何选择适当类型的冲突解决程序的信息，请参阅[选择冲突解决程序](advanced-merge-replication-conflict-choose-a-resolver.md)。</span><span class="sxs-lookup"><span data-stu-id="d9978-147">For information about how to select the appropriate type of resolver, see [Choose a Resolver](advanced-merge-replication-conflict-choose-a-resolver.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9978-148">某些项目冲突解决程序经编写可仅处理特定操作的冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-148">Some article resolvers are written to handle conflicts only for certain operations.</span></span> <span data-ttu-id="d9978-149">例如，某个冲突解决程序可能处理更新操作的冲突，但不处理插入或删除操作的冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-149">For example a resolver might handle updates, but not inserts or deletes.</span></span> <span data-ttu-id="d9978-150">默认的基于优先级的冲突解决程序处理项目冲突解决程序未处理的任何冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-150">The default priority-based conflict resolver handles any conflicts not handled by the article resolver.</span></span>  
  
 <span data-ttu-id="d9978-151">若要指定合并订阅类型和冲突解决优先级，请参阅</span><span class="sxs-lookup"><span data-stu-id="d9978-151">To specify a merge subscription type and conflict resolution priority, see</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="d9978-152">：[指定合并订阅类型和冲突解决优先级 (SQL Server Management Studio)](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span><span class="sxs-lookup"><span data-stu-id="d9978-152">: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span></span>  
  
-   <span data-ttu-id="d9978-153">复制 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 编程和复制管理对象 (RMO) 编程：[创建请求订阅](../create-a-pull-subscription.md)和[创建推送订阅](../create-a-push-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="d9978-153">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming and Replication Management Objects (RMO) programming: [Create a Pull Subscription](../create-a-pull-subscription.md) and [Create a Push Subscription](../create-a-push-subscription.md)</span></span>  
  
### <a name="interactive-resolver"></a><span data-ttu-id="d9978-154">交互式冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="d9978-154">Interactive Resolver</span></span>  
 <span data-ttu-id="d9978-155">复制提供了一个交互式冲突解决程序用户界面，它可以与默认的基于优先级的冲突解决程序或项目冲突解决程序一起使用。</span><span class="sxs-lookup"><span data-stu-id="d9978-155">Replication supplies an Interactive Resolver user interface that can be used in conjunction with either the default priority-based conflict resolver or an article resolver.</span></span> <span data-ttu-id="d9978-156">通过 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同步管理器执行按需同步时，交互式冲突解决程序在运行时显示冲突数据，并让用户选择解决冲突的方式。</span><span class="sxs-lookup"><span data-stu-id="d9978-156">When performing on-demand synchronization through [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager, the Interactive Resolver displays conflict data at run-time, and lets you choose how to resolve conflicts.</span></span> <span data-ttu-id="d9978-157">有关如何启用交互式解决方法并启动交互式冲突解决程序的详细信息，请参阅 [Interactive Conflict Resolution](advanced-merge-replication-conflict-interactive-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="d9978-157">For more information about how to enable interactive resolution and launch the Interactive Resolver, see [Interactive Conflict Resolution](advanced-merge-replication-conflict-interactive-resolution.md).</span></span>  
  
## <a name="viewing-conflicts"></a><span data-ttu-id="d9978-158">查看冲突</span><span class="sxs-lookup"><span data-stu-id="d9978-158">Viewing Conflicts</span></span>  
 <span data-ttu-id="d9978-159">查看冲突最简单的方法是使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 提供的复制冲突查看器（[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 还提供了可以查询冲突表的存储过程）。</span><span class="sxs-lookup"><span data-stu-id="d9978-159">The most straightforward way to view conflicts is to use the Replication Conflict Viewer, available from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also provides stored procedures that allow the conflict tables to be queried.).</span></span> <span data-ttu-id="d9978-160">冲突查看器和交互式冲突解决程序是类似的工具，但交互式冲突解决程序使用户可以在同步发生时解决冲突，而冲突查看器则用于查看已解决的冲突。</span><span class="sxs-lookup"><span data-stu-id="d9978-160">The Conflict Viewer and Interactive Resolver are similar tools, but the Interactive Resolver allows you to resolve conflicts as synchronization occurs, whereas the Conflict Viewer is designed for viewing conflicts after they have been resolved.</span></span> <span data-ttu-id="d9978-161">如果冲突元数据仍存在于系统表中（默认情况下，冲突元数据保留 14 天），则可以覆盖冲突查看器中的冲突解决结果，但如果需要定期对其进行直接干预，则请考虑使用交互式冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="d9978-161">If the conflict metadata is still available in the system tables (conflict metadata is retained for 14 days by default), you can override conflict resolution outcomes in the Conflict Viewer, but if direct intervention is regularly required, consider using the Interactive Resolver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9978-162">包含逻辑记录的冲突不会显示在冲突查看器中。</span><span class="sxs-lookup"><span data-stu-id="d9978-162">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="d9978-163">若要查看有关这些冲突的信息，请使用复制存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9978-163">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="d9978-164">有关详细信息，请参阅[查看合并发布的冲突信息（复制 Transact-SQL 编程）](../view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="d9978-164">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
 <span data-ttu-id="d9978-165">冲突查看器显示来自三个系统表的信息：</span><span class="sxs-lookup"><span data-stu-id="d9978-165">The Conflict Viewer displays information from three system tables:</span></span>  
  
-   <span data-ttu-id="d9978-166">复制为合并项目中的每个表创建一个冲突表，该冲突表的名称格式为 MSmerge_conflict_\<PublicationName>_\<ArticleName>。</span><span class="sxs-lookup"><span data-stu-id="d9978-166">Replication creates a conflict table for each table in a merge article, with a name in the form **MSmerge_conflict_\<PublicationName>_\<ArticleName>**.</span></span>  
  
     <span data-ttu-id="d9978-167">冲突表与其所依据的表具有相同的结构。</span><span class="sxs-lookup"><span data-stu-id="d9978-167">Conflict tables have the same structure as the tables on which they are based.</span></span> <span data-ttu-id="d9978-168">其中某个冲突表中的一行由冲突行的落选版本（冲突行的入选版本位于实际用户表中）组成。</span><span class="sxs-lookup"><span data-stu-id="d9978-168">A row in one of these tables consists of the losing version of a conflict row (the winning version of the row is in the actual user table).</span></span>  
  
-   <span data-ttu-id="d9978-169">**MSmerge_conflicts_info** 表提供了每个冲突的相关信息，包括冲突类型。</span><span class="sxs-lookup"><span data-stu-id="d9978-169">The **MSmerge_conflicts_info** table provides information about each conflict, including the conflict type.</span></span>  
  
-   <span data-ttu-id="d9978-170">表 **sysmergearticles** 标识了具有冲突表的用户表，并提供了冲突表的相关信息。</span><span class="sxs-lookup"><span data-stu-id="d9978-170">The **sysmergearticles** table identifies which user tables have conflict tables and provides information about the conflict tables.</span></span>  
  
 <span data-ttu-id="d9978-171">默认情况下，冲突信息存储在下列位置：</span><span class="sxs-lookup"><span data-stu-id="d9978-171">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="d9978-172">如果发布兼容级别为 90RTM 或更高，则存储在发布服务器和订阅服务器上。</span><span class="sxs-lookup"><span data-stu-id="d9978-172">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="d9978-173">如果发布兼容级别低于 80RTM，则存储在发布服务器上。</span><span class="sxs-lookup"><span data-stu-id="d9978-173">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="d9978-174">如果订阅服务器运行的是 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]，则存储在发布服务器上。</span><span class="sxs-lookup"><span data-stu-id="d9978-174">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../../includes/ssew-md.md)].</span></span> <span data-ttu-id="d9978-175">冲突数据不能存储在 [!INCLUDE[ssEW](../../../includes/ssew-md.md)] 订阅服务器上。</span><span class="sxs-lookup"><span data-stu-id="d9978-175">Conflict data cannot be stored on [!INCLUDE[ssEW](../../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="d9978-176">**查看冲突**</span><span class="sxs-lookup"><span data-stu-id="d9978-176">**To view conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="d9978-177">：[查看和解决合并发布的数据冲突 &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="d9978-177">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   <span data-ttu-id="d9978-178">复制 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 编程：[查看合并发布的冲突信息（复制 Transact-SQL 编程）](../view-conflict-information-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="d9978-178">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] Programming: [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9978-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9978-179">See Also</span></span>  
 [<span data-ttu-id="d9978-180">同步数据</span><span class="sxs-lookup"><span data-stu-id="d9978-180">Synchronize Data</span></span>](../synchronize-data.md)  
  
  
