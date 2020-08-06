---
title: SQL Server 2014 中的废止 Analysis Services 功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- discontinued functionality [Analysis Services]
- unsupported features [Analysis Services]
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5414344eb65c907593c9077ee2ba5610b8b397c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590981"
---
# <a name="discontinued-analysis-services-functionality-in-sql-server-2014"></a><span data-ttu-id="63029-102">SQL Server 2014 中废弃的 Analysis Services 功能</span><span class="sxs-lookup"><span data-stu-id="63029-102">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>
  <span data-ttu-id="63029-103">此主题介绍 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中不再可用的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="63029-103">This topic describes [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features that are no longer available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
## <a name="discontinued-features-in-sssql14"></a><span data-ttu-id="63029-104">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63029-104">Discontinued Features in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
  
|<span data-ttu-id="63029-105">类别</span><span class="sxs-lookup"><span data-stu-id="63029-105">Category</span></span>|<span data-ttu-id="63029-106">不推荐使用的功能</span><span class="sxs-lookup"><span data-stu-id="63029-106">Deprecated feature</span></span>|<span data-ttu-id="63029-107">替代功能</span><span class="sxs-lookup"><span data-stu-id="63029-107">Replacement</span></span>|  
|--------------|------------------------|-----------------|  
|<span data-ttu-id="63029-108">本地多维数据集</span><span class="sxs-lookup"><span data-stu-id="63029-108">Local cubes</span></span>|<span data-ttu-id="63029-109">InsertInto 连接字符串属性</span><span class="sxs-lookup"><span data-stu-id="63029-109">InsertInto connection string property</span></span>|<span data-ttu-id="63029-110">用于填充本地多维数据集的原始连接字符串语法已替换为 Create Global Cube（创建全局多维数据集）语句。</span><span class="sxs-lookup"><span data-stu-id="63029-110">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="63029-111">有关详细信息，请参阅[CREATE GLOBAL CUBE 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)。</span><span class="sxs-lookup"><span data-stu-id="63029-111">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="63029-112">本地多维数据集</span><span class="sxs-lookup"><span data-stu-id="63029-112">Local cubes</span></span>|<span data-ttu-id="63029-113">CreateCube 连接字符串属性</span><span class="sxs-lookup"><span data-stu-id="63029-113">CreateCube connection string property</span></span>|<span data-ttu-id="63029-114">用于填充本地多维数据集的原始连接字符串语法已替换为 Create Global Cube（创建全局多维数据集）语句。</span><span class="sxs-lookup"><span data-stu-id="63029-114">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="63029-115">有关详细信息，请参阅[CREATE GLOBAL CUBE 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)。</span><span class="sxs-lookup"><span data-stu-id="63029-115">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="63029-116">数据挖掘</span><span class="sxs-lookup"><span data-stu-id="63029-116">Data Mining</span></span>|<span data-ttu-id="63029-117">SQL Server 2000 PMML</span><span class="sxs-lookup"><span data-stu-id="63029-117">SQL Server 2000 PMML</span></span>|<span data-ttu-id="63029-118">SQL Server 2000 PMML 功能生成了一种格式的 PMML，它具有专有扩展插件，以支持由 PMML 规范中未提供的数据挖掘算法所提供的独特功能。</span><span class="sxs-lookup"><span data-stu-id="63029-118">The SQL Server 2000 PMML feature produced a form of PMML that had proprietary extensions to support unique features provided by Data Mining algorithms that were not available in the PMML specification.</span></span> <span data-ttu-id="63029-119">在 SQL Server 2005 中，Analysis Services 已将 PMML 功能更新为更高的 PMML 2.1 标准。</span><span class="sxs-lookup"><span data-stu-id="63029-119">In SQL Server 2005, Analysis Services updated the PMML feature to the newer PMML 2.1 standard.</span></span> <span data-ttu-id="63029-120">因此，不再需要在 SQL Server 2000 中添加的专有扩展插件，尽管此版本中仍支持它们。</span><span class="sxs-lookup"><span data-stu-id="63029-120">As a result, the proprietary extensions added in SQL Server 2000 are no longer needed, although they are still supported in this release.</span></span>|  
|<span data-ttu-id="63029-121">MDX 语句</span><span class="sxs-lookup"><span data-stu-id="63029-121">MDX Statement</span></span>|<span data-ttu-id="63029-122">Create Action 语句</span><span class="sxs-lookup"><span data-stu-id="63029-122">Create Action statement</span></span>|<span data-ttu-id="63029-123">包括此语句是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="63029-123">This statement is included for backwards compatibility.</span></span> <span data-ttu-id="63029-124">它将替换为 Action 对象。</span><span class="sxs-lookup"><span data-stu-id="63029-124">It is replaced by the Action object.</span></span> <span data-ttu-id="63029-125">有关如何在最新版本的中创建操作的详细信息 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，请参阅[&#40;Analysis Services 多维数据&#41;的操作](multidimensional-models/actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="63029-125">For more information about how to create actions in recent versions of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="discontinued-features-in-previous-releases"></a><span data-ttu-id="63029-126">以前版本中废止的功能</span><span class="sxs-lookup"><span data-stu-id="63029-126">Discontinued Features in Previous Releases</span></span>  
 <span data-ttu-id="63029-127">用于将 SQL Server 2000 Analysis Services 数据库迁移到更新版本的迁移向导已被废弃，因为不再支持 SQL Server 2000。</span><span class="sxs-lookup"><span data-stu-id="63029-127">Migration Wizard, used to migrate SQL Server 2000 Analysis Services databases to newer versions, is discontinued because SQL Server 2000 is no longer supported.</span></span>  
  
 <span data-ttu-id="63029-128">为与 SQL Server 2000 Analysis Services 数据库兼容而提供的决策支持对象 (DSO) 库也已废弃，因为该库不再是 SQL Server 的一部分了。</span><span class="sxs-lookup"><span data-stu-id="63029-128">Decision Support Objects (DSO) library that provided compatibility with SQL Server 2000 Analysis Services databases is also discontinued and no longer part of SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63029-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63029-129">See Also</span></span>  
 [<span data-ttu-id="63029-130">Analysis Services 向后兼容性</span><span class="sxs-lookup"><span data-stu-id="63029-130">Analysis Services Backward Compatibility</span></span>](analysis-services-backward-compatibility.md)  
  
  
