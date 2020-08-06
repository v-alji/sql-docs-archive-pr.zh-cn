---
title: 使用搜索属性列表搜索文档属性 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- full-text search [SQL Server], properties
- search property lists [SQL Server]
- property searching [SQL Server], about
- full-text indexes [SQL Server], search property lists
- search property lists [SQL Server], about
- property searching [SQL Server]
ms.assetid: ffae5914-b1b2-4267-b927-37e8382e0a9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16ab59a9fcdab29c927cb624dabcdfa71eaae1e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691171"
---
# <a name="search-document-properties-with-search-property-lists"></a><span data-ttu-id="8fc71-102">使用搜索属性列表搜索文档属性</span><span class="sxs-lookup"><span data-stu-id="8fc71-102">Search Document Properties with Search Property Lists</span></span>
  <span data-ttu-id="8fc71-103">文档属性的内容先前无法与文档正文的内容区分。</span><span class="sxs-lookup"><span data-stu-id="8fc71-103">The content of document properties was previously indistinguishable from the content of the document body.</span></span> <span data-ttu-id="8fc71-104">此局限性将全文查询限制为针对整个文档进行一般搜索。</span><span class="sxs-lookup"><span data-stu-id="8fc71-104">This limitation restricted full-text queries to generic searches on whole documents.</span></span> <span data-ttu-id="8fc71-105">但现在，对于 `varbinary`、`varbinary(max)`（包括 `FILESTREAM`）或 `image` 二进制数据列中支持的文档类型，您可以配置全文索引以支持对特定属性（如 Author 和 Title）进行属性范围内的搜索。</span><span class="sxs-lookup"><span data-stu-id="8fc71-105">Now, however, you can configure a full-text index to support property-scoped searching on particular properties, such as Author and Title, for supported document types in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` binary data column.</span></span> <span data-ttu-id="8fc71-106">这种形式的搜索称为“属性搜索”  。</span><span class="sxs-lookup"><span data-stu-id="8fc71-106">This form of searching is known as *property searching*.</span></span>  
  
 <span data-ttu-id="8fc71-107">关联的 [筛选器](configure-and-manage-filters-for-search.md) (IFilter) 确定能否针对指定的文档类型进行属性搜索。</span><span class="sxs-lookup"><span data-stu-id="8fc71-107">The associated [filter](configure-and-manage-filters-for-search.md) (IFilter) determines whether property searching is possible on a specific type of document.</span></span> <span data-ttu-id="8fc71-108">对于某些文档类型，关联的 IFilter 提取为该类型文档定义的某些或所有属性，以及文档正文的内容。</span><span class="sxs-lookup"><span data-stu-id="8fc71-108">For some document types, the associated IFilter extracts some or all of the properties defined for that type of document, as well as the content of the document body.</span></span> <span data-ttu-id="8fc71-109">您可以对全文索引进行配置，以便仅对全文索引期间 IFilter 提取的属性支持属性搜索。</span><span class="sxs-lookup"><span data-stu-id="8fc71-109">You can configure a full-text index to support property searching only on properties that are extracted by an IFilter during full-text indexing.</span></span> <span data-ttu-id="8fc71-110">在提取若干文档属性的 IFilter 中，包括用于提取 Microsoft Office 文档类型（如 .docx、.xlsx 和.pptx）的 IFilter。</span><span class="sxs-lookup"><span data-stu-id="8fc71-110">Among IFilters that extract a number of document properties are the IFilters for Microsoft Office document types (such as .docx, .xlsx, and .pptx).</span></span> <span data-ttu-id="8fc71-111">另一方面，XML IFilter 不发出属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-111">On the other hand, the XML IFilter does not emit properties.</span></span>  
  
##  <a name="how-full-text-search-works-with-search-properties"></a><a name="How_FTS_Works_with_search_properties"></a> <span data-ttu-id="8fc71-112">全文搜索如何与搜索属性一起使用</span><span class="sxs-lookup"><span data-stu-id="8fc71-112">How Full-Text Search Works with Search Properties</span></span>  
  
### <a name="internal-property-ids"></a><span data-ttu-id="8fc71-113">内部属性 ID</span><span class="sxs-lookup"><span data-stu-id="8fc71-113">Internal Property IDs</span></span>  
 <span data-ttu-id="8fc71-114">全文引擎任意向每个注册的属性分配一个内部属性 ID，这个 ID 在该特定搜索列表中唯一标识属性并且特定于该搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="8fc71-114">The Full-Text Engine arbitrarily assigns each registered property an internal property ID, which uniquely identifies the property in that particular search list and which is specific to that search property list.</span></span> <span data-ttu-id="8fc71-115">因此，如果某个属性添加到多个搜索属性列表中，则其内部属性 ID 很可能在不同列表之间是不同的。</span><span class="sxs-lookup"><span data-stu-id="8fc71-115">Therefore, if a property is added to multiple search property lists, its internal property ID is likely to differ between different lists.</span></span>  
  
 <span data-ttu-id="8fc71-116">在向某个搜索列表注册某一属性时，全文引擎向该属性任意分配一个内部属性 ID  。</span><span class="sxs-lookup"><span data-stu-id="8fc71-116">When a property is registered for a search list, the Full-Text Engine arbitrarily assigns an *internal property ID* to the property.</span></span> <span data-ttu-id="8fc71-117">该内部属性 ID 是在该搜索属性列表中唯一标识该属性的整数。</span><span class="sxs-lookup"><span data-stu-id="8fc71-117">The internal property ID is an integer that uniquely identifies the property in that search property list.</span></span>  
  
 <span data-ttu-id="8fc71-118">下图显示一个搜索属性列表的逻辑视图，该搜索属性列表指定两个属性：Title 和 Keywords。</span><span class="sxs-lookup"><span data-stu-id="8fc71-118">The following illustration shows a logical view of a search property list that specifies two properties, Title and Keywords.</span></span> <span data-ttu-id="8fc71-119">Keywords 的属性列表名称是“Tags”。</span><span class="sxs-lookup"><span data-stu-id="8fc71-119">The property-list name for Keywords is "Tags".</span></span> <span data-ttu-id="8fc71-120">这些属性属于其 GUID 为 F29F85E0-4FF9-1068-AB91-08002B27B3D9 的相同属性集。</span><span class="sxs-lookup"><span data-stu-id="8fc71-120">These properties belong to the same property set, whose GUID is F29F85E0-4FF9-1068-AB91-08002B27B3D9.</span></span> <span data-ttu-id="8fc71-121">属性整数标识符对于 Title 为 2，对于 Tags (Keywords) 为 5。</span><span class="sxs-lookup"><span data-stu-id="8fc71-121">The property integer identifiers are 2 for Title and 5 for Tags (Keywords).</span></span> <span data-ttu-id="8fc71-122">全文引擎任意将每个属性映射到在搜索属性列表中唯一的内部属性 ID。</span><span class="sxs-lookup"><span data-stu-id="8fc71-122">The Full-Text Engine arbitrarily maps each property to an internal property ID that is unique to the search property list.</span></span> <span data-ttu-id="8fc71-123">Title 属性的内部属性 ID 为 1，Tags 属性的内部属性 ID 为 2。</span><span class="sxs-lookup"><span data-stu-id="8fc71-123">The internal property ID for the Title property is 1, and the internal property ID for the Tags property is 2.</span></span>  
  
 <span data-ttu-id="8fc71-124">![搜索属性列表到内部表的映射](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "搜索属性列表到内部表的映射")</span><span class="sxs-lookup"><span data-stu-id="8fc71-124">![Mapping of search property list to internal table](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "Mapping of search property list to internal table")</span></span>  
  
 <span data-ttu-id="8fc71-125">内部属性 ID 很可能不同于该属性的属性整数标识符。</span><span class="sxs-lookup"><span data-stu-id="8fc71-125">The internal property ID is likely to be different from the property integer identifier of the property.</span></span> <span data-ttu-id="8fc71-126">如果为多个搜索属性列表注册给定属性，则可能会为每个搜索属性列表指定不同的内部属性 ID。</span><span class="sxs-lookup"><span data-stu-id="8fc71-126">If a given property is registered for multiple search property lists, a different internal property ID might be assigned for each search property list.</span></span> <span data-ttu-id="8fc71-127">例如，内部属性 ID 在一个搜索属性列表中可以是 4，在另一个列表中可以是 1，在其他列表中可以是 3，依此类推。</span><span class="sxs-lookup"><span data-stu-id="8fc71-127">For example, the internal property ID might be 4 in one search property list, 1 in another, 3 in another, and so on.</span></span> <span data-ttu-id="8fc71-128">相反，属性整数标识符是属性所有固有的，并且无论在哪里使用该属性其属性标识符都保持相同。</span><span class="sxs-lookup"><span data-stu-id="8fc71-128">In contrast, the property integer identifier is intrinsic to the property, and it remains the same wherever the property is used.</span></span>  
  
  
  
### <a name="indexing-of-registered-properties"></a><span data-ttu-id="8fc71-129">已注册属性的索引</span><span class="sxs-lookup"><span data-stu-id="8fc71-129">Indexing of Registered Properties</span></span>  
 <span data-ttu-id="8fc71-130">在某个全文索引与搜索属性列表相关联后，必须重新填充该索引以便对特定于属性的搜索词建立索引。</span><span class="sxs-lookup"><span data-stu-id="8fc71-130">After a full-text index is associated with a search property list, the index must be repopulated to index property-specific search terms.</span></span> <span data-ttu-id="8fc71-131">在全文索引期间，所有属性的内容都与其他内容一起存储于全文索引中。</span><span class="sxs-lookup"><span data-stu-id="8fc71-131">During full-text indexing, the contents of all properties are stored in the full-text index along with other content.</span></span> <span data-ttu-id="8fc71-132">但是，在对在某个已注册属性中找到的搜索词建立索引时，全文索引器还将相应的内部属性 ID 与该搜索词一起存储。</span><span class="sxs-lookup"><span data-stu-id="8fc71-132">However, when indexing a search term found in a registered property, the full-text indexer also stores the corresponding internal property ID with the term.</span></span> <span data-ttu-id="8fc71-133">相反，如果未注册某个属性，则该属性将存储于全文索引中，就像它是文档正文的一部分，并且对于内部属性 ID，该属性的值为零。</span><span class="sxs-lookup"><span data-stu-id="8fc71-133">In contrast, if a property is not registered, it is stored in the full-text index as if it were part of the document body, and it has a value of zero for the internal property ID.</span></span>  
  
 <span data-ttu-id="8fc71-134">下图显示一个逻辑视图，说明搜索词如何出现在与上图中所示的搜索属性列表相关联的全文索引中。</span><span class="sxs-lookup"><span data-stu-id="8fc71-134">The following illustration shows a logical view of how search terms appear in a full-text index that is associated with the search property list shown in the preceding illustration.</span></span> <span data-ttu-id="8fc71-135">示例文档 Document 1 包含三个属性（Title、Author 和 Keywords）以及文档正文。</span><span class="sxs-lookup"><span data-stu-id="8fc71-135">A sample document, Document 1 contains three properties-Title, Author, and Keywords-as well as the document body.</span></span> <span data-ttu-id="8fc71-136">对于在搜索属性列表中指定的属性 Title 和 Keywords，搜索词与其在全文索引中的相应内部属性 ID 相关联。</span><span class="sxs-lookup"><span data-stu-id="8fc71-136">For the properties Title and Keywords, which are specified in the search property list, search terms are associated with their corresponding internal property IDs in the full-text index.</span></span> <span data-ttu-id="8fc71-137">相反，将对 Author 属性的内容建立索引，就像它是文档正文的一部分。</span><span class="sxs-lookup"><span data-stu-id="8fc71-137">In contrast, the content of the Author property is indexed as if it were part of the document body.</span></span> <span data-ttu-id="8fc71-138">这意味着，注册某一属性将在一定程度上增加全文索引的大小，具体取决于属性中存储的内容量。</span><span class="sxs-lookup"><span data-stu-id="8fc71-138">This means registering a property increases the size of the full-text index somewhat, depending on the amount of content stored in the property.</span></span>  
  
 <span data-ttu-id="8fc71-139">![使用搜索属性列表的全文检索](../../database-engine/media/ifts-spl-and-fti.gif "使用搜索属性列表的全文检索")</span><span class="sxs-lookup"><span data-stu-id="8fc71-139">![Full-text index that uses a search property list](../../database-engine/media/ifts-spl-and-fti.gif "Full-text index that uses a search property list")</span></span>  
  
 <span data-ttu-id="8fc71-140">Title 属性中的搜索词（“Favorite”、“Biking”和“Trails”）与分配给此索引的 Title 的内部属性 ID (1) 相关联。</span><span class="sxs-lookup"><span data-stu-id="8fc71-140">Search terms in the Title property-"Favorite," "Biking," and "Trails"-are associated with the internal property ID assigned to Title for this index, 1.</span></span> <span data-ttu-id="8fc71-141">Keywords 属性中的搜索词（“biking”和“mountain”）与分配给此索引的 Tags 的内部属性 ID (2) 相关联。</span><span class="sxs-lookup"><span data-stu-id="8fc71-141">Search terms in the Keywords property-"biking" and "mountain"-are associated with the internal property ID assigned to Tags for this index, 2.</span></span> <span data-ttu-id="8fc71-142">对于 Author 属性（“Jane”和“Doe”）的搜索词 n 以及文档正文中的搜索词，该内部属性 ID 为 0。</span><span class="sxs-lookup"><span data-stu-id="8fc71-142">For search terms n the Author property-"Jane" and "Doe"-and search terms in the document body, the internal property ID is 0.</span></span> <span data-ttu-id="8fc71-143">请注意，“biking”一词在 Title 属性、Keywords (Tags) 属性以及文档正文中出现。</span><span class="sxs-lookup"><span data-stu-id="8fc71-143">Note that the term "biking" occurs in the Title property, in the Keywords (Tags) property, and in the document body.</span></span> <span data-ttu-id="8fc71-144">针对 Title 或 Keywords (Tags) 属性中“biking”的属性搜索将在结果中返回此文档。</span><span class="sxs-lookup"><span data-stu-id="8fc71-144">A property search for "biking" in the Title or Keywords (Tags) property would return this document in the results.</span></span> <span data-ttu-id="8fc71-145">针对“biking”的一般全文查询也将返回此文档，就像没有为属性搜索配置索引。</span><span class="sxs-lookup"><span data-stu-id="8fc71-145">A generic full-text query for "biking" would also return this document, just as if the index were not configured for property searching.</span></span> <span data-ttu-id="8fc71-146">在 Author 属性中针对“biking”的属性搜索将不返回此文档。</span><span class="sxs-lookup"><span data-stu-id="8fc71-146">A property search for "biking" in the Author property would not return this document.</span></span>  
  
 <span data-ttu-id="8fc71-147">属性范围的全文查询使用向全文索引的当前搜索属性列表注册的内部属性 ID。</span><span class="sxs-lookup"><span data-stu-id="8fc71-147">A property-scoped full-text query uses the internal property IDs registered for the current search property list of the full-text index.</span></span>  
  
  
  
##  <a name="impact-of-enabling-property-searching"></a><a name="impact"></a> <span data-ttu-id="8fc71-148">启用属性搜索的影响</span><span class="sxs-lookup"><span data-stu-id="8fc71-148">Impact of Enabling Property Searching</span></span>  
 <span data-ttu-id="8fc71-149">根据您在搜索属性列表中指定的属性的数目以及每个属性的内容，配置全文索引以便支持搜索一个或多个属性将在某种程度上增加索引的大小。</span><span class="sxs-lookup"><span data-stu-id="8fc71-149">Configuring a full-text index to support searching on one or more properties increases the size of the index somewhat, depending on the number of properties you specify in your search property list and on the content of each property.</span></span>  
  
 <span data-ttu-id="8fc71-150">在测试 Microsoft Word<sup>？？</sup>、Excel<sup>？？</sup>和 PowerPoint<sup>？</sup>的典型资料时</span><span class="sxs-lookup"><span data-stu-id="8fc71-150">In testing typical corpuses of Microsoft Word<sup>??</sup>, Excel<sup>??</sup>, and PowerPoint<sup>??</sup></span></span> <span data-ttu-id="8fc71-151">文档，我们配置了一个全文索引，用于索引典型的搜索属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-151">documents, we configured a full-text index to index typical search properties.</span></span> <span data-ttu-id="8fc71-152">对这些属性建立索引将全文索引的大小增加了大约 5%。</span><span class="sxs-lookup"><span data-stu-id="8fc71-152">Indexing these properties increased the size of the full-text index size by approximately 5 percent.</span></span> <span data-ttu-id="8fc71-153">我们预计这一大小上的增量对于大多数文档资料而言大致相近。</span><span class="sxs-lookup"><span data-stu-id="8fc71-153">We anticipate that this approximate size increase will to be typical for most document corpuses.</span></span> <span data-ttu-id="8fc71-154">不过，这个大小上的增量最终将取决于相对于整个数据量，给定文档资料中的属性数据量的比例。</span><span class="sxs-lookup"><span data-stu-id="8fc71-154">However, ultimately, the size increase will depend on the amount of property data in a given document corpus relative to the amount of overall data.</span></span>  
  
  
  
##  <a name="creating-a-search-property-list-and-enabling-property-search"></a><a name="creating"></a> <span data-ttu-id="8fc71-155">创建搜索属性列表并启用属性搜索</span><span class="sxs-lookup"><span data-stu-id="8fc71-155">Creating a Search Property List and Enabling Property Search</span></span>  
  
###  <a name="creating-a-search-property-list"></a><a name="creating_sub"></a><span data-ttu-id="8fc71-156">创建搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-156">Creating a Search Property List</span></span>  
 <span data-ttu-id="8fc71-157">**使用 Transact-SQL 创建搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="8fc71-157">**To create a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="8fc71-158">使用 [CREATE SEARCH PROPERTY LIST (Transact-SQL)](/sql/t-sql/statements/create-search-property-list-transact-sql) 语句并至少提供该列表中的一个名称。</span><span class="sxs-lookup"><span data-stu-id="8fc71-158">Use the [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) statement and provide at least a name the list.</span></span>  
  
##### <a name="to-create-a-search-property-list-in-management-studio"></a><span data-ttu-id="8fc71-159">在 Management Studio 中创建搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-159">To create a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="8fc71-160">在对象资源管理器中，展开服务器。</span><span class="sxs-lookup"><span data-stu-id="8fc71-160">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="8fc71-161">展开 **“数据库”**，然后展开要在其中创建搜索属性列表的数据库。</span><span class="sxs-lookup"><span data-stu-id="8fc71-161">Expand **Databases**, and then expand the database in which you want to create the search property list.</span></span>  
  
3.  <span data-ttu-id="8fc71-162">展开“存储”\*\*\*\*，然后右键单击“搜索属性列表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fc71-162">Expand **Storage**, and then right-click **Search Property Lists**.</span></span>  
  
4.  <span data-ttu-id="8fc71-163">选择 **“新建搜索属性列表”**。</span><span class="sxs-lookup"><span data-stu-id="8fc71-163">Select **New Search Property List**.</span></span>  
  
5.  <span data-ttu-id="8fc71-164">指定该属性列表的名称。</span><span class="sxs-lookup"><span data-stu-id="8fc71-164">Specify the property list name.</span></span>  
  
6.  <span data-ttu-id="8fc71-165">还可以选择将其他人指定为该属性列表的所有者。</span><span class="sxs-lookup"><span data-stu-id="8fc71-165">Optionally, specify someone else as the property list owner.</span></span>  
  
7.  <span data-ttu-id="8fc71-166">选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="8fc71-166">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="8fc71-167">**创建空的搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="8fc71-167">**Create an empty search property list**</span></span>  
  
    -   <span data-ttu-id="8fc71-168">**从现有搜索属性列表创建**</span><span class="sxs-lookup"><span data-stu-id="8fc71-168">**Create from an existing search property list**</span></span>  
  
     <span data-ttu-id="8fc71-169">有关详细信息，请参阅 [New Search Property List](../../database-engine/new-search-property-list.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc71-169">For more information, see [New Search Property List](../../database-engine/new-search-property-list.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 
  
###  <a name="adding-properties-to-a-search-property-list"></a><a name="adding"></a><span data-ttu-id="8fc71-170">将属性添加到搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-170">Adding Properties to a Search Property List</span></span>  
 <span data-ttu-id="8fc71-171">属性搜索要求创建“搜索属性列表” \*\* 并且指定您希望可供搜索的一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-171">Property searching requires creating a *search property list* and specifying one or more properties that you want to make searchable.</span></span> <span data-ttu-id="8fc71-172">在您向搜索属性列表添加某一属性时，将向该特定列表注册该属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-172">When you add a property to a search property list, the property is registered for that particular list.</span></span> <span data-ttu-id="8fc71-173">若要向搜索属性列表添加属性，您需要以下值：</span><span class="sxs-lookup"><span data-stu-id="8fc71-173">To add a property to a search property list you need the following values:</span></span>  
  
-   <span data-ttu-id="8fc71-174">属性集 GUID</span><span class="sxs-lookup"><span data-stu-id="8fc71-174">Property set GUID</span></span>  
  
     <span data-ttu-id="8fc71-175">每个搜索属性都属于包含一组相关属性的单个属性集。</span><span class="sxs-lookup"><span data-stu-id="8fc71-175">Each search property belongs to single property set that contains a group of related properties.</span></span> <span data-ttu-id="8fc71-176">每个属性集均由全局唯一标识符 (GUID) 标识。</span><span class="sxs-lookup"><span data-stu-id="8fc71-176">Each property set is identified by a globally unique identifier (GUID).</span></span>  
  
-   <span data-ttu-id="8fc71-177">属性整数标识符</span><span class="sxs-lookup"><span data-stu-id="8fc71-177">Property integer identifier</span></span>  
  
     <span data-ttu-id="8fc71-178">每个搜索属性都拥有在属性集内唯一的标识符。</span><span class="sxs-lookup"><span data-stu-id="8fc71-178">Each search property possesses an identifier that is unique within the property set.</span></span> <span data-ttu-id="8fc71-179">请注意，对于某一给定属性，该标识符可以是整数或字符串，但全文搜索仅支持整数标识符。</span><span class="sxs-lookup"><span data-stu-id="8fc71-179">Note that for a given property, the identifier could be either an integer or a string, however full-text search supports only integer identifiers.</span></span>  
  
-   <span data-ttu-id="8fc71-180">属性名称</span><span class="sxs-lookup"><span data-stu-id="8fc71-180">Property name</span></span>  
  
     <span data-ttu-id="8fc71-181">该名称是用户将在全文查询中为搜索属性指定的名称。</span><span class="sxs-lookup"><span data-stu-id="8fc71-181">This is the name that users will specify in full-text queries to search on the property.</span></span> <span data-ttu-id="8fc71-182">属性名称可以包含内部空格。</span><span class="sxs-lookup"><span data-stu-id="8fc71-182">A property name can contain internal spaces.</span></span> <span data-ttu-id="8fc71-183">最大长度为 256 个字符。</span><span class="sxs-lookup"><span data-stu-id="8fc71-183">The maximum length is 256 characters.</span></span>  
  
     <span data-ttu-id="8fc71-184">属性名称可以是以下任何项：</span><span class="sxs-lookup"><span data-stu-id="8fc71-184">The property name can be any of the following:</span></span>  
  
    -   <span data-ttu-id="8fc71-185">属性的 Windows 规范名称，例如 `System.Author` 或 `System.Contact.HomeAddress`。</span><span class="sxs-lookup"><span data-stu-id="8fc71-185">The Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span>  
  
    -   <span data-ttu-id="8fc71-186">便于您的用户记住的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="8fc71-186">A user-friendly name that is easy for your users to remember.</span></span> <span data-ttu-id="8fc71-187">某些属性与已知的用户友好名称（例如“Author”或“Home Address”）相关联，但您可以指定最适合您的用户的任何名称。</span><span class="sxs-lookup"><span data-stu-id="8fc71-187">Some properties are associated with a well-known user-friendly name, such as "Author" or "Home Address," but you can specify whatever name is most appropriate to your users.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8fc71-188">属性集 GUID 和属性标识符的给定组合在给定搜索属性列表内必须唯一。</span><span class="sxs-lookup"><span data-stu-id="8fc71-188">A given combination of property set GUID and property identifier must be unique in a given search property list.</span></span> <span data-ttu-id="8fc71-189">这意味着，您不能使用不同的名称或说明多次添加同一属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-189">This means that you cannot add the same property more than once with different names or descriptions.</span></span>  
  
-   <span data-ttu-id="8fc71-190">属性说明（可选）</span><span class="sxs-lookup"><span data-stu-id="8fc71-190">Property description (optional)</span></span>  
  
     <span data-ttu-id="8fc71-191">在您将某个搜索属性添加到搜索属性列表时，您可以提供可选说明。</span><span class="sxs-lookup"><span data-stu-id="8fc71-191">When adding a search property to a search property list, you can supply an optional description.</span></span> <span data-ttu-id="8fc71-192">例如，您可能要提供与其名称未表露其含义的属性有关的信息，或者您可能想要描述该属性的属性集。</span><span class="sxs-lookup"><span data-stu-id="8fc71-192">For example, you might want to provide information about a property that is not evident from its name, or you might want to describe the property set of the property.</span></span>  
  
 <span data-ttu-id="8fc71-193">**获取搜索属性列表的值**</span><span class="sxs-lookup"><span data-stu-id="8fc71-193">**To obtain values for a search property list**</span></span>  
  
 <span data-ttu-id="8fc71-194">请参阅 [查找搜索属性的属性集 GUID 和属性整数 ID](find-property-set-guids-and-property-integer-ids-for-search-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc71-194">See [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="8fc71-195">**使用 Transact-SQL 将属性添加到搜索属性列表中**</span><span class="sxs-lookup"><span data-stu-id="8fc71-195">**To add a property to a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="8fc71-196">通过借助主题中介绍的方法之一获得的值使用 [ALTER SEARCH PROPERTY LIST (Transact SQL)](/sql/t-sql/statements/alter-search-property-list-transact-sql) 语句，[查找搜索属性的属性集 GUID 和属性整数 ID](find-property-set-guids-and-property-integer-ids-for-search-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc71-196">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement with the values that you obtained by using one of the methods described in the topic, [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="8fc71-197">下面的示例演示在将属性添加到搜索属性列表时这些值的用法：</span><span class="sxs-lookup"><span data-stu-id="8fc71-197">The following example demonstrates the use of these values when adding a property to a search property list:</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST DocumentTablePropertyList  
   ADD 'Title'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
```  
  
 <span data-ttu-id="8fc71-198">**将属性添加到 Management Studio 中的搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="8fc71-198">**To add a property to a search property list in Management Studio**</span></span>  
  
 <span data-ttu-id="8fc71-199">使用 **“搜索属性列表属性”** 对话框以添加或删除搜索属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-199">Use the **Search Property List Properties** dialog box to add and remove search properties.</span></span> <span data-ttu-id="8fc71-200">在对象资源管理器中，您可以在关联数据库的 **“存储”** 节点下找到 **“搜索属性列表”** 。</span><span class="sxs-lookup"><span data-stu-id="8fc71-200">You can find **Search Property Lists** in Object Explorer under the **Storage** node of the associated database.</span></span>  
  
  
  
