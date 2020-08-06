---
title: 定义和修改静态行筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying filters, static row
- static row filters
- filters [SQL Server replication], static row
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d13fd93b6afdcce6b55e9b181f52087fd620913c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578811"
---
# <a name="define-and-modify-a-static-row-filter"></a><span data-ttu-id="aa4c9-102">定义和修改静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-102">Define and Modify a Static Row Filter</span></span>
  <span data-ttu-id="aa4c9-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定义和修改静态行筛选器。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-103">This topic describes how to define and modify a static row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="aa4c9-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="aa4c9-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="aa4c9-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa4c9-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="aa4c9-107">建议</span><span class="sxs-lookup"><span data-stu-id="aa4c9-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="aa4c9-108">**定义和修改静态行筛选器，使用：**</span><span class="sxs-lookup"><span data-stu-id="aa4c9-108">**To define and modify a static row filter, using:**</span></span>  
  
     [<span data-ttu-id="aa4c9-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa4c9-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="aa4c9-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aa4c9-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aa4c9-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="aa4c9-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="aa4c9-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa4c9-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="aa4c9-113">如果在初始化对发布的订阅后添加、修改或删除静态行筛选器，则必须在更改后生成新的快照并重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-113">If you add, modify, or delete a static row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="aa4c9-114">有关属性更改要求的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
-   <span data-ttu-id="aa4c9-115">如果为对等事务复制启用了发布，则不能筛选表。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-115">If the publication is enabled for peer-to-peer transactional replication, tables cannot be filtered.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="aa4c9-116">建议</span><span class="sxs-lookup"><span data-stu-id="aa4c9-116">Recommendations</span></span>  
  
-   <span data-ttu-id="aa4c9-117">由于这些筛选器是静态的，因此所有订阅服务器都将接收到相同的数据子集。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-117">Because these filters are static, all subscribers will receive the same subset of the data.</span></span> <span data-ttu-id="aa4c9-118">如果您需要在属于合并发布的表项目中动态筛选行，以使每一订阅服务器都能接收到不同的数据分区，请参阅 [定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-118">If you need to dynamically filter rows in a table article belonging to a merge publication so that each subscriber receives a different partition of the data, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span> <span data-ttu-id="aa4c9-119">您还可使用合并复制基于现有的行筛选器筛选相关的行。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-119">Merge replication also enables you to filter related rows based on an existing row filter.</span></span> <span data-ttu-id="aa4c9-120">有关详细信息，请参阅 [定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-120">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="aa4c9-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa4c9-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="aa4c9-122">可在“新建发”布向导的“筛选表行”页面或者在“发布属性 - \<Publication>”对话框的“筛选行”页面上定义、修改和删除静态行筛选器  。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-122">Define, modify, and delete static row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="aa4c9-123">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter"></a><span data-ttu-id="aa4c9-124">定义静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-124">To define a static row filter</span></span>  
  
1.  <span data-ttu-id="aa4c9-125">在“新建发布”导的“筛选表行”页面上或者在“发布属性 - \<Publication>”对话框的“筛选行”页面上，发布类型决定了你执行的操作  ：</span><span class="sxs-lookup"><span data-stu-id="aa4c9-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, the action you take depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="aa4c9-126">对于快照发布或事务发布，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-126">For a snapshot or transactional publication, click **Add**.</span></span>  
  
    -   <span data-ttu-id="aa4c9-127">对于合并发布，请单击 **“添加”** ，再单击 **“添加筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-127">For a merge publication, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="aa4c9-128">在 **“添加筛选器”** 对话框中，从下拉列表框中选择要筛选的表。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-128">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="aa4c9-129">在 **“筛选语句”** 文本区域创建筛选语句。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-129">Create a filter statement in the **Filter statement** text area.</span></span> <span data-ttu-id="aa4c9-130">您可以在文本区域中直接键入，也可以从 **“列”** 列表框中拖放列。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-130">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aa4c9-131">WHERE 子句应使用由两部分构成的命名方式，不支持由三部分和四部分构成的命名方式。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-131">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span> <span data-ttu-id="aa4c9-132">如果发布来自 Oracle 发布服务器，则 WHERE 子句必须符合 Oracle 语法。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-132">If the publication is from an Oracle Publisher, the WHERE clause must be compliant with Oracle syntax.</span></span>  
  
    -   <span data-ttu-id="aa4c9-133">**“筛选语句”** 文本区域包括默认的文本，其格式为：</span><span class="sxs-lookup"><span data-stu-id="aa4c9-133">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="aa4c9-134">默认文本无法更改；请使用标准的 SQL 语法在 WHERE 关键字后键入筛选子句。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-134">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="aa4c9-135">完整筛选子句如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa4c9-135">The complete filter clause would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   <span data-ttu-id="aa4c9-136">静态行筛选器可以包含用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-136">A static row filter can include a user-defined function.</span></span> <span data-ttu-id="aa4c9-137">包含用户定义函数的静态行筛选器的完整筛选子句如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa4c9-137">The complete filter clause for a static row filter with a user-defined function would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="aa4c9-138">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-138">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-static-row-filter"></a><span data-ttu-id="aa4c9-139">修改静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-139">To modify a static row filter</span></span>  
  
1.  <span data-ttu-id="aa4c9-140">在“新建发布”向导的“筛选表行”页面上或者在“发布属性 - \<Publication>”对话框的“筛选行”页面上，在“筛选的表”窗格中选择一个筛选器，然后单击“编辑”    。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="aa4c9-141">在 **“编辑筛选器”** 对话框中，修改筛选器。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-141">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-static-row-filter"></a><span data-ttu-id="aa4c9-142">删除静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-142">To delete a static row filter</span></span>  
  
1.  <span data-ttu-id="aa4c9-143">在“新建发布”向导的“筛选表行”页面上或者在“发布属性 - \<Publication>”对话框的“筛选行”页面上，在“筛选的表”窗格中选择一个筛选器，然后单击“删除”    。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-143">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="aa4c9-144">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aa4c9-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="aa4c9-145">在创建表项目时，可以定义 WHERE 子句以筛选项目中的行。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-145">When creating table articles, you can define a WHERE clause to filter rows out of an article.</span></span> <span data-ttu-id="aa4c9-146">定义行筛选器后，还可以对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-146">You can also change a row filter after it has been defined.</span></span> <span data-ttu-id="aa4c9-147">可使用复制存储过程以编程的方式创建和修改静态行筛选器。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-147">Static row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="aa4c9-148">为快照发布或事务发布定义静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-148">To define a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="aa4c9-149">定义要筛选的项目。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-149">Define the article to filter.</span></span> <span data-ttu-id="aa4c9-150">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-150">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="aa4c9-151">在发布服务器上，对发布数据库执行 [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-151">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="aa4c9-152">为 \@article 指定项目的名称，为 \@publication 指定发布的名称，为 \@filter_name 指定筛选器的名称，并为 \@filter_clause 指定筛选子句（不包括 `WHERE`）   。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-152">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the filter for **\@filter_name**, and the filtering clause for **\@filter_clause** (not including `WHERE`).</span></span>  
  
3.  <span data-ttu-id="aa4c9-153">如果还必须定义列筛选器，请参阅 [定义和修改列筛选器](define-and-modify-a-column-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-153">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span> <span data-ttu-id="aa4c9-154">否则，执行 [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-154">Otherwise, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="aa4c9-155">为 \@publication 指定发布名称，为 \@article 指定筛选项目的名称，为 \@filter_clause 指定步骤 2 中指定的筛选子句  。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-155">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 2 for **\@filter_clause**.</span></span> <span data-ttu-id="aa4c9-156">这将为筛选的项目创建同步对象。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-156">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="aa4c9-157">为快照发布或事务发布修改静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-157">To modify a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="aa4c9-158">在发布服务器上，对发布数据库执行 [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-158">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="aa4c9-159">为 \@article 指定项目的名称，为 \@publication 指定发布的名称，为 \@filter_name 指定新筛选器的名称，并为 \@filter_clause 指定新筛选子句（不包括 `WHERE`）   。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-159">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the new filter for **\@filter_name**, and the new filtering clause for **\@filter_clause** (not including `WHERE`).</span></span> <span data-ttu-id="aa4c9-160">由于此更改将使现有订阅中的数据失效，因此请将 \@force_reinit_subscription 的值指定为 1 。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-160">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="aa4c9-161">在发布服务器上，对发布数据库执行 [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-161">At the Publisher on the publication database, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="aa4c9-162">为 \@publication 指定发布名称，为 \@article 指定筛选项目的名称，为 \@filter_clause 指定步骤 1 中指定的筛选子句  。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-162">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 1 for **\@filter_clause**.</span></span> <span data-ttu-id="aa4c9-163">这将重新创建定义筛选项目的视图。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-163">This re-creates the view that defines the filtered article.</span></span>  
  
3.  <span data-ttu-id="aa4c9-164">对发布重新运行快照代理作业以生成更新的快照。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-164">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="aa4c9-165">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-165">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
4.  <span data-ttu-id="aa4c9-166">重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-166">Reinitialize subscriptions.</span></span> <span data-ttu-id="aa4c9-167">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-167">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-delete-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="aa4c9-168">为快照发布或事务发布删除静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-168">To delete a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="aa4c9-169">在发布服务器上，对发布数据库执行 [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-169">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="aa4c9-170">为 \@article 指定项目的名称，为 \@publication 指定发布的名称，将 \@filter_name 的值指定为 NULL，并将 \@filter_clause 的值指定为 NULL   。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-170">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a value of NULL for **\@filter_name**, and a value of NULL for **\@filter_clause**.</span></span> <span data-ttu-id="aa4c9-171">由于此更改将使现有订阅中的数据失效，因此请将 \@force_reinit_subscription 的值指定为 1 。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-171">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="aa4c9-172">对发布重新运行快照代理作业以生成更新的快照。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-172">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="aa4c9-173">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-173">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="aa4c9-174">重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-174">Reinitialize subscriptions.</span></span> <span data-ttu-id="aa4c9-175">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-175">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="aa4c9-176">为合并发布定义静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-176">To define a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="aa4c9-177">在发布服务器上，对发布数据库执行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-177">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="aa4c9-178">为 \@subset_filterclause 指定筛选子句（不包括 `WHERE`）。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-178">Specify the filtering clause for **\@subset_filterclause** (not including `WHERE`).</span></span> <span data-ttu-id="aa4c9-179">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-179">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="aa4c9-180">如果还必须定义列筛选器，请参阅 [定义和修改列筛选器](define-and-modify-a-column-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-180">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="aa4c9-181">为合并发布修改静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="aa4c9-181">To modify a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="aa4c9-182">在发布服务器上，对发布数据库执行 [sp_changemergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-182">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="aa4c9-183">为 \@publication 指定发布名称，为 \@article 指定筛选项目的名称，为 \@property 指定 subset_filterclause 值，并为 \@value 指定新筛选子句（不包括 `WHERE`）    。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-183">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, a value of **subset_filterclause** for **\@property**, and the new filtering clause for **\@value** (not including `WHERE`).</span></span> <span data-ttu-id="aa4c9-184">由于此更改将使现有订阅中的数据失效，因此请将 \@force_reinit_subscription 的值指定为 1。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-184">Because this change will invalidate data in existing subscriptions, specify a value of 1 for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="aa4c9-185">对发布重新运行快照代理作业以生成更新的快照。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-185">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="aa4c9-186">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-186">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="aa4c9-187">重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-187">Reinitialize subscriptions.</span></span> <span data-ttu-id="aa4c9-188">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-188">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="aa4c9-189">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="aa4c9-189">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="aa4c9-190">在此事务复制示例中，对项目进行水平筛选以删除所有停产的产品。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-190">In this transactional replication example, the article is filtered horizontally to remove all discontinued products.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="aa4c9-191">在此合并复制示例中，对项目进行水平筛选以仅返回属于指定销售人员的行。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-191">In this merge replication example, the articles are filtered horizontally to return only rows that belong to the specified salesperson.</span></span> <span data-ttu-id="aa4c9-192">其中还使用了联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-192">A join filter is also used.</span></span> <span data-ttu-id="aa4c9-193">有关详细信息，请参阅 [定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="aa4c9-193">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="aa4c9-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa4c9-194">See Also</span></span>  
 <span data-ttu-id="aa4c9-195">[定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="aa4c9-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="aa4c9-196">[更改发布和项目属性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="aa4c9-196">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="aa4c9-197">[筛选已发布数据](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="aa4c9-197">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="aa4c9-198">为合并复制筛选已发布数据</span><span class="sxs-lookup"><span data-stu-id="aa4c9-198">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
