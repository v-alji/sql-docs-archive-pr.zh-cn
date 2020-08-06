---
title: 为事务复制启用协调备份 (复制 Transact-sql 编程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77405cd968fa917c3ccc799eb7d168782443eee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693780"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a><span data-ttu-id="db381-102">为事务复制启用协调备份（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="db381-102">Enable Coordinated Backups for Transactional Replication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="db381-103">在为数据库启用事务复制时，可以指定在传递到分发数据库之前必须备份所有事务。</span><span class="sxs-lookup"><span data-stu-id="db381-103">When enabling a database for transactional replication, you can specify that all transactions must be backed up before being delivered to the distribution database.</span></span> <span data-ttu-id="db381-104">也可以对分发数据库启用协调备份，以便在传播到分发服务器的事务未备份前不会截断发布数据库的事务日志。</span><span class="sxs-lookup"><span data-stu-id="db381-104">You can also enable coordinated backup on the distribution database so that the transaction log for the publication database is not truncated until transactions that have been propagated to the Distributor have been backed up.</span></span> <span data-ttu-id="db381-105">有关详细信息，请参阅 [快照复制和事务复制的备份和还原策略](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="db381-105">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a><span data-ttu-id="db381-106">为与事务复制一起发布的数据库启用协调备份</span><span class="sxs-lookup"><span data-stu-id="db381-106">To enable coordinated backups for a database published with transactional replication</span></span>  
  
1.  <span data-ttu-id="db381-107">在发布数据库中，使用 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 函数返回发布数据库的 **IsSyncWithBackup** 属性。</span><span class="sxs-lookup"><span data-stu-id="db381-107">At the Publisher, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the publication database.</span></span> <span data-ttu-id="db381-108">如果函数返回 **1**，则表明已为发布的数据库启用了协调备份。</span><span class="sxs-lookup"><span data-stu-id="db381-108">If the function returns **1**, coordinated backups are already enabled for the published database.</span></span>  
  
2.  <span data-ttu-id="db381-109">如果步骤 1 中的函数返回 **0**，则在发布服务器的发布数据库中执行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db381-109">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="db381-110">为 \@optname\*\*\*\* 指定值 sync with backup\*\*\*\*，并为 \@value\*\*\*\* 指定 true\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db381-110">Specify a value of **sync with backup** for **\@optname**, and **true** for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db381-111">如果将 **sync with backup** 选项更改为 **false**，则运行日志读取器代理或达到运行间隔（如果日志读取器代理配置为连续运行）之后将更新发布数据库的截断点。</span><span class="sxs-lookup"><span data-stu-id="db381-111">If you change the **sync with backup** option to **false**, the truncation point of the publication database will be updated after the Log Reader Agent runs, or after an interval if the Log Reader Agent is running continuously.</span></span> <span data-ttu-id="db381-112">最大间隔由 -MessageInterval 代理参数控制（默认值为 30 秒）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db381-112">The maximum interval is controlled by the **-MessageInterval** agent parameter (which has a default of 30 seconds).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a><span data-ttu-id="db381-113">为分发数据库启用协调备份</span><span class="sxs-lookup"><span data-stu-id="db381-113">To enable coordinated backups for a distribution database</span></span>  
  
1.  <span data-ttu-id="db381-114">在发布数据库中，使用 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 函数返回分发数据库的 **IsSyncWithBackup** 属性。</span><span class="sxs-lookup"><span data-stu-id="db381-114">At the Distributor, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the distribution database.</span></span> <span data-ttu-id="db381-115">如果函数返回 **1**，则表明已为分发数据库启用了协调备份。</span><span class="sxs-lookup"><span data-stu-id="db381-115">If the function returns **1**, coordinated backups are already enabled for the distribution database.</span></span>  
  
2.  <span data-ttu-id="db381-116">如果步骤 1 中的函数返回 **0**，则在分发服务器的分发数据库中执行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db381-116">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="db381-117">为\*\* \@ optname**指定值**sync with backup\*\* ，并为\*\* \@ value**指定**true\*\* 。</span><span class="sxs-lookup"><span data-stu-id="db381-117">Specify a value of **sync with backup** for **\@optname** and **true** for **\@value**.</span></span>  
  
### <a name="to-disable-coordinated-backups"></a><span data-ttu-id="db381-118">禁用协调备份</span><span class="sxs-lookup"><span data-stu-id="db381-118">To disable coordinated backups</span></span>  
  
1.  <span data-ttu-id="db381-119">在发布服务器的发布数据库或在分发服务器的分发数据库中，执行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db381-119">At either the Publisher on the publication database or at the Distributor on the distribution database, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span> <span data-ttu-id="db381-120">为\*\* \@ optname**指定值**sync with backup\*\* ，并为\*\* \@ value**指定**false\*\* 。</span><span class="sxs-lookup"><span data-stu-id="db381-120">Specify a value of **sync with backup** for **\@optname** and **false** for **\@value**.</span></span>  
  
  
