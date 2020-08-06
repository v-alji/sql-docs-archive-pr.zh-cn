---
title: XTP 虚拟处理器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14158b7097427b6704cf5e747fa998a11217ecd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688858"
---
# <a name="xtp-phantom-processor"></a><span data-ttu-id="c5404-102">XTP 虚拟处理器</span><span class="sxs-lookup"><span data-stu-id="c5404-102">XTP Phantom Processor</span></span>
  <span data-ttu-id="c5404-103">XTP 虚拟处理器性能对象包含与 XTP 引擎的虚拟处理子系统相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="c5404-103">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="c5404-104">此组件用于检测在 SERIALIZABLE 隔离级别运行的事务中的虚拟行。</span><span class="sxs-lookup"><span data-stu-id="c5404-104">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>  
  
 <span data-ttu-id="c5404-105">下表介绍了**XTP 虚拟处理器**计数器。</span><span class="sxs-lookup"><span data-stu-id="c5404-105">This table describes the **XTP Phantom Processor** counters.</span></span>  
  
|<span data-ttu-id="c5404-106">计数器</span><span class="sxs-lookup"><span data-stu-id="c5404-106">Counter</span></span>|<span data-ttu-id="c5404-107">说明</span><span class="sxs-lookup"><span data-stu-id="c5404-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5404-108">**灰尘角扫描重试次数/秒（虚拟发出）**</span><span class="sxs-lookup"><span data-stu-id="c5404-108">**Dusty corner scan retries/sec (Phantom-issued)**</span></span>|<span data-ttu-id="c5404-109">在虚拟处理器发出的灰尘角扫描期间，由于写冲突而进行的每秒扫描重试次数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="c5404-109">The number of scan retries due to write conflicts during dusty corner sweeps issued by the phantom processor (on average), per second.</span></span> <span data-ttu-id="c5404-110">此为非常低级的计数器，不适合客户使用。</span><span class="sxs-lookup"><span data-stu-id="c5404-110">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="c5404-111">**删除的虚拟过期行数/秒**</span><span class="sxs-lookup"><span data-stu-id="c5404-111">**Phantom expired rows removed/sec**</span></span>|<span data-ttu-id="c5404-112">虚拟扫描每秒删除的过期行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="c5404-112">The number of expired rows removed by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c5404-113">**接触的虚拟过期行数/秒**</span><span class="sxs-lookup"><span data-stu-id="c5404-113">**Phantom expired rows touched/sec**</span></span>|<span data-ttu-id="c5404-114">虚拟扫描每秒接触的过期行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="c5404-114">The number of expired rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c5404-115">**接触的即将到期的虚拟行数/秒**</span><span class="sxs-lookup"><span data-stu-id="c5404-115">**Phantom expiring rows touched/sec**</span></span>|<span data-ttu-id="c5404-116">虚拟扫描每秒接触的即将到期的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="c5404-116">The number of expiring rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c5404-117">**接触的虚拟行数/秒**</span><span class="sxs-lookup"><span data-stu-id="c5404-117">**Phantom rows touched/sec**</span></span>|<span data-ttu-id="c5404-118">虚拟扫描每秒接触的行数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="c5404-118">The number of rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c5404-119">**启动的虚拟扫描数/秒**</span><span class="sxs-lookup"><span data-stu-id="c5404-119">**Phantom scans started/sec**</span></span>|<span data-ttu-id="c5404-120">每秒启动的虚拟扫描数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="c5404-120">The number of phantom scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5404-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5404-121">See Also</span></span>  
 [<span data-ttu-id="c5404-122">XTP &#40;内存中 OLTP&#41; 性能计数器</span><span class="sxs-lookup"><span data-stu-id="c5404-122">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
