---
title: 禁用轻型池 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13b9ccba0a3a5805dab2eec1d04cc161e6dbd6ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693793"
---
# <a name="disable-lightweight-pooling"></a><span data-ttu-id="c3a82-102">禁用轻型池</span><span class="sxs-lookup"><span data-stu-id="c3a82-102">Disable Lightweight Pooling</span></span>
  <span data-ttu-id="c3a82-103">此规则检查服务器上是否已禁用轻型池。</span><span class="sxs-lookup"><span data-stu-id="c3a82-103">This rule checks that lightweight pooling is disabled on the server.</span></span> <span data-ttu-id="c3a82-104">将 lightweightpooling 设置为 1 将使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 切换到纤程模式计划。</span><span class="sxs-lookup"><span data-stu-id="c3a82-104">Setting lightweightpooling to 1 causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to switch to fiber mode scheduling.</span></span> <span data-ttu-id="c3a82-105">纤程模式专用于 UMS 工作线程的上下文切换是性能的主要瓶颈的某些情况。</span><span class="sxs-lookup"><span data-stu-id="c3a82-105">Fiber mode is intended for certain situations in which the context switching of the UMS workers is the important bottleneck in performance.</span></span> <span data-ttu-id="c3a82-106">由于这种情况很少出现，所以纤程模式很少提高典型系统上的性能或可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="c3a82-106">Because this is rare, fiber mode seldom improves performance or scalability on the typical system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="c3a82-107">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="c3a82-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="c3a82-108">lightweightpooling 选项应仅在以下情况下启用：进行彻底的测试之后、评估所有其他性能优化机会之后，以及上下文切换在您的环境中是已知问题时。</span><span class="sxs-lookup"><span data-stu-id="c3a82-108">The lightweightpooling option should only be enabled after thorough testing, after all other performance tuning opportunities are evaluated, and when context switching is a known issue in your environment.</span></span>  
  
 <span data-ttu-id="c3a82-109">建议您不要使用纤程模式计划日常操作，这是因为它会抑制上下文切换优势的正常发挥，并且使用线程本地存储区 (TLS) 或线程所有的对象（如互斥体，一种 Win32 内核对象）的某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件在纤程模式下无法正常工作</span><span class="sxs-lookup"><span data-stu-id="c3a82-109">We recommend that you do not use fiber mode scheduling for routine operation because it can decrease performance by preventing the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a kind of Win32 kernel object), cannot function correctly in fiber mode</span></span>  
  
 <span data-ttu-id="c3a82-110">若要删除轻型池，请执行下面的语句，然后重新启动 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c3a82-110">To remove lightweight pooling, execute the following statement, and then restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweightpooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="c3a82-111">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="c3a82-111">For More Information</span></span>  
 [<span data-ttu-id="c3a82-112">lightweight pooling 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="c3a82-112">lightweight pooling Server Configuration Option</span></span>](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3a82-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3a82-113">See Also</span></span>  
 [<span data-ttu-id="c3a82-114">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="c3a82-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
