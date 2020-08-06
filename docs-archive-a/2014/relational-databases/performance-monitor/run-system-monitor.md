---
title: 运行系统监视器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dd0baf32402d69e36dc5120d0259b2f8d689897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692853"
---
# <a name="run-system-monitor"></a><span data-ttu-id="88f0a-102">运行系统监视器</span><span class="sxs-lookup"><span data-stu-id="88f0a-102">Run System Monitor</span></span>
  <span data-ttu-id="88f0a-103">系统监视器使用远程过程调用 (RPC) 从 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]收集信息。</span><span class="sxs-lookup"><span data-stu-id="88f0a-103">System Monitor uses remote procedure calls (RPCs) to collect information from Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="88f0a-104">拥有运行系统监视器的 Microsoft Windows 权限的任何用户都可以使用系统监视器来监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="88f0a-104">Any user who has Microsoft Windows permissions to run System Monitor can use System Monitor to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88f0a-105">使用系统监视器或性能监视器时，不能连接到运行于 Windows 98 上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="88f0a-105">When using System Monitor or Performance Monitor, you cannot connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on Windows 98.</span></span>  
  
 <span data-ttu-id="88f0a-106">与所有性能监视工具一样，使用系统监视器监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时，性能方面会受到一些影响。</span><span class="sxs-lookup"><span data-stu-id="88f0a-106">As with all performance monitoring tools, expect some performance overhead when you use System Monitor to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="88f0a-107">特定实例中的实际影响取决于硬件平台、计数器数量以及所选更新间隔。</span><span class="sxs-lookup"><span data-stu-id="88f0a-107">The actual overhead in any specific instance depends on the hardware platform, the number of counters, and the selected update interval.</span></span> <span data-ttu-id="88f0a-108">但是，将系统监视器与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 集成可以尽量减少对性能的影响。</span><span class="sxs-lookup"><span data-stu-id="88f0a-108">However, the integration of System Monitor with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is designed to minimize any reduction in performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88f0a-109">如果选择了系统监视器管理单元中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 性能计数器进行监视，即使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未运行，也会看到计数器。</span><span class="sxs-lookup"><span data-stu-id="88f0a-109">If you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performance counters to monitor in the System Monitor snap-in, you will see the counters even if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running.</span></span>  
  
 <span data-ttu-id="88f0a-110">有关启动系统监视器的信息，请参阅[启动系统监视器 (Windows)](../performance/start-system-monitor-windows.md)。</span><span class="sxs-lookup"><span data-stu-id="88f0a-110">For information about starting System Monitor, see [Start System Monitor &#40;Windows&#41;](../performance/start-system-monitor-windows.md).</span></span>  
  
  
