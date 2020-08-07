---
title: “重新组织索引”任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3f910391bd3a5a35770bb677bc17c91a00ace457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587956"
---
# <a name="reorganize-index-task"></a><span data-ttu-id="241ca-102">“重新组织索引”任务</span><span class="sxs-lookup"><span data-stu-id="241ca-102">Reorganize Index Task</span></span>
  <span data-ttu-id="241ca-103">“重新组织索引”任务重新组织 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库表和视图中的索引。</span><span class="sxs-lookup"><span data-stu-id="241ca-103">The Reorganize Index task reorganizes indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="241ca-104">有关管理索引的详细信息，请参阅 [重新组织和重新生成索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="241ca-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="241ca-105">通过使用“重新组织索引”任务，包可以重新组织单个数据库或多个数据库中的索引。</span><span class="sxs-lookup"><span data-stu-id="241ca-105">By using the Reorganize Index task, a package can reorganize indexes in a single database or multiple databases.</span></span> <span data-ttu-id="241ca-106">如果此任务仅重新组织单个数据库中的索引，则可以选择任务要重新组织其索引的视图或表。</span><span class="sxs-lookup"><span data-stu-id="241ca-106">If the task reorganizes only the indexes in a single database, you can choose the views or the tables whose indexes the task reorganizes.</span></span> <span data-ttu-id="241ca-107">“重新组织索引”任务还包含压缩大型对象数据的选项。</span><span class="sxs-lookup"><span data-stu-id="241ca-107">The Reorganize Index task also includes an option to compact large object data.</span></span> <span data-ttu-id="241ca-108">大型对象数据是具有 `image`、`text`、`ntext`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)` 或 `xml` 数据类型的数据。</span><span class="sxs-lookup"><span data-stu-id="241ca-108">Large object data is data with the `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, or `xml` data type.</span></span> <span data-ttu-id="241ca-109">有关详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="241ca-109">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="241ca-110">“重新组织索引”任务封装了 Transact-SQL ALTER INDEX 语句。</span><span class="sxs-lookup"><span data-stu-id="241ca-110">The Reorganize Index task encapsulates the Transact-SQL ALTER INDEX statement.</span></span> <span data-ttu-id="241ca-111">如果选择压缩大型对象数据，则该语句使用 REORGANIZE WITH (LOB_COMPACTION = ON) 子句，否则 LOB_COMPACTION 将设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="241ca-111">If you choose to compact large object data, the statement uses the REORGANIZE WITH (LOB_COMPACTION = ON) clause, otherwise LOB_COMPACTION is set to OFF.</span></span> <span data-ttu-id="241ca-112">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="241ca-112">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="241ca-113">此任务创建其运行的 Transact-SQL 语句所需的时间与任务重新组织的索引数成正比。</span><span class="sxs-lookup"><span data-stu-id="241ca-113">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of indexes the task reorganizes.</span></span> <span data-ttu-id="241ca-114">如果配置此任务来重新组织具有大量索引的数据库中所有表和视图中的索引，或重新组织多个数据库中的索引，则任务将花费相当长的时间来生成 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="241ca-114">If the task is configured to reorganize indexes in all the tables and views in a database that holds a large number of indexes, or to reorganize indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-reorganize-index-task"></a><span data-ttu-id="241ca-115">“重新组织索引”任务的配置</span><span class="sxs-lookup"><span data-stu-id="241ca-115">Configuration of the Reorganize Index Task</span></span>  
 <span data-ttu-id="241ca-116">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="241ca-116">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="241ca-117">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="241ca-117">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="241ca-118">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="241ca-118">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="241ca-119">“重新组织索引”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="241ca-119">Reorganize Index Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="241ca-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="241ca-120">Related Tasks</span></span>  
 <span data-ttu-id="241ca-121">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="241ca-121">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="241ca-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="241ca-122">See Also</span></span>  
 <span data-ttu-id="241ca-123">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="241ca-123">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="241ca-124">控制流</span><span class="sxs-lookup"><span data-stu-id="241ca-124">Control Flow</span></span>](control-flow.md)  
  
  
