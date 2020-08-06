---
title: optimize for ad hoc workloads 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b217e48d6e4b0ffa0f687ff170f16d4d77ad17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688204"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a><span data-ttu-id="5f004-102">“针对即席工作负荷进行优化”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="5f004-102">optimize for ad hoc workloads Server Configuration Option</span></span>
  <span data-ttu-id="5f004-103">“针对即席工作负荷进行优化”  选项用于提高包含许多一次性临时批处理的工作负荷计划缓存的效率。</span><span class="sxs-lookup"><span data-stu-id="5f004-103">The **optimize for ad hoc workloads** option is used to improve the efficiency of the plan cache for workloads that contain many single use ad hoc batches.</span></span> <span data-ttu-id="5f004-104">如果该选项设置为 1，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将在首次编译批处理时在计划缓存中存储一个编译的小计划存根，而不是存储完全编译的计划。</span><span class="sxs-lookup"><span data-stu-id="5f004-104">When this option is set to 1, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores a small compiled plan stub in the plan cache when a batch is compiled for the first time, instead of the full compiled plan.</span></span> <span data-ttu-id="5f004-105">这种情况下不会让未重复使用的编译计划填充计划缓存，从而有助于缓解内存压力。</span><span class="sxs-lookup"><span data-stu-id="5f004-105">This helps to relieve memory pressure by not allowing the plan cache to become filled with compiled plans that are not reused.</span></span>  
  
 <span data-ttu-id="5f004-106">编译的计划存根使[!INCLUDE[ssDE](../../includes/ssde-md.md)]能够识别此临时批处理以前已经过编译，但只存储了编译计划存根，因此当再次调用（编译或执行）此批处理时，[!INCLUDE[ssDE](../../includes/ssde-md.md)]会对此批处理进行编译，从计划缓存中删除编译计划存根并将完全编译的计划添加到计划缓存中。</span><span class="sxs-lookup"><span data-stu-id="5f004-106">The compiled plan stub allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to recognize that this ad hoc batch has been compiled before but has only stored a compiled plan stub, so when this batch is invoked (compiled or executed) again, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] compiles the batch, removes the compiled plan stub from the plan cache, and adds the full compiled plan to the plan cache.</span></span>  
  
 <span data-ttu-id="5f004-107">将“针对即席工作负荷进行优化”  设置为 1 只会影响新计划；已在计划缓存中的计划不受影响。</span><span class="sxs-lookup"><span data-stu-id="5f004-107">Setting the **optimize for ad hoc workloads** to 1 affects only new plans; plans that are already in the plan cache are unaffected.</span></span>  
  
 <span data-ttu-id="5f004-108">编译计划存根是 sys.dm_exec_cached_plans 目录视图显示的 cacheobjtype 之一。</span><span class="sxs-lookup"><span data-stu-id="5f004-108">The compiled plan stub is one of the cacheobjtypes displayed by the sys.dm_exec_cached_plans catalog view.</span></span> <span data-ttu-id="5f004-109">它具有唯一的 SQL 句柄和计划句柄。</span><span class="sxs-lookup"><span data-stu-id="5f004-109">It has a unique sql handle and plan handle.</span></span> <span data-ttu-id="5f004-110">编译计划存根没有与其关联的执行计划，并且查询计划句柄不会返回 XML 显示计划。</span><span class="sxs-lookup"><span data-stu-id="5f004-110">The compiled plan stub does not have an execution plan associated with it and querying for the plan handle will not return an XML Showplan.</span></span>  
  
 <span data-ttu-id="5f004-111">跟踪标志 8032 将缓存限制参数还原为 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM 设置，此设置通常允许更大的缓存。</span><span class="sxs-lookup"><span data-stu-id="5f004-111">Trace flag 8032 reverts the cache limit parameters to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM setting which in general allows caches to be larger.</span></span> <span data-ttu-id="5f004-112">当频繁重复使用的缓存条目不适合缓存时，以及当 *“针对即席工作负荷进行优化”服务器配置选项* 未能解决与计划缓存相关的问题时，请使用此设置。</span><span class="sxs-lookup"><span data-stu-id="5f004-112">Use this setting when frequently reused cache entries do not fit into the cache and when the *optimize for ad hoc workloads Server Configuration Option* has failed to resolve the problem with plan cache.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="5f004-113">如果大缓存使较少的内存可用于其他内存消耗者（如缓冲池），则跟踪标志 8032 可能导致性能较差。</span><span class="sxs-lookup"><span data-stu-id="5f004-113">Trace flag 8032 can cause poor performance if large caches make less memory available for other memory consumers, such as the buffer pool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f004-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f004-114">See Also</span></span>  
 <span data-ttu-id="5f004-115">[sys.dm_exec_cached_plans (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f004-115">[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql) </span></span>  
 [<span data-ttu-id="5f004-116">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5f004-116">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