###  <a name="associating-a-search-property-list-with-a-full-text-index"></a><a name="associating"></a><span data-ttu-id="8fc71-201">将搜索属性列表与全文索引相关联</span><span class="sxs-lookup"><span data-stu-id="8fc71-201">Associating a Search Property List with a Full-Text Index</span></span>  
 <span data-ttu-id="8fc71-202">为使全文索引支持对向搜索属性列表注册的属性执行属性搜索，您需要将搜索属性列表与索引相关联并且重新填充该索引。</span><span class="sxs-lookup"><span data-stu-id="8fc71-202">For a full-text index to support property searching on the properties that are registered for a search property list, you need to associate the search property list with the index and repopulate the index.</span></span> <span data-ttu-id="8fc71-203">重新填充全文索引将为每个已注册属性中的搜索词创建特定于属性的索引条目。</span><span class="sxs-lookup"><span data-stu-id="8fc71-203">Repopulating the full-text index creates property-specific index entries for search terms in each of the registered properties.</span></span>  
  
 <span data-ttu-id="8fc71-204">只要全文索引保持与此搜索属性列表相关联，全文查询就可以使用 CONTAINS 谓词的 PROPERTY 选项来搜索为该搜索属性列表注册的属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-204">As long as the full-text index remains associated with this search property list, full-text query can use the PROPERTY option of the CONTAINS predicate to search on properties that are registered for that search property list.</span></span>  
  
 <span data-ttu-id="8fc71-205">如果您更改与全文索引关联的搜索属性列表，则该索引必须重新生成以使其进入一致状态。</span><span class="sxs-lookup"><span data-stu-id="8fc71-205">If you change the search property list associated with a full-text index, then the index must be rebuilt to bring it into a consistent state.</span></span> <span data-ttu-id="8fc71-206">将立即截断索引，并在运行完全填充之前保留为空。</span><span class="sxs-lookup"><span data-stu-id="8fc71-206">The index is truncated immediately and is empty until the full population runs.</span></span> <span data-ttu-id="8fc71-207">有关更改搜索属性列表在何时将导致重新生成索引的详细信息，请参阅 [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 中的“注释”。</span><span class="sxs-lookup"><span data-stu-id="8fc71-207">For more information about when changing the search property list causes rebuilding the index, see "Remarks," in [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="8fc71-208">**使用 Transact-SQL 将搜索属性列表与全文索引相关联**</span><span class="sxs-lookup"><span data-stu-id="8fc71-208">**To associate a search property list with a full-text index with Transact-SQL**</span></span>  
  
 <span data-ttu-id="8fc71-209">将 [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 语句和 `SET SEARCH PROPERTY LIST = <property_list_name>` 子句结合使用。</span><span class="sxs-lookup"><span data-stu-id="8fc71-209">Use the [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement with the `SET SEARCH PROPERTY LIST = <property_list_name>` clause.</span></span>  
  
 <span data-ttu-id="8fc71-210">**使用 Management Studio 将搜索属性列表与全文索引相关联**</span><span class="sxs-lookup"><span data-stu-id="8fc71-210">**To associate a search property list with a full-text index with Management Studio**</span></span>  
  
 <span data-ttu-id="8fc71-211">在“全文索引属性”\*\*\*\* 对话框的“常规”\*\*\*\* 页上，为“搜索属性列表”\*\*\*\* 指定一个值。</span><span class="sxs-lookup"><span data-stu-id="8fc71-211">Specify a value for **Search Property List** on the **General** page of the **Full-Text Index Properties** dialog box.</span></span>  
  
  
  
##  <a name="querying-search-properties-with-contains"></a><a name="Ov_CONTAINS_using_PROPERTY"></a> <span data-ttu-id="8fc71-212">使用 CONTAINS 查询搜索属性</span><span class="sxs-lookup"><span data-stu-id="8fc71-212">Querying Search Properties with CONTAINS</span></span>  
 <span data-ttu-id="8fc71-213">针对属性范围的全文查询的基本 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 语法如下：</span><span class="sxs-lookup"><span data-stu-id="8fc71-213">The basic [CONTAINS](/sql/t-sql/queries/contains-transact-sql) syntax for a property-scoped full-text query is as follows:</span></span>  
  
```sql  
SELECT column_name FROM table_name  
  WHERE CONTAINS ( PROPERTY ( column_name, 'property_name' ), '<contains_search_condition>' )  
```  
  
 <span data-ttu-id="8fc71-214">例如，下面的查询在 `Title`数据库的 `Document` 表的 `Production.Document` 列中搜索索引属性 `AdventureWorks` 。</span><span class="sxs-lookup"><span data-stu-id="8fc71-214">For example, the following query searches on an indexed property, `Title`, in the `Document` column of the `Production.Document` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="8fc71-215">该查询仅返回其 `Title` 属性包含字符串 `Maintenance` 或 `Repair`</span><span class="sxs-lookup"><span data-stu-id="8fc71-215">The query returns only documents whose `Title` property contains the string `Maintenance` or `Repair`</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT Document FROM Production.Document  
  WHERE CONTAINS ( PROPERTY ( Document, 'Title' ), 'Maintenance OR Repair')  
GO  
```  
  
 <span data-ttu-id="8fc71-216">该示例假定文档的 IFilter 提取其 Title 属性，然后将 Title 属性添加到搜索属性列表，并且搜索属性列表与全文索引相关联。</span><span class="sxs-lookup"><span data-stu-id="8fc71-216">This example assumes that the IFilter for the document extracts its Title property, that the Title property is added to the search property list, and that the search property list is associated with the full-text index.</span></span>  
  
  
  
##  <a name="managing-search-property-lists"></a><a name="managing"></a> <span data-ttu-id="8fc71-217">管理搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-217">Managing Search Property Lists</span></span>  
  
###  <a name="viewing-and-changing-a-search-property-list"></a><a name="viewing"></a> <span data-ttu-id="8fc71-218">查看和更改搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-218">Viewing and Changing a Search Property List</span></span>  
 <span data-ttu-id="8fc71-219">**使用 Transact-SQL 更改搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="8fc71-219">**To change a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="8fc71-220">使用 [ALTER SEARCH PROPERTY LIST (Transact-SQL)](/sql/t-sql/statements/alter-search-property-list-transact-sql) 语句添加或删除搜索属性。</span><span class="sxs-lookup"><span data-stu-id="8fc71-220">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add or remove search properties.</span></span>  
  
##### <a name="to-view-and-change-a-search-property-list-in-management-studio"></a><span data-ttu-id="8fc71-221">查看和更改 Management Studio 中的搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-221">To view and change a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="8fc71-222">在对象资源管理器中，展开服务器。</span><span class="sxs-lookup"><span data-stu-id="8fc71-222">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="8fc71-223">展开 **“数据库”**，然后展开数据库。</span><span class="sxs-lookup"><span data-stu-id="8fc71-223">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="8fc71-224">展开“存储”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fc71-224">Expand **Storage**.</span></span>  
  
4.  <span data-ttu-id="8fc71-225">展开 **“搜索属性列表”** 以显示搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="8fc71-225">Expand **Search Property Lists** to display the search property lists.</span></span>  
  
5.  <span data-ttu-id="8fc71-226">右键单击该属性列表，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fc71-226">Right-click the property list, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="8fc71-227">在 **“搜索属性列表编辑器”** 对话框中，使用“属性”网格添加或删除搜索属性：</span><span class="sxs-lookup"><span data-stu-id="8fc71-227">In the **Search Property List Editor** dialog box, use the Properties grid to add or remove search properties:</span></span>  
  
    1.  <span data-ttu-id="8fc71-228">若要删除某个文档属性，请单击该属性左侧的行标题，然后按 Del。</span><span class="sxs-lookup"><span data-stu-id="8fc71-228">To remove a document property, click the row header to the left of the property, and press DEL .</span></span>  
  
    2.  <span data-ttu-id="8fc71-229">若要添加文档属性，请单击列表底部的空行，然后在右侧单击 **\*** ，然后输入新属性的值。</span><span class="sxs-lookup"><span data-stu-id="8fc71-229">To add a document property, click in the empty row at the bottom of the list, to the right of the **\***, and enter the values for the new property.</span></span>  
  
         <span data-ttu-id="8fc71-230">有关这些值的信息，请参阅 [搜索属性列表编辑器](../../database-engine/search-property-list-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc71-230">For information about these values, see [Search Property List Editor](../../database-engine/search-property-list-editor.md).</span></span> <span data-ttu-id="8fc71-231">有关如何获取由 Microsoft 定义的属性的这些值的信息，请参阅 [查找搜索属性的属性集 GUID 和属性整数 ID](find-property-set-guids-and-property-integer-ids-for-search-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc71-231">For information about how to obtain these values for properties defined by Microsoft, see [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span> <span data-ttu-id="8fc71-232">有关由独立软件供应商 (ISV) 定义的属性的信息，请参阅该供应商提供的文档。</span><span class="sxs-lookup"><span data-stu-id="8fc71-232">For information about properties defined by an independent software vendor (ISV), see the documentation of that vendor.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
###  <a name="deleting-a-search-property-list"></a><a name="deleting"></a> <span data-ttu-id="8fc71-233">删除搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-233">Deleting a Search Property List</span></span>  
 <span data-ttu-id="8fc71-234">在属性列表与任何全文索引关联时，不能从数据库中删除该列表。</span><span class="sxs-lookup"><span data-stu-id="8fc71-234">You cannot drop a property list from a database while the list is associated with any full-text index.</span></span>  
  
 <span data-ttu-id="8fc71-235">**使用 Transact-SQL 删除搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="8fc71-235">**To delete a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="8fc71-236">使用 [DROP SEARCH PROPERTY LIST (Transact-SQL)](/sql/t-sql/statements/drop-search-property-list-transact-sql)语句。</span><span class="sxs-lookup"><span data-stu-id="8fc71-236">Use the [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-search-property-list-transact-sql) statement.</span></span>  
  
##### <a name="to-delete-a-search-property-list-in-management-studio"></a><span data-ttu-id="8fc71-237">删除 Management Studio 中的搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8fc71-237">To delete a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="8fc71-238">在对象资源管理器中，展开服务器。</span><span class="sxs-lookup"><span data-stu-id="8fc71-238">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="8fc71-239">展开 **“数据库”**，然后展开数据库。</span><span class="sxs-lookup"><span data-stu-id="8fc71-239">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="8fc71-240">展开 **“存储”**，然后展开 **“搜索属性列表”** 节点。</span><span class="sxs-lookup"><span data-stu-id="8fc71-240">Expand **Storage**, and then expand the **Search Property Lists** node.</span></span>  
  
4.  <span data-ttu-id="8fc71-241">右键单击要删除的属性列表，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fc71-241">Right-click the property list that you want to delete, and click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

  
## <a name="see-also"></a><span data-ttu-id="8fc71-242">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fc71-242">See Also</span></span>  
 <span data-ttu-id="8fc71-243">[查找搜索属性的属性集 Guid 和属性整数 Id](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8fc71-243">[Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span></span>  
 [<span data-ttu-id="8fc71-244">配置和管理搜索筛选器</span><span class="sxs-lookup"><span data-stu-id="8fc71-244">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
