---
title: 正确的关联掩码和关联输入输出掩码重叠 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486b4441a20db7630082344fb1f277bba053f3ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694449"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a><span data-ttu-id="07b06-102">正确的关联掩码和关联输入输出掩码重叠</span><span class="sxs-lookup"><span data-stu-id="07b06-102">Correct Affinity Mask and Affinity Input Output Mask Overlap</span></span>
  <span data-ttu-id="07b06-103">此规则检查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例是否有一个或多个要分配以用于 affinity mask 和 affinity I/O mask 选项的处理器。</span><span class="sxs-lookup"><span data-stu-id="07b06-103">This rule checks whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one or more processors that are assigned to be used with both the affinity mask and the affinity I/O mask options.</span></span> <span data-ttu-id="07b06-104">在有多个处理器的计算机上，affinity mask 和 affinity I/O mask 选项用于指定哪些 CPU 由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="07b06-104">On a computer that has more than one processor, the affinity mask and the affinity I/O mask options are used to designate which CPUs are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="07b06-105">启用包含关联掩码和关联 I/O 掩码的 CPU 会由于强制过度使用处理器而降低性能。</span><span class="sxs-lookup"><span data-stu-id="07b06-105">Enabling a CPU with both the affinity mask and the affinity I/O mask can slow performance by forcing the processor to be overused.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="07b06-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="07b06-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="07b06-107">指定 affinity mask 和 affinity I/O mask 选项时，应同时指定这两个选项，但每个 CPU 的启用次数不超过一次。</span><span class="sxs-lookup"><span data-stu-id="07b06-107">When you specify either the affinity mask or the affinity I/O mask options, you should specify both, but only enable each CPU no more than once.</span></span>  
  
 <span data-ttu-id="07b06-108">请勿在 affinity mask 和 affinity I/O mask 选项中同时启用同一个 CPU。</span><span class="sxs-lookup"><span data-stu-id="07b06-108">Do not enable the same CPU in both the affinity mask option and the affinity I/O mask option.</span></span> <span data-ttu-id="07b06-109">每个 CPU 对应的位应处于下列三种状态之一：</span><span class="sxs-lookup"><span data-stu-id="07b06-109">The bits that correspond to each CPU should be in one of the following states:</span></span>  
  
-   <span data-ttu-id="07b06-110">在 affinity mask 和 affinity I/O mask 选项中均为 0</span><span class="sxs-lookup"><span data-stu-id="07b06-110">0 in both the affinity mask option and the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="07b06-111">在 affinity mask 选项中为 0，在 affinity I/O mask 选项中为 1</span><span class="sxs-lookup"><span data-stu-id="07b06-111">0 in the affinity mask option and 1 in the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="07b06-112">在 affinity mask 选项中为 1，在 affinity I/O mask 选项中为 0</span><span class="sxs-lookup"><span data-stu-id="07b06-112">1 in the affinity mask option and 0 in the affinity I/O mask option</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="07b06-113">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="07b06-113">For More Information</span></span>  
 [<span data-ttu-id="07b06-114">affinity mask 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="07b06-114">affinity mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="07b06-115">affinity I/O mask 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="07b06-115">affinity Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="07b06-116">affinity64 mask 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="07b06-116">affinity64 mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="07b06-117">affinity64 I/O mask 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="07b06-117">affinity64 Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="07b06-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07b06-118">See Also</span></span>  
 [<span data-ttu-id="07b06-119">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="07b06-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
