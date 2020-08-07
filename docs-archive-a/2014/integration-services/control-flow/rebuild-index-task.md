---
title: “重新生成索引”任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33bbe25bc8c47f4f749f95dbb7096c3a76c25297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587958"
---
# <a name="rebuild-index-task"></a><span data-ttu-id="b64a8-102">“重新生成索引”任务</span><span class="sxs-lookup"><span data-stu-id="b64a8-102">Rebuild Index Task</span></span>
  <span data-ttu-id="b64a8-103">“重新生成索引”任务重新生成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库表和视图中的索引。</span><span class="sxs-lookup"><span data-stu-id="b64a8-103">The Rebuild Index task rebuilds indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="b64a8-104">有关管理索引的详细信息，请参阅 [重新组织和重新生成索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="b64a8-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="b64a8-105">通过使用“重新生成索引”任务，包可以重新生成单个数据库或多个数据库中的索引。</span><span class="sxs-lookup"><span data-stu-id="b64a8-105">By using the Rebuild Index task, a package can rebuild indexes in a single database or multiple databases.</span></span> <span data-ttu-id="b64a8-106">如果任务仅重新生成单个数据库中的索引，则可以选择任务要重新生成其索引的视图和表。</span><span class="sxs-lookup"><span data-stu-id="b64a8-106">If the task rebuilds only the indexes in a single database, you can choose the views and tables whose indexes the task rebuilds.</span></span>  
  
 <span data-ttu-id="b64a8-107">此任务封装 ALTER INDEX REBUILD 语句并提供下列索引重新生成选项：</span><span class="sxs-lookup"><span data-stu-id="b64a8-107">This task encapsulates an ALTER INDEX REBUILD statement with the following index rebuild options:</span></span>  
  
-   <span data-ttu-id="b64a8-108">指定 FILLFACTOR 百分比或使用原始的 FILLFACTOR 量。</span><span class="sxs-lookup"><span data-stu-id="b64a8-108">Specify a FILLFACTOR percentage or use the original FILLFACTOR amount.</span></span>  
  
-   <span data-ttu-id="b64a8-109">设置 PAD_INDEX = ON，以将 FILLFACTOR 所指定的可用空间分配给索引的中间级别页。</span><span class="sxs-lookup"><span data-stu-id="b64a8-109">Set PAD_INDEX = ON to allocate the free space specified by FILLFACTOR to the intermediate-level pages of the index.</span></span>  
  
-   <span data-ttu-id="b64a8-110">设置 SORT_IN_TEMPDB = ON，以存储用于重新生成 tempdb 中索引的中间排序结果。</span><span class="sxs-lookup"><span data-stu-id="b64a8-110">Set SORT_IN_TEMPDB = ON to store the intermediate sort result used to rebuild the index in tempdb.</span></span> <span data-ttu-id="b64a8-111">当中间排序结果被设置为 OFF 时，结果和索引存储在同一数据库中。</span><span class="sxs-lookup"><span data-stu-id="b64a8-111">When the intermediate sort result is set to OFF, the result is stored in the same database as the index.</span></span>  
  
-   <span data-ttu-id="b64a8-112">设置 IGNORE_DUP_KEY = ON，以便允许多行插入操作（包含违反唯一约束的记录）插入不违反唯一约束的记录。</span><span class="sxs-lookup"><span data-stu-id="b64a8-112">Set IGNORE_DUP_KEY = ON to allow a multirow insert operation that includes records that violate unique constraints to insert the records that do not violate the unique constraints.</span></span>  
  
-   <span data-ttu-id="b64a8-113">设置 ONLINE = ON 以便不保持表锁，这样，将可以在重建索引期间对基础表进行查询或更新。</span><span class="sxs-lookup"><span data-stu-id="b64a8-113">Set ONLINE = ON to not hold table locks so that queries or updates to the underlying table can proceed during re-indexing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b64a8-114">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的各版本中均不提供联机索引操作。</span><span class="sxs-lookup"><span data-stu-id="b64a8-114">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b64a8-115">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="b64a8-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="b64a8-116">有关 ALTER INDEX 语句和索引重新生成选项的详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b64a8-116">For more information about the ALTER INDEX statement and index rebuild options, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b64a8-117">此任务创建它所运行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句花费的时间与它重新生成的索引数成正比。</span><span class="sxs-lookup"><span data-stu-id="b64a8-117">The time the task takes to create the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that the task runs is proportionate to the number of indexes the task rebuilds.</span></span> <span data-ttu-id="b64a8-118">如果配置此任务来重新生成具有大量索引的数据库中所有表和视图中的索引，或重新生成多个数据库中的索引，则任务将花费相当长的时间来生成 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="b64a8-118">If the task is configured to rebuild indexes in all the tables and views in a database with a large number of indexes, or to rebuild indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-rebuild-index-task"></a><span data-ttu-id="b64a8-119">“重新生成索引”任务的配置</span><span class="sxs-lookup"><span data-stu-id="b64a8-119">Configuration of the Rebuild Index Task</span></span>  
 <span data-ttu-id="b64a8-120">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="b64a8-120">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="b64a8-121">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="b64a8-121">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="b64a8-122">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="b64a8-122">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
 [<span data-ttu-id="b64a8-123">“重新生成索引”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="b64a8-123">Rebuild Index Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="b64a8-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b64a8-124">Related Tasks</span></span>  
 <span data-ttu-id="b64a8-125">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的更多信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="b64a8-125">For more about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64a8-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b64a8-126">See Also</span></span>  
 <span data-ttu-id="b64a8-127">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="b64a8-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="b64a8-128">控制流</span><span class="sxs-lookup"><span data-stu-id="b64a8-128">Control Flow</span></span>](control-flow.md)  
  
  
