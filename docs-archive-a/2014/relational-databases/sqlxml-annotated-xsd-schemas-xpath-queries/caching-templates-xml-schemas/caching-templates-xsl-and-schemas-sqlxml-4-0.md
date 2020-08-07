---
title: " (SQLXML 4.0) 缓存模板、XSL 和架构 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: rothja
ms.author: jroth
ms.openlocfilehash: 4df25909cf156957908abf0691964fd66a76343a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587736"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a><span data-ttu-id="8fe55-102">缓存模板、XSL 和架构 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="8fe55-102">Caching Templates, XSL, and Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="8fe55-103">为了提高性能，[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 支持对模板、XSL 和架构进行缓存。</span><span class="sxs-lookup"><span data-stu-id="8fe55-103">To improve performance, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 supports caching templates, XSL, and schemas.</span></span>  
  
 <span data-ttu-id="8fe55-104">所有架构、模板和 XSL 文件（除了来自 http:// 或 ftp:// 位置的文件）都进行缓存。</span><span class="sxs-lookup"><span data-stu-id="8fe55-104">All schemas, templates, and XSL files (except the files from an http:// or ftp:// location) are cached.</span></span> <span data-ttu-id="8fe55-105">在运行进程的过程中，缓存的文件保留在内存中。</span><span class="sxs-lookup"><span data-stu-id="8fe55-105">The cached files remain in memory while the process is running.</span></span> <span data-ttu-id="8fe55-106">在进程退出后，所有缓存内容都将丢失。</span><span class="sxs-lookup"><span data-stu-id="8fe55-106">As the process exits, all the cache is lost.</span></span> <span data-ttu-id="8fe55-107">因此，如果是每个查询都运行一个进程，则缓存带来的好处可能并不明显。</span><span class="sxs-lookup"><span data-stu-id="8fe55-107">Therefore, if you run one process per query, the caching benefit may not be noticeable.</span></span>  
  
 <span data-ttu-id="8fe55-108">本节中的主题提供有关缓存的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8fe55-108">The topics in this section provide more information about caching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fe55-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="8fe55-109">In This Section</span></span>  
 [<span data-ttu-id="8fe55-110">SQLXML 4.0 &#40;模板缓存&#41;</span><span class="sxs-lookup"><span data-stu-id="8fe55-110">Template Caching &#40;SQLXML 4.0&#41;</span></span>](template-caching-sqlxml-4-0.md)  
 <span data-ttu-id="8fe55-111">介绍模板缓存并且提供一个用于模板缓存的注册表项。</span><span class="sxs-lookup"><span data-stu-id="8fe55-111">Describes and provides a registry key for template caching.</span></span>  
  
 [<span data-ttu-id="8fe55-112">XSL 缓存 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="8fe55-112">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
 <span data-ttu-id="8fe55-113">介绍 XSL 缓存并且提供一个用于 XSL 缓存的注册表项。</span><span class="sxs-lookup"><span data-stu-id="8fe55-113">Describes and provides a registry key for XSL caching.</span></span>  
  
 [<span data-ttu-id="8fe55-114">&#40;SQLXML 4.0&#41;的架构缓存</span><span class="sxs-lookup"><span data-stu-id="8fe55-114">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
 <span data-ttu-id="8fe55-115">讨论与架构缓存相关的 SQLXML 并行安装问题，并且提供用于架构缓存的注册表项。</span><span class="sxs-lookup"><span data-stu-id="8fe55-115">Discusses SQLXML side-by-side installation issues related to schema caching, and provides registry keys for schema caching.</span></span>  
  
  
