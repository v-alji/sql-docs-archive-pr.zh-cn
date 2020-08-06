---
title: 监视数据和差异文件对的合并以及排除其故障Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5dc57d08f3db1792a9359b3aa79aaceecd03a025
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590367"
---
# <a name="monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs"></a><span data-ttu-id="0d251-102">监视数据与差异文件对的合并以及排除其故障</span><span class="sxs-lookup"><span data-stu-id="0d251-102">Monitoring and Troubleshooting Merge for Data and Delta File Pairs</span></span>
  <span data-ttu-id="0d251-103">内存中 OLTP 使用合并策略自动合并相邻数据和差异文件对。</span><span class="sxs-lookup"><span data-stu-id="0d251-103">In-Memory OLTP uses a merge policy to merge adjacent data and delta file pairs automatically.</span></span> <span data-ttu-id="0d251-104">无法禁用合并活动。</span><span class="sxs-lookup"><span data-stu-id="0d251-104">You cannot disable merge activity.</span></span>  
  
 <span data-ttu-id="0d251-105">可按如下方式监视数据和差异文件对：</span><span class="sxs-lookup"><span data-stu-id="0d251-105">You can monitor data and delta file pairs, as follows:</span></span>  
  
-   <span data-ttu-id="0d251-106">将内存中存储的大小与存储的总大小进行比较。</span><span class="sxs-lookup"><span data-stu-id="0d251-106">Compare the size of in-memory storage to overall size of storage.</span></span> <span data-ttu-id="0d251-107">如果存储大得不成比例，则可能未触发合并。</span><span class="sxs-lookup"><span data-stu-id="0d251-107">If the storage is dis-proportionately large, then it is likely that merge is not getting triggered.</span></span> <span data-ttu-id="0d251-108">有关信息</span><span class="sxs-lookup"><span data-stu-id="0d251-108">For information</span></span>  
  
-   <span data-ttu-id="0d251-109">使用[sys. dm_db_xtp_checkpoint_files &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql)查看数据和差异文件中的已用空间，以查看是否在其应该触发 merge。</span><span class="sxs-lookup"><span data-stu-id="0d251-109">Look at the used space in data and delta files using [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) to see if merge is not getting triggered when it should.</span></span>  
  
## <a name="performing-a-manual-merge"></a><span data-ttu-id="0d251-110">执行手动合并</span><span class="sxs-lookup"><span data-stu-id="0d251-110">Performing a Manual Merge</span></span>  
 <span data-ttu-id="0d251-111">您可以使用[sys. sp_xtp_merge_checkpoint_files &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)执行手动合并。</span><span class="sxs-lookup"><span data-stu-id="0d251-111">You can use [sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) to perform a manual merge.</span></span>  
  
 <span data-ttu-id="0d251-112">使用以下查询检索有关数据和差异文件的信息，</span><span class="sxs-lookup"><span data-stu-id="0d251-112">Use the following query to retrieve information about the data and delta files,</span></span>  
  
```sql  
select checkpoint_file_id, file_type_desc, internal_storage_slot, file_size_in_bytes, file_size_used_in_bytes,   
inserted_row_count, deleted_row_count, lower_bound_tsn, upper_bound_tsn   
from sys.dm_db_xtp_checkpoint_files  
where state = 1  
order by file_type_desc, upper_bound_tsn  
```  
  
 <span data-ttu-id="0d251-113">假设您找到了三个未合并的数据文件。</span><span class="sxs-lookup"><span data-stu-id="0d251-113">Assume that you found three data files that have not been merged.</span></span> <span data-ttu-id="0d251-114">可使用第一个数据文件的 `lower_bound_tsn` 值和最后一个数据文件的 `upper_bound_tsn` 发出以下命令：</span><span class="sxs-lookup"><span data-stu-id="0d251-114">Using the `lower_bound_tsn` value of the first data file and the `upper_bound_tsn` of the last data file, you can issue the following command:</span></span>  
  
```sql  
exec sys.sp_xtp_merge_checkpoint_files 'H_DB',  12345, 67890  
```  
  
 <span data-ttu-id="0d251-115">假定三个数据和差异文件对的每一对都有 15836 行，并且其中删除了 5279 行。</span><span class="sxs-lookup"><span data-stu-id="0d251-115">Assume that the three data and delta file pairs each had 15,836 rows and 5,279 deleted rows.</span></span> <span data-ttu-id="0d251-116">合并后，新数据文件有 31872 行，未删除行。</span><span class="sxs-lookup"><span data-stu-id="0d251-116">After the merge, the new data file has 31,872 rows and 0 deleted rows.</span></span> <span data-ttu-id="0d251-117">新数据文件的大小可远远大于初始分配的 128MB 大小。</span><span class="sxs-lookup"><span data-stu-id="0d251-117">The size of the new data file can be much larger than the initially allocated size of 128MB.</span></span> <span data-ttu-id="0d251-118">这是因为手动合并优先于合并策略，强制合并所请求的文件。</span><span class="sxs-lookup"><span data-stu-id="0d251-118">This is because manual merge overrides the merge policy and forces the merge of the requested files.</span></span>  
  
 <span data-ttu-id="0d251-119">[具有内存优化表的数据库中检查点文件的博客状态转换](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/)说明数据和差异文件对从开始到垃圾回收的状态转换。</span><span class="sxs-lookup"><span data-stu-id="0d251-119">The blog [State Transition of Checkpoint Files in Databases with Memory-Optimized Tables](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/) describes state transition of data and delta file pairs from inception to garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d251-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d251-120">See Also</span></span>  
 [<span data-ttu-id="0d251-121">创建和管理用于内存优化对象的存储</span><span class="sxs-lookup"><span data-stu-id="0d251-121">Creating and Managing Storage for Memory-Optimized Objects</span></span>](../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
