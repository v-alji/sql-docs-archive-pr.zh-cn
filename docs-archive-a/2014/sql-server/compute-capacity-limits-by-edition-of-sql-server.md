---
title: 按 SQL Server 版本划分的计算能力限制 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- processors [SQL Server], supported
- number of processors supported
- maximum number of processors supported
ms.assetid: cd308bc9-9468-40cc-ad6e-1a8a69aca6c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f098b019205417d0339f426832c5683e6b8fa7cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586305"
---
# <a name="compute-capacity-limits-by-edition-of-sql-server"></a><span data-ttu-id="92ae5-102">Compute Capacity Limits by Edition of SQL Server</span><span class="sxs-lookup"><span data-stu-id="92ae5-102">Compute Capacity Limits by Edition of SQL Server</span></span>
  <span data-ttu-id="92ae5-103">本主题讨论不同 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本的计算能力限制，以及在具有超线程处理器的物理和虚拟化环境中计算能力限制有何不同。</span><span class="sxs-lookup"><span data-stu-id="92ae5-103">This topic discusses compute capacity limits for different editions of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] and how they differ in physical and virtualized environments with hyperthreaded processors.</span></span>  
  
 <span data-ttu-id="92ae5-104">![映射到计算能力限制](../../2014/getting-started/media/compute-capacity-limits.gif "映射到计算能力限制")</span><span class="sxs-lookup"><span data-stu-id="92ae5-104">![Mappings to compute capacity limits](../../2014/getting-started/media/compute-capacity-limits.gif "Mappings to compute capacity limits")</span></span>  
  
 <span data-ttu-id="92ae5-105">下表描述了上图中所用的符号：</span><span class="sxs-lookup"><span data-stu-id="92ae5-105">The following table describes the notations being used in the above diagram:</span></span>  
  
