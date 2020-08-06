---
title: 定义和修改合并项目间的联接筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- merge replication join filters [SQL Server replication]
- modifying filters, join
- join filters
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0770a17ce4c50c9c0e3b8728db85c0f9e80b555b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591253"
---
# <a name="define-and-modify-a-join-filter-between-merge-articles"></a><span data-ttu-id="822f2-102">定义和修改合并项目间的联接筛选器</span><span class="sxs-lookup"><span data-stu-id="822f2-102">Define and Modify a Join Filter Between Merge Articles</span></span>
  <span data-ttu-id="822f2-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定义和修改合并项目间的联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="822f2-103">This topic describes how to define and modify a join filter between merge articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="822f2-104">合并复制支持联接筛选器，这类筛选器通常与参数化筛选器配合使用，以将表分区扩展到其他相关的表项目。</span><span class="sxs-lookup"><span data-stu-id="822f2-104">Merge replication supports join filters, which are typically used in conjunction with parameterized filters to extend table partitioning to other related table articles.</span></span>  
  
 <span data-ttu-id="822f2-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="822f2-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="822f2-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="822f2-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="822f2-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="822f2-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="822f2-108">建议</span><span class="sxs-lookup"><span data-stu-id="822f2-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="822f2-109">**定义和修改合并项目间的联接筛选器，使用：**</span><span class="sxs-lookup"><span data-stu-id="822f2-109">**To define and modify a join filter between merge articles, using:**</span></span>  
  
     [<span data-ttu-id="822f2-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="822f2-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="822f2-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="822f2-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="822f2-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="822f2-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="822f2-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="822f2-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="822f2-114">若要创建联接筛选器，发布必须至少包含两个相关表。</span><span class="sxs-lookup"><span data-stu-id="822f2-114">To create a join filter, a publication must contain at least two related tables.</span></span> <span data-ttu-id="822f2-115">联接筛选器可扩展行筛选器；因此必须先对一个表定义行筛选器，才能使用联接将该筛选器扩展到另一个表。</span><span class="sxs-lookup"><span data-stu-id="822f2-115">A join filter extends a row filter; therefore you must define a row filter on one table before you can extend the filter with a join to another table.</span></span> <span data-ttu-id="822f2-116">定义一个联接筛选器后，如果发布包含更多相关表，则可使用其他联接筛选器来扩展此联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="822f2-116">After one join filter is defined, you can extend this join filter with another join filter if the publication contains additional related tables.</span></span>  
  
-   <span data-ttu-id="822f2-117">如果在初始化对发布的订阅后添加、修改或删除联接筛选器，必须在更改后生成新的快照并重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="822f2-117">If you add, modify, or delete a join filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="822f2-118">有关属性更改要求的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="822f2-119">建议</span><span class="sxs-lookup"><span data-stu-id="822f2-119">Recommendations</span></span>  
  
-   <span data-ttu-id="822f2-120">可以为一组表手动创建联接筛选器，或者复制可以基于表上定义的外键和主键之间的关系自动生成筛选器。</span><span class="sxs-lookup"><span data-stu-id="822f2-120">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the relationships between foreign keys and primary keys defined on the tables.</span></span> <span data-ttu-id="822f2-121">有关自动生成一组联接筛选器的详细信息，请参阅[在合并项目之间自动生成一组联接筛选器 &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-121">For more information on generating a set of join filters automatically, see [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="822f2-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="822f2-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="822f2-123">可在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”对话框的“筛选行”页上定义、修改和删除联接筛选器。  </span><span class="sxs-lookup"><span data-stu-id="822f2-123">Define, modify, and delete join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="822f2-124">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-124">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-join-filter"></a><span data-ttu-id="822f2-125">定义联接筛选器</span><span class="sxs-lookup"><span data-stu-id="822f2-125">To define a join filter</span></span>  
  
1.  <span data-ttu-id="822f2-126">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，在“筛选的表”窗格中选择现有行筛选器或联接筛选器。   </span><span class="sxs-lookup"><span data-stu-id="822f2-126">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select an existing row filter or join filter in the **Filtered Tables** pane.</span></span>  
  
2.  <span data-ttu-id="822f2-127">单击 **“添加”** ，再单击 **“添加联接以扩展所选筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="822f2-127">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="822f2-128">创建联接语句：选择 **“使用生成器创建语句”** 或 **“手动编写联接语句”** 。</span><span class="sxs-lookup"><span data-stu-id="822f2-128">Create the join statement: select either **Use the builder to create the statement** or **Write the join the statement manually**.</span></span>  
  
    -   <span data-ttu-id="822f2-129">如果选择使用生成器，请使用网格中的列（ **“连接”** 、 **“筛选的表列”** 、 **“运算符”** 、和 **“联接的表列”** ）生成联接语句。</span><span class="sxs-lookup"><span data-stu-id="822f2-129">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span>  
  
         <span data-ttu-id="822f2-130">网格中的每个列都包含下拉组合框，允许你选择两个列和一个运算符（=、<>、<=、\<**, **>=、> 和 like）。</span><span class="sxs-lookup"><span data-stu-id="822f2-130">Each column in the grid contains a drop-down combo box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, and **like**).</span></span> <span data-ttu-id="822f2-131">结果显示在 **“预览”** 文本区域中。</span><span class="sxs-lookup"><span data-stu-id="822f2-131">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="822f2-132">如果联接中涉及多个列对，则从 **“连接词”** 列中选择一个连接词（AND 或 OR），然后再输入两列和一个运算符。</span><span class="sxs-lookup"><span data-stu-id="822f2-132">If the join involves more than one pair of columns, select a conjunction (AND or OR) from the **Conjunction** column, and then enter two more columns and an operator.</span></span>  
  
    -   <span data-ttu-id="822f2-133">如果选择手动编写语句，那么请在 **“联接语句”** 文本区域编写联接语句。</span><span class="sxs-lookup"><span data-stu-id="822f2-133">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="822f2-134">使用 **“筛选的表列”** 列表框和 **“联接的表列”** 列表框将列拖放到 **“联接语句”** 文本区域。</span><span class="sxs-lookup"><span data-stu-id="822f2-134">Use the **Filtered table columns** list box and the **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="822f2-135">完整的联接语句如下所示：</span><span class="sxs-lookup"><span data-stu-id="822f2-135">The complete join statement would appear like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         <span data-ttu-id="822f2-136">JOIN 子句应使用由两个部分组成的名称来命名；它不支持由三个部分和四个部分组成的名称命名。</span><span class="sxs-lookup"><span data-stu-id="822f2-136">The JOIN clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="822f2-137">指定联接选项：</span><span class="sxs-lookup"><span data-stu-id="822f2-137">Specify join options:</span></span>  
  
    -   <span data-ttu-id="822f2-138">如果在筛选的表（父表）中联接的列是唯一的，则选择 **“唯一键”** 。</span><span class="sxs-lookup"><span data-stu-id="822f2-138">If the column on which you join in the filtered table (the parent table) is unique, select **Unique key**.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="822f2-139">选择此选项表示联接筛选器中子表和父表是一对一还是一对多的关系。</span><span class="sxs-lookup"><span data-stu-id="822f2-139">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="822f2-140">仅当子表的联接列上具有保证唯一性的约束时才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="822f2-140">Only select this option if you have a constraint on the joining column in the child table that guarantees uniqueness.</span></span> <span data-ttu-id="822f2-141">如果未能正确设置此选项，可能无法收敛数据。</span><span class="sxs-lookup"><span data-stu-id="822f2-141">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   <span data-ttu-id="822f2-142">默认情况下，合并复制在同步过程中会逐行处理更改。</span><span class="sxs-lookup"><span data-stu-id="822f2-142">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="822f2-143">要将筛选的表行和联接的表行中的相关更改作为一个单元进行处理，则选择“逻辑记录”（仅 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 和更高版本）。</span><span class="sxs-lookup"><span data-stu-id="822f2-143">To have related changes in rows of both the filtered table and the joined table processed as a unit, select **Logical record** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions only).</span></span> <span data-ttu-id="822f2-144">只有满足使用逻辑记录的项目和发布要求，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="822f2-144">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="822f2-145">有关详细信息，请参阅[通过逻辑记录对相关行的更改进行分组](../merge/group-changes-to-related-rows-with-logical-records.md)中的“使用逻辑记录的注意事项”部分。</span><span class="sxs-lookup"><span data-stu-id="822f2-145">For more information see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="822f2-146">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="822f2-146">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-join-filter"></a><span data-ttu-id="822f2-147">修改联接筛选器</span><span class="sxs-lookup"><span data-stu-id="822f2-147">To modify a join filter</span></span>  
  
