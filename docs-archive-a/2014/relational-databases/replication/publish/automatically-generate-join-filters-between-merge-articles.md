---
title: 在合并项目之间自动生成一组联接筛选器 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- automatic join filter generation
- join filters
ms.assetid: 7ef419f4-c17f-42a5-9068-174a3ec08941
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bfdbf93aad134e4da873a6aade307754a2637e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576636"
---
# <a name="automatically-generate-a-set-of-join-filters-between-merge-articles-sql-server-management-studio"></a><span data-ttu-id="6aaa5-102">在合并项目之间自动生成一组联接筛选器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6aaa5-102">Automatically Generate a Set of Join Filters Between Merge Articles (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6aaa5-103">在新建发布向导的“筛选表行”页上，或在“发布属性 -   \<Publication>”对话框的“筛选行”页上自动生成一组联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-103">Automatically generate a set of join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="6aaa5-104">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-104">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aaa5-105">如果你在发布订阅初始化后在“发布属性 - \<Publication>”对话框中自动生成一组联接筛选器，则必须生成一个新快照，并在进行更改后重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-105">If you automatically generate a set of join filters in the **Publication Properties - \<Publication>** dialog box after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="6aaa5-106">有关属性更改要求的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-106">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="6aaa5-107">可以手动为一组表创建联接筛选器，也可由复制根据表上定义的外键和主键的关系自动生成联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-107">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the foreign key to primary key relationships defined on the tables.</span></span> <span data-ttu-id="6aaa5-108">有关手动创建联接筛选器的详细信息，请参阅[定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-108">For more information about creating join filters manually, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
### <a name="to-automatically-generate-a-set-of-join-filters-between-merge-articles"></a><span data-ttu-id="6aaa5-109">在合并项目之间自动生成一组联接筛选器</span><span class="sxs-lookup"><span data-stu-id="6aaa5-109">To automatically generate a set of join filters between merge articles</span></span>  
  
1.  <span data-ttu-id="6aaa5-110">在新建发布向导的“筛选表行”页上，或在“发布属性 - \<Publication>”的“筛选行”页上，依次单击“添加”和“自动生成筛选器”。    </span><span class="sxs-lookup"><span data-stu-id="6aaa5-110">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Automatically Generate Filters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6aaa5-111">自动生成筛选器将删除发布中所有现有的行筛选器或联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-111">Automatically generating filters deletes any existing row filters or join filters in the publication.</span></span> <span data-ttu-id="6aaa5-112">可以在自动生成一组筛选器后添加筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-112">You can add filters after automatically generating a set of filters.</span></span>  
  
2.  <span data-ttu-id="6aaa5-113">按照 **“生成筛选器”** 对话框中的过程创建行筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-113">Follow the process in the **Generate Filters** dialog box to create a row filter.</span></span> <span data-ttu-id="6aaa5-114">然后通过主键和外键的关系将行筛选器扩展到与筛选的表有关的表。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-114">The row filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span>  
  
    1.  <span data-ttu-id="6aaa5-115">从下拉列表框中选择要筛选的表。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-115">Select a table to filter from the drop-down list box.</span></span>  
  
    2.  <span data-ttu-id="6aaa5-116">在 **“筛选语句”** 文本框中创建一个筛选语句。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-116">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="6aaa5-117">您可以在文本区域中直接键入，也可以从 **“列”** 列表框中拖放列。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-117">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
         <span data-ttu-id="6aaa5-118">**“筛选语句”** 文本区域包括默认的文本，其格式为：</span><span class="sxs-lookup"><span data-stu-id="6aaa5-118">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
         <span data-ttu-id="6aaa5-119">不能更改默认文本；在 WHERE 关键字后使用标准的 SQL 语法键入静态行筛选器或参数化行筛选器的筛选器子句。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-119">The default text cannot be changed; type the filter clause for a static row filter or a parameterized row filter after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="6aaa5-120">参数化行筛选器的完整筛选器子句如下所示：</span><span class="sxs-lookup"><span data-stu-id="6aaa5-120">The complete filter clause for a parameterized row filter would look like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="6aaa5-121">WHERE 子句应使用由两部分构成的命名方式，不支持由三部分和四部分构成的命名方式。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-121">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
    3.  <span data-ttu-id="6aaa5-122">指定筛选选项。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-122">Specify filter options.</span></span>  
  
         <span data-ttu-id="6aaa5-123">选择指示订阅服务器之间如何共享数据的选项：“此表中的行将转到多个订阅”或“此表中的行将仅转到一个订阅” 。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-123">Select the option that matches how data will be shared among Subscribers: **A row from this table will go to multiple subscriptions** or **A row from this table will go to only one subscription**.</span></span> <span data-ttu-id="6aaa5-124">如果选择 **“此表中的行将仅转到一个订阅”** ，则合并复制可以通过存储和处理较少的元数据来优化性能。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-124">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="6aaa5-125">但是，必须确保在对数据分区时不能将行复制到多个订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-125">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="6aaa5-126">有关详细信息，请参阅主题 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)中的“设置‘分区选项’”部分。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-126">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="6aaa5-127">将对照 SELECT 子句中的表分析并运行指定的筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-127">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="6aaa5-128">如果筛选语句有语法错误或其他问题，将会通知您编辑该筛选语句。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-128">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
     <span data-ttu-id="6aaa5-129">分析语句后，复制将创建必需的联接筛选器，并在 **“筛选表行”** 页或 **“筛选行”** 页的 **“筛选的表”** 窗格中显示这些联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-129">After the statement is parsed, replication creates the necessary join filters and displays them in the **Filtered Tables** pane on the **Filter Table Rows** or **Filter Rows** page.</span></span> <span data-ttu-id="6aaa5-130">如果从新建发布向导生成筛选器，并且尚未为运行此向导的发布服务器配置分发服务器，系统会提示您进行此项配置。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-130">If you are generating filters from the New Publication Wizard and have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
4.  <span data-ttu-id="6aaa5-131">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-131">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
### <a name="to-modify-a-filter-that-was-automatically-generated"></a><span data-ttu-id="6aaa5-132">修改自动生成的筛选器</span><span class="sxs-lookup"><span data-stu-id="6aaa5-132">To modify a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="6aaa5-133">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，在“筛选的表”窗格中选择筛选器，然后单击“编辑”。    </span><span class="sxs-lookup"><span data-stu-id="6aaa5-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="6aaa5-134">在 **“编辑筛选器”** 或 **“编辑联接”** 对话框中修改筛选器。</span><span class="sxs-lookup"><span data-stu-id="6aaa5-134">In the **Edit Filter** or **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-filter-that-was-automatically-generated"></a><span data-ttu-id="6aaa5-135">删除自动生成的筛选器</span><span class="sxs-lookup"><span data-stu-id="6aaa5-135">To delete a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="6aaa5-136">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”的“筛选行”页上，在“筛选的表”窗格中选择筛选器，然后单击“删除”。    </span><span class="sxs-lookup"><span data-stu-id="6aaa5-136">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aaa5-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6aaa5-137">See Also</span></span>  
 <span data-ttu-id="6aaa5-138">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="6aaa5-138">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="6aaa5-139">参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="6aaa5-139">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