|<span data-ttu-id="92ae5-106">值</span><span class="sxs-lookup"><span data-stu-id="92ae5-106">Value</span></span>|<span data-ttu-id="92ae5-107">说明</span><span class="sxs-lookup"><span data-stu-id="92ae5-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ae5-108">0..1</span><span class="sxs-lookup"><span data-stu-id="92ae5-108">0..1</span></span>|<span data-ttu-id="92ae5-109">零个或 1 个</span><span class="sxs-lookup"><span data-stu-id="92ae5-109">Zero or one</span></span>|  
|<span data-ttu-id="92ae5-110">1</span><span class="sxs-lookup"><span data-stu-id="92ae5-110">1</span></span>|<span data-ttu-id="92ae5-111">恰好一个</span><span class="sxs-lookup"><span data-stu-id="92ae5-111">Exactly one</span></span>|  
|<span data-ttu-id="92ae5-112">1..\*</span><span class="sxs-lookup"><span data-stu-id="92ae5-112">1..\*</span></span>|<span data-ttu-id="92ae5-113">一个或更多</span><span class="sxs-lookup"><span data-stu-id="92ae5-113">One or more</span></span>|  
|<span data-ttu-id="92ae5-114">0..\*</span><span class="sxs-lookup"><span data-stu-id="92ae5-114">0..\*</span></span>|<span data-ttu-id="92ae5-115">零个或更多</span><span class="sxs-lookup"><span data-stu-id="92ae5-115">Zero or more</span></span>|  
|<span data-ttu-id="92ae5-116">1..2</span><span class="sxs-lookup"><span data-stu-id="92ae5-116">1..2</span></span>|<span data-ttu-id="92ae5-117">1 个或 2 个</span><span class="sxs-lookup"><span data-stu-id="92ae5-117">One or two</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="92ae5-118">进一步详细阐述：</span><span class="sxs-lookup"><span data-stu-id="92ae5-118">To elaborate further:</span></span>  
> 
>  1.  <span data-ttu-id="92ae5-119">虚拟机分配有一个或多个虚拟处理器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-119">A virtual machine is allocated one or more virtual processors.</span></span>  
> 2.  <span data-ttu-id="92ae5-120">一个或多个虚拟处理器被分配给恰好一个虚拟机。</span><span class="sxs-lookup"><span data-stu-id="92ae5-120">One or more virtual processors are allocated to exactly one virtual machine.</span></span>  
> 3.  <span data-ttu-id="92ae5-121">零个或一个虚拟处理器映射到零个或多个逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-121">Zero or one virtual processor is mapped to zero or more logical processors.</span></span> <span data-ttu-id="92ae5-122">当虚拟处理器到逻辑处理器的映射为：</span><span class="sxs-lookup"><span data-stu-id="92ae5-122">When the virtual processor to logical processor mapping is:</span></span>  
> 
>      -   <span data-ttu-id="92ae5-123">一对零，则表示来宾操作系统未使用未绑定逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-123">One-to-zero, it represents an unbound logical processor not used by the guest operating systems.</span></span>  
>     -   <span data-ttu-id="92ae5-124">一对多，则表示过度提交。</span><span class="sxs-lookup"><span data-stu-id="92ae5-124">One-to-many, it represents an overcommit.</span></span>  
>     -   <span data-ttu-id="92ae5-125">零对多，则表示主机系统上没有虚拟机，所以虚拟机没有使用逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-125">Zero-to-many, it represents the absence of virtual machine on the host system, so no logical processors are used by VMs.</span></span>  
> 4.  <span data-ttu-id="92ae5-126">插槽映射到零个或多个内核。</span><span class="sxs-lookup"><span data-stu-id="92ae5-126">A socket is mapped to zero or more cores.</span></span> <span data-ttu-id="92ae5-127">当插槽到内核的映射为：</span><span class="sxs-lookup"><span data-stu-id="92ae5-127">When the socket to core mapping is:</span></span>  
> 
>      -   <span data-ttu-id="92ae5-128">一对零，则表示一个空插槽（未安装芯片）。</span><span class="sxs-lookup"><span data-stu-id="92ae5-128">One-to-zero, it represents an empty socket (no chip installed).</span></span>  
>     -   <span data-ttu-id="92ae5-129">一对一，则表示在插槽中安装了单核芯片（如今非常罕见)。</span><span class="sxs-lookup"><span data-stu-id="92ae5-129">One-to-one, it represents a single-core chip installed into the socket (very rare these days).</span></span>  
>     -   <span data-ttu-id="92ae5-130">一对多，则表示插槽中安装了多核芯片（典型值为 2、4、8）。</span><span class="sxs-lookup"><span data-stu-id="92ae5-130">One-to-many, it represents a multi-core ship installed into the socket (typical values are 2,4,8).</span></span>  
> 5.  <span data-ttu-id="92ae5-131">内核映射到一个或两个逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-131">A core is mapped to one or two logical processors.</span></span> <span data-ttu-id="92ae5-132">当内核到逻辑处理器的映射为：</span><span class="sxs-lookup"><span data-stu-id="92ae5-132">When the core to logical processor mapping is:</span></span>  
> 
>      -   <span data-ttu-id="92ae5-133">一对一，超线程处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="92ae5-133">One-to-one, hyperthreading is off.</span></span>  
>     -   <span data-ttu-id="92ae5-134">一对二，超线程处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="92ae5-134">One-to-two, hyperthreading is on.</span></span>  
  
 <span data-ttu-id="92ae5-135">下列定义适用于在本主题中使用的术语：</span><span class="sxs-lookup"><span data-stu-id="92ae5-135">The following definitions apply to the terms used throughout this topic:</span></span>  
  
-   <span data-ttu-id="92ae5-136">从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、操作系统、应用程序或驱动程序的角度理解，线程或逻辑处理器是一种逻辑计算引擎。</span><span class="sxs-lookup"><span data-stu-id="92ae5-136">A thread or logical processor is one logical computing engine from the perspective of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the operating system, an application or driver.</span></span>  
  
-   <span data-ttu-id="92ae5-137">内核是一个处理器单元，可由一个或多个逻辑处理器组成。</span><span class="sxs-lookup"><span data-stu-id="92ae5-137">A core is a processor unit, which can consist of one or more logical processors.</span></span>  
  