1.  <span data-ttu-id="822f2-148">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，在“筛选的表”窗格中选择筛选器，然后单击“编辑”。    </span><span class="sxs-lookup"><span data-stu-id="822f2-148">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="822f2-149">在 **“编辑联接”** 对话框中，修改筛选器。</span><span class="sxs-lookup"><span data-stu-id="822f2-149">In the **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-join-filter"></a><span data-ttu-id="822f2-150">删除联接筛选器</span><span class="sxs-lookup"><span data-stu-id="822f2-150">To delete a join filter</span></span>  
  
1.  <span data-ttu-id="822f2-151">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，在“筛选的表”窗格中选择筛选器，然后单击“删除”。    </span><span class="sxs-lookup"><span data-stu-id="822f2-151">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="822f2-152">如果删除的联接筛选器自身是由其他联接扩展而成的，则也将删除那些联接。</span><span class="sxs-lookup"><span data-stu-id="822f2-152">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="822f2-153">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="822f2-153">Using Transact-SQL</span></span>  
 <span data-ttu-id="822f2-154">这些过程显示了父项目上的参数化筛选器以及该项目和相关子项目间的联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="822f2-154">These procedures show a parameterized filter on a parent article with join filters between this article and related child articles.</span></span> <span data-ttu-id="822f2-155">可以使用复制存储过程，以编程方式定义和修改联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="822f2-155">Join filters can be defined and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-join-filter-to-extend-an-article-filter-to-related-articles-in-a-merge-publication"></a><span data-ttu-id="822f2-156">定义联接筛选器以将项目筛选器扩展到合并发布中的相关项目</span><span class="sxs-lookup"><span data-stu-id="822f2-156">To define a join filter to extend an article filter to related articles in a merge publication</span></span>  
  
