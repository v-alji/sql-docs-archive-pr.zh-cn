---
title: 管理对等拓扑（复制 Transact-SQL 编程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, peer-to-peer replication
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a73af1c1f3a7196d87f77681ee9d62a3ef248a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580160"
---
# <a name="administer-a-peer-to-peer-topology-replication-transact-sql-programming"></a><span data-ttu-id="1795c-102">管理对等拓扑（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="1795c-102">Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="1795c-103">管理对等拓扑类似于管理典型的事务复制拓扑，但有许多需要特别注意的地方。</span><span class="sxs-lookup"><span data-stu-id="1795c-103">Administering a peer-to-peer topology is similar to administering a typical transactional replication topology, but there are a number of areas with special considerations.</span></span> <span data-ttu-id="1795c-104">管理对等拓扑的主要区别在于，有些更改需要让系统“停止” \*\*。</span><span class="sxs-lookup"><span data-stu-id="1795c-104">The principal difference in administering a peer-to-peer topology is that some changes require the system to be *quiesced*.</span></span> <span data-ttu-id="1795c-105">为了停止系统，需要停止对所有节点上已发布表的操作，并确保每个节点都已收到来自所有其他节点的所有更改。</span><span class="sxs-lookup"><span data-stu-id="1795c-105">Quiescing a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="1795c-106">有关详细信息，请参阅[停止复制拓扑（复制 Transact-SQL 编程）](quiesce-a-replication-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="1795c-106">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1795c-107">在对等拓扑中，分发服务器使用的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本不能低于请求订阅服务器的版本。</span><span class="sxs-lookup"><span data-stu-id="1795c-107">In a peer-to-peer topology, the distributor cannot be using an earlier version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] than a pull subscriber.</span></span>  
  
### <a name="to-add-an-article-to-an-existing-configuration"></a><span data-ttu-id="1795c-108">向现有配置添加项目</span><span class="sxs-lookup"><span data-stu-id="1795c-108">To add an article to an existing configuration</span></span>  
  
1.  <span data-ttu-id="1795c-109">停止系统。</span><span class="sxs-lookup"><span data-stu-id="1795c-109">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="1795c-110">停止拓扑中每个节点上的分发代理。</span><span class="sxs-lookup"><span data-stu-id="1795c-110">Stop the Distribution Agent at each node in the topology.</span></span> <span data-ttu-id="1795c-111">有关详细信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)或[启动和停止复制代理 (SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="1795c-111">For more information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="1795c-112">执行 CREATE TABLE 语句，在拓扑中每个节点上添加新表。</span><span class="sxs-lookup"><span data-stu-id="1795c-112">Execute the CREATE TABLE statement to add the new table at each node in the topology.</span></span>  
  
4.  <span data-ttu-id="1795c-113">通过使用 [bcp 实用工具](../../../tools/bcp-utility.md)在所有节点上以手动方式为新表大容量复制数据。</span><span class="sxs-lookup"><span data-stu-id="1795c-113">Bulk copy the data for the new table manually at all nodes by using the [bcp utility](../../../tools/bcp-utility.md).</span></span>  
  
5.  <span data-ttu-id="1795c-114">执行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) ，在拓扑中的每个节点上创建新项目。</span><span class="sxs-lookup"><span data-stu-id="1795c-114">Execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) to create the new article at each node in the topology.</span></span> <span data-ttu-id="1795c-115">有关详细信息，请参阅 [定义项目](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="1795c-115">For more information, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1795c-116">执行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 之后，复制会将此项目自动添加到拓扑中的订阅。</span><span class="sxs-lookup"><span data-stu-id="1795c-116">After [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) is executed, replication automatically adds the article to the subscriptions in the topology.</span></span>  
  
6.  <span data-ttu-id="1795c-117">重新启动拓扑中每个节点上的分发代理。</span><span class="sxs-lookup"><span data-stu-id="1795c-117">Restart the Distribution Agents at each node in the topology.</span></span>  
  
### <a name="to-make-schema-changes-to-a-publication-database"></a><span data-ttu-id="1795c-118">对发布数据库进行架构更改</span><span class="sxs-lookup"><span data-stu-id="1795c-118">To make schema changes to a publication database</span></span>  
  
1.  <span data-ttu-id="1795c-119">停止系统。</span><span class="sxs-lookup"><span data-stu-id="1795c-119">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="1795c-120">执行数据定义语言 (DDL) 语句来修改已发布表的架构。</span><span class="sxs-lookup"><span data-stu-id="1795c-120">Execute the data definition language (DDL) statements to modify the schema of published tables.</span></span> <span data-ttu-id="1795c-121">有关支持的架构更改的详细信息，请参阅[对发布数据库进行架构更改](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="1795c-121">For more information about supported schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
3.  <span data-ttu-id="1795c-122">恢复已发布表中的操作之前，请再次停止系统。</span><span class="sxs-lookup"><span data-stu-id="1795c-122">Before you resume activity on published tables, quiesce the system again.</span></span> <span data-ttu-id="1795c-123">这将确保在复制任何新的数据更改前所有节点已收到架构更改。</span><span class="sxs-lookup"><span data-stu-id="1795c-123">This ensures that schema changes have been received by all nodes before any new data changes are replicated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1795c-124">示例</span><span class="sxs-lookup"><span data-stu-id="1795c-124">Example</span></span>  
 <span data-ttu-id="1795c-125">以下示例演示如何将新的表项目添加到具有两个节点的现有对等复制拓扑中。</span><span class="sxs-lookup"><span data-stu-id="1795c-125">The following example demonstrates how to add a new table article to an existing peer-to-peer replication topology that has two nodes.</span></span>  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createtables)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_cmdline)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createarticle)]  
  
## <a name="see-also"></a><span data-ttu-id="1795c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1795c-126">See Also</span></span>  
 <span data-ttu-id="1795c-127">[复制管理常见问题解答](frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="1795c-127">[Replication Administration FAQ](frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="1795c-128">[SQL Server 数据库的备份和还原](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="1795c-128">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="1795c-129">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="1795c-129">Peer-to-Peer Transactional Replication</span></span>](../transactional/peer-to-peer-transactional-replication.md)  
  
  
