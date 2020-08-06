---
title: 内存属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f2d2e56c9a951cee27752bd57d55d185a9b6618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694579"
---
# <a name="memory-properties"></a><span data-ttu-id="51418-102">内存属性</span><span class="sxs-lookup"><span data-stu-id="51418-102">Memory Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="51418-103">支持下表中列出的服务器内存属性。</span><span class="sxs-lookup"><span data-stu-id="51418-103">supports the server memory properties listed in the following table.</span></span> <span data-ttu-id="51418-104">有关设置这些属性的指南，请参阅 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="51418-104">For guidance in setting these properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="51418-105">介于 1 和 100 之间的值表示 **“物理总内存”** 或 **“虚拟地址空间”** 的百分比（以二者中少者计）。</span><span class="sxs-lookup"><span data-stu-id="51418-105">Values between 1 and 100 represent percentages of **Total Physical Memory** or **Virtual Address Space**, whichever is less.</span></span> <span data-ttu-id="51418-106">超过 100 的值表示内存限制（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="51418-106">Values over 100 represent memory limits in bytes.</span></span>  
  
 <span data-ttu-id="51418-107">**适用于：** 多维和表格服务器模式，除非另外说明。</span><span class="sxs-lookup"><span data-stu-id="51418-107">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51418-108">属性</span><span class="sxs-lookup"><span data-stu-id="51418-108">Properties</span></span>  
 `LowMemoryLimit`  
 <span data-ttu-id="51418-109">一个有符号的 64 位双精度浮点数属性，可定义服务器内存不足所在的点，以总物理内存的百分比表示。</span><span class="sxs-lookup"><span data-stu-id="51418-109">A signed 64-bit double-precision floating-point number property that defines the point at which the server is low on memory, expressed as percentage of total physical memory.</span></span> <span data-ttu-id="51418-110">达到此限制时，实例将通过关闭过期会话以及卸载未使用的计算从缓存中缓慢清除内存。</span><span class="sxs-lookup"><span data-stu-id="51418-110">When this limit is reached, the instance will start to slowly clear memory out of caches by closing expired sessions and unloading unused calculations.</span></span> <span data-ttu-id="51418-111">服务器不会在未超过此限制的情况下释放内存。</span><span class="sxs-lookup"><span data-stu-id="51418-111">The server will not release memory below this limit.</span></span> <span data-ttu-id="51418-112">默认值为 65；这指示最低内存限制为物理内存或虚拟地址空间的 65%（以二者中少者计）。</span><span class="sxs-lookup"><span data-stu-id="51418-112">The default value is 65; which indicates the low memory limit is 65% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 `TotalMemoryLimit`  
 <span data-ttu-id="51418-113">定义一个阈值，当达到此阈值时，服务器会更主动地释放内存。</span><span class="sxs-lookup"><span data-stu-id="51418-113">Defines a threshold that when reached, causes the server to deallocate memory more aggressively.</span></span> <span data-ttu-id="51418-114">默认值为物理内存或虚拟地址空间的 80%（以二者中少者计）。</span><span class="sxs-lookup"><span data-stu-id="51418-114">The default value 80% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 <span data-ttu-id="51418-115">请注意，`TotalMemoryLimit` 必须始终小于 `HardMemoryLimit`。</span><span class="sxs-lookup"><span data-stu-id="51418-115">Note that `TotalMemoryLimit` must always be less than `HardMemoryLimit`</span></span>  
  
 `HardMemoryLimit`  
 <span data-ttu-id="51418-116">指定一个内存阈值，达到该阈值后实例会主动终止活动用户会话以减少内存的使用量。</span><span class="sxs-lookup"><span data-stu-id="51418-116">Specifies a memory threshold after which the instance aggressively terminates active user sessions to reduce memory usage.</span></span> <span data-ttu-id="51418-117">所有终止的会话都将收到关于因内存压力而被取消的错误。</span><span class="sxs-lookup"><span data-stu-id="51418-117">All terminated sessions will receive an error about being cancelled by memory pressure.</span></span> <span data-ttu-id="51418-118">默认值为零 (0)，这意味着 `HardMemoryLimit` 将设置为 `TotalMemoryLimit` 和系统的物理总内存之间的中间值；如果系统的物理内存大于进程的虚拟地址空间，则改用虚拟地址空间来计算 `HardMemoryLimit`。</span><span class="sxs-lookup"><span data-stu-id="51418-118">The default value, zero (0), means the `HardMemoryLimit` will be set to a midway value between `TotalMemoryLimit` and the total physical memory of the system; if the physical memory of the system is larger than the virtual address space of the process, then virtual address space will be used instead to calculate `HardMemoryLimit`.</span></span>  
  
 `VirtualMemoryLimit`  
 <span data-ttu-id="51418-119">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-119">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `VertiPaqPagingPolicy`  
 <span data-ttu-id="51418-120">指定服务器内存不足时的分页行为。</span><span class="sxs-lookup"><span data-stu-id="51418-120">Specifies the paging behavior in the event the server runs low on memory.</span></span> <span data-ttu-id="51418-121">以下是有效值：</span><span class="sxs-lookup"><span data-stu-id="51418-121">Valid values are as follows:</span></span>  
  
 <span data-ttu-id="51418-122">零 (**0**) 禁用分页。</span><span class="sxs-lookup"><span data-stu-id="51418-122">Zero (**0**) disables paging.</span></span> <span data-ttu-id="51418-123">如果内存不足，处理将失败，同时显示内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="51418-123">If memory is insufficient, processing fails with an out-of-memory error.</span></span> <span data-ttu-id="51418-124">如果禁用分页，必须向服务帐户授予 Windows 特权。</span><span class="sxs-lookup"><span data-stu-id="51418-124">If you disable paging, you must grant Windows privileges to the service account.</span></span> <span data-ttu-id="51418-125">有关说明，请参阅[配置服务帐户 (Analysis Services)](../instances/configure-service-accounts-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="51418-125">See [Configure Service Accounts &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md) for instructions.</span></span>  
  
 <span data-ttu-id="51418-126">**1** 为默认值。</span><span class="sxs-lookup"><span data-stu-id="51418-126">**1** is the default.</span></span> <span data-ttu-id="51418-127">该属性支持使用操作系统页文件 (pagefile.sys) 分页到磁盘。</span><span class="sxs-lookup"><span data-stu-id="51418-127">This property enables paging to disk using the operating system page file (pagefile.sys).</span></span>  
  
 <span data-ttu-id="51418-128">在 `VertiPaqPagingPolicy` 设置为 1 时，处理不大可能由于内存限制而失败，因为服务器将尝试使用您指定的方法对磁盘进行分页。</span><span class="sxs-lookup"><span data-stu-id="51418-128">When `VertiPaqPagingPolicy` is set to 1, processing is less likely to fail due to memory constraints because the server will try to page to disk using the method that you specified.</span></span> <span data-ttu-id="51418-129">设置 `VertiPaqPagingPolicy` 属性并不会确保内存错误永远不会发生。</span><span class="sxs-lookup"><span data-stu-id="51418-129">Setting the `VertiPaqPagingPolicy` property does not guarantee that memory errors will never happen.</span></span> <span data-ttu-id="51418-130">在下列条件下仍然可能会发生内存不足错误：</span><span class="sxs-lookup"><span data-stu-id="51418-130">Out of memory errors can still occur under the following conditions:</span></span>  
  
-   <span data-ttu-id="51418-131">没有足够的内存来用于所有字典。</span><span class="sxs-lookup"><span data-stu-id="51418-131">There is not enough memory for all dictionaries.</span></span> <span data-ttu-id="51418-132">在处理过程中，Analysis Services 会在内存中锁定每一列的字典，并且所有这些列所占用的内存不能超过为 `VertiPaqMemoryLimit` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="51418-132">During processing, Analysis Services locks the dictionaries for each column in memory, and all of these together cannot be more than the value specified for `VertiPaqMemoryLimit`.</span></span>  
  
-   <span data-ttu-id="51418-133">没有足够的虚拟地址空间来容纳这个过程。</span><span class="sxs-lookup"><span data-stu-id="51418-133">There is insufficient virtual address space to accommodate the process.</span></span>  
  
 <span data-ttu-id="51418-134">为了解决永久性的内存不足错误，您可以尝试重新设计模型以便减少需要处理的数据量，或者可以向计算机添加更多的物理内存。</span><span class="sxs-lookup"><span data-stu-id="51418-134">To resolve persistent out of memory errors, you can either try to redesign the model to reduce the amount of data that needs processing, or you can add more physical memory to the computer.</span></span>  
  
 <span data-ttu-id="51418-135">仅适用于表格服务器模式。</span><span class="sxs-lookup"><span data-stu-id="51418-135">Applies to tabular server mode only.</span></span>  
  
 `VertiPaqMemoryLimit`  
 <span data-ttu-id="51418-136">如果允许分页到磁盘，此属性指定内存占用达到何种程度（表示为内存总量的百分比）才开始分页。</span><span class="sxs-lookup"><span data-stu-id="51418-136">If paging to disk is allowed, this property specifies the level of memory consumption (as a percentage of total memory) at which paging starts.</span></span> <span data-ttu-id="51418-137">默认值为 60。</span><span class="sxs-lookup"><span data-stu-id="51418-137">The default is 60.</span></span> <span data-ttu-id="51418-138">如果内存占用不超过 60%，则服务器不会分页到磁盘。</span><span class="sxs-lookup"><span data-stu-id="51418-138">If memory consumption is less than 60 percent, the server will not page to disk.</span></span>  
  
 <span data-ttu-id="51418-139">此属性依赖于 `VertiPaqPagingPolicyProperty`，该属性必须设置为 1 才能进行分页。</span><span class="sxs-lookup"><span data-stu-id="51418-139">This property depends on the `VertiPaqPagingPolicyProperty`, which must be set to 1 in order for paging to occur.</span></span>  
  
 <span data-ttu-id="51418-140">仅适用于表格服务器模式。</span><span class="sxs-lookup"><span data-stu-id="51418-140">Applies to tabular server mode only.</span></span>  
  
 `HighMemoryPrice`  
 <span data-ttu-id="51418-141">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryHeapType`  
 <span data-ttu-id="51418-142">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="51418-143">仅适用于多维服务器模式。</span><span class="sxs-lookup"><span data-stu-id="51418-143">Applies to multidimensional server mode only.</span></span>  
  
 `HeapTypeForObjects`  
 <span data-ttu-id="51418-144">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="51418-145">仅适用于多维服务器模式。</span><span class="sxs-lookup"><span data-stu-id="51418-145">Applies to multidimensional server mode only.</span></span>  
  
 `DefaultPagesCountToReuse`  
 <span data-ttu-id="51418-146">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `HandleIA64AlignmentFaults`  
 <span data-ttu-id="51418-147">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MidMemoryPrice`  
 <span data-ttu-id="51418-148">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinimumAllocatedMemory`  
 <span data-ttu-id="51418-149">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PreAllocate`  
 <span data-ttu-id="51418-150">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SessionMemoryLimit`  
 <span data-ttu-id="51418-151">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `WaitCountIfHighMemory`  
 <span data-ttu-id="51418-152">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="51418-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51418-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51418-153">See Also</span></span>  
 <span data-ttu-id="51418-154">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="51418-154">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="51418-155">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="51418-155">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
