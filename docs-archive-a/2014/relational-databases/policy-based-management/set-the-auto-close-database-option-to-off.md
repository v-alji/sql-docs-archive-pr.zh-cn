---
title: 将 AUTO_CLOSE 数据库选项设置为 OFF | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: db6cf5a3f82c3493a8732958594743104fccc968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693261"
---
# <a name="set-the-auto_close-database-option-to-off"></a><span data-ttu-id="a7512-102">将 AUTO_CLOSE 数据库选项设置为 OFF</span><span class="sxs-lookup"><span data-stu-id="a7512-102">Set the AUTO_CLOSE Database Option to OFF</span></span>
  <span data-ttu-id="a7512-103">此规则检查 AUTO_ CLOSE 选项是否设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="a7512-103">This rule checks whether the AUTO_ CLOSE option is set OFF.</span></span> <span data-ttu-id="a7512-104">AUTO_CLOSE 设置为 ON 时，该选项可能导致频繁访问数据库而使性能下降，这是因为在每次连接后打开和关闭数据库增加了开销。</span><span class="sxs-lookup"><span data-stu-id="a7512-104">When AUTO_CLOSE is set ON, this option can cause performance degradation on frequently accessed databases because of the increased overhead of opening and closing the database after each connection.</span></span> <span data-ttu-id="a7512-105">AUTO_CLOSE 还会在每次连接后刷新过程缓存。</span><span class="sxs-lookup"><span data-stu-id="a7512-105">AUTO_CLOSE also flushes the procedure cache after each connection.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="a7512-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="a7512-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="a7512-107">如果频繁访问数据库，则将数据库的 AUTO_CLOSE 选项设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="a7512-107">If a database is accessed frequently, set the AUTO_CLOSE option to OFF for the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a7512-108">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="a7512-108">For More Information</span></span>  
 [<span data-ttu-id="a7512-109">ALTER DATABASE SET 选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a7512-109">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="a7512-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7512-110">See Also</span></span>  
 [<span data-ttu-id="a7512-111">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="a7512-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
