---
title: 非 SQL Server 订阅服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], non-SQL Server Subscribers
- heterogeneous data sources, non-SQL Server Subscribers
- heterogeneous data sources
- heterogeneous database replication, non-SQL Server Subscribers
- non-SQL Server Subscribers, about non-SQL Server Subscribers
- heterogeneous Subscribers
- heterogeneous Subscribers, about heterogeneous Subscribers
- Subscribers [SQL Server replication], non-SQL Server Subscribers
- non-SQL Server Subscribers
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a42ba5aedff4f23c6fb6be4155b1c6d4bf20471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690534"
---
# <a name="non-sql-server-subscribers"></a><span data-ttu-id="e163d-102">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="e163d-102">Non-SQL Server Subscribers</span></span>
  <span data-ttu-id="e163d-103">下列非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器可通过推送订阅来订阅快照发布和事务发布。</span><span class="sxs-lookup"><span data-stu-id="e163d-103">The following non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers can subscribe to snapshot and transactional publications using push subscriptions.</span></span> <span data-ttu-id="e163d-104">支持所列每个数据库的两个最新版本使用所列 OLE DB 访问接口的最新版本进行订阅。</span><span class="sxs-lookup"><span data-stu-id="e163d-104">Subscriptions are supported for the two most recent versions of each database listed using the most recent version of the OLE DB provider listed.</span></span>  
  
 <span data-ttu-id="e163d-105">不推荐异类复制到非 SQL Server 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e163d-105">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="e163d-106">不推荐使用 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="e163d-106">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="e163d-107">若要移动数据，请创建使用变更数据捕获和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]的解决方案。</span><span class="sxs-lookup"><span data-stu-id="e163d-107">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|<span data-ttu-id="e163d-108">数据库</span><span class="sxs-lookup"><span data-stu-id="e163d-108">Database</span></span>|<span data-ttu-id="e163d-109">操作系统</span><span class="sxs-lookup"><span data-stu-id="e163d-109">Operating System</span></span>|<span data-ttu-id="e163d-110">提供程序</span><span class="sxs-lookup"><span data-stu-id="e163d-110">Provider</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="e163d-111">Oracle</span><span class="sxs-lookup"><span data-stu-id="e163d-111">Oracle</span></span>|<span data-ttu-id="e163d-112">Oracle 支持的所有平台</span><span class="sxs-lookup"><span data-stu-id="e163d-112">All platforms that Oracle supports</span></span>|<span data-ttu-id="e163d-113">Oracle OLE DB 访问接口（由 Oracle 提供）</span><span class="sxs-lookup"><span data-stu-id="e163d-113">Oracle OLE DB provider (supplied by Oracle)</span></span>|  
|<span data-ttu-id="e163d-114">IBM DB2</span><span class="sxs-lookup"><span data-stu-id="e163d-114">IBM DB2</span></span>|<span data-ttu-id="e163d-115">MVS、AS400、Unix、Linux、Windows（9.x 版除外）</span><span class="sxs-lookup"><span data-stu-id="e163d-115">MVS, AS400, Unix, Linux, Windows excluding 9.x</span></span>|<span data-ttu-id="e163d-116">Microsoft Host Integration Server (HIS) OLE DB 访问接口</span><span class="sxs-lookup"><span data-stu-id="e163d-116">Microsoft Host Integration Server (HIS) OLE DB provider</span></span>|  
  
 <span data-ttu-id="e163d-117">有关创建 Oracle 和 IBM DB2, 订阅的信息，请参阅 [Oracle 订阅服务器](oracle-subscribers.md) 和 [IBM DB2 Subscribers](ibm-db2-subscribers.md)的解决方案。</span><span class="sxs-lookup"><span data-stu-id="e163d-117">For information about creating subscriptions to Oracle and IBM DB2, see [Oracle Subscribers](oracle-subscribers.md) and [IBM DB2 Subscribers](ibm-db2-subscribers.md).</span></span>  
  
