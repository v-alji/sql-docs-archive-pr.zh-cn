---
title: XSL 缓存 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: rothja
ms.author: jroth
ms.openlocfilehash: e41f247c34c1b40bedfdf6924a45afe5f63735b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689816"
---
# <a name="xsl-caching-sqlxml-40"></a><span data-ttu-id="07d32-102">XSL 缓存 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="07d32-102">XSL Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="07d32-103">缓存 XSL 样式表可提高性能。</span><span class="sxs-lookup"><span data-stu-id="07d32-103">Caching XSL style sheets improves performance.</span></span> <span data-ttu-id="07d32-104">如果 XSL 缓存设置为 ON，则在第一次执行之后，XSL 样式表将保留在内存中；这可以提高后续处理的性能。</span><span class="sxs-lookup"><span data-stu-id="07d32-104">Upon its first execution, an XSL style sheet remains in memory if XSL caching is set to ON; this improves performance for subsequent processing.</span></span> <span data-ttu-id="07d32-105">默认设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="07d32-105">The default setting is ON.</span></span>  
  
 <span data-ttu-id="07d32-106">通过在注册表中添加以下项可以设置 XSL 缓存大小：</span><span class="sxs-lookup"><span data-stu-id="07d32-106">You can set the XSL cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="07d32-107">应根据可用内存和要使用的 XSL 样式表的个数来设置 XSL 缓存大小。</span><span class="sxs-lookup"><span data-stu-id="07d32-107">The XSL cache size should be set on the basis of the available memory and the number of XSL style sheets you are using.</span></span> <span data-ttu-id="07d32-108">**XSLCacheSize**大小的默认值为31。</span><span class="sxs-lookup"><span data-stu-id="07d32-108">The default of **XSLCacheSize** size is 31.</span></span> <span data-ttu-id="07d32-109">如果 XSL 访问看起来较慢，您可以增加缓存大小；如果内存较少，则可以降低缓存大小。</span><span class="sxs-lookup"><span data-stu-id="07d32-109">You can increase the cache size if XSL access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="07d32-110">为了获得更好的性能，建议您将**XSLCacheSize**设置为大于您通常使用的 XSL 样式表的数量。</span><span class="sxs-lookup"><span data-stu-id="07d32-110">For better performance, it is recommended that you set **XSLCacheSize** higher than the number of XSL style sheets you usually use.</span></span> <span data-ttu-id="07d32-111">如果**XSLCacheSize**小于您拥有的 xsl 样式表的数目，则会随着 xsl 样式表的数量的增加而降低性能。</span><span class="sxs-lookup"><span data-stu-id="07d32-111">If **XSLCacheSize** is less than the number of XSL style sheets you have, the performance degrades as the number of XSL style sheets increases.</span></span> <span data-ttu-id="07d32-112">**XSLCacheSize**最大可以设置为128。</span><span class="sxs-lookup"><span data-stu-id="07d32-112">The **XSLCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="07d32-113">每次使用缓存的 XSL 样式表时，都将检查 XSL 文件的修改时间以确定是否需要刷新该样式表。</span><span class="sxs-lookup"><span data-stu-id="07d32-113">Every time the cached XSL style sheet is used, the modification time of the XSL file is checked to determine whether it needs to be refreshed.</span></span> <span data-ttu-id="07d32-114">其原因在于磁盘副本新于缓存副本。</span><span class="sxs-lookup"><span data-stu-id="07d32-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d32-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07d32-115">See Also</span></span>  
 <span data-ttu-id="07d32-116">[SQLXML 4.0 &#40;模板缓存&#41;](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="07d32-116">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="07d32-117">&#40;SQLXML 4.0&#41;的架构缓存</span><span class="sxs-lookup"><span data-stu-id="07d32-117">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
  
  
