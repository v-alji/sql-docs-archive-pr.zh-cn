---
title: 使用非聚集列存储索引 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c876eb6fdd466349ac369dcff8e292bc0839c669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689575"
---
# <a name="using-nonclustered-columnstore-indexes"></a><span data-ttu-id="4d821-102">使用非聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="4d821-102">Using Nonclustered Columnstore Indexes</span></span>
  <span data-ttu-id="4d821-103">描述用于在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表上使用非聚集列存储索引的主要任务。</span><span class="sxs-lookup"><span data-stu-id="4d821-103">Describes key tasks for using a nonclustered columnstore index on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="4d821-104">有关列存储索引的概述，请参阅 [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md)。</span><span class="sxs-lookup"><span data-stu-id="4d821-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="4d821-105">有关聚集列存储索引的信息，请参阅 [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="4d821-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="4d821-106">目录</span><span class="sxs-lookup"><span data-stu-id="4d821-106">Contents</span></span>

-   [<span data-ttu-id="4d821-107">创建非聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="4d821-107">Create a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)

-   [<span data-ttu-id="4d821-108">更改非聚集列存储索引中的数据</span><span class="sxs-lookup"><span data-stu-id="4d821-108">Change the Data in a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)

##  <a name="create-a-nonclustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="4d821-109">创建非聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="4d821-109">Create a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="4d821-110">若要将数据加载到非聚集列存储索引中，请首先将数据加载到作为堆或聚集索引存储的传统行存储表中，然后使用[CREATE 列存储索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)创建列存储索引。</span><span class="sxs-lookup"><span data-stu-id="4d821-110">To load data into a nonclustered columnstore index, first load data into a traditional rowstore table stored as a heap or clustered index, and then use [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) to create a columnstore index.</span></span>

 <span data-ttu-id="4d821-111">![将数据加载到列存储索引中](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "将数据加载到列存储索引中")</span><span class="sxs-lookup"><span data-stu-id="4d821-111">![Loading data into a columnstore index](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Loading data into a columnstore index")</span></span>

##  <a name="change-the-data-in-a-nonclustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="4d821-112">更改非聚集列存储索引中的数据</span><span class="sxs-lookup"><span data-stu-id="4d821-112">Change the Data in a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="4d821-113">在您在表上创建非聚集列存储索引后，不能直接在该表中修改数据。</span><span class="sxs-lookup"><span data-stu-id="4d821-113">Once you create a nonclustered columnstore index on a table, you cannot directly modify the data in that table.</span></span> <span data-ttu-id="4d821-114">具有 INSERT、UPDATE、DELETE 或 MERGE 的查询将失败并且返回错误消息。</span><span class="sxs-lookup"><span data-stu-id="4d821-114">A query with INSERT, UPDATE, DELETE, or MERGE will fail and return an error message.</span></span> <span data-ttu-id="4d821-115">若要添加或修改表中的数据，可以执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="4d821-115">To add or modify the data in the table, you can do one of the following:</span></span>

-   <span data-ttu-id="4d821-116">禁用列存储索引。</span><span class="sxs-lookup"><span data-stu-id="4d821-116">Disable the columnstore index.</span></span> <span data-ttu-id="4d821-117">然后可以更新表中的数据。</span><span class="sxs-lookup"><span data-stu-id="4d821-117">You can then update the data in the table.</span></span> <span data-ttu-id="4d821-118">如果禁用列存储索引，则可以在完成数据更新后重新生成列存储索引。</span><span class="sxs-lookup"><span data-stu-id="4d821-118">If you disable the columnstore index, you can rebuild the columnstore index when you finish updating the data.</span></span> <span data-ttu-id="4d821-119">例如：</span><span class="sxs-lookup"><span data-stu-id="4d821-119">For example:</span></span>

    ```
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;
    -- update mytable --
    ALTER INDEX mycolumnstoreindex on mytable REBUILD
    ```

-   <span data-ttu-id="4d821-120">删除列存储索引，更新表，然后重新创建包含 CREATE 列存储索引的列存储索引。</span><span class="sxs-lookup"><span data-stu-id="4d821-120">Drop the columnstore index, update the table, and then re-create the columnstore index with CREATE COLUMNSTORE INDEX.</span></span> <span data-ttu-id="4d821-121">例如：</span><span class="sxs-lookup"><span data-stu-id="4d821-121">For example:</span></span>

    ```
    DROP INDEX mycolumnstoreindex ON mytable
    -- update mytable --
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;

    ```

-   <span data-ttu-id="4d821-122">将数据加载到不含列存储索引的临时表中。</span><span class="sxs-lookup"><span data-stu-id="4d821-122">Load data into a staging table that does not have a columnstore index.</span></span> <span data-ttu-id="4d821-123">在临时表上生成列存储索引。</span><span class="sxs-lookup"><span data-stu-id="4d821-123">Build a columnstore index on the staging table.</span></span> <span data-ttu-id="4d821-124">将临时表切换到主表的一个空分区中。</span><span class="sxs-lookup"><span data-stu-id="4d821-124">Switch the staging table into an empty partition of the main table.</span></span>

-   <span data-ttu-id="4d821-125">将分区从具有列存储索引的表切换到一个空的临时表中。</span><span class="sxs-lookup"><span data-stu-id="4d821-125">Switch a partition from the table with the columnstore index into an empty staging table.</span></span> <span data-ttu-id="4d821-126">如果在临时表上有某个列存储索引，则禁用该列存储索引。</span><span class="sxs-lookup"><span data-stu-id="4d821-126">If there is a columnstore index on the staging table, disable the columnstore index.</span></span> <span data-ttu-id="4d821-127">执行任何更新。</span><span class="sxs-lookup"><span data-stu-id="4d821-127">Perform any updates.</span></span> <span data-ttu-id="4d821-128">生成（或重新生成）列存储索引。</span><span class="sxs-lookup"><span data-stu-id="4d821-128">Build (or rebuild) the columnstore index.</span></span> <span data-ttu-id="4d821-129">将临时表切换回主表的（现在为空的）分区中。</span><span class="sxs-lookup"><span data-stu-id="4d821-129">Switch the staging table back into the (now empty) partition of the main table.</span></span>




