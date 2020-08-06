---
title: " (\"常规\" 页) 的全文目录属性 |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
author: rothja
ms.author: jroth
ms.openlocfilehash: 483601c53db6c8a806ea8c53f771fd4f2608293b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693046"
---
# <a name="full-text-catalog-properties-general-page"></a><span data-ttu-id="a0495-102">全文目录属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="a0495-102">Full-Text Catalog Properties (General Page)</span></span>
  <span data-ttu-id="a0495-103">本节介绍在 **“全文目录属性”** 对话框的 **“常规”** 页上可用的选项和功能。</span><span class="sxs-lookup"><span data-stu-id="a0495-103">This section shows the options and functions available on the **General** page of the **Full-Text Catalog Properties** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0495-104">对于 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 数据库，全文目录是表示一组全文索引的逻辑概念。</span><span class="sxs-lookup"><span data-stu-id="a0495-104">For [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] databases, a full-text catalog is a logical concept that refers to a group of full-text indexes.</span></span> <span data-ttu-id="a0495-105">全文目录是虚拟对象，不属于任何文件组。</span><span class="sxs-lookup"><span data-stu-id="a0495-105">The full-text catalog is a virtual object that does not belong to any filegroup.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a0495-106">选项</span><span class="sxs-lookup"><span data-stu-id="a0495-106">Options</span></span>  
  
### <a name="properties"></a><span data-ttu-id="a0495-107">属性</span><span class="sxs-lookup"><span data-stu-id="a0495-107">Properties</span></span>  
 <span data-ttu-id="a0495-108">**默认目录**</span><span class="sxs-lookup"><span data-stu-id="a0495-108">**Default Catalog**</span></span>  
 <span data-ttu-id="a0495-109">显示目录是否为数据库的默认目录。</span><span class="sxs-lookup"><span data-stu-id="a0495-109">Displays whether the catalog is the default catalog for the database.</span></span>  
  
 <span data-ttu-id="a0495-110">**填充状态**</span><span class="sxs-lookup"><span data-stu-id="a0495-110">**Population Status**</span></span>  
 <span data-ttu-id="a0495-111">指示目录的状态。</span><span class="sxs-lookup"><span data-stu-id="a0495-111">Indicates the status of the catalog.</span></span> <span data-ttu-id="a0495-112">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="a0495-112">Possible values are:</span></span>  
  
-   <span data-ttu-id="a0495-113">**空闲**</span><span class="sxs-lookup"><span data-stu-id="a0495-113">**Idle**</span></span>  
  
-   <span data-ttu-id="a0495-114">**正在进行爬网**</span><span class="sxs-lookup"><span data-stu-id="a0495-114">**Crawl in Progress**</span></span>  
  
-   <span data-ttu-id="a0495-115">**已暂停**</span><span class="sxs-lookup"><span data-stu-id="a0495-115">**Paused**</span></span>  
  
-   <span data-ttu-id="a0495-116">**已中止**</span><span class="sxs-lookup"><span data-stu-id="a0495-116">**Throttled**</span></span>  
  
-   <span data-ttu-id="a0495-117">**恢复**</span><span class="sxs-lookup"><span data-stu-id="a0495-117">**Recovering**</span></span>  
  
-   <span data-ttu-id="a0495-118">关机</span><span class="sxs-lookup"><span data-stu-id="a0495-118">**Shutdown**</span></span>  
  
-   <span data-ttu-id="a0495-119">**正在进行增量填充**</span><span class="sxs-lookup"><span data-stu-id="a0495-119">**Incremental population in progress**</span></span>  
  
-   <span data-ttu-id="a0495-120">**正在生成索引**</span><span class="sxs-lookup"><span data-stu-id="a0495-120">**Building index**</span></span>  
  
-   <span data-ttu-id="a0495-121">**磁盘已满-已暂停**</span><span class="sxs-lookup"><span data-stu-id="a0495-121">**Disk is full-Paused**</span></span>  
  