1.  <span data-ttu-id="822f2-157">为要联接到的项目（又称为父项目）定义筛选。</span><span class="sxs-lookup"><span data-stu-id="822f2-157">Define the filtering for the article being joined to, which is also known as the parent article.</span></span>  
  
    -   <span data-ttu-id="822f2-158">对于使用参数化行筛选器筛选的项目，请参阅 [定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-158">For an article filtered using a parameterized row filter, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="822f2-159">对于使用静态行筛选器筛选的项目，请参阅 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-159">For an article filtered using a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
2.  <span data-ttu-id="822f2-160">在发布服务器上，对发布数据库执行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 来为发布定义一个或多个相关项目（又称为子项目）。</span><span class="sxs-lookup"><span data-stu-id="822f2-160">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define one or more related articles, which are also known as child articles, for the publication.</span></span> <span data-ttu-id="822f2-161">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-161">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="822f2-162">在发布服务器上，对发布数据库执行 [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="822f2-162">At the Publisher on the publication database, execute [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="822f2-163">指定 **@publication** 、的此筛选器的唯一名称 **@filtername** 、在步骤2中创建的子项目的名称 **@article** 、要联接到的父项目的名称 **@join_articlename** ，以及以下值之一 **@join_unique_key** ：</span><span class="sxs-lookup"><span data-stu-id="822f2-163">Specify **@publication**, a unique name for this filter for **@filtername**, the name of the child article created in step 2 for **@article**, the name of the parent article being joined to for **@join_articlename**, and one of the following values for **@join_unique_key**:</span></span>  
  
    -   <span data-ttu-id="822f2-164">**0** - 表示父项目与子项目间的多对一或多对多联接。</span><span class="sxs-lookup"><span data-stu-id="822f2-164">**0** - indicates a many-to-one or many-to-many join between the parent and child articles.</span></span>  
  
    -   <span data-ttu-id="822f2-165">**1** - 表示父项目与子项目间的一对一或一对多联接。</span><span class="sxs-lookup"><span data-stu-id="822f2-165">**1** - indicates a one-to-one or one-to-many join between the parent and child articles.</span></span>  
  
     <span data-ttu-id="822f2-166">此步骤定义了两个项目间的联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="822f2-166">This defines a join filter between the two articles.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="822f2-167">仅 **@join_unique_key** 当对父项目的基础表中的联接列具有保证唯一性的约束时，才设置为**1** 。</span><span class="sxs-lookup"><span data-stu-id="822f2-167">Only set **@join_unique_key** to **1** if you have a constraint on the joining column in the underlying table for the parent article that guarantees uniqueness.</span></span> <span data-ttu-id="822f2-168">如果 **@join_unique_key** 错误地设置为**1** ，则可能无法收敛数据。</span><span class="sxs-lookup"><span data-stu-id="822f2-168">If **@join_unique_key** is set to **1** incorrectly, non-convergence of data may occur.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="822f2-169">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="822f2-169">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="822f2-170">此示例定义了合并发布的项目，并针对 `SalesOrderDetail` 表来筛选 `SalesOrderHeader` 表项目，而该表本身使用静态行筛选器进行筛选。</span><span class="sxs-lookup"><span data-stu-id="822f2-170">This example defines an article for a merge publication, where the `SalesOrderDetail` table article is filtered against the `SalesOrderHeader` table that is itself filtered using a static row filter.</span></span> <span data-ttu-id="822f2-171">有关详细信息，请参阅 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-171">For more information, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
 <span data-ttu-id="822f2-172">此示例定义了合并发布中的一组项目，并针对 `Employee` 表使用一系列联接筛选器来筛选这些项目，而该表本身则使用参数化行筛选器按 [LoginID](/sql/t-sql/functions/host-name-transact-sql) 列中的 **HOST_NAME** 值进行筛选。</span><span class="sxs-lookup"><span data-stu-id="822f2-172">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the value of [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) in the **LoginID** column.</span></span> <span data-ttu-id="822f2-173">有关详细信息，请参阅 [定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="822f2-173">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
## <a name="see-also"></a><span data-ttu-id="822f2-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="822f2-174">See Also</span></span>  
 <span data-ttu-id="822f2-175">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="822f2-175">[Join Filters](../merge/join-filters.md) </span></span>  
 <span data-ttu-id="822f2-176">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="822f2-176">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 <span data-ttu-id="822f2-177">[更改发布和项目属性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="822f2-177">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="822f2-178">[为合并复制筛选已发布数据](../merge/filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="822f2-178">[Filter Published Data for Merge Replication](../merge/filter-published-data-for-merge-replication.md) </span></span>  
 <span data-ttu-id="822f2-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="822f2-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="822f2-180">[定义合并表项目间的逻辑记录关系](define-a-logical-record-relationship-between-merge-table-articles.md) </span><span class="sxs-lookup"><span data-stu-id="822f2-180">[Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md) </span></span>  
 [<span data-ttu-id="822f2-181">定义和修改合并项目的参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="822f2-181">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  
