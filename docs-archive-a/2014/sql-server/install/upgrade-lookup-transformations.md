---
title: 升级查找转换 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74430ab1bed232b8d510a8c28a8a690d88d1f6ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578008"
---
# <a name="upgrade-lookup-transformations"></a><span data-ttu-id="98e6b-102">升级查找转换</span><span class="sxs-lookup"><span data-stu-id="98e6b-102">Upgrade Lookup Transformations</span></span>
  <span data-ttu-id="98e6b-103">当您从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 时，请考虑将该包修改为利用查找转换中的新功能。</span><span class="sxs-lookup"><span data-stu-id="98e6b-103">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] consider modifying packages to take advantage of the new features in the Lookup Transformation.</span></span> <span data-ttu-id="98e6b-104">该转换支持 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 中的缓存类型和数据输出选项。</span><span class="sxs-lookup"><span data-stu-id="98e6b-104">The transformation supports the caching types and data output options available in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)].</span></span> <span data-ttu-id="98e6b-105">有关其他缓存和数据输出的详细信息，请参阅[查找转换](../../integration-services/data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="98e6b-105">For more information about additional the caching and data outputs, see [Lookup Transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="98e6b-106">在 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 中，可用的缓存类型有完全缓存、部分缓存和不缓存。</span><span class="sxs-lookup"><span data-stu-id="98e6b-106">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the available caching types are full caching, partial caching, and no caching.</span></span> <span data-ttu-id="98e6b-107">在 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 中，可以通过配置查找转换来使用其中一种缓存类型。</span><span class="sxs-lookup"><span data-stu-id="98e6b-107">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], you can configure a Lookup transformation to use one of these caching types.</span></span> <span data-ttu-id="98e6b-108">有关如何实现部分缓存或没有缓存的详细信息，请参阅[在无缓存或部分缓存模式下实现查找](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="98e6b-108">For more information about how to implement partial caching or no caching, see [Implement a Lookup in No Cache or Partial Cache Mode](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md).</span></span> <span data-ttu-id="98e6b-109">有关如何实现完全缓存的信息，请参阅[在完全缓存模式下使用缓存连接管理器实现查找转换](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)，并[使用 OLE DB 连接管理器在完全缓存模式下实现查找转换](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="98e6b-109">For information about how to implement full caching, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) and [Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="98e6b-110">在 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 中，查找转换具有一个输入、一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="98e6b-110">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the Lookup transformation had an input, an output, and an error output.</span></span> <span data-ttu-id="98e6b-111">在引用数据集中有匹配条目的输入中的行由输出处理。</span><span class="sxs-lookup"><span data-stu-id="98e6b-111">Rows in the input that had matching entries in the reference dataset were handled by the output.</span></span> <span data-ttu-id="98e6b-112">没有匹配条目的输入中的行则被视为错误，并可能被重定向到错误输出。</span><span class="sxs-lookup"><span data-stu-id="98e6b-112">Rows in the input that did not have matching entries were treated as errors and could be redirected to the error output.</span></span> <span data-ttu-id="98e6b-113">在 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 中，查找转换有两个输出：匹配输出和不匹配输出。</span><span class="sxs-lookup"><span data-stu-id="98e6b-113">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], the Lookup transformation has two outputs: a match output and a no match output.</span></span>  
  
 <span data-ttu-id="98e6b-114">默认情况下，当运行在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中创建的查找转换时，[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 将没有匹配条目的行视为错误，并允许您将这些行重定向到错误输出。</span><span class="sxs-lookup"><span data-stu-id="98e6b-114">By default, when you run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] treats the rows without matching entries as errors and enables you to redirect the rows to an error output.</span></span> <span data-ttu-id="98e6b-115">您也可以配置查找转换，以便将这些行视为非错误并将它们重定向到不匹配输出。</span><span class="sxs-lookup"><span data-stu-id="98e6b-115">You have the option of configuring the Lookup transformation to treat the rows as non-errors and redirect the rows to the no match output.</span></span>  
  
 <span data-ttu-id="98e6b-116">有关详细信息，请参阅[查找转换编辑器 &#40;常规页&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="98e6b-116">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e6b-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98e6b-117">See Also</span></span>  
 [<span data-ttu-id="98e6b-118">查找转换</span><span class="sxs-lookup"><span data-stu-id="98e6b-118">Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
