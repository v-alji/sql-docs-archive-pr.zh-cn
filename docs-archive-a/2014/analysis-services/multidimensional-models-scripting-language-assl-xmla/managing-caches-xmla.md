---
title: " (XMLA) 管理缓存 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdc5bcd2e0500749edfa298a871b6fec7243ddfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580967"
---
# <a name="managing-caches-xmla"></a><span data-ttu-id="2a080-102">管理缓存 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="2a080-102">Managing Caches (XMLA)</span></span>
  <span data-ttu-id="2a080-103">您可以使用 XML for Analysis (XMLA) 中的[ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla)命令来清除指定维度或分区的缓存。</span><span class="sxs-lookup"><span data-stu-id="2a080-103">You can use the [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) command in XML for Analysis (XMLA) to clear the cache of a specified dimension or partition.</span></span> <span data-ttu-id="2a080-104">清除缓存会强制 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 重新生成该对象的缓存。</span><span class="sxs-lookup"><span data-stu-id="2a080-104">Clearing the cache forces [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to rebuild the cache for that object.</span></span>  
  
## <a name="specifying-objects"></a><span data-ttu-id="2a080-105">指定对象</span><span class="sxs-lookup"><span data-stu-id="2a080-105">Specifying Objects</span></span>  
 <span data-ttu-id="2a080-106">命令的[对象](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)属性只能 `ClearCache` 包含以下对象之一的对象引用。</span><span class="sxs-lookup"><span data-stu-id="2a080-106">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `ClearCache` command can contain an object reference only for one of the following objects.</span></span> <span data-ttu-id="2a080-107">如果包含的不是以下对象之一的对象引用，则会出错。</span><span class="sxs-lookup"><span data-stu-id="2a080-107">An error occurs if an object reference is for an object other than one of following objects:</span></span>  
  
 <span data-ttu-id="2a080-108">数据库</span><span class="sxs-lookup"><span data-stu-id="2a080-108">Database</span></span>  
 <span data-ttu-id="2a080-109">清除数据库中包含的所有维度和分区的缓存。</span><span class="sxs-lookup"><span data-stu-id="2a080-109">Clears the cache for all dimensions and partitions contained in the database.</span></span>  
  
 <span data-ttu-id="2a080-110">维度</span><span class="sxs-lookup"><span data-stu-id="2a080-110">Dimension</span></span>  
 <span data-ttu-id="2a080-111">清除指定维度的缓存。</span><span class="sxs-lookup"><span data-stu-id="2a080-111">Clears the cache for the specified dimension.</span></span>  
  
 <span data-ttu-id="2a080-112">多维数据集</span><span class="sxs-lookup"><span data-stu-id="2a080-112">Cube</span></span>  
 <span data-ttu-id="2a080-113">清除多维数据集的度量值组中包含的所有分区的缓存。</span><span class="sxs-lookup"><span data-stu-id="2a080-113">Clears the cache for all partitions contained in the measure groups for the cube.</span></span>  
  
 <span data-ttu-id="2a080-114">度量值组</span><span class="sxs-lookup"><span data-stu-id="2a080-114">Measure group</span></span>  
 <span data-ttu-id="2a080-115">清除度量值组中包含的所有分区的缓存。</span><span class="sxs-lookup"><span data-stu-id="2a080-115">Clears the cache for all partitions contained in the measure group.</span></span>  
  
 <span data-ttu-id="2a080-116">分区</span><span class="sxs-lookup"><span data-stu-id="2a080-116">Partition</span></span>  
 <span data-ttu-id="2a080-117">清除指定分区的缓存。</span><span class="sxs-lookup"><span data-stu-id="2a080-117">Clears the cache for the specified partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a080-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a080-118">See Also</span></span>  
 [<span data-ttu-id="2a080-119">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="2a080-119">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
