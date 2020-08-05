---
title: 验证最大工作线程数设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dbffb87f58d2beb633f43ff18680222ea62cf5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580178"
---
# <a name="verify-max-worker-threads-setting"></a><span data-ttu-id="a24a2-102">验证最大工作线程数设置</span><span class="sxs-lookup"><span data-stu-id="a24a2-102">Verify Max Worker Threads Setting</span></span>
  <span data-ttu-id="a24a2-103">此规则检查 max worker threads 服务器选项中是否存在可能不正确的设置。</span><span class="sxs-lookup"><span data-stu-id="a24a2-103">This rule checks the max worker threads server option for potentially incorrect settings.</span></span> <span data-ttu-id="a24a2-104">如果将 max worker threads 选项设置为较小的值，则可能会使过多的线程无法及时为传入的客户端请求提供服务，并且可能会导致“线程资源不足”。</span><span class="sxs-lookup"><span data-stu-id="a24a2-104">Setting the max worker threads option to a small value may prevent enough threads from servicing incoming client requests in a timely manner and could lead to "thread starvation".</span></span> <span data-ttu-id="a24a2-105">但是，如果将此选项设置为较大的值，则由于每个活动线程在 32 位服务器上占用 512 KB，在 64 位服务器上最多占用 4 MB，因此可能会浪费地址空间。</span><span class="sxs-lookup"><span data-stu-id="a24a2-105">However, setting the option to a large value can waste address space, because each active thread consumes 512 KB on 32-bit servers and up to 4 MB on 64-bit servers.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="a24a2-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="a24a2-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="a24a2-107">将 max worker threads 选项设置为 0。</span><span class="sxs-lookup"><span data-stu-id="a24a2-107">Set the max worker threads option to 0.</span></span> <span data-ttu-id="a24a2-108">这样 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就能够根据用户请求自动确定正确的活动工作线程数。</span><span class="sxs-lookup"><span data-stu-id="a24a2-108">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically determine the correct number of active worker threads based on user requests.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a24a2-109">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="a24a2-109">For More Information</span></span>  
 [<span data-ttu-id="a24a2-110">配置 max worker threads 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="a24a2-110">Configure the max worker threads Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="a24a2-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a24a2-111">See Also</span></span>  
 [<span data-ttu-id="a24a2-112">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="a24a2-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
