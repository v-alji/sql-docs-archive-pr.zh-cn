---
title: 增加或禁用阻塞的进程阈值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a7a90aea3fa8fb4d9c423cea1ec6008b01cde883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578173"
---
# <a name="increase-or-disable-blocked-process-threshold"></a><span data-ttu-id="363db-102">增加或禁用阻塞的进程阈值</span><span class="sxs-lookup"><span data-stu-id="363db-102">Increase or Disable Blocked Process Threshold</span></span>
  <span data-ttu-id="363db-103">此规则检查 blocked process threshold 选项是否已设置为 0（禁用），或者是否已设置为大于或等于 5（秒）的值。</span><span class="sxs-lookup"><span data-stu-id="363db-103">This rules checks that the blocked process threshold option is set to 0 (disabled) or set to a value higher than or equal to 5 (seconds).</span></span> <span data-ttu-id="363db-104">将 blocked process threshold 选项设置为从 1 到 4 的值可能会导致死锁监视器不断运行。</span><span class="sxs-lookup"><span data-stu-id="363db-104">Setting the blocked process threshold option to a value from 1 to 4 can cause the deadlock monitor to run constantly.</span></span> <span data-ttu-id="363db-105">值 1 到 4 应仅用于故障排除，决不应在没有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门的协助下长期使用或在生产环境中使用。</span><span class="sxs-lookup"><span data-stu-id="363db-105">Values 1 to 4 should only be used for troubleshooting, and never long term or in a production environment without the assistance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="363db-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="363db-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="363db-107">若要解决此问题，请将 blocked process threshold 选项设置为 5（秒）或更大的值，或者通过将值设置为 0 来禁用阻塞的进程阈值。</span><span class="sxs-lookup"><span data-stu-id="363db-107">To resolve this problem, set the blocked process threshold option to a value of 5 (seconds) or higher, or disable blocked process threshold by setting the value to 0.</span></span> <span data-ttu-id="363db-108">若要将阻塞的进程阈值设置为值 `5` 秒，请执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="363db-108">To set the blocked process threshold to a value of `5` seconds, execute the following statement:</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="363db-109">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="363db-109">For More Information</span></span>  
 [<span data-ttu-id="363db-110">blocked process threshold 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="363db-110">blocked process threshold Server Configuration Option</span></span>](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="363db-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="363db-111">See Also</span></span>  
 [<span data-ttu-id="363db-112">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="363db-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
