---
title: XTP 存储 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: efd4a9eba36060d3d4bab9b371678ab2b2c409ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587371"
---
# <a name="xtp-storage"></a><span data-ttu-id="14b98-102">XTP 存储</span><span class="sxs-lookup"><span data-stu-id="14b98-102">XTP Storage</span></span>
  <span data-ttu-id="14b98-103">XTP 存储性能对象包含与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XTP 存储相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="14b98-103">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="14b98-104">下表介绍了**XTP 存储**计数器。</span><span class="sxs-lookup"><span data-stu-id="14b98-104">This table describes the **XTP Storage** counters.</span></span>  
  
|<span data-ttu-id="14b98-105">计数器</span><span class="sxs-lookup"><span data-stu-id="14b98-105">Counter</span></span>|<span data-ttu-id="14b98-106">说明</span><span class="sxs-lookup"><span data-stu-id="14b98-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14b98-107">**Checkpoints Closed**</span><span class="sxs-lookup"><span data-stu-id="14b98-107">**Checkpoints Closed**</span></span>|<span data-ttu-id="14b98-108">联机代理执行的已关闭检查点的计数。</span><span class="sxs-lookup"><span data-stu-id="14b98-108">Count of checkpoints closed done by online agent.</span></span>|  
|<span data-ttu-id="14b98-109">**Checkpoints Completed**</span><span class="sxs-lookup"><span data-stu-id="14b98-109">**Checkpoints Completed**</span></span>|<span data-ttu-id="14b98-110">脱机检查点线程处理的检查点计数。</span><span class="sxs-lookup"><span data-stu-id="14b98-110">Count of checkpoints processed by offline checkpoint thread.</span></span>|  
|<span data-ttu-id="14b98-111">**Core Merges Completed**</span><span class="sxs-lookup"><span data-stu-id="14b98-111">**Core Merges Completed**</span></span>|<span data-ttu-id="14b98-112">合并工作线程完成的核心合并数。</span><span class="sxs-lookup"><span data-stu-id="14b98-112">The number of core merges completed by the merge worker thread.</span></span> <span data-ttu-id="14b98-113">仍需要安装这些合并。</span><span class="sxs-lookup"><span data-stu-id="14b98-113">These merges still need to be installed.</span></span>|  
|<span data-ttu-id="14b98-114">**Merge Policy Evaluations**</span><span class="sxs-lookup"><span data-stu-id="14b98-114">**Merge Policy Evaluations**</span></span>|<span data-ttu-id="14b98-115">自服务器启动以来的合并策略评估数。</span><span class="sxs-lookup"><span data-stu-id="14b98-115">The number of merge policy evaluations since the server started.</span></span>|  
|<span data-ttu-id="14b98-116">**Merge Requests Outstanding**</span><span class="sxs-lookup"><span data-stu-id="14b98-116">**Merge Requests Outstanding**</span></span>|<span data-ttu-id="14b98-117">自服务器启动以来未完成的合并请求数。</span><span class="sxs-lookup"><span data-stu-id="14b98-117">The number of merge requests outstanding since the server started.</span></span>|  
|<span data-ttu-id="14b98-118">**Merges Abandoned**</span><span class="sxs-lookup"><span data-stu-id="14b98-118">**Merges Abandoned**</span></span>|<span data-ttu-id="14b98-119">因失败而放弃的合并数。</span><span class="sxs-lookup"><span data-stu-id="14b98-119">The number of merges abandoned due to failure.</span></span>|  
|<span data-ttu-id="14b98-120">**Merges Installed**</span><span class="sxs-lookup"><span data-stu-id="14b98-120">**Merges Installed**</span></span>|<span data-ttu-id="14b98-121">成功安装的合并数。</span><span class="sxs-lookup"><span data-stu-id="14b98-121">The number of merges successfully installed.</span></span>|  
|<span data-ttu-id="14b98-122">**Total Files Merged**</span><span class="sxs-lookup"><span data-stu-id="14b98-122">**Total Files Merged**</span></span>|<span data-ttu-id="14b98-123">已合并的源文件总数。</span><span class="sxs-lookup"><span data-stu-id="14b98-123">The total number of source files merged.</span></span> <span data-ttu-id="14b98-124">此计数可用于查找合并中源文件的平均数目。</span><span class="sxs-lookup"><span data-stu-id="14b98-124">This count can be used to find the average number of source files in the merge.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14b98-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14b98-125">See Also</span></span>  
 [<span data-ttu-id="14b98-126">XTP &#40;内存中 OLTP&#41; 性能计数器</span><span class="sxs-lookup"><span data-stu-id="14b98-126">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
