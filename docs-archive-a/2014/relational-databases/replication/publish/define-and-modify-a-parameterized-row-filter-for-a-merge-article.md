---
title: 定义和修改合并项目的参数化行筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], defining
- parameterized filters [SQL Server replication], modifying
- merge replication [SQL Server replication], dynamic filters
- merge replication parameterized filters [SQL Server replication]
- filters [SQL Server replication], parameterized
- modifying filters, parameterized row
- dynamic filters [SQL Server replication]
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d80ad53661aced22795220507398e2fcc510edd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691657"
---
# <a name="define-and-modify-a-parameterized-row-filter-for-a-merge-article"></a><span data-ttu-id="d98fe-102">定义和修改合并项目的参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="d98fe-102">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>
  <span data-ttu-id="d98fe-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定义和修改参数化行筛选器。</span><span class="sxs-lookup"><span data-stu-id="d98fe-103">This topic describes how to define and modify a parameterized row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d98fe-104">在创建表项目时，可以使用参数化行筛选器。</span><span class="sxs-lookup"><span data-stu-id="d98fe-104">When creating table articles, you can use parameterized row filters.</span></span> <span data-ttu-id="d98fe-105">这些筛选器使用 [WHERE](/sql/t-sql/queries/where-transact-sql) 子句来选择要发布的相应数据。</span><span class="sxs-lookup"><span data-stu-id="d98fe-105">These filters use a [WHERE](/sql/t-sql/queries/where-transact-sql) clause to select the appropriate data to be published.</span></span> <span data-ttu-id="d98fe-106">请勿在子句中指定文本值（像用静态行筛选器处理那样），而是指定以下一个或两个系统函数：[SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) 和 [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="d98fe-106">Rather than specifying a literal value in the clause (as you do with a static row filter), you specify one or both of the following system functions: [SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) and [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql).</span></span> <span data-ttu-id="d98fe-107">有关详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="d98fe-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d98fe-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="d98fe-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d98fe-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d98fe-109">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d98fe-110">如果在初始化对发布的订阅后添加、修改或删除参数化行筛选器，必须在更改后生成新的快照并重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="d98fe-110">If you add, modify, or delete a parameterized row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="d98fe-111">有关属性更改要求的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d98fe-111">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d98fe-112">建议</span><span class="sxs-lookup"><span data-stu-id="d98fe-112">Recommendations</span></span>  
  
-   <span data-ttu-id="d98fe-113">出于性能方面的考虑，我们建议您不要将这些函数应用于参数化行筛选器子句（如 `LEFT([MyColumn]) = SUSER_SNAME()`）中的列名。</span><span class="sxs-lookup"><span data-stu-id="d98fe-113">For performance reasons, we recommend that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="d98fe-114">如果在筛选子句中使用 HOST_NAME 并覆盖 HOST_NAME 值，则可能需要使用 CONVERT 转换数据类型。</span><span class="sxs-lookup"><span data-stu-id="d98fe-114">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="d98fe-115">有关此情况的最佳实践的详细信息，请参阅主题 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)中的“覆盖 HOST_NAME() 值”一节。</span><span class="sxs-lookup"><span data-stu-id="d98fe-115">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d98fe-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d98fe-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d98fe-117">可在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”对话框的“筛选行”页上定义、修改和删除参数化行筛选器。</span><span class="sxs-lookup"><span data-stu-id="d98fe-117">Define, modify, and delete parameterized row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="d98fe-118">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d98fe-118">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter"></a><span data-ttu-id="d98fe-119">定义参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="d98fe-119">To define a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="d98fe-120">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，单击“添加”，然后单击“添加筛选器”。</span><span class="sxs-lookup"><span data-stu-id="d98fe-120">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="d98fe-121">在 **“添加筛选器”** 对话框中，从下拉列表框中选择要筛选的表。</span><span class="sxs-lookup"><span data-stu-id="d98fe-121">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="d98fe-122">在 **“筛选语句”** 文本框中创建一个筛选语句。</span><span class="sxs-lookup"><span data-stu-id="d98fe-122">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="d98fe-123">您可以在文本区域中直接键入，也可以从 **“列”** 列表框中拖放列。</span><span class="sxs-lookup"><span data-stu-id="d98fe-123">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    -   <span data-ttu-id="d98fe-124">**“筛选语句”** 文本区域包括默认的文本，其格式为：</span><span class="sxs-lookup"><span data-stu-id="d98fe-124">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="d98fe-125">默认文本无法更改；请使用标准的 SQL 语法在 WHERE 关键字后键入筛选子句。</span><span class="sxs-lookup"><span data-stu-id="d98fe-125">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="d98fe-126">参数化筛选器包括对系统函数 `HOST_NAME()` 和/或 `SUSER_SNAME()` 的调用，或者对引用这两个函数之一或全部的用户定义函数的调用。</span><span class="sxs-lookup"><span data-stu-id="d98fe-126">A parameterized filter includes a call to the system function `HOST_NAME()` and/or `SUSER_SNAME()`, or a user-defined function that references one or both of these functions.</span></span> <span data-ttu-id="d98fe-127">以下是参数化行筛选器的一个完整筛选子句的示例：</span><span class="sxs-lookup"><span data-stu-id="d98fe-127">The following is an example of a complete filter clause for a parameterized row filter:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="d98fe-128">WHERE 子句应使用由两部分构成的命名方式，不支持由三部分和四部分构成的命名方式。</span><span class="sxs-lookup"><span data-stu-id="d98fe-128">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="d98fe-129">选择指示订阅服务器之间如何共享数据的选项：</span><span class="sxs-lookup"><span data-stu-id="d98fe-129">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="d98fe-130">**此表中的行将转到多个订阅**</span><span class="sxs-lookup"><span data-stu-id="d98fe-130">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="d98fe-131">**此表中的行将仅转到一个订阅**</span><span class="sxs-lookup"><span data-stu-id="d98fe-131">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="d98fe-132">如果选择 **“此表中的行将仅转到一个订阅”** ，则合并复制可以通过存储和处理较少的元数据来优化性能。</span><span class="sxs-lookup"><span data-stu-id="d98fe-132">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="d98fe-133">但是，必须确保在对数据分区时不能将行复制到多个订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="d98fe-133">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="d98fe-134">有关详细信息，请参阅主题 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)中的“设置‘分区选项’”部分。</span><span class="sxs-lookup"><span data-stu-id="d98fe-134">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="d98fe-135">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="d98fe-135">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-parameterized-row-filter"></a><span data-ttu-id="d98fe-136">修改参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="d98fe-136">To modify a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="d98fe-137">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，在“筛选的表”窗格中选择筛选器，然后单击“编辑”。    </span><span class="sxs-lookup"><span data-stu-id="d98fe-137">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="d98fe-138">在 **“编辑筛选器”** 对话框中，修改筛选器。</span><span class="sxs-lookup"><span data-stu-id="d98fe-138">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-parameterized-row-filter"></a><span data-ttu-id="d98fe-139">删除参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="d98fe-139">To delete a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="d98fe-140">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，在“筛选的表”窗格中选择筛选器，然后单击“删除”。    </span><span class="sxs-lookup"><span data-stu-id="d98fe-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d98fe-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d98fe-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="d98fe-142">可以使用复制存储过程以编程方式创建和修改参数化行筛选器。</span><span class="sxs-lookup"><span data-stu-id="d98fe-142">Parameterized row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="d98fe-143">为合并发布中的项目定义参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="d98fe-143">To define a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="d98fe-144">在发布服务器上，对发布数据库执行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d98fe-144">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="d98fe-145">指定 **@publication** 、要为其发布的表的名称、为其 **@article** **@source_object** 定义参数化筛选器的 WHERE 子句 **@subset_filterclause** (不包括 `WHERE`) ，以及以下值之一 **@partition_options** ，其中描述了参数化行筛选器将生成的分区类型：</span><span class="sxs-lookup"><span data-stu-id="d98fe-145">Specify **@publication**, a name for the article for **@article**, the table being published for **@source_object**, the WHERE clause that defines the parameterized filter for **@subset_filterclause** (not including `WHERE`), and one of the following values for **@partition_options**, which describes the type of partitioning that will result from the parameterized row filter:</span></span>  
  
    -   <span data-ttu-id="d98fe-146">**0** - 对项目的筛选是静态的，或者不为每个分区生成唯一的数据子集（“重叠”分区）。</span><span class="sxs-lookup"><span data-stu-id="d98fe-146">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="d98fe-147">**1** - 导致分区重叠，并且在订阅服务器上所做的更新不能更改行所属的分区。</span><span class="sxs-lookup"><span data-stu-id="d98fe-147">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="d98fe-148">**2** - 对项目的筛选将生成不重叠分区，但多个订阅服务器可以接收相同的分区。</span><span class="sxs-lookup"><span data-stu-id="d98fe-148">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="d98fe-149">**3** - 对项目的筛选将为每个订阅生成唯一的不重叠分区。</span><span class="sxs-lookup"><span data-stu-id="d98fe-149">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
