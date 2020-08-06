---
title: affinity64 I/O mask 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19616f5718254bde5601ea1beeec21412ad867de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588050"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a><span data-ttu-id="ed393-102">affinity64 I/O mask 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="ed393-102">affinity64 Input-Output mask Server Configuration Option</span></span>
  <span data-ttu-id="ed393-103">**affinity64 I/O mask** 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affinity I/O mask **选项类似，用于将** 磁盘 I/O 绑定到指定的 CPU 子集。</span><span class="sxs-lookup"><span data-stu-id="ed393-103">The **affinity64 I/O mask** binds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O to a specified subset of CPUs, similar to the **affinity I/O mask** option.</span></span> <span data-ttu-id="ed393-104">使用 **affinity I/O mask** 只能绑定前 32 个处理器，而使用 **affinity64 I/O mask** 可以绑定计算机上剩余的处理器。</span><span class="sxs-lookup"><span data-stu-id="ed393-104">Use **affinity I/O mask** to bind the first 32 processors, and use **affinity64 I/O mask** to bind the remaining processors on the computer.</span></span> <span data-ttu-id="ed393-105">如果重新配置 **affinity64 I/O mask**，则必须重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="ed393-105">If you reconfigure the **affinity64 I/O mask**, you must restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ed393-106">此选项仅出现在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 64 位版本中。</span><span class="sxs-lookup"><span data-stu-id="ed393-106">This option is only visible on the 64-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed393-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed393-107">See Also</span></span>  
 <span data-ttu-id="ed393-108">[affinity I/O mask 服务器配置选项](affinity-input-output-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="ed393-108">[affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="ed393-109">[监视资源使用情况（系统监视器）](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="ed393-109">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="ed393-110">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ed393-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="ed393-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed393-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="ed393-112">RECONFIGURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ed393-112">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
