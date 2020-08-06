---
title: 为全文搜索配置和管理同义词库文件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67f0a5af7be4f41ce33692e5f28ad5adf676980c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694429"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a><span data-ttu-id="cb97a-102">为全文搜索配置和管理同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-102">Configure and Manage Thesaurus Files for Full-Text Search</span></span>
  <span data-ttu-id="cb97a-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，全文查询可以通过使用同义词库来搜索用户指定的字词的同义词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], full-text queries can search for synonyms of user-specified terms through the use of a thesaurus.</span></span> <span data-ttu-id="cb97a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *同义词库*为特定语言定义一组同义词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *thesaurus* defines a set of synonyms for a specific language.</span></span> <span data-ttu-id="cb97a-105">系统管理员可以定义两种形式的同义词：扩展集和替换集。</span><span class="sxs-lookup"><span data-stu-id="cb97a-105">System administrators can define two forms of synonyms: expansion sets and replacement sets.</span></span> <span data-ttu-id="cb97a-106">通过开发针对全文数据定制的同义词库，您可以有效地扩大对这些数据的全文查询的范围。</span><span class="sxs-lookup"><span data-stu-id="cb97a-106">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="cb97a-107">仅对所有 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 和 [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 查询以及指定 FORMSOF THESAURUS 子句的任意 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 查询执行同义词库匹配操作。</span><span class="sxs-lookup"><span data-stu-id="cb97a-107">Thesaurus matching occurs for all [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) queries and for any [CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) queries that specify the FORMSOF THESAURUS clause.</span></span>  
  
##  <a name="basic-tasks-for-setting-up-a-thesaurus-file"></a><a name="tasks"></a><span data-ttu-id="cb97a-108">设置同义词库文件的基本任务</span><span class="sxs-lookup"><span data-stu-id="cb97a-108">Basic Tasks for Setting Up a Thesaurus File</span></span>  
 <span data-ttu-id="cb97a-109">必须先为给定语言定义同义词库映射（同义词），才能使服务器实例上的全文搜索查询可以查找该语言的同义词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-109">Before full-text search queries on your server instance can look for synonyms in a given language, you must define thesaurus mappings (synonyms) for that language.</span></span> <span data-ttu-id="cb97a-110">必须手动配置每个同义词库以定义下面各项：</span><span class="sxs-lookup"><span data-stu-id="cb97a-110">Each thesaurus must be manually configured to define the following:</span></span>  
  
-   <span data-ttu-id="cb97a-111">标注字符设置</span><span class="sxs-lookup"><span data-stu-id="cb97a-111">Diacritics setting</span></span>  
  
     <span data-ttu-id="cb97a-112">对于给定的同义词库，所有搜索模式都是敏感的或不区分变体标记，如波形符 (**~**) 、锐音符号 (**？？？**) ，或元音**格式设置**为区分*大小*写或不*区分*重音 () 。</span><span class="sxs-lookup"><span data-stu-id="cb97a-112">For a given thesaurus, all search patterns are either sensitive or insensitive to diacritical marks such as a tilde (**~**), acute accent mark (**??**), or umlaut (**??**) (that is, *accent sensitive* or *accent insensitive*).</span></span> <span data-ttu-id="cb97a-113">例如，假设指定了 "caf？" 模式。</span><span class="sxs-lookup"><span data-stu-id="cb97a-113">For example, suppose you specify the pattern "caf??"</span></span> <span data-ttu-id="cb97a-114">替换为全文查询中的其他模式。</span><span class="sxs-lookup"><span data-stu-id="cb97a-114">to be replaced by other patterns in a full-text query.</span></span> <span data-ttu-id="cb97a-115">如果同义词库不区分重音，则全文搜索将替换模式 "caf？"。</span><span class="sxs-lookup"><span data-stu-id="cb97a-115">If the thesaurus is accent-insensitive, full-text search replaces the patterns "caf??"</span></span> <span data-ttu-id="cb97a-116">和“cafe”。</span><span class="sxs-lookup"><span data-stu-id="cb97a-116">and "cafe".</span></span> <span data-ttu-id="cb97a-117">如果同义词库区分重音，则全文搜索仅替换模式 "caf？"。</span><span class="sxs-lookup"><span data-stu-id="cb97a-117">If the thesaurus is accent-sensitive, full-text search replaces only the pattern "caf??".</span></span> <span data-ttu-id="cb97a-118">默认情况下，同义词库不区分重音。</span><span class="sxs-lookup"><span data-stu-id="cb97a-118">By default, a thesaurus is accent-insensitive.</span></span>  
  
-   <span data-ttu-id="cb97a-119">扩展集</span><span class="sxs-lookup"><span data-stu-id="cb97a-119">Expansion set</span></span>  
  
     <span data-ttu-id="cb97a-120">扩展集包含一组同义词（如“writer”、“author”和“journalist”），全文查询可将这些同义词互相替换。</span><span class="sxs-lookup"><span data-stu-id="cb97a-120">An expansion set contains a group of synonyms such as "writer", "author", and "journalist" that are substituted for one another by a full-text query.</span></span> <span data-ttu-id="cb97a-121">如果查询包含扩展集中任意同义词的匹配项，这些查询将进行扩展以包含扩展集中的每个其他同义词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-121">Queries that contain a match for any synonym in an expansion set are expanded to include every other synonym in the expansion set.</span></span>  
  
     <span data-ttu-id="cb97a-122">有关详细信息，请参阅本主题后面的“扩展集的 XML 结构”。</span><span class="sxs-lookup"><span data-stu-id="cb97a-122">For more information, see "XML Structure of an Expansion Set," later in this topic.</span></span>  
  
-   <span data-ttu-id="cb97a-123">替换集</span><span class="sxs-lookup"><span data-stu-id="cb97a-123">Replacement set</span></span>  
  
     <span data-ttu-id="cb97a-124">替换集包含将由替换集替换的文本模式。</span><span class="sxs-lookup"><span data-stu-id="cb97a-124">A replacement set contains a text pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="cb97a-125">有关示例，请参阅本主题后面的“替换集的 XML 结构”部分。</span><span class="sxs-lookup"><span data-stu-id="cb97a-125">For an example, see the section "XML Structure of a Replacement Set" later in this topic.</span></span>  
  
  
##  <a name="initial-content-of-the-thesaurus-files"></a><a name="initial_thesaurus_files"></a><span data-ttu-id="cb97a-126">同义词库文件的初始内容</span><span class="sxs-lookup"><span data-stu-id="cb97a-126">Initial Content of the Thesaurus Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cb97a-127">提供了一组 XML 同义词库文件，分别对应于每种支持的语言。</span><span class="sxs-lookup"><span data-stu-id="cb97a-127">provides a set of XML thesaurus files, one for each supported language.</span></span> <span data-ttu-id="cb97a-128">这些文件实际上是空的。</span><span class="sxs-lookup"><span data-stu-id="cb97a-128">These files are essentially empty.</span></span> <span data-ttu-id="cb97a-129">它们仅包含所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 同义词库通用的顶级 XML 结构以及注释掉的示例同义词库。</span><span class="sxs-lookup"><span data-stu-id="cb97a-129">They contain only the top-level XML structure that is common to all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] thesauruses and a commented-out sample thesaurus.</span></span>  
  
 <span data-ttu-id="cb97a-130">随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发行的同义词库文件均包含以下 XML 代码：</span><span class="sxs-lookup"><span data-stu-id="cb97a-130">The thesaurus files that are released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all contain the following XML code:</span></span>  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location-of-the-thesaurus-files"></a><a name="location"></a><span data-ttu-id="cb97a-131">同义词库文件的位置</span><span class="sxs-lookup"><span data-stu-id="cb97a-131">Location of the Thesaurus Files</span></span>  
 <span data-ttu-id="cb97a-132">同义词库文件的默认位置为：</span><span class="sxs-lookup"><span data-stu-id="cb97a-132">The default location of the thesaurus files is:</span></span>  
  
 <span data-ttu-id="cb97a-133">*<SQL_Server_data_files_path>* \MSSQL12。MSSQLSERVER\MSSQL\FTDATA</span><span class="sxs-lookup"><span data-stu-id="cb97a-133">*<SQL_Server_data_files_path>* \MSSQL12.MSSQLSERVER\MSSQL\FTDATA</span></span>\  
  
 <span data-ttu-id="cb97a-134">该默认位置包含以下文件：</span><span class="sxs-lookup"><span data-stu-id="cb97a-134">This default location contains the following files:</span></span>  
  
-   <span data-ttu-id="cb97a-135">特定于语言的同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-135">Language-specific thesaurus files</span></span>  
  
     <span data-ttu-id="cb97a-136">在安装过程中，将在上述位置安装空同义词库文件。</span><span class="sxs-lookup"><span data-stu-id="cb97a-136">During setup, empty thesaurus files are installed in the above location.</span></span> <span data-ttu-id="cb97a-137">对于每种支持的语言，将提供一个单独的文件。</span><span class="sxs-lookup"><span data-stu-id="cb97a-137">A separate file is provided for each supported language.</span></span> <span data-ttu-id="cb97a-138">系统管理员可以自定义这些文件。</span><span class="sxs-lookup"><span data-stu-id="cb97a-138">A system administrator can customize these files.</span></span>  
  
     <span data-ttu-id="cb97a-139">同义词库文件的默认文件名采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="cb97a-139">The default file names of the thesaurus files use following format:</span></span>  
  
     <span data-ttu-id="cb97a-140">"ts" + \<three-letter language-abbreviation> + ".xml"</span><span class="sxs-lookup"><span data-stu-id="cb97a-140">'ts' + \<three-letter language-abbreviation> + '.xml'</span></span>  
  
     <span data-ttu-id="cb97a-141">给定语言的同义词库文件名称是在注册表中的下列值中指定的：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev>。</span><span class="sxs-lookup"><span data-stu-id="cb97a-141">The name of the thesaurus file for a given language is specified in the registry in the following value HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev>.</span></span>  
  
-   <span data-ttu-id="cb97a-142">全局同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-142">The global thesaurus file</span></span>  
  
     <span data-ttu-id="cb97a-143">空的全局同义词库文件 tsGlobal.xml。</span><span class="sxs-lookup"><span data-stu-id="cb97a-143">An empty global thesaurus file, tsGlobal.xml.</span></span>  
  
 <span data-ttu-id="cb97a-144">可通过更改同义词库文件的注册表项来更改其位置和名称。</span><span class="sxs-lookup"><span data-stu-id="cb97a-144">You can change the location and names of a thesaurus file by changing its registry key.</span></span> <span data-ttu-id="cb97a-145">对于每种语言，同义词库文件位置是在注册表的以下值中指定的：</span><span class="sxs-lookup"><span data-stu-id="cb97a-145">For each language, the location of the thesaurus file is specified in the following value in the registry:</span></span>  
  
 <span data-ttu-id="cb97a-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/ \<instance name> /MSSearch/Language/ \<language-abbreviation> /TsaurusFile</span><span class="sxs-lookup"><span data-stu-id="cb97a-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<instance name>/MSSearch/Language/\<language-abbreviation>/TsaurusFile</span></span>  
  
 <span data-ttu-id="cb97a-147">全局同义词库文件对应于 LCID 为 0 的非特定语言。</span><span class="sxs-lookup"><span data-stu-id="cb97a-147">The global thesaurus file corresponds to the Neutral language with LCID 0.</span></span> <span data-ttu-id="cb97a-148">此值只能由管理员更改。</span><span class="sxs-lookup"><span data-stu-id="cb97a-148">This value can be changed by administrators only.</span></span>  
  
  
##  <a name="how-queries-use-thesaurus-files"></a><a name="how_queries_use_tf"></a><span data-ttu-id="cb97a-149">查询如何使用同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-149">How Queries Use Thesaurus Files</span></span>  
 <span data-ttu-id="cb97a-150">同义词库查询同时使用特定于语言的同义词库和全局同义词库。</span><span class="sxs-lookup"><span data-stu-id="cb97a-150">A thesaurus query uses both a language-specific thesaurus and the global thesaurus.</span></span> <span data-ttu-id="cb97a-151">首先，查询查找特定于语言的文件，并加载该文件以进行处理（除非已加载了该文件）。</span><span class="sxs-lookup"><span data-stu-id="cb97a-151">First, the query looks up the language-specific file and loads it for processing (unless it is already loaded).</span></span> <span data-ttu-id="cb97a-152">该查询将进行扩展以包含同义词库文件中的扩展集和替换集规则所指定的特定于语言的同义词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-152">The query is expanded to include the language-specific synonyms specified by the expansion set and replacement set rules in the thesaurus file.</span></span> <span data-ttu-id="cb97a-153">然后，对全局同义词库重复执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="cb97a-153">These steps are then repeated for the global thesaurus.</span></span> <span data-ttu-id="cb97a-154">但是，如果字词已经是特定于语言的同义词库文件中的匹配项的一部分，则不会在全局同义词库中对该字词再次进行匹配。</span><span class="sxs-lookup"><span data-stu-id="cb97a-154">However, if a term is already part of a match in the language specific thesaurus file, the term is ineligible for matching in the global thesaurus.</span></span>  
  
  
##  <a name="understanding-the-structure-of-a-thesaurus-file"></a><a name="structure"></a><span data-ttu-id="cb97a-155">了解同义词库文件的结构</span><span class="sxs-lookup"><span data-stu-id="cb97a-155">Understanding the Structure of a Thesaurus File</span></span>  
 <span data-ttu-id="cb97a-156">每个同义词库文件都定义了一个 ID 为 `Microsoft Search Thesaurus` 的 XML 容器，以及一个包含示例同义词库的注释 `<!--`...`-->`。</span><span class="sxs-lookup"><span data-stu-id="cb97a-156">Each thesaurus file defines an XML container whose ID is `Microsoft Search Thesaurus`, and a comment, `<!--` ... `-->`, that contains a sample thesaurus.</span></span> <span data-ttu-id="cb97a-157">同义词库是在元素中定义 \<thesaurus> 的，该元素包含定义音调符号设置、扩展集和替换集的子元素的示例，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb97a-157">The thesaurus is defined in a \<thesaurus> element that contains samples of the child elements that define the diacritics setting, expansion sets, and replacement sets, as follows:</span></span>  
  
-   <span data-ttu-id="cb97a-158">标注字符设置的 XML 结构</span><span class="sxs-lookup"><span data-stu-id="cb97a-158">XML Structure of the Diacritical Setting</span></span>  
  
     <span data-ttu-id="cb97a-159">同义词库的标注字符设置是在单个 <diacritics_sensitive> 元素中指定的。</span><span class="sxs-lookup"><span data-stu-id="cb97a-159">The diacritics setting of a thesaurus is specified in a single <diacritics_sensitive> element.</span></span> <span data-ttu-id="cb97a-160">此元素包含一个控制重音区分设置的整数值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb97a-160">This element contains an integer value that controls accent sensitivity, as follows:</span></span>  
  
    |<span data-ttu-id="cb97a-161">标注字符设置</span><span class="sxs-lookup"><span data-stu-id="cb97a-161">Diacritics Setting</span></span>|<span data-ttu-id="cb97a-162">值</span><span class="sxs-lookup"><span data-stu-id="cb97a-162">Value</span></span>|<span data-ttu-id="cb97a-163">XML</span><span class="sxs-lookup"><span data-stu-id="cb97a-163">XML</span></span>|  
    |------------------------|-----------|---------|  
    |<span data-ttu-id="cb97a-164">不区分重音</span><span class="sxs-lookup"><span data-stu-id="cb97a-164">Accent insensitive</span></span>|<span data-ttu-id="cb97a-165">0</span><span class="sxs-lookup"><span data-stu-id="cb97a-165">0</span></span>|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |<span data-ttu-id="cb97a-166">区分重音</span><span class="sxs-lookup"><span data-stu-id="cb97a-166">Accent sensitive</span></span>|<span data-ttu-id="cb97a-167">1</span><span class="sxs-lookup"><span data-stu-id="cb97a-167">1</span></span>|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb97a-168">只能在文件中应用一次此设置，它适用于文件中的所有搜索模式。</span><span class="sxs-lookup"><span data-stu-id="cb97a-168">This setting can only be applied one time in the file, and it applies to all search patterns in the file.</span></span> <span data-ttu-id="cb97a-169">不能为各个模式单独指定此设置。</span><span class="sxs-lookup"><span data-stu-id="cb97a-169">This setting cannot be specified for individual patterns.</span></span>  
  
-   <span data-ttu-id="cb97a-170">扩展集的 XML 结构</span><span class="sxs-lookup"><span data-stu-id="cb97a-170">XML Structure of an Expansion Set</span></span>  
  
     <span data-ttu-id="cb97a-171">每个扩展集包含在 \<expansion> 元素中。</span><span class="sxs-lookup"><span data-stu-id="cb97a-171">Each expansion set is enclosed within an \<expansion> element.</span></span> <span data-ttu-id="cb97a-172">在此元素中，可以在 \<sub> 元素中指定一个或多个替换项。</span><span class="sxs-lookup"><span data-stu-id="cb97a-172">Within this element, you specify one or more substitutions in a \<sub> element.</span></span> <span data-ttu-id="cb97a-173">在扩展集中，可以指定一组互为同义词的替换项。</span><span class="sxs-lookup"><span data-stu-id="cb97a-173">In the expansion set, you can specify a group of substitutions that are synonyms of each other.</span></span>  
  
     <span data-ttu-id="cb97a-174">例如，可以编辑扩展部分，以将替换项“writer”、“author”和“journalist”视为同义词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-174">For example, you can edit the expansion section to treat the substitutions "writer", "author", and "journalist" as synonyms.</span></span> <span data-ttu-id="cb97a-175">在一个替换项中包含匹配项的全文搜索查询将展开以包括扩展集中指定的所有其他替换项。</span><span class="sxs-lookup"><span data-stu-id="cb97a-175">full-text search queries that contain matches in one substitution are expanded to include all other substitutions specified in the expansion set.</span></span> <span data-ttu-id="cb97a-176">因此，在前面的示例中，如果对单词“author”发出 FORMS OF THESAURUS 或 FREETEXT 查询，全文搜索还会返回包含单词“writer”和“journalist”的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="cb97a-176">Therefore, in the preceding example, when you issue a FORMS OF THESAURUS or a FREETEXT query for the word "author", full-text search also returns search results containing the words "writer" and "journalist".</span></span>  
  
     <span data-ttu-id="cb97a-177">对于上述示例，您将看到如下所示的扩展集部分：</span><span class="sxs-lookup"><span data-stu-id="cb97a-177">This is what the expansion set section would look like for the above example:</span></span>  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   <span data-ttu-id="cb97a-178">替换集的 XML 结构</span><span class="sxs-lookup"><span data-stu-id="cb97a-178">XML Structure of a Replacement Set</span></span>  
  
     <span data-ttu-id="cb97a-179">每个替换集包含在 \<replacement> 元素中。</span><span class="sxs-lookup"><span data-stu-id="cb97a-179">Each replacement set is enclosed within a \<replacement> element.</span></span> <span data-ttu-id="cb97a-180">在此元素中，可以在 \<pat> 元素中指定一个或多个模式，还可以在 \<sub> 元素中指定零个或多个替换项，每个替换项对应于一个同义词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-180">Within this element you can specify one or more patterns in a \<pat> element and zero or more substitutions in \<sub> elements, one per synonym.</span></span> <span data-ttu-id="cb97a-181">可以指定要由替换集替换的模式。</span><span class="sxs-lookup"><span data-stu-id="cb97a-181">You can specify a pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="cb97a-182">模式和替换项可以包含一个或一组单词。</span><span class="sxs-lookup"><span data-stu-id="cb97a-182">Patterns and substitutions can contain a word, or a sequence of words.</span></span> <span data-ttu-id="cb97a-183">如果没有为某个模式指定任何替换项，则会导致从用户查询中删除该模式。</span><span class="sxs-lookup"><span data-stu-id="cb97a-183">If there is no substitution specified for a pattern, it has the effect of removing the pattern from the user query.</span></span>  
  
     <span data-ttu-id="cb97a-184">例如，假设您希望运行用替换项“Windows Server 2012”或“Windows 8.0”替换“Win8”模式的查询。</span><span class="sxs-lookup"><span data-stu-id="cb97a-184">For example, suppose you want queries for "Win8", the pattern, to be replaced by "Windows Server 2012" or "Windows 8.0", the substitutions.</span></span> <span data-ttu-id="cb97a-185">如果对“Win8”运行全文查询，全文搜索仅返回包含“Windows Server 2012”或“Windows 8.0”的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="cb97a-185">If you run a full-text query for "Win8", full-text search only returns search results containing "Windows Server 2012" or "Windows 8.0".</span></span> <span data-ttu-id="cb97a-186">它不会返回包含“Win8”的结果。</span><span class="sxs-lookup"><span data-stu-id="cb97a-186">It does not return results containing "Win8".</span></span> <span data-ttu-id="cb97a-187">这是因为模式“Win8”已经被模式“Windows Server 2012”和“Windows 8.0”替换。</span><span class="sxs-lookup"><span data-stu-id="cb97a-187">This is because the pattern "Win8" has been "replaced" by the patterns "Windows Server 2012" and "Windows 8.0".</span></span>  
  
     <span data-ttu-id="cb97a-188">对于上述示例，您将看到如下所示的替换集部分：</span><span class="sxs-lookup"><span data-stu-id="cb97a-188">This is what the replacement set section would look like for the above example:</span></span>  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="cb97a-189">如果有两个具有相似模式的替换集可匹配，则优先选用两者中的更长者。</span><span class="sxs-lookup"><span data-stu-id="cb97a-189">If you have two replacement sets with similar patterns being matched, the longer of the two takes precedence.</span></span> <span data-ttu-id="cb97a-190">例如，如果对“Internet Explorer online community”运行 FORMS OF THESAURUS 查询，并且有以下替换集，则“Internet Explorer”替换集的优先级别高于“Internet”的优先级别。</span><span class="sxs-lookup"><span data-stu-id="cb97a-190">For example, if you run a FORMS OF THESAURUS query for "Internet Explorer online community" and you have the following replacement sets, the "Internet Explorer" replacement set takes precedence over the "Internet" replacement set.</span></span> <span data-ttu-id="cb97a-191">因此，查询将作为“IE online community”或“IE 9 online community”进行处理。</span><span class="sxs-lookup"><span data-stu-id="cb97a-191">The query will therefore be processed as "IE online community" or "IE 9 online community".</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="cb97a-192">和</span><span class="sxs-lookup"><span data-stu-id="cb97a-192">and</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working-with-thesaurus-files"></a><a name="working_with_thesaurus_files"></a><span data-ttu-id="cb97a-193">使用同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-193">Working with Thesaurus Files</span></span>  
 <span data-ttu-id="cb97a-194">**编辑同义词库文件**</span><span class="sxs-lookup"><span data-stu-id="cb97a-194">**To edit a thesaurus file**</span></span>  
  
-   [<span data-ttu-id="cb97a-195">编辑同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-195">Editing a Thesaurus File</span></span>](#editing)  
  
 <span data-ttu-id="cb97a-196">**加载更新的同义词库文件**</span><span class="sxs-lookup"><span data-stu-id="cb97a-196">**To load an updated thesaurus file**</span></span>  
  
-   [<span data-ttu-id="cb97a-197">sp_fulltext_load_thesaurus_file (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cb97a-197">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 <span data-ttu-id="cb97a-198">**查看断字符的词汇切分结果、同义词库和非索引字表组合**</span><span class="sxs-lookup"><span data-stu-id="cb97a-198">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="cb97a-199">sys. dm_fts_parser &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="cb97a-199">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing-a-thesaurus-file"></a><a name="editing"></a><span data-ttu-id="cb97a-200">编辑同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-200">Editing a Thesaurus File</span></span>  
 <span data-ttu-id="cb97a-201">可通过编辑给定语言的同义词库文件（XML 文件）来配置该语言的同义词库。</span><span class="sxs-lookup"><span data-stu-id="cb97a-201">The thesaurus for a given language can be configured by editing its thesaurus file (an XML file).</span></span> <span data-ttu-id="cb97a-202">在安装过程中，将安装空的同义词库文件，其中仅包含 \<xml> 容器和注释掉的示例 \<thesaurus> 元素。</span><span class="sxs-lookup"><span data-stu-id="cb97a-202">During setup, empty thesaurus files that contain only the \<xml> container and a commented-out sample \<thesaurus> element are installed.</span></span> <span data-ttu-id="cb97a-203">为了使查找同义词的全文搜索查询正常工作，必须创建 \<thesaurus> 定义一组同义词的实际元素。</span><span class="sxs-lookup"><span data-stu-id="cb97a-203">In order for full-text search queries that look for synonyms to work properly, you must create an actual \<thesaurus> element that defines a set of synonyms.</span></span> <span data-ttu-id="cb97a-204">可以定义两种形式的同义词，即扩展集和替换集。</span><span class="sxs-lookup"><span data-stu-id="cb97a-204">You can define two forms of synonyms, expansion sets and replacement sets.</span></span>  
  
 <span data-ttu-id="cb97a-205">**同义词库文件的限制**</span><span class="sxs-lookup"><span data-stu-id="cb97a-205">**Restrictions for thesaurus files**</span></span>  
  
 <span data-ttu-id="cb97a-206">下面的限制适用于编辑同义词库文件：</span><span class="sxs-lookup"><span data-stu-id="cb97a-206">The following restrictions apply to editing a thesaurus file:</span></span>  
  
-   <span data-ttu-id="cb97a-207">只有系统管理员能够更新、修改或删除同义词库文件。</span><span class="sxs-lookup"><span data-stu-id="cb97a-207">Only system administrators can update, modify, or delete thesaurus files.</span></span>  
  
-   <span data-ttu-id="cb97a-208">使用文本编辑器工具编辑同义词库文件时，必须以 Unicode 格式保存这些文件，并且必须指定字节顺序标记。</span><span class="sxs-lookup"><span data-stu-id="cb97a-208">When editing thesaurus files using text editor tools, the files must be saved in Unicode format, and Byte Order Marks must be specified.</span></span>  
  
-   <span data-ttu-id="cb97a-209">同义词库项不能为空或断字为空字符串。</span><span class="sxs-lookup"><span data-stu-id="cb97a-209">Thesaurus entries cannot be empty or word break to an empty string.</span></span>  
  
-   <span data-ttu-id="cb97a-210">同义词库文件中的短语长度不得超过 512 个字符。</span><span class="sxs-lookup"><span data-stu-id="cb97a-210">Phrases in the thesaurus file must be no longer than 512 characters.</span></span>  
  
-   <span data-ttu-id="cb97a-211">同义词库不能在扩展集的 \<sub> 项和替换集的 \<pat> 元素中包含任何重复项。</span><span class="sxs-lookup"><span data-stu-id="cb97a-211">A thesaurus must not contain any duplicate entries among the \<sub> entries of expansion sets and the \<pat> elements of replacement sets.</span></span>  
  
 <span data-ttu-id="cb97a-212">**针对同义词库文件的建议**</span><span class="sxs-lookup"><span data-stu-id="cb97a-212">**Recommendations for thesaurus files**</span></span>  
  
 <span data-ttu-id="cb97a-213">建议同义词库文件中的项不要包含任何特殊字符。</span><span class="sxs-lookup"><span data-stu-id="cb97a-213">We recommend that entries in the thesaurus file contain no special characters.</span></span> <span data-ttu-id="cb97a-214">这是因为，断字符在遇到特殊字符时会出现不确定的行为。</span><span class="sxs-lookup"><span data-stu-id="cb97a-214">This is because word breakers have subtle behaviors with respect to special characters.</span></span> <span data-ttu-id="cb97a-215">如果同义词库项包含任何特殊字符，在全文查询中与该项一起使用的断字符会出现不确定的行为。</span><span class="sxs-lookup"><span data-stu-id="cb97a-215">If a thesaurus entry contains any special characters, word breakers used in combination with that entry can have subtle behavioral implications for a full-text query.</span></span>  
  
 <span data-ttu-id="cb97a-216">建议不要在 \<sub> 项中包含任何非索引字，因为全文检索中将省略非索引字。</span><span class="sxs-lookup"><span data-stu-id="cb97a-216">We recommend that \<sub> entries contain no stopwords since stopwords are omitted from the full-text index.</span></span> <span data-ttu-id="cb97a-217">查询将进行扩展以包含同义词库文件中的 \<sub> 项，如果 \<sub> 项包含非索引字，则会不必要地增加查询大小。</span><span class="sxs-lookup"><span data-stu-id="cb97a-217">Queries are expanded to include the \<sub> entries from a thesaurus file, and if a \<sub> entry contains stopwords, query size increases unnecessarily.</span></span>  
  
#### <a name="to-edit-a-thesaurus-file"></a><span data-ttu-id="cb97a-218">编辑同义词库文件</span><span class="sxs-lookup"><span data-stu-id="cb97a-218">To edit a thesaurus file</span></span>  
  
1.  <span data-ttu-id="cb97a-219">在记事本中打开同义词库文件。</span><span class="sxs-lookup"><span data-stu-id="cb97a-219">Open the thesaurus file in Notepad.</span></span>  
  
2.  <span data-ttu-id="cb97a-220">如果第一次编辑同义词库文件，请分别删除位于文件开头和末尾的以下注释行：</span><span class="sxs-lookup"><span data-stu-id="cb97a-220">If you are editing the thesaurus file for the first time, remove the following comment lines at the beginning and end of the file, respectively:</span></span>  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  <span data-ttu-id="cb97a-221">添加、修改或删除替换集，或扩展集。</span><span class="sxs-lookup"><span data-stu-id="cb97a-221">Add, modify, or delete a replacement set, or expansion set.</span></span>  
  
4.  <span data-ttu-id="cb97a-222">保存文件并关闭记事本。</span><span class="sxs-lookup"><span data-stu-id="cb97a-222">Save the file and close Notepad.</span></span>  
  
5.  <span data-ttu-id="cb97a-223">使用 [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) 将同义词库文件内容加载到 tempdb 中，并指定对应于同义词库文件语言的本地标识符 (LCID)。</span><span class="sxs-lookup"><span data-stu-id="cb97a-223">Use [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) to load the content of the thesaurus file into tempdb, specifying the local identifier (LCID) that corresponds to the language of the thesaurus file.</span></span> <span data-ttu-id="cb97a-224">例如，对于英语同义词库文件 tsenu.xml，对应的 LCID 为 1033。</span><span class="sxs-lookup"><span data-stu-id="cb97a-224">For example, for the English thesaurus file, tsenu.xml, the corresponding LCID is 1033.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a><span data-ttu-id="cb97a-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb97a-225">See Also</span></span>  
 <span data-ttu-id="cb97a-226">[CONTAINS (Transact-SQL)](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb97a-226">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="cb97a-227">[CONTAINSTABLE (Transact-SQL)](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb97a-227">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="cb97a-228">[FREETEXT (Transact-SQL)](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb97a-228">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="cb97a-229">[FREETEXTTABLE (Transact-SQL)](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb97a-229">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 [<span data-ttu-id="cb97a-230">全文搜索</span><span class="sxs-lookup"><span data-stu-id="cb97a-230">Full-Text Search</span></span>](full-text-search.md)  
  
  
