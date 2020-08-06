---
title: 添加或编辑联接 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.addeditjoin.f1
ms.assetid: 3b546560-720f-48b8-9d63-cf159290e9d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3e17b084a232375734601b515821273d482fcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578156"
---
# <a name="add-or-edit-join"></a><span data-ttu-id="0c34b-102">添加或编辑联接</span><span class="sxs-lookup"><span data-stu-id="0c34b-102">Add or Edit Join</span></span>
  <span data-ttu-id="0c34b-103">可以使用 **“添加联接”** 和 **“编辑联接”** 对话框为合并发布添加和编辑联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="0c34b-103">The **Add Join** and **Edit Join** dialog boxes allow you to add and edit join filters for merge publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c34b-104">编辑现有发布中的筛选器需要为该发布创建新的快照。</span><span class="sxs-lookup"><span data-stu-id="0c34b-104">Editing a filter in an existing publication requires a new snapshot for the publication.</span></span> <span data-ttu-id="0c34b-105">如果发布有订阅，则必须重新初始化这些订阅。</span><span class="sxs-lookup"><span data-stu-id="0c34b-105">If a publication has subscriptions, the subscriptions must be reinitialized.</span></span> <span data-ttu-id="0c34b-106">有关属性更改的详细信息，请参阅[更改发布和项目属性](publish/change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0c34b-106">For more information about property changes, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="0c34b-107">联接筛选器允许根据发布中相关表的筛选方式对表进行筛选。</span><span class="sxs-lookup"><span data-stu-id="0c34b-107">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="0c34b-108">通常，使用参数化行筛选器筛选父表；然后按照定义表之间联接的同样方式定义一个或多个联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="0c34b-108">Typically a parent table is filtered using a parameterized row filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="0c34b-109">联接筛选器会扩展行筛选器，以便仅在相关表中的数据与联接筛选子句匹配时才复制该数据。</span><span class="sxs-lookup"><span data-stu-id="0c34b-109">The join filters extend the row filter so that the data in the related tables is replicated only if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="0c34b-110">联接筛选器通常遵循为其应用到的表定义的主键/外键关系，但并不严格受限于主键/外键关系。</span><span class="sxs-lookup"><span data-stu-id="0c34b-110">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="0c34b-111">联接筛选器可基于用于比较两个项目表中相关数据的任何逻辑。</span><span class="sxs-lookup"><span data-stu-id="0c34b-111">The join filter can be based on any logic that compares related data in two article tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0c34b-112">联接筛选器可关联的表数量不受限制，但有大量表的筛选器会影响合并处理过程中的性能。</span><span class="sxs-lookup"><span data-stu-id="0c34b-112">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can impact performance during merge processing.</span></span> <span data-ttu-id="0c34b-113">如果要生成五个或更多表的联接筛选器，请考虑其他解决方案：不筛选小表、不会发生更改的表或主要是查找表的表。</span><span class="sxs-lookup"><span data-stu-id="0c34b-113">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="0c34b-114">仅在必须跨订阅服务器分区的表之间使用联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="0c34b-114">Use join filters only between tables that must be partitioned among Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0c34b-115">选项</span><span class="sxs-lookup"><span data-stu-id="0c34b-115">Options</span></span>  
 <span data-ttu-id="0c34b-116">此对话框涉及三个步骤，用以在两个表之间创建联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="0c34b-116">This dialog box involves a three-step process to create a join filter between two tables.</span></span> <span data-ttu-id="0c34b-117">创建一个以上的联接筛选器需要多次调用此对话框。</span><span class="sxs-lookup"><span data-stu-id="0c34b-117">Creating more than one join filter requires more than one pass through the dialog box.</span></span>  
  
1.  <span data-ttu-id="0c34b-118">**验证筛选的表并选择联接的表**</span><span class="sxs-lookup"><span data-stu-id="0c34b-118">**Verify filtered table and select the joined table**</span></span>  
  
    -   <span data-ttu-id="0c34b-119">如果要添加新的联接，请验证 **“筛选的表”** 文本框中的表是否正确（如果不正确，请单击 **“取消”** ，在 **“筛选表行”** 页中选择正确的表，并单击 **“添加联接”** 返回此对话框）。</span><span class="sxs-lookup"><span data-stu-id="0c34b-119">If you are adding a new join, verify that the table in the **Filtered table** text box is correct (if it is not correct, click **Cancel**, select the correct table on the **Filter Table Rows** page, and click **Add Join** to return to this dialog box).</span></span> <span data-ttu-id="0c34b-120">再从 **“联接的表”** 下拉列表框中选择一个表。</span><span class="sxs-lookup"><span data-stu-id="0c34b-120">Then select a table from the **Joined table** drop-down list box.</span></span>  
  
    -   <span data-ttu-id="0c34b-121">如果正在编辑现有的联接，那么表名已经指定，无法更改。</span><span class="sxs-lookup"><span data-stu-id="0c34b-121">If you are editing an existing join, the table names will be specified already and cannot be changed.</span></span> <span data-ttu-id="0c34b-122">若要更改联接所涉及的表，您必须在 **“筛选表行”** 页中删除现有联接筛选器，并在不同表之间创建新的联接。</span><span class="sxs-lookup"><span data-stu-id="0c34b-122">To change the tables involved in the join, you must delete the existing join filter on the **Filter Table Rows** page and create a new join between different tables.</span></span>  
  
