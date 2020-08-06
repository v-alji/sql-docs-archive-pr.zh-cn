---
title: 自 SQL Server 2008 以来全文搜索已发生更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d253bb05-9166-4b50-bd4a-27b818f514e0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 99d3ed4478f007bbe7f05838250aa33a9c4fe448
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586174"
---
# <a name="full-text-search-has-changed-since-sql-server-2008"></a><span data-ttu-id="9d1f4-102">全文搜索自 SQL Server 2008 以后已发生更改</span><span class="sxs-lookup"><span data-stu-id="9d1f4-102">Full-Text Search has changed since SQL Server 2008</span></span>
  <span data-ttu-id="9d1f4-103">升级顾问检测到将升级全文搜索。</span><span class="sxs-lookup"><span data-stu-id="9d1f4-103">Upgrade Advisor detected that full-text search is going to be upgraded.</span></span> <span data-ttu-id="9d1f4-104">许多全文搜索选项和设置已发生更改。</span><span class="sxs-lookup"><span data-stu-id="9d1f4-104">Many full-text search options and settings have changed.</span></span> <span data-ttu-id="9d1f4-105">因此，当您升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 全文搜索时，可能需要修改某些设置。</span><span class="sxs-lookup"><span data-stu-id="9d1f4-105">Therefore, when you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Full-Text Search, some of your settings might need modification.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9d1f4-106">组件</span><span class="sxs-lookup"><span data-stu-id="9d1f4-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="9d1f4-107">说明</span><span class="sxs-lookup"><span data-stu-id="9d1f4-107">Description</span></span>  
 <span data-ttu-id="9d1f4-108">若干个全文搜索功能、设置和对象自 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 后已得到修改，并且升级时不会维护许多现有设置。</span><span class="sxs-lookup"><span data-stu-id="9d1f4-108">Several full-text search features, settings and objects have been modified since [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and many of your existing settings will not be maintained when you upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="9d1f4-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="9d1f4-109">Corrective Action</span></span>  
 <span data-ttu-id="9d1f4-110">同时还建议您在升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时查阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 联机丛书中的全文搜索文档以便了解重大更改和最佳实践。</span><span class="sxs-lookup"><span data-stu-id="9d1f4-110">We also recommend reviewing full-text search documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online for breaking changes and best practices when you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9d1f4-111">外部资源</span><span class="sxs-lookup"><span data-stu-id="9d1f4-111">External Resources</span></span>  
 [<span data-ttu-id="9d1f4-112">全文搜索向后兼容性</span><span class="sxs-lookup"><span data-stu-id="9d1f4-112">Full-Text Search Backward Compatibility</span></span>](../../../2014/database-engine/full-text-search-backward-compatibility.md)  
  
 [<span data-ttu-id="9d1f4-113">Full-Text Search Upgrade（全文搜索升级）</span><span class="sxs-lookup"><span data-stu-id="9d1f4-113">Full-Text Search Upgrade</span></span>](https://go.microsoft.com/fwlink/?LinkId=112291)  
  
 [<span data-ttu-id="9d1f4-114">对全文搜索的重大更改</span><span class="sxs-lookup"><span data-stu-id="9d1f4-114">Breaking Changes to Full-Text Search</span></span>](../../../2014/database-engine/breaking-changes-to-full-text-search.md)  
  
  
