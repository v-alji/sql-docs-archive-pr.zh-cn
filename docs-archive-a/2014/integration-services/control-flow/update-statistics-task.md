---
title: “更新统计信息”任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.updatestatisticstask.f1
helpviewer_keywords:
- updating statistics
- Update Statistics task [Integration Services]
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1507ada1e4fa087901383930fce4996c191fb553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576905"
---
# <a name="update-statistics-task"></a><span data-ttu-id="d9440-102">“更新统计信息”任务</span><span class="sxs-lookup"><span data-stu-id="d9440-102">Update Statistics Task</span></span>
  <span data-ttu-id="d9440-103">“更新统计信息”任务为指定的表或索引视图中的一个或多个统计信息组（集合）更新键值分布信息。</span><span class="sxs-lookup"><span data-stu-id="d9440-103">The Update Statistics task updates information about the distribution of key values for one or more statistics groups (collections) in the specified table or indexed view.</span></span> <span data-ttu-id="d9440-104">有关详细信息，请参阅[统计信息](../../relational-databases/statistics/statistics.md)。</span><span class="sxs-lookup"><span data-stu-id="d9440-104">For more information, see [Statistics](../../relational-databases/statistics/statistics.md).</span></span>  
  
 <span data-ttu-id="d9440-105">通过使用“更新统计信息”任务，包可以为单个数据库或多个数据库更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="d9440-105">By using the Update Statistics task, a package can update statistics for a single database or multiple databases.</span></span> <span data-ttu-id="d9440-106">如果此任务仅更新单个数据库中的统计信息，则可以选择任务要为其更新统计信息的视图或表。</span><span class="sxs-lookup"><span data-stu-id="d9440-106">If the task updates only the statistics in a single database, you can choose the views or the tables whose statistics the task updates.</span></span> <span data-ttu-id="d9440-107">可以配置更新来更新所有统计信息、仅更新列统计信息或仅更新索引统计信息。</span><span class="sxs-lookup"><span data-stu-id="d9440-107">You can configure the update to update all statistics, column statistics only, or index statistics only.</span></span>  
  
 <span data-ttu-id="d9440-108">此任务封装 UPDATE STATISTICS 语句，其中包括下列参数和子句：</span><span class="sxs-lookup"><span data-stu-id="d9440-108">This task encapsulates an UPDATE STATISTICS statement, including the following arguments and clauses:</span></span>  
  
-   <span data-ttu-id="d9440-109">table_name 或 view_name 参数   。</span><span class="sxs-lookup"><span data-stu-id="d9440-109">The *table_name* or *view_name* argument.</span></span>  
  
-   <span data-ttu-id="d9440-110">如果更新应用于所有统计信息，则暗示使用 WITH ALL 子句。</span><span class="sxs-lookup"><span data-stu-id="d9440-110">If the update applies to all statistics, the WITH ALL clause is implied.</span></span>  
  
-   <span data-ttu-id="d9440-111">如果更新仅应用于列，则包含 WITH COLUMN 子句。</span><span class="sxs-lookup"><span data-stu-id="d9440-111">If the update applies only to columns, the WITH COLUMN clause is included.</span></span>  
  
-   <span data-ttu-id="d9440-112">如果更新仅应用于索引，则包含 WITH INDEX 子句。</span><span class="sxs-lookup"><span data-stu-id="d9440-112">If the update applies only to indexes, the WITH INDEX clause is included.</span></span>  
  
 <span data-ttu-id="d9440-113">如果“更新统计信息”任务更新多个数据库中的统计信息，则它将运行多个 UPDATE STATISTICS 语句，每个语句用于一个表或视图。</span><span class="sxs-lookup"><span data-stu-id="d9440-113">If the Update Statistics task updates statistics in multiple databases, the task runs multiple UPDATE STATISTICS statements, one for each table or view.</span></span> <span data-ttu-id="d9440-114">UPDATE STATISTICS 的所有实例均使用相同的子句，但使用不同的 table_name 或 view_name 值   。</span><span class="sxs-lookup"><span data-stu-id="d9440-114">All instances of UPDATE STATISTICS use the same clause, but different *table_name* or *view_name* values.</span></span> <span data-ttu-id="d9440-115">有关详细信息，请参阅 [CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql) 和 [UPDATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/update-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d9440-115">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) and [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9440-116">此任务创建它所运行的 Transact-SQL 语句花费的时间与它更新的统计信息数成正比。</span><span class="sxs-lookup"><span data-stu-id="d9440-116">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of statistics the task updates.</span></span> <span data-ttu-id="d9440-117">如果配置此任务来更新具有大量索引的数据库中所有表和视图中的统计信息，或更新多个数据库中的统计信息，则任务将花费相当长的时间来生成 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="d9440-117">If the task is configured to update statistics in all the tables and views in a database with a large number of indexes, or to update statistics in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-update-statistics-task"></a><span data-ttu-id="d9440-118">“更新统计信息”任务的配置</span><span class="sxs-lookup"><span data-stu-id="d9440-118">Configuration of the Update Statistics Task</span></span>  
 <span data-ttu-id="d9440-119">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="d9440-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="d9440-120">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="d9440-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="d9440-121">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="d9440-121">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d9440-122">“更新统计信息”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="d9440-122">Update Statistics Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/update-statistics-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="d9440-123">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d9440-123">Related Tasks</span></span>  
 <span data-ttu-id="d9440-124">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="d9440-124">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d9440-125">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="d9440-125">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9440-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9440-126">See Also</span></span>  
 <span data-ttu-id="d9440-127">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="d9440-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="d9440-128">控制流</span><span class="sxs-lookup"><span data-stu-id="d9440-128">Control Flow</span></span>](control-flow.md)  
  
  
