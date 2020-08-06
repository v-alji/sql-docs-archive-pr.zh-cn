---
title: 全文搜索 DDL、函数、存储过程和视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 98c36715-4195-482e-a4a3-d93ff65b75f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 29b026ac60fd3f7d00ca519c4ced84533ce9740f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590145"
---
# <a name="full-text-search-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="10f86-102">全文搜索 DDL、函数、存储过程和视图</span><span class="sxs-lookup"><span data-stu-id="10f86-102">Full-Text Search DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="10f86-103">列出支持全文搜索（包括属性搜索功能）的 Transact-SQL 语句和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="10f86-103">Lists the Transact-SQL statements and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects that support full-text search, including the property search feature.</span></span>  
  
 <span data-ttu-id="10f86-104">此列表中不包括不推荐使用的对象。</span><span class="sxs-lookup"><span data-stu-id="10f86-104">This list does not include deprecated objects.</span></span>  
  
 <span data-ttu-id="10f86-105">有关支持语义搜索的数据库对象的列表，请参阅 [Semantic Search DDL, Functions, Stored Procedures, and Views](../views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="10f86-105">For the list of database objects that support semantic search, see [Semantic Search DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="10f86-106">Transact-SQL 数据定义语言 (DDL) 语句</span><span class="sxs-lookup"><span data-stu-id="10f86-106">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
-   [<span data-ttu-id="10f86-107">CREATE FULLTEXT CATALOG (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-107">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="10f86-108">CREATE FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-108">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="10f86-109">CREATE FULLTEXT STOPLIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-109">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
-   [<span data-ttu-id="10f86-110">CREATE SEARCH PROPERTY LIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-110">CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-search-property-list-transact-sql)  
  
-   [<span data-ttu-id="10f86-111">ALTER FULLTEXT CATALOG (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-111">ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="10f86-112">ALTER FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-112">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="10f86-113">ALTER FULLTEXT STOPLIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-113">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
-   [<span data-ttu-id="10f86-114">ALTER SEARCH PROPERTY LIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-114">ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-search-property-list-transact-sql)  
  
-   [<span data-ttu-id="10f86-115">DROP FULLTEXT CATALOG (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-115">DROP FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="10f86-116">DROP FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-116">DROP FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="10f86-117">DROP FULLTEXT STOPLIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-117">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
-   [<span data-ttu-id="10f86-118">DROP SEARCH PROPERTY LIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-118">DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-search-property-list-transact-sql)  
  
##  <a name="system-predicates-and-functions"></a><a name="func"></a> <span data-ttu-id="10f86-119">系统谓词和功能</span><span class="sxs-lookup"><span data-stu-id="10f86-119">System Predicates and Functions</span></span>  
  
-   [<span data-ttu-id="10f86-120">CONTAINS (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-120">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
-   [<span data-ttu-id="10f86-121">CONTAINSTABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-121">CONTAINSTABLE &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/containstable-transact-sql)  
  
-   [<span data-ttu-id="10f86-122">FREETEXT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-122">FREETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/freetext-transact-sql)  
  
-   [<span data-ttu-id="10f86-123">FREETEXTTABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-123">FREETEXTTABLE &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/freetexttable-transact-sql)  
  
##  <a name="system-metadata-functions"></a><a name="meta"></a> <span data-ttu-id="10f86-124">系统元数据函数</span><span class="sxs-lookup"><span data-stu-id="10f86-124">System Metadata Functions</span></span>  
  
-   [<span data-ttu-id="10f86-125">COLUMNPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-125">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)  
  
-   [<span data-ttu-id="10f86-126">FULLTEXTCATALOGPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-126">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)  
  
-   [<span data-ttu-id="10f86-127">FULLTEXTSERVICEPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-127">FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextserviceproperty-transact-sql)  
  
-   [<span data-ttu-id="10f86-128">INDEXPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-128">INDEXPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)  
  
-   [<span data-ttu-id="10f86-129">OBJECTPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-129">OBJECTPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectpropertyex-transact-sql)  
  
-   [<span data-ttu-id="10f86-130">OBJECTPROPERTYEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-130">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)  
  
-   [<span data-ttu-id="10f86-131">SERVERPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> <span data-ttu-id="10f86-132">系统存储过程</span><span class="sxs-lookup"><span data-stu-id="10f86-132">System Stored Procedures</span></span>  
  
-   [<span data-ttu-id="10f86-133">sp_fulltext_keymappings (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-133">sp_fulltext_keymappings &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql)  
  
-   [<span data-ttu-id="10f86-134">sp_fulltext_load_thesaurus_file (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-134">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
-   [<span data-ttu-id="10f86-135">sp_fulltext_pendingchanges (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-135">sp_fulltext_pendingchanges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql)  
  
-   [<span data-ttu-id="10f86-136">sp_fulltext_service (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-136">sp_fulltext_service &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)  
  
-   [<span data-ttu-id="10f86-137">sp_help_fulltext_system_components (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-137">sp_help_fulltext_system_components &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> <span data-ttu-id="10f86-138">系统视图 - 目录视图</span><span class="sxs-lookup"><span data-stu-id="10f86-138">System Views - Catalog Views</span></span>  
  
-   [<span data-ttu-id="10f86-139">sys.fulltext_catalogs (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-139">sys.fulltext_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql)  
  
-   [<span data-ttu-id="10f86-140">sys.fulltext_document_types (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-140">sys.fulltext_document_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql)  
  
-   [<span data-ttu-id="10f86-141">sys.fulltext_index_catalog_usages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-141">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)  
  
-   [<span data-ttu-id="10f86-142">sys.fulltext_index_columns (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-142">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
-   [<span data-ttu-id="10f86-143">sys.fulltext_index_fragments (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-143">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)  
  
-   [<span data-ttu-id="10f86-144">sys.fulltext_indexes (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-144">sys.fulltext_indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)  
  
-   [<span data-ttu-id="10f86-145">sys.fulltext_languages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-145">sys.fulltext_languages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)  
  
-   [<span data-ttu-id="10f86-146">sys.fulltext_stoplists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-146">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [<span data-ttu-id="10f86-147">sys.fulltext_stopwords (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-147">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
-   [<span data-ttu-id="10f86-148">sys.fulltext_system_stopwords (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-148">sys.fulltext_system_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql)  
  
-   [<span data-ttu-id="10f86-149">sys.registered_search_properties (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-149">sys.registered_search_properties &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql)  
  
-   [<span data-ttu-id="10f86-150">sys.registered_search_property_lists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-150">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="10f86-151">系统视图 - 动态管理视图</span><span class="sxs-lookup"><span data-stu-id="10f86-151">System Views - Dynamic Management Views</span></span>  
  
-   [<span data-ttu-id="10f86-152">sys.dm_fts_active_catalogs (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-152">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-active-catalogs-transact-sql)  
  
-   [<span data-ttu-id="10f86-153">sys.dm_fts_fdhosts (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-153">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-fdhosts-transact-sql)  
  
-   [<span data-ttu-id="10f86-154">sys.dm_fts_index_keywords (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-154">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)  
  
-   [<span data-ttu-id="10f86-155">sys.dm_fts_index_keywords_by_document (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-155">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)  
  
-   [<span data-ttu-id="10f86-156">sys.dm_fts_index_keywords_by_property (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-156">sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql)  
  
-   [<span data-ttu-id="10f86-157">sys.dm_fts_index_population (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)  
  
-   [<span data-ttu-id="10f86-158">sys.dm_fts_memory_buffers (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-158">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)  
  
-   [<span data-ttu-id="10f86-159">sys.dm_fts_memory_pools (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-159">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
-   [<span data-ttu-id="10f86-160">sys.dm_fts_outstanding_batches (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-160">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql)  
  
-   [<span data-ttu-id="10f86-161">sys.dm_fts_parser (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-161">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
-   [<span data-ttu-id="10f86-162">sys.dm_fts_population_ranges (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f86-162">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-population-ranges-transact-sql)  
  
  