## <a name="considerations-for-non-sql-server-subscribers"></a><span data-ttu-id="e163d-118">非 SQL Server 订阅服务器的注意事项</span><span class="sxs-lookup"><span data-stu-id="e163d-118">Considerations for Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="e163d-119">在复制到非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器时，请牢记下列注意事项：</span><span class="sxs-lookup"><span data-stu-id="e163d-119">Keep the following considerations in mind when replicating to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="e163d-120">一般注意事项</span><span class="sxs-lookup"><span data-stu-id="e163d-120">General Considerations</span></span>  
  
-   <span data-ttu-id="e163d-121">复制支持将表和索引视图作为表发布到非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器（索引视图不能作为索引视图复制）。</span><span class="sxs-lookup"><span data-stu-id="e163d-121">Replication supports publishing tables and indexed views as tables to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers (indexed views cannot be replicated as indexed views).</span></span>  
  
-   <span data-ttu-id="e163d-122">在新建发布向导中创建发布，然后使用 "发布属性" 对话框为非 SQL Server 订阅服务器启用该发布时，不会为非订阅服务器指定订阅数据库中所有对象的所有者， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 而对于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器，则会将其设置为发布数据库中相应对象的所有者。</span><span class="sxs-lookup"><span data-stu-id="e163d-122">When creating a publication in the New Publication Wizard and then enabling it for non-SQL Server Subscribers using the Publication Properties dialog box, the owner of all objects in the subscription database is not specified for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, whereas for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, it is set to the owner of the corresponding object in the publication database.</span></span>  
  
