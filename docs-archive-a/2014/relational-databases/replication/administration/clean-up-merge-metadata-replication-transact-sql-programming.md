---
title: 清除合并元数据（复制 Transact-SQL 编程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a2306db72fd3f0098e18ff058796a5498eafcac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691699"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a><span data-ttu-id="8f59f-102">清除合并元数据（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="8f59f-102">Clean Up Merge Metadata (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="8f59f-103">合并代理基于发布的保持设置定期清除合并复制元数据。</span><span class="sxs-lookup"><span data-stu-id="8f59f-103">Merge replication metadata is cleaned up periodically by the Merge Agent based on the retention setting for the publication.</span></span> <span data-ttu-id="8f59f-104">在发布服务器和订阅服务器的 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)和 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) 系统表中将定期清除元数据。</span><span class="sxs-lookup"><span data-stu-id="8f59f-104">This occurs at the Publisher and Subscriber in the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) system tables.</span></span> <span data-ttu-id="8f59f-105">还可以使用复制存储过程以编程方式清除这些表中的数据。</span><span class="sxs-lookup"><span data-stu-id="8f59f-105">You can also programmatically clean up the data in these tables using replication stored procedures.</span></span>  
  
### <a name="to-manually-clean-up-merge-metadata"></a><span data-ttu-id="8f59f-106">手动清除合并元数据</span><span class="sxs-lookup"><span data-stu-id="8f59f-106">To manually clean up merge metadata</span></span>  
  
1.  <span data-ttu-id="8f59f-107">在发布服务器的发布数据库中，执行 [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8f59f-107">At the Publisher on the publication database, execute [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).</span></span>  
  
2.  <span data-ttu-id="8f59f-108"> (可选) 请注意在步骤1中从[MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)和[MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)系统表中删除的行数，分别在 **@num_genhistory_rows** 、 **@num_contents_rows** 和 **@num_tombstone_rows** 输出参数中返回。</span><span class="sxs-lookup"><span data-stu-id="8f59f-108">(Optional) Note the number of rows removed in step 1 from the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), and [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) system tables, returned respectively in the **@num_genhistory_rows**, **@num_contents_rows**, and **@num_tombstone_rows** output parameters.</span></span>  
  
3.  <span data-ttu-id="8f59f-109">在订阅服务器中重复步骤 1 和 2 来清除订阅数据库的元数据。</span><span class="sxs-lookup"><span data-stu-id="8f59f-109">Repeat steps 1 and 2 at the Subscriber to clean up metadata on the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f59f-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f59f-110">See Also</span></span>  
 [<span data-ttu-id="8f59f-111">订阅过期和停用</span><span class="sxs-lookup"><span data-stu-id="8f59f-111">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  
