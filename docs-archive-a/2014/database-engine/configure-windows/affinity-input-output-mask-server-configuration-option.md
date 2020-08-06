---
title: affinity I/O mask 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- affinity I/O mask option
- processor affinity [SQL Server]
- binding processors [SQL Server]
- CPU affinity mask option
ms.assetid: 9950a8c9-9fe0-4003-95df-6f0d1becb0e7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d0606e2a3f5480b27e27a4a585562f4b289b640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576976"
---
# <a name="affinity-input-output-mask-server-configuration-option"></a><span data-ttu-id="71aa9-102">affinity I/O mask 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="71aa9-102">affinity Input-Output mask Server Configuration Option</span></span>
  <span data-ttu-id="71aa9-103">为了执行多任务， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 和 Windows Server 2003 有时会在不同的处理器之间移动进程线程。</span><span class="sxs-lookup"><span data-stu-id="71aa9-103">To carry out multitasking, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 and Windows Server 2003 sometimes move process threads among different processors.</span></span> <span data-ttu-id="71aa9-104">虽然从操作系统方面而言，此活动是高效的，但是在高系统负荷的情况下，该活动会降低 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的性能，因为每个处理器缓存都会不断地重新加载数据。</span><span class="sxs-lookup"><span data-stu-id="71aa9-104">Although efficient from an operating system point of view, this activity can reduce [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performance under heavy system loads, as each processor cache is repeatedly reloaded with data.</span></span> <span data-ttu-id="71aa9-105">如果将各个处理器分配给特定线程，则通过消除处理器的重新加载需要，可以提高在这些条件下的性能；线程与处理器之间的这种关联称为“处理器关联”。</span><span class="sxs-lookup"><span data-stu-id="71aa9-105">Assigning processors to specific threads can improve performance under these conditions by eliminating processor reloads; such an association between a thread and a processor is called processor affinity.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71aa9-106">通过以下两个关联掩码选项来支持处理器关联： **关联掩码** （也称为 **CPU 关联掩码**）和 **关联 I/O 掩码**。</span><span class="sxs-lookup"><span data-stu-id="71aa9-106">supports processor affinity by means of two affinity mask options: **affinity mask** (also known as **CPU affinity mask**) and **affinity I/O mask**.</span></span> <span data-ttu-id="71aa9-107">有关 **关联掩码** 选项的详细信息，请参阅 [关联掩码服务器配置选项](affinity-mask-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="71aa9-107">For more information on the **affinity mask** option, see [affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md).</span></span> <span data-ttu-id="71aa9-108">对于具有 33 至 64 个处理器的服务器，CPU 和 I/O 关联支持还要求分别使用 [affinity64 掩码服务器配置选项](affinity64-mask-server-configuration-option.md) 和 [affinity64 I/O 掩码服务器配置选项](affinity64-input-output-mask-server-configuration-option.md) 。</span><span class="sxs-lookup"><span data-stu-id="71aa9-108">CPU and I/O affinity support for servers with 33 to 64 processors requires the additional use of the [affinity64 mask Server Configuration Option](affinity64-mask-server-configuration-option.md) and [affinity64 Input-Output mask Server Configuration Option](affinity64-input-output-mask-server-configuration-option.md) respectively.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71aa9-109">对具有 33 到 64 个处理器的服务器的关联支持仅在 64 位操作系统上可用。</span><span class="sxs-lookup"><span data-stu-id="71aa9-109">Affinity support for servers with 33 to 64 processors is only available on 64-bit operating systems.</span></span>  
  
 <span data-ttu-id="71aa9-110">**关联 I/O 掩码** 选项将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘 I/O 绑定到指定的 CPU 子集。</span><span class="sxs-lookup"><span data-stu-id="71aa9-110">The **affinity I/O mask** option binds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O to a specified subset of CPUs.</span></span> <span data-ttu-id="71aa9-111">在高端 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机事务处理 (OLTP) 环境中，此扩展可以提高 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 线程执行 I/O 的性能。</span><span class="sxs-lookup"><span data-stu-id="71aa9-111">In high-end [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] online transactional processing (OLTP) environments, this extension can enhance the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] threads issuing I/Os.</span></span> <span data-ttu-id="71aa9-112">此增强功能不支持对各个磁盘或磁盘控制器的硬件关联。</span><span class="sxs-lookup"><span data-stu-id="71aa9-112">This enhancement does not support hardware affinity for individual disks or disk controllers.</span></span>  
  
 <span data-ttu-id="71aa9-113">**关联 I/O 掩码** 的值指定了在多处理器计算机中有哪些 CPU 可用于处理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="71aa9-113">The value for **affinity I/O mask** specifies which CPUs in a multiprocessor computer are eligible to process [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O operations.</span></span> <span data-ttu-id="71aa9-114">该掩码是一个位图，其中最右边的位指定顺序最低的 CPU(0)，该位左边的位指定顺序次低的 CPU(1)，依此类推。</span><span class="sxs-lookup"><span data-stu-id="71aa9-114">The mask is a bitmap in which the rightmost bit specifies the lowest-order CPU(0), the bit to its immediate left specifies the next-lowest-order CPU(1), and so on.</span></span> <span data-ttu-id="71aa9-115">若要配置超过 32 个处理器，请同时设置 **关联 I/O 掩码** 和 **affinity64 I/O 掩码**。</span><span class="sxs-lookup"><span data-stu-id="71aa9-115">To configure more than 32 processors, set both the **affinity I/O mask** and the **affinity64 I/O mask**.</span></span>  
  
 <span data-ttu-id="71aa9-116">**关联 I/O 掩码** 值如下所示：</span><span class="sxs-lookup"><span data-stu-id="71aa9-116">The values for **affinity I/O mask** are as follows:</span></span>  
  
-   <span data-ttu-id="71aa9-117">在多处理器计算机中，1 字节 **关联 I/O 掩码** 最多可以涵盖 8 个 CPU。</span><span class="sxs-lookup"><span data-stu-id="71aa9-117">A 1-byte **affinity I/O mask** covers up to 8 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="71aa9-118">在多处理器计算机中，2 字节 **关联 I/O 掩码** 最多可以涵盖 16 个 CPU。</span><span class="sxs-lookup"><span data-stu-id="71aa9-118">A 2-byte **affinity I/O mask** covers up to 16 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="71aa9-119">在多处理器计算机中，3 字节 **关联 I/O 掩码** 最多可以涵盖 24 个 CPU。</span><span class="sxs-lookup"><span data-stu-id="71aa9-119">A 3-byte **affinity I/O mask** covers up to 24 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="71aa9-120">在多处理器计算机中，4 字节 **关联 I/O 掩码** 最多可以涵盖 32 个 CPU。</span><span class="sxs-lookup"><span data-stu-id="71aa9-120">A 4-byte **affinity I/O mask** covers up to 32 CPUs in a multiprocessor computer.</span></span>  
  
-   <span data-ttu-id="71aa9-121">若要包括超过 32 个 CPU，请为前 32 个 CPU 配置一个 4 字节 **关联 I/O 掩码** ，并为余下的 CPU 配置最多 4 字节的 **affinity64 I/O** 掩码。</span><span class="sxs-lookup"><span data-stu-id="71aa9-121">To cover more than 32 CPUs, configure a four-byte **affinity I/O mask** for the first 32 CPUs and up to a four-byte **affinity64 I/O mask** for the remaining CPUs.</span></span>  
  
 <span data-ttu-id="71aa9-122">关联 I/O 模式中某一位的值为 1，则指定相应的 CPU 可执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘 I/O 操作；值为 0，则指定相应的 CPU 未安排任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="71aa9-122">A 1 bit in the affinity I/O pattern specifies that the corresponding CPU is eligible to perform [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O operations; a 0 bit specifies that no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O operations should be scheduled for the corresponding CPU.</span></span> <span data-ttu-id="71aa9-123">如果将所有位设置为零或不指定**关联 I/O 掩码**，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘 I/O 将由任何可处理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 线程的 CPU 执行。</span><span class="sxs-lookup"><span data-stu-id="71aa9-123">When all bits are set to zero, or **affinity I/O mask** is not specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O is scheduled to any of the CPUs eligible to process [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] threads.</span></span>  
  
 <span data-ttu-id="71aa9-124">因为设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]“关联 I/O 掩码”选项是一项专用操作，所以建议只在需要时使用。</span><span class="sxs-lookup"><span data-stu-id="71aa9-124">Because setting the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **affinity I/O mask** option is a specialized operation, it should be used only when necessary.</span></span> <span data-ttu-id="71aa9-125">大多数情况下，Windows 2000 或 Windows Server 2003 的默认关联就可以提供最佳性能。</span><span class="sxs-lookup"><span data-stu-id="71aa9-125">In most cases, the Windows 2000 or Windows Server 2003 default affinity provides the best performance.</span></span>  
  
 <span data-ttu-id="71aa9-126">指定**关联 I/O 掩码**选项后，必须将其与**关联掩码**配置选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="71aa9-126">When specifying the **affinity I/O mask** option, you must use it with the **affinity mask** configuration option.</span></span> <span data-ttu-id="71aa9-127">请勿在“关联 I/O 掩码”开关和“关联掩码”选项中启用相同的 CPU。</span><span class="sxs-lookup"><span data-stu-id="71aa9-127">Do not enable the same CPU in both the **affinity I/O mask** switch and the **affinity mask** option.</span></span> <span data-ttu-id="71aa9-128">每个 CPU 对应的位必须处于下列三种状态之一：</span><span class="sxs-lookup"><span data-stu-id="71aa9-128">The bits corresponding to each CPU should be in one of the following three states:</span></span>  
  
-   <span data-ttu-id="71aa9-129">在“关联 I/O 掩码”选项和“关联掩码”选项中均为 0。</span><span class="sxs-lookup"><span data-stu-id="71aa9-129">0 in both the **affinity I/O mask** option and the **affinity mask** option.</span></span>  
  
-   <span data-ttu-id="71aa9-130">在“关联 I/O 掩码”选项中为 1，在“关联掩码”选项中为 0。</span><span class="sxs-lookup"><span data-stu-id="71aa9-130">1 in the **affinity I/O mask** option and 0 in the **affinity mask** option.</span></span>  
  
-   <span data-ttu-id="71aa9-131">在“关联 I/O 掩码”选项中为 0，在“关联掩码”选项中为 1。</span><span class="sxs-lookup"><span data-stu-id="71aa9-131">0 in the **affinity I/O mask** option and 1 in the **affinity mask** option.</span></span>  
  
 <span data-ttu-id="71aa9-132">“关联 I/O 掩码”选项是一个高级选项。</span><span class="sxs-lookup"><span data-stu-id="71aa9-132">The **affinity I/O mask** option is an advanced option.</span></span> <span data-ttu-id="71aa9-133">如果使用 `sp_configure` 系统存储过程来更改该设置，则仅当**show advanced options**设置为1时才能更改**关联 i/o 掩码**。</span><span class="sxs-lookup"><span data-stu-id="71aa9-133">If you are using the `sp_configure` system stored procedure to change the setting, you can change **affinity I/O mask** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="71aa9-134">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，重新配置“关联 I/O 掩码”选项要求重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="71aa9-134">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], reconfiguring the **affinity I/O mask** option requires a restart of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="71aa9-135">请不要在 Windows 操作系统中配置 CPU 关联后，还在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中配置关联掩码。</span><span class="sxs-lookup"><span data-stu-id="71aa9-135">Do not configure CPU affinity in the Windows operating system and also configure the affinity mask in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="71aa9-136">这些设置实现的效果相同，如果配置不一致，则可能会得到意外的结果。</span><span class="sxs-lookup"><span data-stu-id="71aa9-136">These settings are attempting to achieve the same result, and if the configurations are inconsistent, you may have unpredictable results.</span></span> <span data-ttu-id="71aa9-137">最好使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 `sp_configure` 选项配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU 关联。</span><span class="sxs-lookup"><span data-stu-id="71aa9-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU affinity is best configured using the `sp_configure` option in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71aa9-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71aa9-138">See Also</span></span>  
 <span data-ttu-id="71aa9-139">[监视资源使用情况（系统监视器）](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="71aa9-139">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="71aa9-140">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71aa9-140">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="71aa9-141">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71aa9-141">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="71aa9-142">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="71aa9-142">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
