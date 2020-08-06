---
title: 服务器属性（“内存”页）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.memory.f1
ms.assetid: 46a77d4e-ab92-49d3-a14b-423462e50715
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a000a4c670b36b08a34fd544cc5ff5e61c7bab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587596"
---
# <a name="server-properties-memory-page"></a><span data-ttu-id="05a04-102">服务器属性（“内存”页）</span><span class="sxs-lookup"><span data-stu-id="05a04-102">Server Properties (Memory Page)</span></span>
  <span data-ttu-id="05a04-103">使用此页可以查看或修改服务器内存选项。</span><span class="sxs-lookup"><span data-stu-id="05a04-103">Use this page to view or modify your server memory options.</span></span> <span data-ttu-id="05a04-104">当 **“最小服务器内存”** 设置为 0 而 **“最大服务器内存”** 设置为 2147483647 MB 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以在任何给定的时间使用最合理的内存量，具体取决于操作系统以及其他应用程序当前使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="05a04-104">When **Minimum server memory** is set to 0 and **Maximum server memory** is set to 2147483647 MB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can take advantage of the optimum amount of memory at any given time, subject to how much memory the operating system and other applications are currently using.</span></span> <span data-ttu-id="05a04-105">当计算机和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上的负载更改时，分配的内存也会更改。</span><span class="sxs-lookup"><span data-stu-id="05a04-105">As the load on the computer and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] changes, so does the memory allocated.</span></span> <span data-ttu-id="05a04-106">可以进一步将此动态内存分配限制为下面指定的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="05a04-106">You can further limit this dynamic memory allocation to the minimum and maximum values specified below.</span></span>  
  