-   <span data-ttu-id="92ae5-138">物理处理器可包含一个或多个内核。</span><span class="sxs-lookup"><span data-stu-id="92ae5-138">A physical processor can consist of one or more cores.</span></span> <span data-ttu-id="92ae5-139">物理处理器等同于处理器包或插槽。</span><span class="sxs-lookup"><span data-stu-id="92ae5-139">A physical processor is the same as a processor package, or a socket.</span></span>  
  
 <span data-ttu-id="92ae5-140">具有多个物理处理器的系统或是具有含多个内核和/或超线程的物理处理器的系统，可支持操作系统同时执行多项任务。</span><span class="sxs-lookup"><span data-stu-id="92ae5-140">Systems with more than one physical processor or systems with physical processors that have multiple cores and/or hyperthreads enable the operating system to execute multiple tasks simultaneously.</span></span> <span data-ttu-id="92ae5-141">每个执行线程都显示为一个逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-141">Each thread of execution appears as a logical processor.</span></span> <span data-ttu-id="92ae5-142">例如，如果计算机具有启用超线程的两个四核处理器，且每个内核两个线程，则您有 16 个逻辑处理器：2 个处理器 x 每个处理器 4 个内核 x 每个内核 2 个线程。</span><span class="sxs-lookup"><span data-stu-id="92ae5-142">For example, if you have a computer that has two quad-core processors with hyper-threading enabled and two threads per core, you have 16 logical processors: 2 processors x 4 cores per processor x 2 threads per core.</span></span> <span data-ttu-id="92ae5-143">值得注意的是：</span><span class="sxs-lookup"><span data-stu-id="92ae5-143">It is worth noting that:</span></span>  
  
-   <span data-ttu-id="92ae5-144">来自超线程内核的单线程的逻辑处理器计算能力不及来自禁用超线程的同一内核的逻辑处理器计算能力。</span><span class="sxs-lookup"><span data-stu-id="92ae5-144">The compute capacity of a logical processor from a single thread of a hyperthreaded core is less than the compute capacity of a logical processor from that same core with hyperthreading disabled.</span></span>  
  
-   <span data-ttu-id="92ae5-145">但是超线程内核中两个逻辑处理器的计算能力则超过了禁用超线程的同一内核的计算能力。</span><span class="sxs-lookup"><span data-stu-id="92ae5-145">But the compute capacity of the 2 logical processors in the hyperthreaded core is greater than the compute capacity of the same core with hyperthreading disabled.</span></span>  
  
 <span data-ttu-id="92ae5-146">每个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本都有以下两种计算能力限制：</span><span class="sxs-lookup"><span data-stu-id="92ae5-146">Each edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has two compute capacity limits:</span></span>  
  
1.  <span data-ttu-id="92ae5-147">插槽最大值（与物理处理器/插槽/处理器包相同）。</span><span class="sxs-lookup"><span data-stu-id="92ae5-147">A maximum number of Sockets (Same as Physical processor or Socket or Processor package).</span></span>  
  
2.  <span data-ttu-id="92ae5-148">操作系统报告的内核最大数量。</span><span class="sxs-lookup"><span data-stu-id="92ae5-148">A maximum number of cores as reported by the operating system.</span></span>  
  
 <span data-ttu-id="92ae5-149">这些限制适用于单个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="92ae5-149">These limits apply to a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="92ae5-150">它们代表单个实例将使用的最大计算能力。</span><span class="sxs-lookup"><span data-stu-id="92ae5-150">They represent the maximum compute capacity that a single instance will use.</span></span> <span data-ttu-id="92ae5-151">它们不会限制可能部署该实例的服务器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-151">They do not constrain the server upon which the instance may be deployed.</span></span> <span data-ttu-id="92ae5-152">实际上，在同一物理服务器上部署多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例可以有效使用物理服务器的计算能力，因为更多插槽和/或内核的计算能力超出了下表中的计算能力限制。</span><span class="sxs-lookup"><span data-stu-id="92ae5-152">In fact deploying multiple instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the same physical server is an efficient way to use the compute capacity of a physical server with more sockets and/or cores than the capacity limits below.</span></span>  
  
 <span data-ttu-id="92ae5-153">下表指定每个版本的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]的单个实例的计算能力限制：</span><span class="sxs-lookup"><span data-stu-id="92ae5-153">The following table specifies the compute capacity limits for a single instance of each edition of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]:</span></span>  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="92ae5-154">版本</span><span class="sxs-lookup"><span data-stu-id="92ae5-154">Edition</span></span>|<span data-ttu-id="92ae5-155">单个实例使用的最大计算能力 ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)])</span><span class="sxs-lookup"><span data-stu-id="92ae5-155">Maximum Compute Capacity Used by a Single Instance ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)])</span></span>|<span data-ttu-id="92ae5-156">单个实例使用的最大计算能力（AS、RS）1</span><span class="sxs-lookup"><span data-stu-id="92ae5-156">Maximum Compute Capacity Used by a Single Instance (AS, RS)</span></span>|  
