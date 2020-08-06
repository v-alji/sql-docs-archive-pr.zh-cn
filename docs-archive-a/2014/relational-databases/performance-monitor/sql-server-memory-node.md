---
title: SQL Server，内存节点 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5bbc3f581ea9ececeb7d55a614ef27c3c72de7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590740"
---
# <a name="sql-server-memory-node"></a><span data-ttu-id="53d1d-102">SQL Server、内存节点</span><span class="sxs-lookup"><span data-stu-id="53d1d-102">SQL Server, Memory Node</span></span>
  <span data-ttu-id="53d1d-103">Microsoft **中的** “内存节点” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象在 NUMA 节点上提供监视服务器内存使用情况的计数器。</span><span class="sxs-lookup"><span data-stu-id="53d1d-103">The **Memory Node** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor server memory usage on NUMA nodes.</span></span>  
  
## <a name="memory-node-counters"></a><span data-ttu-id="53d1d-104">内存节点计数</span><span class="sxs-lookup"><span data-stu-id="53d1d-104">Memory Node Counters</span></span>  
 <span data-ttu-id="53d1d-105">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]“内存节点”计数器。</span><span class="sxs-lookup"><span data-stu-id="53d1d-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** counters.</span></span>  
  
|<span data-ttu-id="53d1d-106">SQL Server Memory Manager 计数器</span><span class="sxs-lookup"><span data-stu-id="53d1d-106">SQL Server Memory Manager counters</span></span>|<span data-ttu-id="53d1d-107">说明</span><span class="sxs-lookup"><span data-stu-id="53d1d-107">Description</span></span>|  
|----------------------------------------|-----------------|  
|<span data-ttu-id="53d1d-108">**Database Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="53d1d-108">**Database Node Memory (KB)**</span></span>|<span data-ttu-id="53d1d-109">指定服务器当前在此节点上用于数据库页面的内存量。</span><span class="sxs-lookup"><span data-stu-id="53d1d-109">Specifies the amount of memory the server is currently using on this node for database pages.</span></span>|  
|<span data-ttu-id="53d1d-110">**Free Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="53d1d-110">**Free Node Memory (KB)**</span></span>|<span data-ttu-id="53d1d-111">指定服务器在此节点上未使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="53d1d-111">Specifies the amount of memory the server is not using on this node.</span></span>|  
|<span data-ttu-id="53d1d-112">**Foreign Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="53d1d-112">**Foreign Node Memory (KB)**</span></span>|<span data-ttu-id="53d1d-113">指定此节点上非 NUMA 本地内存的量。</span><span class="sxs-lookup"><span data-stu-id="53d1d-113">Specifies the amount of non NUMA-local memory on this node.</span></span>|  
|<span data-ttu-id="53d1d-114">**Stolen Memory Node (KB)**</span><span class="sxs-lookup"><span data-stu-id="53d1d-114">**Stolen Memory Node (KB)**</span></span>|<span data-ttu-id="53d1d-115">指定服务器在此节点上出于数据库页面以外的目的使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="53d1d-115">Specifies the amount of memory the server is using on this node for purposes other than database pages.</span></span>|  
|<span data-ttu-id="53d1d-116">**Target Node Memory**</span><span class="sxs-lookup"><span data-stu-id="53d1d-116">**Target Node Memory**</span></span>|<span data-ttu-id="53d1d-117">指定此节点的理想内存量。</span><span class="sxs-lookup"><span data-stu-id="53d1d-117">Specifies the ideal amount of memory for this node.</span></span>|  
|<span data-ttu-id="53d1d-118">**Total Node Memory**</span><span class="sxs-lookup"><span data-stu-id="53d1d-118">**Total Node Memory**</span></span>|<span data-ttu-id="53d1d-119">指示服务器在此节点上已提交的总内存量。</span><span class="sxs-lookup"><span data-stu-id="53d1d-119">Indicates the total amount of memory the server has committed on this node.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53d1d-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53d1d-120">See Also</span></span>  
 <span data-ttu-id="53d1d-121">[监视资源使用情况（系统监视器）](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="53d1d-121">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="53d1d-122">[SQL Server Buffer Manager 对象](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="53d1d-122">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="53d1d-123">sys.dm_os_performance_counters (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="53d1d-123">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
