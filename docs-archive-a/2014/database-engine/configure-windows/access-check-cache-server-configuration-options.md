---
title: “访问检查缓存”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576980"
---
# <a name="access-check-cache-server-configuration-options"></a><span data-ttu-id="2f42e-102">“访问检查缓存”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="2f42e-102">access check cache Server Configuration Options</span></span>
<span data-ttu-id="2f42e-103">通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]访问数据库对象时，访问检查缓存在一个名为 **访问检查结果缓存**的内部结构中。</span><span class="sxs-lookup"><span data-stu-id="2f42e-103">When database objects are accessed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the access check is cached in an internal structure called the **access check result cache**.</span></span> 
  
<span data-ttu-id="2f42e-104">“访问检查缓存桶计数”选项控制用于访问检查结果缓存的哈希桶的数目。</span><span class="sxs-lookup"><span data-stu-id="2f42e-104">The **access check cache bucket count** option controls the number of hash buckets that are used for the access check result cache.</span></span> 

<span data-ttu-id="2f42e-105">“访问检查缓存配额”选项控制访问检查结果缓存中存储的条目数。</span><span class="sxs-lookup"><span data-stu-id="2f42e-105">The **access check cache quota** option controls the number of entries that are stored in the access check result cache.</span></span> <span data-ttu-id="2f42e-106">如果达到最大条目数，则从访问检查结果缓存中删除最早的条目。</span><span class="sxs-lookup"><span data-stu-id="2f42e-106">When the maximum number of entries is reached, the oldest entries are removed from the access check result cache.</span></span>
  
<span data-ttu-id="2f42e-107">默认值 0 表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在管理这些选项。</span><span class="sxs-lookup"><span data-stu-id="2f42e-107">The default values of 0 indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is managing these options.</span></span> <span data-ttu-id="2f42e-108">从 [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] 到 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ，默认值将转换为以下内部配置：</span><span class="sxs-lookup"><span data-stu-id="2f42e-108">From [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] through [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the default values translate to the following internal configurations:</span></span>
-   <span data-ttu-id="2f42e-109">对于访问检查缓存 bucket 计数，值0将为 x86 体系结构设置默认值256存储桶，为 x64 和 IA-64 体系结构设置 2048 bucket。</span><span class="sxs-lookup"><span data-stu-id="2f42e-109">For access check cache bucket count, the value 0 sets a default value of 256 buckets for x86 architecture, and 2,048 buckets for x64 and IA-64 architectures.</span></span>
-   <span data-ttu-id="2f42e-110">对于访问检查缓存配额，值0会为 x86 体系结构设置默认值1024项，并为 x64 和 IA-64 体系结构设置 28192048 bucket。</span><span class="sxs-lookup"><span data-stu-id="2f42e-110">For access check cache quota, the value 0 sets a default value of 1,024 entries for x86 architecture, and 28,192,048 buckets for x64 and IA-64 architectures.</span></span>

<span data-ttu-id="2f42e-111">在极少数情况下，可以通过更改这些选项来提高性能。</span><span class="sxs-lookup"><span data-stu-id="2f42e-111">In rare circumstances, performance can be improved by changing these options.</span></span> <span data-ttu-id="2f42e-112">例如，如果使用了太多内存，则可能希望减小访问检查结果缓存的大小。</span><span class="sxs-lookup"><span data-stu-id="2f42e-112">For example, you may want to reduce the size of the access check result cache if too much memory is used.</span></span> <span data-ttu-id="2f42e-113">或者，如果在重新计算权限时 CPU 使用率较高，则可能希望增加访问检查结果缓存的大小。</span><span class="sxs-lookup"><span data-stu-id="2f42e-113">Or, you may want to increase the size of the access check result cache if you experience high CPU usage when permissions are recalculated.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f42e-114">Microsoft 建议仅在有 Microsoft 客户支持服务部门提供指导的情况下才更改这些选项。</span><span class="sxs-lookup"><span data-stu-id="2f42e-114">Microsoft recommends only changing these options when directed by Microsoft Customer Support Services.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2f42e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f42e-115">See Also</span></span>  
 <span data-ttu-id="2f42e-116">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2f42e-116">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="2f42e-117">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2f42e-117">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