|---------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|  
|<span data-ttu-id="92ae5-157">Enterprise Edition：基于内核的许可<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="92ae5-157">Enterprise Edition: Core-based Licensing<sup>1</sup></span></span>|<span data-ttu-id="92ae5-158">操作系统支持的最大值</span><span class="sxs-lookup"><span data-stu-id="92ae5-158">Operating system maximum</span></span>|<span data-ttu-id="92ae5-159">操作系统支持的最大值</span><span class="sxs-lookup"><span data-stu-id="92ae5-159">Operating system maximum</span></span>|  
|<span data-ttu-id="92ae5-160">开发人员</span><span class="sxs-lookup"><span data-stu-id="92ae5-160">Developer</span></span>|<span data-ttu-id="92ae5-161">操作系统支持的最大值</span><span class="sxs-lookup"><span data-stu-id="92ae5-161">Operating system maximum</span></span>|<span data-ttu-id="92ae5-162">操作系统支持的最大值</span><span class="sxs-lookup"><span data-stu-id="92ae5-162">Operating system maximum</span></span>|  
|<span data-ttu-id="92ae5-163">计算</span><span class="sxs-lookup"><span data-stu-id="92ae5-163">Evaluation</span></span>|<span data-ttu-id="92ae5-164">操作系统支持的最大值</span><span class="sxs-lookup"><span data-stu-id="92ae5-164">Operating system maximum</span></span>|<span data-ttu-id="92ae5-165">操作系统支持的最大值</span><span class="sxs-lookup"><span data-stu-id="92ae5-165">Operating system maximum</span></span>|  
|<span data-ttu-id="92ae5-166">商业智能</span><span class="sxs-lookup"><span data-stu-id="92ae5-166">Business Intelligence</span></span>|<span data-ttu-id="92ae5-167">限制为 4 个插槽或 16 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-167">Limited to lesser of 4 Sockets or 16 cores</span></span>|<span data-ttu-id="92ae5-168">操作系统支持的最大值</span><span class="sxs-lookup"><span data-stu-id="92ae5-168">Operating system maximum</span></span>|  
|<span data-ttu-id="92ae5-169">Standard</span><span class="sxs-lookup"><span data-stu-id="92ae5-169">Standard</span></span>|<span data-ttu-id="92ae5-170">限制为 4 个插槽或 16 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-170">Limited to lesser of 4 Sockets or 16 cores</span></span>|<span data-ttu-id="92ae5-171">限制为 4 个插槽或 16 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-171">Limited to lesser of 4 Sockets or 16 cores</span></span>|  
|<span data-ttu-id="92ae5-172">Web</span><span class="sxs-lookup"><span data-stu-id="92ae5-172">Web</span></span>|<span data-ttu-id="92ae5-173">限制为 4 个插槽或 16 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-173">Limited to lesser of 4 Sockets or 16 cores</span></span>|<span data-ttu-id="92ae5-174">限制为 4 个插槽或 16 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-174">Limited to lesser of 4 Sockets or 16 cores</span></span>|  
|<span data-ttu-id="92ae5-175">Express</span><span class="sxs-lookup"><span data-stu-id="92ae5-175">Express</span></span>|<span data-ttu-id="92ae5-176">限制为 1 个插槽或 4 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-176">Limited to lesser of 1 Socket or 4 cores</span></span>|<span data-ttu-id="92ae5-177">限制为 1 个插槽或 4 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-177">Limited to lesser of 1 Socket or 4 cores</span></span>|  
|<span data-ttu-id="92ae5-178">Express with Tools</span><span class="sxs-lookup"><span data-stu-id="92ae5-178">Express with Tools</span></span>|<span data-ttu-id="92ae5-179">限制为 1 个插槽或 4 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-179">Limited to lesser of 1 Socket or 4 cores</span></span>|<span data-ttu-id="92ae5-180">限制为 1 个插槽或 4 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-180">Limited to lesser of 1 Socket or 4 cores</span></span>|  
|<span data-ttu-id="92ae5-181">Express with Advanced Services</span><span class="sxs-lookup"><span data-stu-id="92ae5-181">Express with Advanced Services</span></span>|<span data-ttu-id="92ae5-182">限制为 1 个插槽或 4 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-182">Limited to lesser of 1 Socket or 4 cores</span></span>|<span data-ttu-id="92ae5-183">限制为 1 个插槽或 4 核，取二者中的较小值</span><span class="sxs-lookup"><span data-stu-id="92ae5-183">Limited to lesser of 1 Socket or 4 cores</span></span>|  
  
 <span data-ttu-id="92ae5-184"><sup>1</sup>企业版 with Server + 客户端访问许可证 (基于 CAL) 的许可 (不能用于新协议) 每个实例最多只能有20个内核 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="92ae5-184"><sup>1</sup> Enterprise Edition with Server + Client Access License (CAL) based licensing (not available for new agreements) is limited to a maximum of 20 cores per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="92ae5-185">基于内核的服务器许可模型没有限制。</span><span class="sxs-lookup"><span data-stu-id="92ae5-185">There are no limits under the Core-based Server Licensing model.</span></span>  
  
 <span data-ttu-id="92ae5-186">在虚拟化环境中，计算能力限制基于逻辑处理器的数目，而不是内核数目，这是因为处理器体系结构对来宾应用程序不可见。</span><span class="sxs-lookup"><span data-stu-id="92ae5-186">In a virtualized environment, the compute capacity limit is based on the number of logical processors, not cores, because the processor architecture is not visible to the guest applications.</span></span>  <span data-ttu-id="92ae5-187">例如，如果服务器的四个插槽中插入了四核处理器，同时该服务器每个内核可支持两个超线程，这样在启用超线程时就有 32 个逻辑处理器，在禁用超线程时只有 16 个逻辑处理器。</span><span class="sxs-lookup"><span data-stu-id="92ae5-187">For example, a server with four sockets populated with quad-core processors and the ability to enable two hyperthreads per core contains 32 logical processors with hyperthreading enabled but only 16 logical processors with hyperthreading disabled.</span></span> <span data-ttu-id="92ae5-188">这些逻辑处理器可映射到服务器上的虚拟机，该逻辑处理器上的虚拟机的计算负载映射到主机服务器中物理处理器上的执行线程。</span><span class="sxs-lookup"><span data-stu-id="92ae5-188">These logical processors can be mapped to virtual machines on the server with the virtual machines' compute load on that logical processor mapped into a thread of execution on the physical processor in the host server.</span></span>  
  
 <span data-ttu-id="92ae5-189">如果每个虚拟处理器的性能很重要，则最好禁用超线程。</span><span class="sxs-lookup"><span data-stu-id="92ae5-189">You may want to disable hyperthreading when the performance per virtual processor is important.</span></span> <span data-ttu-id="92ae5-190">用户可以在 BIOS 设置过程中使用 BIOS 的处理器设置启用或禁用超线程，但这通常是服务器范围内的操作，该操作将影响运行在该服务器上的所有工作负荷。</span><span class="sxs-lookup"><span data-stu-id="92ae5-190">One can enable or disable hyperthreading using a BIOS setting for the processor during the BIOS setup, but it is typically a server scoped operation that will impact all workloads running on the server.</span></span> <span data-ttu-id="92ae5-191">这就可能要求将要运行在虚拟化环境中的工作负荷与会受益于物理操作系统环境中的超线程性能提升的工作负荷分隔开。</span><span class="sxs-lookup"><span data-stu-id="92ae5-191">This may suggest separating workloads that will run in virtualized environments from those that would benefit from the hyperthreading performance boost in a physical operating system environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ae5-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92ae5-192">See Also</span></span>  
 <span data-ttu-id="92ae5-193">[SQL Server 2014 的版本和组件](../sql-server/editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="92ae5-193">[Editions and Components of SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="92ae5-194">[SQL Server 2014 的各个版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="92ae5-194">[Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="92ae5-195">[SQL Server 的最大容量规范](../sql-server/maximum-capacity-specifications-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="92ae5-195">[Maximum Capacity Specifications for SQL Server](../sql-server/maximum-capacity-specifications-for-sql-server.md) </span></span>  
 [<span data-ttu-id="92ae5-196">SQL Server 2014 安装快速入门</span><span class="sxs-lookup"><span data-stu-id="92ae5-196">Quick-Start Installation of SQL Server 2014</span></span>](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