-   <span data-ttu-id="a0495-122">**Change tracking**</span><span class="sxs-lookup"><span data-stu-id="a0495-122">**Change tracking**</span></span>  
  
 <span data-ttu-id="a0495-123">**项计数**</span><span class="sxs-lookup"><span data-stu-id="a0495-123">**Item Count**</span></span>  
 <span data-ttu-id="a0495-124">显示目录中的全文项数。</span><span class="sxs-lookup"><span data-stu-id="a0495-124">Displays the number of full-text items in the catalog.</span></span>  
  
 <span data-ttu-id="a0495-125">**目录大小**</span><span class="sxs-lookup"><span data-stu-id="a0495-125">**Catalog Size**</span></span>  
 <span data-ttu-id="a0495-126">显示全文目录的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="a0495-126">Displays the size, in megabytes, of the full-text catalog.</span></span>  
  
 <span data-ttu-id="a0495-127">**名称**</span><span class="sxs-lookup"><span data-stu-id="a0495-127">**Name**</span></span>  
 <span data-ttu-id="a0495-128">全文目录的名称。</span><span class="sxs-lookup"><span data-stu-id="a0495-128">The name of the full-text catalog.</span></span>  
  
 <span data-ttu-id="a0495-129">**区分重音**</span><span class="sxs-lookup"><span data-stu-id="a0495-129">**Accent Sensitive**</span></span>  
 <span data-ttu-id="a0495-130">查看或修改目录是否对变音标记敏感，如波形符 (**~**) 、锐音符 (\*\*") \*\*) 或元音变音符 () **¨** 。</span><span class="sxs-lookup"><span data-stu-id="a0495-130">View or modify whether the catalog is sensitive to diacritical marks, such as a tilde (**~**), acute accent mark (**´**), or umlaut (**¨**).</span></span> <span data-ttu-id="a0495-131">有效值是：</span><span class="sxs-lookup"><span data-stu-id="a0495-131">Valid values are:</span></span>  
  
-   <span data-ttu-id="a0495-132">**否**</span><span class="sxs-lookup"><span data-stu-id="a0495-132">**No**</span></span>  
  
-   <span data-ttu-id="a0495-133">**是**</span><span class="sxs-lookup"><span data-stu-id="a0495-133">**Yes**</span></span>  
  
-   <span data-ttu-id="a0495-134">有关发音符号的信息，请参阅 Merriam-Webster 字典中的[音调符号](https://www.merriam-webster.com/dictionary/diacritic)。</span><span class="sxs-lookup"><span data-stu-id="a0495-134">For information about diacritical marks, see [Diacritic](https://www.merriam-webster.com/dictionary/diacritic) in the Merriam-Webster dictionary.</span></span>  
  
 <span data-ttu-id="a0495-135">**上次填充日期**</span><span class="sxs-lookup"><span data-stu-id="a0495-135">**Last Population Date**</span></span>  
 <span data-ttu-id="a0495-136">显示上次填充目录的日期。</span><span class="sxs-lookup"><span data-stu-id="a0495-136">Displays the date the catalog was last populated.</span></span>  
  
 <span data-ttu-id="a0495-137">**所有者**</span><span class="sxs-lookup"><span data-stu-id="a0495-137">**Owner**</span></span>  
 <span data-ttu-id="a0495-138">全文目录的所有者。</span><span class="sxs-lookup"><span data-stu-id="a0495-138">The owner of the full-text catalog.</span></span>  
  
 <span data-ttu-id="a0495-139">**唯一键计数**</span><span class="sxs-lookup"><span data-stu-id="a0495-139">**Unique Key Count**</span></span>  
 <span data-ttu-id="a0495-140">组成目录的全文索引的唯一词条的数目。</span><span class="sxs-lookup"><span data-stu-id="a0495-140">The number of unique words that make up the full-text index for the catalog.</span></span>  
  
### <a name="catalog-action"></a><span data-ttu-id="a0495-141">目录操作</span><span class="sxs-lookup"><span data-stu-id="a0495-141">Catalog Action</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0495-142">**无**</span><span class="sxs-lookup"><span data-stu-id="a0495-142">**None**</span></span>|<span data-ttu-id="a0495-143">不执行 **“优化目录”**、 **“重新生成目录”** 或 **“重新填充目录”** 操作。</span><span class="sxs-lookup"><span data-stu-id="a0495-143">Does not perform **Optimize catalog**, **Rebuild catalog**, or **Repopulate catalog** operations.</span></span>|  
|<span data-ttu-id="a0495-144">**“优化目录”**</span><span class="sxs-lookup"><span data-stu-id="a0495-144">**Optimize catalog**</span></span>|<span data-ttu-id="a0495-145">优化目录的空间利用率，从而提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="a0495-145">Optimizes the space utilization of the catalog and improves query performance.</span></span> <span data-ttu-id="a0495-146">它还可提高搜索结果相关排名的准确性。</span><span class="sxs-lookup"><span data-stu-id="a0495-146">It also improves the accuracy of relevance ranking of search results.</span></span><br /><br /> <span data-ttu-id="a0495-147">该操作执行 ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE。</span><span class="sxs-lookup"><span data-stu-id="a0495-147">This action executes ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE.</span></span>|  
|<span data-ttu-id="a0495-148">**“重新生成目录”**</span><span class="sxs-lookup"><span data-stu-id="a0495-148">**Rebuild catalog**</span></span>|<span data-ttu-id="a0495-149">删除并重新生成全文目录。</span><span class="sxs-lookup"><span data-stu-id="a0495-149">Deletes and rebuilds the full-text catalog.</span></span> <span data-ttu-id="a0495-150">如果更改了基本目录属性（如区分重音），则必须执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a0495-150">This operation must be performed if a fundamental catalog property is changed, such as accent sensitivity.</span></span><br /><br /> <span data-ttu-id="a0495-151">全文目录所在的文件组必须为联机或可读写状态，重新生成才可成功。</span><span class="sxs-lookup"><span data-stu-id="a0495-151">For the rebuild to succeed, the filegroup the full-text catalog resides in must be online or read-writeable.</span></span> <span data-ttu-id="a0495-152">重新生成后，全文索引将重新填充。</span><span class="sxs-lookup"><span data-stu-id="a0495-152">After the rebuild, the full-text index will be repopulated.</span></span><br /><br /> <span data-ttu-id="a0495-153">该操作执行 ALTER FULLTEXT CATALOG *catalog_name* REBUILD。</span><span class="sxs-lookup"><span data-stu-id="a0495-153">This action executes ALTER FULLTEXT CATALOG *catalog_name* REBUILD.</span></span>|  
|<span data-ttu-id="a0495-154">**“重新填充目录”**</span><span class="sxs-lookup"><span data-stu-id="a0495-154">**Repopulate catalog**</span></span>|<span data-ttu-id="a0495-155">使用数据的最新更改来更新目录。</span><span class="sxs-lookup"><span data-stu-id="a0495-155">Updates the catalog with recent changes to the data.</span></span> <span data-ttu-id="a0495-156">使用此选项并不要求停用目录。</span><span class="sxs-lookup"><span data-stu-id="a0495-156">This option does require catalog downtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0495-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0495-157">See Also</span></span>  
 [<span data-ttu-id="a0495-158">填充全文索引</span><span class="sxs-lookup"><span data-stu-id="a0495-158">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
