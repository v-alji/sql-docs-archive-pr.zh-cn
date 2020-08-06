---
title: 设计 Analysis Services 多维) 聚合 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18d8ea1adb645868a11b70966ba3be2ed1764fbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590948"
---
# <a name="designing-aggregations-analysis-services---multidimensional"></a><span data-ttu-id="68167-102">设计聚合（Analysis Services - 多维）</span><span class="sxs-lookup"><span data-stu-id="68167-102">Designing Aggregations (Analysis Services - Multidimensional)</span></span>
  <span data-ttu-id="68167-103">聚合是预先计算的多维数据集数据的汇总，可帮助启用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以提供快速的查询响应。</span><span class="sxs-lookup"><span data-stu-id="68167-103">Aggregations are precalculated summaries of cube data that help enable [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide rapid query responses.</span></span>  
  
 <span data-ttu-id="68167-104">若要为分区设置存储选项和设计聚合，请使用聚合设计向导。</span><span class="sxs-lookup"><span data-stu-id="68167-104">To set storage options and design aggregations for a partition, use the Aggregation Design Wizard.</span></span> <span data-ttu-id="68167-105">由于向导每次可针对一个度量值组的一个分区进行操作，所以可以为每个分区选择不同的选项和设计。</span><span class="sxs-lookup"><span data-stu-id="68167-105">The wizard operates on a single partition of a measure group at a time so that you can select different options and designs for each partition.</span></span> <span data-ttu-id="68167-106">向导将引导您完成为分区配置存储和设计聚合的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="68167-106">The wizard takes you through steps to configure storage and design aggregation for a partition.</span></span> <span data-ttu-id="68167-107">有关配置存储的详细信息，请参阅。</span><span class="sxs-lookup"><span data-stu-id="68167-107">For more information about configuring storage, see.</span></span>  
  
 <span data-ttu-id="68167-108">先选择一种方法控制向导所要设计的聚合数目，然后让向导自己设计聚合。</span><span class="sxs-lookup"><span data-stu-id="68167-108">Select a method for controlling the number of aggregations the wizard will design, and then let the wizard design the aggregations.</span></span>  
  
 <span data-ttu-id="68167-109">目标是设计最优数目的聚合。</span><span class="sxs-lookup"><span data-stu-id="68167-109">The goal is to design the optimal number of aggregations.</span></span> <span data-ttu-id="68167-110">该数目不仅能提供快速的响应时间，还能防止分区过大。</span><span class="sxs-lookup"><span data-stu-id="68167-110">This number should not only provide satisfactory response time, but also prevent excessive partition size.</span></span> <span data-ttu-id="68167-111">聚合的数目越多，响应时间就越快，但所需要的存储空间也就越大，计算所需的时间可能也会更长。</span><span class="sxs-lookup"><span data-stu-id="68167-111">A greater number of aggregations produces faster response times but it also requires more storage space and may take longer to compute.</span></span> <span data-ttu-id="68167-112">此外，随着该向导设计越来越多的聚合，早期的聚合比后来的聚合会产生更大的性能提升。</span><span class="sxs-lookup"><span data-stu-id="68167-112">Moreover, as the wizard designs more and more aggregations, earlier aggregations produce considerably larger performance gains than later aggregations.</span></span> <span data-ttu-id="68167-113">减少用处不大的聚合也能够提高性能。</span><span class="sxs-lookup"><span data-stu-id="68167-113">Reduction in less useful aggregations increases performance as well.</span></span> <span data-ttu-id="68167-114">通过以下向导中可用的方法之一，您可以控制向导设计的聚合数目：</span><span class="sxs-lookup"><span data-stu-id="68167-114">You can control the number of aggregations the wizard designs by one of the following methods available in the wizard:</span></span>  
  
-   <span data-ttu-id="68167-115">为聚合指定存储空间限制。</span><span class="sxs-lookup"><span data-stu-id="68167-115">Specify a storage space limit for the aggregations.</span></span>  
  
-   <span data-ttu-id="68167-116">指定性能提升的极限。</span><span class="sxs-lookup"><span data-stu-id="68167-116">Specify a performance gain limit.</span></span>  
  
-   <span data-ttu-id="68167-117">当显示的“性能与大小”曲线开始稳定在一个可接受的性能提升高度上时，手动停止向导。</span><span class="sxs-lookup"><span data-stu-id="68167-117">Stop the wizard manually when the displayed performance versus size curve starts to level off at an acceptable performance gain.</span></span>  
  
-   <span data-ttu-id="68167-118">选择不设计聚合。</span><span class="sxs-lookup"><span data-stu-id="68167-118">Choose not to design aggregations.</span></span>  
  
 <span data-ttu-id="68167-119">若要设计存储，向导必须能够连接到目标服务器上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="68167-119">To design storage, the wizard must be able to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on the target server.</span></span> <span data-ttu-id="68167-120">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 未在目标服务器上运行，或者存储设计进程无法连接到目标服务器，向导将显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="68167-120">The wizard will display an error message if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not running on the target server or if the storage design process is otherwise unable to connect to the target server.</span></span>  
  
 <span data-ttu-id="68167-121">向导的最后一步允许处理或推迟处理。</span><span class="sxs-lookup"><span data-stu-id="68167-121">The final step of the wizard allows you to process or defer processing.</span></span> <span data-ttu-id="68167-122">处理创建使用向导设计的聚合，而推迟处理则保存所设计的聚合以供将来进行处理，从而使设计活动不必处理就可以继续。</span><span class="sxs-lookup"><span data-stu-id="68167-122">Processing creates the aggregations you design with the wizard, while deferring processing saves the designed aggregations for future processing, thus allowing design activities to continue without processing.</span></span> <span data-ttu-id="68167-123">根据分区大小的不同，处理过程可能会需要相当长的一段时间。</span><span class="sxs-lookup"><span data-stu-id="68167-123">Depending on the size of the partition, processing may take considerable time.</span></span> <span data-ttu-id="68167-124">根据您的选择，可以中断对分区的处理。</span><span class="sxs-lookup"><span data-stu-id="68167-124">If you choose, you can interrupt processing a partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68167-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68167-125">See Also</span></span>  
 [<span data-ttu-id="68167-126">聚合和聚合设计</span><span class="sxs-lookup"><span data-stu-id="68167-126">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
