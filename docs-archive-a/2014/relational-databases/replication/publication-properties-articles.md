---
title: 发布属性，项目 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.articles.f1
ms.assetid: bdeea318-a153-44b8-9e51-9155f3bad18b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b88c54a6fc8c33193af7573ebd9b7c9931d8fbe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690506"
---
# <a name="publication-properties-articles"></a><span data-ttu-id="5d4f1-102">发布属性，项目</span><span class="sxs-lookup"><span data-stu-id="5d4f1-102">Publication Properties, Articles</span></span>
  <span data-ttu-id="5d4f1-103">**“发布属性”** 对话框的 **“项目”** 页包含与发布中所包含项目有关的信息。使用该页，可以将项目添加到现有发布或从现有发布删除项目；并允许您更改项目属性和列筛选。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-103">The **Articles** page of the **Publication Properties** dialog box: contains information about the articles contained in a publication; allows you to add articles to and drop articles from existing publications; and allows you to change article properties and column filtering.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d4f1-104">创建发布之后，某些属性更改要求新的快照。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-104">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="5d4f1-105">如果发布具有多个订阅，某些更改还会要求重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-105">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="5d4f1-106">有关详细信息，请参阅[更改发布和项目属性](publish/change-publication-and-article-properties.md)和[向现有发布添加项目和从中删除项目](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-106">For more information, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
 <span data-ttu-id="5d4f1-107">如果发布的数据库对象依赖于一个或多个其他数据库对象，则必须发布所有被引用对象。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-107">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="5d4f1-108">例如，如果要发布的视图依赖于一个表，则也必须发布该表。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-108">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="5d4f1-109">无法发布的对象旁边有一个红色图标，并在向导页底部的信息面板中附有说明。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-109">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="5d4f1-110">无法发布下列对象：</span><span class="sxs-lookup"><span data-stu-id="5d4f1-110">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="5d4f1-111">加密的对象。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-111">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="5d4f1-112">包含允许 Null 的列的索引视图。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-112">Indexed views containing columns that allow NULL.</span></span>  
  
-   <span data-ttu-id="5d4f1-113">无法在事务发布中发布没有主键的表。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-113">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="5d4f1-114">在为排队更新订阅启用的合并发布和事务发布中，无法发布表。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-114">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="5d4f1-115">有关在多个发布中发布项目的详细信息，请参阅[发布数据和数据库对象](publish/publish-data-and-database-objects.md)中的“在多个发布中发布表”部分。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-115">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="5d4f1-116">Oracle 发布服务器</span><span class="sxs-lookup"><span data-stu-id="5d4f1-116">Oracle Publishers</span></span>  
 <span data-ttu-id="5d4f1-117">Oracle 发布服务器的其他注意事项：</span><span class="sxs-lookup"><span data-stu-id="5d4f1-117">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="5d4f1-118">有关 Oracle 发布服务器可以发布的对象的列表，请参阅 [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-118">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="5d4f1-119">无法发布的对象不会显示。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-119">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="5d4f1-120">有关可以发布的数据类型的列表，请参阅 [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-120">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="5d4f1-121">带有无法发布的数据类型的列不会显示。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-121">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="5d4f1-122">列筛选器</span><span class="sxs-lookup"><span data-stu-id="5d4f1-122">Column Filters</span></span>  
 <span data-ttu-id="5d4f1-123">通过展开 **“要发布的对象”** 窗格中的表，然后只选择需要的列，可以对此页上的列进行筛选（可以在此向导的 **“筛选表行”** 页上筛选行）。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-123">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="5d4f1-124">由于包括安全（防止复制敏感数据）和性能（例如，避免复制较大的二进制大型对象 (BLOB) 列）在内的很多原因，筛选列非常有用。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-124">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="5d4f1-125">有关列筛选（包括无法筛选的列类型的列表）的详细信息，请参阅[筛选已发布数据](publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-125">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d4f1-126">选项</span><span class="sxs-lookup"><span data-stu-id="5d4f1-126">Options</span></span>  
 <span data-ttu-id="5d4f1-127">使用 **“要发布的对象”** 窗格，可以：</span><span class="sxs-lookup"><span data-stu-id="5d4f1-127">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="5d4f1-128">查看所有可用于复制的对象。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-128">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="5d4f1-129">通过选中该对象旁边的复选框，可以将项目添加到发布。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-129">Add an article to a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="5d4f1-130">通过清除该对象旁边的复选框，可以从发布删除项目。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-130">Drop an article from a publication by clearing the check box next to that object.</span></span> <span data-ttu-id="5d4f1-131">有关何时可以删除项目的信息，请参阅[向现有发布添加项目和从中删除项目](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-131">For information about when articles can be dropped, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="5d4f1-132">通过选中对象类型（如 **“表”** ）旁边的复选框，将特定类型（如表）的所有对象包括在发布中。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-132">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="5d4f1-133">展开表节点可以查看表中的列。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-133">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="5d4f1-134">通过清除列旁边的复选框来从发布中筛选表列，或通过选中该复选框来包含未发布的列。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-134">Filter table columns out of a publication by clearing the check box next to the column or include unpublished columns by selecting the check box.</span></span>  
  
-   <span data-ttu-id="5d4f1-135">右键单击窗格中的对象可以查看该对象的命令菜单。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-135">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="5d4f1-136">**项目属性**</span><span class="sxs-lookup"><span data-stu-id="5d4f1-136">**Article Properties**</span></span>  
 <span data-ttu-id="5d4f1-137">单击 **“项目属性”** ，再单击下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="5d4f1-137">Click **Article Properties** , and then click one of the following:</span></span>  
  
-   <span data-ttu-id="5d4f1-138">单击“设置突出显示的 \<ObjectType> 的属性”以启动“项目属性 - \<ObjectName>”对话框；在此对话框中进行的属性更改仅应用于在“项目”页上的对象窗格中突出显示的对象  。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-138">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="5d4f1-139">单击“设置所有 \<ObjectType> 项目的属性”以启动“所有 \<ObjectType> 项目的属性”对话框；在此对话框中进行的属性更改应用于“项目”页上的对象窗格中该类型的所有对象，包括尚未选择进行发布的对象  。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-139">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d4f1-140">在“所有 \<ObjectType> 项目的属性”对话框中进行的属性更改会重写以前在“项目属性 - \<ObjectName>”对话框中进行的任何更改 。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-140">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="5d4f1-141">例如，若要为某对象类型的所有项目设置一些默认值，但还希望为单个对象设置一些属性，请首先设置所有项目的默认值。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-141">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="5d4f1-142">然后再设置单个对象的属性。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-142">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="5d4f1-143">**已选中的表仅用于下载**</span><span class="sxs-lookup"><span data-stu-id="5d4f1-143">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="5d4f1-144">仅限合并复制。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-144">Merge replication only.</span></span> <span data-ttu-id="5d4f1-145">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="5d4f1-146">选择此项可以指定在使用客户端订阅后不允许在订阅服务器上进行更改。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-146">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="5d4f1-147">因为仅供下载的项目不能在订阅服务器上更新，所以跟踪元数据不会发送到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-147">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="5d4f1-148">这可以减少订阅服务器上的存储量并提高性能，特别是当网络连接较慢时。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-148">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="5d4f1-149">此选项对应于 **“项目属性”** 对话框中的选项 **“同步方向”** 的值 **“仅下载到订阅服务器，禁止订阅服务器更改”** 。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-149">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="5d4f1-150">有关详细信息，请参阅[使用仅下载项目优化合并复制性能](merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-150">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="5d4f1-151">**仅显示列表中已选中的对象**</span><span class="sxs-lookup"><span data-stu-id="5d4f1-151">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="5d4f1-152">选中此复选框可以只显示对象窗格中选定的项目。</span><span class="sxs-lookup"><span data-stu-id="5d4f1-152">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4f1-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d4f1-153">See Also</span></span>  
 <span data-ttu-id="5d4f1-154">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="5d4f1-154">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="5d4f1-155">[查看和修改发布属性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5d4f1-155">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="5d4f1-156">[创建并应用初始快照](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="5d4f1-156">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="5d4f1-157">[重新初始化订阅](reinitialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="5d4f1-157">[Reinitialize a Subscription](reinitialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="5d4f1-158">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="5d4f1-158">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