#### <a name="to-change-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="d98fe-150">更改合并发布中的项目的参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="d98fe-150">To change a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="d98fe-151">在发布服务器上，对发布数据库执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d98fe-151">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="d98fe-152">为指定，并为指定的值，将 **@publication** **@article** `subset_filterclause` **@property** 定义参数化筛选器 **@value** (不包含 `WHERE`) ，并将值**1**指定给 **@force_invalidate_snapshot** 和 **@force_reinit_subscription** 。</span><span class="sxs-lookup"><span data-stu-id="d98fe-152">Specify **@publication**, **@article**, a value of `subset_filterclause` for **@property**, the expression that defines the parameterized filter for **@value** (not including `WHERE`), and a value of **1** for both **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="d98fe-153">如果此更改导致不同的分区行为，则再次执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="d98fe-153">If this change results in different partitioning behavior, then execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="d98fe-154">指定 **@publication** 、 **@article** 、的值以及 `partition_options` **@property** 最适合的分区选项 **@value** ，可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="d98fe-154">Specify **@publication**, **@article**, a value of `partition_options` for **@property**, and the most appropriate partitioning option for **@value**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="d98fe-155">**0** - 对项目的筛选是静态的，或者不为每个分区生成唯一的数据子集（“重叠”分区）。</span><span class="sxs-lookup"><span data-stu-id="d98fe-155">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="d98fe-156">**1** - 导致分区重叠，并且在订阅服务器上所做的更新不能更改行所属的分区。</span><span class="sxs-lookup"><span data-stu-id="d98fe-156">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="d98fe-157">**2** - 对项目的筛选将生成不重叠分区，但多个订阅服务器可以接收相同的分区。</span><span class="sxs-lookup"><span data-stu-id="d98fe-157">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="d98fe-158">**3** - 对项目的筛选将为每个订阅生成唯一的不重叠分区。</span><span class="sxs-lookup"><span data-stu-id="d98fe-158">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="d98fe-159">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d98fe-159">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="d98fe-160">此示例在合并发布中定义一组项目，其中的项目是使用一系列联接筛选器基于 `Employee` 表筛选的，而该表则是使用参数化行筛选器基于 **LoginID** 列进行自身筛选的。</span><span class="sxs-lookup"><span data-stu-id="d98fe-160">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the **LoginID** column.</span></span> <span data-ttu-id="d98fe-161">在同步期间，由 [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) 函数返回的值将被覆盖。</span><span class="sxs-lookup"><span data-stu-id="d98fe-161">During synchronization, the value returned by the [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) function is overridden.</span></span> <span data-ttu-id="d98fe-162">有关详细信息，请参阅主题 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)中的“覆盖 HOST_NAME() 值”。</span><span class="sxs-lookup"><span data-stu-id="d98fe-162">For more information, see Overriding the HOST_NAME() Value in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
  
## <a name="see-also"></a><span data-ttu-id="d98fe-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d98fe-163">See Also</span></span>  
 <span data-ttu-id="d98fe-164">[定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="d98fe-164">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="d98fe-165">[更改发布和项目属性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d98fe-165">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="d98fe-166">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="d98fe-166">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="d98fe-167">参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="d98fe-167">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
