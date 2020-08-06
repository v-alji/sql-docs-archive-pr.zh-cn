---
title: 全文搜索断字符和筛选器在 SQL Server 2005 和 SQL Server 2008 中显著提高 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 8d06bda9-0bbf-4baa-b270-07b1c1f640eb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2e7d3b8da56b407d3937b05cd980c3f8a4eb0c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590550"
---
# <a name="full-text-search-word-breakers-and-filters-significantly-improved-in-sql-server-2005-and-sql-server-2008"></a><span data-ttu-id="008ce-102">全文搜索断字符和筛选器在 SQL Server 2005 和 SQL Server 2008 中有重大改进</span><span class="sxs-lookup"><span data-stu-id="008ce-102">Full-Text Search word breakers and filters significantly improved in SQL Server 2005 and SQL Server 2008</span></span>
  <span data-ttu-id="008ce-103">断字符和筛选器都进行了重大更改。</span><span class="sxs-lookup"><span data-stu-id="008ce-103">The word breakers and filters were significantly changed.</span></span> <span data-ttu-id="008ce-104">对断字符进行了更多改进，其中包括增强的语言覆盖范围和可靠性。</span><span class="sxs-lookup"><span data-stu-id="008ce-104">Additional improvements have been made to word breakers, including enhanced language coverage and reliability.</span></span>  
  
## <a name="description"></a><span data-ttu-id="008ce-105">说明</span><span class="sxs-lookup"><span data-stu-id="008ce-105">Description</span></span>  
 <span data-ttu-id="008ce-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文搜索使用的断字符和筛选器经过了重大修改，从而使功能和可靠性都得到提高。</span><span class="sxs-lookup"><span data-stu-id="008ce-106">Word breakers and filters used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Full-Text Search have been significantly modified to achieve improvements in functionality and reliability.</span></span> <span data-ttu-id="008ce-107">在某些特定情况下，对断字符所做的更改可能会影响某些数据的词汇切分方式。</span><span class="sxs-lookup"><span data-stu-id="008ce-107">In some specific cases, changes to the word breakers can impact how some data is tokenized.</span></span> <span data-ttu-id="008ce-108">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中创建的标记可能与 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 或 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中创建的早期标记不同。</span><span class="sxs-lookup"><span data-stu-id="008ce-108">Tokens created in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] may be different from earlier tokens created in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="008ce-109">有关断字符的信息，请参阅[配置和管理断字符和词干分析器以便搜索](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="008ce-109">For information about word breakers, see [Configure and Manage Word Breakers and Stemmers for Search](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008ce-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="008ce-110">See Also</span></span>  
 [<span data-ttu-id="008ce-111">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="008ce-111">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
