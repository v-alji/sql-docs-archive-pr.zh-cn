---
title: SQL Server - Plan Cache 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 002cbe261c531c18bdbb2170da9694cc8abde89d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687807"
---
# <a name="sql-server-plan-cache-object"></a><span data-ttu-id="b16fc-102">SQL Server Plan Cache 对象</span><span class="sxs-lookup"><span data-stu-id="b16fc-102">SQL Server, Plan Cache Object</span></span>
  <span data-ttu-id="b16fc-103">Plan Cache 对象提供用于监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何使用内存来存储对象（例如存储过程、即席和准备的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句以及触发器）的计数器。</span><span class="sxs-lookup"><span data-stu-id="b16fc-103">The **Plan Cache** object provides counters to monitor how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses memory to store objects such as stored procedures, ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, and triggers.</span></span> <span data-ttu-id="b16fc-104">可同时监视 **Plan Cache** 对象的多个实例，每个实例代表一个要监视的不同类型的计划。</span><span class="sxs-lookup"><span data-stu-id="b16fc-104">Multiple instances of the **Plan Cache** object can be monitored at the same time, with each instance representing a different type of plan to monitor.</span></span>  
  
 <span data-ttu-id="b16fc-105">下表介绍了 **SQLServer:Plan Cache**计数器。</span><span class="sxs-lookup"><span data-stu-id="b16fc-105">This table describes are the **SQLServer:Plan Cache**counters.</span></span>  
  
|<span data-ttu-id="b16fc-106">SQL Server Plan Cache 计数器</span><span class="sxs-lookup"><span data-stu-id="b16fc-106">SQL Server Plan Cache counters</span></span>|<span data-ttu-id="b16fc-107">说明</span><span class="sxs-lookup"><span data-stu-id="b16fc-107">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="b16fc-108">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="b16fc-108">**Cache Hit Ratio**</span></span>|<span data-ttu-id="b16fc-109">高速缓存命中次数和查找次数的比率。</span><span class="sxs-lookup"><span data-stu-id="b16fc-109">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="b16fc-110">**Cache Object Counts**</span><span class="sxs-lookup"><span data-stu-id="b16fc-110">**Cache Object Counts**</span></span>|<span data-ttu-id="b16fc-111">高速缓存中高速缓存的对象数。</span><span class="sxs-lookup"><span data-stu-id="b16fc-111">Number of cache objects in the cache.</span></span>|  
|<span data-ttu-id="b16fc-112">**Cache Pages**</span><span class="sxs-lookup"><span data-stu-id="b16fc-112">**Cache Pages**</span></span>|<span data-ttu-id="b16fc-113">高速缓存对象所使用的 8 (KB) 页的数目。</span><span class="sxs-lookup"><span data-stu-id="b16fc-113">Number of 8-kilobyte (KB) pages used by cache objects.</span></span>|  
|<span data-ttu-id="b16fc-114">**Cache Objects in use**</span><span class="sxs-lookup"><span data-stu-id="b16fc-114">**Cache Objects in use**</span></span>|<span data-ttu-id="b16fc-115">正在使用的缓存对象数。</span><span class="sxs-lookup"><span data-stu-id="b16fc-115">Number of cache objects in use.</span></span>|  
  
 <span data-ttu-id="b16fc-116">对象中的每个计数器均包含以下实例：</span><span class="sxs-lookup"><span data-stu-id="b16fc-116">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="b16fc-117">Plan Cache 实例</span><span class="sxs-lookup"><span data-stu-id="b16fc-117">Plan Cache instance</span></span>|<span data-ttu-id="b16fc-118">说明</span><span class="sxs-lookup"><span data-stu-id="b16fc-118">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="b16fc-119">**_Total**</span><span class="sxs-lookup"><span data-stu-id="b16fc-119">**_Total**</span></span>|<span data-ttu-id="b16fc-120">所有类型的缓存实例的信息。</span><span class="sxs-lookup"><span data-stu-id="b16fc-120">Information for all types of cache instances.</span></span>|  
|<span data-ttu-id="b16fc-121">**Sql 计划**</span><span class="sxs-lookup"><span data-stu-id="b16fc-121">**Sql Plans**</span></span>|<span data-ttu-id="b16fc-122">由一个临时的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询（包括自动参数化查询）生成的查询计划，或使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] sp_prepare **或** sp_cursorprepare **预备的**语句生成的查询计划。</span><span class="sxs-lookup"><span data-stu-id="b16fc-122">Query plans produced from an ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] query, including auto-parameterized queries, or from [!INCLUDE[tsql](../../includes/tsql-md.md)] statements prepared using **sp_prepare** or **sp_cursorprepare**.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b16fc-123">将临时的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的计划存入缓存，以便将来需要执行相同的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句时再次使用。</span><span class="sxs-lookup"><span data-stu-id="b16fc-123">caches the plans for ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for later reuse if the identical [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is later executed.</span></span> <span data-ttu-id="b16fc-124">用户参数化的查询（即使未显式准备）也作为准备好的 SQL 计划监视。</span><span class="sxs-lookup"><span data-stu-id="b16fc-124">User-parameterized queries (even if not explicitly prepared) are also monitored as Prepared SQL Plans.</span></span>|  
|<span data-ttu-id="b16fc-125">**对象计划**</span><span class="sxs-lookup"><span data-stu-id="b16fc-125">**Object Plans**</span></span>|<span data-ttu-id="b16fc-126">通过创建存储过程、函数或触发器而生成的查询计划。</span><span class="sxs-lookup"><span data-stu-id="b16fc-126">Query plans generated by creating a stored procedure, function, or trigger.</span></span>|  
|<span data-ttu-id="b16fc-127">**绑定树**</span><span class="sxs-lookup"><span data-stu-id="b16fc-127">**Bound Trees**</span></span>|<span data-ttu-id="b16fc-128">视图、规则、计算列和检查约束的规范化树。</span><span class="sxs-lookup"><span data-stu-id="b16fc-128">Normalized trees for views, rules, computed columns, and check constraints.</span></span>|  
|<span data-ttu-id="b16fc-129">**扩展存储过程**</span><span class="sxs-lookup"><span data-stu-id="b16fc-129">**Extended Stored Procedures**</span></span>|<span data-ttu-id="b16fc-130">扩展存储过程的目录信息。</span><span class="sxs-lookup"><span data-stu-id="b16fc-130">Catalog information for extended stores procedures.</span></span>|  
|<span data-ttu-id="b16fc-131">**临时表和表变量**</span><span class="sxs-lookup"><span data-stu-id="b16fc-131">**Temporary Tables & Table Variables**</span></span>|<span data-ttu-id="b16fc-132">与临时表和表变量相关的缓存信息。</span><span class="sxs-lookup"><span data-stu-id="b16fc-132">Cache information related to temporary tables and table variables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b16fc-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b16fc-133">See Also</span></span>  
 <span data-ttu-id="b16fc-134">[“服务器内存”服务器配置选项](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="b16fc-134">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="b16fc-135">[SQL Server Buffer Manager 对象](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="b16fc-135">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="b16fc-136">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="b16fc-136">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