2.  <span data-ttu-id="0c34b-123">**创建联接语句**</span><span class="sxs-lookup"><span data-stu-id="0c34b-123">**Create the join statement**</span></span>  
  
    -   <span data-ttu-id="0c34b-124">如果要添加新的联接，则可以选择 **“使用生成器创建语句”** 或者 **“手动编写联接语句”** 。</span><span class="sxs-lookup"><span data-stu-id="0c34b-124">If you are adding a new join, select either **Use the builder to create the statement** or **Write the join statement manually**.</span></span> <span data-ttu-id="0c34b-125">如果您开始手动编写联接，那么将无法使用生成器。</span><span class="sxs-lookup"><span data-stu-id="0c34b-125">If you begin writing the join manually, you cannot use the builder.</span></span>  
  
         <span data-ttu-id="0c34b-126">如果选择使用生成器，请使用网格中的列（ **“连接”** 、 **“筛选的表列”** 、 **“运算符”** 、和 **“联接的表列”** ）生成联接语句。</span><span class="sxs-lookup"><span data-stu-id="0c34b-126">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span> <span data-ttu-id="0c34b-127">网格中的每个列都包含下拉列表框，你可用它来选择两个列和一个运算符（=、<>、<=、\<**, **>=、> 等）     。</span><span class="sxs-lookup"><span data-stu-id="0c34b-127">Each column in the grid contains a drop-down list box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, **like**).</span></span> <span data-ttu-id="0c34b-128">结果显示在 **“预览”** 文本区域中。</span><span class="sxs-lookup"><span data-stu-id="0c34b-128">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="0c34b-129">如果联接涉及不止一对列，请从 **“连接”** 列中选择一个连接（ **AND**或 **OR** ），再输入另外两列和一个运算符。</span><span class="sxs-lookup"><span data-stu-id="0c34b-129">If the join involves more than one pair of columns, select a conjunction (**AND** or **OR**) from the **Conjunction** column, and then enter two more columns and another operator.</span></span>  
  
         <span data-ttu-id="0c34b-130">如果选择手动编写语句，那么请在 **“联接语句”** 文本区域编写联接语句。</span><span class="sxs-lookup"><span data-stu-id="0c34b-130">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="0c34b-131">使用 **“筛选的表列”** 列表框和 **“联接的表列”** 列表框将列拖放到 **“联接语句”** 文本区域。</span><span class="sxs-lookup"><span data-stu-id="0c34b-131">Use the **Filtered table columns** list box and **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="0c34b-132">如果要编辑现有的联接，则必须手动进行编辑。</span><span class="sxs-lookup"><span data-stu-id="0c34b-132">If you are editing an existing join, you must make edits manually.</span></span>  
  
3.  <span data-ttu-id="0c34b-133">**指定联接选项**</span><span class="sxs-lookup"><span data-stu-id="0c34b-133">**Specify join options**</span></span>  
  
    -   <span data-ttu-id="0c34b-134">如果在筛选的表中要联接的列是唯一的，请选择 **“唯一键”** 。</span><span class="sxs-lookup"><span data-stu-id="0c34b-134">If the column on which you join in the filtered table is unique, select **Unique key**.</span></span> <span data-ttu-id="0c34b-135">对于唯一列，在合并过程中还可以使用一些专门的性能优化选项。</span><span class="sxs-lookup"><span data-stu-id="0c34b-135">The merge process has special performance optimizations available if the column is unique.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="0c34b-136">选择此选项表示联接筛选器中子表和父表是一对一还是一对多的关系。</span><span class="sxs-lookup"><span data-stu-id="0c34b-136">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="0c34b-137">如果父表中要联接的列具有保证唯一性的约束，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="0c34b-137">Only select this option if you have a constraint on the joining column in the parent table that guarantees uniqueness.</span></span> <span data-ttu-id="0c34b-138">如果未能正确设置此选项，可能无法收敛数据。</span><span class="sxs-lookup"><span data-stu-id="0c34b-138">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   <span data-ttu-id="0c34b-139">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="0c34b-139">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="0c34b-140">默认情况下，合并复制在同步过程中会逐行处理更改。</span><span class="sxs-lookup"><span data-stu-id="0c34b-140">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="0c34b-141">若要按单位处理相关更改，请选择 **“逻辑记录”** 。</span><span class="sxs-lookup"><span data-stu-id="0c34b-141">To have related changes processed as a unit, select **Logical record**.</span></span> <span data-ttu-id="0c34b-142">只有满足使用逻辑记录的项目和发布要求，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="0c34b-142">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="0c34b-143">有关详细信息，请参阅[通过逻辑记录对相关行的更改进行分组](merge/group-changes-to-related-rows-with-logical-records.md)中的“使用逻辑记录的注意事项”部分。</span><span class="sxs-lookup"><span data-stu-id="0c34b-143">For more information, see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
 <span data-ttu-id="0c34b-144">在添加或编辑完筛选器后，请单击 **“确定”** 以保存更改并关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="0c34b-144">After you have added or edited a filter, click **OK** to save changes and close the dialog box.</span></span> <span data-ttu-id="0c34b-145">将对照 SELECT 子句中的表分析并运行指定的筛选器。</span><span class="sxs-lookup"><span data-stu-id="0c34b-145">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="0c34b-146">如果筛选语句有语法错误或其他问题，将会通知您编辑该筛选语句。</span><span class="sxs-lookup"><span data-stu-id="0c34b-146">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c34b-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c34b-147">See Also</span></span>  
 <span data-ttu-id="0c34b-148">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="0c34b-148">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="0c34b-149">[查看和修改发布属性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="0c34b-149">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="0c34b-150">[筛选已发布数据](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="0c34b-150">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="0c34b-151">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="0c34b-151">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="0c34b-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="0c34b-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="0c34b-153">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="0c34b-153">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
