---
title: 筛选表行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.filtertablerows.f1
ms.assetid: 005f5c71-0401-490e-8823-adc54a2e9675
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9adeb2501adfd37658ddf05aa9956d6c3922bb80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578090"
---
# <a name="filter-table-rows"></a><span data-ttu-id="dca9f-102">筛选表行</span><span class="sxs-lookup"><span data-stu-id="dca9f-102">Filter Table Rows</span></span>
  <span data-ttu-id="dca9f-103">在 **“筛选表行”** 页中，您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="dca9f-103">The **Filter Table Rows** page allows you to:</span></span>  
  
-   <span data-ttu-id="dca9f-104">将静态行筛选器应用于快照发布、事务发布和合并发布中的表项目。</span><span class="sxs-lookup"><span data-stu-id="dca9f-104">Apply static row filters to table articles in snapshot, transactional, and merge publications.</span></span>  
  
-   <span data-ttu-id="dca9f-105">将参数化行筛选器应用于合并发布中的表项目。</span><span class="sxs-lookup"><span data-stu-id="dca9f-105">Apply parameterized row filters to table articles in merge publications.</span></span>  
  
-   <span data-ttu-id="dca9f-106">使用联接筛选器将合并表项目的筛选器扩展到相关表项目。</span><span class="sxs-lookup"><span data-stu-id="dca9f-106">Use join filters to extend filters on merge table articles to related table articles.</span></span>  
  
 <span data-ttu-id="dca9f-107">有关筛选选项的详细信息，请参阅[筛选已发布数据](publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dca9f-107">For more information about filtering options, see [Filter Published Data](publish/filter-published-data.md).</span></span> <span data-ttu-id="dca9f-108">可以在 **“发布属性”** 对话框的 **“筛选行”** 页中更改筛选。</span><span class="sxs-lookup"><span data-stu-id="dca9f-108">Filtering can be changed in the **Filter Rows** page of the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="dca9f-109">为了获得最佳的应用程序性能并减少所需的远程存储量，或者要限定某些数据仅供特定的订阅服务器使用，您应该只发布所需数据。</span><span class="sxs-lookup"><span data-stu-id="dca9f-109">To maximize application performance and reduce the amount of remote storage required, or to restrict the availability of certain data to specific Subscribers, you should publish only the data required.</span></span> <span data-ttu-id="dca9f-110">发布中既可以包含未筛选的表，也可以包含已筛选的表。</span><span class="sxs-lookup"><span data-stu-id="dca9f-110">Your publication can include both unfiltered and filtered tables.</span></span> <span data-ttu-id="dca9f-111">例如，可以包含公司产品的完整（未筛选）表，然后使用行筛选器提供一个仅包含特定区域客户的筛选表。</span><span class="sxs-lookup"><span data-stu-id="dca9f-111">For example, you could include the complete (unfiltered) table of company products and use row filters to provide a filtered table of customers for a specific region.</span></span> <span data-ttu-id="dca9f-112">通过筛选已发布数据，可以：</span><span class="sxs-lookup"><span data-stu-id="dca9f-112">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="dca9f-113">最大程度地减少通过网络发送的数据量。</span><span class="sxs-lookup"><span data-stu-id="dca9f-113">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="dca9f-114">减少订阅服务器上需要的存储空间量。</span><span class="sxs-lookup"><span data-stu-id="dca9f-114">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="dca9f-115">根据各个订阅服务器的要求，自定义发布和应用程序。</span><span class="sxs-lookup"><span data-stu-id="dca9f-115">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="dca9f-116">由于可以将不同的数据分区发送到不同的订阅服务器（没有两个订阅服务器会同时更新相同的数据值），因此可以避免或减少订阅服务器更新数据时的冲突。</span><span class="sxs-lookup"><span data-stu-id="dca9f-116">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="dca9f-117">避免传输敏感数据。</span><span class="sxs-lookup"><span data-stu-id="dca9f-117">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="dca9f-118">行筛选器和列筛选器可以用于限制订阅服务器对数据的访问。</span><span class="sxs-lookup"><span data-stu-id="dca9f-118">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="dca9f-119">对于合并复制，如果使用包括 HOST_NAME() 的参数化筛选器，则需要考虑安全问题。</span><span class="sxs-lookup"><span data-stu-id="dca9f-119">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="dca9f-120">有关详细信息，请参阅 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)中的“使用 HOST_NAME() 进行筛选”部分。</span><span class="sxs-lookup"><span data-stu-id="dca9f-120">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="dca9f-121">筛选器不能包含复制所用的 `rowguidcol` 来标识行。</span><span class="sxs-lookup"><span data-stu-id="dca9f-121">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="dca9f-122">默认情况下，这是您设置合并复制时添加的列，命名为 **rowguid**。</span><span class="sxs-lookup"><span data-stu-id="dca9f-122">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dca9f-123">选项</span><span class="sxs-lookup"><span data-stu-id="dca9f-123">Options</span></span>  
 <span data-ttu-id="dca9f-124">**筛选的表**</span><span class="sxs-lookup"><span data-stu-id="dca9f-124">**Filtered Tables**</span></span>  
 <span data-ttu-id="dca9f-125">此窗格使用您向发布中的表项目添加的筛选器进行填充。</span><span class="sxs-lookup"><span data-stu-id="dca9f-125">This pane is populated with filters as you add them to table articles in the publication.</span></span> <span data-ttu-id="dca9f-126">带行筛选器的表在窗格中显示为顶级节点。</span><span class="sxs-lookup"><span data-stu-id="dca9f-126">Tables with row filters are shown as top-level nodes in the pane.</span></span> <span data-ttu-id="dca9f-127">对于合并发布，筛选操作通过联接筛选器扩展到的表显示为子节点。</span><span class="sxs-lookup"><span data-stu-id="dca9f-127">For merge publications, tables to which filtering has been extended through a join filter are shown as child nodes.</span></span>  
  
 <span data-ttu-id="dca9f-128">**添加**</span><span class="sxs-lookup"><span data-stu-id="dca9f-128">**Add**</span></span>  
 <span data-ttu-id="dca9f-129">单击 **“添加”** 可以启动一个用于对表项目进行筛选的对话框。</span><span class="sxs-lookup"><span data-stu-id="dca9f-129">Click **Add** to launch a dialog box that enables you to filter table articles.</span></span> <span data-ttu-id="dca9f-130">对于快照发布或事务发布，单击 **“添加”** 将立即启动对话框。</span><span class="sxs-lookup"><span data-stu-id="dca9f-130">Clicking **Add** for a snapshot or transactional publication launches a dialog box immediately.</span></span> <span data-ttu-id="dca9f-131">对于合并发布，单击“添加”将会显示三个选项 ：“添加筛选器”、“添加联接以扩展所选筛选器”和“自动生成筛选器”  。</span><span class="sxs-lookup"><span data-stu-id="dca9f-131">Clicking **Add** for a merge publication displays three choices: **Add Filter**; **Add Join to Extend the Selected Filter**; **Automatically Generate Filters**.</span></span>  
  
-   <span data-ttu-id="dca9f-132">选择 **“添加筛选器”** 将启动 **“添加筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="dca9f-132">Select **Add Filter** to launch the **Add Filter** dialog box.</span></span> <span data-ttu-id="dca9f-133">使用此对话框可以将行筛选器应用于表项目。</span><span class="sxs-lookup"><span data-stu-id="dca9f-133">This dialog box allows you to apply row filters to a table article.</span></span> <span data-ttu-id="dca9f-134">例如，在 **“添加筛选器”** 对话框中，可以指定在将包含客户数据的表复制到订阅服务器时，该表应只包含法国客户的相关数据。</span><span class="sxs-lookup"><span data-stu-id="dca9f-134">In the **Add Filter** dialog box, you could, for example, specify that a table with customer data should only contain data on French customers when it is replicated to Subscribers.</span></span>  
  
-   <span data-ttu-id="dca9f-135">选择 **“添加联接以扩展所选筛选器”** 将启动 **“添加联接”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="dca9f-135">Select **Add Join to Extend the Selected Filter** to launch the **Add Join** dialog box.</span></span> <span data-ttu-id="dca9f-136">使用 **“添加联接”** 对话框，可以对行筛选器进行扩展，这样就可以筛选与行筛选器所在表相关的表中的数据。</span><span class="sxs-lookup"><span data-stu-id="dca9f-136">The **Add Join** dialog box allows you to extend a row filter so that it filters data in tables related to the table with the row filter.</span></span> <span data-ttu-id="dca9f-137">例如，如果筛选一个客户表以便它仅包含法国客户的相关数据，并且还有一个与客户订单相关的表，则可以在两个表之间定义一个联接，以便该订单表仅包括来自法国客户的订单。</span><span class="sxs-lookup"><span data-stu-id="dca9f-137">For example, if a customer table is filtered so that it only contains data on French customers and there is a related table for customer orders, you can define a join between the two tables so that the orders table only includes orders from French customers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dca9f-138">只有在筛选器窗格中选择了联接的基表后，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="dca9f-138">This option is available only if you first select the base table of the join in the filter pane.</span></span>  
  
-   <span data-ttu-id="dca9f-139">选择 **“自动生成筛选器”** 将启动 **“生成筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="dca9f-139">Select **Automatically Generate Filters** to launch the **Generate Filters** dialog box.</span></span> <span data-ttu-id="dca9f-140">使用此对话框可以为合并发布中的某个表定义行筛选器，复制会自动将该行筛选器扩展到通过外键关系相关联的其他表。</span><span class="sxs-lookup"><span data-stu-id="dca9f-140">This dialog box allows you to define a row filter on one table in a merge publication that replication automatically extends to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="dca9f-141">例如，一个发布可以包括三个表：客户表、订单表（带有指向客户表的外键）和订单详细信息表（带有指向订单表的外键）。</span><span class="sxs-lookup"><span data-stu-id="dca9f-141">For example, a publication could include three tables: a customer table, an orders table (with a foreign key to the customer table), and an order details table (with a foreign key to the orders table).</span></span> <span data-ttu-id="dca9f-142">为客户表定义行筛选器后，复制会将该行筛选器扩展到其他表。</span><span class="sxs-lookup"><span data-stu-id="dca9f-142">Define a row filter on the customer table, and replication will extend it to the other tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dca9f-143">当通过复制自动生成筛选器时，会删除发布中的所有现有筛选器。</span><span class="sxs-lookup"><span data-stu-id="dca9f-143">When filters are automatically generated by replication, any existing filters on the publication are deleted.</span></span> <span data-ttu-id="dca9f-144">若要同时包括自动生成的筛选器和手动指定的筛选器，请首先生成筛选器。</span><span class="sxs-lookup"><span data-stu-id="dca9f-144">To include both filters generated automatically and ones specified manually, generate filters first.</span></span> <span data-ttu-id="dca9f-145">对于每个发布，只能指定一组自动生成的筛选器。</span><span class="sxs-lookup"><span data-stu-id="dca9f-145">You can only specify one set of automatically generated filters for each publication.</span></span>  
  
 <span data-ttu-id="dca9f-146">**编辑**</span><span class="sxs-lookup"><span data-stu-id="dca9f-146">**Edit**</span></span>  
 <span data-ttu-id="dca9f-147">在筛选器窗格中选择一个行筛选器或联接筛选器，然后单击 **“编辑”** 以启动 **“编辑筛选器”** 或 **“编辑联接”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="dca9f-147">Select a row filter or join filter in the filter pane and click **Edit** to launch the **Edit Filter** or **Edit Join** dialog box.</span></span>  
  
 <span data-ttu-id="dca9f-148">**删除**</span><span class="sxs-lookup"><span data-stu-id="dca9f-148">**Delete**</span></span>  
 <span data-ttu-id="dca9f-149">在筛选器窗格中选择一个行筛选器或联接筛选器，然后单击 **“删除”** 以删除该筛选器。</span><span class="sxs-lookup"><span data-stu-id="dca9f-149">Select a row filter or join filter in the filter pane and click **Delete** to delete the filter.</span></span>  
  
 <span data-ttu-id="dca9f-150">**查找表**</span><span class="sxs-lookup"><span data-stu-id="dca9f-150">**Find Table**</span></span>  
 <span data-ttu-id="dca9f-151">仅将发布与联接筛选器合并。</span><span class="sxs-lookup"><span data-stu-id="dca9f-151">Merge publications with join filters only.</span></span> <span data-ttu-id="dca9f-152">单击 **“查找表”** 可以在复杂的筛选器树中查找表。</span><span class="sxs-lookup"><span data-stu-id="dca9f-152">Click **Find Table** to find a table in a complex filter tree.</span></span> <span data-ttu-id="dca9f-153">在关系复杂的数据库中，一个表可以联接到多个表，因此可能出现在筛选器树中的多个位置。</span><span class="sxs-lookup"><span data-stu-id="dca9f-153">In a database with complex relationships, a table can be joined to multiple tables, and therefore can appear in more than one place in the filter tree.</span></span>  
  
 <span data-ttu-id="dca9f-154">实际的表只显示在树中的一个位置，该表在其他位置使用快捷方式来表示。</span><span class="sxs-lookup"><span data-stu-id="dca9f-154">The actual table appears in only one place in the tree, and in other places, the table is represented by a shortcut.</span></span> <span data-ttu-id="dca9f-155">表的快捷方式只是对该表的引用；它不显示该表的子节点。</span><span class="sxs-lookup"><span data-stu-id="dca9f-155">A shortcut to a table is only a reference to the table; it does not show the child nodes of the table.</span></span> <span data-ttu-id="dca9f-156">快捷方式节点标记有快捷方式箭头，展开该节点将显示“单击‘查找表’可查看 \<tablename> 表”文本。</span><span class="sxs-lookup"><span data-stu-id="dca9f-156">A shortcut node is marked with a shortcut arrow, and expanding that node shows the text **Click Find Table to see table for \<tablename>**.</span></span>  
  
 <span data-ttu-id="dca9f-157">选择窗格中的快捷方式节点，并单击 **“查找表”** 。</span><span class="sxs-lookup"><span data-stu-id="dca9f-157">Select a shortcut node in the pane and click **Find Table**.</span></span> <span data-ttu-id="dca9f-158">窗格随即展开，并突出显示所查找的表。</span><span class="sxs-lookup"><span data-stu-id="dca9f-158">The pane is expanded and the table is highlighted.</span></span> <span data-ttu-id="dca9f-159">如果单击 **“查找表”** 而没有选定快捷方式节点，将会启动 **“查找表”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="dca9f-159">If you click **Find Table** without a shortcut node selected, a **Find Table** dialog box is launched.</span></span>  
  
 <span data-ttu-id="dca9f-160">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="dca9f-160">**Filter**</span></span>  
 <span data-ttu-id="dca9f-161">包含筛选器窗格中选定筛选器的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 定义。</span><span class="sxs-lookup"><span data-stu-id="dca9f-161">Contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] definition for the filter selected in the filter pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca9f-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dca9f-162">See Also</span></span>  
 <span data-ttu-id="dca9f-163">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="dca9f-163">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="dca9f-164">[查看和修改发布属性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="dca9f-164">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="dca9f-165">[筛选已发布数据](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="dca9f-165">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="dca9f-166">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="dca9f-166">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="dca9f-167">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="dca9f-167">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="dca9f-168">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="dca9f-168">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
