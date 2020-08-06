---
title: SQLXML 4.0) 的模板缓存 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: rothja
ms.author: jroth
ms.openlocfilehash: b2ea8a539086ada1b15abbb9cff4f838af45818c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586578"
---
# <a name="template-caching-sqlxml-40"></a><span data-ttu-id="a4b73-102">模板缓存 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a4b73-102">Template Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="a4b73-103">模板缓存极大地提高了性能。</span><span class="sxs-lookup"><span data-stu-id="a4b73-103">Template caching significantly improves performance.</span></span> <span data-ttu-id="a4b73-104">如果设置模板缓存，该模板将在首次执行时保留在内存中。</span><span class="sxs-lookup"><span data-stu-id="a4b73-104">If template caching is set, the template remains in memory upon its first execution.</span></span> <span data-ttu-id="a4b73-105">这样可提高后续执行该模板的性能。</span><span class="sxs-lookup"><span data-stu-id="a4b73-105">This improves the performance for the subsequent execution of the template.</span></span>  
  
 <span data-ttu-id="a4b73-106">在注册表中添加以下项可以设置模板缓存大小：</span><span class="sxs-lookup"><span data-stu-id="a4b73-106">You can set the template cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="a4b73-107">模板大小的设置应以可用内存和正在使用的模板数为基础。</span><span class="sxs-lookup"><span data-stu-id="a4b73-107">The template size should be set on the basis of the available memory and the number of templates you are using.</span></span> <span data-ttu-id="a4b73-108">**TemplateCacheSize**大小的默认值为31。</span><span class="sxs-lookup"><span data-stu-id="a4b73-108">The default of **TemplateCacheSize** size is 31.</span></span> <span data-ttu-id="a4b73-109">如果模板访问看起来较慢，您可以增加缓存大小；如果内存较少，则可以降低缓存大小。</span><span class="sxs-lookup"><span data-stu-id="a4b73-109">You can increase the cache size if template access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="a4b73-110">为了获得更好的性能，建议您将**TemplateCacheSize**设置为高于通常使用的模板数。</span><span class="sxs-lookup"><span data-stu-id="a4b73-110">For better performance, it is recommended that you set **TemplateCacheSize** higher than the number of templates you usually use.</span></span> <span data-ttu-id="a4b73-111">如果**TemlateCacheSize**小于模板的数量，则性能会随模板数量的增加而降低。</span><span class="sxs-lookup"><span data-stu-id="a4b73-111">If **TemlateCacheSize** is less than the number of templates you have, performance degrades as the number of templates increase.</span></span> <span data-ttu-id="a4b73-112">**TemplateCacheSize**最大可以设置为128。</span><span class="sxs-lookup"><span data-stu-id="a4b73-112">The **TemplateCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="a4b73-113">每次使用缓存的模板时，将检查模板文件的修改时间以确定是否需要刷新该模板。</span><span class="sxs-lookup"><span data-stu-id="a4b73-113">Every time a cached template is used, the modification time of the template file is checked to see whether it needs to be refreshed.</span></span> <span data-ttu-id="a4b73-114">其原因在于磁盘副本新于缓存副本。</span><span class="sxs-lookup"><span data-stu-id="a4b73-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4b73-115">不能缓存模板参数和命令属性。</span><span class="sxs-lookup"><span data-stu-id="a4b73-115">Template parameters and command properties are not cached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b73-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4b73-116">See Also</span></span>  
 <span data-ttu-id="a4b73-117">[&#40;SQLXML 4.0&#41;的架构缓存](schema-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="a4b73-117">[Schema Caching &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="a4b73-118">XSL 缓存 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a4b73-118">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
