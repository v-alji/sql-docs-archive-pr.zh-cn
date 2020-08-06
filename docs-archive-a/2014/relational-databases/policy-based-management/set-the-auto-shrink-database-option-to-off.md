---
title: 将 AUTO_SHRINK 数据库选项设置为 OFF | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 42d79ed13a691c3d39a28e7ab35a740a9f613fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693260"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a><span data-ttu-id="afac4-102">将 AUTO_SHRINK 数据库选项设置为 OFF</span><span class="sxs-lookup"><span data-stu-id="afac4-102">Set the AUTO_SHRINK Database Option to OFF</span></span>
  <span data-ttu-id="afac4-103">此规则检查 AUTO_SHRINK 数据库选项是否已设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="afac4-103">This rule checks whether the AUTO_SHRINK database option is set to OFF.</span></span> <span data-ttu-id="afac4-104">频繁收缩和展开数据库可能会导致物理碎片。</span><span class="sxs-lookup"><span data-stu-id="afac4-104">Frequently shrinking and expanding a database can lead to physical fragmentation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="afac4-105">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="afac4-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="afac4-106">将 AUTO_SHRINK 数据库选项设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="afac4-106">Set the AUTO_SHRINK database option to OFF.</span></span> <span data-ttu-id="afac4-107">如果您知道以后将不再需要要回收的空间，则可以通过手动收缩数据库来回收该空间。</span><span class="sxs-lookup"><span data-stu-id="afac4-107">If you know that the space that you are reclaiming will not be needed in the future, you can reclaim the space by manually shrinking the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="afac4-108">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="afac4-108">For More Information</span></span>  
 <span data-ttu-id="afac4-109">Microsoft 知识库文章 [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span><span class="sxs-lookup"><span data-stu-id="afac4-109">Microsoft Knowledge Base article [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afac4-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="afac4-110">See Also</span></span>  
 [<span data-ttu-id="afac4-111">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="afac4-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
