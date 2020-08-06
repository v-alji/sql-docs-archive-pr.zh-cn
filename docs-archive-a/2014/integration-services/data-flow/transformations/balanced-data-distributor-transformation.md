---
title: 平衡数据分发器转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.balanceddatadistributor.f1
ms.assetid: ae0b33dd-f44b-42df-b6f6-69861770ce10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09591013bc1f21659720fa9fec2e94167be93a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585917"
---
# <a name="balanced-data-distributor-transformation"></a><span data-ttu-id="4114a-102">平衡的数据分发服务器转换</span><span class="sxs-lookup"><span data-stu-id="4114a-102">Balanced Data Distributor Transformation</span></span>
  <span data-ttu-id="4114a-103">平衡的数据分发服务器 (BDD) 转换可利用新型 CPU 的并发处理能力。</span><span class="sxs-lookup"><span data-stu-id="4114a-103">The Balanced Data Distributor (BDD) transformation takes advantage of concurrent processing capability of modern CPUs.</span></span> <span data-ttu-id="4114a-104">它可将传入行的缓冲区均匀分布到各个独立线程的输出上。</span><span class="sxs-lookup"><span data-stu-id="4114a-104">It distributes buffers of incoming rows uniformly across outputs on separate threads.</span></span> <span data-ttu-id="4114a-105">通过对每个输出路径使用独立线程，BDD 组件提升了运行在多核和多处理器服务器上的 SSIS 包的性能。</span><span class="sxs-lookup"><span data-stu-id="4114a-105">By using separate threads for each output path, the BDD component improves the performance of an SSIS package on multi-core or multi-processor machines.</span></span> <span data-ttu-id="4114a-106">BDD 组件是 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 功能包的一部分。</span><span class="sxs-lookup"><span data-stu-id="4114a-106">The BDD component is part of the Feature Pack for [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="4114a-107">从[此处](https://go.microsoft.com/fwlink/p/?LinkId=391999)下载并安装它。</span><span class="sxs-lookup"><span data-stu-id="4114a-107">Download and install it from [here](https://go.microsoft.com/fwlink/p/?LinkId=391999).</span></span>  
  
 <span data-ttu-id="4114a-108">下图展示了一个使用 BDD 转换的简单示例。</span><span class="sxs-lookup"><span data-stu-id="4114a-108">The following diagram shows a simple example of using the BDD transformation.</span></span> <span data-ttu-id="4114a-109">在该示例中，BDD 转换从平面文件源的输入数据中每次挑选一个管道缓冲区并以循环方式将其向下发送至三个输出路径之一。</span><span class="sxs-lookup"><span data-stu-id="4114a-109">In this example, the BDD transformation picks one pipeline buffer at a time from the input data from a flat file source and sends it down one of the three output paths in a round robin fashion.</span></span> <span data-ttu-id="4114a-110">在 SQL Server Data Tools 中显示数据流任务属性的“属性”窗口中，可查看 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A>（管道缓冲区默认大小）和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A>（管道缓冲区默认最大行数）的值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4114a-110">In SQL Server Data Tools, you can check the values of a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A>(default size of the pipeline buffer) and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A>(default maximum number of rows in a pipeline buffer) in the **Properties** window displaying properties of a data flow task.</span></span>  
  
 <span data-ttu-id="4114a-111">![平衡数据分发器](../../media/balanceddatadistributor.JPG "平衡的数据分发服务器")</span><span class="sxs-lookup"><span data-stu-id="4114a-111">![Balanced Data Distributor](../../media/balanceddatadistributor.JPG "Balanced Data Distributor")</span></span>  
  
 <span data-ttu-id="4114a-112">平衡的数据分发服务器转换可在满足以下条件的方案中提升包的性能：</span><span class="sxs-lookup"><span data-stu-id="4114a-112">The Balanced Data Distributor transformation helps improve performance of a package in a scenario that satisfies the following conditions:</span></span>  
  
1.  <span data-ttu-id="4114a-113">有大量数据传入 BDD 转换。</span><span class="sxs-lookup"><span data-stu-id="4114a-113">There is large amount of data coming into the BDD transformation.</span></span> <span data-ttu-id="4114a-114">如果数据大小较小且只有一个缓冲区能够存放数据，则使用 BDD 转换没有任何意义。</span><span class="sxs-lookup"><span data-stu-id="4114a-114">If the data size is small and only one buffer can hold the data, there is no point in using the BDD transformation.</span></span> <span data-ttu-id="4114a-115">如果数据大小较大且需要多个缓冲区来存放数据，则 BDD 能够借助独立线程高效地并行处理数据缓冲区。</span><span class="sxs-lookup"><span data-stu-id="4114a-115">If the data size is large and several buffers are required to hold the data, BDD can efficiently process buffers of data in parallel by using separate threads.</span></span>  
  
2.  <span data-ttu-id="4114a-116">数据的读取速度可能会超过数据流其余部分处理数据的速度。</span><span class="sxs-lookup"><span data-stu-id="4114a-116">The data can be read faster than the rest of the data flow can process it.</span></span> <span data-ttu-id="4114a-117">在这种情况下，在数据上执行的转换的运行速度将慢于数据的传入速度。</span><span class="sxs-lookup"><span data-stu-id="4114a-117">In this scenario, the transformations that are performed on the data run slowly compared to the rate at which data is coming.</span></span> <span data-ttu-id="4114a-118">如果瓶颈出在目标处，则该目标必须是可并行化的。</span><span class="sxs-lookup"><span data-stu-id="4114a-118">If the bottleneck is at the destination, the destination must be parallelizable though.</span></span>  
  
3.  <span data-ttu-id="4114a-119">数据不必有序。</span><span class="sxs-lookup"><span data-stu-id="4114a-119">The data does not need to be ordered.</span></span> <span data-ttu-id="4114a-120">例如，若要使数据保持有序，则不应使用 BDD 转换来拆分数据。</span><span class="sxs-lookup"><span data-stu-id="4114a-120">For example, if the data needs to stay sorted, you should not split the data using the BDD transformation.</span></span>  
  
 <span data-ttu-id="4114a-121">请注意，如果 SSIS 包中的瓶颈在于从源读取数据的速度，则 BDD 组件无助于性能的提高。</span><span class="sxs-lookup"><span data-stu-id="4114a-121">Note that if the bottleneck in an SSIS package is due to the rate at which data can be read from the source, the BDD component does not help improve the performance.</span></span> <span data-ttu-id="4114a-122">如果 SSIS 包中的瓶颈是因为目标不支持并行，则 BDD 爱莫能助；但是，可以并行执行所有转换并使用 Union All 转换将来自不同 BDD 转换输出路径的输出数据合并，然后再将数据发送至目标。</span><span class="sxs-lookup"><span data-stu-id="4114a-122">If the bottleneck in an SSIS package is because the destination does not support parallelism, the BDD does not help; however, you can perform all the transformations in parallel and use the Union All transformation to combine the output data coming out of different output paths of the BDD transformation before sending the data to the destination.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4114a-123">有关使用该转换的演示，请观看 TechNet Library 上 [平衡的数据分发服务器视频](https://go.microsoft.com/fwlink/?LinkID=226278) 。</span><span class="sxs-lookup"><span data-stu-id="4114a-123">See the [Balanced Data Distributor video](https://go.microsoft.com/fwlink/?LinkID=226278) on the TechNet Library for a presentation with a demo on using the transformation.</span></span>  
  
  
