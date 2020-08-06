---
title: 服务器属性（“处理器”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.processor.f1
ms.assetid: cc1581a2-492b-41f0-bda5-17909b65c4f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4d241f01de7ac961832e77bb09483cff275deb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587585"
---
# <a name="server-properties-processors-page"></a><span data-ttu-id="eb46c-102">服务器属性（“处理器”页）</span><span class="sxs-lookup"><span data-stu-id="eb46c-102">Server Properties (Processors Page)</span></span>
  <span data-ttu-id="eb46c-103">使用此页可以查看或修改处理器选项。</span><span class="sxs-lookup"><span data-stu-id="eb46c-103">Use this page to view or modify your processor options.</span></span> <span data-ttu-id="eb46c-104">只有在安装了多个处理器时，才可以启用处理器关联设置。</span><span class="sxs-lookup"><span data-stu-id="eb46c-104">Processor affinity settings are only enabled when more than one processor is installed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="eb46c-105">选项</span><span class="sxs-lookup"><span data-stu-id="eb46c-105">Options</span></span>  
 <span data-ttu-id="eb46c-106">**处理器关联**</span><span class="sxs-lookup"><span data-stu-id="eb46c-106">**Processor Affinity**</span></span>  
 <span data-ttu-id="eb46c-107">将处理器分配给特定的线程，以消除处理器重新加载和减少处理器之间的线程迁移。</span><span class="sxs-lookup"><span data-stu-id="eb46c-107">Assigns processors to specific threads to eliminating processor reloads and reduce thread migration across processors.</span></span> <span data-ttu-id="eb46c-108">有关详细信息，请参阅 [关联掩码服务器配置选项](affinity-mask-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="eb46c-108">For more information, see [affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="eb46c-109">**I/O 关联**</span><span class="sxs-lookup"><span data-stu-id="eb46c-109">**I/O Affinity**</span></span>  
 <span data-ttu-id="eb46c-110">将 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘 I/O 绑定到指定的 CPU 子集。</span><span class="sxs-lookup"><span data-stu-id="eb46c-110">Binds [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/Os to a specified subset of CPUs.</span></span> <span data-ttu-id="eb46c-111">有关详细信息，请参阅 [关联 I/O 掩码服务器配置选项](affinity-input-output-mask-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="eb46c-111">For more information, see [affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="eb46c-112">**自动设置所有处理器的处理器关联掩码**</span><span class="sxs-lookup"><span data-stu-id="eb46c-112">**Automatically set processor affinity mask for all processors**</span></span>  
 <span data-ttu-id="eb46c-113">允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 设置处理器关联。</span><span class="sxs-lookup"><span data-stu-id="eb46c-113">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the processor affinity.</span></span>  
  
 <span data-ttu-id="eb46c-114">**自动设置所有处理器的 I/O 关联掩码**</span><span class="sxs-lookup"><span data-stu-id="eb46c-114">**Automatically set I/O affinity mask for all processors**</span></span>  
 <span data-ttu-id="eb46c-115">允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 设置 I/O 关联。</span><span class="sxs-lookup"><span data-stu-id="eb46c-115">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the I/O affinity.</span></span>  
  
 <span data-ttu-id="eb46c-116">**最大工作线程数**</span><span class="sxs-lookup"><span data-stu-id="eb46c-116">**Maximum worker threads**</span></span>  
 <span data-ttu-id="eb46c-117">如果为 0，则允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 动态设置工作线程数。</span><span class="sxs-lookup"><span data-stu-id="eb46c-117">0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to dynamically set the number of worker threads.</span></span> <span data-ttu-id="eb46c-118">对于大多数系统而言，此为最佳设置。</span><span class="sxs-lookup"><span data-stu-id="eb46c-118">This setting is best for most systems.</span></span> <span data-ttu-id="eb46c-119">但是，根据您的系统配置，将此选项设置为特定值有时可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="eb46c-119">However, depending on your system configuration, setting this option to a specific value sometimes improves performance.</span></span> <span data-ttu-id="eb46c-120">有关详细信息，请参阅 [配置 max worker threads 服务器配置选项](configure-the-max-worker-threads-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="eb46c-120">For more information, see [Configure the max worker threads Server Configuration Option](configure-the-max-worker-threads-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="eb46c-121">**提升 SQL Server 的优先级**</span><span class="sxs-lookup"><span data-stu-id="eb46c-121">**Boost SQL Server priority**</span></span>  
 <span data-ttu-id="eb46c-122">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否应当以比同一计算机上的其他进程更高的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 计划优先级运行。</span><span class="sxs-lookup"><span data-stu-id="eb46c-122">Specifies whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="eb46c-123">有关详细信息，请参阅 [配置 priority boost 服务器配置选项](configure-the-priority-boost-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="eb46c-123">For more information, see [Configure the priority boost Server Configuration Option](configure-the-priority-boost-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="eb46c-124">**使用 Windows 纤程(轻型池)**</span><span class="sxs-lookup"><span data-stu-id="eb46c-124">**Use Windows fibers (lightweight pooling)**</span></span>  
 <span data-ttu-id="eb46c-125">使用 Windows 纤程代替 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的线程。</span><span class="sxs-lookup"><span data-stu-id="eb46c-125">Use Windows fibers instead of threads for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="eb46c-126">请注意，此选项仅适用于 Windows 2003 Server Edition。</span><span class="sxs-lookup"><span data-stu-id="eb46c-126">Note that this is only available in Windows 2003 Server Edition.</span></span> <span data-ttu-id="eb46c-127">有关详细信息，请参阅 [lightweight pooling 服务器配置选项](lightweight-pooling-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="eb46c-127">For more information, see [lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="eb46c-128">**配置值**</span><span class="sxs-lookup"><span data-stu-id="eb46c-128">**Configured Values**</span></span>  
 <span data-ttu-id="eb46c-129">显示此窗格上选项的配置值。</span><span class="sxs-lookup"><span data-stu-id="eb46c-129">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="eb46c-130">如果更改了这些值，请单击 **“运行值”** 以查看更改是否已生效。</span><span class="sxs-lookup"><span data-stu-id="eb46c-130">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="eb46c-131">如果尚未生效，则必须首先重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="eb46c-131">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="eb46c-132">**“运行值”**</span><span class="sxs-lookup"><span data-stu-id="eb46c-132">**Running Values**</span></span>  
 <span data-ttu-id="eb46c-133">查看此窗格上选项的当前运行值。</span><span class="sxs-lookup"><span data-stu-id="eb46c-133">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="eb46c-134">这些值是只读的。</span><span class="sxs-lookup"><span data-stu-id="eb46c-134">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb46c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb46c-135">See Also</span></span>  
 [<span data-ttu-id="eb46c-136">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eb46c-136">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
