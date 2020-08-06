---
title: 在分发数据库中查看复制的命令和其他信息 (复制 Transact-sql 编程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb5850277d685f2ecf6471fa4bf9814579b2843e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693741"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a><span data-ttu-id="03ea4-102">查看分发数据库中复制的命令和其他信息（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="03ea4-102">View Replicated Commands and Other Information in the Distribution Database (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="03ea4-103">在使用事务复制时，事务命令在分发代理将其传播到所有订阅服务器或订阅服务器中的分发代理请求更改之前存储在分发数据库中。</span><span class="sxs-lookup"><span data-stu-id="03ea4-103">When using transactional replication, transaction commands are stored in the distribution database until the Distribution Agent propagates them to all Subscribers or a Distribution Agent at the Subscriber pulls the changes.</span></span> <span data-ttu-id="03ea4-104">使用复制存储过程可以编程方式查看分发数据库中的这些挂起的命令。</span><span class="sxs-lookup"><span data-stu-id="03ea4-104">These pending commands in the distribution database can be viewed programmatically using replication stored procedures.</span></span> <span data-ttu-id="03ea4-105">有关详细信息，请参阅[复制存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="03ea4-105">For more information, see [Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql).</span></span>  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a><span data-ttu-id="03ea4-106">查看分发数据库中来自所有事务发布的复制命令</span><span class="sxs-lookup"><span data-stu-id="03ea4-106">To view replicated commands from all transactional publications in the distribution database</span></span>  
  
1.  <span data-ttu-id="03ea4-107">在分发服务器的分发数据库中，执行 [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="03ea4-107">At the Distributor on the distribution database, execute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).</span></span>  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a><span data-ttu-id="03ea4-108">查看分发数据库中来自使用事务复制发布的某个特定项目或特定数据库的复制命令</span><span class="sxs-lookup"><span data-stu-id="03ea4-108">To view replicated commands in the distribution database from a specific article or from a specific database published using transactional replication</span></span>  
  
1.  <span data-ttu-id="03ea4-109">（可选）在发布服务器的发布数据库中，执行 [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="03ea4-109">(Optional) At the Publisher on the publication database, execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql).</span></span> <span data-ttu-id="03ea4-110">指定\*\* \@ 发布**和** \@ 项目\*\*。</span><span class="sxs-lookup"><span data-stu-id="03ea4-110">Specify **\@publication** and **\@article**.</span></span> <span data-ttu-id="03ea4-111">请记录结果集中 **article id** 的值。</span><span class="sxs-lookup"><span data-stu-id="03ea4-111">Note the value of **article id** in the result set.</span></span>  
  
2.  <span data-ttu-id="03ea4-112">在分发服务器的分发数据库中，执行 [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="03ea4-112">At the Distributor on the distribution database, execute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).</span></span> <span data-ttu-id="03ea4-113"> (可选) \为\** \@ article_i\d\**指定步骤2中的项目 ID。</span><span class="sxs-lookup"><span data-stu-id="03ea4-113">(Optional) Specify the article ID from step 2 for **\@article_id**.</span></span> <span data-ttu-id="03ea4-114"> (可选) 指\定\** \@ publisher_database_id**的发布数据库的 ID，该 ID 可从[sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)目录视图中的**database_i\d\**列获取。</span><span class="sxs-lookup"><span data-stu-id="03ea4-114">(Optional) Specify the ID of the publication database for **\@publisher_database_id**, which can be obtained from the **database_id** column in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ea4-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03ea4-115">See Also</span></span>  
 [<span data-ttu-id="03ea4-116">以编程方式监视复制</span><span class="sxs-lookup"><span data-stu-id="03ea4-116">Programmatically Monitor Replication</span></span>](../monitoring-replication.md)  
  
  
