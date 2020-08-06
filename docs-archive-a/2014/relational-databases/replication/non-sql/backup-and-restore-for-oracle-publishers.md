---
title: Oracle 发布服务器的备份和还原 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6b994c34e4f4bebc010fe6d71bbd43f6e557cbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577548"
---
# <a name="backup-and-restore-for-oracle-publishers"></a><span data-ttu-id="72594-102">Oracle 发布服务器的备份和还原</span><span class="sxs-lookup"><span data-stu-id="72594-102">Backup and Restore for Oracle Publishers</span></span>
  <span data-ttu-id="72594-103">在备份和还原时，请遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="72594-103">Follow these guidelines when backing up and restoring:</span></span>  
  
-   <span data-ttu-id="72594-104">在备份发布服务器时，确保日志读取器代理未运行，并且未在发布的表上进行其他数据库活动。</span><span class="sxs-lookup"><span data-stu-id="72594-104">Ensure the Log Reader Agent does not run and that other database activity on the published tables does not occur while the Publisher is being backed up.</span></span>  
  
-   <span data-ttu-id="72594-105">同时备份发布服务器和分发服务器。</span><span class="sxs-lookup"><span data-stu-id="72594-105">Backup up the Publisher and Distributor at the same time.</span></span>  
  
-   <span data-ttu-id="72594-106">如果必须还原发布服务器或分发服务器，请重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="72594-106">If the Publisher or Distributor must be restored, reinitialize all subscriptions.</span></span>  
  
-   <span data-ttu-id="72594-107">若要从备份中还原订阅服务器（无须重新初始化订阅），则订阅数据库最后一次备份完成之后传递到分发数据库的事务必须仍然可用。</span><span class="sxs-lookup"><span data-stu-id="72594-107">To restore a Subscriber from a backup (without having to reinitialize subscriptions), the transactions delivered to the distribution database after the last subscription database backup was completed must still be available.</span></span> <span data-ttu-id="72594-108">事务可用的时间长度取决于分发保持设置。</span><span class="sxs-lookup"><span data-stu-id="72594-108">The length of time transactions are available depends on distribution retention settings.</span></span> <span data-ttu-id="72594-109">有关这些设置的信息，请参阅[订阅过期和停用](../subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="72594-109">For information on these settings, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
-   <span data-ttu-id="72594-110">如果由于数据还原造成发布服务器或分发服务器不同步，则复制代理将错误消息写入日志。</span><span class="sxs-lookup"><span data-stu-id="72594-110">If the Publisher or Distributor becomes out of sync as the result of a database restore, the replication agents log error messages.</span></span> <span data-ttu-id="72594-111">此时，必须删除并重新创建所有相关的发布和订阅：</span><span class="sxs-lookup"><span data-stu-id="72594-111">At this point, you must drop and recreate all relevant publications and subscriptions:</span></span>  
  
    1.  <span data-ttu-id="72594-112">编写发布和订阅的定义脚本。</span><span class="sxs-lookup"><span data-stu-id="72594-112">Script the definition of the publications and subscriptions.</span></span> <span data-ttu-id="72594-113">有关详细信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="72594-113">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
         <span data-ttu-id="72594-114">如果在发布服务器和分发服务器状态的版本中发布定义有所更改，就需要修改脚本。</span><span class="sxs-lookup"><span data-stu-id="72594-114">If the definition of the publications has changed between the versions of the Publisher and Distributor states, you will need to modify the scripts.</span></span>  
  
    2.  <span data-ttu-id="72594-115">删除发布和订阅。</span><span class="sxs-lookup"><span data-stu-id="72594-115">Drop the publications and subscriptions.</span></span>  
  
    3.  <span data-ttu-id="72594-116">运行步骤 1 中创建的脚本。</span><span class="sxs-lookup"><span data-stu-id="72594-116">Run the scripts created in step 1.</span></span>  
  
     <span data-ttu-id="72594-117">如果必须删除和重新配置发布服务器，请使用 **CASCADE** 选项删除 **MSSQLSERVERDISTRIBUTOR** 公共同义词和已配置的 Oracle 复制用户，以便从 Oracle 发布服务器中删除所有复制对象。</span><span class="sxs-lookup"><span data-stu-id="72594-117">If the Publisher must be dropped and reconfigured, drop the **MSSQLSERVERDISTRIBUTOR** public synonym and the configured Oracle replication user with the **CASCADE** option to remove all replication objects from the Oracle Publisher.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72594-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72594-118">See Also</span></span>  
 <span data-ttu-id="72594-119">[备份和还原复制的数据库](../administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="72594-119">[Back Up and Restore Replicated Databases](../administration/back-up-and-restore-replicated-databases.md) </span></span>  
 <span data-ttu-id="72594-120">[配置 Oracle 发布服务器](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="72594-120">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="72594-121">Oracle 发布概述</span><span class="sxs-lookup"><span data-stu-id="72594-121">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
