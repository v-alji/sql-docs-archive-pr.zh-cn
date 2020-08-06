---
title: affinity64 mask 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- affinity64 mask option
- binding processors [SQL Server]
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2ea6d2e364feaa67d91de0055617aac9dc285ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588048"
---
# <a name="affinity64-mask-server-configuration-option"></a><span data-ttu-id="493c6-102">affinity64 mask 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="493c6-102">affinity64 mask Server Configuration Option</span></span>
  <span data-ttu-id="493c6-103">affinity64 mask 将处理器绑定到特定的线程，这与 affinity mask 选项相似。</span><span class="sxs-lookup"><span data-stu-id="493c6-103">The affinity64 mask binds processors to specific threads, similar to the affinity mask option.</span></span> <span data-ttu-id="493c6-104">使用 affinity mask 可以绑定前 32 个处理器，而使用 affinity64 mask 可以绑定计算机上余下的处理器。</span><span class="sxs-lookup"><span data-stu-id="493c6-104">Use affinity mask to bind the first 32 processors, and use affinity64 mask to bind the remaining processors on the computer.</span></span> <span data-ttu-id="493c6-105">此选项仅出现在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 64 位版本中。</span><span class="sxs-lookup"><span data-stu-id="493c6-105">This option is only visible on the 64-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] <span data-ttu-id="493c6-106">改为使用 [ALTER SERVER CONFIGURATION (Transact-SQL)](/sql/t-sql/statements/alter-server-configuration-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="493c6-106">Use [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql) instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493c6-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="493c6-107">See Also</span></span>  
 <span data-ttu-id="493c6-108">[affinity mask 服务器配置选项](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="493c6-108">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="493c6-109">[监视资源使用情况（系统监视器）](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="493c6-109">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="493c6-110">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="493c6-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="493c6-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="493c6-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="493c6-112">RECONFIGURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="493c6-112">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
