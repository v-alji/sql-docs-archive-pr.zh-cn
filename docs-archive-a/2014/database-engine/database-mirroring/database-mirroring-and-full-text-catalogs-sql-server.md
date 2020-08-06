---
title: 数据库镜像和全文目录 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- full-text catalogs [SQL Server], database mirroring
- catalogs [SQL Server], database mirroring
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 39929f4bed6edbd1e8ec5c1b72dbe8f7aefeec68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579765"
---
# <a name="database-mirroring-and-full-text-catalogs-sql-server"></a><span data-ttu-id="a2307-102">数据库镜像和全文目录 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2307-102">Database Mirroring and Full-Text Catalogs (SQL Server)</span></span>
  <span data-ttu-id="a2307-103">若要对带有全文目录的数据库进行镜像，请使用常规备份创建主体数据库的完整数据库备份，然后还原备份，以便将数据库复制到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="a2307-103">To mirror a database that has a full-text catalog, use backup as usual to create a full database backup of the principal database, and then restore the backup to copy the database to the mirror server.</span></span> <span data-ttu-id="a2307-104">有关详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="a2307-104">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
## <a name="full-text-catalog-and-indexes-before-failover"></a><span data-ttu-id="a2307-105">故障转移前的全文目录和索引</span><span class="sxs-lookup"><span data-stu-id="a2307-105">Full-Text Catalog and Indexes Before Failover</span></span>  
 <span data-ttu-id="a2307-106">新建镜像数据库中的全文目录与数据库备份时的全文目录相同。</span><span class="sxs-lookup"><span data-stu-id="a2307-106">In a newly created mirror database, the full-text catalog is the same as when the database was backed up.</span></span> <span data-ttu-id="a2307-107">数据库镜像开始后，对 DDL 语句（CREATE FULLTEXT CATALOG、ALTER FULLTEXT CATALOG、DROP FULLTEXT CATALOG）所做的任意目录级更改都会被记录下来，发送到镜像服务器，在镜像数据库中进行重播。</span><span class="sxs-lookup"><span data-stu-id="a2307-107">After database mirroring starts, any catalog-level changes that were made by DDL statements (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) are logged and sent to the mirror server to be replayed on the mirror database.</span></span> <span data-ttu-id="a2307-108">但是，镜像数据库中不会重新生成索引级更改，因为镜像数据库没有登录到主体服务器上。</span><span class="sxs-lookup"><span data-stu-id="a2307-108">However, index-level changes are not reproduced on the mirror database because it is not logged on to the principal server.</span></span> <span data-ttu-id="a2307-109">因此，当主体数据库中的全文目录内容发生变化时，镜像数据库中的全文目录内容便不再同步。</span><span class="sxs-lookup"><span data-stu-id="a2307-109">Therefore, as the contents of the full-text catalog change on the principal database, the contents of the full-text catalog on the mirror database are unsynchronized.</span></span>  
  
## <a name="full-text-indexes-after-failover"></a><span data-ttu-id="a2307-110">故障转移后的全文索引</span><span class="sxs-lookup"><span data-stu-id="a2307-110">Full-Text Indexes After Failover</span></span>  
 <span data-ttu-id="a2307-111">故障转移后，在下列情况下，可能需要对新主体服务器上的全文索引进行完全爬网，即便不是必需，也会有所帮助：</span><span class="sxs-lookup"><span data-stu-id="a2307-111">After a failover, a full crawl of a full-text index on the new principal server might be required or useful in the following situations:</span></span>  
  
-   <span data-ttu-id="a2307-112">如果全文索引的更改跟踪功能处于关闭状态，则必须使用下面的语句对该索引启动完全爬网：</span><span class="sxs-lookup"><span data-stu-id="a2307-112">If change-tracking is turned OFF on a full text index, you must start a full crawl on that index by using the following statement:</span></span>  
  
     <span data-ttu-id="a2307-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span><span class="sxs-lookup"><span data-stu-id="a2307-113">ALTER FULLTEXT INDEX ON *table_name* START FULL POPULATION</span></span>  
  
-   <span data-ttu-id="a2307-114">如果全文索引被配置为自动跟踪更改，则将自动同步全文索引。</span><span class="sxs-lookup"><span data-stu-id="a2307-114">If a full-text index is configured for automatic change tracking, the full-text index is automatically synchronized.</span></span> <span data-ttu-id="a2307-115">但是，同步过程多少会降低全文索引的性能。</span><span class="sxs-lookup"><span data-stu-id="a2307-115">However, synchronization slows full-text performance somewhat.</span></span> <span data-ttu-id="a2307-116">如果性能太低，则可以通过关闭更改跟踪然后将其重置为自动的方式来启动完全爬网：</span><span class="sxs-lookup"><span data-stu-id="a2307-116">If performance is too slow, you can cause a full crawl by setting change tracking off and then resetting it to automatic:</span></span>  
  
    -   <span data-ttu-id="a2307-117">关闭更改跟踪：</span><span class="sxs-lookup"><span data-stu-id="a2307-117">To set change tracking off:</span></span>  
  
         <span data-ttu-id="a2307-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="a2307-118">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING OFF</span></span>  
  
    -   <span data-ttu-id="a2307-119">开启自动更改跟踪：</span><span class="sxs-lookup"><span data-stu-id="a2307-119">To set on automatic change tracking to automatic:</span></span>  
  
         <span data-ttu-id="a2307-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="a2307-120">ALTER FULLTEXT INDEX ON *table_name* SET CHANGE_TRACKING AUTO</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2307-121">若要查看是否已开启自动更改跟踪，可以使用 [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) 函数查询表的 **TableFullTextBackgroundUpdateIndexOn** 属性。</span><span class="sxs-lookup"><span data-stu-id="a2307-121">To see whether auto change tracking is on, you can use the [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) function to query the **TableFullTextBackgroundUpdateIndexOn** property of the table.</span></span>  
  
 <span data-ttu-id="a2307-122">有关详细信息，请参阅 [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a2307-122">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2307-123">在故障转移后启动爬网与在还原后启动爬网相似。</span><span class="sxs-lookup"><span data-stu-id="a2307-123">Starting a crawl after failover works the same as starting a crawl after a restore.</span></span>  
  
## <a name="after-forcing-service"></a><span data-ttu-id="a2307-124">强制服务后</span><span class="sxs-lookup"><span data-stu-id="a2307-124">After Forcing Service</span></span>  
 <span data-ttu-id="a2307-125">对镜像服务器强制运行服务后（可能造成数据丢失），启动完全爬网。</span><span class="sxs-lookup"><span data-stu-id="a2307-125">After service is forced to the mirror server (with possible data loss), start a full crawl.</span></span> <span data-ttu-id="a2307-126">启动完全爬网的方法取决于是否对全文索引启动了更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="a2307-126">The method to use for starting a full crawl depends on whether the full-text index is change tracked.</span></span> <span data-ttu-id="a2307-127">有关详细信息，请参阅本主题前面的“故障转移后的全文索引”。</span><span class="sxs-lookup"><span data-stu-id="a2307-127">For more information, see "Full-Text Indexes After Failover," earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2307-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2307-128">See Also</span></span>  
 <span data-ttu-id="a2307-129">[ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a2307-129">[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="a2307-130">[CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a2307-130">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="a2307-131">[DROP FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a2307-131">[DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="a2307-132">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a2307-132">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="a2307-133">备份和还原全文目录和索引</span><span class="sxs-lookup"><span data-stu-id="a2307-133">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
  
