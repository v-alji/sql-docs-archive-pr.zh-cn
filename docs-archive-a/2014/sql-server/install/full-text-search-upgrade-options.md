---
title: 全文搜索升级选项 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Full-Text Search
- Upgrade options, Full-Text Search
ms.assetid: 16c9376b-5fbb-4495-a429-06a2493849c9
author: rothja
ms.author: jroth
ms.openlocfilehash: ade7a05563598440c3fdc79dd4b3584f7f797d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688455"
---
# <a name="full-text-search-upgrade-options"></a><span data-ttu-id="7678b-102">全文搜索升级选项</span><span class="sxs-lookup"><span data-stu-id="7678b-102">Full-Text Search Upgrade Options</span></span>
  <span data-ttu-id="7678b-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导的“全文搜索升级选项”页选择用于此时要升级的数据库的全文搜索升级选项。</span><span class="sxs-lookup"><span data-stu-id="7678b-103">Use the Full-Text Search Upgrade Options page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to select the full-text search upgrade option to use for the databases that you are upgrading at this time.</span></span>  
  
 <span data-ttu-id="7678b-104">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，每个全文检索都驻留在属于文件组的全文目录中，它们均具有物理路径，并被视为数据库文件。</span><span class="sxs-lookup"><span data-stu-id="7678b-104">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] each full-text index resides in a full-text catalog that belongs to a filegroup, has a physical path, and is treated as a database file.</span></span> <span data-ttu-id="7678b-105">现在，全文目录是一个逻辑概念，即一个虚拟对象，引用一组全文索引。</span><span class="sxs-lookup"><span data-stu-id="7678b-105">Now, a full-text catalog is a logical concept-a virtual object-that refers to a group of full-text indexes.</span></span> <span data-ttu-id="7678b-106">因此，新的全文目录不会视为带有物理路径的数据库文件。</span><span class="sxs-lookup"><span data-stu-id="7678b-106">Therefore, a new full-text catalog is not treated as a database file with a physical path.</span></span> <span data-ttu-id="7678b-107">但是，在升级包含数据文件的所有全文目录期间，将在相同磁盘上创建新的文件组。</span><span class="sxs-lookup"><span data-stu-id="7678b-107">However, during upgrade of any full-text catalog that contains data files, a new filegroup is created on same disk.</span></span> <span data-ttu-id="7678b-108">这可以在升级后维护旧磁盘的 I/O 行为。</span><span class="sxs-lookup"><span data-stu-id="7678b-108">This maintains the old disk I/O behavior after upgrade.</span></span> <span data-ttu-id="7678b-109">该目录的所有全文检索均被放置到新的文件组中（如果存在根路径）。</span><span class="sxs-lookup"><span data-stu-id="7678b-109">Any full-text index from that catalog is placed in the new filegroup if the root path exists.</span></span> <span data-ttu-id="7678b-110">如果旧的全文目录路径无效，该升级则将全文检索保留在与基表相同的文件组中，或者保留在主文件组中（对于分区表）。</span><span class="sxs-lookup"><span data-stu-id="7678b-110">If the old full-text catalog path is invalid, the upgrade keeps the full-text index in the same filegroup as base table or, for a partitioned table, in the primary filegroup.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7678b-111">选项</span><span class="sxs-lookup"><span data-stu-id="7678b-111">Options</span></span>  
 <span data-ttu-id="7678b-112">升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]时，请选择下列全文升级选项之一。</span><span class="sxs-lookup"><span data-stu-id="7678b-112">When you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], choose one of the following full-text upgrade options.</span></span>  
  
 <span data-ttu-id="7678b-113">**导入**</span><span class="sxs-lookup"><span data-stu-id="7678b-113">**Import**</span></span>  
 <span data-ttu-id="7678b-114">导入全文目录。</span><span class="sxs-lookup"><span data-stu-id="7678b-114">Full-text catalogs are imported.</span></span> <span data-ttu-id="7678b-115">一般情况下，导入速度比重新生成速度要快很多。</span><span class="sxs-lookup"><span data-stu-id="7678b-115">Typically, import is significantly faster than rebuild.</span></span> <span data-ttu-id="7678b-116">例如，当仅使用一个 CPU 时，导入的运行速度比重新生成要快 10 倍左右。</span><span class="sxs-lookup"><span data-stu-id="7678b-116">For example, when using only one CPU, import runs about 10 times faster than rebuild.</span></span> <span data-ttu-id="7678b-117">不过，从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 导入的全文目录不能使用新的和增强的断字符，因此最终可能还是要重新生成全文目录。</span><span class="sxs-lookup"><span data-stu-id="7678b-117">However, a full-text catalog imported from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] does not use the new and enhanced word breakers, so you might want to rebuild your full-text catalogs eventually.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7678b-118">重新生成可以以多线程模式运行，如果可用的 CPU 在 10 个以上，且您允许重新生成操作使用所有这些 CPU，则重新生成操作的运行速度可能比导入更快。</span><span class="sxs-lookup"><span data-stu-id="7678b-118">Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.</span></span>  
  
 <span data-ttu-id="7678b-119">如果全文目录不可用，则会重新生成关联的全文检索。</span><span class="sxs-lookup"><span data-stu-id="7678b-119">If a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="7678b-120">此选项仅对 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 数据库可用。</span><span class="sxs-lookup"><span data-stu-id="7678b-120">This option is available for only [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] databases.</span></span>  
  
 <span data-ttu-id="7678b-121">有关导入全文检索的影响的信息，请参阅本主题后面的“有关选择全文升级选项的注意事项”。</span><span class="sxs-lookup"><span data-stu-id="7678b-121">For information about the impact of importing full-text index, see "Considerations for Choosing a Full-Text Upgrade Option," later in this topic.</span></span>  
  
 <span data-ttu-id="7678b-122">**重新生成**</span><span class="sxs-lookup"><span data-stu-id="7678b-122">**Rebuild**</span></span>  
 <span data-ttu-id="7678b-123">使用新的和增强的断字符重新生成全文目录。</span><span class="sxs-lookup"><span data-stu-id="7678b-123">Full-text catalogs are rebuilt using the new and enhanced word breakers.</span></span> <span data-ttu-id="7678b-124">重新生成索引可能需要许多时间，且升级后可能需要占用大量的 CPU 和内存。</span><span class="sxs-lookup"><span data-stu-id="7678b-124">Rebuilding indexes can take a lot of time, and a significant amount of CPU and memory might be required after the upgrade.</span></span>  
  
 <span data-ttu-id="7678b-125">**重置**</span><span class="sxs-lookup"><span data-stu-id="7678b-125">**Reset**</span></span>  
 <span data-ttu-id="7678b-126">重置全文目录。</span><span class="sxs-lookup"><span data-stu-id="7678b-126">Full-text catalogs are reset.</span></span> <span data-ttu-id="7678b-127">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]升级时，将删除全文目录文件，但会保留全文目录和全文检索的元数据。</span><span class="sxs-lookup"><span data-stu-id="7678b-127">When upgrading from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained.</span></span> <span data-ttu-id="7678b-128">在进行升级后，所有全文检索将禁用更改跟踪，并且不会自动启动爬网。</span><span class="sxs-lookup"><span data-stu-id="7678b-128">After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically.</span></span> <span data-ttu-id="7678b-129">在升级完成后，目录将保留为空，直至手动执行完全填充。</span><span class="sxs-lookup"><span data-stu-id="7678b-129">The catalog will remain empty until you manually issue a full population, after the upgrade completes.</span></span>  
  
 <span data-ttu-id="7678b-130">所有这些升级选项确保升级后的数据库从全文性能增强功能中完全受益。</span><span class="sxs-lookup"><span data-stu-id="7678b-130">All of these upgrade options ensure that upgraded databases benefit fully from full-text performance enhancements.</span></span>  
  
