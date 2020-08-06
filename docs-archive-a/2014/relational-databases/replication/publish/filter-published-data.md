---
title: 筛选已发布数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication]
- filters [SQL Server replication], about filtering
- filtering [SQL Server replication]
- static row filters
- transactional replication, filtering published data
- replication [SQL Server], filtering published data
- filtering published data [SQL Server replication]
- snapshot replication [SQL Server], filtering published data
- column filters [SQL Server replication]
ms.assetid: 8a914947-72dc-4119-b631-b39c8070c71b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525e90cecbc4cd6ee817b8fd07748abaf651b524
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578803"
---
# <a name="filter-published-data"></a><span data-ttu-id="e18e8-102">筛选已发布数据</span><span class="sxs-lookup"><span data-stu-id="e18e8-102">Filter Published Data</span></span>
  <span data-ttu-id="e18e8-103">通过筛选表项目，可以为要发布的数据创建分区。</span><span class="sxs-lookup"><span data-stu-id="e18e8-103">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="e18e8-104">通过筛选已发布数据，可以：</span><span class="sxs-lookup"><span data-stu-id="e18e8-104">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="e18e8-105">最大程度地减少通过网络发送的数据量。</span><span class="sxs-lookup"><span data-stu-id="e18e8-105">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="e18e8-106">减少订阅服务器上需要的存储空间量。</span><span class="sxs-lookup"><span data-stu-id="e18e8-106">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="e18e8-107">根据各个订阅服务器的要求，自定义发布和应用程序。</span><span class="sxs-lookup"><span data-stu-id="e18e8-107">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="e18e8-108">由于可以将不同的数据分区发送到不同的订阅服务器（没有两个订阅服务器会同时更新相同的数据值），因此可以避免或减少订阅服务器更新数据时的冲突。</span><span class="sxs-lookup"><span data-stu-id="e18e8-108">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="e18e8-109">避免传输敏感数据。</span><span class="sxs-lookup"><span data-stu-id="e18e8-109">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="e18e8-110">行筛选器和列筛选器可以用于限制订阅服务器对数据的访问。</span><span class="sxs-lookup"><span data-stu-id="e18e8-110">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="e18e8-111">对于合并复制，如果使用包括 HOST_NAME() 的参数化筛选器，则需要考虑安全问题。</span><span class="sxs-lookup"><span data-stu-id="e18e8-111">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="e18e8-112">有关详细信息，请参阅 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)中的“使用 HOST_NAME() 进行筛选”部分。</span><span class="sxs-lookup"><span data-stu-id="e18e8-112">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="e18e8-113">复制提供了四种筛选器：</span><span class="sxs-lookup"><span data-stu-id="e18e8-113">Replication offers four types of filters:</span></span>  
  