## <a name="options"></a><span data-ttu-id="05a04-107">选项</span><span class="sxs-lookup"><span data-stu-id="05a04-107">Options</span></span>  
 <span data-ttu-id="05a04-108">**最小服务器内存(MB)**</span><span class="sxs-lookup"><span data-stu-id="05a04-108">**Minimum server memory (in MB)**</span></span>  
 <span data-ttu-id="05a04-109">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 应该至少以分配的最小内存量启动，在低于此值时不释放内存。</span><span class="sxs-lookup"><span data-stu-id="05a04-109">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should start with at least the minimum amount of allocated memory and not release memory below this value.</span></span> <span data-ttu-id="05a04-110">请根据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的大小和活动设置此值。</span><span class="sxs-lookup"><span data-stu-id="05a04-110">Set this value based on the size and activity of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05a04-111">始终将此选项设置为合理的值，以确保操作系统不会从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 请求过多的内存，从而避免降低 Windows 的性能。</span><span class="sxs-lookup"><span data-stu-id="05a04-111">Always set the option to a reasonable value to ensure that the operating system does not request too much memory from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and inhibit Windows performance.</span></span>  
  
 <span data-ttu-id="05a04-112">**最大服务器内存(MB)**</span><span class="sxs-lookup"><span data-stu-id="05a04-112">**Maximum server memory (in MB)**</span></span>  
 <span data-ttu-id="05a04-113">指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动和运行时它可以分配的内存最大量。</span><span class="sxs-lookup"><span data-stu-id="05a04-113">Specifies the maximum amount of memory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can allocate when it starts and while it runs.</span></span> <span data-ttu-id="05a04-114">如果知道有多个应用程序与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 同时运行，并且要保证这些应用程序有足够的内存运行，则可以将此配置选项设置为特定值。</span><span class="sxs-lookup"><span data-stu-id="05a04-114">This configuration option can be set to a specific value if you know there are multiple applications running at the same time as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and you want to guarantee that these applications have sufficient memory to run.</span></span> <span data-ttu-id="05a04-115">如果这些应用程序（如 Web 服务器或电子邮件服务器）只是按需请求内存，则不必设置该选项，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将会根据需要向它们释放内存。</span><span class="sxs-lookup"><span data-stu-id="05a04-115">If these other applications, such as Web or e-mail servers, request memory only as needed, then do not set the option, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will release memory to them as needed.</span></span> <span data-ttu-id="05a04-116">但是，应用程序通常在启动时使用全部可用内存，并且也不会根据需要请求更多内存。</span><span class="sxs-lookup"><span data-stu-id="05a04-116">However, applications often use whatever memory is available when they start and do not request more if needed.</span></span> <span data-ttu-id="05a04-117">如果以这种方式运行的应用程序与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]同时运行在同一台计算机上，则请设置该选项的值，保证应用程序所需的内存不会由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]来分配。</span><span class="sxs-lookup"><span data-stu-id="05a04-117">If an application that behaves in this manner runs on the same computer at the same time as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], set the option to a value that guarantees that the memory required by the application is not allocated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05a04-118">对于32位系统，可以为**max server memory**指定的最小内存量为 64 MB (MB) ，为64位系统提供 128 mb。</span><span class="sxs-lookup"><span data-stu-id="05a04-118">The minimum amounts of memory you can specify for **max server memory** are 64 megabytes (MB) for 32-bit systems and 128 MB for 64-bit systems.</span></span>  
  
 <span data-ttu-id="05a04-119">**创建索引占用的内存(KB，0 = 动态内存)**</span><span class="sxs-lookup"><span data-stu-id="05a04-119">**Index creation memory (in KB, 0 = dynamic memory)**</span></span>  
 <span data-ttu-id="05a04-120">指定在索引创建排序过程中要使用的内存量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="05a04-120">Specifies the amount of memory (in KB) to use during index creation sorts.</span></span> <span data-ttu-id="05a04-121">默认值为零，表示启用动态分配，在大多数情况下，无需进一步调整即可正常工作；不过，用户可以输入 704 到 2147483647 之间的其他值。</span><span class="sxs-lookup"><span data-stu-id="05a04-121">The default value of zero enables dynamic allocation and should work in most cases without additional adjustment; however, the user can enter a different value from 704 to 2147483647.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05a04-122">不允许使用 1 到 703 之间的值。</span><span class="sxs-lookup"><span data-stu-id="05a04-122">Values from 1 to 703 are not allowed.</span></span> <span data-ttu-id="05a04-123">如果输入此范围的值，该字段将使用 704 覆盖所输入的值。</span><span class="sxs-lookup"><span data-stu-id="05a04-123">If a value in this range is entered, the field overrides the entered value with 704.</span></span>  
  
 <span data-ttu-id="05a04-124">**每次查询占用的最小内存(KB)**</span><span class="sxs-lookup"><span data-stu-id="05a04-124">**Minimum memory per query (in KB)**</span></span>  
 <span data-ttu-id="05a04-125">指定为执行查询分配的内存量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="05a04-125">Specifies the amount of memory (in KB) to allocate for the execution of a query.</span></span> <span data-ttu-id="05a04-126">用户可以将值从 512 设置为 2147483647 KB。</span><span class="sxs-lookup"><span data-stu-id="05a04-126">The user can set the value from 512 to 2147483647 KB.</span></span> <span data-ttu-id="05a04-127">默认值为 1024 KB。</span><span class="sxs-lookup"><span data-stu-id="05a04-127">The default value is 1024 KB.</span></span>  
  
 <span data-ttu-id="05a04-128">**配置值**</span><span class="sxs-lookup"><span data-stu-id="05a04-128">**Configured Values**</span></span>  
 <span data-ttu-id="05a04-129">显示此窗格上选项的配置值。</span><span class="sxs-lookup"><span data-stu-id="05a04-129">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="05a04-130">如果更改了这些值，请单击 **“运行值”** 以查看更改是否已生效。</span><span class="sxs-lookup"><span data-stu-id="05a04-130">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="05a04-131">如果尚未生效，则必须首先重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="05a04-131">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="05a04-132">**“运行值”**</span><span class="sxs-lookup"><span data-stu-id="05a04-132">**Running Values**</span></span>  
 <span data-ttu-id="05a04-133">显示此窗格上选项的当前运行值。</span><span class="sxs-lookup"><span data-stu-id="05a04-133">Shows the currently running values for the options on this pane.</span></span> <span data-ttu-id="05a04-134">这些值是只读的。</span><span class="sxs-lookup"><span data-stu-id="05a04-134">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a04-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05a04-135">See Also</span></span>  
 <span data-ttu-id="05a04-136">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="05a04-136">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="05a04-137">“服务器内存”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="05a04-137">Server Memory Server Configuration Options</span></span>](server-memory-server-configuration-options.md)  
  
  