## <a name="considerations-for-choosing-a-full-text-upgrade-option"></a><span data-ttu-id="7678b-131">有关选择全文升级选项的注意事项</span><span class="sxs-lookup"><span data-stu-id="7678b-131">Considerations for Choosing a Full-Text Upgrade Option</span></span>  
 <span data-ttu-id="7678b-132">为升级选择升级选项时，请考虑以下几点：</span><span class="sxs-lookup"><span data-stu-id="7678b-132">When choosing the upgrade option for your upgrade, consider the following:</span></span>  
  
-   <span data-ttu-id="7678b-133">如何使用断字符？</span><span class="sxs-lookup"><span data-stu-id="7678b-133">How do you use word breakers?</span></span>  
  
     <span data-ttu-id="7678b-134">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的全文搜索服务包括断字符和词干分析器。</span><span class="sxs-lookup"><span data-stu-id="7678b-134">The full-text search service in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] includes word breakers and stemmers.</span></span> <span data-ttu-id="7678b-135">这可能更改 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中特定文本模式或方案的全文查询结果。</span><span class="sxs-lookup"><span data-stu-id="7678b-135">These might change the results of full-text queries from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] for a specific text pattern or scenario.</span></span> <span data-ttu-id="7678b-136">因此，在选择适当的升级选项时，如何使用断字符非常重要：</span><span class="sxs-lookup"><span data-stu-id="7678b-136">Therefore, how you use word breakers is important when choosing a suitable upgrade option:</span></span>  
  
    -   <span data-ttu-id="7678b-137">如果使用的全文语言的断字符未发生更改，或者撤回准确性对您来说并不重要，则适合导入。</span><span class="sxs-lookup"><span data-stu-id="7678b-137">If the word breakers of the full-text language you use did not change, or if recall accuracy is not critical to you, importing is suitable.</span></span> <span data-ttu-id="7678b-138">随后，如果遇到任何撤回问题，您只需通过重新生成全文目录即可升级到新的断字符。</span><span class="sxs-lookup"><span data-stu-id="7678b-138">Later, if you experience any recall issues, you can upgrade to the new word breakers simply by rebuilding your full-text catalogs.</span></span>  
  
    -   <span data-ttu-id="7678b-139">如果您关心撤回准确性，并使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]后已添加的断字符之一，则适合重新生成。</span><span class="sxs-lookup"><span data-stu-id="7678b-139">If you care about recall accuracy and you use one of the word breakers that were added after [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], rebuilding is suitable.</span></span>  
  