-   <span data-ttu-id="e163d-123">如果发布中将包括 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器和非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器，则必须在创建对[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器的任何订阅之前为非 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器启用发布。</span><span class="sxs-lookup"><span data-stu-id="e163d-123">If a publication will have [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers and non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the publication must be enabled for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers before any subscriptions to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers are created.</span></span>  
  
-   <span data-ttu-id="e163d-124">默认情况下，由快照代理为非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器生成的脚本在 CREATE TABLE 语法中使用不带引号的标识符。</span><span class="sxs-lookup"><span data-stu-id="e163d-124">By default, scripts generated by the Snapshot Agent for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers use non-quoted identifiers in the CREATE TABLE syntax.</span></span> <span data-ttu-id="e163d-125">因此，名为“test”的已发布表按“TEST”复制。</span><span class="sxs-lookup"><span data-stu-id="e163d-125">Therefore, a published table named 'test' is replicated as 'TEST'.</span></span> <span data-ttu-id="e163d-126">若要使用与发布数据库中的表相同的大小写，请使用分发代理的 **-QuotedIdentifier** 参数。</span><span class="sxs-lookup"><span data-stu-id="e163d-126">To use the same case as the table in the publication database, use the **-QuotedIdentifier** parameter for the Distribution Agent.</span></span> <span data-ttu-id="e163d-127">如果非 **订阅服务器中已发布的对象名称（如表、列和约束）包含空格或相应版本数据库中保留的字词，则还必须使用** -QuotedIdentifier[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 参数。</span><span class="sxs-lookup"><span data-stu-id="e163d-127">The **-QuotedIdentifier** parameter must also be used if published object names (such as tables, columns, and constraints) include spaces or words that are reserved words in the version of the database at the non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscriber.</span></span> <span data-ttu-id="e163d-128">有关此参数的详细信息，请参阅 [复制分发代理](../agents/replication-distribution-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="e163d-128">For more information about this parameter, see [Replication Distribution Agent](../agents/replication-distribution-agent.md).</span></span>  
  
-   <span data-ttu-id="e163d-129">运行分发代理时使用的帐户必须对 OLE DB 访问接口的安装目录具有读权限。</span><span class="sxs-lookup"><span data-stu-id="e163d-129">The account under which the Distribution Agent runs must have read access to the install directory of the OLE DB provider.</span></span>  
  
-   <span data-ttu-id="e163d-130">默认情况下，对于非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器，分发代理对订阅数据库使用 [(default destination)] 值（分发代理的 **-SubscriberDB** 参数）：</span><span class="sxs-lookup"><span data-stu-id="e163d-130">By default for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the Distribution Agent uses a value of [(default destination)] for the subscription database (the **-SubscriberDB** parameter for the Distribution Agent):</span></span>  
  
    -   <span data-ttu-id="e163d-131">对于 Oracle，一个服务器最多只有一个数据库，因此不必指定数据库。</span><span class="sxs-lookup"><span data-stu-id="e163d-131">For Oracle, a server has at most one database, so it is not necessary to specify the database.</span></span>  
  
    -   <span data-ttu-id="e163d-132">对于 IBM DB2，在 DB2 连接字符串中指定数据库。</span><span class="sxs-lookup"><span data-stu-id="e163d-132">For IBM DB2, the database is specified in the DB2 connection string.</span></span> <span data-ttu-id="e163d-133">有关详细信息，请参阅 [为非 SQL Server 订阅服务器创建订阅](../create-a-subscription-for-a-non-sql-server-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="e163d-133">For more information, see [Create a Subscription for a Non-SQL Server Subscriber](../create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
-   <span data-ttu-id="e163d-134">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器运行在 64 位平台上，必须使用相应 OLE DB 访问接口的 64 位版本。</span><span class="sxs-lookup"><span data-stu-id="e163d-134">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor is running on a 64 bit platform, you must use the 64 bit version of the appropriate OLE DB provider.</span></span>  
  
-   <span data-ttu-id="e163d-135">无论发布服务器和订阅服务器中的排序规则/代码页是什么，复制都以 Unicode 格式移动数据。</span><span class="sxs-lookup"><span data-stu-id="e163d-135">Replication moves data in Unicode format regardless of the collation/code pages used on the Publisher and Subscriber.</span></span> <span data-ttu-id="e163d-136">建议在发布服务器和订阅服务器之间复制时选择一个兼容的排序规则/代码页。</span><span class="sxs-lookup"><span data-stu-id="e163d-136">It is recommended that you choose a compatible collation/code page when replicating between Publishers and Subscribers.</span></span>  
  
-   <span data-ttu-id="e163d-137">如果在发布中添加或删除项目，必须重新初始化对非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器的订阅。</span><span class="sxs-lookup"><span data-stu-id="e163d-137">If an article is added to or deleted from a publication, subscriptions to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers must be reinitialized.</span></span>  
  
-   <span data-ttu-id="e163d-138">所有非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器支持的约束只有：NULL 和 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="e163d-138">The only constraints supported for all non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers are: NULL, and NOT NULL.</span></span> <span data-ttu-id="e163d-139">主键约束按唯一索引复制。</span><span class="sxs-lookup"><span data-stu-id="e163d-139">Primary key constraints are replicated as unique indexes.</span></span>  
  
-   <span data-ttu-id="e163d-140">不同的数据库处理 NULL 值的方式不同，这将影响空白值、空字符串和 NULL 的显示方式，</span><span class="sxs-lookup"><span data-stu-id="e163d-140">The value NULL is treated differently by different databases, which affects how a blank value, an empty string, and a NULL are represented.</span></span> <span data-ttu-id="e163d-141">而显示方式又影响在定义了唯一约束的列中插入值的行为。</span><span class="sxs-lookup"><span data-stu-id="e163d-141">This in turn affects the behavior of values inserted into columns with unique constraints defined.</span></span> <span data-ttu-id="e163d-142">例如，Oracle 允许唯一列中有多个 NULL 值，而 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 仅允许唯一列中存在一个 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="e163d-142">For example, Oracle allows multiple NULL values in a column that is considered unique, whereas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] allows only a single NULL value in a unique column.</span></span>  
  
     <span data-ttu-id="e163d-143">另一个因素是当列被定义为 NOT NULL 时，如何处理 NULL 值、空字符串和空白值。</span><span class="sxs-lookup"><span data-stu-id="e163d-143">An additional factor is how NULL values, empty strings, and blank values are treated when the column is defined as NOT NULL.</span></span> <span data-ttu-id="e163d-144">有关如何为 Oracle 订阅服务器解决此问题的信息，请参阅 [Oracle 订阅服务器](oracle-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="e163d-144">For information about addressing this issue for Oracle Subscribers, see [Oracle Subscribers](oracle-subscribers.md).</span></span>  
  
-   <span data-ttu-id="e163d-145">删除该订阅时，不从非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器中删除与复制有关的元数据（事务序列表）。</span><span class="sxs-lookup"><span data-stu-id="e163d-145">Replication-related metadata (transaction sequence table) is not deleted from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] subscribers when the subscription is removed.</span></span>  
  
### <a name="conforming-to-the-requirements-of-the-subscriber-database"></a><span data-ttu-id="e163d-146">符合订阅服务器数据库的要求</span><span class="sxs-lookup"><span data-stu-id="e163d-146">Conforming to the Requirements of the Subscriber Database</span></span>  
  
-   <span data-ttu-id="e163d-147">已发布的架构和数据必须符合订阅服务器中的数据库的要求。</span><span class="sxs-lookup"><span data-stu-id="e163d-147">Published schema and data must conform to the requirements of the database at the Subscriber.</span></span> <span data-ttu-id="e163d-148">例如，如果非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库的最大行大小比 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]小，必须确保已发布的架构和数据不超过此大小。</span><span class="sxs-lookup"><span data-stu-id="e163d-148">For example, if a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database has a smaller maximum row size than [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you must ensure that the published schema and data do not exceed this size.</span></span>  
  
-   <span data-ttu-id="e163d-149">复制到非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器的表将采用订阅服务器中的数据库的表命名约定。</span><span class="sxs-lookup"><span data-stu-id="e163d-149">Tables replicated to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers will adopt the table naming conventions of the database at the Subscriber.</span></span>  
  
-   <span data-ttu-id="e163d-150">非 SQL Server 订阅服务器不支持 DDL。</span><span class="sxs-lookup"><span data-stu-id="e163d-150">DDL is not supported for non-SQL Server Subscribers.</span></span> <span data-ttu-id="e163d-151">有关架构更改的详细信息，请参阅[对发布数据库进行架构更改](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="e163d-151">For more information about schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
### <a name="replication-feature-support"></a><span data-ttu-id="e163d-152">复制功能支持</span><span class="sxs-lookup"><span data-stu-id="e163d-152">Replication Feature Support</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e163d-153">提供了两种订阅类型：推送订阅和请求订阅。</span><span class="sxs-lookup"><span data-stu-id="e163d-153">offers two types of subscriptions: push and pull.</span></span> <span data-ttu-id="e163d-154">非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器必须使用推送订阅，在这种订阅中，分发代理运行在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器中。</span><span class="sxs-lookup"><span data-stu-id="e163d-154">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers must use push subscriptions, in which the Distribution Agent runs at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e163d-155">提供了两种快照格式：本机 bcp 模式和字符模式。</span><span class="sxs-lookup"><span data-stu-id="e163d-155">offers two snapshot formats: native bcp-mode and character-mode.</span></span> <span data-ttu-id="e163d-156">非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器需要字符模式快照。</span><span class="sxs-lookup"><span data-stu-id="e163d-156">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers require character mode snapshots.</span></span>  
  
-   <span data-ttu-id="e163d-157">非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器不能使用即时更新订阅或排队更新订阅，也不能作为对等拓扑中的节点。</span><span class="sxs-lookup"><span data-stu-id="e163d-157">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers cannot use immediate updating or queued updating subscriptions, or be nodes in a peer-to-peer topology.</span></span>  
  
-   <span data-ttu-id="e163d-158">非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器不能从备份中自动初始化。</span><span class="sxs-lookup"><span data-stu-id="e163d-158">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers cannot be automatically initialized from a backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e163d-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e163d-159">See Also</span></span>  
 <span data-ttu-id="e163d-160">[异类数据库复制](heterogeneous-database-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e163d-160">[Heterogeneous Database Replication](heterogeneous-database-replication.md) </span></span>  
 [<span data-ttu-id="e163d-161">订阅发布</span><span class="sxs-lookup"><span data-stu-id="e163d-161">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
  
  
