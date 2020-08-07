---
title: 语义搜索 DDL、函数、存储过程和视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce6c23f9a8ff1d0dac8986bf6b44c7725d4badc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691165"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="61b5c-102">语义搜索 DDL、函数、存储过程和视图</span><span class="sxs-lookup"><span data-stu-id="61b5c-102">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="61b5c-103">列出用于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中支持统计语义搜索的 Transact-SQL 语句和数据库对象。</span><span class="sxs-lookup"><span data-stu-id="61b5c-103">Lists the Transact-SQL statements and the database objects that support statistical semantic search in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="61b5c-104">有关支持全文搜索的语句和数据库对象的列表，请参阅 [全文搜索 DDL、函数、存储过程和视图](../views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="61b5c-104">For the list of statements and database objects that support full-text search, see [Full-Text Search DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="61b5c-105">Transact-SQL 数据定义语言 (DDL) 语句</span><span class="sxs-lookup"><span data-stu-id="61b5c-105">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
|<span data-ttu-id="61b5c-106">Object</span><span class="sxs-lookup"><span data-stu-id="61b5c-106">Object</span></span>|<span data-ttu-id="61b5c-107">更多信息</span><span class="sxs-lookup"><span data-stu-id="61b5c-107">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="61b5c-108">ALTER FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-108">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)|[<span data-ttu-id="61b5c-109">对表和列启用语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-109">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="61b5c-110">CREATE FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-110">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)|[<span data-ttu-id="61b5c-111">对表和列启用语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-111">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="system-functions"></a><a name="func"></a> <span data-ttu-id="61b5c-112">系统函数</span><span class="sxs-lookup"><span data-stu-id="61b5c-112">System Functions</span></span>  
  
|<span data-ttu-id="61b5c-113">Object</span><span class="sxs-lookup"><span data-stu-id="61b5c-113">Object</span></span>|<span data-ttu-id="61b5c-114">更多信息</span><span class="sxs-lookup"><span data-stu-id="61b5c-114">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="61b5c-115">semantickeyphrasetable (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-115">semantickeyphrasetable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)|[<span data-ttu-id="61b5c-116">使用语义搜索查找文档中的关键短语</span><span class="sxs-lookup"><span data-stu-id="61b5c-116">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)|  
|[<span data-ttu-id="61b5c-117">semanticsimilaritydetailstable (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-117">semanticsimilaritydetailstable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)|[<span data-ttu-id="61b5c-118">使用语义搜索来查找相似和相关文档</span><span class="sxs-lookup"><span data-stu-id="61b5c-118">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
|[<span data-ttu-id="61b5c-119">semanticsimilaritytable (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-119">semanticsimilaritytable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)|[<span data-ttu-id="61b5c-120">使用语义搜索来查找相似和相关文档</span><span class="sxs-lookup"><span data-stu-id="61b5c-120">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="system-metadata-functions"></a><a name="meta"></a> <span data-ttu-id="61b5c-121">系统元数据函数</span><span class="sxs-lookup"><span data-stu-id="61b5c-121">System Metadata Functions</span></span>  
  
|<span data-ttu-id="61b5c-122">Object</span><span class="sxs-lookup"><span data-stu-id="61b5c-122">Object</span></span>|<span data-ttu-id="61b5c-123">更多信息</span><span class="sxs-lookup"><span data-stu-id="61b5c-123">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="61b5c-124">COLUMNPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-124">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|[<span data-ttu-id="61b5c-125">对表和列启用语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-125">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="61b5c-126">DATABASEPROPERTYEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-126">DATABASEPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/databasepropertyex-transact-sql)|[<span data-ttu-id="61b5c-127">对表和列启用语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-127">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="61b5c-128">FULLTEXTCATALOGPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-128">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|[<span data-ttu-id="61b5c-129">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-129">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="61b5c-130">INDEXPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-130">INDEXPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|[<span data-ttu-id="61b5c-131">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-131">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="61b5c-132">OBJECTPROPERTYEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-132">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|[<span data-ttu-id="61b5c-133">对表和列启用语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-133">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="61b5c-134">SERVERPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-134">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|[<span data-ttu-id="61b5c-135">安装和配置语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-135">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-stored-procedures"></a><a name="sproc"></a> <span data-ttu-id="61b5c-136">系统存储过程</span><span class="sxs-lookup"><span data-stu-id="61b5c-136">System Stored Procedures</span></span>  
  
|<span data-ttu-id="61b5c-137">Object</span><span class="sxs-lookup"><span data-stu-id="61b5c-137">Object</span></span>|<span data-ttu-id="61b5c-138">更多信息</span><span class="sxs-lookup"><span data-stu-id="61b5c-138">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="61b5c-139">sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-139">sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)|[<span data-ttu-id="61b5c-140">安装和配置语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-140">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="61b5c-141">sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-141">sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)|[<span data-ttu-id="61b5c-142">安装和配置语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-142">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---catalog-views"></a><a name="cv"></a> <span data-ttu-id="61b5c-143">系统视图 - 目录视图</span><span class="sxs-lookup"><span data-stu-id="61b5c-143">System Views - Catalog Views</span></span>  
  
|<span data-ttu-id="61b5c-144">Object</span><span class="sxs-lookup"><span data-stu-id="61b5c-144">Object</span></span>|<span data-ttu-id="61b5c-145">更多信息</span><span class="sxs-lookup"><span data-stu-id="61b5c-145">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="61b5c-146">sys.fulltext_index_columns (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-146">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|[<span data-ttu-id="61b5c-147">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-147">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="61b5c-148">sys.fulltext_semantic_language_statistics_database (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-148">sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)|[<span data-ttu-id="61b5c-149">安装和配置语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-149">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="61b5c-150">sys.fulltext_semantic_languages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-150">sys.fulltext_semantic_languages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)|[<span data-ttu-id="61b5c-151">安装和配置语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-151">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="61b5c-152">系统视图 - 动态管理视图</span><span class="sxs-lookup"><span data-stu-id="61b5c-152">System Views - Dynamic Management Views</span></span>  
  
|<span data-ttu-id="61b5c-153">Object</span><span class="sxs-lookup"><span data-stu-id="61b5c-153">Object</span></span>|<span data-ttu-id="61b5c-154">更多信息</span><span class="sxs-lookup"><span data-stu-id="61b5c-154">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="61b5c-155">sys.dm_db_fts_index_physical_stats (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-155">sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)|[<span data-ttu-id="61b5c-156">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-156">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="61b5c-157">sys.dm_fts_index_population (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|[<span data-ttu-id="61b5c-158">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-158">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="61b5c-159">sys.dm_fts_semantic_similarity_population (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61b5c-159">sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)|[<span data-ttu-id="61b5c-160">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-160">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a><span data-ttu-id="61b5c-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61b5c-161">See Also</span></span>  
 [<span data-ttu-id="61b5c-162">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="61b5c-162">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
  
  