-   <span data-ttu-id="7678b-140">是否基于整数全文键列生成了任何全文检索？</span><span class="sxs-lookup"><span data-stu-id="7678b-140">Were any full-text indexes built on integer full-text key columns?</span></span>  
  
     <span data-ttu-id="7678b-141">重新生成执行内部优化，在某些情况下该优化可提高升级的全文检索的查询性能。</span><span class="sxs-lookup"><span data-stu-id="7678b-141">Rebuilding performs internal optimizations that improve the query performance of the upgraded full-text index in some cases.</span></span> <span data-ttu-id="7678b-142">具体来说，如果您具有的全文目录包含基表的全文键列为整数数据类型的全文检索，则重新生成将在升级后实现全文查询的理想性能。</span><span class="sxs-lookup"><span data-stu-id="7678b-142">Specifically, if you have full-text catalogs that contain full-text indexes for which the full-text key column of the base table is an integer data type, rebuilding achieves ideal performance of full-text queries after upgrade.</span></span> <span data-ttu-id="7678b-143">在这种情况下，我们强烈建议使用 **“重新生成”** 选项。</span><span class="sxs-lookup"><span data-stu-id="7678b-143">In this case, we highly recommend you to use the **Rebuild** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7678b-144">对于 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的全文索引，建议采用整数数据类型作为全文键列。</span><span class="sxs-lookup"><span data-stu-id="7678b-144">For full-text indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that the column serving as the full-text key be an integer data type.</span></span> <span data-ttu-id="7678b-145">有关详细信息，请参阅 [改进全文索引的性能](../../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="7678b-145">For more information, see [Improve the Performance of Full-Text Indexes](../../relational-databases/indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="7678b-146">使服务器实例处于联机状态的优先级是什么？</span><span class="sxs-lookup"><span data-stu-id="7678b-146">What is the priority for getting your server instance online?</span></span>  
  
     <span data-ttu-id="7678b-147">升级期间的导入或重新生成操作会占用很多 CPU 资源，这会延迟其余服务器实例的升级和联机。</span><span class="sxs-lookup"><span data-stu-id="7678b-147">Importing or rebuilding during upgrade takes a lot of CPU resources, which delays getting the rest of the server instance upgraded and online.</span></span> <span data-ttu-id="7678b-148">如果使服务器实例尽快处于联机状态非常重要，并且希望在升级后运行手动填充，则适合 **“重置”** 。</span><span class="sxs-lookup"><span data-stu-id="7678b-148">If getting the server instance online as soon as possible is important and if you are willing to run a manual population after the upgrade, **Reset** is suitable.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="7678b-149">其他资源</span><span class="sxs-lookup"><span data-stu-id="7678b-149">Additional Resources</span></span>  
  
