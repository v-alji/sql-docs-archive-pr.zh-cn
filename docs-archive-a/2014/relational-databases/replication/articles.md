---
title: 项目 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.articles.f1
ms.assetid: 7c743dc6-6c6d-4c92-b711-842e1b0b273e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91336314a9538633af7c528d756d8461f7e8fe13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693771"
---
# <a name="articles"></a><span data-ttu-id="119ad-102">项目</span><span class="sxs-lookup"><span data-stu-id="119ad-102">Articles</span></span>
  <span data-ttu-id="119ad-103">在 **“项目”** 页中，可以指定要作为项目包含在发布中的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="119ad-103">On the **Articles** page, you specify which database objects to include as articles in the publication.</span></span> <span data-ttu-id="119ad-104">如果发布的数据库对象依赖于一个或多个其他数据库对象，则必须发布所有被引用对象。</span><span class="sxs-lookup"><span data-stu-id="119ad-104">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="119ad-105">例如，如果要发布的视图依赖于一个表，则也必须发布该表。</span><span class="sxs-lookup"><span data-stu-id="119ad-105">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="119ad-106">无法发布的对象旁边有一个红色图标，并在向导页底部的信息面板中附有说明。</span><span class="sxs-lookup"><span data-stu-id="119ad-106">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="119ad-107">无法发布下列对象：</span><span class="sxs-lookup"><span data-stu-id="119ad-107">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="119ad-108">加密的对象。</span><span class="sxs-lookup"><span data-stu-id="119ad-108">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="119ad-109">无法在事务发布中发布没有主键的表。</span><span class="sxs-lookup"><span data-stu-id="119ad-109">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="119ad-110">在为排队更新订阅启用的合并发布和事务发布中，无法发布表。</span><span class="sxs-lookup"><span data-stu-id="119ad-110">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="119ad-111">有关在多个发布中发布项目的详细信息，请参阅[发布数据和数据库对象](publish/publish-data-and-database-objects.md)中的“在多个发布中发布表”部分。</span><span class="sxs-lookup"><span data-stu-id="119ad-111">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="119ad-112">Oracle 发布服务器</span><span class="sxs-lookup"><span data-stu-id="119ad-112">Oracle Publishers</span></span>  
 <span data-ttu-id="119ad-113">Oracle 发布服务器的其他注意事项：</span><span class="sxs-lookup"><span data-stu-id="119ad-113">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="119ad-114">有关 Oracle 发布服务器可以发布的对象的列表，请参阅 [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="119ad-114">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="119ad-115">无法发布的对象不会显示。</span><span class="sxs-lookup"><span data-stu-id="119ad-115">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="119ad-116">有关可以发布的数据类型的列表，请参阅 [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="119ad-116">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="119ad-117">带有无法发布的数据类型的列不会显示。</span><span class="sxs-lookup"><span data-stu-id="119ad-117">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="119ad-118">列筛选器</span><span class="sxs-lookup"><span data-stu-id="119ad-118">Column Filters</span></span>  
 <span data-ttu-id="119ad-119">通过展开 **“要发布的对象”** 窗格中的表，然后只选择需要的列，可以对此页上的列进行筛选（可以在此向导的 **“筛选表行”** 页上筛选行）。</span><span class="sxs-lookup"><span data-stu-id="119ad-119">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="119ad-120">由于包括安全（防止复制敏感数据）和性能（例如，避免复制较大的二进制大型对象 (BLOB) 列）在内的很多原因，筛选列非常有用。</span><span class="sxs-lookup"><span data-stu-id="119ad-120">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="119ad-121">有关列筛选（包括无法筛选的列类型的列表）的详细信息，请参阅[筛选已发布数据](publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="119ad-121">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="119ad-122">选项</span><span class="sxs-lookup"><span data-stu-id="119ad-122">Options</span></span>  
 <span data-ttu-id="119ad-123">使用 **“要发布的对象”** 窗格，可以：</span><span class="sxs-lookup"><span data-stu-id="119ad-123">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="119ad-124">查看所有可用于复制的对象。</span><span class="sxs-lookup"><span data-stu-id="119ad-124">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="119ad-125">通过选中对象旁边的复选框可以将相应的对象添加到发布中。</span><span class="sxs-lookup"><span data-stu-id="119ad-125">Include an object in a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="119ad-126">通过选中对象类型（如 **“表”** ）旁边的复选框，将特定类型（如表）的所有对象包括在发布中。</span><span class="sxs-lookup"><span data-stu-id="119ad-126">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="119ad-127">展开表节点可以查看表中的列。</span><span class="sxs-lookup"><span data-stu-id="119ad-127">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="119ad-128">通过清除列旁边的复选框可以将表列从发布中筛除。</span><span class="sxs-lookup"><span data-stu-id="119ad-128">Filter table columns out of a publication by clearing the check box next to the column.</span></span>  
  
-   <span data-ttu-id="119ad-129">右键单击窗格中的对象可以查看该对象的命令菜单。</span><span class="sxs-lookup"><span data-stu-id="119ad-129">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="119ad-130">**项目属性**</span><span class="sxs-lookup"><span data-stu-id="119ad-130">**Article Properties**</span></span>  
 <span data-ttu-id="119ad-131">单击“项目属性” ，再单击下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="119ad-131">Click **Article Properties**, and then click one of the following:</span></span>  
  
-   <span data-ttu-id="119ad-132">单击“设置突出显示的 \<ObjectType> 项目的属性”以启动“项目属性 - \<ObjectName>”对话框；在此对话框中进行的属性更改仅应用于在“项目”页上的对象窗格中突出显示的对象。  </span><span class="sxs-lookup"><span data-stu-id="119ad-132">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="119ad-133">单击“设置所有 \<ObjectType> 项目的属性”以启动“所有 \<ObjectType> 项目的属性”对话框；在此对话框中进行的属性更改应用于“项目”页上的对象窗格中该类型的所有对象，包括尚未选择进行发布的对象。  </span><span class="sxs-lookup"><span data-stu-id="119ad-133">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="119ad-134">在“所有 \<ObjectType> 项目的属性”对话框中进行的属性更改会替代之前在“项目属性 - \<ObjectName>”对话框中进行的任何更改。 </span><span class="sxs-lookup"><span data-stu-id="119ad-134">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="119ad-135">例如，若要为某对象类型的所有项目设置一些默认值，但还希望为单个对象设置一些属性，请首先设置所有项目的默认值。</span><span class="sxs-lookup"><span data-stu-id="119ad-135">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="119ad-136">然后再设置单个对象的属性。</span><span class="sxs-lookup"><span data-stu-id="119ad-136">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="119ad-137">**已选中的表仅用于下载**</span><span class="sxs-lookup"><span data-stu-id="119ad-137">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="119ad-138">仅限合并复制。</span><span class="sxs-lookup"><span data-stu-id="119ad-138">Merge replication only.</span></span> <span data-ttu-id="119ad-139">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="119ad-139">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="119ad-140">选择此项可以指定在使用客户端订阅后不允许在订阅服务器上进行更改。</span><span class="sxs-lookup"><span data-stu-id="119ad-140">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="119ad-141">因为仅供下载的项目不能在订阅服务器上更新，所以跟踪元数据不会发送到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="119ad-141">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="119ad-142">这可以减少订阅服务器上的存储量并提高性能，特别是当网络连接较慢时。</span><span class="sxs-lookup"><span data-stu-id="119ad-142">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="119ad-143">此选项对应于 **“项目属性”** 对话框中的选项 **“同步方向”** 的值 **“仅下载到订阅服务器，禁止订阅服务器更改”** 。</span><span class="sxs-lookup"><span data-stu-id="119ad-143">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="119ad-144">有关详细信息，请参阅[使用仅下载项目优化合并复制性能](merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="119ad-144">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="119ad-145">**仅显示列表中已选中的对象**</span><span class="sxs-lookup"><span data-stu-id="119ad-145">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="119ad-146">选中此复选框可以只显示对象窗格中选定的项目。</span><span class="sxs-lookup"><span data-stu-id="119ad-146">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119ad-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="119ad-147">See Also</span></span>  
 <span data-ttu-id="119ad-148">[发布数据和数据库对象](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="119ad-148">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="119ad-149">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="119ad-149">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="119ad-150">查看和修改发布属性</span><span class="sxs-lookup"><span data-stu-id="119ad-150">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)  
  
  
