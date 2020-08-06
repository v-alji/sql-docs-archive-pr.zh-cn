---
title: " (SQLXML 4.0) 的架构缓存 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e36711955fa28bafd3b0996b1a02f6cd71f3c4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590118"
---
# <a name="schema-caching-sqlxml-40"></a><span data-ttu-id="905a6-102">架构缓存 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="905a6-102">Schema Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="905a6-103">在并行安装了 XML for Microsoft SQL Server 2000 Web Release 1、Microsoft SQLXML 2.0 和 SQLXML 3.0 的情况下，可以显式控制所有版本中的架构缓存，方法是使用以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="905a6-103">With a side-by-side installation of XML for Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0, and SQLXML 3.0, you can explicitly control the schema caching in all versions by using the following registry keys:</span></span>  
  
 <span data-ttu-id="905a6-104">Web Release 1：</span><span class="sxs-lookup"><span data-stu-id="905a6-104">Web Release 1:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 <span data-ttu-id="905a6-105">SQLXML 2.0：</span><span class="sxs-lookup"><span data-stu-id="905a6-105">SQLXML 2.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 <span data-ttu-id="905a6-106">SQLXML 3.0：</span><span class="sxs-lookup"><span data-stu-id="905a6-106">SQLXML 3.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="905a6-107">有关并行安装的详细信息，请参阅[SQLXML 4.0 SP1 中的新增功能](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md)。</span><span class="sxs-lookup"><span data-stu-id="905a6-107">For more information about side-by-side installation, see [What's New in SQLXML 4.0 SP1](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).</span></span>  
  
 <span data-ttu-id="905a6-108">架构缓存可极大提高 XPath 查询的性能。</span><span class="sxs-lookup"><span data-stu-id="905a6-108">Schema caching significantly improves the performance of an XPath query.</span></span> <span data-ttu-id="905a6-109">对映射架构执行 XPath 查询时，架构存储在内存中，并且在内存中生成所需的数据结构。</span><span class="sxs-lookup"><span data-stu-id="905a6-109">When an XPath query is executed against a mapping schema, the schema is stored in memory, and the necessary data structures are built in memory.</span></span> <span data-ttu-id="905a6-110">如果设置了架构缓存，架构将保留在内存中，因此可提高后续 XPath 查询的性能。</span><span class="sxs-lookup"><span data-stu-id="905a6-110">If schema caching is set, the schema remains in memory, thereby improving performance for subsequent XPath queries.</span></span>  
  
 <span data-ttu-id="905a6-111">可以通过在注册表中添加以上注册表项来设置架构缓存大小。</span><span class="sxs-lookup"><span data-stu-id="905a6-111">You can set the schema cache size by adding the above key in the registry</span></span>  
  
 <span data-ttu-id="905a6-112">应基于可用内存大小和要使用的架构数量来设置架构缓存大小。</span><span class="sxs-lookup"><span data-stu-id="905a6-112">The schema size is set based on the available memory and the number of schemas you are using.</span></span> <span data-ttu-id="905a6-113">默认的**SchemaCacheSize**大小为31。</span><span class="sxs-lookup"><span data-stu-id="905a6-113">The default **SchemaCacheSize** size is 31.</span></span> <span data-ttu-id="905a6-114">如果将**SchemaCacheSize**设置得更高，则会使用更多的内存。</span><span class="sxs-lookup"><span data-stu-id="905a6-114">If you set **SchemaCacheSize** higher, more memory is used.</span></span> <span data-ttu-id="905a6-115">因此，如果架构访问较慢，可以增加缓存大小；如果内存较少，则可以降低缓存大小。</span><span class="sxs-lookup"><span data-stu-id="905a6-115">Therefore, you can increase the cache size if schema access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="905a6-116">出于性能原因，建议你将**SchemaCacheSize**设置为高于你通常使用的映射架构数。</span><span class="sxs-lookup"><span data-stu-id="905a6-116">For performance reasons, it is recommended that you set **SchemaCacheSize** higher than the number of mapping schemas you usually use.</span></span> <span data-ttu-id="905a6-117">随着架构数量的增加，如果**SchemaCacheSize**少于您拥有的架构数量，则会降低性能。</span><span class="sxs-lookup"><span data-stu-id="905a6-117">As the number of schemas increase, if **SchemaCacheSize** is less than the number of schemas you have, the performance degrades.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="905a6-118">在开发期间，建议不缓存架构，因为这样会使对架构的更改在大约两分钟后才会反映在缓存中。</span><span class="sxs-lookup"><span data-stu-id="905a6-118">During development, it is recommended that you do not cache the schemas, because the changes to the schemas are not reflected in the cache for about two minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905a6-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="905a6-119">See Also</span></span>  
 <span data-ttu-id="905a6-120">[SQLXML 4.0 &#40;模板缓存&#41;](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="905a6-120">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="905a6-121">XSL 缓存 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="905a6-121">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