-   <span data-ttu-id="e18e8-114">静态行筛选器，适用于所有类型的复制。</span><span class="sxs-lookup"><span data-stu-id="e18e8-114">Static row filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="e18e8-115">使用静态行筛选器，可以选择要发布的行的子集。</span><span class="sxs-lookup"><span data-stu-id="e18e8-115">Using static row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="e18e8-116">已筛选发布的所有订阅服务器都接收已筛选表的相同的行子集。</span><span class="sxs-lookup"><span data-stu-id="e18e8-116">All Subscribers to a filtered publication receive the same subset of rows for the filtered table.</span></span> <span data-ttu-id="e18e8-117">有关详细信息，请参阅本主题中的“静态行筛选器”部分。</span><span class="sxs-lookup"><span data-stu-id="e18e8-117">For more information, see the section "Static Row Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="e18e8-118">列筛选器，适用于所有类型的复制。</span><span class="sxs-lookup"><span data-stu-id="e18e8-118">Column filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="e18e8-119">使用列筛选器，可以选择要发布的列的子集。</span><span class="sxs-lookup"><span data-stu-id="e18e8-119">Using column filters, you can choose a subset of columns to be published.</span></span> <span data-ttu-id="e18e8-120">有关详细信息，请参阅本主题中的“列筛选器”部分。</span><span class="sxs-lookup"><span data-stu-id="e18e8-120">For more information, see the section "Column Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="e18e8-121">参数化行筛选器，仅适用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="e18e8-121">Parameterized row filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="e18e8-122">使用参数化行筛选器，可以选择要发布的行的子集。</span><span class="sxs-lookup"><span data-stu-id="e18e8-122">Using parameterized row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="e18e8-123">与向所有订阅服务器发送相同行子集的静态筛选器不同，参数化行筛选器使用订阅服务器提供的数据值向订阅服务器发送不同的行子集。</span><span class="sxs-lookup"><span data-stu-id="e18e8-123">Unlike static filters that send the same subset of rows to every Subscriber, parameterized row filters use a data value supplied by the Subscriber to send Subscribers different subsets of rows.</span></span> <span data-ttu-id="e18e8-124">有关详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="e18e8-124">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="e18e8-125">联接筛选器，仅适用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="e18e8-125">Join filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="e18e8-126">使用联接筛选器，可以将行筛选器从一个已发布表扩展到另一个已发布表。</span><span class="sxs-lookup"><span data-stu-id="e18e8-126">Using join filters, you can extend a row filter from one published table to another.</span></span> <span data-ttu-id="e18e8-127">有关详细信息，请参阅 [Join Filters](../merge/join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="e18e8-127">For more information, see [Join Filters](../merge/join-filters.md).</span></span>  
  
## <a name="static-row-filters"></a><span data-ttu-id="e18e8-128">静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="e18e8-128">Static Row Filters</span></span>  
 <span data-ttu-id="e18e8-129">下图显示的已发布表已经过筛选，因此发布中只包括第 2、3、6 行。</span><span class="sxs-lookup"><span data-stu-id="e18e8-129">The following illustration shows a published table that is filtered so that only rows 2, 3, and 6 are included in the publication.</span></span>  
  
 <span data-ttu-id="e18e8-130">![行筛选](../media/repl-16.gif "行筛选")</span><span class="sxs-lookup"><span data-stu-id="e18e8-130">![Row filtering](../media/repl-16.gif "Row filtering")</span></span>  
  
 <span data-ttu-id="e18e8-131">静态行筛选器使用 WHERE 子句来选择要发布的相应数据，您需要指定 WHERE 子句的最后部分。</span><span class="sxs-lookup"><span data-stu-id="e18e8-131">A static row filter uses a WHERE clause to select the appropriate data to be published; you specify the final part of the WHERE clause.</span></span> <span data-ttu-id="e18e8-132">请考虑 Adventure Works 示例数据库中的 **Product 表** ，此表包含列 **ProductLine**。</span><span class="sxs-lookup"><span data-stu-id="e18e8-132">Consider the **Product Table** in the Adventure Works sample database, which contains the column **ProductLine**.</span></span> <span data-ttu-id="e18e8-133">若要只发布包含与山地车相关的产品数据的行，请指定 `ProductLine = 'M'`。</span><span class="sxs-lookup"><span data-stu-id="e18e8-133">To publish only the rows with data on products related to mountain bikes, specify `ProductLine = 'M'`.</span></span>  
  
 <span data-ttu-id="e18e8-134">静态行筛选器为每个发布生成一组数据。</span><span class="sxs-lookup"><span data-stu-id="e18e8-134">A static row filter results in a single set of data for each publication.</span></span> <span data-ttu-id="e18e8-135">在上面的示例中，所有订阅服务器只收到包含与山地车相关的产品数据的行。</span><span class="sxs-lookup"><span data-stu-id="e18e8-135">In the previous example, all Subscribers would receive only the rows with data on products related to mountain bikes.</span></span> <span data-ttu-id="e18e8-136">如果另一个订阅服务器只需要包含与公路自行车相关的产品数据的行：</span><span class="sxs-lookup"><span data-stu-id="e18e8-136">If you have another Subscriber that requires only the rows with data on products related to road bikes:</span></span>  
  
-   <span data-ttu-id="e18e8-137">对于快照复制或事务复制，可以再创建一个发布，在这两个发布中都包括该表（在该发布中的项目的筛选器子句中指定 `ProductLine = 'R')`）。</span><span class="sxs-lookup"><span data-stu-id="e18e8-137">With snapshot or transactional replication, you can create another publication and include the table in both publications (in the filter clause for the article in that publication, specify `ProductLine = 'R')`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e18e8-138">在事务发布中使用行筛选器会显著增加开销，因为对于为已发布表写入的每个日志行，都需要计算项目筛选器子句以确定是否要复制该行。</span><span class="sxs-lookup"><span data-stu-id="e18e8-138">Row filters in transactional publications can add significant overhead because the article filter clause is evaluated for each log row written for a published table, to determine whether the row should be replicated.</span></span> <span data-ttu-id="e18e8-139">如果每个复制节点都能支持全部数据负载，而且总体数据集相当小，则应避免在事务发布中使用行筛选器。</span><span class="sxs-lookup"><span data-stu-id="e18e8-139">Row filters in transactional publications should be avoided if each replication node can support the full data load, and the overall data set is reasonably small.</span></span>  
  
-   <span data-ttu-id="e18e8-140">对于合并复制，请使用参数化行筛选器，而不要使用静态行筛选器创建多个发布。</span><span class="sxs-lookup"><span data-stu-id="e18e8-140">With merge replication, use parameterized row filters rather than creating multiple publications with static row filters.</span></span> <span data-ttu-id="e18e8-141">有关详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="e18e8-141">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="e18e8-142">若要定义或修改静态行筛选器，请参阅 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="e18e8-142">To define or modify a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="e18e8-143">列筛选器</span><span class="sxs-lookup"><span data-stu-id="e18e8-143">Column Filters</span></span>  
 <span data-ttu-id="e18e8-144">下图显示了一个筛选出列 C 的发布。</span><span class="sxs-lookup"><span data-stu-id="e18e8-144">The following illustration shows a publication that filters out column C.</span></span>  
  
 <span data-ttu-id="e18e8-145">![列筛选](../media/repl-17.gif "列筛选")</span><span class="sxs-lookup"><span data-stu-id="e18e8-145">![Column filtering](../media/repl-17.gif "Column filtering")</span></span>  
  
 <span data-ttu-id="e18e8-146">还可以同时使用行筛选和列筛选，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="e18e8-146">You can also use row and column filtering together, as illustrated here.</span></span>  
  
 <span data-ttu-id="e18e8-147">![行筛选和列筛选](../media/repl-18.gif "行筛选和列筛选")</span><span class="sxs-lookup"><span data-stu-id="e18e8-147">![Row and column filtering](../media/repl-18.gif "Row and column filtering")</span></span>  
  
 <span data-ttu-id="e18e8-148">创建发布后，可以使用列筛选从现有发布中删除列，但在发布服务器中的表中保留该列，也可以在发布中包括现有列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-148">After a publication is created, you can use column filtering to drop a column from an existing publication, but retain the column in the table at the Publisher, and also to include an existing column in the publication.</span></span> <span data-ttu-id="e18e8-149">对于其他更改（如向表添加新列，然后再将其添加到已发布项目中），请使用架构更改复制。</span><span class="sxs-lookup"><span data-stu-id="e18e8-149">For other changes, such as adding a new column to a table and then adding it to the published article, use schema change replication.</span></span> <span data-ttu-id="e18e8-150">有关详细信息，请参阅[对发布数据库进行架构更改](make-schema-changes-on-publication-databases.md)主题中的“添加列”和“删除列”这两部分。</span><span class="sxs-lookup"><span data-stu-id="e18e8-150">For more information, see the "Adding Columns" and "Dropping Columns" sections in the topic [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="e18e8-151">下表列出的列类型不能从某些类型的发布中筛选出。</span><span class="sxs-lookup"><span data-stu-id="e18e8-151">The types of columns listed in the following table cannot be filtered out of certain types of publications.</span></span>  
  
|<span data-ttu-id="e18e8-152">列类型</span><span class="sxs-lookup"><span data-stu-id="e18e8-152">Column type</span></span>|<span data-ttu-id="e18e8-153">发布类型和选项</span><span class="sxs-lookup"><span data-stu-id="e18e8-153">Type of publication and options</span></span>|  
|-----------------|-------------------------------------|  
|<span data-ttu-id="e18e8-154">主键列</span><span class="sxs-lookup"><span data-stu-id="e18e8-154">Primary key column</span></span>|<span data-ttu-id="e18e8-155">主键列对于事务发布中的所有表都是必需的。</span><span class="sxs-lookup"><span data-stu-id="e18e8-155">Primary key columns are required for all tables in transactional publications.</span></span> <span data-ttu-id="e18e8-156">主键对于合并发布中的表并不是必需的，但如果存在主键列，则无法筛选该列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-156">Primary keys are not required for tables in merge publications, but if a primary key column is present, it cannot be filtered.</span></span>|  
|<span data-ttu-id="e18e8-157">外键列</span><span class="sxs-lookup"><span data-stu-id="e18e8-157">Foreign key column</span></span>|<span data-ttu-id="e18e8-158">使用新建发布向导创建的所有发布。</span><span class="sxs-lookup"><span data-stu-id="e18e8-158">All publications created using the New Publication wizard.</span></span> <span data-ttu-id="e18e8-159">可以使用 Transact-SQL 存储过程来筛选外键列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-159">You can filter foreign key columns using Transact-SQL stored procedures.</span></span> <span data-ttu-id="e18e8-160">有关详细信息，请参阅 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="e18e8-160">For more information, [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>|  
|<span data-ttu-id="e18e8-161">**rowguid** 列</span><span class="sxs-lookup"><span data-stu-id="e18e8-161">The **rowguid** column</span></span>|<span data-ttu-id="e18e8-162">合并发布<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e18e8-162">Merge publications<sup>1</sup></span></span>|  
|<span data-ttu-id="e18e8-163">**msrepl_tran_version** 列</span><span class="sxs-lookup"><span data-stu-id="e18e8-163">The **msrepl_tran_version** column</span></span>|<span data-ttu-id="e18e8-164">允许可更新订阅的快照或事务发布</span><span class="sxs-lookup"><span data-stu-id="e18e8-164">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="e18e8-165">不允许 NULL 且没有默认值或 IDENTITY 属性集的列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-165">Columns that do not allow NULL and do not have default values or the IDENTITY property set.</span></span>|<span data-ttu-id="e18e8-166">允许可更新订阅的快照或事务发布</span><span class="sxs-lookup"><span data-stu-id="e18e8-166">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="e18e8-167">具有唯一约束或索引的列</span><span class="sxs-lookup"><span data-stu-id="e18e8-167">Columns with unique constraints or indexes</span></span>|<span data-ttu-id="e18e8-168">允许可更新订阅的快照或事务发布</span><span class="sxs-lookup"><span data-stu-id="e18e8-168">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="e18e8-169">SQL Server 7.0 合并发布中的所有列</span><span class="sxs-lookup"><span data-stu-id="e18e8-169">All columns in a SQL Server 7.0 merge publication</span></span>|<span data-ttu-id="e18e8-170">SQL Server 7.0 合并发布中不能筛选的列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-170">Columns cannot be filtered in SQL Server 7.0 merge publications.</span></span>|  
|<span data-ttu-id="e18e8-171">时间戳</span><span class="sxs-lookup"><span data-stu-id="e18e8-171">Timestamp</span></span>|<span data-ttu-id="e18e8-172">允许可更新订阅的 SQL Server 7.0 快照或事务发布</span><span class="sxs-lookup"><span data-stu-id="e18e8-172">SQL Server 7.0 snapshot or transactional publications that allow updatable subscriptions</span></span>|  
  
 <span data-ttu-id="e18e8-173"><sup>1</sup>如果在合并发布中发布表，且该表已包含具有属性集的数据类型的列 `uniqueidentifier` ，则 `ROWGUIDCOL` 复制可以使用此列，而不是创建另一个名为**rowguid**的列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-173"><sup>1</sup> If you are publishing a table in a merge publication and that table already contains a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set, replication can use this column instead of creating an additional column named **rowguid**.</span></span> <span data-ttu-id="e18e8-174">在这种情况下，必须发布现有列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-174">In this case, the existing column must be published.</span></span>  
  
 <span data-ttu-id="e18e8-175">若要定义或修改列筛选器，请参阅 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)中的“使用 HOST_NAME() 进行筛选”部分。</span><span class="sxs-lookup"><span data-stu-id="e18e8-175">To define or modify a column filter, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
## <a name="filtering-considerations"></a><span data-ttu-id="e18e8-176">筛选注意事项</span><span class="sxs-lookup"><span data-stu-id="e18e8-176">Filtering Considerations</span></span>  
 <span data-ttu-id="e18e8-177">筛选数据时，请谨记下列注意事项：</span><span class="sxs-lookup"><span data-stu-id="e18e8-177">Keep the following considerations in mind when filtering data:</span></span>  
  
-   <span data-ttu-id="e18e8-178">行筛选器中引用的所有列必须都包括在发布中。</span><span class="sxs-lookup"><span data-stu-id="e18e8-178">All columns referenced in row filters must be included in the publication.</span></span> <span data-ttu-id="e18e8-179">也就是说，不能使用列筛选器排除行筛选器中使用的列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-179">In other words, you cannot use a column filter to exclude a column that is used in a row filter.</span></span>  
  
-   <span data-ttu-id="e18e8-180">如果在初始化订阅后添加或更改了筛选器，必须重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="e18e8-180">If a filter is added or changed after subscriptions have been initialized, the subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="e18e8-181">筛选器中使用的列所允许的最大字节数对于合并发布中的项目是 1024，对于事务发布中的项目是 8000。</span><span class="sxs-lookup"><span data-stu-id="e18e8-181">The maximum number of bytes allowed for a column used in a filter is 1024 for an article in a merge publication and 8000 for an article in a transactional publication.</span></span>  
  
-   <span data-ttu-id="e18e8-182">下列数据类型的列不能在行筛选器或联接筛选器中引用。</span><span class="sxs-lookup"><span data-stu-id="e18e8-182">Columns with the following data types cannot be referenced in row filters or join filters:</span></span>  
  
    -   `varchar(max) and nvarchar(max)`  
  
    -   `varbinary(max)`  
  
    -   `text and ntext`  
  
    -   `image`  
  
    -   `XML`  
  
    -   `UDT`  
  
-   <span data-ttu-id="e18e8-183">事务复制允许您将索引视图按视图或表来复制。</span><span class="sxs-lookup"><span data-stu-id="e18e8-183">Transactional replication allows you to replicate an indexed view as a view or as a table.</span></span> <span data-ttu-id="e18e8-184">如果将视图按表复制，则无法从表中筛选列。</span><span class="sxs-lookup"><span data-stu-id="e18e8-184">If you replicate the view as a table, you cannot filter columns from the table.</span></span>  
  
 <span data-ttu-id="e18e8-185">行筛选器未设计为跨数据库工作。</span><span class="sxs-lookup"><span data-stu-id="e18e8-185">Row filters are not designed to work across databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e18e8-186">有意将 `sp_replcmds` 的执行（执行筛选器）限制为数据库所有者 (`dbo`)。</span><span class="sxs-lookup"><span data-stu-id="e18e8-186">intentionally restricts the execution of `sp_replcmds` (which filters execute under) to the database owner (`dbo`).</span></span> <span data-ttu-id="e18e8-187">`dbo` 不具有跨数据库权限。</span><span class="sxs-lookup"><span data-stu-id="e18e8-187">The `dbo` does not have cross database privileges.</span></span> <span data-ttu-id="e18e8-188">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 中增加 CDC（变更数据捕获）后，`sp_replcmds` 逻辑将使用用户可以返回到和查询的信息填充变更跟踪表。</span><span class="sxs-lookup"><span data-stu-id="e18e8-188">With the addition of CDC (Change Data Capture) in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] the `sp_replcmds` logic populates the change tracking tables with information that the user can return to and query.</span></span> <span data-ttu-id="e18e8-189">出于安全原因， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 会限制此逻辑的执行，使恶意 `dbo` 不能劫持此执行路径。</span><span class="sxs-lookup"><span data-stu-id="e18e8-189">For security reasons, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restricts the execution of this logic so that a malicious `dbo` can't highjack this execution path.</span></span> <span data-ttu-id="e18e8-190">例如，恶意的 `dbo` 可能在 CDC 表上添加触发器，然后这些触发器会在调用 `sp_replcmds` 的用户（在这种情况下为日志读取器代理）的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="e18e8-190">For example, a malicious `dbo` could add triggers on CDC tables which would then get executed under the context of the user calling `sp_replcmds`, in this case the logreader agent.</span></span>  <span data-ttu-id="e18e8-191">如果运行该代理所用的帐户具有更高权限，则恶意的 `dbo` 可以提升其权限。</span><span class="sxs-lookup"><span data-stu-id="e18e8-191">If the account the agent is running under has higher privilege the malicious `dbo` could escalate his privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18e8-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e18e8-192">See Also</span></span>  
 [<span data-ttu-id="e18e8-193">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="e18e8-193">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
